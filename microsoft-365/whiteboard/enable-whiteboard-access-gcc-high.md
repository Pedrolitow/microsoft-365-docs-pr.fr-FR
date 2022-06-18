---
title: Activer et gérer l’accès aux Microsoft Whiteboard pour les environnements Cloud de la communauté du secteur public High
ms.author: chucked
author: chuckedmonson
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Découvrez comment activer, désactiver et gérer des données de tableau blanc.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: e99e1cd92038f02e38dcd28c8f94400344f53fe7
ms.sourcegitcommit: b0b1be67de8f40b199bb9b51eb3568e59377e93a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2022
ms.locfileid: "66159766"
---
# <a name="enable-and-manage-access-to-microsoft-whiteboard-for-gcc-high-environments"></a>Activer et gérer l’accès aux Microsoft Whiteboard pour les environnements Cloud de la communauté du secteur public High

>[!NOTE]
> Ce guide s’applique aux environnements us Cloud de la communauté du secteur public (Cloud de la communauté du secteur public) High.

Microsoft Whiteboard sur OneDrive Entreprise est activée par défaut pour les locataires Microsoft 365 applicables. Il peut être activé ou désactivé à l’échelle du locataire. Vous devez également vous assurer que **Microsoft Whiteboard Services** est activé dans les **applications** Azure Active Directory centre  > **d’administration** Enterprise.

Les URL suivantes sont requises :

- 'https://*.office365.us/'
- 'https://login.microsoftonline.us/'
- 'https://graph.microsoft.us/'
- 'https://graph.microsoftazure.us/'
- 'https://admin.onedrive.us'
- 'https://shell.cdn.office.net/'
- 'https://config.ecs.gov.teams.microsoft.us'
- 'https://tb.events.data.microsoft.com/'

Vous pouvez contrôler l’accès au Tableau blanc de la manière suivante :

- Activez ou désactivez le tableau blanc pour l’ensemble de votre locataire à l’aide du [module PowerShell SharePoint Online](/microsoft-365/enterprise/manage-sharepoint-online-with-microsoft-365-powershell).

- Afficher ou masquer le tableau blanc pour des utilisateurs spécifiques dans des réunions à l’aide d’une stratégie de réunion Teams. Il reste visible via le web, les clients natifs et l’application d’onglet Teams.

- Exiger des stratégies d’accès conditionnel pour accéder au Tableau blanc à l’aide du centre d’administration Azure Active Directory.

>[!NOTE]
> Le tableau blanc sur OneDrive Entreprise n’apparaît pas dans le Centre d'administration Microsoft 365. Teams stratégie de réunion masque uniquement les points d’entrée du tableau blanc, elle n’empêche pas les utilisateurs d’utiliser le tableau blanc. Les stratagèmes d’accès conditionnel empêchent l’accès au Tableau blanc, mais ne masquent pas les points d’entrée.

## <a name="enable-or-disable-whiteboard"></a>Activer ou désactiver le tableau blanc

Pour activer ou désactiver le tableau blanc pour votre locataire, procédez comme suit : 

1. Utilisez le [module PowerShell SharePoint Online](/microsoft-365/enterprise/manage-sharepoint-online-with-microsoft-365-powershell) pour activer ou désactiver toutes les expériences Fluid sur votre client Microsoft 365.

2. Connecter à [SharePoint PowerShell en ligne](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

3. Activez Fluid à l’aide de l’applet de commande suivante :<code>Set-SPOTenant</code>

   <pre><code class="lang-powershell">Set-SPOTenant -IsWBFluidEnabled $true</code></pre>

La modification doit prendre environ 60 minutes pour s’appliquer à l’ensemble de votre location. Si vous ne voyez pas cette option, vous devez mettre à jour le module.

>[!NOTE]
> Par défaut, le tableau blanc est activé. S’il a été désactivé dans les applications d’entreprise Azure Active Directory, le tableau blanc sur OneDrive Entreprise ne fonctionnera pas.

## <a name="show-or-hide-whiteboard"></a>Afficher ou masquer le tableau blanc

Pour afficher ou masquer le Tableau blanc dans les réunions, consultez [les paramètres de stratégie de réunion](/microsoftteams/meeting-policies-content-sharing).

## <a name="see-also"></a>Voir aussi

[Gérer les données pour le tableau blanc - Cloud de la communauté du secteur public Élevé](manage-data-gcc-high.md)

[Gérer le partage pour le tableau blanc - Cloud de la communauté du secteur public Élevé](manage-sharing-gcc-high.md)

[Gérer les clients pour le Tableau blanc - Cloud de la communauté du secteur public Élevé](manage-clients-gcc-high.md)




