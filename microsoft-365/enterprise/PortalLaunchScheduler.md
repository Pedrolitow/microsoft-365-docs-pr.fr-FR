---
title: Lancer votre portail à l’aide du planificateur de lancement du portail
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
description: Cet article explique comment lancer votre portail à l’aide du planificateur de lancement de portail
ms.openlocfilehash: e5e5850fa7e74f3e3b342e9bb28d17f65b491664
ms.sourcegitcommit: 474bd6a86c3692d11fb2c454591c89029ac5bbd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "49356666"
---
# <a name="launch-your-portal-using-the-portal-launch-scheduler"></a>Lancer votre portail à l’aide du planificateur de lancement du portail

Un portail est un site SharePoint sur votre intranet et qui comporte un grand nombre d’internautes qui utilisent du contenu sur le site. Le lancement de votre portail dans les vagues est une partie importante de la façon de s’assurer que les utilisateurs ont une expérience fluide et performante qui accèdent à un nouveau portail SharePoint Online. 

Le lancement dans les vagues est un moyen clé de déployer votre portail, comme indiqué dans [la planification de votre plan de déploiement du lancement de portail dans SharePoint Online](https://docs.microsoft.com/microsoft-365/Enterprise/Planportallaunchroll-out?view=o365-worldwide). Le planificateur de lancement de portail est conçu pour vous aider à suivre une approche de déploiement Wave/phase en gérant les redirections pour le nouveau portail. Pendant chacune des vagues, vous pouvez recueillir les commentaires des utilisateurs et surveiller les performances pendant chaque vague de déploiement. Cela présente l’avantage d’introduire lentement le portail, ce qui vous permet de suspendre et de résoudre les problèmes avant de passer à la prochaine vague, et de garantir une expérience positive pour vos utilisateurs. 

Il existe deux types de redirection : 
- bidirectionnel : lancer un nouveau portail SharePoint Online moderne pour remplacer un portail classique ou moderne SharePoint existant 
- redirection temporaire des pages : lancer un nouveau portail SharePoint Online moderne sans portail SharePoint existant

Le planificateur de lancement de portail est disponible uniquement pour lancer des portails SharePoint Online modernes (c’est-à-dire des sites de communication). Les lancements doivent être planifiés au moins 7 jours à l’avance. Le nombre d’ondes requises est déterminé par le nombre d’utilisateurs attendu. Avant de planifier le lancement d’un portail, l' [outil Diagnostics de la page pour SharePoint](https://aka.ms/perftool) doit être exécuté pour vérifier que la page d’accueil du portail est intègre. À la fin du lancement du portail, tous les utilisateurs disposant d’autorisations sur le site seront en mesure d’accéder au nouveau site. 

Pour plus d’informations sur le lancement d’un portail réussi, suivez les principes de base, les pratiques et les recommandations détaillés dans [Creating, lancement and Maintaining a successful Portal](https://docs.microsoft.com/sharepoint/portal-health). 

> [!NOTE]
> Cette fonctionnalité n’est pas disponible pour Office 365 Germany, Office 365 géré par 21Vianet (Chine) ou Microsoft 365.

## <a name="app-setup-and-connecting-to-sharepoint-online"></a>Installation de l’application et connexion à SharePoint Online
1. [Téléchargez la dernière version de SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

    > [!NOTE]
    > Si vous avez installé une version antérieure de SharePoint Online Management Shell, accédez à Ajouter ou supprimer des programmes et désinstaller « SharePoint Online Management Shell ».<br>Dans la page du Centre de téléchargement, sélectionnez votre langue, puis cliquez sur le bouton Télécharger. Vous serez invité à choisir entre le téléchargement d’un fichier .msi x64 et x86. Téléchargez le fichier x64 si vous exécutez la version 64 bits de Windows ou le fichier x86 si vous exécutez la version 32 bits. En cas de doute, consultez [Quelle est la version du système d’exploitation Windows que j’utilise ?](https://support.microsoft.com/help/13443/windows-which-operating-system). Une fois le fichier téléchargé, exécutez-le, puis suivez les étapes de l'Assistant d'installation.

2. Connectez-vous à SharePoint en tant qu’[administrateur général ou administrateur SharePoint](/sharepoint/sharepoint-admin-role) dans Microsoft 365. Pour savoir comment procéder, reportez-vous à l’article [Prise en main de SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).


## <a name="view-any-existing-portal-launch-setups"></a>Afficher les configurations de lancement de portail existantes

Pour voir s’il existe des configurations de lancement de portail existantes :

   ```PowerShell
   Get-SPOPortalLaunchWaves -LaunchSiteUrl <object> -DisplayFormat <object>
   ```

## <a name="schedule-a-portal-launch-on-the-site"></a>Planifier un lancement de portail sur le site

Le nombre d’ondes requises dépend de la taille de lancement attendue. 
- Moins de 10 000 utilisateurs : 1 vague
- 10 000 à 30k utilisateurs : 3 vagues 
- 30k + 100 000 utilisateurs : 5 ondulations
- Plus de 100 000 utilisateurs : 5 ondulations et contacter votre équipe de compte Microsoft

### <a name="steps-for-bidirectional-redirection"></a>Étapes de la redirection bidirectionnelle

La redirection bidirectionnelle implique le lancement d’un nouveau portail SharePoint Online moderne pour remplacer un portail classique ou moderne SharePoint existant. Les utilisateurs des ondes actives seront redirigés vers le nouveau site, qu’ils naviguaient vers l’ancien ou le nouveau site. Les utilisateurs d’une vague non lancée qui tentent d’accéder au nouveau site sont redirigés vers l’ancien site jusqu’à ce que leur vague soit lancée. 

Si vous avez des administrateurs ou des propriétaires qui ont besoin d’accéder aux anciens et aux nouveaux sites sans être redirigés, vérifiez qu’ils sont répertoriés à l’aide du `WaveOverrideUsers` paramètre. Nous prenons uniquement en charge la redirection entre la page d’accueil par défaut sur l’ancien site et la page d’accueil par défaut sur le nouveau site.

Pour migrer des utilisateurs à partir d’un site SharePoint existant vers un nouveau site SharePoint de manière intermédiaire :

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

2. Validation complète. La redirection peut prendre 5-10 minutes pour terminer sa configuration au sein du service. 

### <a name="steps-for-redirection-to-temporary-page"></a>Étapes de la redirection vers la page temporaire

La redirection de page temporaire doit être utilisée lorsqu’il n’existe aucun portail SharePoint existant. Les utilisateurs sont dirigés vers un nouveau portail SharePoint Online moderne de manière intermédiaire. Si un utilisateur est dans une vague qui n’a pas été lancée, il est redirigé vers une page temporaire (n’importe quelle URL). 

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

2. Validation complète. La redirection peut prendre 5-10 minutes pour terminer sa configuration au sein du service. 
   - `New-SPOPortalLaunchWaves  -LaunchSiteUrl "https://*.sharepoint.com/sites/newsite" -RedirectionType Bidirectional -RedirectUrl "https://*.sharepoint.com/sites/oldsite" -ExpectedNumberOfUsers LessThan10kUsers -WaveOverrideUsers "*@microsoft.com" -Waves ' [{Name:"Wave 1", Groups:["Viewers SG1"], LaunchDateUtc:"2020/10/14"}, {Name:"Wave 2", Groups:["Viewers SG2"], LaunchDateUtc:"2020/10/15"}]' -IsTesting $true`

## <a name="pause-or-restart-a-portal-launch-on-the-site"></a>Suspendre ou redémarrer un lancement de portail sur le site

1. Pour suspendre le lancement d’un portail en cours et empêcher temporairement les progrès à venir, exécutez la commande suivante :

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Pause - LaunchSiteUrl <object>
   ```
2. Vérifiez que tous les utilisateurs sont redirigés vers l’ancien site. 

3. Pour redémarrer un lancement de portail suspendu, exécutez la commande suivante :

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Restart - LaunchSiteUrl <object>
   ```
   
4. Vérifiez que la redirection est maintenant restaurée. 

## <a name="delete-a-portal-launch-on-the-site"></a>Supprimer un lancement de portail sur le site
1. Créer une vague de lancement de portail.
  - `New-SPOPortalLaunchWaves  -LaunchSiteUrl "https://*.sharepoint.com/sites/NewSite" -RedirectionType ToTemporaryPage -RedirectUrl "https://*.sharepoint.com/sites/OldSite" -ExpectedNumberOfUsers From10kTo30kUsers -WaveOverrideUsers *@microsoft.com -Waves [{Name:"Wave 1", Groups:["Viewers SG1"], LaunchDateUtc:"2020/10/14"}, {Name:"Wave 2", Groups:["Viewers SG2"], LaunchDateUtc:"2020/10/15"}]' -IsTesting $true`

2. Exécutez la commande suivante pour supprimer un lancement de portail planifié ou en cours pour un site.

   ```PowerShell
   Remove-SPOPortalLaunchWaves -LaunchSiteUrl <object>
   ```

3. Vérifiez qu’aucune redirection ne se produit pour tous les utilisateurs.

## <a name="learn-more"></a>En savoir plus
[Planification de votre plan de déploiement de lancement de portail dans SharePoint Online](https://docs.microsoft.com/microsoft-365/Enterprise/Planportallaunchroll-out)
