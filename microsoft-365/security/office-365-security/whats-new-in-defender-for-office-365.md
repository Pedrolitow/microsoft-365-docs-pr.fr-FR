---
title: Nouveautés de Microsoft Defender pour Office 365
description: Découvrez les nouvelles fonctionnalités disponibles dans la dernière version de Microsoft Defender pour Office 365.
keywords: nouveautés de Microsoft Defender pour Office 365, ga, généralement disponibles, fonctionnalités, disponibles, nouvelles
search.appverid: met150
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: conceptual
ms.date: 12/03/2021
ms.custom: seo-marvel-apr2020
ms.reviewer: vippand
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 30ee5d69db08dc4471bf6aa59558a934734e2f54
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2021
ms.locfileid: "61302433"
---
# <a name="whats-new-in-microsoft-defender-for-office-365"></a>Nouveautés de Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à :**

- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cet article répertorie les nouvelles fonctionnalités de la dernière version de Microsoft Defender pour Office 365. Les fonctionnalités actuellement en prévisualisation sont notées avec **(prévisualisation).**

Pour en savoir plus, regardez [cette vidéo](https://www.youtube.com/watch?v=Tdz6KfruDGo&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=3).

> [!TIP]
> Vous n’avez pas encore Microsoft Defender Office 365 ? [Contactez les ventes pour démarrer une version d’essai.](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html)

Pour plus d’informations sur les nouveautés des autres produits de sécurité Microsoft Defender, voir :

- [Nouveautés de Microsoft 365 Defender](../defender/whats-new.md)
- [Nouveautés dans Microsoft Defender pour point de terminaison](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Nouveautés de Microsoft Defender pour l’identité](/defender-for-identity/whats-new)
- [Nouveautés de la Microsoft Cloud App Security](/cloud-app-security/release-notes)


## <a name="decemberjanuary-2021"></a>Décembre/janvier 2021

- Expériences de repérage et d’investigation mises à jour pour Microsoft Defender pour [Office 365 :](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/updated-hunting-and-investigation-experiences-for-microsoft/ba-p/3002015)présentation du panneau de synthèse des e-mails pour les expériences dans Defender pour Office 365, ainsi que des mises à jour de l’expérience pour l’Explorateur de menaces et les détections en temps réel.


## <a name="october-2021"></a>Octobre 2021

- [Amélioration avancée de la distribution DKIM](configure-advanced-delivery.md): prise en charge supplémentaire de l’entrée de domaine DKIM dans le cadre de la configuration de simulation de hameçonnage tierce.
- [Sécurisé par défaut :](secure-by-default.md)sécurisé étendu par défaut Exchange règles de flux de messagerie (également appelées règles de transport).

## <a name="september-2021"></a>Septembre 2021

- [Amélioration de l’expérience de rapport dans Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/improving-the-reporting-experience-in-microsoft-defender-for/ba-p/2760898)
- [Stratégies de mise](quarantine-policies.md)en quarantaine : les administrateurs peuvent configurer un contrôle granulaire pour l’accès des destinataires aux messages mis en quarantaine et personnaliser les notifications de courrier indésirable à l’utilisateur final.
  - [Vidéo de l’expérience de l’administrateur](https://youtu.be/vnar4HowfpY)
  - [Vidéo de l’expérience de l’utilisateur final](https://youtu.be/s-vozLO43rI)
  - D’autres nouvelles fonctionnalités mises en quarantaine sont décrites dans ce billet de blog : Simplification de l’expérience de mise [en quarantaine.](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/simplifying-the-quarantine-experience/ba-p/2676388)
- La redirection du portail commence par défaut, redirigeant les utilisateurs de la sécurité & conformité vers Microsoft 365 Defender <https://security.microsoft.com> . Pour plus d’informations à ce sujet, voir : [Redirection](/microsoft-365/security/defender/microsoft-365-security-mdo-redirection) des comptes du Centre Office 365 sécurité et conformité vers Microsoft 365 Defender

## <a name="august-2021"></a>Août 2021

- [Révision de l’administrateur pour les messages](admin-review-reported-message.md)signalés : les administrateurs peuvent désormais renvoyer des messages de modèle aux utilisateurs finaux après avoir passé en revue les messages signalés. Les modèles peuvent être personnalisés pour votre organisation et basés sur le verdict de votre administrateur.
- [Ajouter des allows](manage-tenant-allows.md)dans la liste d’adresses client autoriser/bloquer : vous pouvez désormais ajouter des entrées d’autoriser à la liste d’adresses client autoriser/bloquer si le message bloqué a été envoyé dans le cadre du processus de soumission de l’administrateur. Selon la nature du bloc, l’URL envoyée, le fichier et/ou l’expéditeur sont ajoutés à la liste d’adresses client autoriser/bloquer. Dans la plupart des cas, les autoriser sont ajoutés pour donner au système un peu de temps et l’autoriser naturellement si cela est justifié. Dans certains cas, Microsoft gère l’autoriser pour vous.

## <a name="july-2021"></a>Juillet 2021

- [Améliorations apportées à l’analyse du courrier électronique dans les enquêtes automatisées](email-analysis-investigations.md)
- [Remise avancée](configure-advanced-delivery.md): introduction d’une nouvelle fonctionnalité de configuration de la remise de simulations de hameçonnage tiers aux utilisateurs et de messages non filtrés aux boîtes aux lettres d’opération de sécurité.
- [Coffre liens pour Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams)
- Nouvelles stratégies d’alerte pour les scénarios suivants : boîtes aux lettres compromises, hameçonnage de formulaires, messages malveillants remis en raison de remplacements et de l’arrondi zap
  - Activité suspecte de transfert d’e-mail
  - L’utilisateur ne peut pas partager de formulaires et collecter des réponses.
  - Formulaire bloqué en raison d’une tentative d’hameçonnage potentielle
  - Formulaire marqué d'un indicateur et confirmé comme hameçonnage
  - [Nouvelles stratégies d’alerte pour ZAP](../../compliance/new-defender-alert-policies.md)
- Les alertes Microsoft Defender pour Office 365 sont désormais intégrées dans Microsoft 365 Defender - Microsoft 365 Defender de la file d’attente des alertes unifiées et de la file d’attente des [alertes unifiées](../defender/investigate-alerts.md)
- [](user-tags.md) Les balises utilisateur sont désormais intégrées aux expériences d’alerte de Microsoft Defender pour Office 365, notamment : la file d’attente des alertes et les détails dans Office 365 Security & Compliance, et l’application de stratégies d’alerte personnalisées aux balises utilisateur pour créer des stratégies d’alerte ciblées.
  - Les balises sont également disponibles dans la file d’attente des alertes unifiées du portail Microsoft 365 Defender (Microsoft Defender pour Office 365 Plan 2)

## <a name="june-2021"></a>Juin 2021

- Le nouveau premier contact conseil de sécurité dans les stratégies anti-hameçonnage. Cette conseil de sécurité s’affiche lorsque les destinataires reçoivent pour la première fois un message électronique d’un expéditeur ou ne reçoivent pas souvent de courrier d’un expéditeur. Pour plus d’informations sur ce paramètre et comment le configurer, consultez les articles suivants :
  - [Premier contact conseil de sécurité](set-up-anti-phishing-policies.md#first-contact-safety-tip)
  - [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md)
  - [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md)

## <a name="aprilmay-2021"></a>Avril/mai 2021

- [](mdo-email-entity-page.md)Page Entité de messagerie : vue unifiée à 360 degrés d’un e-mail avec des informations enrichies sur les menaces, l’authentification et les détections, les détails de détonation et une toute nouvelle expérience d’aperçu du courrier électronique.
- [Office 365 API](/office/office-365-management-api/office-365-management-activity-api-schema#email-message-events)de gestion : mises à jour de EmailEvents (RecordType 28) pour ajouter l’action de remise, les emplacements de remise d’origine et les derniers, ainsi que les détails de détection mis à jour.
- [Analyse des menaces](/microsoft-365/security/defender/threat-analytics)pour Defender pour Office 365 : afficher les acteurs des menaces actifs, les techniques courantes et les surfaces d’attaque, ainsi que les rapports complets de chercheurs Microsoft sur les campagnes en cours.

## <a name="februarymarch-2021"></a>Février/mars 2021

- Intégration de l’ID d’alerte (recherche à l’aide de l’ID d’alerte et Alert-Explorer navigation) dans les expériences [de recherche](threat-explorer.md)
- Augmentation des limites d’exportation des enregistrements de 9990 à 200 000 dans les expériences [de chasse](threat-explorer.md)
- Extension de la limite de rétention et de recherche des données de l’Explorateur (et des détections en temps réel) pour les clients d’essai de 7 (limite précédente) à 30 jours dans les expériences de [repérage](threat-explorer.md)
- Nouveaux pivots  de repérage appelés domaine emprunt d’identité et utilisateur dont l’identité est usurpée dans l’Explorateur (et détections en temps réel) pour rechercher des attaques d’emprunt d’identité contre des utilisateurs ou des domaines protégés.  Pour plus d’informations, voir [les détails.](threat-explorer.md#view-phishing-emails-sent-to-impersonated-users-and-domains) (Microsoft Defender pour Office 365 Plan 1 ou Plan 2)


## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender pour Office 365 Plan 1 et Plan 2

Savez-vous que Microsoft Defender pour Office 365 est disponible dans deux plans ? [En savoir plus sur ce que chaque plan inclut.](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2)

## <a name="see-also"></a>Voir aussi

[Microsoft 365 feuille de route](https://www.microsoft.com/microsoft-365/roadmap)

[Description du service Microsoft Defender Office 365 service](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)
