---
title: Informations de fiabilité
description: ''
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 06e1446ca290439c9e6689f4461c825438cf6aaf
ms.sourcegitcommit: cebbdd393dcfd93ff43a1ab66ad70115853f83e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2021
ms.locfileid: "52739782"
---
# <a name="reliability-insights"></a>Informations de fiabilité

Cette vue vous fournit un résumé d’état de vos appareils gérés. Pour afficher les données de fiabilité, sélectionnez **l’onglet** Fiabilité.


![Volet de fiabilité : fiabilité sur les appareils en haut à gauche, fiabilité dans le graphique dans le temps en haut à droite, tableau des problèmes les plus élevés dans la partie inférieure. Boutons d’aide et de commentaires en bas à droite.](../../media/insights_reliability.png)

La **section** Fiabilité sur les appareils offre un résumé d’état d’état rapide de votre déploiement au cours des 14 derniers jours en signalant le pourcentage d’appareils considérés comme « sains » et le temps moyen observé depuis la dernière défaillance signalée. 

 
Le **graphique Fiabilité au fil du** temps sur la droite indique le nombre d’appareils avec des erreurs critiques et le nombre total d’erreurs critiques observées au fil du temps.

La **section Principaux problèmes** détaille les problèmes détectés spécifiques qui affectent au moins 5 % de vos appareils gérés. Les détails signalés sont les suivants :

- Type de problème
    - L’application se bloque, au cours de laquelle une application cesse de fonctionner ou s’arrête de manière inattendue
    - L’application se bloque, où une application cesse de répondre aux entrées
    - Erreurs critiques, qui se produisent lorsque Windows a rencontré un problème dont il ne peut pas récupérer
- Nombre d’appareils affectés par le même problème
- Pourcentage d’appareils gérés représenté par le nombre
- Nombre total d’occurrences du problème spécifique
- Composant logiciel qui semble être la source du problème
- Catégorie du problème détecté :
    - Navigateur (Edge, Chrome, IE)
    - Inconnu (composants autres que Microsoft)
    - Pilote (audio, graphiques ou autres pilotes)
    - Productivité (Slack, G-Suites, Microsoft Office et ses extensions ou extensions, Teams)
    - Média (applications d’image, de musique ou de vidéo)
    - Sécurité (Windows composants de sécurité)
- L’état actuel de Bureau géré Microsoft Operations examine et remédie au problème

