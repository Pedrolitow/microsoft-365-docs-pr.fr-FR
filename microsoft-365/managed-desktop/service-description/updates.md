---
title: Gestion des mises à jour dans le bureau géré Microsoft
description: Mise à jour de bureau Microsoft est un équilibre entre la vitesse et la stabilité.
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 01/09/2019
ms.openlocfilehash: bee6381b0f2b7b1e2d929329c3cf628ab7657678
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26866945"
---
# <a name="how-updates-are-handled-in-microsoft-managed-desktop"></a>Gestion des mises à jour dans le bureau géré Microsoft


<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/update-rings); do not delete.-->

<!--Update management -->

Ordinateur de bureau Microsoft se connecte à tous les périphériques à une infrastructure moderne basée sur le cloud. Windows, Office, les pilotes, microprogrammes et Microsoft Store pour les mises à jour des applications métiers mise à jour est un équilibre entre la vitesse et la stabilité. Sonneries de déploiement seront utilisés pour s’assurer du système d’exploitation et de déploiement des stratégies de manière sûre. 

## <a name="update-groups"></a>Mettre à jour des groupes

Ordinateur de bureau Microsoft utilise quatre groupes Azure AD pour gérer les mises à jour :

- Test : Périphériques de non-production destinées à valider les modifications avant de déployer les modifications sur le reste du client. Périphériques de cet anneau sont hors de portée de prise en charge de l’utilisateur final documentée. 
- Premier : Contient des premiers logiciels, et les périphériques peuvent être soumis à des mises à jour de la version préliminaire.
- Rapide : Hiérarchise vitesse sur la stabilité. Utile pour détecter les problèmes de qualité avant d’être au groupe de large. 
- Large : Dernier groupe pour la fonctionnalité et la qualité des mises à jour sont disponibles. Ce groupe contient la majorité des utilisateurs dans le client et par conséquent favorisant stabilité la vitesse de déploiement.

Mises à jour publiées par Microsoft sont cumulatifs et peuvent être classées en tant que la qualité ou la fonctionnalité mises à jour. Pour plus d’informations, voir [mise à jour Windows : Forum aux questions sur](https://support.microsoft.com/help/12373/windows-update-faq). 

Comment mettre à jour les travaux de déploiement :
- Ordinateur de bureau Microsoft déploie une nouvelle fonctionnalité ou la qualité mise à jour en fonction de la planification spécifiée ci-dessous.
- Au cours du déploiement de bureau Microsoft surveille des signes de défaillance ou d’interruption (basé sur des signaux de télémétrie et système de prise en charge de l’utilisateur final). Si les sont détectés, le déploiement à tous les groupes actuels et futurs est immédiatement suspendu.
    - Exemple : si un problème est détecté lors du déploiement d’une mise à jour de la qualité au premier groupe, puis les déploiements de mise à jour préalable, rapide et large seront tous être suspendues jusqu'à ce que le problème est résolu.
    - Problèmes de compatibilité peuvent être signalés par un ticket de classement dans le portail Microsoft gérées bureau IT Admin.
- Fonctionnalité et la qualité des mises à jour sont suspendues indépendamment. Pause est en vigueur pour 35 jours par défaut, mais peut être réduit ou étendue selon si le problème est résolue.
- Une fois que les groupes sont non suspendus, déploiement reprend en fonction de la planification ci-dessous.
- Ce processus de déploiement s’applique aux mises à jour de fonctionnalité et de qualité, bien que la chronologie varie pour chacun.

<table>
<tr><th colspan="5">Mettre à jour les paramètres de déploiement</th></tr>
<tr><th>Type de mise à jour</th><th>Tester</th><th>Premier</th><th>Rapide</th><th>Large</th></tr>
<tr><td>Mises à jour de la qualité pour le système d’exploitation</td><td>0 jours</td><td>0 jours</td><td>0 jours</td><td>3 jours</td></tr>
<tr><td>Mises à jour de la fonctionnalité de système d’exploitation</td><td>0 jours</td><td>30 jours</td><td>60 jours</td><td>90 jours</td></tr>
<tr><td>Pilotes/microprogrammes</td><td colspan="4">Suit la planification des mises à jour de la qualité</td></tr>
<tr><td>Définition de virus</td><td colspan="4">Mise à jour avec chaque analyse</td></tr>
</table>

Ces périodes d’exclusion sont conçues pour garantir une haute sécurité et les normes de performance pour tous les utilisateurs. En outre, basé sur les données collectées sur tous les périphériques de bureau Microsoft et l’étendue et l’impact des mises à jour différentes, de bureau Microsoft réserve flexibilité pour modifier la longueur des périodes report ci-dessus pour les groupes de tout déploiement sur une annonce base hoc.

## <a name="windows-insider-program"></a>Programme internes de Windows

Ordinateur de bureau Microsoft ne gère pas les périphériques qui font partie du programme Windows internes. Le programme Windows interne est utilisé pour valider la version préliminaire du logiciel Windows et est destiné aux périphériques critiques non stratégiques. Alors que c’est une initiative Microsoft importante, elle n’est pas destinée pour le déploiement dans les environnements de production. 

Tous les périphériques avec les versions de Windows initiés figureront dans le groupe de tests et ne pas être inclus dans la mise à jour les contrats de niveau de service (SLA.

## <a name="bandwidth-management"></a>Gestion de bande passante

Optimisation de la remise est utilisée pour le fonctionnement de toutes les mises à jour de système et du pilote. Elle réduit la taille de téléchargement à partir du service Windows Update (WU) en recherchant des mises à jour de homologues au sein du réseau d’entreprise.


