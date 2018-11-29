---
title: Gestion des mises à jour dans le bureau géré Microsoft
description: Mise à jour de bureau Microsoft est un équilibre entre la vitesse et la stabilité.
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: jdeckerms
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: 513e03b7d703e0a9f78281ddac764d8a29ed5c8f
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866945"
---
# <a name="how-updates-are-handled-in-microsoft-managed-desktop"></a>Gestion des mises à jour dans le bureau géré Microsoft


<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/update-rings); do not delete.-->

<!--Update management -->

Ordinateur de bureau Microsoft se connecte à tous les périphériques à une infrastructure moderne basée sur le cloud. Windows, Office, les pilotes, microprogrammes et Microsoft Store pour les mises à jour des applications métiers mise à jour est un équilibre entre la vitesse et la stabilité. Sonneries de déploiement seront utilisés pour s’assurer du système d’exploitation et de déploiement des stratégies de manière sûre. 

## <a name="update-rings"></a>Mise à jour sonne

Ordinateur de bureau Microsoft utilise quatre groupes Azure AD pour gérer les mises à jour :

- Test : L’anneau test est conçu uniquement pour le test et validation des modifications apportées dans le client du client.  
- Premier : Premier est destiné à être un anneau de test au plus tôt avec les utilisateurs expérimentés tech limité qui sont prêts à installer le logiciel au début et être soumis à certaines mises à jour de la version préliminaire.
- Rapide : L’anneau rapide est où nous pouvons prévoir un vaste ensemble d’utilisateurs.  L’objectif de cet anneau consiste à conserver les périphériques mis à jour et de sécurité avec un rythme rapide de distribution de logiciels.  
- Étendue : L’anneau lente est un déploiement estime équilibré de qualité et les fonctionnalités mises à jour.  Mises à jour de la qualité sont toujours remis à un rapide rythme, mais pas immédiatement. 

Les mises à jour dans le système de sonnerie d’appel sont considérés comme qualité ou fonctionnalités mises à jour :
- Mises à jour de qualité incluent la sécurité, critique et mises à jour.  Il s’agit généralement mensuels mises à jour. 
- Mises à jour de la fonctionnalité contiennent non seulement la sécurité révisions de qualité, mais également les ajouts de fonctionnalité significative et modifications ; elles sont publiées semestrielle. 

Fonctionne de la promotion de la sonnerie :
- Ordinateur de bureau Microsoft déploie une nouvelle fonctionnalité ou la qualité mise à jour en fonction de la planification spécifiée ci-dessous.
- Au cours du déploiement de bureau Microsoft surveille des signes de défaillance ou de toute autre interruption (via les signaux de télémétrie et de notre système de prise en charge de l’utilisateur final) ; Si les sont détectés, le déploiement à tous les sonneries actuelles et futures est immédiatement suspendu.
    - Exemple : si un problème est détecté lors du déploiement d’une mise à jour de qualité à la première sonnerie, puis tout d’abord, rapide et large seront tous être suspendue jusqu'à ce que le problème est résolu.
    - Problèmes de compatibilité peuvent être signalés par un ticket de classement dans le portail Microsoft gérées bureau IT Admin.
- Fonctionnalité et la qualité des mises à jour sont suspendues indépendamment.  Pause est en vigueur pour 35 jours par défaut, mais peut être réduit ou étendue selon si le problème est résolue.
- Une fois les sonneries reprises, déploiement reprend en fonction de la planification ci-dessous.
- Ce processus de promotion s’applique aux mises à jour de fonctionnalité et de qualité, bien que la chronologie varie pour chacun.

<table>
<tr><th colspan="5">Sonneries et les paramètres de report</th></tr>
<tr><th>Type de mise à jour</th><th>Sonnerie d’appel test</th><th>Premier</th><th>Rapide</th><th>Large</th></tr>
<tr><td>Mises à jour de la qualité pour le système d’exploitation</td><td>0 jours</td><td>0 jours</td><td>1 jour</td><td>5 jours</td></tr>
<tr><td>Mises à jour de la fonctionnalité de système d’exploitation</td><td>Canal semestrielle (ciblés) + 0 jours</td><td>Canal semestrielle (ciblés) + 30 jours</td><td>Canal semestrielle (ciblés) + 60 jours</td><td>Canal semestrielle + 30 jours</td></tr>
<tr><td>Pilotes/microprogrammes</td><td colspan="4">Suit la planification des mises à jour de la qualité</td></tr>
<tr><td>Définition de virus</td><td colspan="4">Mise à jour avec chaque analyse</td></tr>
<tr><td>Cliquez sur Office Plus proactive exécuter</td><td colspan="4">Aligné sur le canal semestrielle</td></tr>
</table>


## <a name="windows-insider-program"></a>Programme internes de Windows

Ordinateur de bureau Microsoft ne gère pas les périphériques qui font partie du programme Windows internes. Ce programme est utilisé pour valider la version préliminaire du logiciel Windows et est destiné aux périphériques critiques non stratégiques. Alors que c’est une initiative Microsoft importante, elle n’est pas destinée pour le déploiement dans les environnements de production. 

Tous les périphériques avec les versions de Windows initiés seront placées dans l’anneau de Test et ne pas être inclus dans la mise à jour SLA.

## <a name="bandwidth-management"></a>Gestion de bande passante

Optimisation de la remise est utilisée pour le fonctionnement de toutes les mises à jour de système et du pilote. Elle réduit la taille de téléchargement à partir du service Windows Update (WU) en recherchant des mises à jour de homologues au sein du réseau d’entreprise.


