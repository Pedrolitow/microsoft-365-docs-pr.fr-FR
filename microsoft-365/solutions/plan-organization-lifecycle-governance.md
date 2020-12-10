---
title: Planification de la gouvernance d’organisation et du cycle de vie pour les groupes Microsoft 365 et Microsoft teams
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
description: Les options de gouvernance du cycle de vie des outils de collaboration dans Microsoft 365
ms.openlocfilehash: 4d779701d241fc7178ab759063be1b8cdf2e960c
ms.sourcegitcommit: a0cddd1f888edb940717e434cda2dbe62e5e9475
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49613019"
---
# <a name="plan-organization-and-lifecycle-governance-for-microsoft-365-groups-and-microsoft-teams"></a>Planification de la gouvernance d’organisation et du cycle de vie pour les groupes Microsoft 365 et Microsoft teams

Les groupes Microsoft 365 disposent d’un ensemble complet d’outils permettant d’implémenter les capacités de gouvernance dont votre organisation a besoin. 

La section suivante décrit les fonctionnalités, recommande les meilleures pratiques et fournit des instructions pour poser les bonnes questions afin de déterminer les exigences de gouvernance et comment les répondre.

## <a name="control-who-can-create-microsoft-365-groups"></a>Contrôler qui peut créer des groupes Microsoft 365

Les utilisateurs finaux peuvent créer des groupes à partir de plusieurs points de terminaison, dont Outlook, SharePoint, teams et d’autres environnements.

![Description de l’image](../media/04.png)

Nous vous recommandons vivement de fournir des propriétaires de groupes et d’aider les utilisateurs à effectuer leur travail plus facilement. La limitation de la création de groupes et d’équipes peut ralentir la productivité des utilisateurs, car de nombreux services Microsoft 365 nécessitent la création de groupes pour que le service fonctionne.

Envisagez les options de gouvernance suivantes pour la création de groupes :

- Pour limiter la prolifération des groupes, utilisez les [stratégies d’expiration des groupes](microsoft-365-groups-expiration-policy.md) pour supprimer automatiquement les groupes qui ne sont pas utilisés.
- Limitez la création de groupes aux membres d’un groupe de [sécurité dont l’appartenance dynamique](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-create-rule) contient, par exemple, tous les employés à plein temps.
- Limitez la création de groupe à un groupe de sécurité et obligez les utilisateurs à effectuer une formation dans les stratégies d’utilisation de groupe de votre organisation afin de devenir membres du groupe de sécurité.

Si vous souhaitez limiter les personnes autorisées à créer des groupes, voir [gérer les personnes autorisées à créer des groupes Microsoft 365](manage-creation-of-groups.md) pour plus d’informations sur la configuration de ce.

## <a name="group-delete-restore-and-archiving"></a>Suppression, restauration et archivage de groupe

Lorsqu’un groupe Microsoft 365 est supprimé, il est conservé par défaut pendant 30 jours. Cette période de 30 jours est appelée « suppression réversible », car vous avez encore la possibilité de le restaurer. Après cette période de 30 jours, le groupe et le contenu associé sont supprimés de manière définitive et ne peuvent plus être restaurés.

Si vous avez des stratégies de rétention en place pour conserver la conversation, les fichiers ou le courrier, ces éléments seront conservés une fois le groupe supprimé. Pour plus d’informations, voir [en savoir plus sur les stratégies de rétention](https://docs.microsoft.com/microsoft-365/compliance/retention-policies) .

Si vous souhaitez supprimer un groupe tout en conservant le contenu d’un ou plusieurs services connectés à un groupe, reportez-vous à la rubrique [groupes d’archivage, teams et Yammer](end-life-cycle-groups-teams-sites-yammer.md) pour obtenir des informations.

## <a name="group-naming-policy"></a>Stratégie de noms de groupes

Une stratégie de noms de groupes peut vous aider à gérer les groupes de deux manières :

- Une stratégie de noms de préfixe/suffixe peut être utilisée pour appliquer des chaînes fixes ou des attributs Azure AD au début ou à la fin d’un nom de groupe et de son adresse de messagerie associée. En procédant ainsi, vous pouvez vous assurer de l’inclusion, par exemple, des noms de service ou des régions dans les noms de groupe.
- Une stratégie de mots bloqués permet de s’assurer que certains mots, tels que les noms des cadres, ne sont pas utilisés dans les noms de groupe.

Les stratégies d’attribution de noms sont appliquées lors de la création de groupes à partir de l’un des services connectés à un groupe.

Si vous décidez d’utiliser des stratégies d’attribution de noms pour les groupes, consultez la rubrique [stratégie de noms de groupes Microsoft 365](groups-naming-policy.md).

## <a name="group-expiration-policy"></a>Stratégie d’expiration de groupe

Vous pouvez spécifier une période d’expiration et tout groupe qui atteint la fin de cette période et qui n’est pas renouvelé, sera supprimé. La période d’expiration commence lorsque le groupe est créé, ou à la date à laquelle il a été renouvelé pour la dernière fois.

Une fois que vous avez défini les groupes pour qu’ils expirent :
- Les propriétaires du groupe sont invités à renouveler le groupe en tant qu’expiration.
- Les groupes actifs sont renouvelés automatiquement.
- Tout groupe qui n’est pas renouvelé est supprimé.
- Tous les groupes qui sont supprimés peuvent être restaurés dans les 30 jours par les propriétaires du groupe ou l’administrateur.

Les stratégies d’expiration constituent un bon moyen de limiter la prolifération des groupes en s’assurant que les groupes qui ne sont plus utilisés sont supprimés. Si vous souhaitez créer une stratégie d’expiration de groupe, consultez la rubrique [Microsoft 365 Group expiration Policy](microsoft-365-groups-expiration-policy.md).

## <a name="related-topics"></a>Voir aussi

[Planification de la gouvernance de collaboration étape par étape](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Création de votre plan de gouvernance de collaboration](collaboration-governance-first.md)
