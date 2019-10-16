---
title: Personnaliser le service
description: ''
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: b2b74194c9b73e538fc1be937456b76deef75feb
ms.sourcegitcommit: eed48c21790d31a85292f7e39bf1e30c42f10d36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "37523669"
---
# <a name="customize-the-service"></a>Personnaliser le service

Microsoft Managed Desktop fournit une liste d’appareils organisée, des [paramètres standard des appareils](device-policies.md), des applications requises et certains [paramètres configurables](../working-with-managed-desktop/config-setting-overview.md), conçus pour offrir une expérience sécurisée, productive et agréable aux utilisateurs finaux. Il est préférable de toujours conserver le service tel qu’il est fourni. Toutefois, nous reconnaissons que certains détails du service ne correspondent pas exactement aux besoins de votre organisation. Si vous pensez que vous devez modifier le service d’une certaine façon, il est important de suivre les processus suivants pour demander ces modifications.

 
## <a name="types-of-customizations"></a>Type de personnalisations
Une personnalisation est un ajout ou une modification apportée à la configuration de base du bureau géré Microsoft ; des exemples vont de la configuration des ports USB au déploiement d’un nouvel agent de sécurité. Nous regroupons différentes personnalisations de la manière suivante :


|Type  |Description  |
|---------|---------|
|Logiciels de productivité     |  Logiciels de premier plan requis par les utilisateurs finaux, limités par les exigences de l' [application](mmd-app-requirements.md)       |
|Agents de sécurité & VPN     |  Logiciel utilisé pour sécuriser, surveiller ou modifier le comportement du périphérique ou du réseau       |
|Surveillance de l’expérience numérique     |  Logiciel utilisé pour effectuer le suivi des données sur l’appareil d’un utilisateur pour lui faire rapport.       |
|Pilotes matériels ou logiciels     |   Pilotes de périphériques, restreints par les exigences de l' [application](mmd-app-requirements.md)      |
|Stratégies     | Paramètres Windows 10 ou Office 365 ProPlus sur un appareil géré        |
|Appareils     | Appareils qui ne figurent pas dans la [liste](device-list.md) des appareils de bureau géré Microsoft        |
|Other     |  Tout ce qui n’est pas couvert par les autres zones       |



 
## <a name="request-a-customization"></a>Demander une personnalisation

Soumettez des demandes via le portail d’administration de bureau géré Microsoft en créant une demande de modification. N’oubliez pas d’inclure les détails suivants :
-   Type de personnalisation : quelle catégorie de personnalisation s’agit-elle ? (reportez-vous au tableau précédent)
-   Exigence : Quelles sont les exigences métiers spécifiques pour la personnalisation ?
-   Proposition : quelle solution votre entreprise demande-t-elle ?
-   Chronologie : combien de temps voulez-vous que cette personnalisation soit la dernière ? 


## <a name="how-we-assess-a-customization-request"></a>Comment nous évaluons une demande de personnalisation

Lors de l’examen des demandes de personnalisation, nous évaluons ces facteurs dans l’ordre suivant :
 
1.  Certaines applications et stratégies déployées par Microsoft Managed Desktop sur tous les appareils ne sont pas négociables, de sorte que votre requête ne doit pas les affecter. Pour plus d’informations, voir Configuration de l' [appareil](device-policies.md) .
2.  Les logiciels de productivité restreints requis par un utilisateur final pour effectuer leur travail seront vraisemblablement approuvés. 
3.  Si nous pouvons répondre à vos besoins à l’aide de la technologie Microsoft, nous approuverons probablement votre demande pour une période de migration de trois à douze mois (en fonction de l’étendue du projet).
4.  Si nous ne pouvons pas répondre à vos besoins à l’aide de la technologie Microsoft, nous approuvons probablement votre demande, sauf si elle viole l’une des conditions ci-dessous.  

Ces principes permettent de s’assurer que le bureau géré Microsoft peut toujours répondre à vos besoins lors du suivi des écarts par rapport à notre modèle standard. 

## <a name="key-conditions"></a>Conditions clés

Nous examinerons les personnalisations pour s’assurer qu’elles n’enfreignent aucune des conditions suivantes :

-   Une personnalisation ne doit pas avoir un impact négatif sur la sécurité du système. 
-   La gestion de la personnalisation ne doit pas occasionner de coûts significatifs pour les opérations ou la prise en charge de Microsoft Managed Desktop.
-   Une personnalisation ne doit pas affecter la stabilité du système, par exemple, en provoquant un blocage ou un blocage du mode noyau.
-   Le changement ne doit pas nous empêcher d’utiliser le service ou le conflit avec la technologie principale de bureau géré Microsoft.

Ces conditions peuvent être modifiées à l’avenir. Si nous faisons ces modifications, nous vous fournirons un préavis de 30 jours avant que ces conditions entrent en vigueur.

## <a name="revoking-approval-for-a-customization"></a>Révocation de l’approbation pour une personnalisation

Une fois qu’une personnalisation demandée est approuvée et déployée, il est possible que nous découvrons des problèmes qui enfreignent les conditions clés qui n’étaient pas évidentes lorsque nous avons approuvé la modification à la première place. Dans ce cas, nous pouvons être amenés à révoquer l’approbation pour la personnalisation.
 
Dans ce cas, nous vous en informerons à l’aide du portail d’administration de bureau géré Microsoft. À partir de la première fois que nous vous avertissons, vous disposez de 90 jours pour supprimer la personnalisation avant que les appareils avec la personnalisation ne soient plus liés par les contrats de niveau de service de bureau géré Microsoft. Nous vous enverrons plusieurs notifications en fonction d’une chronologie stricte : Toutefois, un incident ou une menace grave pourrait nécessiter de modifier la chronologie ou nos décisions concernant une personnalisation. Nous ne *supprimons* pas la personnalisation sans votre consentement, mais tous les appareils avec une personnalisation révoquée ne seront plus liés par notre contrat de niveau de service. Voici la chronologie des notifications que nous vous enverrons :

- **Première notification :** Nous fournissons le premier avis de notre décision de révoquer l’approbation, notamment des informations sur la raison de la révocation, les actions que nous vous recommandons de prendre, la date d’échéance de ces actions et les étapes à suivre pour contester la décision. Il s’agit de 90 jours à l’avance avant que la personnalisation doive être supprimée de tous les appareils. 
- **Deuxième notification (30 jours plus tard) :** Nous fournissons une deuxième notification, incluant les mêmes informations que dans le premier avis. 
- **Troisième mention (60 jours après la première notification) :** Nous fournissons une troisième notification, incluant les mêmes informations que dans le premier avis. 
- **Dernière mention (1 semaine avant le délai d' 90 jours) :** Nous fournissons une quatrième notification, notamment les mêmes informations que dans le premier avis.
- **90 jours après la première notification :** Les contrats de niveau de service de bureau géré Microsoft ne s’appliquent plus aux appareils dont la personnalisation a été révoquée. À tout moment, vous pouvez contester la décision et fournir des informations supplémentaires à prendre en compte, notamment la mise à niveau, les modifications apportées à la configuration ou le changement de logiciel. 

