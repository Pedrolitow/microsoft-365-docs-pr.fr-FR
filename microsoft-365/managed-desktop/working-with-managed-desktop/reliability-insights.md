---
title: Informations de fiabilité
description: ''
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 06e1446ca290439c9e6689f4461c825438cf6aaf
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47950341"
---
# <a name="reliability-insights"></a>Informations de fiabilité

Cet affichage vous fournit un résumé de l’intégrité de vos appareils gérés. Pour afficher les données de fiabilité, sélectionnez l’onglet **fiabilité** .


![Volet de fiabilité : fiabilité entre les appareils dans l’angle supérieur gauche, fiabilité sur le graphique des temps dans le coin supérieur droit de la table des problèmes en haut. Boutons aide et commentaires dans le coin inférieur droit.](../../media/insights_reliability.png)

La section **fiabilité sur les appareils** offre un récapitulatif de l’intégrité rapide de votre déploiement au cours des 14 derniers jours en signalant le pourcentage d’appareils considérés comme « sains » et le temps moyen observé depuis le dernier échec signalé. 

 
La **fiabilité** dans le graphique temporel signale le nombre d’appareils présentant des erreurs critiques et le nombre total d’erreurs critiques observées au fil du temps.

La section des **problèmes principaux** explique en détail des problèmes détectés spécifiques affectant au moins 5% de vos appareils gérés. Les détails signalés sont les suivants :

- Type de problème
    - L’application se bloque, dans laquelle une application cesse de fonctionner ou s’arrête de manière inattendue
    - L’application se bloque lorsqu’une application cesse de répondre aux entrées
    - Erreurs critiques, qui se produisent lorsque Windows a rencontré un problème qu’il ne peut pas récupérer à partir de
- Nombre d’appareils affectés par le même problème
- Pourcentage d’appareils gérés que le nombre représente
- Nombre total d’occurrences du problème spécifique
- Composant logiciel qui semble être à l’origine du problème
- Catégorie du problème détecté :
    - Navigateur (Edge, chrome, IE)
    - Inconnu (composants non-Microsoft)
    - Pilote (audio, graphiques ou autres pilotes)
    - Productivité (marge, G-Suites, Microsoft Office et ses compléments ou extensions, Teams)
    - Applications multimédia (image, musique ou vidéo)
    - Sécurité (composants de sécurité Windows)
- État actuel lorsque Microsoft Managed Desktop Operations examine et corrige le problème

