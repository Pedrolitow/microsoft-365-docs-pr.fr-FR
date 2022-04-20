---
title: Configurer l’audit (Standard) dans Microsoft 365
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
ms.custom: admindeeplinkEXCHANGE
search.appverid:
- MOE150
- MET150
description: Cet article explique comment configurer l’audit (Standard) afin que vous puissiez commencer à rechercher les activités d’audit effectuées par les utilisateurs et les administrateurs de votre organisation.
ms.openlocfilehash: 15e72d1b2899799f432cdc717352cf53a0a370e4
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993729"
---
# <a name="set-up-microsoft-purview-audit-standard"></a>Configurer l’audit Microsoft Purview (Standard)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Audit (Standard) dans Microsoft 365 vous permet de rechercher des enregistrements d’audit pour les activités effectuées dans les différents services Microsoft 365 par les utilisateurs et les administrateurs. Étant donné que l’audit (Standard) est activé par défaut pour la plupart des organisations Microsoft 365 et Office 365, vous n’avez besoin que de quelques opérations avant que vous et d’autres membres de votre organisation puissiez rechercher dans le journal d’audit.

Cet article décrit les étapes suivantes nécessaires à la configuration de l’audit (Standard).

![Étapes de configuration de l’audit (Standard).](../media/BasicAuditingWorkflow.png)

Ces étapes incluent la garantie des abonnements organisationnels et des licences utilisateur nécessaires pour générer et conserver les enregistrements d’audit et l’attribution d’autorisations aux membres de votre équipe des opérations de sécurité, de l’informatique, de la conformité et des équipes juridiques afin de pouvoir rechercher dans le journal d’audit.

Pour plus d’informations, consultez [Audit (Standard) dans Microsoft 365](auditing-solutions-overview.md#audit-standard).

## <a name="step-1-verify-organization-subscription-and-user-licensing"></a>Étape 1 : Vérifier l’abonnement de l’organisation et les licences utilisateur

La gestion des licences pour l’audit (Standard) nécessite l’abonnement d’organisation approprié qui fournit l’accès à l’outil de recherche de journaux d’audit et aux licences par utilisateur nécessaires pour journaliser et conserver les enregistrements d’audit.

Lorsqu’une activité auditée est effectuée par un utilisateur ou un administrateur, un enregistrement d’audit est généré et stocké dans le journal d’audit pour votre organisation. Dans Audit (Standard), les enregistrements d’audit sont conservés et consultables dans le journal d’audit pendant 90 jours.

Pour obtenir la liste des exigences d’abonnement et de licence pour l’audit (Standard), consultez [les solutions d’audit dans Microsoft 365](auditing-solutions-overview.md#licensing-requirements).

## <a name="step-2-assign-permissions-to-search-the-audit-log"></a>Étape 2 : Attribuer des autorisations pour rechercher dans le journal d’audit

Les administrateurs et les membres des équipes d’investigation doivent se voir attribuer le rôle journaux d’audit ou journaux d’audit View-Only dans Exchange Online pour effectuer une recherche dans le journal d’audit. Par défaut, ces rôles sont affectés aux groupes de rôles Gestion de la conformité et Gestion de l’organisation sur la page **Autorisations** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>. Les administrateurs globaux dans votre client Office 365 et Microsoft 365 sont automatiquement des membres du groupe de rôle Gestion de l'organisation dans Exchange Online. Pour permettre à un utilisateur d’effectuer des recherches dans le journal d’audit avec le niveau minimal de privilèges, vous pouvez créer un groupe de rôles personnalisé dans Exchange Online, ajouter le rôle Journaux d’audit en affichage seul ou Journaux d’audit, puis ajouter l’utilisateur en tant que membre du nouveau groupe de rôles. Pour plus d’informations, voir [Gérer les groupes de rôles dans Exchange Online](/Exchange/permissions-exo/role-groups).

La capture d’écran suivante montre les deux rôles liés à l’audit attribués au groupe de rôles Gestion de l’organisation dans le centre d’administration Exchange.

![Auditer les rôles attribués au groupe de rôles dans Exchange Online.](../media/EACAuditRoles.png)

## <a name="step-3-search-the-audit-log"></a>Étape 3 : Rechercher dans le journal d’audit

Vous êtes maintenant prêt à effectuer une recherche dans le journal d’audit dans le portail de conformité Microsoft Purview.

1. Accédez et <https://compliance.microsoft.com> connectez-vous à l’aide d’un compte qui a reçu les autorisations d’audit appropriées.

2. Dans le volet de navigation gauche du portail de conformité, cliquez sur **Afficher tout** , puis sur **Audit**.

3. Dans la page **Audit** , configurez la recherche à l’aide des conditions suivantes sous l’onglet **Recherche** . 

   ![Paramètres de configuration pour la recherche dans le journal d’audit.](../media/AuditLogSearchToolMCCCallouts.png)

   1. **Plage de date et d’heure**. Sélectionnez une plage de dates et d’heures pour afficher les événements survenus pendant cette période. La date et l’heure sont présentées dans l’heure locale. Les sept derniers jours sont sélectionnés par défaut.
  
   2. **Activités**. Sélectionnez les activités à rechercher. Utilisez la zone de recherche pour rechercher des activités à ajouter à la liste. Pour obtenir une liste partielle des activités auditées, consultez [Activités auditées](search-the-audit-log-in-security-and-compliance.md#audited-activities). Laissez cette zone vide pour renvoyer des entrées pour toutes les activités auditées.
  
   3. **Utilisateurs**.  Cliquez dans cette zone et commencez à taper le nom des utilisateurs pour lequel afficher les résultats de la recherche. Les entrées du journal d’audit pour les activités sélectionnées effectuées par les utilisateurs que vous sélectionnez dans cette zone sont affichées dans la liste des résultats. Laissez cette zone vide pour renvoyer les entrées pour tous les utilisateurs (et les comptes de service) dans votre organisation.
  
   4. **Fichier, dossier ou site**. Tapez une partie ou la totalité d’un nom de fichier ou de dossier pour rechercher l’activité liée au fichier de dossier qui contient le mot clé spécifié. Vous pouvez également spécifier l’URL d’un fichier ou d’un dossier. Si vous utilisez une URL d’un fichier ou d’un dossier, assurez-vous que le type du chemin d’URL complet ou si vous tapez une partie de l’URL, n’incluez pas de caractères ou d’espaces spéciaux. Laissez cette zone vide pour renvoyer les entrées correspondant à tous les fichiers et dossiers dans votre organisation.

4. Cliquez sur **Rechercher** pour exécuter la recherche.

Une nouvelle page s’affiche pour afficher la recherche dans le journal d’audit en cours d’exécution. Une fois la recherche terminée, les enregistrements d’audit s’affichent sur la page. Cliquez sur un enregistrement pour afficher une page volante avec des propriétés détaillées.

Pour obtenir des instructions plus détaillées, consultez [Rechercher dans le journal d’audit dans le centre de conformité](search-the-audit-log-in-security-and-compliance.md).
