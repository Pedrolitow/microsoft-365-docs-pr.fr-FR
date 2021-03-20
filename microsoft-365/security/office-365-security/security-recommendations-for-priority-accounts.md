---
title: Recommandations en matière de sécurité pour les comptes prioritaires dans Microsoft 365, comptes de priorité, comptes de priorité dans Office 365, comptes de priorité dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.date: ''
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-protecthve
description: Les administrateurs peuvent apprendre à élever les paramètres de sécurité et à utiliser des rapports, des alertes et des enquêtes pour les comptes prioritaires dans leurs organisations Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 48089ae21a0cfad90eaa0ee65915f71292092c2e
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50917309"
---
# <a name="security-recommendations-for-priority-accounts-in-microsoft-365"></a>Recommandations en matière de sécurité pour les comptes prioritaires dans Microsoft 365

Tous les comptes d’utilisateur n’ont pas accès aux mêmes informations d’entreprise. Certains comptes ont accès à des informations sensibles, telles que des données financières, des informations de développement de produits, l’accès des partenaires aux systèmes de build critiques, etc. S’ils sont compromis, les comptes qui ont accès à des informations hautement confidentielles constituent une menace grave. Nous appelons ces types de comptes _prioritaires._ Les comptes de priorité incluent (sans s’y limiter) les directeurs d’exploitation, les CSO, les cfo, les comptes d’administrateur d’infrastructure, les comptes système de build, etc.

Pour les attaquants, les attaques par hameçonnage ordinaires qui castent un réseau aléatoire pour des utilisateurs ordinaires ou inconnus sont inefficaces. En _revanche,_ les attaques  de harponnage ou de harponnage qui ciblent des comptes prioritaires sont très vantants pour les attaquants. Ainsi, les comptes prioritaires nécessitent une protection plus forte que l’ordinaire pour empêcher la compromission des comptes.

Microsoft 365 et Microsoft Defender pour Office 365 contiennent plusieurs fonctionnalités clés qui fournissent des couches de sécurité supplémentaires pour vos comptes prioritaires. Cet article décrit ces fonctionnalités et leur utilisation.

![Résumé des recommandations de sécurité sous forme d’icône](../../media/security-recommendations-for-priority-users.png)

****

|Tâche|Toutes les plans Office 365 Entreprise|Microsoft 365 E3|Microsoft 365 E5|
|---|:---:|:---:|:---:|
|[Renforcer la sécurité de la signature pour les comptes prioritaires](#increase-sign-in-security-for-priority-accounts)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Utiliser des stratégies de sécurité prédéfines strictes pour les comptes prioritaires](#use-strict-preset-security-policies-for-priority-accounts)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Appliquer des balises utilisateur à des comptes prioritaires](#apply-user-tags-to-priority-accounts)|||![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Surveiller les comptes prioritaires dans les alertes, les rapports et les détections](#monitor-priority-accounts-in-alerts-reports-and-detections)|||![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Former les utilisateurs](#train-users)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|

## <a name="increase-sign-in-security-for-priority-accounts"></a>Renforcer la sécurité de la signature pour les comptes prioritaires

Les comptes prioritaires nécessitent une sécurité accrue de la signature. Vous pouvez augmenter la sécurité de leur authentification en exigeant une authentification multifacteur (MFA) et en désactivant les protocoles d’authentification hérités.

Pour obtenir des instructions, [consultez l’étape 1. Renforcer la sécurité de la sign-in pour les travailleurs à distance avec l’fa MFA](../../solutions/empower-people-to-work-remotely-secure-sign-in.md). Bien que cet article porte sur les travailleurs à distance, les mêmes concepts s’appliquent aux utilisateurs prioritaires.

**Remarque**: nous vous recommandons vivement de désactiver globalement les protocoles d’authentification hérités pour tous les utilisateurs prioritaires, comme décrit dans l’article précédent. Si les besoins de votre entreprise vous en empêchent, Exchange Online propose les contrôles suivants pour limiter l’étendue des protocoles d’authentification hérités :

- Vous pouvez [](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) utiliser [](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules) des stratégies d’authentification et des règles d’accès client dans Exchange Online pour bloquer ou autoriser l’authentification de base et les protocoles d’authentification hérités tels que POP3, IMAP4 et SMTP authentifié pour des utilisateurs spécifiques.

- Vous pouvez désactiver l’accès POP3 et IMAP4 sur des boîtes aux lettres individuelles. Vous pouvez désactiver smTP authentifié au niveau de l’organisation et l’activer sur des boîtes aux lettres spécifiques qui en ont encore besoin. Pour obtenir des instructions, consultez les rubriques suivantes :
  - [Activer ou désactiver l’accès POP3 ou IMAP4 pour un utilisateur](/exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)
  - [Activer ou désactiver l’envoi SMTP de client authentifié (SMTP AUTH)](/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission)

Il est également intéressant de noter que l’authentification de base est en cours d’utilisation dans Exchange Online pour les services web Exchange (EWS), Exchange ActiveSync, POP3, IMAP4 et Remote PowerShell. Pour plus d’informations, voir ce [billet de blog.](https://developer.microsoft.com/office/blogs/deferred-end-of-support-date-for-basic-authentication-in-exchange-online/)

## <a name="use-strict-preset-security-policies-for-priority-accounts"></a>Utiliser des stratégies de sécurité prédéfines strictes pour les comptes prioritaires

Les utilisateurs prioritaires nécessitent des actions plus strictes pour les différentes protections disponibles dans Exchange Online Protection (EOP) et Defender pour Office 365.

Par exemple, au lieu de remettre des messages classés comme courrier indésirable dans le dossier Courrier indésirable, vous devez mettre en quarantaine ces mêmes messages s’ils sont destinés à des comptes prioritaires.

Vous pouvez implémenter cette approche rigoureuse pour les comptes prioritaires à l’aide du profil Strict dans les stratégies de sécurité prédéfines.

Les stratégies de sécurité prédéfinées sont un emplacement pratique et central pour appliquer nos paramètres de stratégie stricts recommandés pour toutes les protections dans EOP et Defender pour Office 365. Pour plus d’informations, voir Stratégies de sécurité [prédéfini dans EOP et Microsoft Defender pour Office 365.](preset-security-policies.md)

Pour plus d’informations sur la différence entre les paramètres de stratégie Strict et les paramètres de stratégie standard et par défaut, voir Paramètres recommandés pour EOP et Microsoft Defender pour la sécurité [Office 365.](recommended-settings-for-eop-and-office365-atp.md)

## <a name="apply-user-tags-to-priority-accounts"></a>Appliquer des balises utilisateur à des comptes prioritaires

Les balises utilisateur dans Microsoft Defender pour Office 365 Plan 2 (dans le cadre de Microsoft 365 E5 ou d’un abonnement à un module add-on) sont un moyen d’identifier et de classer rapidement des utilisateurs ou des groupes d’utilisateurs spécifiques dans des rapports et des enquêtes d’incident.

**Les comptes de priorité** sont un type de balise utilisateur intégrée (appelée balise _système)_ que vous pouvez utiliser pour identifier les incidents et les alertes impliquant des comptes prioritaires. Pour plus d’informations **sur les comptes prioritaires,** voir [Gérer et surveiller les comptes de priorité.](../../admin/setup/priority-accounts.md)

Vous pouvez également créer des balises personnalisées pour identifier et classer vos comptes prioritaires. Pour plus d’informations, voir [Balises utilisateur.](user-tags.md) Notez que vous pouvez gérer les **comptes de priorité (balises** système) dans la même interface que les balises utilisateur personnalisées.

## <a name="monitor-priority-accounts-in-alerts-reports-and-detections"></a>Surveiller les comptes prioritaires dans les alertes, les rapports et les détections

Après avoir sécurisé et identifié vos utilisateurs prioritaires, vous pouvez utiliser les rapports, alertes et enquêtes disponibles dans EOP et Defender pour Office 365 pour identifier rapidement les incidents ou les détections impliquant des comptes prioritaires. Les fonctionnalités qui la prise en charge des balises utilisateur sont décrites dans le tableau suivant.

<br>

****

|Fonctionnalité|Description|
|---|---|
|Alertes|Les balises utilisateur des utilisateurs concernés sont visibles et disponibles en tant que filtres dans la page Afficher les **alertes** dans le Centre de sécurité & conformité. Pour plus d’informations, voir [Affichage des alertes.](../../compliance/alert-policies.md#viewing-alerts)|
|Threat Explorer <p> Détections en temps réel|Dans l’Explorateur de menaces **(Microsoft** Defender pour Office 365 Plan 2) ou les **détections** en temps réel (Microsoft Defender pour Office 365 Plan 1), les balises utilisateur sont visibles dans l’affichage Grille courrier et le volant Détails du courrier électronique. Les balises utilisateur sont également disponibles en tant que propriété filtrable. Pour plus d’informations, [voir Balises dans l’Explorateur de menaces.](threat-explorer.md#tags-in-threat-explorer)|
|Vues de campagne|Les balises utilisateur sont l’une des nombreuses propriétés filtrables dans les affichages campagne dans Microsoft Defender pour Office 365 Plan 2. Pour plus d’informations, voir [Affichages de campagne.](campaigns.md)|
|Rapport sur l’état de la protection contre les menaces|Dans la quasi-ensemble des vues et des tableaux détaillés du rapport d’état de la **protection** contre les **menaces,** vous pouvez filtrer les résultats par compte de priorité. Pour plus d’informations, consultez [le rapport d’état de la protection contre les menaces.](view-email-security-reports.md#threat-protection-status-report)|
|Rapport sur les problèmes de messagerie pour le rapport des comptes prioritaires|Le rapport Problèmes de messagerie pour les comptes de priorité dans le Centre d’administration Exchange (EAC) contient des informations sur les messages non reçus et **différés** pour les comptes **prioritaires.** Pour plus d’informations, [consultez le rapport Problèmes de messagerie pour le rapport des comptes prioritaires.](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)|
|

## <a name="train-users"></a>Former les utilisateurs

La formation des utilisateurs avec des comptes prioritaires peut aider à gagner beaucoup de temps et de frustration à ces utilisateurs et à votre équipe des opérations de sécurité. Les utilisateurs expérimentés sont moins susceptibles d’ouvrir des pièces jointes ou de cliquer sur des liens dans des messages électroniques douteux, et ils sont plus susceptibles d’éviter les sites web suspects.

Le manuel de campagne de [cyber-sécurité](https://www.belfercenter.org/CyberPlaybook) de l’établissement d’un établissement scolaire de contrôle de la sécurité fournit d’excellents conseils pour établir une culture forte de sensibilisation à la sécurité au sein de votre organisation, notamment pour former les utilisateurs à l’identification des attaques par hameçonnage.

Microsoft 365 fournit les ressources suivantes pour aider à informer les utilisateurs de votre organisation :

<br>

****

|Concept|Ressources|Description|
|---|---|---|
|Microsoft 365|[Parcours d’apprentissage personnalisables](/office365/customlearning/)|Ces ressources peuvent vous aider à mettre en place une formation pour les utilisateurs de votre organisation.|
|Sécurité Microsoft 365|[Module d’apprentissage : sécuriser votre organisation avec une sécurité intégrée et intelligente à partir de Microsoft 365](/learn/modules/security-with-microsoft-365)|Ce module vous permet de décrire comment les fonctionnalités de sécurité Microsoft 365 fonctionnent ensemble et d’articuler les avantages de ces fonctionnalités de sécurité.|
|Authentification multifacteur|[Vérification en deux étapes : quelle est la page de vérification supplémentaire ?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time)|Cet article aide les utilisateurs finaux à comprendre ce qu’est l’authentification multifacteur et pourquoi elle est utilisée au niveau de votre organisation.|
|Formation à la simulation d’attaques|[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)|La formation sur la simulation d’attaques dans Microsoft Defender pour Office 365 Plan 2 permet aux administrateurs de configurer, de lancer et de suivre les attaques par hameçonnage simulées contre des groupes d’utilisateurs spécifiques.|

En outre, Microsoft recommande aux utilisateurs d’prendre les mesures décrites dans cet article : Protéger votre compte et vos appareils contre les pirates [informatiques et les programmes malveillants.](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6) Ces actions incluent :

- Utilisation de mots de passe forts
- Protection des appareils
- Activation des fonctionnalités de sécurité sur les PC Windows 10 et Mac (pour les appareils non utilisés)

## <a name="see-also"></a>Voir aussi

[Annonce de la protection des comptes prioritaires dans Microsoft Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/announcing-priority-account-protection-in-microsoft-defender-for/ba-p/1696385)