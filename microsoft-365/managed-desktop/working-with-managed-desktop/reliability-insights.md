---
title: Informations de fiabilité
description: ''
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: f830e01d54aef9065727971533633f8e63bc1214
ms.sourcegitcommit: e292e9f0181d722a11398fbd012bb84589aef052
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257032"
---
# <a name="reliability-insights"></a>Informations de fiabilité

Cet affichage vous fournit un résumé de l’intégrité de vos appareils gérés. Pour afficher les données de fiabilité, sélectionnez l’onglet **fiabilité** .


![Volet de fiabilité](images/insights_reliability.png)

La section **fiabilité sur les appareils** offre un récapitulatif de l’intégrité rapide de votre déploiement au cours des 14 derniers jours en signalant le pourcentage d’appareils considérés comme « sains » et le temps moyen observé depuis le dernier échec signalé. 

 
La **fiabilité** dans le graphique temporel signale le nombre d’appareils présentant des erreurs critiques et le nombre total d’erreurs critiques observées au fil du temps.

La section des **problèmes principaux** explique en détail des problèmes détectés spécifiques affectant au moins 5% de vos appareils gérés. Les détails signalés sont les suivants :

- Type de problème
    - L’application se bloque, dans laquelle une application cesse de fonctionner ou s’arrête de manière inattendue
    - L’application se bloque lorsqu’une application cesse de répondre aux entrées
    - Erreurs critiques, qui se produisent lorsque Windows a rencontré un problème qu’il ne peut pas récupérer à partir de
- Nombre d’appareils affectés par le même problème
- Pourcentage d’appareils gérés que le nombre représente
- Nombre total d’occurrences d’un problème spécifique
- Composant logiciel qui semble être à l’origine du problème
- État actuel lorsque Microsoft Managed Desktop Operations examine et corrige le problème

