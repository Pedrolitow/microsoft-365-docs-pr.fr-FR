---
title: Balises utilisateur dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom:
- admindeeplinkDEFENDER
- admindeeplinkEXCHANGE
description: Les administrateurs peuvent apprendre à identifier des groupes spécifiques d’utilisateurs à l’aide de balises utilisateur dans Microsoft Defender Office 365 Plan 2. Le filtrage des balises est disponible pour les alertes, les rapports et les enquêtes dans Microsoft Defender Office 365 pour identifier rapidement les utilisateurs marqués.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a3472a7625082e21d88e01db12cd5d8d14f86c27
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2021
ms.locfileid: "61422746"
---
# <a name="user-tags-in-microsoft-defender-for-office-365"></a>Balises utilisateur dans Microsoft Defender pour Office 365

> [!NOTE]
> La fonctionnalité de balises utilisateur est en prévisualisation, n’est pas disponible pour tout le monde et peut faire l’objet de changements. Pour plus d’informations sur la planification de publication, consultez la [feuille de Microsoft 365 de publication.](https://www.microsoft.com/microsoft-365/roadmap)

Les balises utilisateur sont des identificateurs pour des groupes spécifiques d’utilisateurs [dans Microsoft Defender Office 365](defender-for-office-365.md). Il existe deux types de balises utilisateur :

- **Balises système**: actuellement, [les comptes de priorité](../../admin/setup/priority-accounts.md) sont le seul type de balise système.
- **Balises personnalisées**: vous créez ces balises utilisateur vous-même.

Si votre organisation dispose de Defender pour Office 365 Plan 2 (inclus dans votre abonnement ou en tant qu’complément), vous pouvez créer des balises utilisateur personnalisées en plus de l’utilisation de la balise de comptes prioritaires.

> [!NOTE]
> Actuellement, vous pouvez uniquement appliquer des balises utilisateur aux utilisateurs de boîtes aux lettres.

Après avoir appliqué des balises système ou des balises personnalisées aux utilisateurs, vous pouvez les utiliser comme filtres dans les alertes, les rapports et les enquêtes :

- [Alertes](alerts.md)
- [Stratégies d’alerte personnalisées](../../compliance/alert-policies.md#viewing-alerts)
- [Détections en temps réel et de l’Explorateur de menaces](threat-explorer.md)
- [Page de l’entité d’e-mail](mdo-email-entity-page.md#other-innovations)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Vues de campagne](campaigns.md)
- [Soumissions d’administrateurs et d’utilisateurs](admin-submission.md)
- Pour les comptes prioritaires, [](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report) vous pouvez utiliser le rapport Problèmes de messagerie pour les comptes prioritaires dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d Exchange’administration.</a>

Cet article explique comment configurer des balises utilisateur dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender.</a> Il n’existe aucune cmdlet dans Microsoft 365 Defender portail pour gérer les balises utilisateur.

Pour voir comment les balises utilisateur font partie de la stratégie visant à protéger les comptes d’utilisateur à fort impact, consultez [recommandations](security-recommendations-for-priority-accounts.md)en matière de sécurité pour les comptes prioritaires dans Microsoft 365 .

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le portail Microsoft 365 Defender sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com/</a>. Pour aller directement à la page **des balises utilisateur,** ouvrez <https://security.microsoft.com/securitysettings/userTags> .

- Des autorisations doivent vous être attribuées dans le portail Microsoft 365 Defender avant de pouvoir suivre les procédures de cet article :
  - Pour créer, modifier et supprimer des balises utilisateur,  vous devez être membre des groupes de rôles Gestion de l’organisation ou **Administrateur de** la sécurité.
  - Pour ajouter et supprimer des membres de balises utilisateur existantes, vous devez  être membre des groupes de rôles Gestion de l’organisation, Administrateur de la sécurité ou Opérateur de sécurité
  - Pour accéder en lecture seule aux balises utilisateur,  vous devez être membre des groupes de rôles Lecteur global ou **Lecteur de** sécurité.

  Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d'administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le portail Microsoft 365 Defender et les autorisations pour d’autres fonctionnalités dans  Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  >
  > - La gestion des balises utilisateur est contrôlée par les **rôles Lecteur de balises** et **Gestionnaire de balises.**

- Vous pouvez également gérer et surveiller les comptes prioritaires dans le Centre d'administration Microsoft 365. Pour obtenir des instructions, voir [Gérer et surveiller les comptes prioritaires.](../../admin/setup/priority-accounts.md)

- Pour plus d’informations _sur la sécurisation des_ comptes privilégiés (comptes d’administrateur), consultez cette [rubrique.](/azure/architecture/framework/security/critical-impact-accounts)

## <a name="use-the-microsoft-365-defender-portal-to-create-user-tags"></a>Utiliser le portail Microsoft 365 Defender pour créer des balises utilisateur

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender,</a>go to **Paramètres** \> **Email & collaboration** User \> **tags**.

2. Dans la page **Balises utilisateur,** cliquez sur ![ Créer une icône de balise.](../../media/m365-cc-sc-create-icon.png) **Créer une balise**.

3. **L’Assistant Créer** une balise s’ouvre dans un nouveau volant. Dans la page **Définir la balise,** configurez les paramètres suivants :
   - **Nom**: entrez un nom unique et descriptif pour la balise. Il s’agit de la valeur que vous verrez et utiliserez. Notez que vous ne pouvez pas renommer une balise après l’avoir créé.
   - **Description**: entrez une description facultative de la balise.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Affecter des membres,** faites l’une des étapes suivantes :
   - Cliquez sur ![ Icône Ajouter des membres.](../../media/m365-cc-sc-create-icon.png) **Ajouter des membres**. Dans le volant qui s’affiche, faites l’une des étapes suivantes pour ajouter des utilisateurs individuels ou des groupes :
     - Cliquez dans la zone et faites défiler la liste pour sélectionner un utilisateur ou un groupe.
     - Cliquez dans la zone et commencez à taper pour filtrer la liste et sélectionner un utilisateur ou un groupe.
     - Pour ajouter des valeurs supplémentaires, cliquez dans une zone vide dans la zone.
     - Pour supprimer des entrées individuelles, cliquez sur ![Supprimer l’icône d’entrée.](../../media/m365-cc-sc-remove-selection-icon.png) à côté de l’entrée dans la zone.
     - Pour supprimer toutes les entrées, cliquez sur ![ Icône Supprimer l’entrée.](../../media/m365-cc-sc-remove-selection-icon.png) sur **l’élément Utilisateurs et** groupes nn sélectionnés sous la zone.

     Lorsque vous avez terminé, cliquez sur **Ajouter**.

     De retour sur la page **Affecter des** membres, vous pouvez également supprimer des entrées en cliquant sur ![ l’icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) à côté de l’entrée.

   - Cliquez **sur Importer** pour sélectionner un fichier texte qui contient les adresses de messagerie des utilisateurs ou des groupes. Assurez-vous que le fichier texte contient une entrée par ligne.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **de balise Révision** qui s’affiche, examinez vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer,** puis sur **Terminé.**

## <a name="use-the-microsoft-365-defender-portal-to-view-user-tags"></a>Utiliser le portail Microsoft 365 Defender pour afficher les balises utilisateur

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender,</a>go to **Paramètres** \> **Email & collaboration** User \> **tags**.

2. Dans la page **Balises utilisateur,** les propriétés suivantes sont affichées dans la liste des balises utilisateur :

   - **Balise**: nom de la balise utilisateur. Notez que cela inclut la balise système **de** compte Priorité intégrée.
   - **Appliqué à**: nombre de membres
   - **Dernière modification**
   - **Créé le**

3. Lorsque vous sélectionnez une balise utilisateur en cliquant sur le nom, les détails sont affichés dans un volant.

## <a name="use-the-microsoft-365-defender-portal-to-modify-user-tags"></a>Utiliser le portail Microsoft 365 Defender pour modifier les balises utilisateur

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender,</a>go to **Paramètres** \> **Email & collaboration** User \> **tags**.

2. Dans la page **Balises utilisateur,** sélectionnez la balise utilisateur dans la liste, puis cliquez sur Modifier ![ l’icône de balise.](../../media/m365-cc-sc-edit-icon.png) **Modifier la balise**.

3. Dans le volet d’informations qui s’affiche, le même Assistant et les mêmes paramètres sont disponibles comme décrit dans la section Utiliser le portail [Microsoft 365 Defender](#use-the-microsoft-365-defender-portal-to-create-user-tags) pour créer des balises utilisateur plus tôt dans cet article.

   **Remarques** :

   - La **page Définir la** balise n’est pas disponible pour la balise système de compte priorité intégrée, vous ne pouvez donc pas renommer cette balise ou modifier la description. 
   - Vous ne pouvez pas renommer une balise personnalisée, mais vous pouvez modifier la description.

## <a name="use-the-microsoft-365-defender-portal-to-remove-user-tags"></a>Utiliser le portail Microsoft 365 Defender pour supprimer des balises utilisateur

> [!NOTE]
> Vous ne pouvez pas supprimer la balise système de compte **Priorité** intégrée.

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender,</a>go to **Paramètres** \> **Email & collaboration** User \> **tags**.

2. Dans la page **Balises utilisateur,** sélectionnez la balise utilisateur dans la liste, puis cliquez sur Supprimer ![ l’icône de balise.](../../media/m365-cc-sc-delete-icon.png) **Supprimer une balise**.

3. Lisez l’avertissement dans la boîte de dialogue de confirmation qui s’affiche, puis cliquez sur **Oui, supprimer.**
