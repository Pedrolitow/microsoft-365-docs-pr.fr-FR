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
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 34674847-a6b7-4a7e-9eaa-b64f22bc150d
description: En savoir plus sur les autorisations requises pour les tâches dans Exchange Online protection autonome
ms.openlocfilehash: ae43dc2223b17d3b73f9b76fa6bde8fb9cb95e77
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48202866"
---
# <a name="permissions-in-standalone-eop"></a>Autorisations dans EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Autonome Exchange Online Protection (EOP) sans boîte aux lettres Exchange Online utilise le modèle d’autorisations de contrôle d’accès basé sur un rôle (RBAC) pour accorder facilement des autorisations à vos administrateurs. Vous pouvez utiliser les fonctionnalités d’autorisation de EOP autonome pour faire en sorte que votre nouvelle organisation s’exécute rapidement.

Pour accorder des autorisations aux utilisateurs, consultez la rubrique [gérer les groupes de rôles d’administrateur dans EOP](manage-admin-role-group-permissions-in-eop.md).

Pour plus d’informations sur les autorisations dans Microsoft 365, voir [à propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).

## <a name="role-based-permissions"></a>Autorisations basées sur des rôles

Les autorisations d’administrateur que vous accordez aux utilisateurs sont basées sur les rôles de gestion. Un rôle de gestion définit les cmdlets disponibles pour un ensemble de tâches données. Étant donné que le centre d’administration Exchange (Centre d’administration Exchange) et la version autonome d’EOP de PowerShell utilisent les cmdlets, l’octroi de l’accès à une cmdlet permet à l’utilisateur d’effectuer les tâches connexes dans le centre d’administration Exchange ou dans un PowerShell autonome EOP. Par exemple, le rôle destinataires de messagerie définit les applets de commande nécessaires pour modifier les utilisateurs de messagerie.

Dans EOP autonome, les rôles d’administrateur sont le seul type de rôle de gestion disponible (il n’y a pas de rôles d’utilisateur final ou de stratégie d’attribution de rôle).

## <a name="role-groups"></a>Groupes de rôles

Pour faciliter l’attribution de rôles aux utilisateurs, la fonction EOP autonome utilise des groupes de rôles. Les rôles de gestion sont attribués à des groupes de rôles, et les membres du groupe de rôles obtiennent les autorisations associées aux rôles. En d’autres termes, les rôles de gestion ne sont pas directement attribués aux utilisateurs ; ils sont affectés à un groupe de rôles. Ce modèle vous permet d’affecter de nombreux rôles à de nombreux membres de groupe de rôles en même temps. Les membres des groupes de rôles peuvent être des utilisateurs de messagerie, des groupes de sécurité à extension messagerie, des utilisateurs du centre d’administration Microsoft 365 et d’autres groupes de rôles.

La figure suivante montre la relation entre les utilisateurs, les groupes de rôles et les rôles.

![Relations des rôles, des groupes de rôles et des membres](../../media/ITPro_Security_RBAC_EXO_SimplifiedRoleGroupRelationship.png)

Les groupes de rôles disponibles dans EOP autonome sont décrits dans le tableau suivant.

****

|Groupe de rôles|Description|Rôles par défaut attribués|
|---|---|---|
|ComplianceManagement|Configurez et gérez les paramètres de conformité au sein de l’organisation, y compris la protection contre la perte de données (DLP) si votre abonnement dispose de fonctionnalités DLP. <br/><br/> Les membres du rôle [administrateur de conformité](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#compliance-administrator) dans Azure ad obtiennent automatiquement les autorisations de ce groupe de rôles.|Journaux d’audit <br/><br/> Administration de la conformité <br/><br/> Gestion des droits relatifs à l’information <br/><br/> Gestion de la rétention <br/><br/> Journaux d'audit en affichage seul <br/><br/> Afficher uniquement la configuration <br/><br/> Afficher uniquement les destinataires|
|ContentExplorerContentViewer|Non utilisé.|Visionneuse de contenu de classification des données|
|ContentExplorerListViewer|Non utilisé.|Visionneuse de liste de classification des données|
|Centre|Afficher et gérer les utilisateurs de messagerie.|Réinitialiser le mot de passe <br/><br/> Options de l’utilisateur <br/><br/> Afficher uniquement les destinataires|
|HygieneManagement|Gérer les fonctionnalités de protection (blocage du courrier indésirable, protection contre les programmes malveillants, etc.).|Hygiène de transport <br/><br/> Afficher uniquement la configuration <br/><br/> Afficher uniquement les destinataires|
|MailFlowAdministrator|Afficher et gérer les connecteurs et les domaines acceptés|Domaines distants et acceptés <br/><br/> Afficher uniquement les destinataires|
|OrganizationManagement|Accès administrateur à l’ensemble de l’organisation et possibilité d’effectuer quasiment n’importe quelle tâche. <br/><br/> Les membres du rôle [administrateur général](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#global-administrator--company-administrator) dans Azure ad obtiennent automatiquement les autorisations de ce groupe de rôles. <br/><br/> **Important**: étant donné que le groupe de rôles OrganizationManagement est un rôle puissant, seuls les utilisateurs qui effectuent des tâches administratives au niveau de l’organisation doivent être membres de ce groupe de rôles.|Programmes malveillants <br/><br/> Désir <br/><br/> Journaux d’audit <br/><br/> Administrateur de conformité <br/><br/> Groupes de distribution dynamique <br/><br/> Gestion des droits relatifs à l’information <br/><br/> Création de destinataires de message <br/><br/> Destinataires de message <br/><br/> Suivi de messages <br/><br/> Migration <br/><br/> Accès au client de l’Organisation <br/><br/> Configuration de l’Organisation <br/><br/> Paramètres de transport de l’Organisation <br/><br/> Quarantaine <br/><br/> Stratégies de destinataire <br/><br/> Domaines distants et acceptés <br/><br/> Réinitialiser le mot de passe <br/><br/> Gestion de la rétention <br/><br/> Gestion des rôles <br/><br/> Administrateur de sécurité <br/><br/> Création et appartenance à un groupe de sécurité <br/><br/> Lecteur de sécurité <br/><br/> Administrateur d’étiquette de sensibilité <br/><br/> Surveillance <br/><br/> Hygiène de transport <br/><br/> Règles de transport <br/><br/> Options de l’utilisateur <br/><br/> Protection contre les programmes malveillants en affichage seul <br/><br/> Affichage de courrier indésirable en lecture seule <br/><br/> Journaux d'audit en affichage seul <br/><br/> Afficher uniquement la configuration <br/><br/> Mise en quarantaine en lecture seule <br/><br/> Afficher uniquement les destinataires <br/><br/> Intelligence des menaces en affichage seul|
|QuarantineAdministrator|Gère les messages mis en quarantaine pour tous les destinataires.|Quarantaine|
|RecipientManagement|Créer, gérer et supprimer des objets destinataire dans l’organisation.|Groupes de distribution dynamique <br/><br/> Création de destinataires de message <br/><br/> Destinataires de message <br/><br/> Suivi de messages <br/><br/> Migration <br/><br/> Stratégies de destinataire <br/><br/> Réinitialiser le mot de passe|
|RecordsManagement|Configurez les fonctionnalités de conformité, telles que les balises de stratégie de rétention, les classifications de message et les règles de flux de messagerie (également appelées règles de transport).|Suivi de messages <br/><br/> Gestion de la rétention <br/><br/> Règles de transport|
|SecurityAdministrator|Configurez tous les aspects de la protection dans l’organisation (blocage du courrier indésirable, anti-programme malveillant, protection contre l’usurpation d’identité, mise en quarantaine, etc.). <br/><br/> Les membres du rôle [administrateur de sécurité](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#security-administrator) dans Azure ad obtiennent automatiquement les autorisations de ce groupe de rôles.|Programmes malveillants <br/><br/> Désir <br/><br/> Journaux d’audit <br/><br/> Quarantaine <br/><br/> Administrateur de sécurité <br/><br/> Administrateur d’étiquette de sensibilité <br/><br/> Protection contre les programmes malveillants en affichage seul <br/><br/> Affichage de courrier indésirable en lecture seule <br/><br/> Journaux d'audit en affichage seul <br/><br/> Mise en quarantaine en lecture seule <br/><br/> Intelligence des menaces en affichage seul|
|SecurityReader|Accès en lecture seule à tous les aspects de la protection dans l’organisation (blocage du courrier indésirable, anti-programme malveillant, protection contre l’usurpation d’identité, mise en quarantaine, etc.). <br/><br/> Les membres du rôle de [lecteur de sécurité](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#security-reader) dans Azure ad obtiennent automatiquement les autorisations de ce groupe de rôles.|Lecteur de sécurité <br/><br/> Protection contre les programmes malveillants en affichage seul <br/><br/> Affichage de courrier indésirable en lecture seule <br/><br/> Mise en quarantaine en lecture seule <br/><br/> Intelligence des menaces en affichage seul|
|TenantAdmins|L’appartenance à ce groupe de rôles est synchronisée entre les services et gérés de manière centralisée. Par défaut, aucun rôle n’est attribué à ce groupe de rôles. Toutefois, il est membre du groupe de rôles gestion de l’organisation et hérite de ces autorisations.|aucune|
|ViewOnlyOrganizationManagement|Afficher les objets de destinataire, de protection et de configuration, ainsi que leurs propriétés dans l’organisation.|Administrateur de conformité <br/><br/> Administrateur de sécurité <br/><br/> Lecteur de sécurité <br/><br/> Administrateur d’étiquette de sensibilité <br/><br/> Afficher uniquement la configuration <br/><br/> Afficher uniquement les destinataires|
|

Si vous travaillez dans une petite organisation qui n’a que quelques administrateurs, il se peut que vous deviez ajouter ces utilisateurs au groupe de rôles gestion de l’organisation uniquement, et vous n’aurez peut-être jamais besoin d’utiliser les autres groupes de rôles. Si vous travaillez dans une grande organisation, vous pouvez avoir des administrateurs qui effectuent des tâches spécifiques, telles que la configuration des destinataires. Dans ce cas, vous pouvez ajouter un administrateur au groupe de rôles Gestion des destinataires, et un autre administrateur au groupe de rôles gestion de l’organisation. Ces administrateurs peuvent ensuite gérer leurs domaines spécifiques, mais ils ne disposent pas des autorisations nécessaires pour gérer les domaines dont ils ne sont pas responsables.

Si les groupes de rôles intégrés dans Exchange Online ne correspondent pas à la fonction de vos administrateurs, vous pouvez créer des groupes de rôles y ajouter des rôles. Pour plus d’informations, consultez la rubrique [Manage Role Groups in standalone EOP](manage-admin-role-group-permissions-in-eop.md).

## <a name="roles"></a>Rôles

Les rôles intégrés qui sont disponibles dans la version autonome d’EOP sont décrits dans le tableau suivant.

****

|Rôle * *|Description|Affectations de groupe de rôles par défaut|
|---|---|---|
|Programmes malveillants|Afficher et modifier la configuration et les rapports pour les fonctionnalités anti-programme malveillant.|OrganizationManagement <br/><br/> SecurityAdministrator|
|Désir|Afficher et modifier la configuration et les rapports pour les fonctionnalités de blocage du courrier indésirable.|OrganizationManagement <br/><br/> SecurityAdministrator|
|Journaux d’audit|Recherchez dans le journal d’audit de l’administrateur et affichez les résultats.|ComplianceManagement <br/><br/> OrganizationManagement <br/><br/> SecurityAdministrator|
|Administrateur de conformité<sup>\*</sup>||ComplianceManagement <br/><br/> OrganizationManagement <br/><br/> ViewOnlyOrganizationManagement|
|Visionneuse de contenu de classification des données<sup>\*</sup>||ContentExplorerContentViewer|
|Visionneuse de liste de classification des données<sup>\*</sup>||
|Groupes de distribution dynamique|Créez et gérez tous les groupes de distribution, les groupes de sécurité à extension messagerie et les membres.|OrganizationManagement <br/><br/> RecipientManagement|
|Gestion des droits relatifs à l’information<sup>\*</sup>||ComplianceManagement <br/><br/> OrganizationManagement|
|Création de destinataires de message|Créez et supprimez des utilisateurs de messagerie.|OrganizationManagement <br/><br/> RecipientManagement|
|Destinataires de message|Modifier les utilisateurs de messagerie existants.|OrganizationManagement <br/><br/> RecipientManagement|
|Suivi des messages<sup>\*</sup>||OrganizationManagement <br/><br/> RecipientManagement <br/><br/> Gestion des enregistrements|
|MIGR<sup>\*</sup>||OrganizationManagement <br/><br/> RecipientManagement|
|MyBaseOptions|Permet aux utilisateurs de consulter leurs propres messages mis en quarantaine. <br/><br/> Ce rôle est automatiquement attribué aux utilisateurs et vous ne pouvez pas l’affecter manuellement.|aucune|
|Accès au client de l’Organisation<sup>\*</sup>||OrganizationManagement|
|Configuration de l’Organisation|Affichage des rapports.|OrganizationManagement|
|Paramètres de transport de l’Organisation<sup>\*</sup>||OrganizationManagement|
|Quarantaine|Gérez tous les types de messages mis en quarantaine pour tous les destinataires.|OrganizationManagement <br/><br/> QuarantineAdministrator <br/><br/> SecurityAdministrator|
|Stratégies de destinataire<sup>\*</sup>||OrganizationManagement <br/><br/> RecipientManagement|
|Domaines distants et acceptés|Gérer les domaines distants, les domaines acceptés et les connecteurs.|MailFlowAdministrator <br/><br/> OrganizationManagement|
|Réinitialiser le mot de passe<sup>\*</sup>||Centre <br/><br/> OrganizationManagement <br/><br/> RecipientManagement|
|Gestion de la rétention<sup>\*</sup>||ComplianceManagement <br/><br/> OrganizationManagement <br/><br/> RecordsManagement|
|Gestion des rôles|Créer et gérer des groupes de rôles.|OrganizationManagement|
|Administrateur de sécurité|Gestion de la configuration et des rapports pour toutes les fonctionnalités de sécurité et de protection.|OrganizationManagement <br/><br/> SecurityAdministrator <br/><br/> ViewOnlyOrganizationManagement|
|Création et appartenance à un groupe de sécurité|Créer et gérer des groupes de sécurité à extension messagerie.|OrganizationManagement|
|Lecteur de sécurité|Affichage de la configuration et des rapports pour les fonctionnalités de sécurité et de protection.|Gestion de l’organisation <br/><br/> SecurityReader <br/><br/> ViewOnlyOrganizationManagement|
|Administrateur d’étiquette de sensibilité<sup>\*</sup>||OrganizationManagement <br/><br/> SecurityAdministrator <br/><br/> ViewOnlyOrganizationManagement|
|Supervision<sup>\*</sup>||OrganizationManagement|
|Hygiène de transport|Gérer les logiciels malveillants, les fonctionnalités de blocage du courrier indésirable et les fonctionnalités de détection d’usurpation d’identité.|HygieneManagement <br/><br/> OrganizationManagement|
|Règles de transport|Créer et gérer des règles de flux de messagerie (également appelées règles de transport).|OrganizationManagement <br/><br/> RecordsManagement|
|Options de l’utilisateur|Modifier les utilisateurs de messagerie existants.|Centre <br/><br/> OrganizationManagement|
|Protection contre les programmes malveillants en affichage seul|Affichage de la configuration et des rapports pour les fonctionnalités anti-programme malveillant.|OrganizationManagement <br/><br/> SecurityAdministrator <br/><br/> SecurityReader|
|Affichage de courrier indésirable en lecture seule|Affichage de la configuration et des rapports pour les fonctionnalités de blocage du courrier indésirable.|OrganizationManagement <br/><br/> SecurityAdministrator <br/><br/> SecurityReader|
|Journaux d'audit en affichage seul|Recherchez dans le journal d’audit de l’administrateur et affichez les résultats.|ComplianceManagement <br/><br/> OrganizationManagement <br/><br/> SecurityAdministrator|
|Afficher uniquement la configuration|Affichez tous les paramètres d’organisation et de flux de messagerie (autres que les destinataires) de l’organisation.|ComplianceManagement <br/><br/> HygieneManagement <br/><br/> OrganizationManagement <br/><br/> ViewOnlyOrganizationManagement|
|Mise en quarantaine en lecture seule|Afficher tous les messages mis en quarantaine pour tous les destinataires.|OrganizationManagement <br/><br/> SecurityAdministrator <br/><br/> SecurityReader|
|Afficher uniquement les destinataires|Afficher les propriétés du destinataire et exécuter le suivi des messages.|ComplianceManagement <br/><br/> Centre <br/><br/> HygieneManagement <br/><br/> MailFlowAdministrator <br/><br/>  OrganizationManagement <br/><br/> ViewOnlyOrganizationManagement|
|Intelligence des menaces en affichage seul<sup>\*</sup>||OrganizationManagement <br/><br/> SecurityAdministrator <br/><br/> SecurityReader|
|

<sup>\*</sup> Bien que ce rôle soit disponible, il n’est rien utile dans EOP autonome.

## <a name="microsoft-365-permissions-in-standalone-eop"></a>Autorisations Microsoft 365 dans EOP autonome

Lorsque vous créez un utilisateur dans le centre d’administration 365 de Microsoft, vous pouvez choisir d’affecter divers rôles d’administrateur, tels que administrateur général, administrateur de service, administrateur de mot de passe, etc., à l’utilisateur. Certains rôles Microsoft 365, mais pas tous, accordent des autorisations d’administration à l’utilisateur dans EOP.

> [!NOTE]
> Le compte que vous avez utilisé pour créer votre organisation EOP autonome est automatiquement affecté au rôle d’administrateur global.

Le tableau suivant répertorie les rôles Microsoft 365 et les groupes de rôles EOP autonomes auxquels ils correspondent. Pour plus d’informations sur ces rôles, consultez la rubrique [à propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).

****

|Rôle Microsoft 365|Groupe de rôles EOP|
|---|---|
|Administrateur Exchange|OrganizationManagement|
|Administrateur global|OrganizationManagement <br/><br/> **Remarque**: le rôle d’administrateur global et le groupe de rôles OrganizationManagement sont liés à l’aide d’un groupe de rôles d’administrateur de société spécial. Le groupe de rôles administrateur d’entreprise est géré en interne et ne peut pas être modifié directement.|
|Administrateur de mots de passe|Centre|
|Lecteur général|ViewOnlyOrganizationManagement|
|Administrateur de la sécurité|SecurityAdministrator|
|Lecteur Sécurité|SecurityReader|
|

Les autres rôles Microsoft 365 n’ont pas de groupe de rôles EOP correspondant et n’accordent pas d’autorisations d’administration dans EOP. Pour plus d’informations sur l’affectation d’un rôle Microsoft 365 à un utilisateur, reportez-vous à la rubrique [assigner des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles).

Les utilisateurs peuvent bénéficier de droits d’administration dans EOP sans les ajouter aux rôles Microsoft 365. Pour ce faire, ajoutez l’utilisateur en tant que membre d’un groupe de rôles EOP. L’utilisateur obtiendra les autorisations dans EOP, mais il n’obtiendra pas les autorisations dans les autres charges de travail Microsoft 365.

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien copié un groupe de rôles, effectuez l’une des opérations suivantes :

- Dans le centre d’administration Exchange, accédez à rôles d’administrateur des **autorisations** \> **Admin Roles**et vérifiez que le groupe de rôles est affiché (ou non). Sélectionnez le groupe de rôles et vérifiez les paramètres dans le volet d’informations ou cliquez sur **modifier** ![ l’icône modifier ](../../media/ITPro-EAC-EditIcon.png) pour vérifier les paramètres.

- Dans Exchange Online PowerShell, remplacez \<Role Group Name\> par le nom du groupe de rôles et exécutez la commande suivante pour vérifier que le groupe de rôles existe (ou n’existe pas) et vérifiez les paramètres :

    ```PowerShell
    Get-RoleGroup -Identity "<Role Group Name>" | Format-List
    ```
