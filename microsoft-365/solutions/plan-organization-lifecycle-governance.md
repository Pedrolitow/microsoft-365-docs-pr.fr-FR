---
title: Planifier la gouvernance de l’organisation et du cycle de vie Microsoft 365 groupes et Microsoft Teams
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
recommendations: false
description: En savoir plus sur les options de gouvernance du cycle de vie pour les outils de collaboration Microsoft 365
ms.openlocfilehash: 7d88618b75ef731bf38df029970efdc05f3eea5a
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52538818"
---
# <a name="plan-organization-and-lifecycle-governance-for-microsoft-365-groups-and-microsoft-teams"></a>Planifier la gouvernance de l’organisation et du cycle de vie Microsoft 365 groupes et Microsoft Teams

Microsoft 365 groupes disposent d’un riche ensemble d’outils pour implémenter les fonctionnalités de gouvernance dont votre organisation a besoin. 

La section suivante décrit les fonctionnalités, recommande les meilleures pratiques et fournit des conseils pour poser les bonnes questions afin de déterminer les conditions requises pour la gouvernance et comment y répondre.

## <a name="control-who-can-create-microsoft-365-groups"></a>Contrôler les personnes qui peuvent créer Microsoft 365 groupes

Les groupes peuvent être créés par les utilisateurs finaux à partir de plusieurs points de fin, notamment Outlook, SharePoint, Teams et d’autres environnements.

![image desc](../media/04.png)

Nous vous recommandons vivement le libre-service pour permettre aux propriétaires de groupes et aider les utilisateurs à faire leur travail plus facilement. La limitation de la création de groupes et d’équipes peut ralentir la productivité des utilisateurs, car de nombreux services Microsoft 365 nécessitent que des groupes soient créés pour que le service fonctionne.

Prenons les options de gouvernance suivantes pour la création de groupes :

- Pour limiter la prolifération des groupes, utilisez des [stratégies d’expiration](microsoft-365-groups-expiration-policy.md) de groupes pour supprimer automatiquement les groupes qui ne sont pas utilisés.
- Limiter la création de groupes aux membres [d’un](/azure/active-directory/users-groups-roles/groups-create-rule) groupe de sécurité avec une appartenance dynamique contenant, par exemple, tous les employés à plein temps.
- Limitez la création de groupes à un groupe de sécurité et obligez les utilisateurs à effectuer une formation sur les stratégies d’utilisation des groupes de votre organisation afin de devenir membres du groupe de sécurité.

Si vous souhaitez limiter les personnes autorisées à créer des groupes, consultez Gérer les personnes autorisées à créer des groupes Microsoft 365 [pour](manage-creation-of-groups.md) plus d’informations sur la configuration de ce groupe.

## <a name="group-delete-restore-and-archiving"></a>Suppression, restauration et archivage de groupes

Lorsqu’Microsoft 365 groupe est supprimé, il est conservé par défaut pendant 30 jours. Cette période de 30 jours est appelée « suppression réversible », car vous avez encore la possibilité de le restaurer. Après cette période de 30 jours, le groupe et le contenu associé sont supprimés de manière définitive et ne peuvent plus être restaurés.

Si vous avez des stratégies de rétention en place pour conserver la conversation, les fichiers ou le courrier, ces éléments sont conservés après la suppression du groupe. Pour plus [d’informations, voir](../compliance/retention.md) En savoir plus sur les stratégies de rétention.

Si vous souhaitez supprimer un groupe, mais conserver le contenu d’un ou plusieurs services connectés à un groupe, consultez Groupes d’archivage, équipes et [Yammer](end-life-cycle-groups-teams-sites-yammer.md) pour plus d’informations.

## <a name="group-naming-policy"></a>Stratégie de noms de groupes

Une stratégie de noms de groupes peut vous aider à régir les groupes de deux manières :

- Une stratégie de noms de préfixe/suffixe peut être utilisée pour appliquer des chaînes fixes ou des attributs Azure AD au début ou à la fin d’un nom de groupe et de son adresse de messagerie associée. En faisant cela, vous pouvez garantir l’inclusion, par exemple, des noms de service ou des régions dans les noms de groupes.
- Une stratégie de mots bloqués permet de s’assurer que certains mots, tels que les noms des cadres, ne sont pas utilisés dans les noms de groupes.

Les stratégies d’attribution de noms sont appliquées lorsque des groupes sont créés à partir de l’un des services connectés à un groupe.

Si vous décidez d’utiliser des stratégies d’attribution de noms pour les groupes, [voir Microsoft 365 d’attribution de](groups-naming-policy.md)noms de groupes.

## <a name="group-expiration-policy"></a>Stratégie d’expiration de groupe

Vous pouvez spécifier une période d’expiration et tout groupe qui arrive à la fin de cette période et qui n’est pas renouvelé sera supprimé. La période d’expiration commence lors de la création du groupe ou à la date de son dernier renouvellement.

Une fois que vous avez fixé l’expiration des groupes :
- Les propriétaires du groupe sont avertis de renouveler le groupe à mesure que l’expiration approche.
- Les groupes actifs sont renouvelés automatiquement.
- Tout groupe qui n’est pas renouvelé est supprimé.
- Tout groupe supprimé peut être restauré dans les 30 jours par les propriétaires du groupe ou l’administrateur.

Les stratégies d’expiration sont un bon moyen de limiter la prolifération des groupes en veillant à ce que les groupes qui ne sont plus utilisés soient supprimés. Si vous souhaitez créer une stratégie d’expiration de groupe, voir [Microsoft 365 stratégie d’expiration de groupe.](microsoft-365-groups-expiration-policy.md)

## <a name="related-topics"></a>Voir aussi

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Supprimer un ancien employé et sécuriser les données](/microsoft-365/admin/add-users/remove-former-employee)
