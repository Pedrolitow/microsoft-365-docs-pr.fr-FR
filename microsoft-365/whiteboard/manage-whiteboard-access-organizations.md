---
title: Gérer l’accès au Tableau blanc Microsoft pour votre organisation
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
description: Découvrez comment configurer le Tableau blanc Microsoft pour votre organisation dans le Centre d'administration Microsoft 365.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 1de0cd66a817a3db50b98bf6895be20184c974fc
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554580"
---
# <a name="manage-access-to-microsoft-whiteboard-for-your-organization"></a>Gérer l’accès au Tableau blanc Microsoft pour votre organisation

>[!NOTE]
> Cet article s’applique aux organisations d’entreprise ou d’éducation qui utilisent le Tableau blanc. Pour les environnements US Government GCC High, consultez [Gérer l’accès au Tableau blanc Microsoft pour les environnements GCC High](manage-whiteboard-access-gcc-high.md).

Le Tableau blanc Microsoft est un canevas de collaboration visuelle où les personnes, le contenu et les idées se rassemblent. Aujourd’hui, le tableau blanc s’exécute sur les clients Azure entreprise et Éducation. Le tableau blanc est en cours de transition pour être exécuté au-dessus de OneDrive Entreprise. Cette transition apporte de nombreuses nouvelles fonctionnalités et vous permet de créer, partager, découvrir et gérer des tableaux blancs aussi facilement que n’importe quel document Office.

Le tableau blanc est automatiquement activé pour les locataires Microsoft 365 applicables. 

Le tableau blanc est conforme aux normes mondiales, notamment les clauses soc 1, SOC 2, ISO 27001, HIPAA et modèle de l’UE. 

Les paramètres d’administration suivants sont requis pour le tableau blanc :

- Le tableau blanc doit être activé globalement dans le Centre d'administration Microsoft 365.

- L’applet <code>Set-SPOTenant -IsWBFluidEnabled</code> de commande doit être activée à l’aide de [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

>[!NOTE]
> Le déploiement de OneDrive Entreprise stockage est en cours. Lorsque vous accédez à la Centre d'administration Microsoft 365, l’option d’adhésion ou de désactivation de OneDrive Entreprise stockage est désactivée si votre locataire a déjà été transféré vers OneDrive Entreprise.

Vous pouvez contrôler l’accès au Tableau blanc de la manière suivante :

- Activez ou désactivez le tableau blanc pour l’ensemble de votre locataire à l’aide de la Centre d'administration Microsoft 365.

- Afficher ou masquer le tableau blanc pour des utilisateurs spécifiques dans des réunions à l’aide d’une stratégie de réunion Teams. Il reste visible via le web, les clients natifs et l’application onglet Teams.

- Exiger des stratégies d’accès conditionnel pour accéder au Tableau blanc à l’aide du Centre d’administration Azure Active Directory.

>[!NOTE]
> Les stratégies de réunion Teams masquent uniquement les points d’entrée du Tableau blanc ; cela n’empêche pas les utilisateurs d’utiliser le tableau blanc. Les stratégies d’accès conditionnel empêchent tout accès au Tableau blanc, mais ne masquent pas les points d’entrée.

## <a name="enable-or-disable-whiteboard"></a>Activer ou désactiver le tableau blanc

Pour activer ou désactiver le tableau blanc pour votre locataire, procédez comme suit :

1. Aller au Centre d’administration Microsoft 365.

2. Dans la page d’accueil du centre d’administration, dans la zone De recherche en haut à droite, *tapez Tableau blanc*.

3. Dans les résultats de la recherche, sélectionnez **Les paramètres du tableau blanc**.

4. Dans le panneau Tableau blanc, activez **ou désactivez le tableau blanc pour activer ou désactiver l’ensemble de votre organisation**.

5. Sélectionnez **Enregistrer**.

6. Connectez-vous à [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

7. Activez Fluid à l’aide de l’applet de commande suivante :<code>Set-SPOTenant</code>

   <pre><code class="lang-powershell">Set-SPOTenant -IsWBFluidEnabled $true</code></pre>
 
## <a name="show-or-hide-whiteboard"></a>Afficher ou masquer le tableau blanc

Pour afficher ou masquer le Tableau blanc dans les réunions, consultez [les paramètres de stratégie de réunion](/microsoftteams/meeting-policies-content-sharing). 

## <a name="prevent-access-to-whiteboard"></a>Empêcher l’accès au Tableau blanc

Pour empêcher l’accès au Tableau blanc pour des utilisateurs spécifiques, consultez [Création d’une stratégie d’accès conditionnel](/azure/active-directory/conditional-access/concept-conditional-access-policies).

## <a name="see-also"></a>Voir aussi

[Gérer les données pour le tableau blanc](manage-data-organizations.md)

[Gérer le partage pour le tableau blanc](manage-sharing-organizations.md)

[Déployer le tableau blanc sur Windows](deploy-on-windows-organizations.md)
