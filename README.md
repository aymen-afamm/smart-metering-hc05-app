⚡ Smart Metering HC-05 (Compteur d'Énergie Intelligent)

Ce projet implémente un système de surveillance de consommation d'énergie simulée avec un microcontrôleur Arduino. Il utilise le protocole Bluetooth pour envoyer les données de consommation à une application mobile et permet le contrôle à distance de deux LED via l'application.

⚙️ Fonctionnalités

Télémétrie de Consommation : Envoi continu de la valeur de consommation (kWh) toutes les 10 secondes à l'application mobile.

Affichage Local : Affichage centré du numéro d'ID (ID:#453687) et de la consommation incrémentée sur un écran LCD 16x4.

Contrôle Bidirectionnel : Réception de commandes Bluetooth (via une Switch) pour allumer ou éteindre deux LED de statut.

Débogage Intégré : Affichage des commandes reçues sur le Moniteur Série pour faciliter le dépannage (e.g., Recu BT/USB (lower): [led_off]).

🧱 Composants Matériels Requis

Composant

Description

Microcontrôleur

Arduino Uno

Communication

Module Bluetooth HC-05 ou HC-06

Affichage

Écran LCD 16x4 avec adaptateur I2C

Contrôle

2 x LED (avec résistances 220 $\Omega$)

Application

Application Android (Code source Kotlin/XML fourni dans ce projet)

🔌 Schéma de Câblage

Connexions Essentielles

Composant

Broche du Composant

Broche de l'Arduino Uno

Notes

HC-05

TXD

D10

(RX Logiciel)

HC-05

RXD

D11

(TX Logiciel)

LCD I2C

SDA

A4



LCD I2C

SCL

A5



LED 1

Anode (+)

D2

Broche de sortie

LED 2

Anode (+)

D3

Broche de sortie

⚠️ ATTENTION : Ne jamais connecter les LED aux broches D0 (RX matériel) et D1 (TX matériel), car cela interférerait avec la communication série et causerait des erreurs.

💻 Instructions de Mise en Route (Arduino)

Installez les Bibliothèques :

LiquidCrystal_I2C (par B. T. H.)

SoftwareSerial (intégrée à l'IDE Arduino)

Vérifiez l'Adresse LCD : Dans le code (compteur_led_arduino.cpp), assurez-vous que l'adresse 0x27 est correcte pour votre module LCD. Si l'affichage est décalé, remplacez-la par 0x3F.

Téléversez le Code : Téléversez le fichier compteur_led_arduino.cpp sur votre Arduino Uno.

📱 Protocole de Communication Bluetooth

L'application mobile (Kotlin) et l'Arduino communiquent sur une vitesse de 9600 bauds.

1. Données Sortantes (Arduino $\rightarrow$ Téléphone)

L'Arduino envoie la valeur du compteur sous le format :
[Nombre] kWh

Exemple : 154359 kWh

2. Commandes Entrantes (Téléphone $\rightarrow$ Arduino)

Les commandes doivent être envoyées en minuscules et suivies du caractère de nouvelle ligne (\n).

Commande Envoyée

Résultat sur l'Arduino

led_off

Les LED connectées à D2 et D3 s'éteignent.

led_on

Les LED connectées à D2 et D3 s'allument.

🐞 Dépannage (Switch LED ne Fonctionne Pas)

Si les LED ne s'éteignent pas :

Vérification de Câblage : Confirmez que les LED sont bien sur D2/D3 et que le HC-05 est bien sur D10/D11 (croisé : TX $\rightarrow$ RX, RX $\rightarrow$ TX).

Test de Réception (Moniteur Série) :

Déconnectez les fils du HC-05 (D10/D11).

Ouvrez le Moniteur Série de l'IDE.

Tapez led_off (avec "Nouvelle ligne" sélectionné) et envoyez.

Si les LED s'éteignent, le problème vient de l'envoi de l'application mobile (problème de nouvelle ligne ou de connexion instable).

⚡⚡⚡⚡ Avant la connection ⚡⚡⚡⚡
![WhatsApp Image 2025-10-27 at 05 26 36](https://github.com/user-attachments/assets/16bab38c-bdc2-4fde-8254-afa60a415cd5)


⚡⚡⚡⚡ Apres la connection ⚡⚡⚡⚡
![WhatsApp Image 2025-10-27 at 05 33 30](https://github.com/user-attachments/assets/8d81f694-8cd0-4d19-a6f3-fc967ec9fd27)


