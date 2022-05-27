---
title: Automatisations de charge utile pour l’entraînement de simulation d’attaque
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent apprendre à utiliser les automatisations de charge utile (collecte de charge utile) pour collecter et lancer des simulations automatisées pour l’entraînement de simulation d’attaque dans Microsoft Defender pour Office 365 plan 2.
ms.technology: mdo
ms.openlocfilehash: 862547884f9a7697382affda734af0f323c86c4a
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739558"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Automatisations de charge utile pour l’entraînement de simulation d’attaque

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à** [Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Dans la formation de simulation d’attaque dans Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2, les automatisations de charge utile (également appelées _collectes de charge utile_) collectent des informations à partir de messages de hameçonnage réels signalés par les utilisateurs de votre organisation. Bien que le nombre de ces messages soit probablement faible dans votre organisation, vous pouvez spécifier les conditions à rechercher dans les attaques par hameçonnage (par exemple, les destinataires, la technique d’ingénierie sociale, les informations de l’expéditeur, etc.). L’entraînement de simulation d’attaque imite ensuite les messages et les charges utiles utilisés dans l’attaque pour lancer automatiquement des simulations inoffensifs pour les utilisateurs ciblés.

Pour créer une automatisation de charge utile, procédez comme suit :

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com/>l’onglet **Automatisations** de la charge utile de l’onglet \> Email **& Collaboration** \> **Attack Simulation Training** \> **Automations**.

   Pour accéder directement à l’onglet **Automations** où vous pouvez sélectionner **Les automatisations de charge utile**, utilisez <https://security.microsoft.com/attacksimulator?viewid=automations>.

2. Dans **Les automatisations de charge utile**, sélectionnez ![l’icône Créer une automatisation.](../../media/m365-cc-sc-create-icon.png) **Créez l’automatisation**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Bouton Créer une simulation sous l’onglet Automations de la charge utile dans l’entraînement de simulation d’attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

3. L’Assistant Création s’ouvre. Le reste de cet article décrit les pages et les paramètres qu’elles contiennent.

> [!NOTE]
> À tout moment pendant l’Assistant création, vous pouvez cliquer sur **Enregistrer et fermer** pour enregistrer votre progression et continuer à configurer l’automatisation de la charge utile ultérieurement. Vous pouvez reprendre là où vous vous étiez arrêté en sélectionnant l’automatisation de charge utile dans **les automatisations** de charge utile, puis en ![cliquant sur l’icône Modifier l’automatisation.](../../media/m365-cc-sc-edit-icon.png) **Modifier l’automatisation**.

## <a name="automation-name"></a>Nom de l’automatisation

Dans la page **de noms Automation** , configurez les paramètres suivants :

- **Nom** : entrez un nom unique et descriptif pour l’automatisation de la charge utile.
- **Description** : entrez une description détaillée facultative pour l’automatisation de la charge utile.

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="run-conditions"></a>Conditions d’exécution

Dans la page **Conditions** d’exécution, sélectionnez les conditions de l’attaque par hameçonnage réelle qui détermine quand l’automatisation s’exécutera.

Vous ne pouvez utiliser chaque condition qu’une seule fois. Plusieurs conditions utilisent la logique AND (\<Condition1\> et \<Condition2\>).

![Icône Ajouter une condition.](../../media/m365-cc-sc-create-icon.png) **Ajouter une condition**.

- **Non. des utilisateurs ciblés dans la campagne** : configurez les paramètres suivants :
  - **Égal à**, **Inférieur** à, **Supérieur** à, **Inférieur ou égal à**, ou **Supérieur ou égal à**.
  - **Valeur d’entrée** : nombre d’utilisateurs ciblés par la campagne de hameçonnage.
- **Campagnes avec une technique spécifique de hameçonnage** : sélectionnez l’une des valeurs disponibles :
  - **Collecte des informations d’identification**
  - **Pièce jointe de programme malveillant**
  - **Lien dans la pièce jointe**
  - **Lien vers un programme malveillant**
  - **Drive-by URL**
- **Domaine d’expéditeur spécifique** : entrez une valeur de domaine de messagerie de l’expéditeur (par exemple, contoso.com).
- **Nom d’expéditeur spécifique** : entrez une valeur de nom d’expéditeur.
- **E-mail de l’expéditeur spécifique** : entrez une adresse e-mail de l’expéditeur.
- **Destinataires d’utilisateurs et de groupes spécifiques** : commencez à taper le nom ou l’adresse e-mail de l’utilisateur ou du groupe. Lorsqu’il apparaît, sélectionnez-le.

Pour supprimer une condition après l’avoir ajoutée, cliquez sur ![Icône Supprimer.](../../media/m365-cc-sc-delete-icon.png).

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="review-automation"></a>Passer en revue l’automatisation

Dans la page **Vérifier l’automatisation** , vous pouvez consulter les détails de votre automatisation de charge utile.

Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

Lorsque vous avez terminé, cliquez sur **Envoyer**.
