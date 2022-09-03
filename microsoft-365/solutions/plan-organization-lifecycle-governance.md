---
title: Planifier l’organisation et la gouvernance du cycle de vie pour les groupes Microsoft 365 et Microsoft Teams
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Se pencher sur les options de gouvernance du cycle de vie pour les outils de collaboration dans Microsoft 365
ms.openlocfilehash: ef47d7f9000cb6c350f8f90c47881e65d58d3128
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67575678"
---
# <a name="plan-organization-and-lifecycle-governance-for-microsoft-365-groups-and-microsoft-teams"></a>Planifier l’organisation et la gouvernance du cycle de vie pour les groupes Microsoft 365 et Microsoft Teams

Les groupes Microsoft 365 disposent d’un ensemble complet d’outils permettant d’implémenter les fonctionnalités de gouvernance dont votre organisation a besoin. 

La section suivante décrit les fonctionnalités, recommande les meilleures pratiques et fournit des conseils pour poser les bonnes questions afin de déterminer les exigences de gouvernance et comment les satisfaire.

## <a name="control-who-can-create-microsoft-365-groups"></a>Contrôler qui peut créer des groupes Microsoft 365

Les groupes peuvent être créés par des utilisateurs finaux à partir de plusieurs points de terminaison, notamment Outlook, SharePoint, Teams et d’autres environnements.

![image desc.](../media/04.png)

Nous recommandons vivement le libre-service pour autonomiser les propriétaires de groupes et aider les utilisateurs à accomplir leur travail plus facilement. La limitation de la création de groupes et d’équipes peut ralentir la productivité des utilisateurs, car de nombreux services Microsoft 365 nécessitent la création de groupes pour que le service fonctionne.

Tenez compte des options de gouvernance suivantes pour la création de groupes :

- Pour limiter l’étalement des groupes, utilisez des [stratégies d’expiration de groupes](microsoft-365-groups-expiration-policy.md) pour supprimer automatiquement les groupes qui ne sont pas utilisés.
- Limitez la création de groupes aux membres d’un [groupe de sécurité avec une appartenance dynamique](/azure/active-directory/users-groups-roles/groups-create-rule) contenant, par exemple, tous les employés à temps plein.
- Limitez la création d’un groupe à un groupe de sécurité et demandez aux utilisateurs d’effectuer une formation dans les stratégies d’utilisation de groupe de votre organisation afin de devenir membres du groupe de sécurité.

Si vous souhaitez limiter qui peut créer des groupes, consultez [Gérer qui peut créer des groupes Microsoft 365](manage-creation-of-groups.md) pour plus d’informations sur la configuration de ce groupe.

## <a name="group-delete-restore-and-archiving"></a>Suppression, restauration et archivage de groupe

Lorsqu’un groupe Microsoft 365 est supprimé, par défaut, il est conservé pendant 30 jours. Cette période de 30 jours est appelée « suppression réversible », car vous avez encore la possibilité de le restaurer. Après cette période de 30 jours, le groupe et le contenu associé sont supprimés de manière définitive et ne peuvent plus être restaurés.

Si des stratégies de rétention sont en place pour conserver la conversation, les fichiers ou la messagerie, ces éléments sont conservés une fois le groupe supprimé. Pour [plus d’informations, consultez En savoir plus sur les stratégies de rétention](../compliance/retention.md) .

Si vous souhaitez supprimer un groupe mais conserver le contenu d’un ou de plusieurs services connectés au groupe, consultez [les groupes d’archives, les équipes et Yammer](end-life-cycle-groups-teams-sites-yammer.md) pour plus d’informations.

## <a name="group-naming-policy"></a>Stratégie de noms de groupes

Une stratégie de nommage de groupes peut vous aider à régir les groupes de deux manières :

- Une stratégie de nommage de préfixe/suffixe peut être utilisée pour appliquer des chaînes fixes ou des attributs Azure AD au début ou à la fin d’un nom de groupe et de son adresse e-mail associée. En procédant ainsi, vous pouvez garantir l’inclusion, par exemple, de noms de départements ou de régions dans les noms de groupes.
- Une stratégie de mots bloqués peut garantir que certains mots, tels que les noms des cadres, ne sont pas utilisés dans les noms de groupes.

Les stratégies d’affectation de noms sont appliquées lorsque des groupes sont créés à partir de l’un des services connectés au groupe.

Si vous décidez d’utiliser des stratégies d’affectation de noms pour les groupes, consultez [Groupes Microsoft 365 stratégie d’affectation de noms](groups-naming-policy.md).

## <a name="group-expiration-policy"></a>Stratégie d’expiration de groupe

Vous pouvez spécifier une période d’expiration et tout groupe qui atteint la fin de cette période et qui n’est pas renouvelé sera supprimé. La période d’expiration commence à la création du groupe ou à la date de son dernier renouvellement.

Une fois que vous avez défini des groupes pour qu’ils expirent :
- Les propriétaires du groupe sont avertis de renouveler le groupe à mesure que l’expiration approche.
- Les groupes actifs sont renouvelés automatiquement.
- Tout groupe qui n’est pas renouvelé est supprimé.
- Tout groupe supprimé peut être restauré dans les 30 jours par les propriétaires du groupe ou l’administrateur.

Les stratégies d’expiration sont un bon moyen de limiter l’étalement des groupes en veillant à ce que les groupes qui ne sont plus utilisés soient supprimés. Si vous souhaitez créer une stratégie d’expiration de groupe, consultez [Groupes Microsoft 365 stratégie d’expiration](microsoft-365-groups-expiration-policy.md).

## <a name="related-topics"></a>Voir aussi

[Recommandations en matière de planification de la gouvernance de collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Supprimer un ancien employé et sécuriser les données](/microsoft-365/admin/add-users/remove-former-employee)
