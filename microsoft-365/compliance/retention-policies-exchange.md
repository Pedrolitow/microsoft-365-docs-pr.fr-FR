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
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Découvrez le fonctionnement de la rétention Microsoft 365 pour Exchange, à l’aide de stratégies de rétention et d’étiquettes de rétention pour gérer la rétention automatique ou la suppression des données pour votre organisation.
ms.openlocfilehash: 6337c1e23bf2d78ca1bd2c11ebbe8340e2045b5b
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66942141"
---
# <a name="learn-about-retention-for-exchange"></a>Découvrir la rétention pour Exchange

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Les informations contenues dans cet article complètent [Découvrir la rétention](retention.md) car elles contiennent des informations spécifiques à Exchange. Pour d’autres charges de travail, voir :

- [En savoir plus sur la rétention dans SharePoint et OneDrive](retention-policies-sharepoint.md)
- [En savoir plus sur la rétention dans Microsoft Teams](retention-policies-teams.md)
- [Découvrir la rétention pour Yammer](retention-policies-yammer.md)

## <a name="whats-included-for-retention-and-deletion"></a>Éléments composant la rétention et la suppression

Les éléments Exchange suivants des boîtes aux lettres utilisateur et des boîtes aux lettres partagées peuvent être conservés et supprimés à l’aide de stratégies de rétention et d’étiquettes de rétention : messages électroniques (messages reçus, brouillons, messages envoyés) avec des pièces jointes, des tâches lorsqu’ils ont une date de fin et des notes. 

Les éléments de calendrier qui ont une date de fin sont prises en charge pour les stratégies de rétention, mais ne sont pas pris en charge pour les étiquettes de rétention.

Les contacts, ainsi que les tâches et les éléments de calendrier qui n’ont pas de date de fin ne sont pas pris en charge.

Les autres éléments stockés dans une boîte aux lettres, tels que les messages Skype et Teams, ne sont pas inclus dans les stratégies ou étiquettes de rétention de Exchange. Ces éléments ont leurs propres stratégies de rétention.

Les boîtes aux lettres doivent avoir au moins 10 Mo de données avant que les paramètres de rétention ne s’appliquent à celles-ci et que des étiquettes de rétention puissent leur être publiées.

## <a name="how-retention-works-for-exchange"></a>Fonctionnement de la rétention pour Exchange

Les boîtes aux lettres et les dossiers publics utilisent le [dossier Éléments récupérables](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) pour conserver des éléments. Seules les personnes disposant d’autorisations eDiscovery peuvent afficher les éléments dans le dossier Éléments récupérables d’un autre utilisateur.
  
Lorsqu’un utilisateur supprime un message d’un dossier autre que le dossier Éléments supprimés, le message est par défaut déplacé vers le dossier Éléments supprimés. Toutefois, un utilisateur peut supprimer de façon réversible un élément (Maj + Suppr) dans n’importe quel dossier, ce qui permet d’ignorer le dossier Éléments supprimés et place directement l’élément dans le dossier Éléments récupérables.
  
Lorsque vous appliquez des paramètres de rétention à des données Exchange, un travail du minuteur évalue régulièrement les éléments du dossier Éléments récupérables. Si un élément ne correspond pas aux règles d’au moins une stratégie de rétention ou une étiquette de rétention pour retenir l’élément. Il est supprimé définitivement du dossier Éléments récupérables.

> [!NOTE]
> En raison du [premier principe de rétention](retention.md#the-principles-of-retention-or-what-takes-precedence), la suppression définitive est toujours suspendue si le même élément doit être retenu à cause d’une autre stratégie de rétention ou d’une étiquette de rétention ou qu’il est bloqué pour des raisons juridiques ou d’enquête.

L’exécution du travail du minuteur peut prendre jusqu’à sept jours, et l’emplacement Exchange doit contenir au moins 10 Mo.
  
Lorsqu’un utilisateur tente de modifier les propriétés d’un élément de boîte aux lettres (objet, corps, pièces jointes, expéditeurs et destinataires ou la date d’envoi ou de réception d’un message), une copie de l’élément d’origine est enregistrée dans le dossier Éléments récupérables avant la validation de la modification. Cette action se produit à chaque modification ultérieure. À la fin de la période de rétention, les copies présentes dans le dossier Éléments récupérables sont supprimées définitivement.

Une fois que les paramètres de rétention sont appliqués à du contenu Exchange, les chemins d’accès au contenu sont fonction des paramètres de rétention qui consistent à conserver et à supprimer, à conserver uniquement ou à supprimer uniquement.

Lorsque les paramètres de la stratégie de rétention sont définis sur conserver et supprimer :

![Diagramme du flux de rétention dans la messagerie et les dossiers publics.](../media/88f174cc-bbf4-4305-93d7-0515f496c8f9.png)

1. **Si l’élément est modifié ou supprimé définitivement** par l’utilisateur (par MAJ + SUPPR ou supprimé du dossier Éléments supprimés) pendant la période de rétention : l’élément est déplacé (ou copié, dans le cas d’une modification) vers le dossier Éléments récupérables. Ici, un travail du minuteur s’exécute régulièrement et identifie les éléments dont la période de rétention a expiré, et ces éléments sont supprimés définitivement dans les 14 jours suivant la fin de la période de rétention. Notez que le paramètre par défaut est de 14 jours, mais qu’il peut être configuré sur 30 jours.

2. **Si l’élément n’est pas modifié ou supprimé** pendant la période de rétention. Le même processus s’exécute régulièrement sur tous les dossiers dans la boîte aux lettres et identifie les éléments dont la période de rétention a expiré, et ces éléments sont supprimés définitivement dans les 14 jours suivant la fin de la période de rétention. Notez que le paramètre par défaut est de 14 jours, mais qu’il peut être configuré sur 30 jours. 

Lorsque les paramètres de la stratégie de rétention sont définis sur conserver uniquement ou supprimer uniquement, les chemins d’accès du contenu sont des variantes de l’option conserver et supprimer :

### <a name="content-paths-for-retain-only-retention-settings"></a>Chemins d’accès du contenu pour la stratégie de rétention de conservation uniquement

1. **Si l’élément est modifié ou supprimé** pendant la période de rétention : une copie de l’élément d’origine est créée dans le dossier Éléments récupérables et conservée jusqu’à la fin de la période de rétention, lorsque la copie dans le dossier Éléments récupérables est définitivement supprimée dans un délai de 14 jours après l’expiration de l’élément. 

2. **Si le contenu n’est ni modifié ni supprimé** pendant la période de rétention : rien ne se passe avant et après la période de rétention ; le document reste à son emplacement d’origine.

### <a name="content-paths-for-delete-only-retention-settings"></a>Chemins d’accès du contenu pour la stratégie de rétention de suppression uniquement

1. **Si le contenu n’est pas supprimé** pendant la période de rétention : à la fin de la période configurée dans la stratégie de rétention, l’élément est déplacé vers le dossier Éléments récupérables. 

2. **Si l’élément est supprimé** pendant la période de rétention : l’élément est placé immédiatement dans le dossier Éléments récupérables. Si un utilisateur supprime l’élément à partir de là ou vide le dossier Éléments récupérables, l’élément est définitivement supprimé. Dans le cas contraire, l’élément est définitivement supprimé après avoir été placé dans le dossier Éléments récupérables pendant 14 jours. 

## <a name="user-notification-of-expiry-date"></a>Notification de l'utilisateur sur la date d’expiration

Les stratégies de rétention pour Exchange, contrairement aux stratégies de rétention pour d’autres charges de travail Microsoft 365, ont une présence utilisateur en affichant, en haut de chaque message par e-mail, le nom de la stratégie de rétention qui a la date d’expiration la plus courte pour l’élément et la date d’expiration calculée de celui-ci. Les utilisateurs ne voient pas cette notification si la stratégie de rétention ne supprime pas les éléments (conserver uniquement).

Si une étiquette de rétention est appliquée à un message par e-mail, le nom de cette étiquette et date d’expiration correspondante est toujours affichée et remplace le nom et la date d’une stratégie de rétention appliquée à la boîte aux lettres.

N’oubliez pas que, dans ce contexte, la date d’expiration pour la suppression d’un e-mail correspond à celle à laquelle les utilisateurs peuvent s’attendre à ce que le message par e-mail se déplace automatiquement vers le dossier Éléments récupérables (s’il ne s’y trouve pas encore). Les e-mails dans le Dossier Éléments récupérables ne sont pas supprimés de manière définitive et restent à cet emplacement à des fins de conformité s’ils font l’objet de paramètres de rétention pour les conserver ou s’ils sont mis sous conservation eDiscovery pour des raisons juridiques ou d’enquête.

## <a name="when-a-user-leaves-the-organization"></a>Lorsqu’un utilisateur quitte l’organisation 

Si un utilisateur quitte votre organisation et que sa boîte aux lettres est incluse dans une stratégie pour la rétention, la boîte aux lettres devient inactive lorsque le compte d’utilisateur Microsoft 365 est supprimé. Le contenu d’une boîte aux lettres inactive est toujours soumis à une stratégie de rétention placée sur la boîte aux lettres avant que celle-ci ne devienne inactive et ce contenu est disponible pour une recherche eDiscovery. Pour obtenir plus d’informations, consultez l’article [Boîtes aux lettres inactives dans Exchange Online](inactive-mailboxes-in-office-365.md).

Lorsque les paramètres de rétention ne s’appliquent plus, car les données sont définitivement supprimées ou la période de rétention a expiré, l’administrateur Exchange peut désormais [supprimer la boîte aux lettres inactive](delete-an-inactive-mailbox.md). Dans ce cas, la boîte aux lettres inactive n’est pas automatiquement supprimée.

## <a name="configuration-guidance"></a>Instructions de configuration

Si vous débutez avec la configuration de la rétention dans Microsoft 365, consultez [Démarrage avec la gestion du cycle de vie des données](get-started-with-data-lifecycle-management.md).

Si vous êtes prêt à configurer une stratégie ou une étiquette de rétention pour Exchange, consultez les instructions suivantes :
- [Créer et configurer des stratégies de rétention](create-retention-policies.md)
- [Publier des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)
- [Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)
