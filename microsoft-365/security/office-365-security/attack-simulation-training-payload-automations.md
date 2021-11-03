---
title: Automatisations de charge utile pour la formation à la simulation d’attaques
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent apprendre à utiliser les automatisations de charge utile (collecte de charge utile) pour collecter et lancer des simulations automatisées pour la formation à la simulation d’attaques dans Microsoft Defender pour Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: 0e090b79c8e04de5f0e9e81449d805d2b124bc59
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60717623"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Automatisations de charge utile pour la formation à la simulation d’attaques

**S’applique** [à Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Dans la formation sur la simulation d’attaques dans Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2, les automatisations de charge utile (également appelées collecte de charge _utile)_ collectent des informations à partir de messages de hameçonnage réels signalés par les utilisateurs de votre organisation. Bien que le nombre de ces messages soit probablement faible dans votre organisation, vous pouvez spécifier les conditions à rechercher dans les attaques par hameçonnage (par exemple, les destinataires, la technique d’ingénierie sociale, les informations sur l’expéditeur, etc.). L’entraînement de simulation d’attaque imite ensuite les messages et les charges utiles utilisés dans l’attaque pour lancer automatiquement des simulations sans danger pour les utilisateurs ciblés.

Pour créer une automatisation de charge utile, faites les étapes suivantes :

1. Dans le portail Microsoft 365 Defender à l’adresse , go <https://security.microsoft.com/> to Email & **collaboration** Attack \> **simulation training** Payload \> **automations** tab.

   Pour aller directement à l’onglet **Automatisations de la charge** utile, utilisez <https://security.microsoft.com/attacksimulator?viewid=payloadautomation> .

2. Sous **l’onglet Automatisations de la charge** utile, ![ sélectionnez Créer une icône de simulation.](../../media/m365-cc-sc-create-icon.png) **Créer une simulation.**

   ![Créez un bouton de simulation sous l’onglet Automatisations de la charge utile dans la formation à la simulation d’attaques dans Microsoft 365 Defender portail.](../../media/attack-sim-training-sim-automations-create.png)

3. L’Assistant Création s’ouvre. Le reste de cet article décrit les pages et les paramètres qu’elles contiennent.

> [!NOTE]
> À tout moment pendant l’Assistant  création de simulation, vous pouvez cliquer sur Enregistrer et fermer pour enregistrer votre progression et continuer à configurer la simulation ultérieurement. La simulation incomplète a la valeur **d’état** **Brouillon** sous **l’onglet Simulations.** Vous pouvez reprendre là où vous vous êtes laissé en sélectionnant la simulation et en cliquant sur ![ Modifier l’icône de simulation.](../../media/m365-cc-sc-edit-icon.png) **Modifiez** le nom de la simulation.## et décrivez la simulation.

## <a name="automation-name"></a>Nom d’automation

Dans la page **nom Automation,** configurez les paramètres suivants :

- **Nom**: entrez un nom unique et descriptif pour la simulation.
- **Description**: entrez une description détaillée facultative de la simulation.

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="run-conditions"></a>Conditions d’exécuter

Dans la page **Conditions d’utilisation,** sélectionnez les conditions de l’attaque par hameçonnage réelle qui détermine à quel moment l’automatisation s’exécutera.

Vous ne pouvez utiliser chaque condition qu’une seule fois. Plusieurs conditions utilisent la logique AND ( \<Condition1\> et \<Condition2\> ).

![Icône Ajouter une condition.](../../media/m365-cc-sc-create-icon.png) **Ajouter une condition**.

- **Non. des utilisateurs ciblés dans la campagne**: Configurez les paramètres suivants :
  - **Égal à**, **Inférieur** à , **Supérieur à**, Inférieur ou égal **à**, ou Supérieur ou **égal à**.
  - **Entrez la valeur**: nombre d’utilisateurs ciblés par la campagne de hameçonnage.
- **Campagnes avec une technique de hameçonnage spécifique**: sélectionnez l’une des valeurs disponibles :
  - **Informations d’identification**
  - **Pièce jointe de programme malveillant**
  - **Lien dans la pièce jointe**
  - **Lien vers un programme malveillant**
  - **URL de lecteur par**
- **Domaine d’expéditeur spécifique**: entrez une valeur de domaine de messagerie de l’expéditeur (par exemple, contoso.com).
- **Nom d’expéditeur spécifique**: entrez une valeur de nom d’expéditeur.
- **Courrier électronique de l’expéditeur spécifique**: entrez une adresse de messagerie de l’expéditeur.
- **Utilisateurs et destinataires de groupe spécifiques**: commencez à taper le nom ou l’adresse e-mail de l’utilisateur ou du groupe. Lorsqu’il apparaît, sélectionnez-le.

Pour supprimer une condition après l’avoir ajoutée, cliquez sur ![Icône Supprimer.](../../media/m365-cc-sc-delete-icon.png).

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="review-automation"></a>Passer en revue l’automatisation

Dans la page **Examiner l’automatisation,** vous pouvez consulter les détails de l’automatisation de votre charge utile.

Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

Lorsque vous avez terminé, cliquez sur **Envoyer**.
