---
title: Gérer l’accès au Tableau blanc Microsoft pour les environnements GCC
ms.author: v-jdeweese
author: johnddeweese
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.service: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Découvrez comment activer, désactiver et gérer des données de tableau blanc.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 46a4c6db8755f7ee2928828453518acdb2a2eb36
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67597607"
---
# <a name="manage-access-to-microsoft-whiteboard-for-gcc-environments"></a>Gérer l’accès au Tableau blanc Microsoft pour les environnements GCC

>[!NOTE]
> Ces conseils s’appliquent aux environnements cloud de la communauté du gouvernement des États-Unis (GCC).

Le tableau blanc Microsoft sur OneDrive Entreprise est activé par défaut pour les locataires Microsoft 365 applicables. Il peut être activé ou désactivé à l’échelle du locataire. Vous devez également vous assurer que **Microsoft Whiteboard Services** est activé dans les **applications d’entreprise** du **Centre** >  d’administration Azure Active Directory.

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

- Afficher ou masquer le tableau blanc pour des utilisateurs spécifiques dans des réunions à l’aide d’une stratégie de réunion Microsoft Teams. Il reste visible via le web, les clients natifs et l’application onglet Teams.

- Exiger des stratégies d’accès conditionnel pour accéder au Tableau blanc à l’aide du Centre d’administration Azure Active Directory.

>[!NOTE]
> La stratégie de réunion Teams masque uniquement les points d’entrée du Tableau blanc. Cela n’empêche pas les utilisateurs d’utiliser le tableau blanc. Les stratégies d’accès conditionnel empêchent l’accès au Tableau blanc, mais ne masquent pas les points d’entrée.

## <a name="enable-or-disable-whiteboard"></a>Activer ou désactiver le tableau blanc

Pour activer ou désactiver le tableau blanc pour votre locataire, procédez comme suit : 

1. Utilisez le [module PowerShell SharePoint Online](/microsoft-365/enterprise/manage-sharepoint-online-with-microsoft-365-powershell) pour activer ou désactiver toutes les expériences Fluid dans votre locataire Microsoft 365.

2. Connectez-vous à [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

3. Activez Fluid à l’aide de l’applet de commande suivante :<code>Set-SPOTenant</code>

   <pre><code class="lang-powershell">Set-SPOTenant -IsWBFluidEnabled $true</code></pre>

La modification doit prendre environ 60 minutes pour s’appliquer à l’ensemble de votre location. Si vous ne voyez pas cette option, vous devez mettre à jour le module.

## <a name="show-or-hide-whiteboard"></a>Afficher ou masquer le tableau blanc

Pour afficher ou masquer le Tableau blanc dans les réunions, consultez [les paramètres de stratégie de réunion](/microsoftteams/meeting-policies-content-sharing).

## <a name="see-also"></a>Voir aussi

[Gérer les données pour le Tableau blanc - GCC](manage-data-gcc.md)

[Gérer le partage pour le tableau blanc - GCC](manage-sharing-gcc.md)

[Gérer les clients pour le Tableau blanc - GCC](manage-clients-gcc.md)