---
title: Utiliser des règles de réduction de la surface d’attaque (ASR)
description: Fournit des conseils pour l’opérationnalisation du déploiement de vos règles de réduction de la surface d’attaque.
keywords: Déploiement de règles de réduction de la surface d’attaque (ASR), Microsoft ASR, gérer les règles ASR defender, surveiller les règles asr, chasse avancée des règles asr, rapport de règles ASR, règles asr faux positifs, configurer asr, système de prévention des intrusions de l’hôte, règles de protection, règles anti-exploitation, règles d’exploitation, règles de prévention des infections, Microsoft Defender pour point de terminaison, configurer des règles ASR
search.product: eADQiWindows 10XVcnh
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.service: microsoft-365-security
ms.subservice: mde
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.topic: conceptual
ms.collection:
- m365-security
- m365solution-asr-rules
- highpri
- tier1
ms.date: 1/18/2022
search.appverid: met150
ms.openlocfilehash: 98aa168624b4093923ed6afa476e3385248ce3c2
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68624640"
---
# <a name="operationalize-attack-surface-reduction-asr-rules"></a>Utiliser des règles de réduction de la surface d’attaque (ASR)

Une fois que vous avez entièrement déployé des règles de réduction de la surface d’attaque (ASR), il est essentiel que vous ayez des processus en place pour surveiller et répondre aux activités liées à l’ASR. Les activités sont les suivantes : 

## <a name="managing-asr-rules-false-positives"></a>Gestion des faux positifs des règles ASR

Des faux positifs/négatifs peuvent se produire avec n’importe quelle solution de protection contre les menaces. Les faux positifs sont des cas où une entité (par exemple, un fichier ou un processus) est détectée et identifiée comme malveillante, bien que l’entité ne soit pas réellement une menace. En revanche, un faux négatif est une entité qui n’a pas été détectée comme une menace, mais qui est malveillante. Pour plus d’informations sur les faux positifs et les faux négatifs, consultez : [Résoudre les faux positifs/négatifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)

## <a name="keeping-up-with-asr-rules-reports"></a>Suivre les rapports de règles ASR

L’examen régulier et cohérent des rapports est un aspect essentiel de la maintenance de votre déploiement de règles ASR et de la mise à jour des menaces nouvellement émergentes. Votre organisation doit avoir planifié des révisions des événements de règles ASR à une cadence qui reste à jour avec les événements signalés par les règles ASR. Selon la taille de votre organisation, les révisions peuvent être quotidiennes, horaires ou continues.

## <a name="asr-rules-advanced-hunting"></a>Règles ASR - Repérage avancé

L’une des fonctionnalités les plus puissantes de [Microsoft 365 Defender](https://security.microsoft.com) est la chasse avancée. Si vous n’êtes pas familiarisé avec la chasse avancée, consultez : [Chasse proactive contre les menaces avec la chasse avancée](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview).

> :::image type="content" source="images/asr-defender365-advanced-hunting2.png" alt-text="Page Repérage avancé dans le portail Microsoft 365 Defender. Microsoft Defender pour point de terminaison (MDE) règles ASR, règles ASR de chasse avancée, rapports de règles asr, règles asr faux positifs," lightbox="images/asr-defender365-advanced-hunting2.png":::

La chasse avancée est un outil de chasse aux menaces basé sur une requête (Langage de requête Kusto) qui vous permet d’explorer jusqu’à 30 jours de données capturées (brutes) que Microsoft Defender détection et réponse des points de terminaison ATP (EDR) collectent à partir de toutes vos machines. Grâce à la chasse avancée, vous pouvez inspecter de manière proactive les événements afin de localiser des indicateurs et des entités intéressants. L’accès flexible aux données facilite le repérage sans contrainte pour les menaces connues et potentielles.

Grâce à la chasse avancée, il est possible d’extraire des informations sur les règles ASR, de créer des rapports et d’obtenir des informations détaillées sur le contexte d’un audit de règle ASR donné ou d’un événement de bloc.

 Vous pouvez interroger des événements de règles ASR à partir de la table DeviceEvents dans la section de chasse avancée du portail Microsoft 365 Defender. Par exemple, une requête simple telle que celle ci-dessous peut signaler tous les événements qui ont des règles ASR en tant que source de données, au cours des 30 derniers jours, et les résumera par le nombre d’ActionTypes, que dans ce cas, il s’agit du nom de code réel de la règle ASR.

Les événements ASR affichés dans le portail de chasse en cours d’avancement sont limités aux processus uniques observés toutes les heures. L’heure de l’événement ASR est la première fois que l’événement est vu dans cette heure.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting3.png" alt-text="Ligne de commande de requête de repérage avancée dans le portail Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting3.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting4.png" alt-text="Les résultats de la requête de repérage avancé dans le portail Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting4.png":::

L’exemple ci-dessus montre que 187 événements ont été enregistrés pour AsrLsassCredentialTheft :

- 102 pour bloqué
- 85 pour audité
- 2 événements pour AsrOfficeChildProcess (1 pour Audité et 1 pour Block)
- 8 événements pour AsrPsexecWmiChildProcessAudited

Si vous souhaitez vous concentrer sur la règle AsrOfficeChildProcess et obtenir des détails sur les fichiers et processus réels impliqués, modifiez le filtre pour ActionType et remplacez la ligne de synthèse par une projection des champs souhaités (dans ce cas, il s’agit de DeviceName, FileName, FolderPath, etc.).

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting4b.png" alt-text="Exemple de requête de chasse avancée axée sur le portail Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting4b.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting5b.png" alt-text="La requête de chasse avancée a porté sur les résultats dans le portail Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting5b.png":::

Le véritable avantage de la chasse avancée est que vous pouvez mettre en forme les requêtes à votre goût. En mettant en forme votre requête, vous pouvez voir l’histoire exacte de ce qui se passait, que vous souhaitiez identifier quelque chose sur un ordinateur individuel ou que vous souhaitiez extraire des insights de l’ensemble de votre environnement.

Pour plus d’informations sur les options de chasse, consultez : [Démystifier les règles de réduction de la surface d’attaque - Partie 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968).

## <a name="topics-in-this-deployment-collection"></a>Rubriques de cette collection de déploiement

[Vue d’ensemble du déploiement des règles de réduction de surface d’attaque (ASR)](attack-surface-reduction-rules-deployment.md)

[Planifier le déploiement des règles de réduction de surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-plan.md)

[Tester des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-test.md)

[Activer des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-implement.md)

[Référence des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-reference.md)
