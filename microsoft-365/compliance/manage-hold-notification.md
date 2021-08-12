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
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez le flux de travail de communications Advanced eDiscovery pour suivre l’état de vos notifications de mise en attente légale et, si nécessaire, les mettre à jour et les renvoyer.
ms.openlocfilehash: 88dd3ef8e74dd67b196f574b1cfe8ba5c33a1a63afeac8701f19e36476e56767
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53842133"
---
# <a name="manage-hold-notifications"></a>Gérer les notifications de conservation

Une fois que vous avez initié votre flux de travail de notification de mise en attente légale, vous pouvez utiliser le flux de travail de communications dans Advanced eDiscovery pour suivre l’état de vos communications. L’onglet Communications contient la liste de toutes les notifications au sein de votre Advanced eDiscovery cas. Vous pouvez voir des détails tels que le nombre de dépositaires qui ont été affectés ou qui ont reçu l’avis.

## <a name="monitor-acknowledgments"></a>Surveiller les accusés de réception

Après avoir sélectionné une communication dans l’onglet **Communications,** vous pouvez afficher la liste des dépositaires qui ont reconnu un avis de conservation. 

1. Dans le centre de conformité, allez à **eDiscovery > Advanced eDiscovery**.

2. Sélectionnez un cas, puis cliquez sur **l’onglet Communications.**

3. Sélectionnez une communication pour afficher la page de **présentation des communications** du dépositaire.

La liste des dépositaires associés à la communication sélectionnée s’affiche sur la page de présentation des communications. Cette page affiche également des informations sur le nombre d’accusés de réception reçus et le nombre d’accusés de réception en suspens. La page indique également quels dépositaires ont envoyé un accusé de réception de la notification de conservation.

## <a name="re-send-a-hold-notice"></a>Renvoyer un avis de non-attente

Parfois, les dépositaires perdent le suivi des messages électroniques dans leur travail quotidien. Ou dans le cas d’un litige de longue durée, un dépositaire peut vous contacter ou d’autres personnes et vous demander de renvoyer une notification. Lorsque vous gérez le flux de travail de communications pour les notifications de non-accès pour raisons juridiques, vous devrez peut-être renvoyer un avis pour le renvoyer dans la « partie supérieure de la boîte aux lettres d’un utilisateur ».

Pour renvoyer une notification de conservation à un dépositaire :

1. Dans Advanced eDiscovery, sélectionnez un cas, puis cliquez sur **l’onglet Communications.**

2. Sélectionnez une communication pour afficher la page de **présentation des communications** du dépositaire.

3. Cliquez **sur Plus > notification de ré-envoi de la notification de non-attente.**

4. Dans la page **de** notification de nouvelle conservation, sélectionnez les dépositaires dont vous souhaitez renvoyer l’avis et tapez une raison facultative.

5. Cliquez **sur Renvoyer** pour envoyer l’avis aux dépositaires sélectionnés.

Si un dépositaire n’a pas reconnu la notification de conservation, le flux de travail de rappel et d’escalade est redémarré. Si un dépositaire a reconnu l’avis de conservation, il reçoit une copie de l’avis de conservation d’origine.

> [!NOTE]
> Vous pouvez uniquement renvoyer une notification de conservation légale aux dépositaires affectés à la communication. 

## <a name="update-preservation-requirements"></a>Mettre à jour les exigences de conservation
  
Au fur et à mesure de l’avancement du cas, les dépositaires peuvent être tenus de conserver des données supplémentaires ou inférieures aux instructions précédemment. Dans les termes eDiscovery, vous devez émettre à nouveau l’avis de mise en attente avec le contenu mis à jour.

Pour mettre à jour le contenu de l’avis de mise en attente initiale :

1. Dans Advanced eDiscovery, sélectionnez un cas, puis cliquez sur **l’onglet Communications.**

2. Sélectionnez l’avis de conservation à mettre à jour, puis cliquez sur **Modifier** dans la page de **communication** du dépositaire.

3. Dans **l’Assistant Modifier la communication,** cliquez sur Définir le contenu du portail dans le volet gauche de l’Assistant, puis mettez à jour le contenu de l’avis. 

4. Cliquez sur **Save (Enregistrer)**.

L’avis de réé émission est envoyé à tous les dépositaires affectés à la notification de conservation légale. En outre, si l’avis de rappel ou d’escalade est activé, les flux de travail pour ces types de notifications redémarrent.

## <a name="update-legal-hold-notifications-and-settings"></a>Mettre à jour les notifications et paramètres de mise en attente légale

Lorsque vous mettez à jour le contenu ou les paramètres de l’avis d’émission, de publication, de réédition, de rappel ou d’escalade, ces modifications s’appliquent à toutes les communications futures générées par le flux de travail.

## <a name="more-information"></a>Plus d’informations

- [Ajouter des consignataires à un cas](add-custodians-to-case.md)

- [Créer une notification de non-droit](create-hold-notification.md)

- [Reconnaitre une notification de conservation](acknowledge-hold-notification.md)
