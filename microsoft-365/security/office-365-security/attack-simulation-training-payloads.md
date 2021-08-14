---
title: Créer une charge utile pour la formation à la simulation d’attaques
ms.author: daniha
author: danihalfin
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent apprendre à créer des charges utiles personnalisées pour la formation à la simulation d’attaques dans Microsoft Defender Office 365.
ms.technology: mdo
ms.openlocfilehash: ecd7b539aa22d2935f96860769b30751022d89ea43151a94222caeec9b309928
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53810369"
---
# <a name="create-a-custom-payload-for-attack-simulation-training"></a>Créer une charge personnalisée pour une formation à la simulation d’attaque

**S’applique** [à Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Microsoft offre un catalogue de charges utiles robuste pour diverses techniques d’ingénierie sociale à jumeler avec votre formation à la simulation d’attaques. Toutefois, vous pouvez créer des charges utiles personnalisées qui fonctionneront mieux pour votre organisation. Cet article explique comment créer une charge utile dans la formation sur la simulation d’attaques dans Microsoft Defender pour Office 365.

Vous pouvez créer une charge  utile en cliquant sur Créer une charge utile dans l’onglet [ **Charge utile**](https://security.microsoft.com/attacksimulator?viewid=payload) dédiée ou dans l’Assistant de création [de simulation.](attack-simulation-training.md#selecting-a-payload)

La première étape de l’Assistant vous permettra de sélectionner un type de charge utile. **Actuellement, seul le courrier électronique est disponible.**

Ensuite, sélectionnez une technique associée. Pour plus d’informations sur les techniques, voir [la sélection d’une technique d’ingénierie sociale.](attack-simulation-training.md#selecting-a-social-engineering-technique)

À l’étape suivante, nommez votre charge utile. Si vous le souhaitez, vous pouvez lui donner une description.

> [!NOTE]
> Certaines marques, logos, symboles, insignias et autres identificateurs source bénéficient d’une protection maximale en vertu de lois et lois locales, nationales et fédérales. L’utilisation non autorisée de ces indicateurs peut imposer des sanctions aux utilisateurs, y compris des amendes pénales. Bien qu’il ne s’agit pas d’une liste complète, il s’agit notamment des personnes à l’emploi de Lasc, du vice-président et de l’espion, du CENTRE d’enquêtes sur la sécurité sociale, de la sécurité sociale, du service de sécurité sociale des États-Unis et du service de revenu interne des États-Unis. Au-delà de ces catégories de marques, l’utilisation et la modification d’une marque tierce impliquent un risque inhérent. L’utilisation de vos propres marques et logos dans une charge utile serait moins risqué, en particulier lorsque votre organisation autorise l’utilisation. Si vous avez d’autres questions sur ce qui est approprié ou non à utiliser lors de la création ou de la configuration d’une charge utile, vous devez consulter vos conseillers juridiques.

## <a name="configure-payload"></a>Configurer la charge utile

Il est maintenant temps de créer votre charge utile. Dans la section Détails de l’expéditeur, entrer le nom de l’expéditeur, l’adresse e-mail et l’objet **de l’e-mail.** Sélectionnez une URL de hameçonnage dans la liste fournie. Cette URL sera incorporée ultérieurement dans le corps du message.

> [!TIP]
> Vous pouvez choisir un e-mail interne pour l’expéditeur de votre charge utile, ce qui fait apparaître la charge utile comme provenant d’un autre employé de l’entreprise. Cela augmente la sensibilité à la charge utile et aide à informer les employés sur les risques de menaces internes.

Un éditeur de texte enrichi est disponible pour créer votre charge utile. Vous pouvez également importer un e-mail que vous avez créé au préalable. Lorsque vous créez le corps de  l’e-mail, tirez parti des balises dynamiques pour personnaliser l’e-mail sur vos cibles. Cliquez **sur le lien Hameçonnage** pour ajouter l’URL de hameçonnage précédemment sélectionnée dans le corps du message.

![Lien de hameçonnage et balises dynamiques mises en évidence dans la création de charge utile pour Microsoft Defender pour Office 365](../../media/attack-sim-preview-payload-email-body.png)

> [!TIP]
> Pour gagner du temps, basculez sur l’option de remplacement de tous les liens du message électronique par le **lien de hameçonnage.**

Une fois que vous avez terminé de créer la charge utile à votre convenance, cliquez sur **Suivant**.

## <a name="adding-indicators"></a>Ajout d’indicateurs

Les indicateurs aideront les employés qui traversent la simulation d’attaque à comprendre l’indice qu’ils peuvent rechercher dans les futures attaques. Pour commencer, cliquez sur **Ajouter un indicateur.**

Sélectionnez un indicateur que vous souhaitez utiliser dans la liste de listes. Cette liste est organisée pour contenir les indices les plus courants qui apparaissent dans les messages électroniques de hameçonnage. Une fois sélectionné, assurez-vous que le placement de l’indicateur est définie sur À partir du corps de l’e-mail **et** cliquez sur Sélectionner **du texte**. Sélectionnez la partie de votre charge utile où cet indicateur apparaît, puis cliquez sur **Sélectionner.**

![Texte mis en surbrillant dans le corps du message à ajouter à un indicateur dans la formation à la simulation d’attaques](../../media/attack-sim-preview-select-text.png)

Ajoutez une description personnalisée pour décrire l’indicateur et cliquez dans le cadre d’aperçu de l’indicateur pour afficher un aperçu de votre indicateur. Une fois terminé, cliquez sur **Ajouter**. Répétez ces étapes jusqu’à ce que vous avez couvert tous les indicateurs de votre charge utile.

## <a name="review-payload"></a>Examiner la charge utile

Vous avez terminé de créer votre charge utile. Il est maintenant temps de passer en revue les détails et d’afficher un aperçu de votre charge utile. La prévisualisation inclut tous les indicateurs que vous avez créés. Vous pouvez modifier chaque partie de la charge utile à partir de cette étape. Une fois satisfait, vous pouvez **soumettre votre** charge utile.

> [!IMPORTANT]
> Les charges utiles que vous avez créées auront **le client** comme source. Lorsque vous sélectionnez des charges utiles, veillez à ne pas filtrer le **client.**

## <a name="related-links"></a>Liens associés

[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

[Créer une simulation d’attaque par hameçonnage](attack-simulation-training.md)

[Découvrez les formations à la simulation d’attaque](attack-simulation-training-insights.md)
