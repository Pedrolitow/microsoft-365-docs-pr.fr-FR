---
title: Groupes de déploiement d’appareils
description: Groupes de déploiement utilisés pour gérer les mises à jour et autres modifications
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: c343692e904e292f333cd2e3d729f0c56a819e7774262fcd4baf0197071637e3
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53863894"
---
# <a name="device-deployment-groups"></a>Groupes de déploiement d’appareils

Microsoft Manged Desktop utilise des groupes de déploiement pour gérer la publication des mises à jour et les modifications de configuration apportées aux appareils. Les appareils sont ajoutés automatiquement aux groupes de déploiement (« anneaux » ou « groupes de mise à jour ») lorsqu’ils sont inscrits Microsoft Manged Desktop. Les groupes de déploiement permettent aux appareils de recevoir des modifications dans une chronologie progressive.

Vous pouvez affecter certains appareils à des fins de test uniquement, ou désigner des utilisateurs précoces spécifiques pour recevoir les modifications en premier. Si vous avez des appareils critiques tels que ceux utilisés par les cadres ou qui font des fonctions critiques pour l’entreprise, vous pouvez les conserver dans le groupe qui obtient les mises à jour à la cadence la plus lente. Microsoft Manged Desktop vous permet de spécifier qu’un appareil doit rester dans l’un des groupes suivants.

- **Test**: préférable pour les appareils utilisés pour les tests ou les utilisateurs qui peuvent tolérer des modifications fréquentes et une exposition aux nouvelles fonctionnalités et fournir des commentaires précoces. Ce groupe reçoit fréquemment des modifications et les expériences de ce groupe ont un fort effet. Le groupe test est exempté de tout contrat de niveau de service établi et du support utilisateur. Il est préférable de déplacer quelques appareils au début, puis de vérifier l’expérience utilisateur. Microsoft Manged Desktop n’affectera pas automatiquement d’appareils à ce groupe ; Il n’aura que les appareils que vous spécifiez.
- **Tout** d’abord : idéal pour les utilisateurs précoces, les validateurs volontaires ou désignés, les professionnels de l’informatique ou les représentants des fonctions professionnelles, c’est-à-dire les personnes qui peuvent valider les modifications et vous faire part de leurs commentaires sur l’expérience.
- **Large** reçoit les modifications en dernier. La plupart de votre organisation fait généralement partie de ce groupe. Vous pouvez également spécifier les appareils qui doivent faire partie de ce groupe et qui ne doivent recevoir des modifications qu’en dernier, car ils font des fonctions critiques ou appartiennent à des utilisateurs dans des rôles critiques. 
- **Automatique**: sélectionnez cette option lorsque vous souhaitez Microsoft Manged Desktop affecter automatiquement des appareils à l’un des autres groupes. (Nous n’affecterons pas automatiquement les appareils au test.) Si vous souhaitez libérer un appareil que vous avez précédemment spécifié afin qu’il puisse être automatiquement attribué à nouveau, sélectionnez cette option. 

Microsoft Manged Desktop utilise des groupes supplémentaires pour contrôler les déploiements, mais vous ne pourrez pas leur affecter d’appareils. Toutefois, vous pouvez déplacer des appareils de ces groupes vers l’un des groupes de cet article. Pour plus d’informations sur Windows les mises à jour sont gérées en groupes, voir Comment les mises à jour sont [gérées dans Microsoft Manged Desktop](updates.md).

Si un appareil se trouve dans un groupe que vous avez spécifié, le groupe affecté **par** indique **Admin**. Si Microsoft Manged Desktop a affecté le groupe, il dit **Auto**. Pendant qu’un appareil est en cours de déplacement vers un groupe, il est dit **en attente**. Le **champ** Groupe affiche toujours le groupe dans qui se trouve l’appareil et ne se met à jour qu’une fois le déplacement terminé.

> [!IMPORTANT]
> N’essayez pas de modifier directement l’appartenance de ces groupes. Suivez toujours les étapes décrites dans [Affecter des appareils à un groupe de déploiement.](../working-with-managed-desktop/assign-deployment-group.md)
