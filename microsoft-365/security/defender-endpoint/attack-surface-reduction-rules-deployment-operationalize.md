---
title: Operationalize attack surface reduction (ASR) rules deployment
description: Fournit des conseils pour rendre opérationnel le déploiement de vos règles de réduction de la surface d’attaque.
keywords: Déploiement des règles de réduction de la surface d’attaque, déploiement de la réduction de la surface d’attaque, activer les règles d’attaque, configurer la réduction de la surface d’attaque, système de prévention des intrusions hôte, règles de protection, règles anti-attaque, règles d’attaque, règles de prévention des infections, Microsoft Defender pour le point de terminaison, configurer des règles de réduction de la surface d’attaque
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 9a3e8ab38c807b8cf3ea54bb5a18a5405d0b3c49
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465352"
---
# <a name="step-4-operationalize-asr-rules"></a>Étape 4 : Opérationnaliser les règles ASR

Une fois que vous avez déployé entièrement les règles de réduction de la surface d’attaque( ASR), il est essentiel de mettre en place des processus pour surveiller les activités liées à la réduction de la surface d’attaque et y répondre.

## <a name="managing-false-positives"></a>Gestion des faux positifs

Les faux positifs/négatifs peuvent se produire avec n’importe quelle solution de protection contre les menaces. Les faux positifs sont des cas dans lesquels une entité (telle qu’un fichier ou un processus) est détectée et identifiée comme malveillante, bien que l’entité ne soit pas réellement une menace. En revanche, un faux négatif est une entité qui n’a pas été détectée comme une menace, mais qui est malveillante. Pour plus d’informations sur les faux positifs et les faux négatifs, voir : [Traiter les faux positifs/négatifs dans Microsoft Defender pour endpoint](defender-endpoint-false-positives-negatives.md)

## <a name="keeping-up-with-reports"></a>Suivi des rapports

Un examen cohérent et régulier des rapports est un aspect essentiel de la maintenance du déploiement de vos règles de asr et de la conservation des nouvelles menaces émergentes. Votre organisation doit avoir programmé des révisions des événements de règles de la asr à une cadence qui restera à jour avec les événements signalés par les règles de la asr. Selon la taille de votre organisation, les avis peuvent être une surveillance quotidienne, horaire ou continue.

## <a name="hunting"></a>Repérage

L’une des fonctionnalités les plus puissantes de [Microsoft 365 Defender](https://security.microsoft.com) est la recherche avancée. Si vous n’êtes pas familiarisé avec le chasse avancée, voir : [recherchez de manière proactive les menaces avec le chasse avancée](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview).

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting2.png" alt-text="Page Recherche avancée dans le portail Microsoft 365 Defender web" lightbox="images/asr-defender365-advanced-hunting2.png":::

Le repérage avancé est un outil de repérage de menaces basé sur une requête (Kusto Query Language) qui vous permet d’explorer jusqu’à 30 jours des données capturées (brutes) collectées par Microsoft Defender ATP Endpoint Detection and Response (PEPT) à partir de tous vos ordinateurs. Grâce à la recherche avancée, vous pouvez inspecter de manière proactive les événements afin de localiser des indicateurs et des entités intéressants. L’accès flexible aux données facilite le repérage sans contrainte pour les menaces connues et potentielles.

Grâce à la recherche avancée, il est possible d’extraire des informations sur les règles de la asr, de créer des rapports et d’obtenir des informations détaillées sur le contexte d’un événement d’audit ou de blocage de règle asr donné.

 Vous pouvez interroger les événements de règles asr à partir de la table DeviceEvents dans la section de recherche avancée du portail Microsoft 365 Defender. Par exemple, une requête simple, telle que celle ci-dessous, peut signaler tous les événements qui ont des règles de asr en tant que source de données, au cours des 30 derniers jours, et les synthétisera par le nombre ActionType, qui dans ce cas sera le nom de code réel de la règle asr.

Les événements asr présentés dans le portail de chasse sont limitées à des processus uniques visibles toutes les heures. L’heure de l’événement ASR est la première fois que l’événement est vu dans cette heure.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting3.png" alt-text="Ligne de commande de requête de recherche avancée dans le portail Microsoft 365 Defender de recherche" lightbox="images/asr-defender365-advanced-hunting3.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting4.png" alt-text="La requête de recherche avancée entraîne l’Microsoft 365 Defender de recherche" lightbox="images/asr-defender365-advanced-hunting4.png":::

L’exemple ci-dessus indique que 187 événements ont été enregistrés pour AsrLsassCredentialTheft :

- 102 pour bloqué
- 85 pour audit
- 2 événements pour AsrOfficeChildProcess (1 pour Audited et 1 pour Block)
- 8 événements pour AsrPsexecWmiChildProcessAudited

Si vous souhaitez vous concentrer sur la règle AsrOfficeChildProcess et obtenir des détails sur les fichiers et processus impliqués, modifiez le filtre pour ActionType et remplacez la ligne de synthèse par une projection des champs souhaités (dans ce cas, il s’agit de DeviceName, FileName, FolderPath, etc.).

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting4b.png" alt-text="Exemple de requête de recherche avancée axée sur le portail Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting4b.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting5b.png" alt-text="La requête de recherche avancée axée sur les résultats dans le portail Microsoft 365 Defender recherche" lightbox="images/asr-defender365-advanced-hunting5b.png":::

Le véritable avantage de la recherche avancée est que vous pouvez mettre en forme les requêtes à votre convenance. La mise en forme de votre requête vous permet de voir l’histoire exacte de ce qui se passe, que vous vouliez épingler quelque chose sur un ordinateur individuel ou que vous vouliez extraire des informations de l’ensemble de votre environnement.

Pour plus d’informations sur les options de recherche, voir : [Démystification](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968) des règles de réduction de la surface d’attaque - Partie 3.

## <a name="topics-in-this-deployment-collection"></a>Rubriques de cette collection de déploiements

[Prérequis pour le déploiement des règles ASR](attack-surface-reduction-rules-deployment.md)

[Étape 1 : Planifier le déploiement des règles ASR](attack-surface-reduction-rules-deployment-plan.md)

[Étape 2 : Tester les règles ASR](attack-surface-reduction-rules-deployment-test.md)

[Étape 3 : Mettre en œuvre les règles ASR](attack-surface-reduction-rules-deployment-implement.md)
