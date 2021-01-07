---
title: Recommandations en matière de sécurité pour les comptes prioritaires dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.date: ''
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à élever les paramètres de sécurité et à utiliser des rapports, des alertes et des analyses pour les comptes prioritaires dans leurs organisations Microsoft 365.
ms.openlocfilehash: 9788131ea881a1cb3c36a60dfaac01ed5daf0901
ms.sourcegitcommit: 5ba0015c1554048f817fdfdc85359eee1368da64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "49769244"
---
# <a name="security-recommendations-for-priority-accounts-in-microsoft-365"></a>Recommandations en matière de sécurité pour les comptes prioritaires dans Microsoft 365

Que faire si vous avez reçu un message urgent d’un exécutif de votre organisation qui vous a demandé d’effectuer une opération ? Voulez-vous le faire ? La plupart des personnes se conforment à la demande.

Pour les attaquants, les attaques par hameçonnage ordinaires qui effectuent un net aléatoire pour obtenir les informations d’identification des utilisateurs inconnus ou aléatoires sont inefficaces. D’autre part, les attaques de _Spear Phishing_ ou de _baleine_ qui ciblent les utilisateurs dans des positions de puissance ou d’autorité sont bien plus satisfaisantes pour les attaquants. Si ces comptes de priorité sont compromis, l’agresseur peut accéder à des comptes dotés de fonctionnalités d’administration, financières, de produit ou même d’accès physique au sein de l’organisation.

Microsoft 365 et Microsoft Defender pour Office 365 contiennent de nombreuses fonctionnalités différentes qui peuvent vous aider à fournir des couches de sécurité supplémentaires pour vos comptes prioritaires. Les fonctionnalités disponibles et leur utilisation sont présentées dans cet article.

![Résumé des recommandations en matière de sécurité sous forme d’icône](../../media/security-recommendations-for-priority-users.png)

## <a name="increase-sign-in-security-for-priority-accounts"></a>Augmenter la sécurité de connexion pour les comptes prioritaires

Les comptes de priorité nécessitent une sécurité de connexion accrue. Vous pouvez augmenter leur sécurité de connexion en exigeant l’authentification multifacteur (MFA) et la désactivation des protocoles d’authentification hérités.

Pour obtenir des instructions, voir [Step 1. Renforcer la sécurité des utilisateurs distants avec MFA](https://docs.microsoft.com/microsoft-365/solutions/empower-people-to-work-remotely-secure-sign-in). Bien que cet article concerne les travailleurs distants, les mêmes concepts s’appliquent aux utilisateurs prioritaires.

**Remarques** :

- L’authentification de base est en cours d’utilisation dans Exchange Online pour les services Web Exchange (EWS), Exchange ActiveSync, POP3, IMAP4 et PowerShell à distance. Pour plus d’informations, consultez ce billet de [blog](https://developer.microsoft.com/office/blogs/deferred-end-of-support-date-for-basic-authentication-in-exchange-online/).

- Vous pouvez utiliser des [stratégies d’authentification](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) et des [règles d’accès client](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules) dans Exchange Online pour bloquer l’authentification de base et les protocoles d’authentification hérités, tels que POP3, IMAP4 et SMTP authentifié.

- Vous pouvez désactiver l’accès POP3 et IMAP4 sur des boîtes aux lettres individuelles. Vous pouvez désactiver SMTP authentifié au niveau de l’organisation et l’activer sur des boîtes aux lettres spécifiques qui le requièrent encore. Pour obtenir des instructions, consultez les rubriques suivantes :
  - [Activer ou désactiver l’accès POP3 ou IMAP4 pour un utilisateur](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)
  - [Activer ou désactiver l’envoi SMTP de client authentifié (authentification SMTP)](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission)

## <a name="use-strict-preset-security-policies-for-priority-accounts"></a>Utiliser des stratégies de sécurité prédéfinies rigoureuses pour les comptes prioritaires

Les utilisateurs prioritaires ont besoin d’actions plus rigoureuses pour les différentes protections disponibles dans Exchange Online Protection (EOP) et Defender pour Office 365.

Par exemple, au lieu de remettre les messages classés comme courriers indésirables dans le dossier courrier indésirable, vous devez mettre en quarantaine ces mêmes messages s’ils sont destinés à des comptes prioritaires.

Vous pouvez implémenter cette approche rigoureuse pour les comptes prioritaires en utilisant le profil strict dans les stratégies de sécurité prédéfinies.

Les stratégies de sécurité prédéfinies constituent un emplacement pratique et centralisé pour appliquer nos paramètres de stratégie stricts recommandés pour toutes les protections dans EOP et Defender pour Office 365. Pour plus d’informations, reportez-vous à la rubrique [stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

Pour plus d’informations sur la différence entre les paramètres de stratégie stricts et les paramètres de stratégie par défaut et standard, voir [Recommended Settings for EOP and Microsoft Defender for Office 365 Security](recommended-settings-for-eop-and-office365-atp.md).

## <a name="apply-user-tags-to-priority-accounts"></a>Appliquer les balises utilisateur aux comptes prioritaires

Les balises utilisateur de Microsoft Defender pour Office 365 plan 2 (dans le cadre de Microsoft 365 E5 ou d’un abonnement de complément) constituent un moyen d’identifier et de classer rapidement des utilisateurs ou des groupes d’utilisateurs spécifiques dans des rapports et des recherches d’incidents.

La fonctionnalité **comptes de priorité** est un type de balise utilisateur intégrée (appelée _balise système_) que vous pouvez utiliser pour identifier les incidents et les alertes qui impliquent des comptes prioritaires. Pour plus d’informations sur les **comptes de priorité**, consultez la rubrique [Manage and Monitor Priority Accounts](https://docs.microsoft.com/microsoft-365/admin/setup/priority-accounts).

Vous pouvez également créer des balises personnalisées pour identifier et classer vos comptes prioritaires. Pour plus d’informations, consultez la rubrique [User Tags](user-tags.md). Notez que vous pouvez gérer les **comptes de priorité** (balises système) dans la même interface que les balises utilisateur personnalisées.

## <a name="monitor-priority-accounts-in-alerts-reports-and-detections"></a>Surveiller les comptes prioritaires dans les alertes, les rapports et les détections

Une fois que vous avez sécurisé et identifié vos utilisateurs prioritaires, vous pouvez utiliser les rapports, alertes et enquêtes disponibles dans EOP et Defender pour Office 365 pour identifier rapidement les incidents ou les détections qui impliquent des comptes prioritaires. Les fonctionnalités qui prennent en charge les balises utilisateur sont décrites dans le tableau suivant.

<br>

****

|Fonctionnalité|Description|
|---|---|
|Alertes|Les balises utilisateur des utilisateurs concernés sont visibles et disponibles en tant que filtres sur la page **afficher les alertes** dans le centre de sécurité & conformité. Pour plus d’informations, consultez la rubrique [affichage des alertes](https://docs.microsoft.com/microsoft-365/compliance/alert-policies#viewing-alerts).|
|Threat Explorer <p> Détections en temps réel|Dans l' **Explorateur de menaces** (Microsoft Defender pour Office 365 plan 2) ou les **détections en temps réel** (microsoft Defender pour Office 365 plan 1), les balises utilisateur sont visibles dans l’affichage de grille du courrier électronique et dans la fenêtre mobile des détails du courrier électronique. Les balises utilisateur sont également disponibles en tant que propriété filtrable. Pour plus d’informations, consultez la rubrique  [balises dans l’Explorateur de menaces](threat-explorer.md#tags-in-threat-explorer).|
|Vues de campagne|Les balises utilisateur sont l’une des nombreuses propriétés filtrables dans les vues de campagne dans Microsoft Defender pour Office 365 plan 2. Pour plus d’informations, consultez la rubrique [vues de campagne](campaigns.md).|
|Rapport sur l’état de la protection contre les menaces|Dans presque toutes les vues et tableaux de détails du **rapport d’état de protection contre les menaces**, vous pouvez filtrer les résultats par **comptes prioritaires**. Pour plus d’informations, consultez la rubrique [Threat Protection Status Report](view-email-security-reports.md#threat-protection-status-report).|
|Rapports sur les problèmes de messagerie pour les comptes prioritaires|Le rapport **problèmes de messagerie pour les comptes prioritaires** dans le centre d’administration Exchange contient des informations sur les messages non remis et retardés pour les **comptes prioritaires**. Pour plus d’informations, consultez la rubrique [email issues for Priority Accounts Report](https://docs.microsoft.com/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report).|
|

## <a name="see-also"></a>Voir aussi

[Annonce de la protection des comptes prioritaires dans Microsoft Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/announcing-priority-account-protection-in-microsoft-defender-for/ba-p/1696385)
