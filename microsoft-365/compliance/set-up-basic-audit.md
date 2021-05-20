---
title: Mettre en place l’audit de base Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-scenario
search.appverid:
- MOE150
- MET150
description: Cet article décrit comment configurer l’audit de base afin que vous puissiez commencer à rechercher des activités d’audit effectuées par les utilisateurs et les administrateurs de votre organisation.
ms.openlocfilehash: 59b5c85003ef0e19f7d3dd7417f764f446244652
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52564824"
---
# <a name="set-up-basic-audit-in-microsoft-365"></a>Mettre en place l’audit de base Microsoft 365

L’audit de base Microsoft 365 vous permet de rechercher des enregistrements d’audit pour les activités effectuées dans les différents services Microsoft 365 par les utilisateurs et les administrateurs. Étant donné que l’audit de base est activé par défaut pour la plupart des organisations de Microsoft 365 et Office 365, il n’y a que quelques choses que vous devez faire avant que vous et d’autres membres de votre organisation puissiez rechercher dans le journal d’audit.

Cet article traite des étapes suivantes nécessaires à la mise en place de l’audit de base.

![Étapes de mise en place de l’audit de base](../media/BasicAuditingWorkflow.png)

Ces étapes comprennent l’assurance des abonnements organisationnels appropriés et des licences d’utilisateur nécessaires pour générer et préserver les dossiers d’audit et l’attribution d’autorisations aux membres de l’équipe de vos opérations de sécurité, de vos équipes informatique, de conformité et juridiques afin de pouvoir rechercher le journal de vérification.

Pour plus d’informations, [voir Audit de base dans Microsoft 365](auditing-solutions-overview.md#basic-audit).

## <a name="step-1-verify-organization-subscription-and-user-licensing"></a>Étape 1 : Vérifier l’abonnement à l’organisation et les licences d’utilisation

L’octroi de licences pour la vérification de base nécessite l’abonnement approprié à l’organisation qui donne accès à l’outil de recherche de journaux de vérification et aux licences par utilisateur nécessaires pour enregistrer et conserver les dossiers de vérification.

Lorsqu’une activité auditée est effectuée par un utilisateur ou un administrateur, un enregistrement d’audit est généré et stocké dans le journal d’audit pour votre organisation. Dans la vérification de base, les dossiers de vérification sont conservés et consultables dans le journal de vérification pendant 90 jours.

Pour une liste des exigences en matière d’abonnement et de licence pour l’audit de base, [consultez les solutions d’audit Microsoft 365](auditing-solutions-overview.md#licensing-requirements).

## <a name="step-2-assign-permissions-to-search-the-audit-log"></a>Étape 2 : Attribuez des autorisations pour rechercher le journal d’audit

Les administrateurs et les membres des équipes d’enquête doivent se voir attribuer le rôle View-Only journaux d’audit ou de registres d’audit dans Exchange Online pour rechercher le journal de vérification. Par défaut, ces rôles sont affectés aux groupes de rôles Gestion de la conformité et Gestion de l’organisation sur la page **Autorisations** dans le Centre d’administration Exchange. Les administrateurs mondiaux dans les Office 365 et Microsoft 365 sont automatiquement ajoutés en tant que membres du groupe de rôle de gestion de l’organisation dans Exchange Online. Pour permettre à un utilisateur d’effectuer des recherches dans le journal d’audit avec le niveau minimal de privilèges, vous pouvez créer un groupe de rôles personnalisé dans Exchange Online, ajouter le rôle Journaux d’audit en affichage seul ou Journaux d’audit, puis ajouter l’utilisateur en tant que membre du nouveau groupe de rôles. Pour plus d’informations, voir [Gérer les groupes de rôles dans Exchange Online](/Exchange/permissions-exo/role-groups).

La capture d’écran suivante montre les deux rôles liés à l’audit attribués au groupe de rôle de gestion de l’organisation dans Exchange centre d’administration.

![Rôles de vérification attribués au groupe de rôle dans Exchange Online](../media/EACAuditRoles.png)

## <a name="step-3-search-the-audit-log"></a>Étape 3 : Recherchez le journal d’audit

Vous êtes maintenant prêt à rechercher le journal d’audit dans le centre de Microsoft 365 de contrôle.

1. Rendez-vous <https://compliance.microsoft.com> et connectez-vous à l’aide d’un compte qui a reçu les autorisations de vérification appropriées.

2. Dans le volet de navigation gauche du centre de Microsoft 365, cliquez sur **Afficher tout et** cliquez ensuite sur **Audit**.

3. Sur la page **Audit,** configurez la recherche en utilisant les conditions suivantes sur **l’onglet** Recherche. 

   ![Paramètres de configuration pour la recherche de journaux d’audit](../media/AuditLogSearchToolMCCCallouts.png)

   1. **Date et plage d’heure**. Sélectionnez une plage de dates et d’heures pour afficher les événements survenus pendant cette période. La date et l’heure sont présentées dans l’heure locale. Les sept derniers jours sont sélectionnés par défaut.
  
   2. **Activités**. Sélectionnez les activités à rechercher. Utilisez la zone de recherche pour rechercher des activités à ajouter à la liste. Pour une liste partielle des activités vérifiées, voir [Activités vérifiées](search-the-audit-log-in-security-and-compliance.md#audited-activities). Laissez cette boîte vide pour retourner les entrées pour toutes les activités vérifiées.
  
   3. **Utilisateurs**.  Cliquez dans cette case et commencez à taper le nom des utilisateurs pour afficher les résultats de recherche. Les entrées du journal d’audit pour les activités sélectionnées effectuées par les utilisateurs que vous sélectionnez dans cette boîte sont affichées dans la liste des résultats. Laissez cette zone vide pour renvoyer les entrées pour tous les utilisateurs (et les comptes de service) dans votre organisation.
  
   4. **Fichier, dossier ou site**. Tapez une partie ou la partie d’un nom de fichier ou de dossier pour rechercher l’activité liée au fichier de dossier qui contient le mot clé spécifié. Vous pouvez également spécifier l’URL d’un fichier ou d’un dossier. Si vous utilisez une URL d’un fichier ou d’un dossier, assurez-vous que le type de chemin URL complet ou si vous tapez une partie de l’URL, n’incluez pas de caractères ou d’espaces spéciaux. Laissez cette zone vide pour renvoyer les entrées correspondant à tous les fichiers et dossiers dans votre organisation.

4. Cliquez **sur Recherche** pour exécuter la recherche.

Une nouvelle page s’affiche qui affiche la recherche de journal d’audit est en cours d’exécution. Lorsque la recherche est terminée, les dossiers de vérification sont affichés sur la page. Cliquez sur un enregistrement pour afficher une page de flyout avec des propriétés détaillées.

Pour plus d’instructions détaillées, consultez [le journal d’audit dans le centre de conformité](search-the-audit-log-in-security-and-compliance.md).
