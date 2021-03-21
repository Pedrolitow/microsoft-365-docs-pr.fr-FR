---
title: Lancer votre portail à l’aide du Programmeur de lancement du portail
ms.author: jhendr
author: jhendr
manager: pamgreen
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
description: Cet article explique comment lancer votre portail à l’aide du Programmeur de lancement du portail
ms.openlocfilehash: e39f00dbc63ae7f1dcaf907d9c67df2c1683efc6
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50926141"
---
# <a name="launch-your-portal-using-the-portal-launch-scheduler"></a>Lancer votre portail à l’aide du Programmeur de lancement du portail

Un portail est un site SharePoint sur votre intranet et qui comporte un grand nombre d’internautes qui utilisent du contenu sur le site. Le lancement de votre portail par vagues est une partie importante de la garantie que les utilisateurs ont une expérience fluide et performante d’accès à un nouveau portail SharePoint Online. 

Le lancement par vagues est un moyen clé de déployer votre portail, comme détaillé dans la planification de votre plan de déploiement de lancement de portail [dans SharePoint Online.](./planportallaunchroll-out.md?view=o365-worldwide) Le Programme de lancement du portail est conçu pour vous aider à suivre une approche de déploiement wave/progressive en gérant les redirections pour le nouveau portail. Pendant chacune des vagues, vous pouvez recueillir les commentaires des utilisateurs et surveiller les performances pendant chaque vague de déploiement. Cela a l’avantage d’introduire le portail lentement, de vous donner la possibilité de suspendre et de résoudre les problèmes avant de poursuivre la vague suivante, et de garantir finalement une expérience positive pour vos utilisateurs. 

Il existe deux types de redirection : 
- bidirectionnel : lancer un nouveau portail SharePoint Online moderne pour remplacer un portail SharePoint classique ou moderne existant 
- redirection de page temporaire : lancer un nouveau portail SharePoint Online moderne sans portail SharePoint existant

Le programme de lancement du portail est disponible uniquement pour lancer des portails SharePoint Online modernes (c’est-à-dire, des sites de communication). Les lancements doivent être programmés au moins 7 jours à l’avance. Le nombre de vagues requis est déterminé par le nombre d’utilisateurs attendu. Avant de planifier un lancement de portail, l’outil Diagnostic de page pour [SharePoint](./page-diagnostics-for-spo.md) doit être exécuté pour vérifier que la page d’accueil du portail est saine. À la fin du lancement du portail, tous les utilisateurs ayant des autorisations sur le site pourront accéder au nouveau site. 

Pour plus d’informations sur le lancement d’un portail réussi, suivez les principes, pratiques et recommandations de base détaillés dans La création, le lancement et la maintenance d’un [portail sain.](/sharepoint/portal-health) 

> [!NOTE]
> Cette fonctionnalité n’est pas disponible pour les plans Office 365 Germany, Office 365 géré par 21Vianet (Chine) ou Microsoft 365 pour le gouvernement américain.

## <a name="app-setup-and-connecting-to-sharepoint-online"></a>Configuration de l’application et connexion à SharePoint Online
1. [Téléchargez la dernière version de SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

    > [!NOTE]
    > Si vous avez installé une version antérieure de SharePoint Online Management Shell, accédez à Ajouter ou supprimer des programmes et désinstaller « SharePoint Online Management Shell ».<br>Dans la page du Centre de téléchargement, sélectionnez votre langue, puis cliquez sur le bouton Télécharger. Vous serez invité à choisir entre le téléchargement d’un fichier .msi x64 et x86. Téléchargez le fichier x64 si vous exécutez la version 64 bits de Windows ou le fichier x86 si vous exécutez la version 32 bits. En cas de doute, consultez [Quelle est la version du système d’exploitation Windows que j’utilise ?](https://support.microsoft.com/help/13443/windows-which-operating-system). Une fois le fichier téléchargé, exécutez-le, puis suivez les étapes de l'Assistant d'installation.

2. Connectez-vous à SharePoint en tant qu’[administrateur général ou administrateur SharePoint](/sharepoint/sharepoint-admin-role) dans Microsoft 365. Pour savoir comment procéder, reportez-vous à l’article [Prise en main de SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).


## <a name="view-any-existing-portal-launch-setups"></a>Afficher les configurations de lancement de portail existantes

Pour voir s’il existe des configurations de lancement de portail :

   ```PowerShell
   Get-SPOPortalLaunchWaves -LaunchSiteUrl <object> -DisplayFormat <object>
   ```

## <a name="schedule-a-portal-launch-on-the-site"></a>Planifier un lancement de portail sur le site

Le nombre de vagues requises dépend de la taille de lancement attendue. 
- Moins de 10 000 utilisateurs : 1 vague
- 10 000 à 30 000 utilisateurs : 3 vagues 
- 30 000 à 100 000 utilisateurs : 5 vagues
- Plus de 100 000 utilisateurs : 5 vagues et contactez votre équipe de compte Microsoft

### <a name="steps-for-bidirectional-redirection"></a>Étapes de redirection bidirectionnelle

La redirection bidirectionnelle implique le lancement d’un nouveau portail SharePoint Online moderne pour remplacer un portail SharePoint classique ou moderne existant. Les utilisateurs en vagues actives sont redirigés vers le nouveau site, qu’ils naviguent vers l’ancien ou le nouveau site. Les utilisateurs d’une vague non lancée qui tentent d’accéder au nouveau site sont redirigés vers l’ancien site jusqu’à ce que leur vague soit lancée. 

La redirection est uniquement prise en charge entre la page d’accueil par défaut sur l’ancien site et la page d’accueil par défaut sur le nouveau site. Si vous avez des administrateurs ou des propriétaires qui ont besoin d’accéder aux anciens et nouveaux sites sans être redirigés, assurez-vous qu’ils sont répertoriés à l’aide du `WaveOverrideUsers` paramètre.

Pour migrer les utilisateurs d’un site SharePoint existant vers un nouveau site SharePoint de manière par étape :

1. Exécutez la commande suivante pour désigner les vagues de lancement du portail.
   
   ```PowerShell
    New-SPOPortalLaunchWaves -LaunchSiteUrl <object> -RedirectionType Bidirectional -RedirectUrl <string> -ExpectedNumberOfUsers <object> -WaveOverrideUsers <object> -Waves <object>
    ```

Exemple :
   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl "https://contoso.sharepoint.com/teams/newsite" -RedirectionType Bidirectional -RedirectUrl "https://contoso.sharepoint.com/teams/oldsite" -ExpectedNumberOfUsers 10kTo30kUsers -WaveOverrideUsers "admin@contoso.com" -Waves ' 
[{Name:"Wave 1", Groups:["Viewers 1"], LaunchDateUtc:"2020/10/14"}, 
{Name:"Wave 2", Groups:["Viewers 2"], LaunchDateUtc:"2020/10/15"}, 
{Name:"Wave 3", Groups:["Viewers 3"], LaunchDateUtc:"2020/10/16"}]'
   ```

2. Validation complète. La redirection peut prendre entre 5 et 10 minutes pour terminer sa configuration dans le service. 

### <a name="steps-for-redirection-to-temporary-page"></a>Étapes de redirection vers une page temporaire

La redirection de page temporaire doit être utilisée lorsqu’il n’existe aucun portail SharePoint existant. Les utilisateurs sont dirigés vers un nouveau portail SharePoint Online moderne de manière par étape. Si un utilisateur est dans une vague qui n’a pas été lancée, il est redirigé vers une page temporaire (toute URL). 

1. Exécutez la commande suivante pour désigner les vagues de lancement du portail.
   
      ```PowerShell
    New-SPOPortalLaunchWaves -LaunchSiteUrl <object> -RedirectionType ToTemporaryPage -RedirectUrl <string> -ExpectedNumberOfUsers <object> -WaveOverrideUsers <object> -Waves <object>
    ```

Exemple :
   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl "https://contoso.sharepoint.com/teams/newsite" -RedirectionType ToTemporaryPage -RedirectUrl "https://portal.contoso.com/UnderConstruction.aspx" -ExpectedNumberOfUsers 10kTo30kUsers -WaveOverrideUsers "admin@contoso.com" -Waves ' 
[{Name:"Wave 1", Groups:["Viewers 1"], LaunchDateUtc:"2020/10/14"}, 
{Name:"Wave 2", Groups:["Viewers 2"], LaunchDateUtc:"2020/10/15"}, 
{Name:"Wave 3", Groups:["Viewers 3"], LaunchDateUtc:"2020/10/16"}]'
   ```

2. Validation complète. La redirection peut prendre entre 5 et 10 minutes pour terminer sa configuration dans le service. 

## <a name="pause-or-restart-a-portal-launch-on-the-site"></a>Suspendre ou redémarrer un lancement de portail sur le site

1. Pour interrompre un lancement du portail en cours et empêcher temporairement les progressions de vague à venir, exécutez la commande suivante :

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Pause - LaunchSiteUrl <object>
   ```
2. Vérifier que tous les utilisateurs sont redirigés vers l’ancien site. 

3. Pour redémarrer un lancement du portail qui a été suspendu, exécutez la commande suivante :

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Restart - LaunchSiteUrl <object>
   ```
   
4. Vérifier que la redirection est maintenant restaurée. 

## <a name="delete-a-portal-launch-on-the-site"></a>Supprimer un lancement de portail sur le site

1. Exécutez la commande suivante pour supprimer un lancement de portail prévu ou en cours pour un site.

   ```PowerShell
   Remove-SPOPortalLaunchWaves -LaunchSiteUrl <object>
   ```

2. Vérifier qu’aucune redirection ne se produit pour tous les utilisateurs.

## <a name="learn-more"></a>Si vous souhaitez en savoir plus
[Planification de votre plan de déploiement de lancement de portail dans SharePoint Online](./planportallaunchroll-out.md)