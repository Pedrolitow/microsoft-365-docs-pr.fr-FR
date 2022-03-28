---
title: Configurer l’audit avancé dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Cet article explique comment configurer l’audit avancé afin de pouvoir effectuer des enquêtes d’investigation lorsque des comptes d’utilisateur sont compromis ou pour enquêter sur d’autres incidents liés à la sécurité.
ms.openlocfilehash: dafe53161e04f28f2f5e4ff8dcfa71bab6c1a1f1
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754590"
---
# <a name="set-up-advanced-audit-in-microsoft-365"></a>Configurer l’audit avancé dans Microsoft 365

Si votre organisation dispose d’un abonnement et d’une licence d’utilisateur final qui prend en charge l’audit avancé, effectuez les étapes suivantes pour configurer et utiliser les fonctionnalités supplémentaires de l’audit avancé.

![Flux de travail pour configurer l’Audit avancé.](../media/AdvancedAuditWorkflow.png)

## <a name="step-1-set-up-advanced-audit-for-users"></a>Étape 1 : Configurer l’audit avancé pour les utilisateurs

Les fonctionnalités d’audit avancées telles que la possibilité d’enregistrer des événements importants tels que MailItemsAccessed et envoyer nécessitent une licence E5 appropriée attribuée aux utilisateurs. De plus, l’application/plan de service d’audit avancé doit être activé pour ces utilisateurs. Pour vérifier que l’application d’audit avancée est attribuée aux utilisateurs, procédez comme suit pour chaque utilisateur :

1. Dans la Centre d'administration Microsoft 365, sélectionnez **utilisateurs UsersActive** >  et sélectionnez un utilisateur.<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a>

2. Dans la page déroulante des propriétés de l’utilisateur, cliquez sur **Licences et applications**.

3. Dans la section **Licences** , vérifiez qu’une licence E5 est attribuée à l’utilisateur ou qu’une licence de module add-on appropriée lui est attribuée. Pour obtenir la liste des licences qui prisent en charge l’audit avancé, consultez [la liste des licences d’audit avancé requises](auditing-solutions-overview.md#advanced-audit-1).

4. Développez la section **Applications** et vérifiez que la case à cocher **Audit avancé Microsoft 365** est activée.

5. Si la case à cocher n’est pas sélectionnée, sélectionnez-la, puis cliquez sur **Enregistrer les modifications.**

   La journalisation des enregistrements d’audit pour MailItemsAccessed et Send commence dans les 24 heures. Vous devez effectuer l’étape 3 pour démarrer la journalisation de deux autres événements d’audit avancé : SearchQueryInitiatedExchange et SearchQueryInitiatedSharePoint.

En outre, si vous avez personnalisé les actions de boîte aux lettres qui sont enregistrées sur des boîtes aux lettres utilisateur ou des boîtes aux lettres partagées, les nouveaux événements d’audit avancé publiés par Microsoft ne seront pas automatiquement audités sur ces boîtes aux lettres. Pour plus d’informations sur la modification des actions de boîte aux lettres auditées pour chaque type de connexion, consultez la section « Modifier ou restaurer les actions de boîte aux lettres enregistrées par défaut » dans [Gérer l’audit de boîte aux lettres](enable-mailbox-auditing.md#change-or-restore-mailbox-actions-logged-by-default).

## <a name="step-2-enable-advanced-audit-events"></a>Étape 2 : Activer les événements d’audit avancé

Vous devez activer la journalité de deux événements d’audit avancé (SearchQueryInitiatedExchange et SearchQueryInitiatedSharePoint) lorsque les utilisateurs effectuent des recherches dans Exchange Online et SharePoint Online. Pour permettre à ces deux événements d’être audités pour les utilisateurs, exécutez la commande suivante (pour chaque utilisateur) [dans Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) :

```powershell
Set-Mailbox <user> -AuditOwner @{Add="SearchQueryInitiated"}
```

Dans un environnement multigé géographique, vous devez exécuter la commande **Set-Mailbox** précédente dans la forêt où se trouve la boîte aux lettres de l’utilisateur. Pour identifier l’emplacement de la boîte aux lettres de l’utilisateur, exécutez la commande suivante : 

```powershell
Get-Mailbox <user identity> | FL MailboxLocations
```

Si la commande permettant d’activer l’audit des requêtes de recherche a été précédemment exécuté dans une forêt différente de celle dans laquelle se trouve la boîte aux lettres de l’utilisateur, vous devez supprimer la valeur SearchQueryInitiated de la boîte aux lettres de l’utilisateur en l’exécutant `Set-Mailbox -AuditOwner @{Remove="SearchQueryInitiated"}` , puis l’ajouter à la boîte aux lettres de l’utilisateur dans la forêt où se trouve la boîte aux lettres de l’utilisateur.

## <a name="step-3-set-up-audit-retention-policies"></a>Étape 3 : Configurer des stratégies de rétention d’audit

En plus de la stratégie par défaut qui conserve les enregistrements d’audit Exchange, SharePoint et Azure AD pendant un an, vous pouvez créer des stratégies de rétention supplémentaires pour le journal d’audit afin de répondre aux exigences des équipes de sécurité, informatique et de conformité de votre organisation. Pour plus d’informations, voir [gérer les stratégies de rétention du journal d’audit](audit-log-retention-policies.md).

## <a name="step-4-search-for-advanced-audit-events"></a>Étape 4 : Rechercher des événements d’audit avancés

Maintenant que l’audit avancé est installé pour votre organisation, vous pouvez rechercher des événements d’audit avancés essentiels et d’autres activités lors de la conduite d’enquêtes légales. Après avoir effectué les étapes 1 et 2, vous pouvez rechercher dans le journal d’audit les événements d’audit avancés et d’autres activités pendant les enquêtes d’investigation de comptes compromis et d’autres types d’enquêtes de sécurité ou de conformité. Pour plus d’informations sur la conduite d’une investigation d’investigation d’utilisateurs compromis à l’aide de l’événement d’audit avancé MailItemsAccessed, voir [Utiliser l’audit](mailitemsaccessed-forensics-investigations.md) avancé pour examiner les comptes compromis.
