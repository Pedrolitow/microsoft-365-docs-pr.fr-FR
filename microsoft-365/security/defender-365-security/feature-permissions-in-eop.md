---
title: Autorisations des fonctionnalités dans EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.assetid: 34674847-a6b7-4a7e-9eaa-b64f22bc150d
description: En savoir plus sur l’autorisation requise pour les tâches dans Exchange Online Protection autonome
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 212a109c792522270b7e5000747bec950b7f4fe2
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51063398"
---
# <a name="permissions-in-standalone-eop"></a>Autorisations dans EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
-  [Exchange Online Protection autonome](exchange-online-protection-overview.md)

Exchange Online Protection (EOP) autonome sans boîtes aux lettres Exchange Online utilise le modèle d’autorisations de contrôle d’accès basé sur un rôle (RBAC) pour accorder facilement des autorisations à vos administrateurs. Vous pouvez utiliser les fonctionnalités d’autorisation dans EOP autonome pour que votre nouvelle organisation soit rapidement opérationnel.

Pour accorder des autorisations aux utilisateurs, voir Gérer les groupes de [rôles d’administrateur dans EOP.](manage-admin-role-group-permissions-in-eop.md)

Pour plus d’informations sur les autorisations dans Microsoft 365, voir [à propos des rôles d’administrateur.](../../admin/add-users/about-admin-roles.md)

## <a name="role-based-permissions"></a>Autorisations basées sur des rôles

Les autorisations d’administrateur que vous accordez aux utilisateurs sont basées sur les rôles de gestion. Un rôle de gestion définit les cmdlets disponibles pour un ensemble de tâches données. Étant donné que le Centre d’administration Exchange (CAE) et EOP Autonome PowerShell utilisent des cmdlets, l’accès à une cmdlet donne à l’utilisateur l’autorisation d’effectuer les tâches connexes dans le CAE ou dans EOP PowerShell autonome. Par exemple, le rôle Destinataires de courrier définit les cmdlets qui sont requises pour modifier les utilisateurs de messagerie.

Dans EOP autonome, les rôles d’administration sont le seul type de rôle de gestion disponible (il n’existe aucun rôle d’utilisateur final ou stratégie d’attribution de rôle).

## <a name="role-groups"></a>Groupes de rôles

Pour faciliter l’attribution de rôles aux utilisateurs, EOP autonome utilise des groupes de rôles. Les rôles de gestion sont attribués à des groupes de rôles et les membres du groupe de rôles obtiennent les autorisations associées aux rôles. En d’autres termes, les rôles de gestion ne sont pas directement attribués aux utilisateurs ; Ils sont affectés au groupe de rôles. Ce modèle vous permet d’attribuer plusieurs rôles à plusieurs membres du groupe de rôles à la fois. Les membres du groupe de rôles peuvent être des utilisateurs de messagerie, des groupes de sécurité à messagerie, des utilisateurs du Centre d’administration Microsoft 365 et d’autres groupes de rôles.

La figure suivante montre la relation entre les utilisateurs, les groupes de rôles et les rôles.

![Relations des rôles, des groupes de rôles et des membres](../../media/ITPro_Security_RBAC_EXO_SimplifiedRoleGroupRelationship.png)

Les groupes de rôles disponibles dans EOP autonome sont décrits dans le tableau suivant.

****

|Groupe de rôles|Description|Rôles par défaut attribués|
|---|---|---|
|ComplianceManagement|Configurez et gérez les paramètres de conformité au sein de l’organisation, y compris la protection contre la perte de données (DLP) si votre abonnement dispose de fonctionnalités DLP. <p> Les membres du [rôle Administrateur de](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#compliance-administrator) conformité dans Azure AD obtiennent automatiquement les autorisations de ce groupe de rôles.|Journaux d’audit <p> Administration de la conformité <p> Gestion des droits relatifs à l’information <p> Gestion de la rétention <p> Journaux d'audit en affichage seul <p> Afficher uniquement la configuration <p> Afficher uniquement les destinataires|
|ContentExplorerContentViewer|Non utilisé.|Visionneuse de contenu de classification des données|
|ContentExplorerListViewer|Non utilisé.|Visionneuse de listes de classification des données|
|HelpDesk|Afficher et gérer les utilisateurs de messagerie.|Réinitialiser le mot de passe <p> Options utilisateur <p> Afficher uniquement les destinataires|
|HygieneManagement|Gérer les fonctionnalités de protection (anti-courrier indésirable, anti-programme malveillant, etc.).|Hygiène de transport <p> Afficher uniquement la configuration <p> Afficher uniquement les destinataires|
|MailFlowAdministrator|Afficher et gérer les domaines et connecteurs acceptés|Domaines distants et acceptés <p> Afficher uniquement les destinataires|
|OrganizationManagement|Accès administrateur à l’ensemble de l’organisation et possibilité d’effectuer presque n’importe quelle tâche. <p> Les membres du [rôle Administrateur général](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#global-administrator--company-administrator) dans Azure AD obtiennent automatiquement les autorisations de ce groupe de rôles. <p> **Important**: étant donné que le groupe de rôles OrganizationManagement est un rôle puissant, seuls les utilisateurs qui effectuent des tâches administratives au niveau de l’organisation doivent être membres de ce groupe de rôles.|AntiMalware <p> AntiSpam <p> Journaux d’audit <p> Administrateur de conformité <p> Groupes de distribution dynamique <p> Gestion des droits relatifs à l’information <p> Création de destinataires de message <p> Destinataires de message <p> Suivi de messages <p> Migration <p> Accès au client de l’organisation <p> Configuration de l’organisation <p> Paramètres de transport de l’organisation <p> Quarantaine <p> Stratégies de destinataire <p> Domaines distants et acceptés <p> Réinitialiser le mot de passe <p> Gestion de la rétention <p> Gestion des rôles <p> Administrateur de sécurité <p> Création et appartenance à un groupe de sécurité <p> Lecteur de sécurité <p> Administrateur d’étiquette de niveau de sensibilité <p> Surveillance <p> Hygiène de transport <p> Règles de transport <p> Options utilisateur <p> View-Only anti-programme malveillant <p> View-Only AntiSpam <p> Journaux d'audit en affichage seul <p> Afficher uniquement la configuration <p> View-Only quarantaine <p> Afficher uniquement les destinataires <p> View-Only Threat Intelligence|
|QuarantineAdministrator|Gérer les messages mis en quarantaine pour tous les destinataires.|Quarantaine|
|RecipientManagement|Créer, gérer et supprimer des objets destinataire dans l’organisation.|Groupes de distribution dynamique <p> Création de destinataires de message <p> Destinataires de message <p> Suivi de messages <p> Migration <p> Stratégies de destinataire <p> Réinitialiser le mot de passe|
|RecordsManagement|Configurer les fonctionnalités de conformité, telles que les balises de stratégie de rétention, les classifications des messages et les règles de flux de messagerie (également appelées règles de transport).|Suivi de messages <p> Gestion de la rétention <p> Règles de transport|
|SecurityAdministrator|Configurez tous les aspects de la protection dans l’organisation (anti-courrier indésirable, anti-programme malveillant, anti-usurpation d’adresse, mise en quarantaine, etc.). <p> Les membres du [rôle Administrateur de](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#security-administrator) la sécurité dans Azure AD obtiennent automatiquement les autorisations de ce groupe de rôles.|AntiMalware <p> AntiSpam <p> Journaux d’audit <p> Quarantaine <p> Administrateur de sécurité <p> Administrateur d’étiquette de niveau de sensibilité <p> View-Only anti-programme malveillant <p> View-Only AntiSpam <p> Journaux d'audit en affichage seul <p> View-Only quarantaine <p> View-Only Threat Intelligence|
|SecurityReader|Accès en affichage seul à tous les aspects de la protection de l’organisation (anti-courrier indésirable, anti-programme malveillant, détection d’usurpation d’adresse, mise en quarantaine, etc.). <p> Les membres du [rôle Lecteur de](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#security-reader) sécurité dans Azure AD obtiennent automatiquement les autorisations de ce groupe de rôles.|Lecteur de sécurité <p> View-Only anti-programme malveillant <p> View-Only AntiSpam <p> View-Only quarantaine <p> View-Only Threat Intelligence|
|TenantAdmins|L’appartenance à ce groupe de rôles est synchronisée entre les services et gérée de manière centralisée. Par défaut, aucun rôle n’est attribué à ce groupe de rôles. Toutefois, il sera membre du groupe de rôles Gestion de l’organisation et héritera de ces autorisations.|aucune|
|ViewOnlyOrganizationManagement|Afficher les objets destinataire, protection et configuration et leurs propriétés dans l’organisation.|Administrateur de conformité <p> Administrateur de sécurité <p> Lecteur de sécurité <p> Administrateur d’étiquette de niveau de sensibilité <p> Afficher uniquement la configuration <p> Afficher uniquement les destinataires|
|

Si vous travaillez dans une petite organisation qui ne compte que quelques administrateurs, vous devrez peut-être ajouter ces utilisateurs au groupe de rôles Gestion de l’organisation uniquement et vous n’aurez peut-être jamais besoin d’utiliser les autres groupes de rôles. Si vous travaillez dans une organisation de grande taille, vous pouvez avoir des administrateurs qui effectuent des tâches spécifiques, telles que la configuration du destinataire. Dans ce cas, vous pouvez ajouter un administrateur au groupe de rôles Gestion des destinataires et un autre administrateur au groupe de rôles Gestion de l’organisation. Ces administrateurs peuvent alors gérer leurs domaines spécifiques, mais ils ne sont pas autorisés à gérer les domaines dont ils ne sont pas responsables.

Si les groupes de rôles intégrés dans Exchange Online ne correspondent pas à la fonction de vos administrateurs, vous pouvez créer des groupes de rôles y ajouter des rôles. Pour plus d’informations, voir [Gérer les groupes de rôles dans EOP autonome.](manage-admin-role-group-permissions-in-eop.md)

## <a name="roles"></a>Rôles

Les rôles intégrés disponibles dans EOP autonome sont décrits dans le tableau suivant.

****

|Role**|Description|Attributions de groupe de rôles par défaut|
|---|---|---|
|AntiMalware|Afficher et modifier la configuration et les rapports pour les fonctionnalités anti-programme malveillant.|OrganizationManagement <p> SecurityAdministrator|
|AntiSpam|Afficher et modifier la configuration et les rapports pour les fonctionnalités anti-courrier indésirable.|OrganizationManagement <p> SecurityAdministrator|
|Journaux d’audit|Recherchez le journal d’audit de l’administrateur et affichez les résultats.|ComplianceManagement <p> OrganizationManagement <p> SecurityAdministrator|
|Administrateur de conformité<sup>\*</sup>||ComplianceManagement <p> OrganizationManagement <p> ViewOnlyOrganizationManagement|
|Visionneuse de contenu de classification des données<sup>\*</sup>||ContentExplorerContentViewer|
|Visionneuse de listes de classification des données<sup>\*</sup>||
|Groupes de distribution dynamique|Créer et gérer tous les groupes de distribution, les groupes de sécurité à messagerie et les membres.|OrganizationManagement <p> RecipientManagement|
|Gestion des droits de l’information<sup>\*</sup>||ComplianceManagement <p> OrganizationManagement|
|Création de destinataires de message|Créez et supprimez des utilisateurs de messagerie.|OrganizationManagement <p> RecipientManagement|
|Destinataires de message|Modifier les utilisateurs de messagerie existants.|OrganizationManagement <p> RecipientManagement|
|Suivi des messages<sup>\*</sup>||OrganizationManagement <p> RecipientManagement <p> Gestion des enregistrements|
|Migration<sup>\*</sup>||OrganizationManagement <p> RecipientManagement|
|MyBaseOptions|Permet aux utilisateurs d’afficher leurs propres messages mis en quarantaine. <p> Ce rôle est automatiquement attribué aux utilisateurs et vous ne pouvez pas l’attribuer manuellement.|aucune|
|Accès au client de l’organisation<sup>\*</sup>||OrganizationManagement|
|Configuration de l’organisation|Affichage des rapports.|OrganizationManagement|
|Paramètres de transport de l’organisation<sup>\*</sup>||OrganizationManagement|
|Quarantaine|Gérer tous les types de message mis en quarantaine pour tous les destinataires.|OrganizationManagement <p> QuarantineAdministrator <p> SecurityAdministrator|
|Stratégies de destinataire<sup>\*</sup>||OrganizationManagement <p> RecipientManagement|
|Domaines distants et acceptés|Gérer les domaines distants, les domaines acceptés et les connecteurs.|MailFlowAdministrator <p> OrganizationManagement|
|Réinitialiser le mot de passe<sup>\*</sup>||HelpDesk <p> OrganizationManagement <p> RecipientManagement|
|Gestion de la rétention<sup>\*</sup>||ComplianceManagement <p> OrganizationManagement <p> RecordsManagement|
|Gestion des rôles|Créer et gérer des groupes de rôles.|OrganizationManagement|
|Administrateur de sécurité|Gérez la configuration et les rapports pour toutes les fonctionnalités de sécurité et de protection.|OrganizationManagement <p> SecurityAdministrator <p> ViewOnlyOrganizationManagement|
|Création et appartenance à un groupe de sécurité|Créer et gérer des groupes de sécurité à messagerie.|OrganizationManagement|
|Lecteur de sécurité|Afficher la configuration et les rapports pour les fonctionnalités de sécurité et de protection.|Gestion de l’organisation <p> SecurityReader <p> ViewOnlyOrganizationManagement|
|Administrateur d’étiquette de niveau de sensibilité<sup>\*</sup>||OrganizationManagement <p> SecurityAdministrator <p> ViewOnlyOrganizationManagement|
|Supervision<sup>\*</sup>||OrganizationManagement|
|Hygiène de transport|Gérer les fonctionnalités anti-programme malveillant, anti-courrier indésirable et anti-usurpation.|HygieneManagement <p> OrganizationManagement|
|Règles de transport|Créer et gérer des règles de flux de messagerie (également appelées règles de transport).|OrganizationManagement <p> RecordsManagement|
|Options utilisateur|Modifier les utilisateurs de messagerie existants.|HelpDesk <p> OrganizationManagement|
|View-Only anti-programme malveillant|Afficher la configuration et les rapports pour les fonctionnalités anti-programme malveillant.|OrganizationManagement <p> SecurityAdministrator <p> SecurityReader|
|View-Only AntiSpam|Afficher la configuration et les rapports pour les fonctionnalités anti-courrier indésirable.|OrganizationManagement <p> SecurityAdministrator <p> SecurityReader|
|Journaux d'audit en affichage seul|Recherchez le journal d’audit de l’administrateur et affichez les résultats.|ComplianceManagement <p> OrganizationManagement <p> SecurityAdministrator|
|Afficher uniquement la configuration|Afficher tous les paramètres d’organisation et de flux de messagerie (non destinataires) de l’organisation.|ComplianceManagement <p> HygieneManagement <p> OrganizationManagement <p> ViewOnlyOrganizationManagement|
|View-Only quarantaine|Afficher tous les messages mis en quarantaine pour tous les destinataires.|OrganizationManagement <p> SecurityAdministrator <p> SecurityReader|
|Afficher uniquement les destinataires|Afficher les propriétés du destinataire et exécuter le suivi des messages.|ComplianceManagement <p> HelpDesk <p> HygieneManagement <p> MailFlowAdministrator <p>  OrganizationManagement <p> ViewOnlyOrganizationManagement|
|View-Only Threat Intelligence<sup>\*</sup>||OrganizationManagement <p> SecurityAdministrator <p> SecurityReader|
|

<sup>\*</sup> Bien que ce rôle soit disponible, il n’a rien d’utile dans EOP autonome.

## <a name="microsoft-365-permissions-in-standalone-eop"></a>Autorisations Microsoft 365 dans EOP autonome

Lorsque vous créez un utilisateur dans le Centre d’administration Microsoft 365, vous pouvez choisir d’attribuer ou non différents rôles d’administrateur, tels que l’administrateur global, l’administrateur de service, l’administrateur de mot de passe, etc. à l’utilisateur. Certains rôles Microsoft 365, mais pas tous, accordent à l’utilisateur des autorisations d’administration dans EOP.

> [!NOTE]
> Le compte que vous avez utilisé pour créer votre organisation EOP autonome est automatiquement attribué au rôle d’administrateur global.

Le tableau suivant répertorie les rôles Microsoft 365 et les groupes de rôles EOP autonomes à qui ils correspondent. Pour plus d’informations sur ces rôles, voir [à propos des rôles d’administrateur.](../../admin/add-users/about-admin-roles.md)

****

|Rôle Microsoft 365|Groupe de rôles EOP|
|---|---|
|Administrateur Exchange|OrganizationManagement|
|Administrateur global|OrganizationManagement <p> **Remarque**: le rôle d’administrateur général et le groupe de rôles OrganizationManagement sont liés à l’aide d’un groupe de rôles d’administrateur d’entreprise spécial. Le groupe de rôles Administrateur d’entreprise est géré en interne et ne peut pas être modifié directement.|
|Administrateur de mots de passe|HelpDesk|
|Lecteur général|ViewOnlyOrganizationManagement|
|Administrateur de la sécurité|SecurityAdministrator|
|Lecteur Sécurité|SecurityReader|
|

Les autres rôles Microsoft 365 n’ont pas de groupe de rôles EOP correspondant et n’accordent pas d’autorisations administratives dans EOP. Pour plus d’informations sur l’attribution d’un rôle Microsoft 365 à un utilisateur, voir [Attribuer des rôles d’administrateur.](../../admin/add-users/assign-admin-roles.md)

Les utilisateurs peuvent se voir accorder des droits d’administration dans EOP sans les ajouter aux rôles Microsoft 365. Pour ce faire, ajoutez l’utilisateur en tant que membre d’un groupe de rôles EOP. L’utilisateur aura des autorisations dans EOP, mais il n’aura pas d’autorisations dans les autres charges de travail Microsoft 365.

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez correctement copié un groupe de rôles, faites l’une des étapes suivantes :

- Dans le EAC, allez à Rôles d’administrateur **des autorisations** et vérifiez que le groupe de rôles est répertorié \> (ou non répertorié). Sélectionnez le groupe de rôles et vérifiez les  paramètres dans le volet Détails ou cliquez sur Modifier l’icône ![ modifier pour vérifier les ](../../media/ITPro-EAC-EditIcon.png) paramètres.

- Dans Exchange Online PowerShell, remplacez par le nom du groupe de rôles, puis exécutez la commande suivante pour vérifier que le groupe de rôles existe (ou n’existe pas) et vérifier les \<Role Group Name\> paramètres :

  ```PowerShell
  Get-RoleGroup -Identity "<Role Group Name>" | Format-List
  ```