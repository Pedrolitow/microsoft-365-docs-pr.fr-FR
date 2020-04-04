---
title: Accéder aux données d'un ancien utilisateur et les sauvegarder
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: a6f7f9ad-e3f5-43de-ade5-e5a0d7531604
description: Découvrez comment conserver les fichiers et les e-mails d’un employé lorsque la personne quitte votre organisation.
ms.openlocfilehash: 11c946e5c242b05fea3a15b9427f36029c61082f
ms.sourcegitcommit: ff62dd99fa0d4e780da25dc622f93ddc8f7f95a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "43142562"
---
# <a name="get-access-to-and-back-up-a-former-users-data"></a>Accéder aux données d'un ancien utilisateur et les sauvegarder


Quand un employé quitte votre organisation, vous voudrez probablement accéder à ses données (documents et courriers électroniques) et les consulter, les sauvegarder ou les transmettre à un nouvel employé.
  
    
## <a name="access-a-former-users-onedrive-documents"></a>Accéder aux documents OneDrive d’un ancien utilisateur

Si vous supprimez la licence d’un utilisateur, mais que vous ne supprimez pas le compte, vous pouvez vous accorder l’accès au contenu dans le OneDrive de l’utilisateur. Si vous supprimez le compte de l’utilisateur, vous disposez de 30 jours par défaut pour accéder aux données OneDrive de l’ancien utilisateur. [Découvrez comment configurer la rétention OneDrive pour les utilisateurs supprimés](/onedrive/set-retention). Si vous ne [restaurez pas un compte d’utilisateur](/office365/admin/add-users/restore-user) pendant ce temps, son contenu OneDrive est supprimé. 

Pour conserver les fichiers OneDrive d’un ancien utilisateur, commencez par vous accorder l’accès à son OneDrive, puis déplacez les fichiers que vous souhaitez conserver. 

::: moniker range="o365-worldwide"

> [!NOTE]
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.  
    
2. Sélectionnez un utilisateur.

3. Dans le volet droit, sélectionnez **OneDrive**. Sous **accéder à des fichiers**, sélectionnez **créer un lien vers des fichiers**.

4. Sélectionnez le lien pour ouvrir l’emplacement du fichier. Téléchargez les fichiers sur votre ordinateur ou sélectionnez **déplacer vers** ou **copier** vers pour les déplacer ou les copier vers votre propre OneDrive ou une bibliothèque partagée. 

> [!NOTE]
> Vous pouvez déplacer ou copier jusqu’à 500 Mo de fichiers et de dossiers à la fois.<br/>
> Lorsque vous déplacez ou copiez des documents qui ont un historique des versions, seule la dernière version est déplacée.  

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez un utilisateur.

3. Dans le volet droit, développez **paramètres OneDrive**, puis en regard de **accès**, sélectionnez **fichiers Access**.

4. Sélectionnez le lien pour ouvrir l’emplacement du fichier. Téléchargez les fichiers sur votre ordinateur ou sélectionnez **déplacer vers** ou **copier** vers pour les déplacer ou les copier vers votre propre OneDrive ou une bibliothèque partagée. 

> [!NOTE]
> Vous pouvez déplacer ou copier jusqu’à 500 Mo de fichiers et de dossiers à la fois.<br/>
> Lorsque vous déplacez ou copiez des documents qui ont un historique des versions, seule la dernière version est déplacée.  

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

2. Sélectionnez un utilisateur.

3. Dans le volet droit, développez **paramètres OneDrive**, puis en regard de **accès**, sélectionnez **fichiers Access**.

4. Sélectionnez le lien pour ouvrir l’emplacement du fichier. Téléchargez les fichiers sur votre ordinateur ou sélectionnez **déplacer vers** ou **copier** vers pour les déplacer ou les copier vers votre propre OneDrive ou une bibliothèque partagée.  

> [!NOTE]
> Vous pouvez déplacer ou copier jusqu’à 500 Mo de fichiers et de dossiers à la fois.<br/>
> Lorsque vous déplacez ou copiez des documents qui ont un historique des versions, seule la dernière version est déplacée.  

::: moniker-end
    


## <a name="revoke-admin-access-to-a-users-onedrive"></a>Révoquer l’accès administrateur au OneDrive d’un utilisateur

En tant qu’administrateur général, vous pouvez vous accorder l’accès au contenu dans OneDrive d’un utilisateur, mais vous pouvez supprimer votre accès lorsque vous n’en avez plus besoin. 

::: moniker range="o365-worldwide"

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration</a> en tant qu’administrateur général ou administrateur SharePoint. 

    Si vous recevez un message indiquant que vous n’êtes pas autorisé à accéder au centre d’administration, vous ne disposez pas des autorisations d’administrateur dans votre organisation.

::: moniker-end

::: moniker range="o365-germany"

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a> en tant qu’administrateur général ou administrateur SharePoint.

    Si vous recevez un message indiquant que vous n’êtes pas autorisé à accéder au centre d’administration, vous ne disposez pas des autorisations d’administrateur dans votre organisation.

::: moniker-end

::: moniker range="o365-21vianet"

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a> en tant qu’administrateur général ou administrateur SharePoint.

    Si vous recevez un message indiquant que vous n’êtes pas autorisé à accéder au centre d’administration, vous ne disposez pas des autorisations d’administrateur dans votre organisation.

::: moniker-end

2. Dans le volet gauche, sélectionnez **centres** \> d’administration **SharePoint**. (Vous devrez peut-être sélectionner **Afficher tout** pour afficher la liste des centres d’administration.)

3. Si la version classique du Centre d’administration SharePoint s’affiche, en haut de la page, sélectionnez **Ouvrir maintenant** pour ouvrir la nouvelle version du Centre d’administration SharePoint.

4. Dans le volet gauche, sélectionnez **plus de fonctionnalités**.

5. Sous **profils utilisateur**, sélectionnez **ouvrir**.

6. Sous **personnes**, sélectionnez **gérer les profils utilisateur**.

7. Entrez le nom de l’utilisateur et sélectionnez **Rechercher**.

8. Cliquez avec le bouton droit sur l’utilisateur, puis choisissez **gérer les propriétaires de collection de sites**.

9. Supprimez la personne qui n’a plus besoin d’accéder aux données de l’utilisateur, puis sélectionnez **OK**.

    
## <a name="access-the-outlook-data-of-a-former-user"></a>Accéder aux données Outlook d’un ancien utilisateur

Pour enregistrer les messages électroniques, le calendrier, les tâches et les contacts de l’ancien employé, exportez les informations vers un fichier de données Outlook (. pst).
  
1. [Ajoutez le message électronique de l’ancien employé](https://support.office.com/article/6e27792a-9267-4aa4-8bb6-c84ef146101b.aspx) à votre Outlook (si vous [réinitialisez le mot de passe de l’utilisateur](reset-passwords.md), vous pouvez le définir sur une valeur qui ne vous indique que).
    
2. Dans Outlook, sélectionnez **fichier**.
    
    ![Voici à quoi ressemble le ruban dans Outlook 2016.](../../media/d7f66ed3-9861-4521-b410-e86a58ab15a7.png)
  
3. Sélectionnez **ouvrir &amp; ** l' \> **importation/exportation**de l’exportation.
    
    ![Commande d’importation/exportation en mode Backstage](../../media/6013919e-d8ce-4902-b7b4-78ff4260a2f8.jpg)
  
4. Sélectionnez **Exporter vers un fichier**, puis cliquez sur **suivant**.
    
    ![Option Exporter vers un fichier dans l’Assistant d’importation et d’exportation](../../media/458466a0-366b-4fbf-a2db-1919412c6527.jpg)
  
5. Sélectionnez **fichier de données Outlook (. pst)**, puis **suivant**.
    
6. Sélectionnez le compte que vous souhaitez exporter en sélectionnant le nom ou l’adresse de messagerie, par exemple, Weiler ou anne@contoso.com. Si vous souhaitez exporter tout le contenu de votre compte, y compris le courrier, le calendrier, les contacts, les tâches et les notes, vérifiez que la case à cocher **inclure les sous-dossiers** est activée. 
    
    > [!NOTE]
    > Vous pouvez exporter un compte à la fois. Si vous souhaitez exporter plusieurs comptes, après l’exportation d’un compte, répétez ces étapes. 
  
    ![Boîte de dialogue Exporter le fichier de données Outlook avec le dossier supérieur sélectionné et inclure les sous-dossiers activés](../../media/ce36616f-d76d-4ce2-b517-8ac4874e0971.jpg)
  
7. Sélectionnez **Suivant**.
    
8. Sélectionnez **Parcourir** pour sélectionner l’emplacement d’enregistrement du fichier de données Outlook (. pst). Tapez un *nom de fichier*, puis cliquez sur **OK** pour continuer. 
    
    > [!NOTE]
    > Si vous avez utilisé l’exportation avant, l’emplacement du dossier et le nom de fichier précédents apparaissent. Tapez un *autre nom de fichier* avant de sélectionner **OK**. 
  
9. Si vous effectuez l’exportation vers un fichier de données Outlook (. pst) existant, sous **options**, spécifiez les actions à effectuer lors de l’exportation d’éléments qui existent déjà dans le fichier.
    
10. Sélectionnez **Terminer**.
    
Outlook commence l’exportation immédiatement sauf si un nouveau fichier de données Outlook (. pst) est créé ou si un fichier protégé par mot de passe est utilisé.
  
   - Si vous créez un fichier de données Outlook (. pst), un mot de passe facultatif peut aider à protéger le fichier. Lorsque la boîte de dialogue **créer un fichier de données Outlook** s’affiche, tapez le *mot de passe* dans les zones **mot** de passe et **confirmer le mot de passe** , puis cliquez sur **OK**. Dans la boîte de dialogue **mot de passe du fichier de données Outlook** , tapez le *mot de passe*, puis cliquez sur **OK**.
    
  - Si vous effectuez une exportation vers un fichier de données Outlook (. pst) qui est protégé par mot de passe, dans la boîte de dialogue **mot de passe du fichier de données Outlook** , tapez le *mot de passe*, puis cliquez sur **OK**.
    
Découvrez comment [exporter ou sauvegarder des courriers électroniques, des contacts et des calendriers dans un fichier. pst Outlook](https://support.office.com/article/14252b52-3075-4e9b-be4e-ff9ef1068f91.aspx) dans Outlook 2010. 
  
  
  > [!NOTE]
  > Par défaut, votre courrier électronique est disponible hors connexion pendant une période de 12 mois. Si nécessaire, reportez-vous à la rubrique Comment [augmenter les données disponibles hors connexion](Https://docs.microsoft.com/outlook/troubleshoot/mailboxes/only-subset-items-synchronized).
 
## <a name="give-another-user-access-to-a-former-users-email"></a>Accorder à un autre utilisateur l’accès à l’adresse de messagerie d’un ancien utilisateur 

Pour accorder l’accès aux messages électroniques, au calendrier, aux tâches et aux contacts de l’ancien employé à un autre employé, importez les informations dans la boîte de réception Outlook d’un autre employé.

> [!NOTE]
> Vous pouvez également [convertir la boîte aux lettres de l’ancien utilisateur en boîte aux lettres partagée](https://docs.microsoft.com/office365/admin/email/convert-user-mailbox-to-shared-mailbox) ou [transférer le courrier électronique d’un ancien employé à un autre employé](https://docs.microsoft.com/office365/admin/add-users/remove-former-employee#forward-a-former-employees-email-to-another-employee-or-convert-to-a-shared-mailbox).

  
1. Dans Outlook, accédez à **fichier** \> **: &amp; ouvrir exporter** \> l' **importation/exportation**.
    
    Cette opération démarre l’Assistant d’importation et d’exportation.
    
2. Sélectionnez **Importer à partir d’un autre programme ou fichier**, puis cliquez sur **suivant**.
    
    ![Assistant d’importation et d’exportation](../../media/15cdd674-cd7b-492c-8e93-992cfa890f26.jpg)
  
3. Sélectionnez **fichier de données Outlook (. pst)**, puis cliquez sur **suivant**.
    
4. Accédez au fichier. pst que vous souhaitez importer.
    
5. Sous **options**, choisissez le mode de traitement des doublons.
    
6. Sélectionnez **Suivant**.
    
7. Si un mot de passe a été attribué au fichier de données Outlook (. pst), entrez le mot de passe, puis sélectionnez **OK**.
    
8. Définir les options d’importation des éléments. Il n’est généralement pas nécessaire de modifier les paramètres par défaut.
    
9. Sélectionnez **Terminer**.

> [!NOTE]
> Les étapes restent les mêmes pour accéder aux données de messagerie et à OneDrive d’un utilisateur existant.
    
> [!TIP]
> Si vous souhaitez importer ou restaurer uniquement quelques éléments à partir d’un fichier de données Outlook (. pst), vous pouvez ouvrir le fichier de données Outlook. Ensuite, dans le volet de navigation, faites glisser les éléments des dossiers du fichier de données Outlook vers vos dossiers Outlook existants. 
  
  
## <a name="related-articles"></a>Articles connexes
[Supprimer un ancien employé d'Office 365](remove-former-employee.md)

[Ajouter et supprimer des administrateurs sur un compte OneDrive](/sharepoint/manage-user-profiles#add-and-remove-admins-for-a-users-onedrive)

[Restaurer un OneDrive supprimé](/onedrive/restore-deleted-onedrive)
  
[Rétention et suppression de OneDrive](/onedrive/retention-and-deletion)
  
