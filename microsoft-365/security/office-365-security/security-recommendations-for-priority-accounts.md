---
title: Recommandations de sécurité pour les comptes prioritaires dans Microsoft 365, les comptes prioritaires, les comptes de priorité dans Office 365, les comptes de priorité dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- m365-security
- m365solution-overview
- m365solution-protecthve
- highpri
ms.custom: ''
description: Les administrateurs peuvent apprendre à élever les paramètres de sécurité et à utiliser des rapports, des alertes et des enquêtes pour les comptes prioritaires dans leurs organisations Microsoft 365.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 621f1e2f3048d6f013cf8e668de6b83a49b3d163
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68090484"
---
# <a name="security-recommendations-for-priority-accounts-in-microsoft-365"></a>Recommandations de sécurité pour les comptes prioritaires dans Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Tous les comptes d’utilisateurs n’ont pas accès aux mêmes informations d’entreprise. Certains comptes ont accès à des informations sensibles, telles que les données financières, les informations de développement de produits, l’accès des partenaires aux systèmes de build critiques, etc. En cas de compromission, les comptes qui ont accès à des informations hautement confidentielles constituent une menace sérieuse. Nous appelons ces types de _comptes prioritaires_. Les comptes prioritaires incluent (mais ne sont pas limités à) les chefs de la direction, les directeurs financiers, les directeurs financiers, les comptes d’administrateur d’infrastructure, les comptes système de build et bien plus encore.

Pour les attaquants, les attaques par hameçonnage ordinaires qui génèrent un filet aléatoire pour des utilisateurs ordinaires ou inconnus sont inefficaces. D’autre part, les attaques par _harponnage_ ou _de chasse à la baleine qui ciblent_ des comptes prioritaires sont très gratifiantes pour les attaquants. Par conséquent, les comptes prioritaires nécessitent une protection plus forte que la protection ordinaire pour empêcher toute compromission de compte.

Microsoft 365 et Microsoft Defender pour Office 365 contiennent plusieurs fonctionnalités clés qui fournissent des couches de sécurité supplémentaires pour vos comptes prioritaires. Cet article décrit ces fonctionnalités et comment les utiliser.

:::image type="content" source="../../media/security-recommendations-for-priority-users.png" alt-text="Résumé des recommandations de sécurité sous forme d’icône" lightbox="../../media/security-recommendations-for-priority-users.png":::

|Tâche|Tous les plans Office 365 Entreprise|Microsoft 365 E3|Microsoft 365 E5|
|---|:---:|:---:|:---:|
|[Augmenter la sécurité de connexion pour les comptes prioritaires](#increase-sign-in-security-for-priority-accounts)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Utiliser des stratégies de sécurité prédéfinies strictes pour les comptes prioritaires](#use-strict-preset-security-policies-for-priority-accounts)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Appliquer des balises utilisateur aux comptes prioritaires](#apply-user-tags-to-priority-accounts)|||![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Surveiller les comptes de priorité dans les alertes, les rapports et les détections](#monitor-priority-accounts-in-alerts-reports-and-detections)|||![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Former les utilisateurs](#train-users)|![Inclus.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../../media/d238e041-6854-4a78-9141-049224df0795.png)|

> [!NOTE]
> Pour plus d’informations sur la sécurisation des _comptes privilégiés_ (comptes d’administrateur), consultez [cette rubrique](/security/compass/critical-impact-accounts).

## <a name="increase-sign-in-security-for-priority-accounts"></a>Augmenter la sécurité de connexion pour les comptes prioritaires

Les comptes prioritaires nécessitent une sécurité de connexion accrue. Vous pouvez augmenter leur sécurité de connexion en exigeant une authentification multifacteur (MFA) et en désactivant les protocoles d’authentification hérités.

Pour obtenir des instructions, consultez [l’étape 1. Augmentez la sécurité de connexion pour les travailleurs distants avec l’authentification multifacteur](../../solutions/empower-people-to-work-remotely-secure-sign-in.md). Bien que cet article concerne les travailleurs distants, les mêmes concepts s’appliquent aux utilisateurs prioritaires.

**Remarque** : Nous vous recommandons vivement de désactiver globalement les protocoles d’authentification hérités pour tous les utilisateurs prioritaires, comme décrit dans l’article précédent. Si vos exigences métier vous empêchent de le faire, Exchange Online propose les contrôles suivants pour limiter l’étendue des protocoles d’authentification hérités :

- Vous pouvez utiliser des [stratégies d’authentification](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) et [des règles d’accès client](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules) dans Exchange Online pour bloquer ou autoriser l’authentification de base et les protocoles d’authentification hérités tels que POP3, IMAP4 et SMTP authentifié pour des utilisateurs spécifiques.

- Vous pouvez désactiver l’accès POP3 et IMAP4 sur des boîtes aux lettres individuelles. Vous pouvez désactiver smTP authentifié au niveau de l’organisation et l’activer sur des boîtes aux lettres spécifiques qui en ont encore besoin. Pour obtenir des instructions, consultez les articles suivants :
  - [Activer ou désactiver l’accès POP3 ou IMAP4 pour un utilisateur](/exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)
  - [Activer ou désactiver la soumission SMTP du client authentifié (SMTP AUTH)](/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission)

Il est également important de noter que l’authentification de base est en cours de dépréciation dans Exchange Online pour les services web Exchange (EWS), Exchange ActiveSync, POP3, IMAP4 et PowerShell distant. Pour plus d’informations, consultez ce [billet de blog](https://developer.microsoft.com/office/blogs/deferred-end-of-support-date-for-basic-authentication-in-exchange-online/).

## <a name="use-strict-preset-security-policies-for-priority-accounts"></a>Utiliser des stratégies de sécurité prédéfinies strictes pour les comptes prioritaires

Les utilisateurs prioritaires nécessitent des actions plus strictes pour les différentes protections disponibles dans Exchange Online Protection (EOP) et Defender pour Office 365.

Par exemple, au lieu de remettre des messages classés comme courrier indésirable au dossier Junk Email, vous devez mettre en quarantaine ces mêmes messages s’ils sont destinés aux comptes prioritaires.

Vous pouvez implémenter cette approche stricte pour les comptes prioritaires à l’aide du profil Strict dans les stratégies de sécurité prédéfinies.

Les stratégies de sécurité prédéfinies sont un emplacement pratique et central pour appliquer nos paramètres de stratégie stricts recommandés pour toutes les protections dans EOP et Defender pour Office 365. Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

Pour plus d’informations sur la façon dont les paramètres de stratégie stricts diffèrent des paramètres de stratégie par défaut et standard, consultez [Paramètres recommandés pour la sécurité EOP et Microsoft Defender pour Office 365](recommended-settings-for-eop-and-office365.md).

## <a name="apply-user-tags-to-priority-accounts"></a>Appliquer des balises utilisateur aux comptes prioritaires

Les balises utilisateur dans Microsoft Defender pour Office 365 Plan 2 (dans le cadre de Microsoft 365 E5 ou d’un abonnement de module complémentaire) permettent d’identifier et de classer rapidement des utilisateurs ou groupes d’utilisateurs spécifiques dans les rapports et les enquêtes sur les incidents.

**Les comptes de priorité** sont un type de balise utilisateur intégrée (appelée _balise système_) que vous pouvez utiliser pour identifier les incidents et les alertes qui impliquent des comptes de priorité. Pour plus d’informations sur les **comptes de priorité**, consultez [Gérer et surveiller les comptes de priorité](../../admin/setup/priority-accounts.md).

Vous pouvez également créer des balises personnalisées pour identifier et classer vos comptes prioritaires. Pour plus d’informations, consultez [balises utilisateur](user-tags.md). Vous pouvez gérer les **comptes de priorité** (balises système) dans la même interface que les balises utilisateur personnalisées.

## <a name="monitor-priority-accounts-in-alerts-reports-and-detections"></a>Surveiller les comptes de priorité dans les alertes, les rapports et les détections

Une fois que vous avez sécurisé et étiqueté vos utilisateurs prioritaires, vous pouvez utiliser les rapports, alertes et investigations disponibles dans EOP et Defender pour Office 365 pour identifier rapidement les incidents ou les détections qui impliquent des comptes prioritaires. Les fonctionnalités qui prennent en charge les balises utilisateur sont décrites dans le tableau suivant.

|Fonctionnalité|Description|
|---|---|
|Alertes|Les balises utilisateur des utilisateurs affectés sont visibles et disponibles sous forme de filtres sur la page **Alertes** du portail Microsoft 365 Defender. Pour plus d’informations, consultez [Affichage des alertes](../../compliance/alert-policies.md#view-alerts).|
|Explorer <p> Détections en temps réel|Dans **l’Explorateur** (Defender pour Office 365 Plan 2) ou **les détections en temps réel** (Defender pour Office 365 Plan 1), les balises utilisateur sont visibles dans la grille Email et le menu volant des détails Email. Les balises utilisateur sont également disponibles en tant que propriété filtrable. Pour plus d’informations, consultez  [Balises dans l’Explorateur](threat-explorer.md#tags-in-threat-explorer).|
|Vues de campagne|Les balises utilisateur sont l’une des nombreuses propriétés filtrables dans les vues de campagne dans Microsoft Defender pour Office 365 Plan 2. Pour plus d’informations, consultez [Vues de campagne](campaigns.md).|
|Rapport sur l’état de la protection contre les menaces|Dans pratiquement toutes les vues et tables de détails du **rapport d’état de la protection contre les menaces**, vous pouvez filtrer les résultats par **comptes de priorité**. Pour plus d’informations, consultez le [rapport d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report).|
|Email problèmes liés au rapport des comptes prioritaires|Le **rapport Email problèmes liés aux comptes prioritaires** dans le Centre d’administration Exchange (EAC) contient des informations sur les messages non remis et différés pour les **comptes prioritaires**. Pour plus d’informations, consultez [Email problèmes liés au rapport des comptes prioritaires](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report).|

## <a name="train-users"></a>Former les utilisateurs

La formation des utilisateurs avec des comptes prioritaires peut aider à faire gagner beaucoup de temps et de frustration à ces utilisateurs et à votre équipe chargée des opérations de sécurité. Les utilisateurs avertis sont moins susceptibles d’ouvrir des pièces jointes ou de cliquer sur des liens dans des messages électroniques douteux, et ils sont plus susceptibles d’éviter les sites web suspects.

Le [manuel de la campagne de cybersécurité](https://www.belfercenter.org/CyberPlaybook) de l’École Harvard Kennedy fournit d’excellents conseils pour établir une culture forte de la sensibilisation à la sécurité au sein de votre organisation, y compris la formation des utilisateurs pour identifier les attaques par hameçonnage.

Microsoft 365 fournit les ressources suivantes pour aider à informer les utilisateurs de votre organisation :

|Concept|Ressources|Description|
|---|---|---|
|Microsoft 365|[Parcours d’apprentissage personnalisables](/office365/customlearning/)|Ces ressources peuvent vous aider à mettre en place une formation pour les utilisateurs de votre organisation.|
|Sécurité Microsoft 365|[Module d’apprentissage : Sécuriser votre organisation avec une sécurité intégrée et intelligente à partir de Microsoft 365](/training/modules/security-with-microsoft-365)|Ce module vous permet de décrire comment les fonctionnalités de sécurité Microsoft 365 fonctionnent ensemble et d’articuler les avantages de ces fonctionnalités de sécurité.|
|Authentification multifacteur|[Vérification en deux étapes : quelle est la page de vérification supplémentaire ?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time)|Cet article aide les utilisateurs finaux à comprendre ce qu’est l’authentification multifacteur et pourquoi elle est utilisée auprès de votre organisation.|
|Formation à la simulation d'attaque|[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)|Exercice de simulation d'attaque dans Microsoft Defender pour Office 365 Plan 2 permet à l’administrateur de configurer, lancer et suivre des attaques par hameçonnage simulées contre des groupes d’utilisateurs spécifiques.|

En outre, Microsoft recommande aux utilisateurs d’effectuer les actions décrites dans cet article : [Protéger votre compte et vos appareils contre les pirates et les programmes malveillants](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6). Ces actions incluent :

- Utilisation de mots de passe forts
- Protection des appareils
- Activation des fonctionnalités de sécurité sur les PC Windows et Mac (pour les appareils non gérés)

## <a name="see-also"></a>Voir aussi

[Annonce de la protection prioritaire des comptes dans Microsoft Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/announcing-priority-account-protection-in-microsoft-defender-for/ba-p/1696385)
