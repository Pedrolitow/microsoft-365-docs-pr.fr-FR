---
title: Déploiement d’un site d’équipe SharePoint Online isolé
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/30/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: Utilisez ce guide de déploiement étape par étape pour créer et configurer un site d’équipe SharePoint Online isolé dans Microsoft Office 365.
ms.openlocfilehash: f9e8482238c7da4d10b6299b0f8a997734edbb13
ms.sourcegitcommit: 474bd6a86c3692d11fb2c454591c89029ac5bbd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "49356906"
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a>Déploiement d’un site d’équipe SharePoint Online isolé

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


 **Résumé :** Découvrez comment déployer un nouveau site d’équipe SharePoint Online isolé en suivant ces instructions détaillées.
  
Cet article est un guide de déploiement détaillé pour créer et configurer un site d’équipe SharePoint Online isolé dans Microsoft Office 365. Pour cela, vous devez utiliser les trois groupes SharePoint par défaut et les niveaux d’autorisation correspondants (un groupe d’accès Azure Active Directory (AD) pour chaque niveau d’accès).
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a>Phase 1 : création et remplissage des groupes d’accès au site d’équipe

Au cours de cette phase, vous allez créer les trois groupes d’accès basés sur Azure AD pour les trois groupes SharePoint par défaut et les remplir avec les comptes d’utilisateur appropriés.
  
> [!NOTE]
> Pour réaliser les étapes suivantes, vous devez avoir créé tous les comptes d’utilisateur nécessaires et leur avoir affecté les licences appropriées. Dans le cas contraire, ajoutez-les et attribuez-leur des licences avant de passer à l’étape 1. 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a>Étape 1 : liste des administrateurs SharePoint Online du site

Choisissez les comptes d’utilisateur des administrateurs SharePoint Online pour le site d’équipe isolé.
  
Si vous gérez des comptes d’utilisateur et des groupes via Microsoft 365 et que vous souhaitez utiliser Windows PowerShell, effectuez une liste de leurs noms d’utilisateur principaux (UPN) (exemple UPN : belindan@contoso.com).
  
### <a name="step-2-list-the-members-for-the-site"></a>Étape 2 : liste des membres du site

Choisissez les comptes d’utilisateur des membres du site d’équipe isolé, c’est-à-dire ceux qui collaboreront sur les ressources stockées sur le site.
  
Si vous gérez des comptes d’utilisateur et des groupes via Microsoft 365 et que vous souhaitez utiliser PowerShell, créez une liste de leur UPN. S’il existe un grand nombre de membres du site, vous pouvez enregistrer la liste de noms UPN dans un fichier texte et tous les ajouter avec une seule commande PowerShell.
  
### <a name="step-3-list-the-viewers-for-the-site"></a>Étape 3 : liste des visiteurs du site

Choisissez les comptes d’utilisateur des visiteurs du site d’équipe isolé, c’est-à-dire ceux qui peuvent afficher les ressources stockées sur le site sans pouvoir les modifier ou collaborer directement sur leur contenu.
  
Si vous gérez des comptes d’utilisateur et des groupes via Microsoft 365 et que vous souhaitez utiliser PowerShell, créez une liste de leur UPN. S’il existe un grand nombre de membres du site, vous pouvez enregistrer la liste de noms UPN dans un fichier texte et tous les ajouter avec une seule commande PowerShell.
  
Les visiteurs du site peuvent comprendre des membres de l’équipe de direction, du service juridique ou de plusieurs services.
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a>Étape 4 : création des trois groupes d’accès du site dans Azure AD

Vous devez créer les groupes d’accès suivants dans Azure AD :
  
- Administrateurs du site (qui contient la liste de l’étape 1)
    
- Membres du site (qui contient la liste de l’étape 2)
    
- Visiteurs du site (qui contient la liste de l’étape 3)
    
1. Dans votre navigateur, accédez au portail Azure [https://portal.azure.com](https://portal.azure.com) et connectez-vous avec les informations d’identification d’un compte qui a été affecté au rôle administrateur de gestion des utilisateurs ou administrateur de la société.
    
2. Dans le portail Azure, cliquez sur **Azure Active Directory > Groupes**.
    
3. Dans le panneau **Groupes - Tous les groupes**, cliquez sur **+ Nouveau groupe**.
    
4. Sur le **nouveau** panneau de groupe :
    
    - Sélectionnez **Sécurité** dans **Type de groupe**.

    - Tapez le nom du groupe dans **nom**.

    - Tapez une description du groupe dans **Description du groupe**.

    - Sélectionnez **Affecté** dans le champ **Type d’appartenance**.
    
5. Cliquez sur **Créer** et fermez le panneau **Groupe**.
    
6. Répétez les étapes 3-5 pour vos autres groupes.
    
> [!NOTE]
> Vous devez utiliser le portail Azure pour créer les groupes afin que les fonctionnalités Office soient activées. Si un site SharePoint Online isolé est par la suite configuré comme un site hautement confidentiel avec une étiquette Azure information protection pour chiffrer des fichiers et attribuer des autorisations à des groupes spécifiques, les groupes autorisés doivent avoir été créés avec les fonctionnalités Office activées. Vous ne pouvez pas modifier le paramètre fonctionnalités Office d’un groupe Azure AD une fois qu’il a été créé. 
  
Voici la configuration obtenue avec les trois groupes d’accès au site.
  
![Les trois groupes d’accès pour votre déploiement d’un site SharePoint Online isolé.](../../media/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a>Étape 5. Ajouter les comptes d’utilisateur aux groupes d’accès

Procédez comme suit :
  
1. Ajoutez la liste des utilisateurs de l’étape 1 au groupe d’accès Administrateurs du site
    
2. Ajoutez la liste des utilisateurs de l’étape 2 au groupe d’accès Membres du site
    
3. Ajoutez la liste des utilisateurs de l’étape 3 au groupe d’accès Visiteurs du site
    
Si vous gérez des comptes d’utilisateur et des groupes par le biais des services de domaine Active Directory (AD DS), ajoutez des utilisateurs aux groupes d’accès appropriés en utilisant vos procédures de gestion des utilisateurs et des groupes AD DS normales et attendez la synchronisation avec votre abonnement Microsoft 365.
  
Si vous gérez des comptes d’utilisateur et des groupes via Office 365, vous pouvez utiliser le centre d’administration Microsoft 365 ou PowerShell. Si vous avez des noms de groupe en double pour tous les groupes d’accès, vous devez utiliser le centre d’administration Microsoft 365.
  
Pour le centre d’administration Microsoft 365, connectez-vous à l’aide d’un compte d’utilisateur auquel a été attribué le rôle administrateur de compte d’utilisateur ou administrateur de société et utilisez des groupes pour ajouter les comptes d’utilisateur et les groupes d’utilisateurs appropriés aux groupes d’accès appropriés.
  
Pour PowerShell, [Connectez-vous d’abord avec le module Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/microsoft-365/enterprise/connect-to-microsoft-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Ensuite, utilisez le bloc de commandes suivant pour ajouter un compte d’utilisateur individuel à un groupe d’accès :
  
```powershell
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```
Si vous avez stocké les UPN des comptes d’utilisateur des groupes d’accès dans un fichier texte, vous pouvez exécuter le bloc de commandes PowerShell suivant pour les ajouter tous en même temps :
  
```powershell
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

Pour PowerShell, utilisez le bloc de commandes suivant pour ajouter un groupe individuel à un groupe d’accès :
  
```powershell
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

Voici les résultats que vous devriez obtenir :
  
- Le groupe Azure AD administrateurs du site contient les comptes d’utilisateur ou les groupes d’administrateurs de site
    
- Le groupe Azure AD membres du site contient les comptes d’utilisateur ou les groupes de membres du site.
    
- Le groupe Azure AD visiteurs du site contient les comptes d’utilisateur ou les groupes qui peuvent uniquement afficher le contenu du site.
    
Validez la liste des membres du groupe pour chaque groupe d’accès avec le centre d’administration Microsoft 365 ou avec le bloc de commandes PowerShell suivant :
  
```powershell
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

Voici la configuration obtenue avec les trois groupes d’accès au site renseignés avec des comptes d’utilisateur ou des groupes.
  
![Les trois groupes d’accès renseignés avec les comptes d’utilisateur.](../../media/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a>Phase 2 : création et configuration du site d’équipe isolé

Au cours de cette phase, vous allez créer le site SharePoint Online isolé et configurer les niveaux d’autorisation SharePoint Online par défaut pour utiliser vos nouveaux groupes d’accès Azure AD. Par défaut, les nouveaux sites d’équipe incluent un groupe Microsoft 365 et d’autres ressources associées, mais dans ce cas, nous allons créer un site d’équipe sans groupe Microsoft 365. Cela permet de gérer les autorisations entièrement via SharePoint.
  
Commencez par créer le site d’équipe SharePoint Online en suivant ces étapes.
  
1. Connectez-vous au centre d’administration Microsoft 365 avec un compte qui sera également utilisé pour administrer le site d’équipe SharePoint Online (un administrateur SharePoint Online). Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.microsoft.com/office/e9eb7d51-5430-4929-91ab-6157c5a050b4).

2. Dans le centre d’administration 365 de Microsoft, sous **centres d’administration**, cliquez sur **SharePoint**.

3. Dans le centre d’administration SharePoint, développez **sites** , puis cliquez sur **sites actifs**.

4. Cliquez sur **créer**, puis choisissez **autres options**.

5. Dans la liste **choisir un modèle** , choisissez **site d’équipe**.
   
6. Dans **nom du site**, tapez un nom pour le site d’équipe. 
    
7. Dans **administrateur principal**, tapez le compte avec lequel vous vous connectez.
 
8. Cliquez sur **Terminer**.
    
Ensuite, dans le nouveau site d’équipe SharePoint Online, configurez les autorisations.
  
1. Dans la barre d’outils, cliquez sur l’icône Paramètres, puis cliquez sur **Paramètres du site**.

2. Sous **partage du site**, cliquez sur **modifier la façon dont les membres peuvent partager**.

3. Choisissez les **seuls propriétaires de site peuvent partager des fichiers, des dossiers et le site**.

4. Définissez la valeur **autoriser les demandes d’accès** sur **désactivé**.

5. Cliquez sur **Enregistrer**.
    
6. Dans le volet **autorisations** , cliquez sur **paramètres d’autorisations avancés**.
    
7. Dans l’onglet **autorisations** de votre navigateur, cliquez sur **\<site name> membres** de la liste.
    
8. Dans **Utilisateurs et groupes**, cliquez sur **Nouveau**.
    
9. Dans la boîte de dialogue **Partager**, saisissez le nom du groupe d’accès Membres du site, sélectionnez-le, puis cliquez sur **Partager**.
    
10. Cliquez sur le bouton de retour de votre navigateur.
    
11. Cliquez sur **\<site name> propriétaires** dans la liste.
    
12. Dans **Utilisateurs et groupes**, cliquez sur **Nouveau**.
    
13. Dans la boîte de dialogue **Partager**, saisissez le nom du groupe d’accès Administrateurs du site, sélectionnez-le, puis cliquez sur **Partager**.
    
14. Cliquez sur le bouton de retour de votre navigateur.
    
15. Cliquez sur **\<site name> visiteurs** de la liste.
    
16. Dans **Utilisateurs et groupes**, cliquez sur **Nouveau**.
    
17. Dans la boîte de dialogue **Partager**, saisissez le nom du groupe d’accès Visiteurs du site, sélectionnez-le, puis cliquez sur **Partager**.
    
18. Fermez l’onglet **Autorisations** de votre navigateur.
    
Voici les résultats que vous devez escompter :
  
- Le groupe SharePoint **\<site name> propriétaires** contient le groupe d’accès administrateurs du site, dans lequel tous les membres ont le niveau d’autorisation **contrôle total** .
    
- Le groupe SharePoint **\<site name> membres** contient le groupe d’accès membres du site, dans lequel tous les membres ont le niveau d’autorisation **modifier** .
    
- Le groupe SharePoint **\<site name> visiteurs** contient le groupe d’accès visiteurs du site, dans lequel tous les membres ont le niveau d’autorisation **lecture** .
    
- L’option permettant aux membres d’inviter d’autres membres ou non membres à demander l’accès au site est désactivée.
    
Voici la configuration obtenue avec les trois groupes SharePoint pour le site configuré pour utiliser les trois groupes d’accès, qui sont renseignés avec les comptes d’utilisateur ou les groupes Azure AD.
  
![La configuration finale de votre site SharePoint Online isolé avec des groupes d’accès et des comptes d’utilisateurs.](../../media/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
Comme vous êtes membres de l’un des groupes d’accès, vous et les membres du site pouvez désormais collaborer sur les ressources du site.
  
## <a name="next-step"></a>Étape suivante

Si vous avez besoin de modifier les membres du groupe d’accès du site ou de créer un dossier de documents avec des autorisations personnalisées, consultez la rubrique [Manage an isolated SharePoint Online team site](manage-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Voir aussi

[Sites d’équipe SharePoint Online isolés](isolated-sharepoint-online-team-sites.md)
  
[Conception d'un site d'équipe SharePoint Online isolé](design-an-isolated-sharepoint-online-team-site.md)
  
[Gestion d’un site d’équipe SharePoint Online isolé](manage-an-isolated-sharepoint-online-team-site.md)
  



