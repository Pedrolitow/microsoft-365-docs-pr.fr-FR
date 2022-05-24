---
title: Balises utilisateur dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 12/17/2021
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Les administrateurs peuvent apprendre à identifier des groupes spécifiques d’utilisateurs avec des balises utilisateur dans Microsoft Defender pour Office 365 Plan 2. Le filtrage des balises est disponible dans les alertes, les rapports et les enquêtes dans Microsoft Defender pour Office 365 pour identifier rapidement les utilisateurs marqués.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3d4f5b82e09c9a58e891fa6fcba009ac490c0cb1
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647466"
---
# <a name="user-tags-in-microsoft-defender-for-office-365"></a>Balises utilisateur dans Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les balises utilisateur sont des identificateurs pour des groupes spécifiques d’utilisateurs dans [Microsoft Defender pour Office 365](defender-for-office-365.md). Il existe deux types de balises utilisateur :

- **Balises système** : actuellement, les [comptes Priority](../../admin/setup/priority-accounts.md) sont le seul type de balise système.
- **Balises personnalisées** : vous créez ces balises utilisateur vous-même.

Si votre organisation a Defender pour Office 365 plan 2 (inclus dans votre abonnement ou en tant que module complémentaire), vous pouvez créer des balises utilisateur personnalisées en plus de l’utilisation de la balise de comptes de priorité.

> [!NOTE]
> Actuellement, vous pouvez uniquement appliquer des balises utilisateur aux utilisateurs de boîte aux lettres.

Après avoir appliqué des balises système ou personnalisées aux utilisateurs, vous pouvez les utiliser comme filtres dans les alertes, les rapports et les enquêtes :

- [Alertes](alerts.md)
- [Stratégies d’alerte personnalisées](../../compliance/alert-policies.md#viewing-alerts)
- [Explorateur de menaces et détections en temps réel](threat-explorer.md)
- [Rapport utilisateur compromis](view-email-security-reports.md#compromised-users-report)
- [Page de l’entité d’e-mail](mdo-email-entity-page.md#other-innovations)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Rapport des principaux expéditeurs et destinataires](view-email-security-reports.md#top-senders-and-recipients-report)
- [Simulation d’attaque](attack-simulation-training.md#target-users)
- [Vues de campagne](campaigns.md)
- [Administration et soumissions d’utilisateurs](admin-submission.md)
- [Mise en quarantaine](quarantine.md)
- Pour les comptes prioritaires, vous pouvez utiliser les [problèmes de messagerie pour le rapport des comptes prioritaires](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report) dans le centre d’administration Exchange (EAC).

Cet article explique comment configurer des balises utilisateur dans le portail Microsoft 365 Defender. Il n’existe aucune applet de commande dans Microsoft 365 Defender portail pour gérer les balises utilisateur.

Pour voir comment les balises utilisateur font partie de la stratégie visant à protéger les comptes d’utilisateur à fort impact, consultez [les recommandations de sécurité pour les comptes prioritaires dans Microsoft 365](security-recommendations-for-priority-accounts.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Balises utilisateur** , utilisez <https://security.microsoft.com/securitysettings/userTags>.

- Vous devez disposer d’autorisations dans le portail Microsoft 365 Defender avant de pouvoir effectuer les procédures décrites dans cet article :
  - Pour créer, modifier et supprimer des balises utilisateur personnalisées, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité** .
  - Pour ajouter et supprimer des membres de la balise système de compte prioritaire, vous devez être membre de **l’administrateur de sécurité** et **Exchange Administration** groupes de rôles.
  - Pour ajouter et supprimer des membres de balises utilisateur personnalisées existantes, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité** .
  - Pour accéder en lecture seule aux balises utilisateur, vous devez être membre des groupes de **rôles Lecteur général**, **Opérateur de sécurité** ou **Lecteur de sécurité** .

  Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle de Azure Active Directory correspondant dans le Centre d'administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le portail Microsoft 365 Defender _et_ les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  >
  > - La gestion des balises utilisateur est contrôlée par les rôles **Lecteur** de balises et **Gestionnaire de balises** .

- Vous pouvez également gérer et surveiller les comptes prioritaires dans le Centre d'administration Microsoft 365. Pour obtenir des instructions, consultez [Gérer et surveiller les comptes prioritaires](../../admin/setup/priority-accounts.md).

- Pour plus d’informations sur la sécurisation des _comptes privilégiés_ (comptes d’administrateur), consultez [cette rubrique](/azure/architecture/framework/security/critical-impact-accounts).

## <a name="use-the-microsoft-365-defender-portal-to-create-user-tags"></a>Utiliser le portail Microsoft 365 Defender pour créer des balises utilisateur

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Paramètres** \> **balises utilisateur e-mail & collaboration**\>. Pour accéder directement à la page **Balises utilisateur** , utilisez <https://security.microsoft.com/securitysettings/userTags>.

2. Dans la page **Balises utilisateur** , cliquez sur ![l’icône Créer une balise.](../../media/m365-cc-sc-create-icon.png) **Créer une balise**.

3. L’Assistant **Création d’une balise** s’ouvre dans un nouveau menu volant. Dans la page **Définir la balise** , configurez les paramètres suivants :
   - **Nom** : entrez un nom descriptif unique pour la balise. Il s’agit de la valeur que vous verrez et utiliserez. Notez que vous ne pouvez pas renommer une balise après l’avoir créée.
   - **Description** : entrez une description facultative pour la balise.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Affecter des membres** , effectuez l’une des étapes suivantes :
   - Cliquez sur l’icône ![Ajouter des membres.](../../media/m365-cc-sc-create-icon.png) **Ajoutez des membres**. Dans le menu volant qui s’affiche, effectuez l’une des étapes suivantes pour ajouter des utilisateurs ou des groupes individuels :
     - Cliquez dans la zone et faites défiler la liste pour sélectionner un utilisateur ou un groupe.
     - Cliquez dans la zone et commencez à taper pour filtrer la liste, puis sélectionnez un utilisateur ou un groupe.
     - Pour ajouter des valeurs supplémentaires, cliquez dans une zone vide dans la zone.
     - Pour supprimer des entrées individuelles, cliquez sur ![Icône Supprimer l’entrée.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de l’entrée dans la zone.
     - Pour supprimer toutes les entrées, cliquez sur ![l’icône Supprimer l’entrée.](../../media/m365-cc-sc-remove-selection-icon.png) sur l’élément **Utilisateurs nn sélectionnés et groupes nn** sous la zone.

     Lorsque vous avez terminé, cliquez sur **Ajouter**.

     De retour sur la page **Attribuer des membres** , vous pouvez également supprimer des entrées en cliquant sur l’icône ![Supprimer.](../../media/m365-cc-sc-delete-icon.png) en regard de l’entrée.

   - Cliquez sur **Importer** pour sélectionner un fichier texte qui contient les adresses e-mail des utilisateurs ou des groupes. Assurez-vous que le fichier texte contient une entrée par ligne.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Révision de balise** qui s’affiche, passez en revue vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**, puis sur **Terminé**.

## <a name="use-the-microsoft-365-defender-portal-to-view-user-tags"></a>Utiliser le portail Microsoft 365 Defender pour afficher les balises utilisateur

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Paramètres** \> **balises utilisateur e-mail & collaboration**\>. Pour accéder directement à la page **Balises utilisateur** , utilisez <https://security.microsoft.com/securitysettings/userTags>.

2. Dans la page **Balises utilisateur** , les propriétés suivantes sont affichées dans la liste des balises utilisateur :

   - **Balise** : nom de la balise utilisateur. Notez que cela inclut la balise système de **compte Priority** intégrée.
   - **Appliqué à** : Nombre de membres
   - **Dernière modification**
   - **Créé le**

3. Lorsque vous sélectionnez une balise utilisateur en cliquant sur le nom, les détails s’affichent dans un menu volant.

## <a name="use-the-microsoft-365-defender-portal-to-modify-user-tags"></a>Utiliser le portail Microsoft 365 Defender pour modifier les balises utilisateur

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Paramètres** \> **balises utilisateur e-mail & collaboration**\>. Pour accéder directement à la page **Balises utilisateur** , utilisez <https://security.microsoft.com/securitysettings/userTags>.

2. Dans la page **Balises utilisateur** , sélectionnez la balise utilisateur dans la liste, puis cliquez sur ![l’icône Modifier la balise.](../../media/m365-cc-sc-edit-icon.png) **Modifier la balise**.

3. Dans le menu volant d’informations qui s’affiche, le même Assistant et les mêmes paramètres sont disponibles comme décrit dans [la section Utiliser le portail Microsoft 365 Defender pour créer des balises utilisateur](#use-the-microsoft-365-defender-portal-to-create-user-tags) plus haut dans cet article.

   **Remarques** :

   - La page **Définir une balise** n’est pas disponible pour la balise système de **compte Priority** intégrée. Vous ne pouvez donc pas renommer cette balise ou modifier la description.
   - Vous ne pouvez pas renommer une balise personnalisée, mais vous pouvez modifier la description.

## <a name="use-the-microsoft-365-defender-portal-to-remove-user-tags"></a>Utiliser le portail Microsoft 365 Defender pour supprimer les balises utilisateur

> [!NOTE]
> Vous ne pouvez pas supprimer la balise système de **compte Priority** intégrée.

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Paramètres** \> **balises utilisateur e-mail & collaboration**\>. Pour accéder directement à la page **Balises utilisateur** , utilisez <https://security.microsoft.com/securitysettings/userTags>.

2. Dans la page **Balises utilisateur** , sélectionnez la balise utilisateur dans la liste, puis cliquez sur ![l’icône Supprimer la balise.](../../media/m365-cc-sc-delete-icon.png) **Supprimer la balise**.

3. Lisez l’avertissement dans la boîte de dialogue de confirmation qui s’affiche, puis cliquez sur **Oui, supprimer**.

## <a name="more-information"></a>Informations supplémentaires

[Configurer et passer en revue les comptes prioritaires dans Microsoft Defender pour Office 365](configure-review-priority-account.md)
