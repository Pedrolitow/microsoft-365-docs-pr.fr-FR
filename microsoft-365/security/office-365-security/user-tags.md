---
title: Balises utilisateur dans Office 365 – Protection avancée contre les menaces
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à identifier des groupes d’utilisateurs spécifiques à l’aide de balises utilisateur dans Office 365 DAV (plan 2). Le filtrage des balises est disponible dans les alertes, les rapports et les enquêtes dans la protection avancée contre les menaces d’Office 365 pour identifier rapidement les utilisateurs balisés.
ms.openlocfilehash: 475bf976a71fb688df8db9ac25f3b397c078d79a
ms.sourcegitcommit: 260c69fa31a898428d51cfdbd762c5f0213c403c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2020
ms.locfileid: "48417274"
---
# <a name="user-tags-in-office-365-atp"></a>Balises utilisateur dans Office 365 – Protection avancée contre les menaces

> [!NOTE]
> La fonctionnalité de balises utilisateur est en mode aperçu, n’est pas accessible à tous et peut faire l’objet de modifications. Pour plus d’informations sur le calendrier des publications, consultez la feuille de [route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap).

Les balises utilisateur sont des identificateurs pour des groupes d’utilisateurs spécifiques dans [Office 365 Advanced Threat Protection (ATP)](office-365-atp.md). Il existe deux types de balises utilisateur :

- **Balises système**: actuellement, le [compte de priorité](https://docs.microsoft.com/microsoft-365/admin/setup/priority-accounts) est le seul type de balise système.
- **Balises personnalisées**: créez ces balises utilisateur vous-même.

Si votre organisation dispose d’Office 365 DAV plan 2 (inclus dans votre abonnement ou en tant que module complémentaire), vous pouvez créer des balises utilisateur personnalisées en plus de l’utilisation de la balise Accounts Priority.

Une fois que vous avez appliqué des balises système ou des balises personnalisées aux utilisateurs, vous pouvez utiliser ces balises comme filtres dans les alertes, les rapports et les analyses :

- [Alertes dans le centre de sécurité & conformité](alerts.md)
- [Explorateur de menaces et détections en temps réel](threat-explorer.md)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Vues de campagne](campaigns.md)

Cet article explique comment configurer les balises utilisateur dans le centre de sécurité & conformité. Il n’existe pas de cmdlets dans Security & Compliance Center pour gérer les balises utilisateur.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **balises utilisateur** , ouvrez <https://protection.office.com/userTags> .

- Pour créer, modifier ou supprimer des **balises utilisateur personnalisées**, vous devez être membre des groupes de rôles gestion de l' **organisation** ou **administrateur de sécurité** dans le centre de sécurité & conformité. Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

- Pour configurer des comptes de priorité (balises système), vous devez être un [administrateur général](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#global-administrator--company-administrator) ou un [administrateur Exchange](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#exchange-administrator).

  Vous pouvez également gérer et surveiller les comptes de priorité dans le centre d’administration 365 de Microsoft. Pour obtenir des instructions, consultez la rubrique [Manage and Monitor Priority Accounts](https://docs.microsoft.com/microsoft-365/admin/setup/priority-accounts).

## <a name="use-the-security-center-to-create-user-tags"></a>Utiliser le centre de sécurité pour créer des balises utilisateur

1. Dans le centre de sécurité, accédez **Threat management** aux \> **balises utilisateur**de gestion des menaces.

2. Sur la page **balises utilisateur** qui s’ouvre, cliquez sur **créer une balise**.

3. L’Assistant **créer une balise** s’ouvre en un nouveau. Dans la page **définir la balise** , configurez les paramètres suivants :

   - **Nom**: entrez un nom unique et descriptif pour la balise. Il s’agit de la valeur que vous allez voir et utiliser.

   - **Description**: entrez une description facultative pour la balise.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **affecter des boîtes aux lettres** , effectuez l’une des opérations suivantes :

   - Cliquez sur **Ajouter des boîtes aux lettres**. Dans le survol qui s’affiche, effectuez l’une des opérations suivantes pour ajouter des utilisateurs ou des groupes individuels :

     - Cliquez dans la zone et faites défiler la liste pour sélectionner un utilisateur ou un groupe.
     - Cliquez dans la zone et commencez à taper pour filtrer la liste, puis sélectionnez un utilisateur ou un groupe.
     - Pour ajouter des valeurs supplémentaires, cliquez dans une zone vide de la zone.
     - Pour supprimer des entrées individuelles de la zone, cliquez sur **supprimer** l' ![ icône supprimer de ](../../media/scc-remove-icon.png) l’utilisateur ou du groupe dans la zone.
     - Pour supprimer les entrées existantes de la liste située en dessous du champ, cliquez sur **supprimer** ![ l’icône supprimer de l' ](../../media/scc-remove-icon.png) entrée.

     Lorsque vous avez terminé, cliquez sur **Ajouter**.

   - Cliquez sur **Importer** pour sélectionner un fichier texte qui contient les adresses de messagerie des utilisateurs ou des groupes. Assurez-vous que le fichier texte contient une entrée par ligne.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **balise de révision** , vérifiez vos paramètres. Vous pouvez cliquer sur **modifier** dans la section spécifique pour apporter des modifications.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

## <a name="use-the-security-center-to-view-user-tags"></a>Utiliser le centre de sécurité pour afficher les balises utilisateur

1. Dans le centre de sécurité, accédez **Threat management** aux \> **balises utilisateur**de gestion des menaces.

2. Sur la page **balises utilisateur** qui s’ouvre, sélectionnez la balise utilisateur que vous souhaitez afficher (ne cliquez pas sur la case à cocher).

3. Dans le menu déroulant en lecture seule qui s’affiche, passez en revue les paramètres.

   Lorsque vous avez terminé, cliquez sur **Fermer**.

## <a name="use-the-security-center-to-modify-user-tags"></a>Utiliser le centre de sécurité pour modifier les balises utilisateur

1. Dans le centre de sécurité, accédez **Threat management** aux \> **balises utilisateur**de gestion des menaces.

2. Sur la page **balises utilisateur** qui s’ouvre, sélectionnez la balise utilisateur que vous souhaitez afficher, puis cliquez sur **modifier la balise**.

3. L’Assistant stratégie s’ouvre dans une **balise de modification** . Cliquez sur **suivant** pour passer en revue et modifier les paramètres.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

## <a name="use-the-security-center-to-remove-user-tags"></a>Utiliser le centre de sécurité pour supprimer des balises utilisateur

**Remarque**: vous ne pouvez pas supprimer la balise de **compte de priorité** intégrée.

1. Dans le centre de sécurité, accédez **Threat management** aux \> **balises utilisateur**de gestion des menaces.

2. Sur la page **balises utilisateur** qui s’ouvre, sélectionnez la balise utilisateur que vous souhaitez supprimer, cliquez sur **Supprimer la balise**, puis sélectionnez **Oui, supprimer** dans l’avertissement qui s’affiche.
