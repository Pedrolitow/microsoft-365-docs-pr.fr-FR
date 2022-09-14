---
title: Limites du site portail moderne SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 10/9/2019
audience: Admin
ms.topic: interactive-tutorial
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
description: Découvrez les recommandations en matière de performances pour les sites modernes dans SharePoint Online, telles que la limitation des appels à SharePoint et aux points de terminaison externes.
ms.openlocfilehash: 07a94786a5c3a7cc58a170b5f838962b08577e06
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67693364"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>Limites du site portail moderne SharePoint Online

Cet article fournit des recommandations en matière de performances pour les sites portail modernes dans SharePoint Online. Suivez les instructions de cet article pour optimiser les performances du site portail moderne et éviter les problèmes de performances courants.

## <a name="performance-considerations-for-modern-portal-sites"></a>Considérations relatives aux performances pour les sites du portail moderne

Du point de vue de l’optimisation des performances, certaines caractéristiques rendent les sites portail modernes uniques. La principale différence entre les sites de collaboration et de portail dans SharePoint Online est l’échelle. Les sites du portail sont généralement censés servir plus de pages vues à un plus grand nombre d’utilisateurs que les sites de collaboration, et sont susceptibles de contenir plus de contenu statique et moins de ressources modifiables. En outre, l’architecture des sites modernes diffère des sites classiques, car la majeure partie du traitement impliqué dans le rendu des pages et l’exécution du code a lieu sur le client plutôt que sur le serveur.

L’optimisation des performances pour les sites du portail moderne se concentre principalement sur quelques objectifs globaux :

- Réduire la taille totale des composants de chaque page de site
- Décharger l’hébergement de fichiers statiques courants tels que des images, des feuilles de style et des scripts sur CDN
- Limiter les appels à SharePoint et aux points de terminaison externes uniquement à ce qui est nécessaire
- Éviter les demandes en double pour le même contenu

La plupart des instructions de cet article se concentrent sur la réduction et l’optimisation des appels à SharePoint Online. L’exécution d’appels répétitifs chaque fois qu’une page est chargée aura un impact sur les performances des utilisateurs, car les informations seront récupérées du service chaque fois, même si elles n’ont pas changé. Par conséquent, les demandes adressées à SharePoint peuvent être classées en tant qu’appels courants pour tous les utilisateurs ou appels requis pour chaque utilisateur individuel. Les résultats de ces deux catégories d’appels doivent être mis en cache pour optimiser l’expérience utilisateur.

>[!NOTE]
>Utilisez [l’outil Diagnostics de page pour SharePoint](./page-diagnostics-for-spo.md) comme point de départ pour analyser des métriques de performances spécifiques sur les pages de site SharePoint Online.

## <a name="modern-portal-site-limits-and-recommendations"></a>Limites et recommandations de site du portail moderne

|**Limite**|**Valeur maximale recommandée**|**Remarques**|
|:-----|:-----|:-----|:-----|
|Pages et éléments d’actualités  <br/> |5 000 par site  <br/> |Nous vous recommandons de limiter le nombre de pages et d’articles d’actualités d’un site portail moderne à moins de 5 000.  <br/> |
|Composants WebPart sur une page  <br/> |20 par page  <br/> |Nous vous recommandons d’utiliser au moins 20 composants WebPart par page, y compris les composants WebPart Microsoft et les composants WebPart personnalisés. <br/> Pour plus d’informations, consultez [Optimiser les performances des composants WebPart dans les pages de site modernes de SharePoint Online](modern-web-part-optimization.md).  <br/> |
|Composants WebPart dynamiques sur une page  <br/> |4 par page  <br/> |Les composants WebPart dynamiques qui effectuent une ou plusieurs requêtes sur SharePoint pour extraire les données les plus récentes doivent être limités à 4 par page. Le composant _WebPart Actualités_ est un exemple de composant WebPart dynamique. <br/> Pour plus d’informations, consultez [Optimiser les performances des composants WebPart dans les pages de site modernes de SharePoint Online](modern-web-part-optimization.md).    <br/> |
|Groupes de sécurité  <br/> |20 par site  <br/> |Le nombre de groupes de sécurité affecte l’échelle de nombreuses requêtes dans les sites portail modernes. Nous vous recommandons de limiter le nombre de groupes de sécurité à un ensemble aussi petit que possible, avec un maximum de 20 par site.  <br/> |
|Éléments dans la navigation de site  <br/> |100 par site  <br/> |Nous vous recommandons d’ajouter moins de 100 éléments à la navigation de site et d’utiliser des contrôles de navigation à l’extérieur.  <br/> Pour plus d’informations, consultez [Optimiser le poids de page dans les pages de site modernes SharePoint Online](modern-page-weight-optimization.md). <br/> |
|Taille maximale de l’image  <br/> |300 Ko par image  <br/> |Nous vous recommandons de limiter la taille des images à 300 Ko ou plus, et d’utiliser un CDN pour héberger des images, des feuilles de style et des scripts. <br/>Pour plus d’informations, consultez [Optimiser les images dans les pages de site modernes SharePoint Online](modern-image-optimization.md) et [Utiliser le réseau de distribution de contenu (CDN) Office 365 avec SharePoint Online](use-microsoft-365-cdn-with-spo.md).  <br/> |
|Utilisateurs disposant de droits d’édition  <br/> |200 utilisateurs par site  <br/> |Les sites du portail SharePoint sont optimisés pour afficher et consommer du contenu. Les autorisations de modification sur un portail doivent être limitées à un groupe restreint d’utilisateurs, car les autorisations de modification téléchargent des contrôles supplémentaires et sont donc plus lentes pour ces utilisateurs. Un nombre excessif d’utilisateurs disposant d’autorisations de modification affecte donc l’expérience globale. <br/> |
|IFrames tiers  <br/> |2 par page  <br/> |Les iFrames sont imprévisiblement lents, car ils chargent une page externe distincte, y compris tout le contenu associé, tel que javascript, CSS et les éléments d’infrastructure. Si vous devez utiliser des iFrames, limitez leur nombre à 2 ou moins par page.<br/> Pour plus d’informations, consultez [Optimiser les iFrames dans les pages de site de publication modernes et classiques de SharePoint Online](modern-iframe-optimization.md). <br/> |
|Appels au service UPA  <br/> |1 par utilisateur et par heure  <br/> |Nous vous recommandons de ne pas effectuer d’appels _par demande_ au service UPA (Application de profil utilisateur). [Microsoft API Graph](/graph/call-api) et [PageContext](/javascript/api/sp-page-context/pagecontext) peuvent être utilisés pour rechercher des informations utilisateur.  <br/> Si un appel de service UPA est nécessaire, effectuez un seul appel si nécessaire, puis mettez en cache les informations à réutiliser dans la même session. |
|Appels au service taxonomie  <br/> |5 par utilisateur et par heure  <br/> |Nous vous recommandons de ne pas effectuer d’appels _par demande_ au service taxonomie. Si des appels de service de taxonomie sont nécessaires, mettez en cache les informations à réutiliser dans la même session. <br/> Pour plus d’informations, consultez [Optimiser les appels de page dans les pages de site de publication modernes et classiques de SharePoint Online](modern-page-call-optimization.md). <br/> |

## <a name="related-topics"></a>Voir aussi

[Création d’un portail SharePoint sain](/sharepoint/portal-health)

[Optimisation des performances SharePoint Online](tune-sharepoint-online-performance.md)

[Optimisation des performances Office 365](tune-microsoft-365-performance.md)

[Limites de SharePoint Online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[Performances offertes par l’expérience moderne de SharePoint](/sharepoint/modern-experience-performance)

[Aide relative aux performances des portails SharePoint Online](/sharepoint/dev/solution-guidance/portal-performance)
