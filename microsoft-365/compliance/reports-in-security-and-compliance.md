---
title: Rapports dans le Centre de conformité et sécurité
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: overview
f1_keywords:
- ms.o365.cc.AuditingHelp
ms.service: O365-seccomp
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: 7acd33ce-1ec8-49fb-b625-43bac7b58c5a
description: Utilisez le Centre de sécurité & conformité pour obtenir différents rapports pour votre organisation SharePoint Online et Exchange Online, ainsi que Azure Active Directory rapports.
ms.openlocfilehash: 3e72ecab68ece31c44d99f85806492e788f4cd7c
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50926152"
---
# <a name="reports-in-the-security--compliance-center"></a>Rapports dans le Centre de conformité et sécurité

Vous pouvez utiliser la **page** Afficher les rapports dans le Centre de sécurité & conformité pour accéder rapidement aux rapports d’audit pour SharePoint Online et Exchange Online organisations. Vous pouvez également accéder Azure Active Directory rapports de connexion des utilisateurs (AD), aux rapports d’activité des utilisateurs et au journal d’audit Azure AD à partir de la page Afficher **les rapports.** Cela est dû au fait que votre abonnement Microsoft 365 payant inclut un abonnement gratuit à Microsoft Azure. La première fois que vous essayez d’accéder à ces rapports Azure, vous devez effectuer un processus d’inscription à une seule fois. 
  
> [!TIP]
> Pour afficher des rapports supplémentaires sur l’activité dans votre organisation, voir Rapports d’activité dans [Microsoft 365 d’administration.](../admin/activity-reports/activity-reports.md) 
  
 **Avant de commencer**
  
Vous avez besoin des autorisations suivantes pour afficher les rapports dans le Centre de sécurité & conformité.
  
- Le rôle Lecteur sécurité doit vous être attribué dans le Centre d’administration Exchange (EAC) pour afficher les rapports dans le Centre de sécurité & conformité. Par défaut, ce rôle est attribué aux groupes de rôles Gestion de l’organisation et Lecteur sécurité dans le EAC.
    
- Le rôle Gestion de la conformité View-Only DLP doit vous être attribué dans le Centre de sécurité & conformité pour afficher les rapports DLP dans le Centre de sécurité & et conformité. Par défaut, ce rôle est attribué aux groupes de rôles Administrateur de conformité, Gestion de l’organisation, Administrateur de la sécurité et Lecteur sécurité dans le Centre de sécurité & conformité.

- En outre, le rôle Destinataires View-Only'EAC doit vous être attribué pour afficher les rapports DLP dans le CEA. Par défaut, ce rôle est attribué aux groupes de rôles Gestion de la conformité, Gestion de l’organisation View-Only Gestion de l’organisation dans le EAC.
  
 **Pour ouvrir la page Afficher les rapports dans le Centre de sécurité & conformité :**
  
1. Accédez à [https://protection.office.com/#/viewreports](https://protection.office.com/#/viewreports).
    
2. Connectez-vous à l’aide des informations d’identification d’un compte d’utilisateur de votre organisation.
    
Dans la page **Afficher les rapports,** vous pouvez afficher les types de rapports suivants : 
  
- [Rapports d’audit](#auditing-reports)
- [Rapport de surveillance](#supervisory-review-report)
- [Rapports de protection contre la perte de données](#data-loss-prevention-reports)
    
## <a name="auditing-reports"></a>Rapports d’audit

Le tableau suivant décrit les rapports de la section **Audit** de la **page** Afficher les rapports dans le Centre de sécurité & conformité. 
  
|**Rapport**|**Description**|
|:-----|:-----|
|**rapport du journal d’audit** <br/> |Vous pouvez rechercher dans le journal d’audit les activités des utilisateurs et des administrateurs dans votre organisation. Le rapport contient les entrées de l’activité des utilisateurs et des administrateurs dans Exchange Online, SharePoint Online, OneDrive Entreprise et Azure Active Directory, qui est le service d’annuaire pour Office 365. Pour plus d’informations, [voir Rechercher dans le journal d’audit dans le Office 365](search-the-audit-log-in-security-and-compliance.md).  <br/> |
|**Rapports Azure AD** <br/> |Pour rechercher des activités de sign-in inhabituelles ou suspectes dans votre organisation, vous pouvez utiliser des rapports de Microsoft Azure. Vous pouvez également afficher les événements dans le journal d’audit Azure AD. Pour afficher les rapports dans Azure, cliquez simplement **sur Afficher les rapports Azure AD.** Pour plus d’informations, voir : <br/><br/>[Utilisez votre abonnement Azure Active Directory gratuit dans Office 365](use-your-free-azure-ad-subscription-in-office-365.md). <br/> [Afficher vos rapports d’accès et d’utilisation.](/azure/active-directory/reports-monitoring/overview-reports)  <br/> |
|**Rapports d’audit Exchange** <br/> | Vous pouvez utiliser la fonctionnalité d’audit dans Microsoft 365 pour suivre les modifications apportées à votre configuration Exchange Online par les administrateurs de votre organisation. Les modifications apportées à votre Exchange Online par un administrateur de centre de données Microsoft ou par un administrateur délégué sont également enregistrées. Pour Exchange Online, la journalisation d’audit de l’administrateur est activée par défaut, vous n’avez donc rien à faire pour l’activer. Exchange Online également la journalisation d’audit des boîtes aux lettres pour vous aider à suivre l’accès aux boîtes aux lettres par une personne autre que le propriétaire de la boîte aux lettres. Vous devez activer l’enregistrement d’audit des boîte aux lettres pour chaque boîte aux lettres dont vous souhaitez surveiller l’accès par une autre personne que son propriétaire.  <br/>  Pour l’enregistrement d’audit de l’administrateur et de la boîte aux lettres, vous pouvez exécuter des rapports d’audit pour afficher les entrées du journal d’audit. Vous pouvez également exporter des journaux d’audit de boîte aux lettres et d’administrateur qui vous sont envoyés dans un délai de 24 heures dans un fichier XML joint au message électronique. <br/><br/>Pour plus d’informations sur l’exportation des journaux d’audit, voir :  <br/><br/> [Exporter les journaux d’audit de boîte aux lettres](/exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs) <br/> [Afficher et exporter le journal d’audit de l’administrateur du centre de données](/exchange/security-and-compliance/exchange-auditing-reports/view-external-admin-audit-log) <br/> [Rechercher les modifications des groupes de rôles ou les journaux d’audit de l’administrateur](/exchange/security-and-compliance/exchange-auditing-reports/search-role-group-changes) <br/>   [Exchange rapports d’audit.](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)  <br/> |
   
## <a name="supervisory-review-report"></a>Rapport de surveillance

Avec le rapport de contrôle de surveillance, vous pouvez voir l’état de toutes les stratégies de contrôle de surveillance de votre organisation. Pour plus d’informations, voir Configurer des stratégies de [contrôle de surveillance pour votre organisation.](./communication-compliance-configure.md)
  
## <a name="data-loss-prevention-reports"></a>Rapports de protection contre la perte de données

Les rapports de protection contre la perte de données (DLP) contiennent des informations sur les stratégies et règles DLP appliquées au contenu qui contiennent des données sensibles dans votre organisation. Vous pouvez également configurer ce rapport pour afficher des informations sur les actions DLP basées sur votre stratégie et vos règles DLP. Pour plus d’informations, [voir le rapport sur la protection contre la perte de données.](view-the-dlp-reports.md)