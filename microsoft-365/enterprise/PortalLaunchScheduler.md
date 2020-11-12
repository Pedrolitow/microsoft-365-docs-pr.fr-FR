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
ms.openlocfilehash: 929492742fd140654bd13be8165093ee10647c6d
ms.sourcegitcommit: da34ac08c7d029c2c42d4428d0bb03fd57c448be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "48999578"
---
# <a name="launch-your-portal-using-the-portal-launch-scheduler"></a>Lancer votre portail à l’aide du planificateur de lancement du portail

Vous pouvez lancer votre portail à l’aide du planificateur de lancement de portail en validant d’abord la capacité de l’administrateur client à configurer une vague pour un nouveau portail. L’administrateur peut ensuite valider une redirection de demandes en fonction de l’existence d’un utilisateur dans les ondes actives.

Pour plus d’informations sur le lancement d’un portail réussi, suivez les principes de base, les pratiques et les recommandations détaillés dans la rubrique [création, lancement et maintenance d’un portail intègre](https://go.microsoft.com/fwlink/?linkid=2105838). 

## <a name="app-setup"></a>Installation de l’application
1. Désinstallez-le si vous disposez `Microsoft.Online.SharePoint.PowerShell` d’un ordinateur existant dans le panneau de configuration.
2. Sur PowerShell `Install-Module -Name Microsoft.Online.SharePoint.PowerShell` .

## <a name="connect-to-sharepoint-online"></a>Se connecter à SharePoint Online
1. Ouvrez [SharePoint Online Management Shell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) dans Windows.
2. Connectez-vous à votre client en tant qu’administrateur.
   - `Connect-SPOService -Url "https://*-admin.sharepoint.com" -Credential "username”`
3.  Entrez votre mot de passe lorsque vous y êtes invité.

## <a name="command-to-get-an-existing-setup"></a>Commande pour obtenir une configuration existante

Pour afficher les configurations de lancement de portail existantes :

1. Transmettre `Get-SPOPortalLaunchWaves  -LaunchSiteUrl  https://*.sharepoint.com/sites/newsite` .
2. Transmettez le paramètre supplémentaire `-DisplayFormat Raw` si vous souhaitez voir la collection Wave au format RAW.

## <a name="commands-for-bi-directional-redirection"></a>Commandes de redirection bidirectionnelle

Pour migrer les anciens utilisateurs de site vers le nouveau site de manière intermédiaire :

1. Créez des vagues de lancement de portail.
   - Ceci s’applique uniquement lors de la phase de test de la version préliminaire.
   - Pour tester immédiatement l’impact de la modification, assurez-vous que la première vague `LaunchDateUtc` est définie sur la date actuelle. Si vous ne fournissez pas cet indicateur, vous obtenez un message d’erreur. Cette erreur se produit car les lancements en production doivent être planifiés au moins 7 jours à l’avance.

  `New-SPOPortalLaunchWaves  -LaunchSiteUrl "https://*.sharepoint.com/sites/newsite" -RedirectionType Bidirectional -RedirectUrl "https://*.sharepoint.com/sites/oldsite" -ExpectedNumberOfUsers LessThan10kUsers -WaveOverrideUsers "*@microsoft.com" -Waves ' [{Name:"Wave 1", Groups:["Viewers SG1"], LaunchDateUtc:"2020/10/14"}, {Name:"Wave 2", Groups:["Viewers SG2"], LaunchDateUtc:"2020/10/15"}]' -IsTesting $true`

2. Validation complète.
  - La redirection peut prendre jusqu’à 5 minutes pour terminer sa configuration au sein du service ; par conséquent, veuillez patienter avant de poursuivre.
  - Si vous vous connectez avec l’utilisateur spécifié en tant que `WaveOverrideUsers` , aucune modification n’est apportée. Vous devez rester sur le site sur lequel vous avez accédé.
  - Connectez-vous avec un utilisateur qui fait partie des *visionneuses SG1*.
    - Accédez à l’ancien site et vous devez être redirigé vers le nouveau site.
    - Accédez au nouveau site et restez sur le nouveau site.
    - Connectez-vous avec l’utilisateur dans les *visionneuses SG2* et accédez à l’ancien site et restez sur l’ancien site.
    - Accédez au nouveau site et vous devez être redirigé vers l’ancien site.

3. Suspendre le lancement du portail.
  - Si vous devez suspendre les ondes de lancement, vous pouvez les suspendre pendant « x » jours. La définition `Status` de la suspension de l’indicateur empêche toute progression des vagues à venir. 
  - `Set-SPOPortalLaunchWaves -Status Pause - LaunchSiteUrl  https://*.sharepoint.com/sites/NewSite`.
  - Cela permet de valider que tous les utilisateurs sont redirigés vers l’ancien site.

4. Redémarrez la progression du lancement du portail. 
  - `Set-SPOPortalLaunchWaves -Status Restart - LaunchSiteUrl  https://*.sharepoint.com/sites/NewSite`.
  - Vérifiez que la redirection est maintenant restaurée.

5. Supprimer un portail lancer le programme d’installation.
  - `Remove-SPOPortalLaunchWaves -LaunchSiteUrl https://*.sharepoint.com/sites/NewSite`.
  - Vérifiez qu’aucune redirection ne se produit pour tous les utilisateurs.

## <a name="commands-for-redirection-to-temporary-page"></a>Commandes de redirection vers une page temporaire

Suivez ces étapes si vous n’avez pas de site précédent et si vous ne souhaitez pas que les utilisateurs qui ne sont pas dans l’atterrissage se déplacent sur la nouvelle page de portail.

Pour créer une page temporaire dans l’un des sites :

1. Créer une vague de lancement de portail.
   - `New-SPOPortalLaunchWaves  -LaunchSiteUrl "https://*.sharepoint.com/sites/NewSite" -RedirectionType ToTemporaryPage -RedirectUrl "https://*.sharepoint.com/sites/OldSite" -ExpectedNumberOfUsers From10kTo30kUsers -WaveOverrideUsers *@microsoft.com -Waves [{Name:"Wave 1", Groups:["Viewers SG1"], LaunchDateUtc:"2020/10/14"}, {Name:"Wave 2", Groups:["Viewers SG2"], LaunchDateUtc:"2020/10/15"}]' -IsTesting $true`

2. Validation complète.

  - Patientez cinq minutes avant de poursuivre, car l’action peut prendre jusqu’à cinq minutes.
  - Connectez-vous à l’utilisateur qui fait partie des *observateurs SG1* et :
     - Accédez au nouveau site, et vous devez rester sur le nouveau site.
     - Naviguez jusqu’à la page Temp, et vous devez rester sur la page Temp.
  - Connectez-vous à l’utilisateur qui fait partie des *visionneuses SG2* et :
     - Naviguez jusqu’au nouveau site, et vous devez être redirigé vers la page Temp.
     - Accédez à la page Temp et restez sur la page Temp.

3. Supprimer un portail lancer le programme d’installation.
  - `Remove-SPOPortalLaunchWaves - LaunchSiteUrl  https://*.sharepoint.com/sites/NewSite`.
  - Vérifiez qu’aucune redirection ne se produit pour tous les utilisateurs.

## <a name="learn-more"></a>En savoir plus
[Planification de votre plan de déploiement de lancement de portail dans SharePoint Online](https://docs.microsoft.com/microsoft-365/Enterprise/Planportallaunchroll-out)