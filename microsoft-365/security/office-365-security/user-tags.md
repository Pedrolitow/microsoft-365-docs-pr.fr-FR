---
title: Balises utilisateur dans Microsoft Defender pour Office 365
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
description: Les administrateurs peuvent apprendre à identifier des groupes d’utilisateurs spécifiques à l’aide de balises utilisateur dans Microsoft Defender pour Office 365 plan 2. Le filtrage des balises est disponible dans les alertes, les rapports et les analyses de Microsoft Defender pour Office 365 afin d’identifier rapidement les utilisateurs balisés.
ms.openlocfilehash: ad06bf90f1ecb93d671bfcad6fad0b4f2a952cb2
ms.sourcegitcommit: 47de4402174c263ae8d70c910ca068a7581d04ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "49663606"
---
# <a name="user-tags-in-microsoft-defender-for-office-365"></a>Balises utilisateur dans Microsoft Defender pour Office 365

> [!NOTE]
> La fonctionnalité de balises utilisateur est en mode aperçu, n’est pas accessible à tous et peut faire l’objet de modifications. Pour plus d’informations sur le calendrier des publications, consultez la feuille de [route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap).

Les balises utilisateur sont des identificateurs pour des groupes d’utilisateurs spécifiques dans [Microsoft Defender pour Office 365](office-365-atp.md). Il existe deux types de balises utilisateur :

- **Balises système**: actuellement, le [compte de priorité](https://docs.microsoft.com/microsoft-365/admin/setup/priority-accounts) est le seul type de balise système.
- **Balises personnalisées**: créez ces balises utilisateur vous-même.

Si votre organisation a Defender pour Office 365 plan 2 (inclus dans votre abonnement ou en tant que module complémentaire), vous pouvez créer des balises utilisateur personnalisées en plus de l’utilisation de la balise Accounts Priority.

Une fois que vous avez appliqué des balises système ou des balises personnalisées aux utilisateurs, vous pouvez utiliser ces balises comme filtres dans les alertes, les rapports et les analyses :

- [Alertes dans le centre de sécurité & conformité](alerts.md)
- [Explorateur de menaces et détections en temps réel](threat-explorer.md)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Vues de campagne](campaigns.md)
- Pour les comptes prioritaires, vous pouvez utiliser le [rapport problèmes de messagerie pour les comptes prioritaires](https://docs.microsoft.com/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report) dans le centre d’administration Exchange.

Cet article explique comment configurer les balises utilisateur dans le centre de sécurité & conformité. Il n’existe pas de cmdlets dans Security & Compliance Center pour gérer les balises utilisateur.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **balises utilisateur** , ouvrez <https://protection.office.com/userTags> .

- Pour pouvoir utiliser ce cmdlet, vous devez disposer des autorisations dans le centre de sécurité et conformité Office 365.
  - Pour créer, modifier et supprimer des balises utilisateur, vous devez être membre des groupes de rôles de gestion de l' **organisation** ou d' **administrateur de sécurité** .
  - Pour ajouter et supprimer des membres de balises utilisateur existantes, vous devez être membre des groupes de rôles gestion de l' **organisation**, administrateur de la **sécurité** ou **opérateur de sécurité** .
  - Pour un accès en lecture seule aux balises utilisateur, vous devez être membre des groupes de rôles **lecteur global** ou **lecteur de sécurité** .

  Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le centre de sécurité et de conformité _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).
  - La gestion des balises utilisateur est contrôlée par les rôles du **lecteur de balises**, du **collaborateur** de balises et du **Gestionnaire de balises** .

- Vous pouvez également gérer et surveiller les comptes de priorité dans le centre d’administration 365 de Microsoft. Pour obtenir des instructions, consultez la rubrique [Manage and Monitor Priority Accounts](https://docs.microsoft.com/microsoft-365/admin/setup/priority-accounts).

## <a name="use-the-security-center-to-create-user-tags"></a>Utiliser le centre de sécurité pour créer des balises utilisateur

1. Dans le centre de sécurité, accédez  aux \> **balises utilisateur** de gestion des menaces.

2. Sur la page **balises utilisateur** qui s’ouvre, cliquez sur **créer une balise**.

3. L’Assistant **créer une balise** s’ouvre en un nouveau. Dans la page **définir la balise** , configurez les paramètres suivants :
   - **Nom**: entrez un nom unique et descriptif pour la balise. Il s’agit de la valeur que vous allez voir et utiliser.
   - **Description**: entrez une description facultative pour la balise.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **affecter des utilisateurs** , effectuez l’une des opérations suivantes :

   - Cliquez sur **Ajouter des utilisateurs**. Dans le survol qui s’affiche, effectuez l’une des opérations suivantes pour ajouter des utilisateurs ou des groupes individuels :
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

1. Dans le centre de sécurité, accédez  aux \> **balises utilisateur** de gestion des menaces.

2. Sur la page **balises utilisateur** qui s’ouvre, sélectionnez la balise utilisateur que vous souhaitez afficher (ne cliquez pas sur la case à cocher).

3. Dans le menu déroulant en lecture seule qui s’affiche, passez en revue les paramètres.

   Lorsque vous avez terminé, cliquez sur **Fermer**.

## <a name="use-the-security-center-to-modify-user-tags"></a>Utiliser le centre de sécurité pour modifier les balises utilisateur

1. Dans le centre de sécurité, accédez  aux \> **balises utilisateur** de gestion des menaces.

2. Sur la page **balises utilisateur** qui s’ouvre, sélectionnez la balise utilisateur que vous souhaitez afficher, puis cliquez sur **modifier la balise**.

3. L’Assistant stratégie s’ouvre dans une **balise de modification** . Cliquez sur **suivant** pour passer en revue et modifier les paramètres.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

## <a name="use-the-security-center-to-remove-user-tags"></a>Utiliser le centre de sécurité pour supprimer des balises utilisateur

**Remarque**: vous ne pouvez pas supprimer la balise de **compte de priorité** intégrée.

1. Dans le centre de sécurité, accédez  aux \> **balises utilisateur** de gestion des menaces.

2. Sur la page **balises utilisateur** qui s’ouvre, sélectionnez la balise utilisateur que vous souhaitez supprimer, cliquez sur **Supprimer la balise**, puis sélectionnez **Oui, supprimer** dans l’avertissement qui s’affiche.
