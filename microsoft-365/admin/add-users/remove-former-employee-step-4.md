---
title: 'Étape 4 : donner à un autre employé l’accès OneDrive données Outlook données'
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- m365solution-removeemployee
search.appverid:
- BCS160
- MET150
- MOE150
description: Suivez les étapes de cet article pour accorder à un autre employé l’accès aux données de OneDrive et Outlook de l’ancien employé.
ms.openlocfilehash: 8825ffa78412bd9f8de60a18edc2bfac73f7bae1
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62520462"
---
# <a name="step-4---give-another-employee-access-to-onedrive-and-outlook-data"></a>Étape 4 : donner à un autre employé l’accès OneDrive données Outlook données

Lorsqu’un employé quitte votre organisation, vous pouvez accéder à ses données OneDrive et Outlook, les back up et choisir de les donner à un autre employé.
  
## <a name="access-a-former-users-onedrive-documents"></a>Accéder aux documents d’un ancien OneDrive utilisateur

Si vous supprimez la licence d’un utilisateur, mais que vous ne supprimez pas le compte, vous pouvez vous accorder l’accès au contenu dans le compte de l’OneDrive. Si vous supprimez le compte de l’utilisateur, vous avez 30 jours par défaut pour accéder aux données de l’OneDrive utilisateur. [Découvrez comment définir le OneDrive rétention des utilisateurs supprimés](/onedrive/set-retention). Si vous ne [restituerez pas de compte d’utilisateur](/office365/admin/add-users/restore-user) dans ce délai, son contenu OneDrive est supprimé.

Pour conserver les fichiers OneDrive d’un ancien utilisateur, donnez-vous d’abord accès à leurs OneDrive, puis déplacez les fichiers que vous souhaitez conserver.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez un utilisateur.

3. Dans la page des propriétés utilisateur, **sélectionnez OneDrive**. Sous **Obtenir l’accès aux fichiers**, **sélectionnez Créer un lien vers des fichiers**.

4. Sélectionnez le lien pour ouvrir l’emplacement du fichier. Téléchargez les fichiers sur votre ordinateur, ou  sélectionnez Déplacer  vers ou Copier pour les déplacer ou les copier dans votre propre OneDrive ou dans une bibliothèque partagée.

> [!NOTE]
> Vous pouvez déplacer ou copier jusqu’à 500 Mo de fichiers et de dossiers à la fois.<br/>
> Lorsque vous déplacez ou copiez des documents qui ont un historique des versions, seule la dernière version est déplacée.  

Vous pouvez également accorder l’accès à un autre utilisateur pour accéder au compte d’un ancien OneDrive.

1. Connectez-vous au Centre <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">d’administration</a> en tant qu’administrateur global ou SharePoint administrateur.

    Si vous recevez un message vous  that you don’t have permission to access the admin center, then you don’t have administrator permissions in your organization.

2. Dans le volet gauche, sélectionnez Centres **d’administration** \> **SharePoint**. (Vous devrez peut-être sélectionner **Afficher tout** pour afficher la liste des centres d’administration.)

3. Si l’SharePoint d’administration classique s’affiche,  sélectionnez Ouvrir maintenant en haut de la page pour ouvrir SharePoint’administration.

4. Dans le volet gauche, sélectionnez **Autres fonctionnalités**.

5. Sous **Profils utilisateur**, sélectionnez **Ouvrir**.

6. Sous **Personnes**, sélectionnez **Gérer les profils utilisateur**.

7. Entrez le nom de l’ancien employé et sélectionnez **Rechercher**.

8. Cliquez avec le bouton droit sur l’utilisateur, puis choisissez **Gérer les propriétaires de collections de sites**.

9. Ajoutez l’utilisateur aux **administrateurs de collection de sites** et sélectionnez **OK**.

10. L’utilisateur peut désormais accéder au compte de l’ancien employé OneDrive l’URL OneDrive’utilisateur. 

### <a name="revoke-admin-access-to-a-users-onedrive"></a>Révoquer l’accès administrateur au compte d’un OneDrive

Vous pouvez vous accorder l’accès au contenu dans le OneDrive d’un utilisateur, mais vous pouvez supprimer votre accès lorsque vous n’en avez plus besoin.

1. Connectez-vous au Centre <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">d’administration</a> en tant qu’administrateur global ou SharePoint administrateur.

    Si vous recevez un message vous  that you don’t have permission to access the admin center, then you don’t have administrator permissions in your organization.

2. Dans le volet gauche, sélectionnez Centres **d’administration** \> **SharePoint**. (Vous devrez peut-être sélectionner **Afficher tout** pour afficher la liste des centres d’administration.)

3. Si l’SharePoint d’administration classique s’affiche,  sélectionnez Ouvrir maintenant en haut de la page pour ouvrir SharePoint’administration.

4. Dans le volet gauche, sélectionnez **Autres fonctionnalités**.

5. Sous **Profils utilisateur**, sélectionnez **Ouvrir**.

6. Sous **Personnes**, sélectionnez **Gérer les profils utilisateur**.

7. Entrez le nom de l’utilisateur et sélectionnez **Rechercher**.

8. Cliquez avec le bouton droit sur l’utilisateur, puis choisissez **Gérer les propriétaires de collections de sites**.

9. Supprimez la personne qui n’a plus besoin d’accéder aux données de l’utilisateur, puis sélectionnez **OK**.

## <a name="access-the-outlook-data-of-a-former-user"></a>Accéder aux Outlook données d’un ancien utilisateur

Pour enregistrer les messages électroniques, le calendrier, les tâches et les contacts de l’ancien employé, exportez les informations dans Outlook fichier de données (.pst).
  
1. [Ajoutez l’e-mail de l’ancien](https://support.microsoft.com/office/6e27792a-9267-4aa4-8bb6-c84ef146101b) employé à votre Outlook (si vous réinitialisez le mot de passe de [l’utilisateur](reset-passwords.md), vous pouvez le définir sur quelque chose que vous connaissez uniquement.)

2. Dans Outlook, sélectionnez **Fichier**.

    ![Voici à quoi ressemble le ruban dans Outlook 2016.](../../media/d7f66ed3-9861-4521-b410-e86a58ab15a7.png)
  
3. **Sélectionnez Ouvrir &amp; l’Import/Export**\>.

    ![Import/Export commande en affichage Backstage.](../../media/6013919e-d8ce-4902-b7b4-78ff4260a2f8.jpg)
  
4. **Sélectionnez Exporter vers un fichier**, puis Sélectionnez **Suivant**.

    ![Exporter vers une option de fichier dans l’Assistant Importation et exportation.](../../media/458466a0-366b-4fbf-a2db-1919412c6527.jpg)
  
5. Sélectionnez **Fichier de données Outlook (.pst)**, puis cliquez sur **Suivant**.

6. Sélectionnez le compte que vous souhaitez exporter en sélectionnant le nom ou l’adresse de messagerie, tel que Mailbox - Anne Weiler ou anne@contoso.com. Si vous souhaitez exporter tout ce qui se trouve dans votre compte, y compris la messagerie, le calendrier, les contacts,  les tâches et les notes, assurez-vous que la case à cocher Inclure les sous-foldeurs est cocher.

    > [!NOTE]
    > Vous pouvez exporter un compte à la fois. Si vous souhaitez exporter plusieurs comptes, une fois qu’un compte est exporté, répétez ces étapes.
  
    ![Exporter Outlook boîte de dialogue Fichier de données avec le dossier supérieur sélectionné et Inclure les sous-dossiers cochés.](../../media/ce36616f-d76d-4ce2-b517-8ac4874e0971.jpg)
  
7. Sélectionnez **Suivant**.

8. **Sélectionnez Parcourir** pour sélectionner l’endroit où enregistrer Outlook fichier de données (.pst). Tapez  *un nom de fichier*, puis sélectionnez **OK** pour continuer.

    > [!NOTE]
    > Si vous avez déjà utilisé l’exportation, l’emplacement du dossier précédent et le nom de fichier apparaissent. Tapez  *un autre nom de fichier*  avant de sélectionner **OK**.
  
9. Si vous exportez vers un fichier de données Outlook existant (.pst), sous **Options**, spécifiez ce qu’il faut faire lors de l’exportation d’éléments qui existent déjà dans le fichier.

10. Sélectionnez **Terminer**.

Outlook l’exportation commence immédiatement, sauf si un nouveau fichier de données Outlook (.pst) est créé ou qu’un fichier protégé par mot de passe est utilisé.
  
- Si vous créez un fichier de données Outlook (.pst), un mot de passe facultatif peut vous aider à protéger le fichier. Lorsque la **boîte de dialogue Créer Outlook** données s’affiche, tapez le  mot de passe  dans les  zones Mot de passe et Vérifier le mot de passe, puis sélectionnez **OK**. Dans la **boîte Outlook mot de passe du** fichier de données, tapez le mot *de passe,* puis sélectionnez **OK**.

- Si vous exportez vers un fichier de données Outlook (.pst) existant protégé par mot de passe, dans la boîte de dialogue Mot de passe du fichier de données **Outlook**, tapez le mot de *passe, puis* sélectionnez **OK**.

Découvrez comment exporter [ou sauvegarder le courrier électronique, les contacts et le calendrier vers Outlook fichier .pst](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) Outlook 2010.

  > [!NOTE]
  > Par défaut, votre courrier électronique est disponible hors connexion pendant une période de 12 mois. Si nécessaire, voir comment augmenter [les données disponibles hors connexion](/outlook/troubleshoot/mailboxes/only-subset-items-synchronized).

### <a name="give-another-user-access-to-a-former-users-email"></a>Accorder à un autre utilisateur l’accès à la messagerie d’un ancien utilisateur

Pour accorder à un autre employé l’accès aux messages électroniques, au calendrier, aux tâches et aux contacts de l’ancien employé, importez les informations dans la boîte de réception Outlook’un autre employé.

> [!NOTE]
> Vous pouvez également [convertir la boîte aux lettres de l’ancien](/office365/admin/email/convert-user-mailbox-to-shared-mailbox) utilisateur en boîte aux lettres partagée ou envoyer le courrier électronique [d’un ancien employé à un autre employé](/office365/admin/add-users/remove-former-employee#forward-a-former-employees-email-to-another-employee-or-convert-to-a-shared-mailbox).

1. In Outlook, go to **File** \> **Open &amp; Export** \> **Import/Export**.

    L’Assistant Importation et exportation démarre.

2. Sélectionnez **Importer depuis un autre programme ou fichier**, puis cliquez sur **Suivant**.

    ![Assistant Importation et exportation.](../../media/15cdd674-cd7b-492c-8e93-992cfa890f26.jpg)
  
3. **Sélectionnez Outlook fichier de données (.pst)** et sélectionnez **Suivant**.

4. Accédez au fichier .pst à importer.

5. Sous **Options**, choisissez la façon dont vous souhaitez traiter les doublons

6. Sélectionnez **Suivant**.

7. Si un mot de passe a été affecté au fichier de données Outlook (.pst), entrez le mot de passe, puis sélectionnez **OK**.

8. Définissez les options d’importation d’éléments. Les paramètres par défaut n’ont généralement pas besoin d’être modifiés.

9. Sélectionnez **Terminer**.

> [!NOTE]
> Les étapes restent les mêmes pour accéder aux données de messagerie OneDrive d’un utilisateur existant.

> [!TIP]
> Si vous souhaitez importer ou restaurer uniquement quelques éléments à partir d’un fichier de données Outlook (.pst), vous pouvez ouvrir le Outlook de données. Ensuite, dans le volet de navigation, faites glisser les éléments de Outlook fichiers de données vers vos dossiers Outlook existants.

### <a name="cancel-outlook-meetings"></a>Annuler Outlook réunions

Veillez à annuler toutes les réunions que l’ancien utilisateur avait dans son calendrier. Cela permet aux utilisateurs de supprimer les réunions créées par l’ancien utilisateur.

Si la personne a eu des réunions qui ont réservé des équipements ou des salles, elle ne peut pas être réservée tant que ces réunions n’ont pas été annulées. [Lisez Supprimer un rendez-vous ou une réunion](https://support.microsoft.com/office/delete-an-appointment-or-a-meeting-2703bfdb-9a07-4396-be3b-a9f79438455b) pour les étapes.

## <a name="related-content"></a>Contenu associé

[Ajouter et supprimer des administrateurs sur un compte OneDrive client](/sharepoint/manage-user-profiles#add-and-remove-admins-for-a-users-onedrive) (article)

[Restaurer une OneDrive](/onedrive/restore-deleted-onedrive) supprimée (article)

[OneDrive rétention et suppression (](/onedrive/retention-and-deletion)article)

[Partager des fichiers et des dossiers OneDrive](https://support.microsoft.com/office/share-onedrive-files-and-folders-9fcc2f7d-de0c-4cec-93b0-a82024800c07)
