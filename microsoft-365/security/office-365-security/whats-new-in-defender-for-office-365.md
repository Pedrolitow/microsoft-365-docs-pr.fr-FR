---
title: Nouveautés de Microsoft Defender pour Office 365
description: Découvrez les nouvelles fonctionnalités disponibles dans la dernière version de Microsoft Defender pour Office 365.
keywords: nouveautés de Microsoft Defender pour Office 365, ga, généralement disponibles, fonctionnalités, disponibles, nouvelles
search.appverid: met150
ms.sitesec: library
ms.pagetype: security
f1.keywords: NOCSH
ms.author: tracyp
author: msfttracyp
ms.localizationpriority: medium
ms.date: 08/30/2022
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: conceptual
ms.custom: seo-marvel-apr2020
ms.reviewer: vippand
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 7a8efc09e296914307bfd8b8003c09eb8f25bada
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67671762"
---
# <a name="whats-new-in-microsoft-defender-for-office-365"></a>Nouveautés de Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**

- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cet article répertorie les nouvelles fonctionnalités de la dernière version de Microsoft Defender pour Office 365. Les fonctionnalités actuellement en préversion sont indiquées par **(préversion).**

Pour en savoir plus, regardez [cette vidéo](https://www.youtube.com/watch?v=Tdz6KfruDGo&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=3).

Pour plus d’informations sur les nouveautés des autres produits de sécurité Microsoft Defender, consultez :

- [Nouveautés de Microsoft 365 Defender](../defender/whats-new.md)
- [Nouveautés dans Microsoft Defender pour point de terminaison](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Nouveautés de Microsoft Defender pour Identity](/defender-for-identity/whats-new)
- [Nouveautés de Microsoft Defender for Cloud Apps](/cloud-app-security/release-notes)

## <a name="september-2022"></a>Septembre 2022

**Redirection automatique du Centre de sécurité et de conformité Office 365 vers le portail Microsoft 365 Defender :** la redirection automatique commence pour les utilisateurs qui accèdent aux solutions de sécurité dans Office 365 Centre de sécurité et de conformité (protection.office.com) vers les solutions appropriées dans portail Microsoft 365 Defender (security.microsoft.com). Cela s’applique à tous les flux de travail de sécurité tels que les alertes, la gestion des menaces et les rapports. 
- URL de redirection :
    - Environnement GCC :
        - À partir de Office 365 URL du Centre de conformité & de sécurité : protection.office.com
        - Pour Microsoft 365 Defender URL : security.microsoft.com
    - environnement GCC-High :
        - À partir de Office 365 URL du Centre de sécurité & conformité : scc.office365.us
        - Pour Microsoft 365 Defender URL : security.microsoft.us
    - Environnement DoD :
        - À partir de Office 365 URL du Centre de conformité & de sécurité : scc.protection.apps.mil
        - Pour Microsoft 365 Defender URL : security.apps.mil
- Les éléments du Centre de sécurité et de conformité Office 365 qui ne sont pas liés à la sécurité ne sont pas redirigés vers Microsoft 365 Defender. Pour plus d’informations sur la redirection des solutions de conformité vers le Centre de conformité Microsoft 365, consultez la publication 244886 du Centre de messages. 
- Il s’agit d’une continuation de [Microsoft 365 Defender offre une expérience XDR unifiée aux clients GCC, GCC High et DoD - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/public-sector-blog/microsoft-365-defender-delivers-unified-xdr-experience-to-gcc/ba-p/3263702), annoncé en mars 2022.
- Cette modification permet aux utilisateurs d’afficher et de gérer des solutions de sécurité Microsoft 365 Defender supplémentaires dans un portail.
- Ce changement affecte tous les clients qui utilisent le Centre de sécurité et de conformité Office 365 (protection.office.com), y compris Microsoft Defender pour Office (Plan 1 ou Plan 2), Microsoft 365 E3 /E5, Office 365 E3/E5 et Exchange Online Protection. Pour obtenir la liste complète, consultez [Security & Compliance Center - Service Descriptions | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)
- Cette modification a un impact sur tous les utilisateurs qui se connectent au portail de sécurité et de conformité Office 365 (protection.office.com), y compris les équipes de sécurité et les utilisateurs finaux qui accèdent à l’expérience de mise en quarantaine Email, dans la **mise en quarantaine** de révision du **portail** >  >  Microsoft Defender.
- La redirection est activée par défaut et a un impact sur tous les utilisateurs du locataire.
- Les administrateurs généraux et les administrateurs de sécurité peuvent activer ou désactiver la redirection dans le portail Microsoft 365 Defender en accédant à **Paramètres** >  Email &**la redirection du portail** de **collaboration** >  et en basculant la redirection.

## <a name="july-2022"></a>Juillet 2022

- [Introduction d’actions dans la page d’entité de messagerie](mdo-email-entity-page.md) : les administrateurs peuvent effectuer des actions préventives, correctives et d’envoi à partir de la page d’entité de messagerie.

## <a name="june-2022"></a>Juin 2022

- [Utilisez le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les expéditeurs usurpés dans le portail soumissions : créez des entrées](allow-block-email-spoof.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-spoofed-senders-in-the-submissions-portal) d’expéditeur usurpées autorisées à l’aide de la liste d’autorisation/de blocage du locataire.

- [L’emprunt d’identité permet d’utiliser la soumission d’administrateur](allow-block-email-spoof.md#about-impersonated-domains-or-senders) : l’ajout autorise les expéditeurs usurpés d’identité à l’aide de la page Soumissions dans Microsoft 365 Defender.

- [Afficher la soumission administrateur convertie à partir de la soumission de l’utilisateur](admin-submission.md#convert-user-reported-messages-from-the-custom-mailbox-into-an-admin-submission) : configurez la boîte aux lettres personnalisée pour intercepter les messages signalés par l’utilisateur sans envoyer les messages à Microsoft à des fins d’analyse.

- [Afficher l’alerte associée pour les soumissions d’utilisateurs et d’administrateurs](admin-submission.md#view-associated-alert-for-user-and-admin-email-submissions) : affichez l’alerte correspondante pour chaque message de hameçonnage signalé par l’utilisateur et l’envoi d’e-mail d’administrateur.

- [Protection d’emprunt d’identité configurable pour les utilisateurs et domaines personnalisés et étendue accrue dans les stratégies prédéfinies](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/configurable-impersonation-protection-and-scope-for-preset/ba-p/3294459) :
  - (Choisissez de) Appliquez des stratégies Strict/Standard prédéfinies à l’ensemble de l’organisation et évitez de sélectionner des utilisateurs, des groupes ou des domaines de destinataires spécifiques, ce qui sécurise tous les utilisateurs destinataires de votre organisation.
  - Configurez les paramètres de protection de l’emprunt d’identité pour les utilisateurs personnalisés et les domaines personnalisés dans les stratégies Strict/Standard prédéfinies et protégez automatiquement vos utilisateurs ciblés et le domaine ciblé contre les attaques d’emprunt d’identité.

- [Simplification de l’expérience de quarantaine (deuxième partie) dans Microsoft 365 Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/simplifying-the-quarantine-experience-part-two/ba-p/3354687) : met en évidence des fonctionnalités supplémentaires pour rendre l’expérience de quarantaine encore plus facile à utiliser.

## <a name="april-2022"></a>Avril 2022

- [Présentation de la table URLClickEvents dans Microsoft 365 Defender Repérage avancé](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/introducing-the-urlclickevents-table-in-advanced-hunting-with/ba-p/3295096) : présentation de la table UrlClickEvents dans la chasse avancée avec Microsoft Defender pour Office 365.
- [Améliorations manuelles de la correction des e-mails](/microsoft-365/security/office-365-security/remediate-malicious-email-delivered-office-365) : ajout d’actions manuelles de vidage de messagerie effectuées dans Microsoft Defender pour Office 365 au Centre d’action unifié Microsoft 365 Defender (M365D) à l’aide d’une nouvelle enquête axée sur les actions.
- [Introduction d’une protection différenciée pour les comptes prioritaires dans Microsoft Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/introducing-differentiated-protection-for-priority-accounts-in/ba-p/3283838) : introduction de la disponibilité générale de la protection différenciée pour les comptes prioritaires.

## <a name="march-2022"></a>Mars 2022

- [Simplification de l’expérience de soumission dans Microsoft Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/streamlining-the-submissions-experience-in-microsoft-defender/ba-p/3152080) : présentation du nouveau processus de soumission unifié et rationalisé pour simplifier votre expérience.

## <a name="january-2022"></a>Janvier 2022

- [Mises à jour des expériences de chasse et d’investigation pour Microsoft Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/updated-hunting-and-investigation-experiences-for-microsoft/ba-p/3002015) : présentation du panneau de synthèse des e-mails pour les expériences dans Defender pour Office 365, ainsi que des mises à jour de l’expérience pour l’Explorateur de menaces et les détections en temps réel.

## <a name="october-2021"></a>Octobre 2021

- [Amélioration DKIM de remise avancée](configure-advanced-delivery.md) : ajout de la prise en charge de l’entrée de domaine DKIM dans le cadre de la configuration de simulation d’hameçonnage tierce.
- [Sécuriser par défaut](secure-by-default.md) : étendu sécurisé par défaut pour les règles de flux de messagerie Exchange (également appelées règles de transport).

## <a name="september-2021"></a>Septembre 2021

- [Amélioration de l’expérience de création de rapports dans Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/improving-the-reporting-experience-in-microsoft-defender-for/ba-p/2760898)
- [Stratégies de quarantaine](quarantine-policies.md) : les administrateurs peuvent configurer un contrôle granulaire pour l’accès des destinataires aux messages mis en quarantaine et personnaliser les notifications de courrier indésirable de l’utilisateur final.
  - [Vidéo de l’expérience d’administrateur](https://youtu.be/vnar4HowfpY)
  - [Vidéo de l’expérience de l’utilisateur final](https://youtu.be/s-vozLO43rI)
  - D’autres nouvelles fonctionnalités à venir à l’expérience de quarantaine sont décrites dans ce billet de blog : [Simplifier l’expérience de quarantaine](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/simplifying-the-quarantine-experience/ba-p/2676388).
- La redirection du portail par défaut commence, redirigeant les utilisateurs de La sécurité & conformité vers Microsoft 365 Defender<https://security.microsoft.com>. Pour plus d’informations, consultez : [Redirection de comptes depuis Office 365 Centre de sécurité & conformité vers Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-security-mdo-redirection)

## <a name="august-2021"></a>Août 2021

- [Administration examiner les messages signalés](admin-review-reported-message.md) : les administrateurs peuvent désormais renvoyer des messages modèles aux utilisateurs finaux après avoir examiné les messages signalés. Les modèles peuvent être personnalisés pour votre organisation et en fonction du verdict de votre administrateur.
- Ou peut désormais ajouter des entrées d’autorisation à la liste d’autorisation/de blocage du locataire si le message bloqué a été envoyé dans le cadre du processus de soumission de l’administrateur. Selon la nature du bloc, l’URL, le fichier et/ou l’autorisation de l’expéditeur envoyé sont ajoutés à la liste d’autorisations/de blocs du locataire. Dans la plupart des cas, les autorisations sont ajoutées pour donner au système un certain temps et l’autoriser naturellement si nécessaire. Dans certains cas, Microsoft gère l’autorisation pour vous. Pour plus d’informations, consultez l’article suivant :
  - [Utiliser le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les URL dans le portail Soumissions](allow-block-urls.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-urls-in-the-submissions-portal)
  - [Utiliser le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les fichiers dans le portail Soumissions](allow-block-files.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-files-in-the-submissions-portal)
  - [Utilisez le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les domaines et les adresses e-mail dans le portail Soumissions](allow-block-email-spoof.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-domains-and-email-addresses-in-the-submissions-portal)

## <a name="july-2021"></a>Juillet 2021

- [améliorations de l’analyse Email dans les enquêtes automatisées](email-analysis-investigations.md)
- [Livraison avancée](configure-advanced-delivery.md) : introduction d’une nouvelle fonctionnalité de configuration de la remise de simulations d’hameçonnage tierces aux utilisateurs et de messages non filtrés dans les boîtes aux lettres d’opération de sécurité.
- [Liens sécurisés pour Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams)
- Nouvelles stratégies d’alerte pour les scénarios suivants : boîtes aux lettres compromises, hameçonnage de formulaires, courriers malveillants remis en raison de remplacements et arrondi à ZAP
  - Activité suspecte de transfert d’e-mail
  - L’utilisateur ne peut pas partager de formulaires et collecter des réponses.
  - Formulaire bloqué en raison d’une tentative d’hameçonnage potentielle
  - Formulaire marqué d'un indicateur et confirmé comme hameçonnage
  - [Nouvelles stratégies d’alerte pour ZAP](../../compliance/new-defender-alert-policies.md)
- Microsoft Defender pour Office 365 alertes sont désormais intégrées dans Microsoft 365 Defender : [Microsoft 365 Defender file d’attente d’alertes unifiées et file d’attente d’alertes unifiées](../defender/investigate-alerts.md)
- [Les balises utilisateur](user-tags.md) sont désormais intégrées à Microsoft Defender pour Office 365 expériences d’alerte, notamment : la file d’attente des alertes et les détails dans Office 365 Sécurité & Conformité, et l’étendue des stratégies d’alerte personnalisées aux balises utilisateur pour créer des stratégies d’alerte ciblées.
  - Les balises sont également disponibles dans la file d’attente des alertes unifiées dans le portail Microsoft 365 Defender (Microsoft Defender pour Office 365 Plan 2)

## <a name="june-2021"></a>Juin 2021

- Nouveau paramètre de conseil de sécurité du premier contact dans les stratégies anti-hameçonnage. Ce conseil de sécurité s’affiche lorsque les destinataires reçoivent pour la première fois un e-mail d’un expéditeur ou qu’ils ne reçoivent pas souvent d’e-mail d’un expéditeur. Pour plus d’informations sur ce paramètre et la façon de le configurer, consultez les articles suivants :
  - [Premier conseil de sécurité de contact](set-up-anti-phishing-policies.md#first-contact-safety-tip)
  - [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md)
  - [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md)

## <a name="aprilmay-2021"></a>Avril/mai 2021

- [Email page d’entité](mdo-email-entity-page.md) : vue unifiée à 360 degrés d’un e-mail avec des informations enrichies sur les menaces, l’authentification et les détections, les détails de la détonation et une toute nouvelle expérience d’aperçu de l’e-mail.
- [API de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#email-message-events) : Mises à jour à EmailEvents (RecordType 28) pour ajouter l’action de remise, les emplacements de remise d’origine et les derniers, ainsi que les détails de détection mis à jour.
- [Analyse des menaces pour Defender pour Office 365](/microsoft-365/security/defender/threat-analytics) : affichez les acteurs actifs des menaces, les techniques populaires et les surfaces d’attaque, ainsi que les rapports détaillés des chercheurs Microsoft sur les campagnes en cours.

## <a name="februarymarch-2021"></a>février/mars 2021

- Intégration de l’ID d’alerte (recherche à l’aide de l’ID d’alerte et de la navigation Alert-Explorer) dans les [expériences de chasse](threat-explorer.md)
- Augmentation des limites d’exportation des enregistrements de 9990 à 200 000 dans les expériences de [chasse](threat-explorer.md)
- Extension de la conservation des données de l’Explorateur (et des détections en temps réel) et de la limite de recherche pour les locataires d’essai de 7 (limite précédente) à 30 jours dans les [expériences de chasse](threat-explorer.md)
- Nouveaux tableaux croisés dynamiques de chasse appelés **domaine emprunté** et **utilisateur emprunt d’identité** dans l’Explorateur (et détections en temps réel) pour rechercher des attaques d’emprunt d’identité contre des utilisateurs ou domaines protégés. Pour plus d’informations, consultez [les détails](threat-explorer.md#view-phishing-emails-sent-to-impersonated-users-and-domains). (Microsoft Defender pour Office 365 Plan 1 ou Plan 2)

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender pour Office 365 Plan 1 et Plan 2

Saviez-vous que Microsoft Defender pour Office 365 est disponible dans deux plans ? [En savoir plus sur ce que chaque plan inclut](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="see-also"></a>Voir aussi

- [Feuille de route microsoft 365](https://www.microsoft.com/microsoft-365/roadmap)
- [description du service Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)
