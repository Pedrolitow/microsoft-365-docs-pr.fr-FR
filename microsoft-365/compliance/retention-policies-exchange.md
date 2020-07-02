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
description: Découvrez le comportement de rétention qui s’applique spécifiquement à la messagerie électronique et aux dossiers publics Exchange.
ms.openlocfilehash: e19e790c23c5e61748f38fb22f96d2347acb144e
ms.sourcegitcommit: 5e8901e7e571f20ede04f460bd3e7077dda004ca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "44874882"
---
# <a name="learn-about-retention-policies-for-exchange"></a>Découvrir les stratégies de rétention pour Exchange

Les informations contenues dans cet article complètent l’article [Découvrir les stratégies de rétention](retention-policies.md) car elles contiennent des informations spécifiques à Exchange.

## <a name="how-a-retention-policy-works-with-exchange-locations"></a>Fonctionnement d’une stratégie de rétention avec les emplacements Exchange

Pour la messagerie, le calendrier et les autres éléments de l’utilisateur, une stratégie de rétention est appliquée au niveau de la boîte aux lettres.

Pour un dossier public, une stratégie de rétention est appliquée au niveau du dossier, et non au niveau de la boîte aux lettres. 

Les boîtes aux lettres et les dossiers publics utilisent le même dossier [Éléments récupérables ](https://docs.microsoft.com/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder)pour conserver des éléments. Seules les personnes disposant des autorisations eDiscovery peuvent afficher le dossier Éléments récupérables d’un autre utilisateur.
  
Par défaut, lorsqu’un utilisateur supprime un message dans un dossier autre que le dossier Éléments supprimés, le message est déplacé vers le dossier Éléments supprimés. Lorsqu’un utilisateur supprime un élément dans le dossier Éléments supprimés, le message est déplacé vers le dossier Éléments récupérables. En outre, une personne peut supprimer de façon réversible, un élément (MAJ + SUPPR) dans n’importe quel dossier, ce qui permet de passer outre le dossier Éléments supprimés et de placer l’élément directement dans le dossier Éléments récupérables.
  
Lorsque vous appliquez une stratégie de rétention à un emplacement Exchange, un travail du minuteur évalue régulièrement les éléments du dossier Éléments récupérables. Si un élément ne correspond pas aux règles d’au moins une stratégie de rétention, l’élément est supprimé définitivement du dossier Éléments récupérables.

L’exécution du travail du minuteur peut prendre jusqu’à sept jours, et l’emplacement Exchange doit contenir au moins 10 Mo.
  
Lorsqu’un utilisateur tente de modifier les propriétés d’un élément de la boîte aux lettres (l’objet, le corps, les pièces jointes, les expéditeurs et destinataires ou la date d’envoi ou de réception d’un message), une copie de l’élément d’origine est enregistré dans le dossier Éléments récupérables avant la validation de la modification. Cette action se produit à chaque modification ultérieure. À la fin de la période de rétention, les copies dans le dossier Éléments récupérables sont supprimées définitivement.

Une fois qu’une stratégie de rétention est attribuée à une boîte aux lettres ou à un dossier public, les chemins d’accès du contenu dépendent de la stratégie de rétention qui soit conserve et supprime le contenu, soit le conserve uniquement soit le supprime uniquement.

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

## <a name="excluding-specific-types-of-exchange-items-from-a-retention-policy"></a>Exclusion de types spécifiques d’éléments Exchange d’une stratégie de rétention

PowerShell vous permet d’exclure des types spécifiques d’éléments Exchange d’une stratégie de rétention. Par exemple, vous pouvez exclure les messages vocaux, les conversations par messagerie instantanée et d’autres contenus Skype Entreprise Online dans les boîtes aux lettres. Vous pouvez également exclure les éléments de calendrier, de note et de tâche. Cette fonctionnalité n’est disponible qu’en utilisant PowerShell. Elle n’est pas disponible lorsque vous créez une stratégie de rétention à l’aide de l’Assistant dans le Centre de conformité Microsoft 365.
  
Pour exclure les types sélectionnés pour les éléments Exchange dans une stratégie de rétention, utilisez le paramètre  `ExcludedItemClasses` avec les cmdlets [New-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/new-retentioncompliancerule) et [Set-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/set-retentioncompliancerule).

Pour utiliser les cmdlets des stratégies de rétention, vous devez tout d’abord vous [connecter au Centre de sécurité et conformité PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell?view=exchange-ps).

### <a name="when-a-user-leaves-the-organization"></a>Lorsqu’un utilisateur quitte l’organisation 

Si un utilisateur quitte votre organisation et que sa boîte aux lettres est incluse dans une stratégie de rétention, celle-ci devient inactive lorsque le compte Microsoft 365 de l’utilisateur est supprimé. Le contenu d’une boîte aux lettres inactive reste soumis à toute stratégie de rétention qui a été appliquée à la boîte aux lettres avant sa désactivation, et le contenu est accessible aux recherches eDiscovery. Pour plus d’informations, consultez [Boîtes aux lettres inactives dans Exchange Online](inactive-mailboxes-in-office-365.md). 

## <a name="how-to-configure-a-retention-policy-for-exchange"></a>Comment configurer une stratégie de rétention pour Exchange

Suivez les instructions pour [créer et configurer des stratégies de rétention](create-retention-policies.md) et pour la page **Choisir les emplacements** de l’assistant, sélectionnez l’une des options suivantes :

- **Appliquer la stratégie uniquement au contenu dans les courriers électroniques Exchange, les dossiers publics, les groupes Office 365, les documents OneDrive et SharePoint**

- **Choisir des emplacements spécifiques** > **Messagerie Exchange**, **Dossiers publics Exchange** et **groupes Office 365**.

Même si un groupe Microsoft 365 possède une boîte aux lettres Exchange, une stratégie de rétention qui inclut l’ensemble de l’emplacement de la **messagerie Exchange** n’inclut pas le contenu des boîtes aux lettres du groupe Microsoft 365. Pour conserver le contenu de ces boîtes aux lettres, sélectionnez l’emplacement **groupes Office 365**.
