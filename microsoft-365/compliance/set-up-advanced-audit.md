---
title: Configurer l’audit (Premium) dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Cet article explique comment configurer l’audit (Premium) afin que vous puissiez effectuer des investigations judiciaires lorsque des comptes d’utilisateurs sont compromis ou pour enquêter sur d’autres incidents liés à la sécurité.
ms.openlocfilehash: f1c858964ee3cb5e6cdfcdb7416468318393ebba
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097951"
---
# <a name="set-up-microsoft-purview-audit-premium"></a>Configurer l’audit Microsoft Purview (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Si votre organisation dispose d’un abonnement et d’une licence d’utilisateur final qui prend en charge l’audit (Premium), effectuez les étapes suivantes pour configurer et utiliser les fonctionnalités supplémentaires dans Audit (Premium).

![Flux de travail pour configurer l’audit (Premium).](../media/AdvancedAuditWorkflow.png)

## <a name="step-1-set-up-audit-premium-for-users"></a>Étape 1 : Configurer l’audit (Premium) pour les utilisateurs

Les fonctionnalités d’audit (Premium) telles que la possibilité d’enregistrer des événements importants tels que MailItemsAccessed et envoyer nécessitent une licence E5 appropriée attribuée aux utilisateurs. De plus, l’application/plan de service d’audit avancé doit être activé pour ces utilisateurs. Pour vérifier que l’application d’audit avancée est attribuée aux utilisateurs, procédez comme suit pour chaque utilisateur :

1. Dans le Centre d'administration Microsoft 365, accédez aux **utilisateurs UsersActive** > , puis sélectionnez un utilisateur.<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a>

2. Dans la page déroulante des propriétés de l’utilisateur, cliquez sur **Licences et applications**.

3. Dans la section **Licences** , vérifiez que l’utilisateur se voit attribuer une licence E5 ou qu’une licence de module complémentaire appropriée lui est attribuée. Pour obtenir la liste des licences qui prennent en charge l’audit (Premium), consultez [Les exigences en matière de licences d’audit (Premium](auditing-solutions-overview.md#audit-premium-1)).

4. Développez la section **Applications** et vérifiez que la case à cocher **Audit avancé Microsoft 365** est activée.

5. Si la case à cocher n’est pas cochée, sélectionnez-la, puis cliquez sur **Enregistrer les modifications.**

   La journalisation des enregistrements d’audit pour MailItemsAccessed et Send commence dans les 24 heures. Vous devez effectuer l’étape 3 pour commencer la journalisation de deux autres événements d’audit (Premium) : SearchQueryInitiatedExchange et SearchQueryInitiatedSharePoint.

En outre, si vous avez personnalisé les actions de boîte aux lettres qui sont journalisées sur les boîtes aux lettres utilisateur ou les boîtes aux lettres partagées, les nouveaux événements d’audit (Premium) publiés par Microsoft ne seront pas automatiquement audités sur ces boîtes aux lettres. Pour plus d’informations sur la modification des actions de boîte aux lettres auditées pour chaque type de connexion, consultez la section « Modifier ou restaurer les actions de boîte aux lettres enregistrées par défaut » dans [Gérer l’audit de boîte aux lettres](enable-mailbox-auditing.md#change-or-restore-mailbox-actions-logged-by-default).

## <a name="step-2-enable-audit-premium-events"></a>Étape 2 : Activer les événements d’audit (Premium)

Vous devez activer la journalisation de deux événements d’audit (Premium) (SearchQueryInitiatedExchange et SearchQueryInitiatedSharePoint) lorsque les utilisateurs effectuent des recherches dans Exchange Online et SharePoint Online. Pour permettre l’audit de ces deux événements pour les utilisateurs, exécutez la commande suivante (pour chaque utilisateur) dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) :

```powershell
Set-Mailbox <user> -AuditOwner @{Add="SearchQueryInitiated"}
```

Dans un environnement multigéographique, vous devez exécuter la commande **Set-Mailbox** précédente dans la forêt où se trouve la boîte aux lettres de l’utilisateur. Pour identifier l’emplacement de la boîte aux lettres de l’utilisateur, exécutez la commande suivante : 

```powershell
Get-Mailbox <user identity> | FL MailboxLocations
```

Si la commande permettant d’activer l’audit des requêtes de recherche était précédemment exécutée dans une forêt différente de celle dans laquelle se trouve la boîte aux lettres de l’utilisateur, vous devez supprimer la valeur SearchQueryInitiated de la boîte aux lettres de l’utilisateur en l’exécutant `Set-Mailbox -AuditOwner @{Remove="SearchQueryInitiated"}` , puis l’ajouter à la boîte aux lettres de l’utilisateur dans la forêt où se trouve la boîte aux lettres de l’utilisateur.

## <a name="step-3-set-up-audit-retention-policies"></a>Étape 3 : Configurer des stratégies de rétention d’audit

En plus de la stratégie par défaut qui conserve les enregistrements d’audit Exchange, SharePoint et Azure AD pendant un an, vous pouvez créer des stratégies de rétention supplémentaires pour le journal d’audit afin de répondre aux exigences des équipes de sécurité, informatique et de conformité de votre organisation. Pour plus d’informations, voir [gérer les stratégies de rétention du journal d’audit](audit-log-retention-policies.md).

## <a name="step-4-search-for-audit-premium-events"></a>Étape 4 : Rechercher des événements d’audit (Premium)

Maintenant que vous avez configuré l’audit (Premium) pour votre organisation, vous pouvez rechercher des événements d’audit essentiels (Premium) et d’autres activités lors de la réalisation d’investigations judiciaires. Une fois l’étape 1 et l’étape 2 terminées, vous pouvez rechercher dans le journal d’audit les événements d’audit (Premium) et d’autres activités pendant les investigations judiciaires sur des comptes compromis et d’autres types d’enquêtes de sécurité ou de conformité. Pour plus d’informations sur la conduite d’une enquête judiciaire sur les comptes d’utilisateur compromis à l’aide de l’événement MailItemsAccessed Audit (Premium), consultez [Utiliser l’audit (Premium) pour examiner les comptes compromis](mailitemsaccessed-forensics-investigations.md).
