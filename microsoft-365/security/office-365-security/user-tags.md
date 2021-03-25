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
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à identifier des groupes spécifiques d’utilisateurs à l’aide de balises utilisateur dans Microsoft Defender pour Office 365 Plan 2. Le filtrage des balises est disponible dans les alertes, les rapports et les enquêtes dans Microsoft Defender pour Office 365 pour identifier rapidement les utilisateurs marqués.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6f98dcfe3e8c44e852134e7a12def4ff78c1bcdd
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204515"
---
# <a name="user-tags-in-microsoft-defender-for-office-365"></a>Balises utilisateur dans Microsoft Defender pour Office 365

> [!NOTE]
> La fonctionnalité de balises utilisateur est en prévisualisation, n’est pas disponible pour tout le monde et peut faire l’objet de changements. Pour plus d’informations sur la planification de publication, consultez la feuille [de route Microsoft 365.](https://www.microsoft.com/microsoft-365/roadmap)

Les balises utilisateur sont des identificateurs pour des groupes spécifiques d’utilisateurs [dans Microsoft Defender pour Office 365.](defender-for-office-365.md) Il existe deux types de balises utilisateur :

- **Balises système**: actuellement, [les comptes de priorité](../../admin/setup/priority-accounts.md) sont le seul type de balise système.
- **Balises personnalisées**: vous créez ces balises utilisateur vous-même.

Si votre organisation dispose de Defender pour Office 365 Plan 2 (inclus dans votre abonnement ou en tant qu’complément), vous pouvez créer des balises utilisateur personnalisées en plus de l’utilisation de la balise de comptes prioritaires.

Après avoir appliqué des balises système ou des balises personnalisées aux utilisateurs, vous pouvez les utiliser comme filtres dans les alertes, les rapports et les enquêtes :

- [Alertes dans le Centre de sécurité & conformité](alerts.md)
- [Détections en temps réel et de l’Explorateur de menaces](threat-explorer.md)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Vues de campagne](campaigns.md)
- Pour les comptes prioritaires, [](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report) vous pouvez utiliser le rapport Problèmes de messagerie pour les comptes prioritaires dans le Centre d’administration Exchange (EAC).

Cet article explique comment configurer des balises utilisateur dans le Centre de sécurité & conformité. Il n’existe aucune cmdlet dans le Centre de sécurité & conformité pour gérer les balises utilisateur.

Pour voir comment les balises utilisateur font partie de la stratégie visant à protéger les comptes d’utilisateur à fort impact, voir recommandations en matière de sécurité pour les comptes prioritaires dans [Microsoft 365.](security-recommendations-for-priority-accounts.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour aller directement à la page **des balises utilisateur,** ouvrez <https://protection.office.com/userTags> .

- Pour pouvoir utiliser ce cmdlet, vous devez disposer des autorisations dans le centre de sécurité et conformité Office 365.
  - Pour créer, modifier et supprimer des balises utilisateur,  vous devez être membre des groupes de rôles Gestion de l’organisation ou **Administrateur** de la sécurité.
  - Pour ajouter et supprimer des membres de balises utilisateur existantes, vous devez  être membre des groupes de rôles Gestion de l’organisation, Administrateur de la sécurité ou Opérateur de sécurité
  - Pour accéder en lecture seule aux balises utilisateur,  vous devez être membre des groupes de rôles Lecteur global ou **Lecteur** de sécurité.

  Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le centre de sécurité et de conformité _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  - La gestion des balises utilisateur est contrôlée par les **rôles Lecteur de balises** et **Gestionnaire de balises.**

- Vous pouvez également gérer et surveiller les comptes prioritaires dans le Centre d’administration Microsoft 365. Pour obtenir des instructions, voir [Gérer et surveiller les comptes prioritaires.](../../admin/setup/priority-accounts.md)

## <a name="use-the-security--compliance-center-to-create-user-tags"></a>Utiliser le Centre de sécurité & conformité pour créer des balises utilisateur

1. Dans le Centre de sécurité & conformité, allez aux **balises utilisateur de gestion** \> **des menaces.**

2. Dans la page **Balises utilisateur** qui s’ouvre, cliquez **sur Créer une balise.**

3. **L’Assistant Création** d’une balise s’ouvre dans un nouveau volant. Dans la page **Définir la balise,** configurez les paramètres suivants :
   - **Nom**: entrez un nom unique et descriptif pour la balise. Il s’agit de la valeur que vous verrez et utiliserez.
   - **Description**: entrez une description facultative de la balise.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Affecter des** utilisateurs, faites l’une des étapes suivantes :

   - Cliquez **sur Ajouter des utilisateurs.** Dans le volant qui s’affiche, faites l’une des étapes suivantes pour ajouter des utilisateurs individuels ou des groupes :
     - Cliquez dans la zone et faites défiler la liste pour sélectionner un utilisateur ou un groupe.
     - Cliquez dans la zone et commencez à taper pour filtrer la liste et sélectionner un utilisateur ou un groupe.
     - Pour ajouter des valeurs supplémentaires, cliquez dans une zone vide dans la zone.
     - Pour supprimer des entrées individuelles de la zone, cliquez sur **Supprimer** l’icône sur l’utilisateur ou ![ le groupe dans la ](../../media/scc-remove-icon.png) zone.
     - Pour supprimer des entrées existantes de la liste sous la zone, cliquez sur **Supprimer** ![ l’icône ](../../media/scc-remove-icon.png) Supprimer l’entrée.

     Lorsque vous avez terminé, cliquez sur **Ajouter**.

   - Cliquez **sur Importer** pour sélectionner un fichier texte qui contient les adresses de messagerie des utilisateurs ou des groupes. Assurez-vous que le fichier texte contient une entrée par ligne.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **De révision,** examinez vos paramètres. Vous pouvez cliquer **sur Modifier** dans la section spécifique pour apporter des modifications.

   Lorsque vous avez terminé, cliquez sur **Envoyer.**

## <a name="use-the-security--compliance-center-to-view-user-tags"></a>Utiliser le Centre de sécurité & conformité pour afficher les balises utilisateur

1. Dans le Centre de sécurité & conformité, allez aux **balises utilisateur de gestion** \> **des menaces.**

2. Dans la page **Balises utilisateur** qui s’ouvre, sélectionnez la balise utilisateur à afficher (ne cliquez pas sur la case à cocher).

3. Dans la liste des détails en lecture seule qui s’affiche, examinez les paramètres.

   Lorsque vous avez terminé, cliquez sur **Fermer**.

## <a name="use-the-security--compliance-center-to-modify-user-tags"></a>Utiliser le Centre de sécurité & conformité pour modifier les balises utilisateur

1. Dans le Centre de sécurité & conformité, allez aux **balises utilisateur de gestion** \> **des menaces.**

2. Dans la page **Balises utilisateur** qui s’ouvre, sélectionnez la balise utilisateur à afficher, puis cliquez sur **Modifier la balise**.

3. L’Assistant Stratégie s’ouvre dans un **volant de balise Modifier.** Cliquez **sur Suivant** pour passer en revue et modifier les paramètres.

   Lorsque vous avez terminé, cliquez sur **Envoyer.**

## <a name="use-the-security--compliance-center-to-remove-user-tags"></a>Utiliser le Centre de sécurité & conformité pour supprimer des balises utilisateur

**Remarque**: vous ne pouvez pas supprimer la balise de compte **Priority** intégrée.

1. Dans le Centre de sécurité & conformité, allez aux **balises utilisateur de gestion** \> **des menaces.**

2. Dans **la** page Balises utilisateur qui s’ouvre, sélectionnez la balise utilisateur à supprimer, cliquez sur Supprimer la **balise,** puis sélectionnez **Oui,** supprimez l’avertissement qui s’affiche.