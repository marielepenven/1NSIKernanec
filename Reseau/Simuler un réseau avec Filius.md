# Simuler un réseau avec Filius. 

### Introduction. 

Le terme **réseau** en informatique signifie que au moins deux ordinateurs sont reliés entre eux. Il existe plusieurs façon de relier des ordinateurs entre eux mais l’**Ethernet** et le **wifi** sont les plus répandus. Les raisonnements concernant le wifi étant quasiment les mêmes que pour l’Ethernet, nous parlerons principalement d’Ethernet dans ce TP.

Pour relier deux ordinateurs il nous faut un câble Ethernet avec des prises RJ45 :

![](/Reseau/IMG/reseau_13.jpg)



Et les ordinateurs doivent posséder une carte réseau :

![](/Reseau/IMG/reseau_14.jpg)

### Les adresses IP. 

Une adresse **IPv4** est un nombre sur 4 octet écrit sous la forme a.b.c.d qui identifie un ordinateur sur le réseau. Elle doit donc être **unique**. Un octet peut prendre des valeurs entre 0 et 255.

Question 1: Quel est le nombre total d’adresses IPv4 existantes ?



Ce nombre n’étant pas très grand par rapport au nombre d’appareils connectés à internet, les adresses IP sont épuisées depuis 2011. Il a donc fallu utiliser des adresses plus longues : l’**IPv6**. 

Alors que le protocole Internet de la version 4 est codé sur 32 bits et s’écrit sous forme décimale, son successeur IPv6 permet des **adresses de 128 bits**, qui sont basées sur une **écriture hexadécimale** pour des raisons de lisibilité. Cette comparaison permet de comprendre nettement que le problème central de IPv4 a été résolu : avec 128 bits, il est maintenant possible de générer bien plus **d’adresses IP uniques** qu’avec 32 bits.

Exemples:

- **Adresse IPv4 :** 203.0.120.195

- **Adresse IPv6** **:** 2001:0620:0000:0000:0211:24FF:FE80:C12C



Question 2: Calculez le nombre d’adresses IPv6 existantes.

Ce nombre est suffisamment grand pour que l’IPv6 dure jusqu’à la fin du monde.

Pour des raisons de simplicité et car l’IPv4 est toujours largement utilisé, nous utiliserons l’IPv4 dans ce TP.



**Ping**

Ping est une commande pour tester simplement le lien entre deux ordinateurs. Elle envoie plusieurs requêtes et donne les statistiques sur les réponses reçues. Le temps de réponse est la donnée la plus connue car il permet d’estimer la « rapidité » de votre connexion.

Question 3: 

a. Ouvrer sur votre ordinateur le terminal Tilix. 

b. En utilisant la commande ```ifconfig``` , trouver votre adresse ip. 

c. Demander l'adresse ip de votre voisin de classe et effectuer la commande ```ping x.x.x.x```où x.x.x.x est l'adresse ip de votre voisin. Quel est le temps moyen de réponse? 

d. Faire un ping vers google.fr, quel est  le temps moyen de réponse ? 



### Les sous-réseaux. 

Un sous-réseau est une subdivision d'un réseau de taille plus importante. Le masque de sous réseau permet de distinguer la partie de l'adresse commune à tous les appareils du sous-réseau et celle qui varie d'un appareil à l'autre. 



Par exemple 255.0.0.0 est un masque de sous-réseau (255 = 111111111). On peut également le noter /8 car les huit premiers bits sont à 1. Ainsi toutes les adresses d’un sous-réseau avec ce masque auront les mêmes 8 premiers bits.

Par exemple 126.154.168.222/8 et 126.214.25.1/8 appartiennent au même sous réseau d’adresse 126.0.0.0/8 car elles commencent par 126.

Par contre 123.201.32.57/8 n’appartient pas au même sous réseau car 123 ≠ 126.



Question 4: Déterminer les adresses des sous-réseaux des IP suivantes :

\- 14.213.3.45/8

\- 25.65.245.23/16

\- 128.226.1.24/24



Question 5: Déterminer si les adresses suivantes appartiennent au même sous-réseau :

\- 172.23.4.7/16 et 172.23.5.8/16

\- 24.2.8.127/8 et 24.23.5.52/8

\- 193.28.7.2/24 et 193.28.8.3/24



Question 6: Combien de machines peut-on trouver au maximum dans les sous-réseaux suivants ?

\- 192.168.2.0/24

\- 176.24.0.0/16

\- 10.0.0.0/8



### Filius. 

Nous allons utiliser le logiciel **Filius** pour simuler des réseaux.
Visionner la vidéo suivante avant de passer à la suite du TP. 
[prise en main de Filius](https://youtu.be/HOPPr_tRyRg)


**Premier réseau**

Le réseau le plus simple est constitué de deux ordinateurs reliés par un câble :

![](/Reseau/IMG/reseau_15.jpg)

Créez ce réseau dans Filius avec les propriétés suivantes :

\- Nom :Portable 1 ; Adresse IP : 192.168.1.1

\- Nom :Portable 2 ; Adresse IP : 192.168.1.2

Une fois votre réseau terminé, passez en mode simulation. En cliquant sur le portable 1, installez « ligne de commande » et lancez-le. Saisissez alors la commande suivante :

```ping 192.168.1.2```

Question 7: Quelle réponse obtenez vous ? 

**Deuxiéme réseau**



Pour relier plusieurs ordinateurs nous avons besoin d’un appareil supplémentaire : un **switch**.

![](/Reseau/IMG/reseau_16.jpg)

Un switch est en quelque sorte une « multiprise réseau ». On peut en utiliser beaucoup dans un réseau.



Créez le réseau ci-dessous avec Filius :

![](/Reseau/IMG/reseau_17.jpg)



\- Nom :Portable 1 ; Adresse IP : 192.168.1.1

\- Nom :Portable 2 ; Adresse IP : 192.168.1.2

\- Nom :Portable 3 ; Adresse IP : 192.168.1.3

Tester la connexion entre deux ordinateurs avec la commande ping.

Dans la simulation nous utiliserons 255.255.255.0 comme masque de sous réseau. Il nous faudra donc avoir les 3 premiers octets identiques pour des adresses du même sous-réseau.

Question 8: Quelle est l’adresse du sous réseau de votre exemple dans Filius ?

**3e réseau**



Ajoutez un switch et trois ordinateurs à votre réseau existant pour obtenir le schéma suivant :

![](/Reseau/IMG/reseau_18.jpg)



\- Nom :Portable 4 ; Adresse IP : 192.168.1.4

\- Nom :Portable 5 ; Adresse IP : 192.168.1.5

\- Nom :Portable 6 ; Adresse IP : 192.168.1.6

Vérifier que la connexion est bonne entre les portables 1 et 6.



**4e réseau**

Nous allons garder la même structure que le réseau précédent en changeant de sous réseau les trois nouveaux ordinateurs :

\- Nom :Portable 4 ; Adresse IP : 192.168.2.4

\- Nom :Portable 5 ; Adresse IP : 192.168.2.5

\- Nom :Portable 6 ; Adresse IP : 192.168.2.6

Question 9:  Tester à nouveau la connexion entre les portables 1 et 6. Que constatez-vous ?



Ce comportement est normal car pour faire communiquer deux sous-réseaux il faut un composant plus « intelligent » qu’un switch : un **routeur**.

![](/Reseau/IMG/reseau_19.jpg)

Un routeur peut servir de passerelle entre deux sous-réseaux.

Ajoutez un routeur et modifiez le câblage pour obtenir l’architecture suivante :

![](/Reseau/IMG/reseau_20.jpg)



Il faut maintenant configurer le routeur et les ordinateurs pour que tout fonctionne.

Sur le routeur :

\- carte réseau connectée à Switch 1 mettre l’IP à 192.168.1.254

\- carte réseau connectée à Switch 2 mettre l’IP à 192.168.2.254

\- dans l’onglet « général » cocher « routage automatique »

Sur les ordinateurs reliés au Switch 1 ajouter la passerelle 192.168.1.254 et sur les ordinateurs reliés au Switch 2 ajouter la passerelle 192.168.2.254 pour qu’ils sachent à qui demander pour communiquer hors de leur sous-réseau.

Question 10: Tester à nouveau la connexion entre les portables 1 et 6. Que constatez-vous ?

Question 11:  Sur l’ordinateur 1 saisissez traceroute 192.168.2.6. Que constatez vous ? 

