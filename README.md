# arduino-nrf24-capteur
Principe de fonctionnement
Le module nRF24l01 est un émetteur-récepteur faible puissance qui permet l’échange de données sans fil sur la bande de fréquence radio 2.4GHz. Il permet de communiquer entre deux appareils de manière efficace et sur une moyenne distance (50m) lorsque ces derniers sont en vue directe, c’est-à-dire sans obstacle. Si vous souhaitez communiquer sur de plus longues distances en extérieur, il faudra préférer un module RF433 ou LoRa. En intérieur, si un ou plusieurs murs sont présents entre l’émetteur et le récepteur, il sera préférable d’utiliser la communication WiFi ou Bluetooth.

Schéma
Le module nRF24L01 utilise la protocole SPI pour communiquer avec le microcontrôleur et doit être alimenté entre 1.9 et 3.6V. La communication SPI utilise des boches spécifiques.Le brochage se fait comme suit (à gauche côté NRF24L01, à droite côté Arduino UNO):

Vcc (Alimentation) <-> 3V3
CE (Reset) <-> 2
GND (Masse) <-> GND
MOSI (Master Output Slave Input) <-> 11
MISO (Master Input Slave Output) <-> 12
SCK (Serial Clock) <-> 13
CS (chip select) <-> 4
Pour améliorer la portée et la stabilité de la connexion, il est conseillé de souder un condensateur entre les broches Vcc et GND sur certains modules.

![img](https://www.aranacorp.com/wp-content/uploads/arduino-radio-module-nrf24l01_bb.png)

Code
Pour gérer le module NRF24L01 nous utilisons les librairies RF24.h, nRF24L01.h et SPI.h. Dans le code suivant, qui fonctionne pour le maître (role=0) et l’esclave (role=1), nous définissons un noeud pour chaque module, un qui va envoyer des données l'autre qui va les recevoir.