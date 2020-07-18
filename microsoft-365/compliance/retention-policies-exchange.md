---
title: Découvrir la rétention pour Exchange
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Découvrir le fonctionnement de la rétention pour Exchange.
ms.openlocfilehash: e1860b9ff9c521a5a6a61c58d822a2a893570e99
ms.sourcegitcommit: e8b9a4f18330bc09f665aa941f1286436057eb28
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "45127441"
---
# <a name="learn-about-retention-for-exchange"></a>Découvrir la rétention pour Exchange

Les informations contenues dans cet article complètent l’article [Découvrir la rétention](retention.md) car elles contiennent des informations spécifiques à Exchange.

## <a name="how-retention-works-for-exchange"></a>Fonctionnement de la rétention pour Exchange

Les boîtes aux lettres et les dossiers publics utilisent le même dossier [Éléments récupérables ](https://docs.microsoft.com/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder)pour conserver des éléments. Seules les personnes disposant des autorisations eDiscovery peuvent afficher le dossier Éléments récupérables d’un autre utilisateur.
  
Par défaut, lorsqu’un utilisateur supprime un message dans un dossier autre que le dossier Éléments supprimés, le message est déplacé vers le dossier Éléments supprimés. Lorsqu’un utilisateur supprime un élément dans le dossier Éléments supprimés, le message est déplacé vers le dossier Éléments récupérables. En outre, une personne peut supprimer de façon réversible, un élément (MAJ + SUPPR) dans n’importe quel dossier, ce qui permet de passer outre le dossier Éléments supprimés et de placer l’élément directement dans le dossier Éléments récupérables.
  
Lorsque vous appliquez des paramètres de rétention à des données Exchange, un travail du minuteur évalue régulièrement les éléments du dossier Éléments récupérables. Si un élément ne correspond pas aux règles d’au moins une stratégie de rétention ou une étiquette de rétention, l’élément est supprimé définitivement du dossier Éléments récupérables.

L’exécution du travail du minuteur peut prendre jusqu’à sept jours, et l’emplacement Exchange doit contenir au moins 10 Mo.
  
Lorsqu’un utilisateur tente de modifier les propriétés d’un élément de la boîte aux lettres (l’objet, le corps, les pièces jointes, les expéditeurs et destinataires ou la date d’envoi ou de réception d’un message), une copie de l’élément d’origine est enregistré dans le dossier Éléments récupérables avant la validation de la modification. Cette action se produit à chaque modification ultérieure. À la fin de la période de rétention, les copies dans le dossier Éléments récupérables sont supprimées définitivement.

Une fois que les paramètres de rétention sont appliqués à du contenu Exchange, les chemins d’accès au contenu sont fonction des paramètres de rétention qui consistent à conserver et à supprimer, à conserver uniquement ou à supprimer uniquement.

Lorsque les paramètres de la stratégie de rétention sont définis sur conserver et supprimer :

![Diagramme du flux de rétention dans la messagerie et les dossiers publics](../media/88f174cc-bbf4-4305-93d7-0515f496c8f9.png)

1. **Si l’élément est modifié ou supprimé définitivement** par l’utilisateur (avec MAJ + SUPPR ou supprimé dans le dossier Éléments supprimés) pendant la période de rétention : l’élément est déplacé (ou copié, dans le cas d’une modification) dans le dossier Éléments récupérables. Ici, un travail de minuteur s’exécute régulièrement et identifie les éléments dont la période de rétention a expiré. Ces éléments sont ensuite supprimés définitivement dans un délai de 14 jours après la fin de la période de rétention. Notez que le paramètre par défaut est de 14 jours, mais qu’il peut être configuré jusqu’à 30 jours.

2. **Si l’élément n’est ni modifié ni supprimé** pendant la période de rétention : le même processus s’exécute régulièrement sur tous les dossiers de la boîte aux lettres et identifie les éléments dont la période de rétention a expiré. Ceux-ci sont alors supprimés définitivement dans les 14 jours suivant la fin de la période de rétention. Notez que le paramètre par défaut est de 14 jours, mais qu’il peut être configuré jusqu’à 30 jours. 

Lorsque les paramètres de la stratégie de rétention sont définis sur conserver uniquement ou supprimer uniquement, les chemins d’accès du contenu sont des variantes de l’option conserver et supprimer :

### <a name="content-paths-for-retain-only-retention-settings"></a>Chemins d’accès du contenu pour la stratégie de rétention de conservation uniquement

1. **Si l’élément est modifié ou supprimé** pendant la période de rétention : une copie de l’élément d’origine est créée dans le dossier Éléments récupérables et conservée jusqu’à la fin de la période de rétention, lorsque la copie dans le dossier Éléments récupérables est définitivement supprimée dans un délai de 14 jours après l’expiration de l’élément. 

2. **Si le contenu n’est ni modifié ni supprimé** pendant la période de rétention : rien ne se passe avant et après la période de rétention ; le document reste à son emplacement d’origine.

### <a name="content-paths-for-delete-only-retention-settings"></a>Chemins d’accès du contenu pour la stratégie de rétention de suppression uniquement

1. **Si le contenu n’est pas supprimé** pendant la période de rétention : à la fin de la période configurée dans la stratégie de rétention, l’élément est déplacé vers le dossier Éléments récupérables. 

2. **Si l’élément est supprimé** pendant la période de rétention : l’élément est placé immédiatement dans le dossier Éléments récupérables. Si un utilisateur supprime l’élément à partir de là ou vide le dossier Éléments récupérables, l’élément est définitivement supprimé. Dans le cas contraire, l’élément est définitivement supprimé après avoir été placé dans le dossier Éléments récupérables pendant 14 jours. 

## <a name="when-a-user-leaves-the-organization"></a>Lorsqu’un utilisateur quitte l’organisation 

Si un utilisateur quitte votre organisation et que sa boîte aux lettres est incluse dans une stratégie de rétention, celle-ci devient inactive lorsque le compte Microsoft 365 de l’utilisateur est supprimé. Le contenu d’une boîte aux lettres inactive reste soumis à toute stratégie de rétention qui a été appliquée à la boîte aux lettres avant sa désactivation, et le contenu est accessible aux recherches eDiscovery. Pour plus d’informations, consultez [Boîtes aux lettres inactives dans Exchange Online](inactive-mailboxes-in-office-365.md).

## <a name="configuration-guidance"></a>Instructions de configuration

Si vous êtes prêt à configurer la rétention dans Microsoft 365, voir [Prise en main des stratégies de rétention et des étiquettes de rétention](get-started-with-retention.md).
