---
title: Exceptions au plan de service
description: Comment demander des exceptions au plan de service standard
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 8069a899b9992a0e8b941b6ac53cd2f230a6174a
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2022
ms.locfileid: "62825178"
---
# <a name="exceptions-to-the-service-plan"></a>Exceptions au plan de service

Microsoft Manged Desktop fournit une liste d’appareils organisés, des [paramètres](device-policies.md) d’appareil standard, des exigences d’applications et certains [paramètres configurables, tous conçus](../working-with-managed-desktop/config-setting-overview.md) pour offrir une expérience sécurisée, productive et agréable aux utilisateurs.

Il est préférable de toujours rester avec le service tel que fourni. Toutefois, nous savons que certains détails du service peuvent ne pas répondre exactement aux besoins de votre organisation. Si vous pensez que vous devez modifier le service d’une certaine manière, il est important que vous suiviez les processus suivants pour demander ces modifications.

## <a name="types-of-exceptions"></a>Types d’exceptions

Une exception est tout ajout ou toute modification à la configuration Microsoft Manged Desktop base. Les exemples vont de la configuration des ports USB au déploiement d’un nouveau pilote de périphérique. Nous groupons différentes exceptions comme suit :

| Types d’exception | Description |
| ----- | ----- |
| Logiciels de productivité | Logiciels de premier plan requis par les utilisateurs, restreints par les exigences [de l’application](mmd-app-requirements.md). |
| Agents de sécurité & VPN | Logiciel utilisé pour sécuriser, surveiller ou modifier le comportement de l’appareil ou du réseau. |
| Surveillance de l’expérience numérique | Logiciel utilisé pour suivre les données sur l’appareil d’un utilisateur afin de les signaler au système informatique. |
| Pilotes matériels ou logiciels | Pilotes de périphérique, restreints par les exigences de [l’application](mmd-app-requirements.md). |
| Stratégies | Windows 10 ou Applications Microsoft 365 pour les grandes entreprises sur un appareil géré. |
| Appareils | Les appareils qui ne sont pas répertoriés dans la [Microsoft Manged Desktop’appareils.](device-list.md) |
| Other | Tout ce qui n’est pas couvert par les autres domaines. |

## <a name="request-an-exception"></a>Demander une exception

Envoyez des demandes via le portail Microsoft Manged Desktop’administration en créant une demande de modification. N’oubliez pas d’inclure les détails suivants :

| Modifier les détails de la demande | Description |
| ----- | ----- |
| Type d’exemption | Quel type d’exception s’agit-il ? (voir le [tableau précédent](#types-of-exceptions)) |
| Conditions requises | Quelle est la condition professionnelle spécifique à l’exception ? |
| Proposition | Quelle solution votre entreprise demande-t-elle ? |
| Chronologie | Combien de temps voulez-vous que cette exception dure ? |

## <a name="how-we-assess-an-exception-request"></a>Évaluation d’une demande d’exception

Lorsque nous examinerons les demandes d’exception, nous évaluons ces facteurs dans cet ordre :

1. Certaines applications et stratégies déployées Microsoft Manged Desktop sur tous les appareils ne sont pasgociables. Votre demande ne doit pas affecter ces applications et stratégies. Pour plus d’informations, voir [Configuration de l’appareil](device-policies.md).
2. Les logiciels de productivité restreints requis par un utilisateur pour faire leur travail seront probablement approuvés.
3. Si nous pouvons répondre à vos exigences à l’aide de la technologie Microsoft, nous approuverons probablement votre demande pour une période de migration d’exception de trois à 12 mois. La période de migration dépend de l’étendue du projet.
4. Si nous ne pouvons pas répondre à vos exigences à l’aide de la technologie Microsoft, nous approuverons probablement votre demande, sauf si elle enfreint l’une des [conditions clés](#key-conditions).  

Ces principes garantissent que les Microsoft Manged Desktop toujours répondre à vos besoins tout en suivant les écarts par rapport à notre modèle standard.

## <a name="key-conditions"></a>Conditions clés

Nous examinerons les exceptions pour nous assurer qu’elles ne violent pas l’une des conditions ci-après :

- Une exception ne doit pas affecter la sécurité du système.
- La maintenance de l’exception ne doit pas avoir de coût significatif pour les opérations Microsoft Manged Desktop ou la prise en charge.
- Une exception ne doit pas affecter la stabilité du système, par exemple en provoquant des incidents ou des incidents en mode noyau.
- La modification ne doit pas nous empêcher d’exploiter le service ou d’être en conflit avec la technologie Microsoft Manged Desktop de base.
- L’exception ne peut pas impliquer la personnalisation de l’expérience utilisateur, telle que la modification du menu Démarrer ou de la barre des tâches.

Ces conditions peuvent changer à l’avenir. Si nous arons apporté de telles modifications, nous fournirons un préavis de 30 jours avant que ces conditions entrent en vigueur.  Si Microsoft Manged Desktop offre une autre façon de répondre à une exception approuvée, Microsoft Manged Desktop avertit le client doit Microsoft Manged Desktop modifier la façon dont il prend en charge l’exception.

## <a name="revoking-approval-for-an-exception"></a>Révocation de l’approbation d’une exception

Une fois qu’une exception demandée a été approuvée et déployée, il est possible que nous découvrons des problèmes qui ne respectent pas les conditions clés qui n’étaient pas évidentes lorsque nous avons approuvé la modification en premier lieu. Dans ce cas, nous pouvons être dans l’devoir de révoquer l’approbation de l’exception.

Si nous devons révoquer l’approbation de l’exception, nous vous en informerons à l’aide Microsoft Manged Desktop portail d’administration. À partir de la première notification, vous avez 90 jours pour supprimer l’exception avant que les appareils à l’exception ne soient plus liés par les contrats de niveau de service Microsoft Manged Desktop de service.

Nous vous enverrons plusieurs notifications selon une chronologie stricte. Toutefois, un incident grave ou une menace peut nous obliger à modifier la chronologie de nos décisions concernant une exception. Nous ne supprimerons *pas une* exception sans votre consentement. Toutefois, tout appareil avec une exception révoquée ne sera plus lié par notre contrat de niveau de service. Le tableau suivant est la chronologie des notifications que nous vous envoyons :

| Type de notification | Description |
| ----- | ----- |
| Première notification | Nous fournissons les informations suivantes dans le premier avis : <ul><li>Informations sur la raison pour laquelle nous les révoquer.</li><li>Les actions que nous vous conseillons d’prendre.</li><li>Échéance de ces actions.</li><Li>Étapes à suivre si vous souhaitez faire appel de la décision.</li></ul> <br>Cet avis se produit 90 jours à l’avance avant que l’exception ne soit supprimée de tous les appareils. |
| Deuxième avis (30 jours plus tard) | Nous fournissons un deuxième avis, y compris les mêmes informations que celles fournies dans le premier avis. |
| Troisième avis (60 jours après le premier avis) | Nous fournissons un troisième avis, y compris les mêmes informations que celles fournies dans le premier avis. |
| Notification finale (une semaine avant l’échéance de 90 jours) | Nous fournissons un quatrième avis, y compris les mêmes informations que celles fournies dans le premier avis. |
| 90 jours après la première notification| Microsoft Manged Desktop contrats de niveau de service ne s’appliquent plus aux appareils qui ont l’exception révoquée. À tout moment, vous pouvez défier la décision et fournir des informations supplémentaires à prendre en compte, notamment la mise à niveau, les modifications de configuration ou la modification des logiciels. |
