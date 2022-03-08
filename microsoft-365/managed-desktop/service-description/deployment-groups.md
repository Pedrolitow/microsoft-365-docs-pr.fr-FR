---
title: Groupes de déploiement d’appareils
description: Groupes de déploiement utilisés pour gérer les mises à jour et autres modifications
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 624bde84da9a0c35f5814e3b6c67c2d190683fc6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330298"
---
# <a name="device-deployment-groups"></a>Groupes de déploiement d’appareils

Microsoft Manged Desktop utilise des groupes de déploiement pour gérer la publication des mises à jour et les modifications de configuration apportées aux appareils. Les appareils sont ajoutés automatiquement aux groupes de déploiement (« anneaux » ou « groupes de mise à jour ») lorsqu’ils sont inscrits Microsoft Manged Desktop. Les groupes de déploiement permettent aux appareils de recevoir des modifications dans une chronologie progressive.

Vous pouvez affecter certains appareils uniquement à des fins de test ou désigner des utilisateurs précoces spécifiques pour recevoir les modifications en premier. Si vous avez des appareils critiques, tels que ceux utilisés par les cadres ou qui font des fonctions critiques pour l’entreprise, vous pouvez les conserver dans le groupe qui obtient les mises à jour à la cadence la plus lente. Microsoft Manged Desktop vous permet de spécifier qu’un appareil doit rester dans l’un des groupes suivants.

| Group | Description |
| ----- | ----- |
| Tester | Le groupe test est le meilleur pour les appareils qui sont utilisés pour le test ou les utilisateurs qui peuvent tolérer des modifications fréquentes, l’exposition aux nouvelles fonctionnalités et peuvent fournir des commentaires précoces.<br><br>Ce groupe reçoit fréquemment des modifications et les expériences de ce groupe ont un fort effet. Le groupe test est exempté de tout contrat de niveau de service établi et du support utilisateur. Il est préférable de déplacer quelques appareils au début, puis de passer en revue l’expérience utilisateur. Microsoft Manged Desktop n’affectera pas automatiquement d’appareils à ce groupe. Ce groupe contient uniquement les appareils que vous spécifiez.
| Premier | Le premier groupe est idéal pour les utilisateurs précoces, les volontaires, les validateurs désignés, les professionnels de l’informatique ou les représentants des fonctions professionnelles. Autrement dit, les personnes qui peuvent valider les modifications et vous faire part de leurs commentaires sur l’expérience.
| Rapide | Le groupe Rapide est idéal pour les représentants des fonctions professionnelles. Ces personnes peuvent valider les modifications avant un déploiement à grande échelle.
| Larges | Le groupe Large reçoit les modifications en dernier.<br><br>La plupart de votre organisation fait généralement partie de ce groupe. Vous pouvez spécifier les appareils qui doivent être dans ce groupe. Ces appareils doivent recevoir les modifications en dernier, car ils font des fonctions critiques ou appartiennent à des utilisateurs dans des rôles critiques.
| Automatique | Sélectionnez Automatique lorsque vous souhaitez Microsoft Manged Desktop affecter automatiquement des appareils à l’un des autres groupes.<br><br>Nous n’affecterons pas automatiquement les appareils au test. Si vous souhaitez libérer un appareil que vous avez précédemment spécifié afin qu’il puisse être automatiquement attribué à nouveau, sélectionnez cette option.

Pour plus d’informations sur la façon Windows les mises à jour sont gérées en groupes, voir Comment les mises à jour sont [gérées dans Microsoft Manged Desktop](updates.md).

## <a name="labels"></a>Étiquettes

Le groupe affecté par colonne contient les étiquettes suivantes :

| Étiquette | Description |
| ----- | ----- |
| Administrateur | L’appareil se trouve dans un groupe que vous avez spécifié. |
| Auto | Microsoft Manged Desktop le groupe. |
| Pending | L’appareil est en cours de déplacement vers un groupe. |

La **colonne Groupe** affiche toujours le groupe dans quel groupe se trouve l’appareil et ne se met à jour qu’une fois le déplacement terminé.

> [!IMPORTANT]
> N’essayez pas de modifier directement l’appartenance de ces groupes. Suivez toujours les étapes décrites dans [Affecter des appareils à un groupe de déploiement](../working-with-managed-desktop/assign-deployment-group.md).
