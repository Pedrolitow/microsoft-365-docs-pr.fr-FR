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
description: Utilisez le flux de travail de communication dans Advanced eDiscovery pour suivre l’état de vos notifications de conservation légale et, le cas échéant, mettez à jour et renvoyez-les.
ms.openlocfilehash: 8852bfd1651e1855d276b60ba6fac35c378d4631
ms.sourcegitcommit: 6d672eb8287526a9db90df5fa85bc4984a7047d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "42280112"
---
# <a name="manage-hold-notifications"></a>Gérer les notifications de conservation

Une fois que vous avez lancé votre flux de travail de notification de conservation légale, vous pouvez utiliser le flux de travail de communication dans Advanced eDiscovery pour suivre l’état de vos communications. L’onglet communications contient une liste de toutes les notifications dans votre cas avancé de découverte électronique avancée. Vous pouvez afficher des informations telles que le nombre de dépositaires qui ont été attribués ou ont accusé réception de l’avis.

## <a name="monitor-acknowledgments"></a>Surveiller les accusés de réception

Une fois que vous avez sélectionné une communication dans l’onglet **communications** , vous pouvez afficher la liste des dépositaires ayant accusé réception d’une notification de suspension. 

1. Dans le centre de conformité, accédez à **ediscovery > Advanced eDiscovery**.

2. Sélectionnez un cas, puis cliquez sur l’onglet **communications** .

3. Sélectionnez une communication pour afficher la page de sélection de la **communication du dépositaire** .

La liste des dépositaires associés à la communication sélectionnée s’affiche sur la page mobile de communication. Cette page affiche également des informations et indique le nombre d’accusés de réception reçus et le nombre de pages en suspens. La page indique également quels dépositaires ont envoyé un accusé de réception indiquant qu’ils ont reçu la notification de mise en attente.

## <a name="re-send-a-hold-notice"></a>Renvoyer une notification de suspension

Parfois, les dépositaires perdent le suivi des messages électroniques dans leur travail quotidien. Ou pour un cas de litige de longue durée, un dépositaire peut vous contacter ou d’autres personnes et vous demander de renvoyer une notification. Lorsque vous gérez le flux de travail des communications pour les notifications de conservation légale, il se peut que vous deviez renvoyer un avertissement pour le ramener à la « partie supérieure de la boîte aux lettres d’un utilisateur ».

Pour renvoyer une notification de suspension à un dépositaire, procédez comme suit :

1. Dans Advanced eDiscovery, sélectionnez un cas, puis cliquez sur l’onglet **communications** .

2. Sélectionnez une communication pour afficher la page de sélection de la **communication du dépositaire** .

3. Cliquez sur **plus > relancer la notification de suspension**.

4. Sur la page de menu **déroulante de retransmission des notifications de suspension** , sélectionnez les dépositaires que vous souhaitez renvoyer à l’avis et tapez une raison facultative.

5. Cliquez **sur renvoyer pour** envoyer l’avertissement aux dépositaires sélectionnés.

Si un dépositaire n’a pas reconnu la notification de blocage, le flux de rappel et le flux de travail de remontée des problèmes sont redémarrés. Si un dépositaire a accusé réception de la notification d’attente, le dépositaire reçoit une copie de l’avis de suspension d’origine.

> [!NOTE]
> Vous ne pouvez renvoyer une notification de suspension légale qu’aux dépositaires qui sont affectés à la communication. 

## <a name="update-preservation-requirements"></a>Exigences en matière de conservation des mises à jour
  
En cas de progression, les dépositaires peuvent être tenus de conserver des données supplémentaires ou moins que celles précédemment demandées. Dans les termes eDiscovery, vous devez relancer l’avis de suspension avec du contenu mis à jour.

Pour mettre à jour le contenu de l’avis de mise en attente initiale :

1. Dans Advanced eDiscovery, sélectionnez un cas, puis cliquez sur l’onglet **communications** .

2. Sélectionnez la notification de mise en attente que vous souhaitez mettre à jour, puis cliquez sur **modifier** sur la page flyout de la **communication du dépositaire** .

3. Dans l’Assistant **modifier la communication** , cliquez sur définir le contenu du **portail** dans le volet gauche de l’Assistant, puis mettez à jour le contenu de l’avis.

4. Cliquez sur **Enregistrer**.

L’avis de ré-émission est envoyé à tous les dépositaires affectés à la notification de suspension légale. En outre, si l’avis de rappel ou de notification d’escalade est activé, les flux de travail de ces types de notifications redémarreront.

## <a name="update-legal-hold-notifications-and-settings"></a>Mettre à jour les notifications et les paramètres de conservation légale

Lorsque vous mettez à jour le contenu ou les paramètres de l’émission, de la publication, de la réémission, de la relance ou de l’avis d’escalade, ces modifications s’appliquent à toutes les communications futures générées par le flux de travail.

## <a name="more-information"></a>Plus d’informations

- [Ajouter des consignataires à un cas](add-custodians-to-case.md)

- [Créer une notice de suspension légale](create-hold-notification.md)

- [Reconnaitre une notification de conservation](acknowledge-hold-notification.md)
