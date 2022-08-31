---
title: Automatisations de charge utile pour Exercice de simulation d'attaque
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.service: microsoft-365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent apprendre à utiliser les automatisations de charge utile (collecte de charge utile) pour collecter et lancer des simulations automatisées pour Exercice de simulation d'attaque dans Microsoft Defender pour Office 365 plan 2.
ms.subservice: mdo
ms.openlocfilehash: 340ca76086e7696017e1433433a5294a8003b225
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67480468"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Automatisations de charge utile pour Exercice de simulation d'attaque

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à** [Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Dans Exercice de simulation d'attaque dans Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2, les automatisations de charge utile (également appelées _collectes de charge utile_) collectent des informations à partir de messages d’attaque par hameçonnage réels signalés par les utilisateurs dans votre Organisation. Bien que le nombre de ces messages soit probablement faible dans votre organisation, vous pouvez spécifier les conditions à rechercher dans les attaques par hameçonnage (par exemple, les destinataires, la technique d’ingénierie sociale, les informations de l’expéditeur, etc.). Exercice de simulation d'attaque imitera ensuite les messages et les charges utiles utilisés dans l’attaque pour lancer automatiquement des simulations sans danger pour les utilisateurs ciblés.

Pour voir les automatisations de charge utile disponibles, ouvrez le portail Microsoft 365 Defender à <https://security.microsoft.com>l’adresse **Email & collaboration** \> **Exercice de simulation d'attaque** \> onglet \> **Automations**, puis sélectionnez **Automations de charge utile**. Pour accéder directement à l’onglet **Automations** où vous pouvez sélectionner **Les automatisations de charge utile**, utilisez <https://security.microsoft.com/attacksimulator?viewid=automations>.

Les informations suivantes s’affichent pour chaque automatisation de charge utile :

- **Nom de l’automatisation**
- **Type** : la valeur est **Payload**.
- **Éléments collectés**
- **Dernière modification**
- **État** : la valeur est **Ready** ou **Draft**.

Lorsque vous sélectionnez une automatisation de charge utile dans la liste, un menu volant de détails s’affiche avec les informations suivantes :

- **Onglet Général** : affiche des informations de base sur l’automatisation de simulation.
- Onglet **Historique des exécutions** : cet onglet est disponible uniquement pour les automatisations de charge utile avec la valeur **État** **Prête**.

## <a name="create-payload-automations"></a>Créer des automatisations de charge utile

Pour créer une automatisation de charge utile, procédez comme suit :

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com/>accédez à **Email & collaboration** \> **Exercice de simulation d'attaque** \> **automations** de l’onglet \> **Automations.** Pour accéder directement à l’onglet **Automations** où vous pouvez sélectionner **Les automatisations de charge utile**, utilisez <https://security.microsoft.com/attacksimulator?viewid=automations>.

   Cliquez sur l’icône ![Créer une automatisation.](../../media/m365-cc-sc-create-icon.png) **Créez l’automatisation**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Bouton Créer une simulation sous l’onglet Automations de la charge utile dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

   > [!NOTE]
   > À tout moment pendant l’Assistant création, vous pouvez cliquer sur **Enregistrer et fermer** pour enregistrer votre progression et continuer à configurer l’automatisation de la charge utile ultérieurement. Vous pouvez reprendre là où vous vous étiez arrêté en sélectionnant l’automatisation de charge utile dans **les automatisations** de charge utile, puis en ![cliquant sur l’icône Modifier l’automatisation.](../../media/m365-cc-sc-edit-icon.png) **Modifier l’automatisation**. L’automatisation de charge utile partiellement terminée aura la valeur **Status** **Draft**.

2. Dans la page **de noms Automation** , configurez les paramètres suivants :

   - **Nom** : entrez un nom unique et descriptif pour l’automatisation de la charge utile.
   - **Description** : entrez une description détaillée facultative pour l’automatisation de la charge utile.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

3. Dans la page **Conditions** d’exécution, sélectionnez les conditions de l’attaque par hameçonnage réelle qui détermine quand l’automatisation s’exécutera.

   Cliquez sur ![l’icône Ajouter une condition.](../../media/m365-cc-sc-create-icon.png) **Ajoutez une condition** et sélectionnez l’une des conditions suivantes :

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

   Vous ne pouvez utiliser chaque condition qu’une seule fois. Plusieurs conditions utilisent la logique AND (\<Condition1\> et \<Condition2\>).

   Pour ajouter une autre condition, cliquez sur ![l’icône Ajouter une condition.](../../media/m365-cc-sc-create-icon.png) **Ajouter une condition**.

   Pour supprimer une condition après l’avoir ajoutée, cliquez sur ![Icône Supprimer.](../../media/m365-cc-sc-delete-icon.png).

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Vérifier l’automatisation** , vous pouvez consulter les détails de votre automatisation de charge utile.

   Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

5. Dans la page **Nouvelle automatisation créée** , vous pouvez utiliser les liens pour activer l’automatisation ou accéder à la page **Simulations** .

   Lorsque vous avez terminé, cliquez sur **Terminé**.

De retour sur les **automatisations de charge utile** dans **Automations**, la page de connexion que vous avez créée est maintenant répertoriée.

## <a name="turn-payload-automations-on-or-off"></a>Activer ou désactiver les automatisations de charge utile

Vous pouvez uniquement activer ou désactiver les automatisations de charge utile lorsque la valeur **d’état** est **Prêt**. Vous ne pouvez pas activer ou désactiver les automatisations de charge utile incomplètes où la valeur **Status** est **Draft**.

Pour activer une automatisation de charge utile, sélectionnez-la dans la liste en cliquant sur la case à cocher. Cliquez sur l’icône ![Activer.](../../media/m365-cc-sc-turn-on-off-icon.png) **Activez l’icône** qui s’affiche, puis cliquez sur **Confirmer** dans la boîte de dialogue.

Pour désactiver une automatisation de charge utile, sélectionnez-la dans la liste en cliquant sur la case à cocher. Cliquez sur l’icône ![Désactiver.](../../media/m365-cc-sc-turn-on-off-icon.png) **Activez l’icône** qui s’affiche, puis cliquez sur **Confirmer** dans la boîte de dialogue.

## <a name="modify-payload-automations"></a>Modifier les automatisations de charge utile

Pour modifier une automatisation de charge utile existante dans **les automatisations de charge utile, effectuez** l’une des étapes suivantes :

- Sélectionnez l’automatisation de la charge utile dans la liste en cliquant sur la case à cocher. Cliquez sur l’icône Modifier l’automatisation ![.](../../media/m365-cc-sc-edit-icon.png) **Icône Modifier l’automatisation** qui s’affiche.
- Sélectionnez l’automatisation de la charge utile dans la liste en cliquant n’importe où dans la ligne, à l’exception de la case à cocher. Dans le menu volant d’informations qui s’ouvre, sous l’onglet **Général** , cliquez sur **Modifier** dans les sections **Nom**, **Description** ou **Conditions** d’exécution.

L’Assistant Automation de charge utile s’ouvre avec les paramètres et les valeurs de l’automatisation de charge utile sélectionnée. Les étapes sont les mêmes que celles décrites dans la section [Créer des automatisations de charge utile](#create-payload-automations) .

## <a name="remove-payload-automations"></a>Supprimer les automatisations de charge utile

Pour supprimer une automatisation de charge utile, sélectionnez l’automatisation de charge utile dans la liste en cliquant sur la case à cocher. Cliquez sur l’icône ![Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Icône Supprimer** qui s’affiche, puis cliquez sur **Confirmer** dans la boîte de dialogue.

## <a name="related-links"></a>Liens associés

[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

[Automatisations de simulation pour Exercice de simulation d'attaque](attack-simulation-training-simulation-automations.md)

[Découvrez les formations à la simulation d’attaque](attack-simulation-training-insights.md)
