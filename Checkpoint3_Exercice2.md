# Exercice 2 - VM Linux

## Partie 1 - Gestion des utilisateurs

### Q.2.1.1 Sur le serveur, créer un compte pour ton usage personnel. 
![image](https://github.com/user-attachments/assets/8a24e93a-e699-4144-ab48-f46fec46fd6e)



### Q.2.1.2 Quelles préconisations proposes-tu concernant ce compte ? 


1.- Definir un mot de passe robuste avec minimum 12 caractères ; avec majuscules, minuscules, chiffres et caractères spéciaux.

2.- Désactiver l'accès root direct en SSH.

3.- Accorder des privilèges sudo uniquement si nécessaire.

4.- Activer l'authentification par clé SSH.

## Partie 2 - Configuration de SSH

### Q.2.2.1 Désactiver complètement l'accès à distance de l'utilisateur root.

Éditer le fichier sshd_config avec la commande nano /etc/ssh/sshd_config

![image](https://github.com/user-attachments/assets/e3086efb-3b49-4c08-9a77-d0c7025459da)




### Q.2.2.2 Autoriser l'accès à distance à ton compte personnel uniquement.

Éditer le fichier sshd_config avec la commande nano /etc/ssh/sshd_config

![image](https://github.com/user-attachments/assets/1b8568cb-37c8-4bbd-ab16-1a260283ffeb)


### Q.2.2.3 Mettre en place une authentification par clé valide et désactiver l'authentification par mot de passe.

![image](https://github.com/user-attachments/assets/9260bfd2-1cf0-4906-a392-302857ca07d4)

![image](https://github.com/user-attachments/assets/e8b41b26-4dfa-47f1-91ba-e2f25a692a96)

![image](https://github.com/user-attachments/assets/c04a8117-6b6a-4c54-b3fb-a9a3a4344b25)



## Partie 3 - Analyse du stockage

### Q.2.3.1 Quels sont les systèmes de fichiers actuellement montés ?

![image](https://github.com/user-attachments/assets/823401a1-a966-460f-ae78-7f2410c8213f)



### Q.2.3.2 Quel type de système de stockage ils utilisent ?
![image](https://github.com/user-attachments/assets/218049cf-1190-49f5-b771-ad69a7a354ba)


LVM
![image](https://github.com/user-attachments/assets/e404942e-a97f-413a-81c0-8d5d51fe7c85)


### Q.2.3.3  Ajouter un nouveau disque de 8,00 Gio au serveur et réparer le volume RAID

![image](https://github.com/user-attachments/assets/72e97421-9ef7-4cb0-98cf-f96f3c8c069a)

![image](https://github.com/user-attachments/assets/1d21809e-58e4-4331-9cc2-ed76313c84ac)

![image](https://github.com/user-attachments/assets/cc4ad593-7d09-4f8b-9994-660e014fb58a)

![image](https://github.com/user-attachments/assets/67a4fadd-e816-4cb6-8e7c-f6e3f150e100)

![image](https://github.com/user-attachments/assets/8a555527-1545-4276-b2db-17826de31a2c)




### Q.2.3.4 Ajouter un nouveau volume logique LVM de 2 Gio qui servira à héberger des sauvegardes. Ce volume doit être monté automatiquement à chaque démarrage dans l'emplacement par défaut : /var/lib/bareos/storage.

Création du volume logique 

![image](https://github.com/user-attachments/assets/7819115a-5ea5-4189-abd5-05cb9660d281)

Formatage du volume logique

![image](https://github.com/user-attachments/assets/ed6967aa-1c39-49cb-a563-cbf30c6d376d)

![image](https://github.com/user-attachments/assets/6f3c4ca0-64c4-4665-898c-c9ec92858095)

![image](https://github.com/user-attachments/assets/6b24150c-c193-471a-8b34-eea8d92621ff)

![image](https://github.com/user-attachments/assets/bb4d77af-4826-45c3-8f89-3466e99dab52)




### Q.2.3.5 Combien d'espace disponible reste-t-il dans le groupe de volume ?

![image](https://github.com/user-attachments/assets/c455b8e7-f01d-4bc9-9993-ddb09c2ce176)


## Partie 4 - Sauvegardes

### Q.2.4.1 Expliquer succinctement les rôles respectifs des 3 composants bareos installés sur la VM.

Bareos Director (bareos-dir) → Orchestre et planifie les sauvegardes
Bareos Storage Daemon (bareos-sd) → Stocke les sauvegardes sur un disque ou autre support
Bareos File Daemon (bareos-fd) → Lit les fichiers sur le client et les envoie au stockage


## Partie 5 - Filtrage et analyse réseau

### Q.2.5.1 Quelles sont actuellement les règles appliquées sur Netfilter ?

![image](https://github.com/user-attachments/assets/dcc59a1b-1a01-45ba-bff1-46f2f0c6f5f9)

### Q.2.5.2 Quels types de communications sont autorisées ?

Selon la sortie de la commande précédent :
* Tout trafic lié à des connexions déjà établies "ct state established,related accept".
* Tout trafic interne (localhost) "iifname "lo" accept".
* Accès SSH sur le port 22 "tcp dport 22 accept"
* Trafic ICMP en IPv4 et IPv6 " ip protocol icmp accept" et "ip6 nexthdr ipv6-icmp accept".

### Q.2.5.3 Quels types sont interdit ?

Tout le reste.

### Q.2.5.4 Sur nftables, ajouter les règles nécessaires pour autoriser bareos à communiquer avec les clients bareos potentiellement présents sur l'ensemble des machines du réseau local sur lequel se trouve le serveur.

![image](https://github.com/user-attachments/assets/71d9abd1-c7b2-435e-a614-ba8101a810ff)

## Partie 6 - Analyse de logs

### Q.2.6.1 Lister les 10 derniers échecs de connexion ayant eu lieu sur le serveur en indiquant pour chacun :

    La date et l'heure de la tentative
    L'adresse IP de la machine ayant fait la tentative

![image](https://github.com/user-attachments/assets/1b9c76e3-01d3-41ed-b1b6-a4ae07601581)




