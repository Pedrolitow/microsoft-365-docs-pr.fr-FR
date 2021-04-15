---
title: Accéder aux données d'un ancien utilisateur et les sauvegarder
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: a6f7f9ad-e3f5-43de-ade5-e5a0d7531604
description: Découvrez comment conserver les fichiers et messages électroniques d'un employé lorsque la personne quitte votre organisation.
ms.openlocfilehash: 17911e4a4551bba07d2c2ad034941bba737dcc1d
ms.sourcegitcommit: 223a36a86753fe9cebee96f05ab4c9a144133677
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51755605"
---
# <a name="get-access-to-and-back-up-a-former-users-data"></a>Accéder aux données d'un ancien utilisateur et les sauvegarder


Lorsqu'un employé quitte votre organisation, vous souhaitez probablement accéder à ses données (documents et courriers électroniques) et les consulter, les back up ou les donner à un nouvel employé.
  
    
## <a name="access-a-former-users-onedrive-documents"></a>Accéder aux documents OneDrive d'un ancien utilisateur

Si vous supprimez la licence d'un utilisateur, mais que vous ne supprimez pas le compte, vous pouvez vous accorder l'accès au contenu du OneDrive de l'utilisateur. Si vous supprimez le compte de l'utilisateur, vous avez 30 jours par défaut pour accéder aux données OneDrive de l'ancien utilisateur. [Découvrez comment définir la rétention OneDrive pour les utilisateurs supprimés.](/onedrive/set-retention) Si vous ne [restituerez pas de](/office365/admin/add-users/restore-user) compte d'utilisateur dans ce délai, son contenu OneDrive est supprimé. 

Pour conserver les fichiers OneDrive d'un ancien utilisateur, donnez-vous d'abord accès à son OneDrive, puis déplacez les fichiers que vous souhaitez conserver. 

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-germany"

 1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

 1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez un utilisateur.

3. Dans le volet droit, sélectionnez **OneDrive.** Sous **Obtenir l'accès aux fichiers,** **sélectionnez Créer un lien vers des fichiers.**

4. Sélectionnez le lien pour ouvrir l'emplacement du fichier. Téléchargez les fichiers sur  votre ordinateur, ou sélectionnez Déplacer vers ou Copier pour les déplacer ou les copier sur votre propre OneDrive ou dans une bibliothèque partagée.  

> [!NOTE]
> Vous pouvez déplacer ou copier jusqu'à 500 Mo de fichiers et de dossiers à la fois.<br/>
> Lorsque vous déplacez ou copiez des documents qui ont un historique des versions, seule la dernière version est déplacée.  

## <a name="revoke-admin-access-to-a-users-onedrive"></a>Révoquer l'accès administrateur au OneDrive d'un utilisateur

En tant qu'administrateur global, vous pouvez vous accorder l'accès au contenu dans OneDrive d'un utilisateur, mais vous pouvez supprimer votre accès lorsque vous n'en avez plus besoin. 

 ::: moniker range="o365-worldwide"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Dans le volet gauche, sélectionnez **Centres d'administration** \> **SharePoint**. (Vous devrez peut-être sélectionner **Afficher tout** pour afficher la liste des centres d’administration.)

3. Si le Centre d'administration SharePoint classique apparaît, sélectionnez **Ouvrir** maintenant en haut de la page pour ouvrir le Centre d'administration SharePoint.

4. Dans le volet gauche, sélectionnez **Autres fonctionnalités.**

5. Sous **Profils utilisateur,** sélectionnez **Ouvrir.**

6. Sous **Personnes,** sélectionnez **Gérer les profils utilisateur.**

7. Entrez le nom de l'utilisateur et sélectionnez **Rechercher.**

8. Cliquez avec le bouton droit sur l'utilisateur, puis choisissez **Gérer les propriétaires de collections de sites.**

9. Supprimez la personne qui n'a plus besoin d'accéder aux données de l'utilisateur, puis sélectionnez **OK**.

    
## <a name="access-the-outlook-data-of-a-former-user"></a>Accéder aux données Outlook d'un ancien utilisateur

Pour enregistrer les messages électroniques, le calendrier, les tâches et les contacts de l'ancien employé, exportez les informations dans un fichier de données Outlook (.pst).
  
1. [Ajoutez l'e-mail de l'ancien](https://support.microsoft.com/office/6e27792a-9267-4aa4-8bb6-c84ef146101b) employé à votre outlook (si vous réinitialisez le mot de passe de [l'utilisateur,](reset-passwords.md)vous pouvez le définir sur quelque chose que vous connaissez uniquement.)
    
2. Dans Outlook, sélectionnez **Fichier**.
    
    ![Voici à quoi ressemble le ruban dans Outlook 2016.](../../media/d7f66ed3-9861-4521-b410-e86a58ab15a7.png)
  
3. Sélectionnez **&amp; Ouvrir exporter** \> **l'importation/exportation.**
    
    ![Commande Importer/Exporter en affichage Backstage](../../media/6013919e-d8ce-4902-b7b4-78ff4260a2f8.jpg)
  
4. Sélectionnez **Exporter vers un fichier,** puis sélectionnez **Suivant.**
    
    ![Exporter vers une option de fichier dans l'Assistant Importation et exportation](../../media/458466a0-366b-4fbf-a2db-1919412c6527.jpg)
  
5. Sélectionnez **fichier de données Outlook (.pst),** puis sélectionnez **Suivant**.
    
6. Sélectionnez le compte que vous souhaitez exporter en sélectionnant le nom ou l'adresse de messagerie, tel que Mailbox - Anne Weiler ou anne@contoso.com. Si vous souhaitez exporter tout ce qui se trouve dans votre compte,  y compris la messagerie, le calendrier, les contacts, les tâches et les notes, assurez-vous que la case à cocher Inclure les sous-foldeurs est cocher. 
    
    > [!NOTE]
    > Vous pouvez exporter un compte à la fois. Si vous souhaitez exporter plusieurs comptes, une fois qu'un compte est exporté, répétez ces étapes. 
  
    ![Boîte de dialogue Exporter le fichier de données Outlook avec le dossier supérieur sélectionné et inclure les sous-dossiers sélectionnés](../../media/ce36616f-d76d-4ce2-b517-8ac4874e0971.jpg)
  
7. Sélectionnez **Suivant**.
    
8. Sélectionnez **Parcourir** pour sélectionner l'endroit où enregistrer le fichier de données Outlook (.pst). Tapez  *un nom de fichier,* puis sélectionnez **OK** pour continuer. 
    
    > [!NOTE]
    > Si vous avez déjà utilisé l'exportation, l'emplacement du dossier précédent et le nom de fichier apparaissent. Tapez *un autre nom de fichier* avant de sélectionner **OK.** 
  
9. Si vous exportez vers un fichier de données Outlook existant (.pst), sous **Options,** spécifiez ce qu'il faut faire lors de l'exportation d'éléments qui existent déjà dans le fichier.
    
10. Sélectionnez **Terminer**.
    
Outlook commence immédiatement l'exportation, sauf si un nouveau fichier de données Outlook (.pst) est créé ou qu'un fichier protégé par mot de passe est utilisé.
  
   - Si vous créez un fichier de données Outlook (.pst), un mot de passe facultatif peut vous aider à protéger le fichier. Lorsque la boîte de dialogue Créer  un fichier de  données **Outlook** s'affiche, tapez le mot de passe dans les zones Mot de passe et Vérifier le mot de passe, puis sélectionnez **OK**.  Dans la boîte de dialogue Mot de passe du fichier de données **Outlook,** tapez le mot de *passe,* puis sélectionnez **OK.**
    
  - Si vous exportez vers un fichier de données Outlook (.pst) existant protégé par mot de passe, dans la boîte de dialogue Mot de passe du fichier de données **Outlook,** tapez le mot de *passe,* puis sélectionnez **OK.**
    
Découvrez comment exporter ou sauvegarder le courrier électronique, les contacts et le calendrier dans un fichier [.pst Outlook](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) dans Outlook 2010. 
  
  
  > [!NOTE]
  > Par défaut, votre courrier électronique est disponible hors connexion pendant une période de 12 mois. Si nécessaire, voir comment augmenter [les données disponibles hors connexion.](/outlook/troubleshoot/mailboxes/only-subset-items-synchronized)
 
## <a name="give-another-user-access-to-a-former-users-email"></a>Accorder à un autre utilisateur l'accès à la messagerie d'un ancien utilisateur 

Pour accorder à un autre employé l'accès aux messages électroniques, au calendrier, aux tâches et aux contacts de l'ancien employé, importez les informations dans la boîte de réception Outlook d'un autre employé.

> [!NOTE]
> Vous pouvez également convertir la boîte aux lettres de [l'ancien](/office365/admin/email/convert-user-mailbox-to-shared-mailbox) utilisateur en boîte aux lettres partagée ou envoyer le courrier électronique [d'un](/office365/admin/add-users/remove-former-employee#forward-a-former-employees-email-to-another-employee-or-convert-to-a-shared-mailbox)ancien employé à un autre employé.

  
1. Dans Outlook, go to **File** \> **Open &amp; Export** \> **Import/Export**.
    
    L'Assistant Importation et exportation démarre.
    
2. Sélectionnez **Importer à partir d'un autre programme ou fichier,** puis sélectionnez **Suivant**.
    
    ![Assistant Importation et exportation](../../media/15cdd674-cd7b-492c-8e93-992cfa890f26.jpg)
  
3. Sélectionnez **fichier de données Outlook (.pst)** et sélectionnez **Suivant**.
    
4. Accédez au fichier .pst à importer.
    
5. Sous **Options,** choisissez la façon dont vous souhaitez traiter les doublons
    
6. Sélectionnez **Suivant**.
    
7. Si un mot de passe a été affecté au fichier de données Outlook (.pst), entrez le mot de passe, puis sélectionnez **OK**.
    
8. Définissez les options d'importation d'éléments. Les paramètres par défaut n'ont généralement pas besoin d'être modifiés.
    
9. Sélectionnez **Terminer**.

> [!NOTE]
> Les étapes restent les mêmes pour accéder aux données OneDrive et de messagerie d'un utilisateur existant.
    
> [!TIP]
> Si vous souhaitez importer ou restaurer uniquement quelques éléments à partir d'un fichier de données Outlook (.pst), vous pouvez ouvrir le fichier de données Outlook. Ensuite, dans le volet de navigation, faites glisser les éléments des dossiers de fichiers de données Outlook vers vos dossiers Outlook existants. 
  
  
## <a name="related-articles"></a>Articles connexes
[Supprimer un ancien employé d'Office 365](remove-former-employee.md)

[Ajouter et supprimer des administrateurs sur un compte OneDrive](/sharepoint/manage-user-profiles#add-and-remove-admins-for-a-users-onedrive)

[Restaurer un OneDrive supprimé](/onedrive/restore-deleted-onedrive)
  
[Rétention et suppression sur OneDrive](/onedrive/retention-and-deletion)
