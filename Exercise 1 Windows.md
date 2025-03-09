
# Partie 1 - Gestion des utilisateurs

## Q.1.1.1 
1. Aller dans AD Users and computers
2. Chercher la OU de Kelly Rhameur
3. Cloner l’utilisateur en mettant les information de Lionel Lemarchand
![imagen](https://github.com/user-attachments/assets/ca865ded-c85a-4259-940d-ac348acc8f25)



## Q.1.1.2 
- Clic droit sur LabUsers pour en avoir une nouvelle OU et la appeler DeactivatedUsers, glisser déposer. En cliquant le bouton droit sur l’utilisateur on aura l’option Désactiver.
![imagen](https://github.com/user-attachments/assets/adadbf9c-470c-461d-92f8-72d6a9804a0b)


## Q.1.1.3 
![imagen](https://github.com/user-attachments/assets/7eed6611-1cf8-4e41-91f8-fa8da5e38f52)



## Q.1.1.4 - Gestion des dossiers individuels
- Créer le dossier individuel de Lionel Lemarchand. Archiver le dossier de Kelly Rhameur.
![Captura de pantalla 2025-03-09 233431](https://github.com/user-attachments/assets/facbe7cc-102c-4973-8c9c-53871845950b)

  
   
# Partie 2 - Restriction utilisateurs

## Q.1.2.1 
![Captura de pantalla 2025-03-07 095952](https://github.com/user-attachments/assets/22158205-c378-42cd-9e06-24d551b12659)


## Q.1.2.2 

![Captura de pantalla 2025-03-07 100152](https://github.com/user-attachments/assets/46cfc87a-26d3-4cfc-9ece-70b200523879)

## Q.1.2.3 
![Captura de pantalla 2025-03-07 100152](https://github.com/user-attachments/assets/43240458-e148-4c19-8ec0-d285abfc12ab)


# Partie 3 - Lecteurs réseaux

## Q.1.3.1  Création d'une GPO "Drive-Mount" pour monter les lecteurs E: et F:

Accéder à la Gestion des stratégies de groupe (GPO)
- Ouvrir **Group Policy Management** 
- Créer une nouvelle **GPO** nommée **"Drive-Mount"**.
- Lier cette GPO à l'OU contenant les utilisateurs ou ordinateurs concernés.

Configurer le mappage des lecteurs réseau
- Modifier la GPO "Drive-Mount".
- Naviguer vers :  
  **User Configuration** → **Preferences** → **Windows Settings** → **Drive Maps**.
- Clic droit → **New** → **Mapped Drive**.

Ajouter le lecteur E:
- **Action** : Create  
- **Location** : `\\Serveur\PartageE`  
- **Reconnect** : Coché  
- **Drive Letter** : `E:`  
- **Connect as** : Laisser vide (utilise les identifiants de l'utilisateur)  
- **Common** → Cocher "Run in logged-on user's security context".

Ajouter le lecteur F:
- Répéter les étapes précédentes en changeant :
  - **Location** : `\\Serveur\PartageF`
  - **Drive Letter** : `F:`


