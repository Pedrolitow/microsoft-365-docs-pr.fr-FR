---
title: Limites du site portail moderne SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/9/2019
audience: Admin
ms.topic: interactive-tutorial
ms.service: o365-administration
localization_priority: Normal
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
description: Découvrez les recommandations en matière de performances pour les sites modernes dans SharePoint Online, telles que la limitation des appels vers SharePoint et les points de terminaison externes.
ms.openlocfilehash: 28c32be276f6c27194d164708e268a5cd36ac957
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50925319"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>Limites du site portail moderne SharePoint Online

Cet article fournit des recommandations en matière de performances pour les sites portail modernes dans SharePoint Online. Utilisez les instructions de cet article pour optimiser les performances des sites portail modernes et éviter les problèmes de performances courants.

## <a name="performance-considerations-for-modern-portal-sites"></a>Considérations sur les performances pour les sites portail modernes

Du point de vue de l’optimisation des performances, il existe quelques caractéristiques qui rendent les sites portail modernes uniques. La principale différence entre les sites de collaboration et les sites portail dans SharePoint Online est l’échelle. Les sites portail sont généralement censés servir plus d’affichages de page à un plus grand nombre d’utilisateurs que les sites de collaboration, et sont susceptibles de contenir plus de contenu statique et moins de ressources modifiables. En outre, l’architecture des sites modernes diffère des sites classiques dans la plupart des processus impliqués dans le rendu des pages et l’exécution du code sur le client plutôt que sur le serveur.

L’optimisation des performances des sites portail modernes est principalement axée sur quelques objectifs globaux :

- Réduire la taille totale des composants de chaque page de site
- Décharger l’hébergement de fichiers statiques courants tels que des images, des feuilles de style et des scripts sur CDN
- Limiter les appels à SharePoint et aux points de terminaison externes uniquement à ce qui est nécessaire
- Éviter les demandes en double pour le même contenu

Bon nombre des instructions de cet article se concentrent sur la réduction et l’optimisation des appels vers SharePoint Online. Le fait d’effectuer des appels répétitifs chaque fois qu’une page est chargée a une incidence sur les performances des utilisateurs, car les informations sont récupérées du service à chaque fois, même si elles n’ont pas changé. En tant que tel, les demandes à SharePoint peuvent être classées en tant qu’appels communs à tous les utilisateurs ou appels requis pour chaque utilisateur individuel. Les résultats de ces deux catégories d’appels doivent être mis en cache pour optimiser l’expérience utilisateur.

>[!NOTE]
>Utilisez [l’outil Diagnostic de page pour SharePoint](./page-diagnostics-for-spo.md) comme point de départ pour analyser des mesures de performances spécifiques sur les pages de site SharePoint Online.

## <a name="modern-portal-site-limits-and-recommendations"></a>Recommandations et limites des sites portail modernes

|**Limite**|**Valeur maximale recommandée**|**Notes**|
|:-----|:-----|:-----|:-----|
|Pages et éléments d’actualité  <br/> |5 000 par site  <br/> |Nous vous recommandons de limiter le nombre de pages et d’éléments d’actualités dans un site portail moderne à moins de 5 000.  <br/> |
|Composants Web Parts sur une page  <br/> |20 par page  <br/> |Nous vous recommandons d’utiliser au moins 20 composants Web Part par page, y compris les composants Web Parts Microsoft pré-personnalisés et les composants Web Part personnalisés. <br/> Pour plus d’informations, voir Optimiser les performances du site Web Dans les [pages de sites modernes SharePoint Online.](modern-web-part-optimization.md)  <br/> |
|Composants Web Parts dynamiques sur une page  <br/> |4 par page  <br/> |Les composants Web Part dynamiques qui font une ou plusieurs requêtes à SharePoint pour extraire les dernières données doivent être limités à 4 par page. Le _partie_ Web Part Actualités est un exemple de partie Web dynamique. <br/> Pour plus d’informations, voir Optimiser les performances du site Web Dans les [pages de sites modernes SharePoint Online.](modern-web-part-optimization.md)    <br/> |
|Groupes de sécurité  <br/> |20 par site  <br/> |Le nombre de groupes de sécurité affecte l’échelle de nombreuses requêtes dans les sites portail modernes. Nous vous recommandons de limiter le nombre de groupes de sécurité à un ensemble aussi petit que possible, avec un maximum de 20 par site.  <br/> |
|Éléments dans la navigation du site  <br/> |100 par site  <br/> |Nous vous recommandons d’ajouter moins de 100 éléments à la navigation du site et d’utiliser des contrôles de navigation pré-utilisés.  <br/> Pour plus d’informations, voir Optimiser le poids des pages dans les [pages de sites modernes SharePoint Online.](modern-page-weight-optimization.md) <br/> |
|Taille maximale de l’image  <br/> |300 Ko par image  <br/> |Nous vous recommandons de limiter la taille des images à 300 000b ou moins et d’utiliser un CDN pour héberger des images, des feuilles de style et des scripts. <br/>Pour plus d’informations, voir Optimiser les images dans les pages de site moderne [SharePoint Online](modern-image-optimization.md) et utiliser le réseau de distribution de contenu [(CDN) Office 365 avec SharePoint Online.](use-microsoft-365-cdn-with-spo.md)  <br/> |
|Utilisateurs ayant des droits de modification  <br/> |200 utilisateurs par site  <br/> |Les sites portail SharePoint sont optimisés pour l’affichage et la consommation de contenu. Les autorisations de modification sur un portail doivent être limitées à un groupe restreint d’utilisateurs, car les autorisations de modification téléchargent des contrôles supplémentaires et sont donc plus lentes pour ces utilisateurs. Un nombre excessif d’utilisateurs ayant des autorisations de modification affectera donc l’expérience globale. <br/> |
|IFrames tiers  <br/> |2 par page  <br/> |Les iFrames sont trop lents, car ils chargent une page externe distincte, y compris tout le contenu associé, tel que javascript, CSS et les éléments d’infrastructure. Si vous devez utiliser des iFrames, limitez leur nombre à 2 ou moins par page.<br/> Pour plus d’informations, voir Optimiser les iFrames dans les pages de site de publication modernes et [classiques SharePoint Online.](modern-iframe-optimization.md) <br/> |
|Appels vers le service UPA  <br/> |1 par utilisateur et par heure  <br/> |Nous vous recommandons de ne pas effectuer d’appels _par demande_ au service UPA (User Profile Application). [L’API Microsoft Graph et](/graph/call-api) [PageContext](/javascript/api/sp-page-context/pagecontext?view=sp-typescript-latest) peuvent être utilisés pour interroger des informations utilisateur.  <br/> Si un appel de service UPA est nécessaire, appelez le cas échéant un seul appel, puis cachez les informations à réutiliser dans la même session. |
|Appels au service de taxonomie  <br/> |5 par utilisateur et par heure  <br/> |Nous vous recommandons de ne pas effectuer _d’appels par demande_ au service de taxonomie. Si des appels de service de taxonomie sont nécessaires, mettre en cache les informations à réutiliser dans la même session. <br/> Pour plus d’informations, voir Optimiser les appels de page dans les pages de site de publication modernes et classiques [SharePoint Online.](modern-page-call-optimization.md) <br/> |

## <a name="related-topics"></a>Rubriques connexes

[Création d’un portail SharePoint sain](/sharepoint/portal-health)

[Optimisation des performances SharePoint Online](tune-sharepoint-online-performance.md)

[Optimisation des performances Office 365](tune-microsoft-365-performance.md)

[Limites de SharePoint Online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[Performances offertes par l’expérience moderne de SharePoint](/sharepoint/modern-experience-performance)

[Aide relative aux performances des portails SharePoint Online](/sharepoint/dev/solution-guidance/portal-performance)