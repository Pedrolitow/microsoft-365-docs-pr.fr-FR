---
title: Exceptions au plan de service
description: ''
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: aca3bb6413aaab7620b1e1277c821a79dba4bb2f
ms.sourcegitcommit: 9083036e787cf997fbceb19c66af594d0fa81d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "38302901"
---
# <a name="exceptions-to-the-service-plan"></a>Exceptions au plan de service

Microsoft Managed Desktop fournit une liste d’appareils organisée, des [paramètres standard des appareils](device-policies.md), des applications requises et certains [paramètres configurables](../working-with-managed-desktop/config-setting-overview.md), conçus pour offrir une expérience sécurisée, productive et agréable aux utilisateurs finaux. Il est préférable de toujours conserver le service tel qu’il est fourni. Toutefois, nous reconnaissons que certains détails du service ne correspondent pas exactement aux besoins de votre organisation. Si vous pensez que vous devez modifier le service d’une certaine façon, il est important de suivre les processus suivants pour demander ces modifications.
 
## <a name="types-of-exceptions"></a>Types d’exceptions

Une exception est l’ajout ou la modification de la configuration de base du bureau géré Microsoft ; des exemples vont de la configuration des ports USB au déploiement d’un nouveau pilote de périphérique. Nous regroupons différentes exceptions comme suit :

|Type  |Description  |
|---------|---------|
|Logiciels de productivité     |  Logiciels de premier plan requis par les utilisateurs finaux, limités par les exigences de l' [application](mmd-app-requirements.md)       |
|Agents de sécurité & VPN     |  Logiciel utilisé pour sécuriser, surveiller ou modifier le comportement du périphérique ou du réseau       |
|Surveillance de l’expérience numérique     |  Logiciel utilisé pour effectuer le suivi des données sur l’appareil d’un utilisateur pour lui faire rapport.       |
|Pilotes matériels ou logiciels     |   Pilotes de périphériques, restreints par les exigences de l' [application](mmd-app-requirements.md)      |
|Stratégies     | Paramètres Windows 10 ou Office 365 ProPlus sur un appareil géré        |
|Appareils     | Appareils qui ne figurent pas dans la [liste](device-list.md) des appareils de bureau géré Microsoft        |
|Other     |  Tout ce qui n’est pas couvert par les autres zones       |
 
## <a name="request-an-exception"></a>Demander une exception

Soumettez des demandes via le portail d’administration de bureau géré Microsoft en créant une demande de modification. N’oubliez pas d’inclure les détails suivants :

-   Type d’exemption : quelle catégorie d’exception est-elle ? (reportez-vous au tableau précédent)
-   Exigence : Quelles sont les exigences métiers spécifiques pour l’exception ?
-   Proposition : quelle solution votre entreprise demande-t-elle ?
-   Chronologie : combien de temps souhaitez-vous que cette exception dure ? 

## <a name="how-we-assess-an-exception-request"></a>Comment nous évaluons une demande d’exception

Lorsque nous examinez les demandes d’exception, nous évaluons ces facteurs dans cet ordre :
 
1.  Certaines applications et stratégies déployées par Microsoft Managed Desktop sur tous les appareils ne sont pas négociables, de sorte que votre requête ne doit pas les affecter. Pour plus d’informations, voir Configuration de l' [appareil](device-policies.md) .
2.  Les logiciels de productivité restreints requis par un utilisateur final pour effectuer leur travail seront vraisemblablement approuvés. 
3.  Si nous pouvons répondre à vos besoins à l’aide de la technologie Microsoft, nous approuverons probablement votre demande pour une période de migration des exceptions de trois à douze mois (en fonction de l’étendue du projet).
4.  Si nous ne pouvons pas répondre à vos besoins à l’aide de la technologie Microsoft, nous approuvons probablement votre demande, sauf si elle viole l’une des conditions ci-dessous.  

Ces principes permettent de s’assurer que le bureau géré Microsoft peut toujours répondre à vos besoins lors du suivi des écarts par rapport à notre modèle standard. 

## <a name="key-conditions"></a>Conditions clés

Nous allons passer en revue les exceptions afin de s’assurer qu’elles n’enfreignent aucune des conditions suivantes :

-   Une exception ne doit pas avoir d’impact négatif sur la sécurité du système. 
-   La gestion de l’exception ne doit pas occasionner de coûts significatifs pour les opérations ou la prise en charge de Microsoft Managed Desktop.
-   Une exception ne doit pas affecter la stabilité du système, par exemple, en provoquant un blocage ou un blocage du mode noyau.
-   Le changement ne doit pas nous empêcher d’utiliser le service ou le conflit avec la technologie principale de bureau géré Microsoft.

Ces conditions peuvent être modifiées à l’avenir. Si nous faisons ces modifications, nous vous fournirons un préavis de 30 jours avant que ces conditions entrent en vigueur.  Si Microsoft Managed Desktop offre un autre moyen de répondre à une exception approuvée, le bureau géré Microsoft avertit le client si le bureau géré par Microsoft a modifié la manière de prendre en charge l’exception. 

## <a name="revoking-approval-for-an-exception"></a>Révocation de l’approbation pour une exception

Une fois qu’une exception demandée est approuvée et déployée, il est possible que nous découvrons des problèmes qui enfreignent les conditions clés qui n’étaient pas évidentes lorsque nous avons approuvé la modification à la première place. Dans ce cas, nous pouvons être amenés à révoquer l’approbation pour l’exception.
 
Dans ce cas, nous vous en informerons à l’aide du portail d’administration de bureau géré Microsoft. À partir de la première fois que nous vous avertissons, vous disposez de 90 jours pour supprimer l’exception avant que les appareils avec l’exception ne soient plus liés par les contrats de niveau de service de bureau géré Microsoft. Nous vous enverrons plusieurs notifications en fonction d’une chronologie stricte : Toutefois, un incident ou une menace grave pourrait nécessiter de modifier la chronologie ou nos décisions concernant une exception. Nous ne *supprimerons* pas d’exception sans votre consentement, mais tous les appareils avec une exception révoquée ne seront plus liés par notre contrat de niveau de service. Voici la chronologie des notifications que nous vous enverrons :

- **Première notification :** Nous fournissons le premier avis de notre décision de révoquer l’approbation, notamment des informations sur la raison de la révocation, les actions que nous vous recommandons de prendre, la date d’échéance de ces actions et les étapes à suivre pour contester la décision. Il s’agit de 90 jours avant la suppression de l’exception de tous les appareils. 
- **Deuxième notification (30 jours plus tard) :** Nous fournissons une deuxième notification, incluant les mêmes informations que dans le premier avis. 
- **Troisième mention (60 jours après la première notification) :** Nous fournissons une troisième notification, incluant les mêmes informations que dans le premier avis. 
- **Dernière mention (1 semaine avant le délai d' 90 jours) :** Nous fournissons une quatrième notification, notamment les mêmes informations que dans le premier avis.
- **90 jours après la première notification :** Les contrats de niveau de service de bureau géré Microsoft ne s’appliquent plus à tous les appareils qui ont l’exception révoquée. À tout moment, vous pouvez contester la décision et fournir des informations supplémentaires à prendre en compte, notamment la mise à niveau, les modifications apportées à la configuration ou le changement de logiciel. 


