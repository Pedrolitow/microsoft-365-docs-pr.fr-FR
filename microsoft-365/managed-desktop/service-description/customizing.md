---
title: Exceptions au plan de service
description: Comment demander des exceptions au plan de service standard
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 59a2b8227eb7e410ecf8506ce288978213537edc
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52245515"
---
# <a name="exceptions-to-the-service-plan"></a>Exceptions au plan de service

Bureau géré Microsoft fournit une liste d’appareils [organisés,](device-policies.md)des paramètres d’appareil standard, des exigences d’applications et certains [paramètres configurables, conçus](../working-with-managed-desktop/config-setting-overview.md)pour offrir une expérience sécurisée, productive et agréable aux utilisateurs. Il est préférable de toujours rester avec le service tel que fourni. Toutefois, nous savons que certains détails du service peuvent ne pas répondre exactement aux besoins de votre organisation. Si vous pensez avoir besoin de modifier le service d’une certaine manière, il est important que vous suiviez les processus suivants pour demander ces modifications.
 
## <a name="types-of-exceptions"></a>Types d’exceptions

Une exception est l’ajout ou la modification de la configuration Bureau géré Microsoft base de données . Les exemples vont de la configuration des ports USB au déploiement d’un nouveau pilote de périphérique. Nous groupons différentes exceptions comme suit :

|Type  |Description  |
|---------|---------|
|Logiciels de productivité     |  Logiciels de premier plan requis par les utilisateurs, restreints par les exigences [de l’application](mmd-app-requirements.md)       |
|Agents de sécurité & VPN     |  Logiciel utilisé pour sécuriser, surveiller ou modifier le comportement de l’appareil ou du réseau       |
|Surveillance de l’expérience numérique     |  Logiciel utilisé pour suivre les données sur l’appareil d’un utilisateur afin de les signaler à l’informatique       |
|Pilotes matériels ou logiciels     |   Pilotes de périphérique, restreints par les exigences de [l’application](mmd-app-requirements.md)      |
|Stratégies     | Windows 10 ou Applications Microsoft 365 pour les grandes entreprises sur un appareil géré        |
|Appareils     | Appareils qui ne sont pas dans la liste des [Bureau géré Microsoft’appareils](device-list.md)        |
|Autre     |  Tout ce qui n’est pas couvert par les autres domaines       |
 
## <a name="request-an-exception"></a>Demander une exception

Envoyez des demandes via le portail Bureau géré Microsoft’administration en créant une demande de modification. N’oubliez pas d’inclure les détails suivants :

- Type d’exemption : quelle catégorie d’exception s’agit-il ? (voir le tableau précédent)
- Exigence : quelle est la condition professionnelle spécifique pour l’exception ?
- Proposition : quelle solution votre entreprise demande-t-elle ?
- Chronologie : pendant combien de temps voulez-vous que cette exception dure ? 

## <a name="how-we-assess-an-exception-request"></a>Évaluation d’une demande d’exception

Lorsque nous examinerons les demandes d’exception, nous évaluons ces facteurs dans cet ordre :
 
1. Certaines applications et stratégies déployées Bureau géré Microsoft sur tous les appareils ne sont pasgociables, votre demande ne doit donc pas les affecter. Pour plus [d’informations,](device-policies.md) voir Configuration de l’appareil.
2. Les logiciels de productivité restreints requis par un utilisateur pour faire leur travail seront probablement approuvés. 
3. Si nous pouvons répondre à vos exigences à l’aide de la technologie Microsoft, nous approuverons probablement votre demande pour une période de migration d’exception de trois à 12 mois (selon l’étendue du projet).
4. Si nous ne pouvons pas répondre à vos exigences à l’aide de la technologie Microsoft, nous approuverons probablement votre demande, sauf si elle enfreint l’une des conditions ci-dessous.  

Ces principes garantissent que les Bureau géré Microsoft toujours répondre à vos besoins tout en suivant les écarts par rapport à notre modèle standard. 

## <a name="key-conditions"></a>Conditions clés

Nous examinerons les exceptions pour nous assurer qu’elles ne violent pas l’une des conditions ci-après :

- Une exception ne doit pas avoir d’impact négatif sur la sécurité du système. 
- La maintenance de l’exception ne doit pas avoir de coût significatif pour les opérations Bureau géré Microsoft ou la prise en charge.
- Une exception ne doit pas affecter la stabilité du système, par exemple en provoquant des incidents ou des incidents en mode noyau.
- La modification ne doit pas nous empêcher d’exploiter le service ou d’être en conflit avec la technologie Bureau géré Microsoft de base.

Ces conditions peuvent changer à l’avenir. Si nous arons apporté de telles modifications, nous fournirons un préavis de 30 jours avant que ces conditions entrent en vigueur.  Si Bureau géré Microsoft offre une autre façon de répondre à une exception approuvée, Bureau géré Microsoft avertit le client Bureau géré Microsoft modifier la prise en charge de l’exception. 

## <a name="revoking-approval-for-an-exception"></a>Révocation de l’approbation d’une exception

Après l’approbation et le déploiement d’une exception demandée, il est possible que nous découvrons des problèmes qui ne respectent pas les conditions clés qui n’étaient pas évidentes lorsque nous avons approuvé la modification. Dans ce cas, il se peut que nous deions révoquer l’approbation de l’exception.
 
Si cela se produit, nous vous en informerons à l’aide du portail Bureau géré Microsoft’administration. À partir de la première notification, vous avez 90 jours pour supprimer l’exception avant que les appareils à l’exception ne soient plus liés par les contrats de niveau de service Bureau géré Microsoft. Nous vous enverrons plusieurs notifications en fonction d’une chronologie stricte. Toutefois, un incident grave ou une menace peut nous obliger à modifier la chronologie ou nos décisions concernant une exception. Nous ne *supprimerons* pas une exception sans votre consentement, mais tout appareil avec une exception révoquée ne sera plus lié par notre contrat de niveau de service. Voici la chronologie des notifications que nous vous envoyons :

- **Première remarque :** Nous fournissons le premier avis de notre décision de révoquer l’approbation, notamment des informations sur la raison de sa révocation, les actions que nous vous conseillons de prendre, l’échéance de ces actions et les étapes à suivre si vous souhaitez faire appel de la décision. Cet avis se produit 90 jours à l’avance avant que l’exception ne soit supprimée de tous les appareils. 
- **Deuxième avis (30 jours plus tard) :** Nous fournissons un deuxième avis, y compris les mêmes informations que celles fournies dans le premier avis. 
- **Troisième avis (60 jours après le premier avis) :** Nous fournissons un troisième avis, y compris les mêmes informations que celles fournies dans le premier avis. 
- **Notification finale (une semaine avant l’échéance de 90 jours) :** Nous fournissons un quatrième avis, y compris les mêmes informations que celles fournies dans le premier avis.
- **90 jours après la** première notification : Bureau géré Microsoft contrats de niveau de service ne s’appliquent plus aux appareils qui ont l’exception révoquée. À tout moment, vous pouvez défier la décision et fournir des informations supplémentaires à prendre en compte, notamment la mise à niveau, les modifications de configuration ou la modification des logiciels. 


