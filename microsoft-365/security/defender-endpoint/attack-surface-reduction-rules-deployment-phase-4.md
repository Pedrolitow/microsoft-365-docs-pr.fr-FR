---
title: 'Phase de déploiement des règles asr 4 : opérationnel'
description: Fournit des conseils pour rendre opérationnel le déploiement de vos règles de réduction de la surface d’attaque.
keywords: Déploiement des règles de réduction de la surface d’attaque, déploiement de la réduction de la surface d’attaque, activer les règles d’attaque, configurer la réduction de la surface d’attaque, système de prévention des intrusions hôte, règles de protection, règles anti-attaque, règles d’attaque, règles de prévention des infections, Microsoft Defender pour le point de terminaison, configurer des règles de réduction de la surface d’attaque
search.product: eADQiWindows 10XVcnh
ms.reviewer: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 7c06be427df2425a2160201324a6ed267d88d0fd
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2021
ms.locfileid: "61218333"
---
# <a name="attack-surface-reduction-rules-deployment-phase-4-operationalize"></a>Phase 4 du déploiement des règles de réduction de la surface d’attaque : opérationnaliser

Une fois que vous avez déployé entièrement les règles de la asr, il est essentiel de mettre en place des processus pour surveiller et répondre aux activités liées à la asr.

## <a name="manage-false-positives"></a>Gérer les faux positifs

Les faux positifs/négatifs peuvent se produire avec n’importe quelle solution de protection contre les menaces. Les faux positifs sont des cas dans lesquels une entité (telle qu’un fichier ou un processus) est détectée et identifiée comme malveillante, bien que l’entité ne soit pas réellement une menace. En revanche, un faux négatif est une entité qui n’a pas été détectée comme une menace, mais qui est malveillante. Pour plus d’informations sur les faux positifs et les faux négatifs, voir : Traiter les [faux positifs/négatifs dans Microsoft Defender pour endpoint](defender-endpoint-false-positives-negatives.md)

## <a name="keeping-up-with-reports"></a>Suivi des rapports

Un examen cohérent et régulier des rapports est un aspect essentiel de la maintenance du déploiement de vos règles de asr et de la conservation des nouvelles menaces émergentes. Votre organisation doit avoir programmé des révisions des événements de règles de la asr à une cadence qui restera à jour avec les événements signalés par les règles de la asr. Selon la taille de votre organisation, les avis peuvent être une surveillance quotidienne, horaire ou continue.

## <a name="hunting"></a>Repérage

L’une des fonctionnalités les plus [puissantes de Microsoft 365 Defender](https://securitycenter.microsoft.com) est la recherche avancée. Si vous n’êtes pas familiarisé avec le chasse avancée, voir : recherchez de manière proactive les menaces [avec le chasse avancée.](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender de recherche avancée](images/asr-defender365-advanced-hunting2.png)

Le repérage avancé est un outil de repérage de menaces basé sur une requête (Kusto Query Language) qui vous permet d’explorer jusqu’à 30 jours des données capturées (brutes) collectées par Microsoft Defender ATP Endpoint Detection and Response (PEPT) à partir de tous vos ordinateurs. Grâce à la recherche avancée, vous pouvez inspecter de manière proactive les événements afin de localiser des indicateurs et des entités intéressants. L’accès flexible aux données facilite le repérage sans contrainte pour les menaces connues et potentielles.

Grâce à la recherche avancée, il est possible d’extraire des informations sur les règles de la asr, de créer des rapports et d’obtenir des informations détaillées sur le contexte d’un événement d’audit ou de blocage de règle asr donné.

 Vous pouvez interroger les événements de règles asr à partir de la table DeviceEvents dans la section de recherche avancée du portail Microsoft 365 Defender. Par exemple, une requête simple, telle que celle ci-dessous, peut signaler tous les événements qui ont des règles de asr en tant que source de données, au cours des 30 derniers jours, et les synthétisera par le nombre ActionType, qui dans ce cas sera le nom de code réel de la règle asr.

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender ligne de commande de requête de recherche avancée](images/asr-defender365-advanced-hunting3.png)

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender de requête de recherche avancée](images/asr-defender365-advanced-hunting4.png)

L’exemple ci-dessus indique que 187 événements ont été enregistrés pour AsrLsassCredentialTheft :

- 102 pour bloqué
- 85 pour audit
- 2 événements pour AsrOfficeChildProcess (1 pour Audited et 1 pour Block)
- 8 événements pour AsrPsexecWmiChildProcessAudited

Si vous souhaitez vous concentrer sur la règle AsrOfficeChildProcess et obtenir des détails sur les fichiers et processus impliqués, modifiez le filtre pour ActionType et remplacez la ligne de synthèse par une projection des champs souhaités (dans ce cas, il s’agit de DeviceName, FileName, FolderPath, etc.).

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender requête de recherche avancée axée sur](images/asr-defender365-advanced-hunting4b.png)

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender résultats de requête de recherche avancée](images/asr-defender365-advanced-hunting5b.png)

Le véritable avantage de la recherche avancée est que vous pouvez mettre en forme les requêtes à votre convenance. La mise en forme de votre requête vous permet de voir l’histoire exacte de ce qui se passe, que vous vouliez épingler quelque chose sur un ordinateur individuel ou que vous vouliez extraire des informations de l’ensemble de votre environnement.

Pour plus d’informations sur les options de recherche, voir : [Démystification](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)des règles de réduction de la surface d’attaque - Partie 3 .

## <a name="topics-in-this-deployment-collection"></a>Rubriques de cette collection de déploiements

[Guide de déploiement des règles asr : vue d’ensemble](attack-surface-reduction-rules-deployment.md)

[Phase de déploiement des règles asr 1 : planifier](attack-surface-reduction-rules-deployment-phase-1.md)

[Phase de déploiement des règles asr 2 : test](attack-surface-reduction-rules-deployment-phase-2.md)

[Phase 3 de déploiement des règles asr : implémenter](attack-surface-reduction-rules-deployment-phase-3.md)