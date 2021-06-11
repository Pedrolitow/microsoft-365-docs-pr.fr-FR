---
title: Configurer l’audit de base dans Microsoft 365
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
description: Cet article explique comment configurer l’audit de base afin de pouvoir commencer à rechercher les activités d’audit effectuées par les utilisateurs et les administrateurs de votre organisation.
ms.openlocfilehash: 59b5c85003ef0e19f7d3dd7417f764f446244652
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52564824"
---
# <a name="set-up-basic-audit-in-microsoft-365"></a>Configurer l’audit de base dans Microsoft 365

L’audit de base Microsoft 365 vous permet de rechercher des enregistrements d’audit pour les activités effectuées dans les différents services Microsoft 365 par les utilisateurs et les administrateurs. Étant donné que l’audit de base est activé par défaut pour la plupart des organisations Microsoft 365 et Office 365, vous ne devez effectuer que quelques opérations avant que vous et d’autres membres de votre organisation ne parviez à effectuer des recherches dans le journal d’audit.

Cet article décrit les étapes suivantes nécessaires à la mise en place de l’audit de base.

![Étapes de la mise en place de l’audit de base](../media/BasicAuditingWorkflow.png)

Ces étapes incluent la vérification des abonnements organisationnels et des licences utilisateur appropriés requis pour générer et conserver les enregistrements d’audit, ainsi que l’attribution d’autorisations aux membres de vos équipes de sécurité, informatiques, de conformité et juridiques afin de pouvoir effectuer des recherches dans le journal d’audit.

Pour plus d’informations, voir [Audit de base dans Microsoft 365](auditing-solutions-overview.md#basic-audit).

## <a name="step-1-verify-organization-subscription-and-user-licensing"></a>Étape 1 : Vérifier l’abonnement de l’organisation et la gestion des licences utilisateur

La gestion des licences pour l’audit de base nécessite l’abonnement approprié à l’organisation qui permet d’accéder à l’outil de recherche du journal d’audit et à la gestion des licences par utilisateur nécessaires pour enregistrer et conserver les enregistrements d’audit.

Lorsqu’une activité auditée est effectuée par un utilisateur ou un administrateur, un enregistrement d’audit est généré et stocké dans le journal d’audit pour votre organisation. Dans l’audit de base, les enregistrements d’audit sont conservés et peuvent faire l’objet d’une recherche dans le journal d’audit pendant 90 jours.

Pour obtenir la liste des conditions d’abonnement et de licence requises pour l’audit de base, voir [solutions d’audit dans Microsoft 365](auditing-solutions-overview.md#licensing-requirements).

## <a name="step-2-assign-permissions-to-search-the-audit-log"></a>Étape 2 : Attribuer des autorisations pour effectuer des recherches dans le journal d’audit

Les administrateurs et les membres des équipes d’enquête doivent avoir le rôle Journaux d’audit View-Only ou Journaux d’audit dans Exchange Online pour effectuer des recherches dans le journal d’audit. Par défaut, ces rôles sont affectés aux groupes de rôles Gestion de la conformité et Gestion de l’organisation sur la page **Autorisations** dans le Centre d’administration Exchange. Les administrateurs globaux Office 365 et Microsoft 365 sont automatiquement ajoutés en tant que membres du groupe de rôles Gestion de l’organisation dans Exchange Online. Pour permettre à un utilisateur d’effectuer des recherches dans le journal d’audit avec le niveau minimal de privilèges, vous pouvez créer un groupe de rôles personnalisé dans Exchange Online, ajouter le rôle Journaux d’audit en affichage seul ou Journaux d’audit, puis ajouter l’utilisateur en tant que membre du nouveau groupe de rôles. Pour plus d’informations, voir [Gérer les groupes de rôles dans Exchange Online](/Exchange/permissions-exo/role-groups).

La capture d’écran suivante montre les deux rôles liés à l’audit attribués au groupe de rôles Gestion de l’organisation dans Exchange’administration centrale.

![Auditer les rôles attribués au groupe de rôles dans Exchange Online](../media/EACAuditRoles.png)

## <a name="step-3-search-the-audit-log"></a>Étape 3 : Effectuer des recherches dans le journal d’audit

Vous êtes maintenant prêt à effectuer des recherches dans le journal d’audit dans Microsoft 365 conformité.

1. Go to <https://compliance.microsoft.com> and sign in using an account that has been assigned the appropriate audit permissions.

2. Dans le volet de navigation gauche du centre Microsoft 365 conformité, cliquez sur Afficher **tout,** puis sur **Auditer.**

3. Dans la page **Audit,** configurez la recherche en utilisant les conditions suivantes sous **l’onglet** Recherche. 

   ![Paramètres de configuration pour la recherche dans le journal d’audit](../media/AuditLogSearchToolMCCCallouts.png)

   1. **Date et plage de temps.** Sélectionnez une plage de dates et d’heures pour afficher les événements survenus pendant cette période. La date et l’heure sont présentées dans l’heure locale. Les sept derniers jours sont sélectionnés par défaut.
  
   2. **Activités**. Sélectionnez les activités à rechercher. Utilisez la zone de recherche pour rechercher les activités à ajouter à la liste. Pour obtenir une liste partielle des activités auditées, voir [Activités auditées.](search-the-audit-log-in-security-and-compliance.md#audited-activities) Laissez cette zone vide pour renvoyer les entrées de toutes les activités auditées.
  
   3. **Utilisateurs**.  Cliquez dans cette zone et commencez à taper le nom des utilisateurs pour afficher les résultats de la recherche. Les entrées du journal d’audit pour les activités sélectionnées effectuées par les utilisateurs que vous sélectionnez dans cette zone sont affichées dans la liste des résultats. Laissez cette zone vide pour renvoyer les entrées pour tous les utilisateurs (et les comptes de service) dans votre organisation.
  
   4. **Fichier, dossier ou site**. Tapez tout ou partie d’un nom de fichier ou de dossier pour rechercher l’activité liée au fichier de dossier qui contient le mot clé spécifié. Vous pouvez également spécifier l’URL d’un fichier ou d’un dossier. Si vous utilisez l’URL d’un fichier ou d’un dossier, assurez-vous que vous tapez le chemin d’accès à l’URL complète ou si vous tapez une partie de l’URL, n’incluez pas de caractères ou d’espaces spéciaux. Laissez cette zone vide pour renvoyer les entrées correspondant à tous les fichiers et dossiers dans votre organisation.

4. Cliquez **sur Rechercher** pour exécuter la recherche.

Une nouvelle page s’affiche et indique que la recherche du journal d’audit est en cours d’exécution. Lorsque la recherche est terminée, les enregistrements d’audit sont affichés sur la page. Cliquez sur un enregistrement pour afficher une page volante avec des propriétés détaillées.

Pour obtenir des instructions plus détaillées, consultez la recherche dans le journal [d’audit dans le centre de conformité.](search-the-audit-log-in-security-and-compliance.md)
