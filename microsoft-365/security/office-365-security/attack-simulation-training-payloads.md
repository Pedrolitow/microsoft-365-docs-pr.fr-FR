---
title: Créer une charge utile pour la formation à la simulation d’attaque
ms.author: daniha
author: danihalfin
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
description: Découvrez comment créer une charge utile personnalisée pour la formation à la simulation d’attaque dans Microsoft Defender pour Office 365.
ms.openlocfilehash: ffb5397d9b39a35b4cb8bd0fdb3301cd156896e1
ms.sourcegitcommit: dab50e1cc5bba920720b80033c93457f5ca1c330
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "48944519"
---
# <a name="create-a-custom-payload-for-attack-simulation-training"></a>Créer une charge utile personnalisée pour la formation à la simulation d’attaque

Microsoft propose un catalogue de charges utiles robuste pour les différentes techniques d’ingénierie sociale à associer à votre formation à la simulation d’attaque. Toutefois, vous pouvez créer des charges utiles personnalisées qui fonctionneront mieux pour votre organisation. Les rubriques suivantes décrivent comment créer une charge utile dans la formation à la simulation d’attaque via Microsoft Defender pour Office 365.

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Vous pouvez créer une charge utile en cliquant sur **créer une charge utile** dans l' [onglet **charge utile** dédiée](https://security.microsoft.com/attacksimulator?viewid=payload) ou dans l' [Assistant Création de simulation](attack-simulation-training.md#selecting-a-payload).

La première étape de l’Assistant vous permet de sélectionner un type de charge utile. **Actuellement, seul le courrier électronique est disponible**.

Ensuite, sélectionnez une technique associée. Pour plus d’informations sur les techniques, consultez la rubrique relative à [la sélection d’une technique d’ingénierie sociale](attack-simulation-training.md#selecting-a-social-engineering-technique).

Dans l’étape suivante, nommez votre charge utile. Vous pouvez également lui donner une description.

## <a name="configure-payload"></a>Configurer la charge utile

À présent, il est temps de créer votre charge utile. Entrez le nom de l’expéditeur, le courrier électronique et l’objet de l’e-mail dans la section **informations sur l’expéditeur** . Sélectionnez une URL de hameçonnage dans la liste fournie. Cette URL sera ensuite incorporée dans le corps du message.

> [!TIP]
> Vous pouvez choisir un message électronique interne pour l’expéditeur de votre charge utile, ce qui fera apparaître la charge utile comme provenant d’un autre employé de la société. Cela augmentera la sensibilité à la charge utile et permettra de sensibiliser les employés sur le risque de menaces internes.

Un éditeur de texte enrichi est disponible pour créer votre charge utile. Vous pouvez également importer un courrier électronique que vous avez créé à l’avance. Lorsque vous structurez le corps du message, tirez parti des **balises dynamiques** pour personnaliser le courrier électronique à vos objectifs. Cliquez sur le **lien hameçonnage (phishing** ) pour ajouter l’URL d’hameçonnage précédemment sélectionnée dans le corps du message.

![Lien de hameçonnage et balises dynamiques mises en surbrillance dans la création de charge utile pour Microsoft Defender pour Office 365](../../media/attack-sim-preview-payload-email-body.png)

> [!TIP]
> Pour vous épargner un peu de temps, activez la case à cocher pour **remplacer tous les liens dans le message électronique par le lien hameçonnage**.

Une fois que vous avez fini de créer la charge utile à votre convenance, cliquez sur **suivant**.

## <a name="adding-indicators"></a>Ajout d’indicateurs

Les indicateurs permettent aux employés de suivre la simulation d’attaque de comprendre l’indice qu’ils peuvent rechercher dans les attaques futures. Pour commencer, cliquez sur **Ajouter un indicateur**.

Sélectionnez un indicateur que vous souhaitez utiliser dans la liste déroulante. Cette liste est organisée pour contenir les indices les plus courants qui apparaissent dans les messages électroniques de hameçonnage. Une fois que vous avez sélectionné, vérifiez que le positionnement de l’indicateur est défini sur **dans le corps de l’e-mail** , puis cliquez sur **Sélectionner le texte**. Mettez en surbrillance la partie de la charge utile où cet indicateur s’affiche, puis cliquez sur **Sélectionner**.

![Texte mis en surbrillance dans le corps du message à ajouter à un indicateur dans la formation à la simulation d’attaque](../../media/attack-sim-preview-select-text.png)

Ajoutez une description personnalisée pour décrire l’indicateur et cliquez dans le cadre d’aperçu de l’indicateur pour afficher un aperçu de votre indicateur. Une fois l’opération terminée, cliquez sur **Ajouter**. Répétez ces étapes jusqu’à ce que vous ayez abordé tous les indicateurs de votre charge utile.

## <a name="review-payload"></a>Examiner la charge utile

Vous avez fini de créer votre charge utile. À présent, il est temps de passer en revue les détails et d’afficher un aperçu de votre charge utile. L’aperçu inclut tous les indicateurs que vous avez créés. Vous pouvez modifier chaque partie de la charge utile à partir de cette étape. Une fois satisfait, **envoyez** votre charge utile. 

> [!IMPORTANT]
> Le **client** sera défini comme source pour les charges que vous avez créées. Lors de la sélection des charges utiles, vérifiez que le **client** n’est pas filtré.