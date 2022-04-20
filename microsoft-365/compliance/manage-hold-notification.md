---
title: Gérer les notifications de conservation
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez le flux de travail de communication dans eDiscovery (Premium) pour suivre l’état de vos notifications de conservation légale et, si nécessaire, les mettre à jour et les renvoyer.
ms.openlocfilehash: 83e5331aaea59893f06cfa0629d627e500cfe1b1
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996171"
---
# <a name="manage-hold-notifications"></a>Gérer les notifications de conservation

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Une fois que vous avez lancé votre flux de travail de notification de conservation légale, vous pouvez utiliser le flux de travail de communication dans Microsoft Purview eDiscovery (Premium) pour suivre l’état de vos communications. L’onglet Communications contient une liste de toutes les notifications dans votre cas eDiscovery (Premium). Vous pouvez voir des détails tels que le nombre de consignats qui ont été affectés ou qui ont accepté l’avis.

## <a name="monitor-acknowledgments"></a>Surveiller les accusés de réception

Une fois que vous avez sélectionné une communication dans l’onglet **Communications** , vous pouvez afficher la liste des consignatateurs qui ont reconnu un avis de suspension. 

1. Dans le Centre de conformité, accédez à **eDiscovery > eDiscovery (Premium)**.

2. Sélectionnez un cas, puis cliquez sur l’onglet **Communications** .

3. Sélectionnez une communication pour afficher la page de menu volant de **communication du consignateur** .

Une liste des consignats associés à la communication sélectionnée s’affiche sur la page de menu volant de communication. Cette page affiche également des insights et sur le nombre d’accusés de réception reçus et le nombre d’accusés de réception en attente. La page indique également quels consignats ont envoyé un accusé de réception indiquant qu’ils ont reçu la notification de conservation.

## <a name="re-send-a-hold-notice"></a>Réexécuter un avis de suspension

Parfois, les consignats perdent le suivi des messages électroniques dans leur travail quotidien. Ou, dans le cas d’un litige de longue durée, un consignaculateur peut vous contacter ou d’autres personnes et vous demander de réexécuter un avis. Lorsque vous gérez le flux de travail de communications pour les avis de suspension légale, vous devrez peut-être réexécuter une notification pour la ramener au « haut de la boîte aux lettres d’un utilisateur ».

Pour réexécuter un avis de suspension à un consignateur :

1. Dans eDiscovery (Premium), sélectionnez un cas, puis cliquez sur l’onglet **Communications**.

2. Sélectionnez une communication pour afficher la page de menu volant de **communication du consignateur** .

3. Cliquez sur **Autres > Réexécuter l’avis de suspension**.

4. Dans la page de menu volant **Réexélectionner l’avis de suspension** , sélectionnez les consignats que vous devez renvoyer à l’avis et tapez une raison facultative.

5. Cliquez sur **Réexécuter** pour envoyer l’avis aux consignatateurs sélectionnés.

Si un dépositaire n’a pas reconnu la notification de suspension, le flux de travail de rappel et d’escalade est redémarré. Si un gardien a reconnu l’avis de conservation, il recevra une copie de l’avis de conservation d’origine.

> [!NOTE]
> Vous pouvez uniquement renvoyer une notification de conservation légale aux consignats affectés à la communication. 

## <a name="update-preservation-requirements"></a>Mettre à jour les exigences de conservation
  
À mesure que le cas progresse, les consignataires peuvent être tenus de conserver des données supplémentaires ou inférieures à celles qui ont été demandées précédemment. En termes eDiscovery, vous devez réexécuter l’avis de suspension avec le contenu mis à jour.

Pour mettre à jour le contenu de l’avis de mise en attente initiale :

1. Dans eDiscovery (Premium), sélectionnez un cas, puis cliquez sur l’onglet **Communications**.

2. Sélectionnez l’avis de suspension que vous souhaitez mettre à jour, puis cliquez sur **Modifier** dans la page de menu volant de **communication du consignateur** .

3. Dans l’Assistant **Modifier la communication** , cliquez sur **Définir le contenu du portail** dans le volet gauche de l’Assistant, puis mettez à jour le contenu de l’avis.

4. Cliquez sur **Enregistrer**.

L’avis de réexélation sera envoyé à tous les consignats affectés à la notification de conservation légale. En outre, si l’avis de rappel ou d’escalade est activé, les flux de travail de ces types d’avis redémarrent.

## <a name="update-legal-hold-notifications-and-settings"></a>Mettre à jour les notifications et les paramètres de conservation légale

Lorsque vous mettez à jour le contenu ou les paramètres de l’avis d’émission, de publication, de réédition, de rappel ou d’escalade, ces modifications s’appliquent à toutes les communications futures générées par le flux de travail.

## <a name="more-information"></a>Plus d’informations

- [Ajouter des consignataires à un cas](add-custodians-to-case.md)

- [Créer un avis de conservation légale](create-hold-notification.md)

- [Reconnaitre une notification de conservation](acknowledge-hold-notification.md)
