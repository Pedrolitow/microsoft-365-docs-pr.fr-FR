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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: conceptual
ms.date: 07/27/2021
ms.custom: seo-marvel-apr2020
ms.reviewer: vippand
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1c046bf15cf3ccfbbbfb8969b0f0bc48db1ad4f5
ms.sourcegitcommit: 99817013bcb26b7ed051e011c8addb716cc91d8f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58349895"
---
# <a name="whats-new-in-microsoft-defender-for-office-365"></a>Nouveautés de Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cet article répertorie les nouvelles fonctionnalités de la dernière version de Microsoft Defender pour Office 365. Les fonctionnalités actuellement en prévisualisation sont notées avec **(prévisualisation).**

Pour en savoir plus, regardez [cette vidéo](https://www.youtube.com/watch?v=Tdz6KfruDGo&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=3).
> [!TIP]
> Vous n’avez pas encore Microsoft Defender Office 365 ? [Contactez les ventes pour démarrer une version d’essai.](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html)

## <a name="august-2021"></a>Août 2021

- [Révision de l’administrateur pour les messages](admin-review-reported-message.md)signalés : les administrateurs peuvent désormais renvoyer des messages de modèle aux utilisateurs finaux après avoir passé en revue les messages signalés. Les modèles peuvent être personnalisés pour votre organisation et basés sur le verdict de votre administrateur.
- Ajout d’autoriser dans la liste d’adresses client [autoriser/bloquer](manage-tenant-allows.md): les autoriser ne peuvent pas être ajoutés directement à la liste d’adresses client autoriser/bloquer, mais peuvent maintenant être si le message bloqué est envoyé dans le cadre du processus de soumission de l’administrateur. Selon le bloc qui s’est produit, une URL, un fichier et/ou une adresse d’expéditeur sont ajoutés à la liste d’adresses client autoriser/bloquer. Dans la plupart des cas, les autoriser sont ajoutés pour donner au système un peu de temps et l’autoriser naturellement si cela est justifié. Dans certains cas, Microsoft gère l’autoriser pour vous.

## <a name="july-2021"></a>Juillet 2021

- [Améliorations apportées à l’analyse du courrier électronique dans les enquêtes automatisées](email-analysis-investigations.md)
- [Remise avancée](configure-advanced-delivery.md): introduction d’une nouvelle fonctionnalité de configuration de la remise de simulations de hameçonnage tiers aux utilisateurs et de messages non filtrés aux boîtes aux lettres d’opération de sécurité.
- [Coffre Liens pour Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams)
- Nouvelles stratégies d’alerte pour les scénarios suivants : boîtes aux lettres compromises, hameçonnage de formulaires, messages malveillants remis en raison de remplacements et de l’arrondi zap
  - Activité suspecte de transfert d’e-mail
  - Utilisateur restreint au partage de formulaires et à la collecte de réponses
  - Formulaire bloqué en raison d’une tentative de hameçonnage potentielle
  - Formulaire marqué et confirmé comme hameçonnage
  - [Nouvelles stratégies d’alerte pour ZAP](../../compliance/new-defender-alert-policies.md)
- Les alertes Microsoft Defender pour Office 365 sont désormais intégrées dans Microsoft 365 Defender - Microsoft 365 Defender de la file d’attente des alertes unifiées et de la file d’attente des [alertes unifiées](../defender/investigate-alerts.md)
- [](user-tags.md) Les balises utilisateur sont désormais intégrées aux expériences d’alerte de Microsoft Defender pour Office 365, notamment : la file d’attente des alertes et les détails dans Office 365 Security & Compliance, et l’application de stratégies d’alerte personnalisées aux balises utilisateur pour créer des stratégies d’alerte ciblées. 
  - Les balises sont également disponibles dans la file d’attente des alertes unifiées dans le centre Microsoft 365 Defender (Microsoft Defender pour Office 365 Plan 2)


## <a name="june-2021"></a>Juin 2021

- Le nouveau premier contact conseil de sécurité dans les stratégies anti-hameçonnage. Cette conseil de sécurité s’affiche lorsque les destinataires reçoivent pour la première fois un message électronique d’un expéditeur ou ne reçoivent pas souvent de courriers électroniques d’un expéditeur. Pour plus d’informations sur ce paramètre et comment le configurer, consultez les articles suivants :
  - [Premier contact conseil de sécurité](set-up-anti-phishing-policies.md#first-contact-safety-tip)
  - [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md)
  - [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md)

## <a name="aprilmay-2021"></a>Avril/mai 2021

- [](mdo-email-entity-page.md)Page Entité de messagerie : vue unifiée à 360 degrés d’un e-mail avec des informations enrichies sur les menaces, l’authentification et les détections, les détails de détonation et une toute nouvelle expérience d’aperçu du courrier électronique.
- [Office 365 API](/office/office-365-management-api/office-365-management-activity-api-schema#email-message-events)de gestion : mises à jour de EmailEvents (RecordType 28) pour ajouter l’action de remise, les emplacements de remise d’origine et les derniers, ainsi que les détails de détection mis à jour.
- [Analyse des menaces](/microsoft-365/security/defender/threat-analytics)pour Defender pour Office 365 : affichez les acteurs des menaces actifs, les techniques courantes et les surfaces d’attaque, ainsi que les rapports complets des chercheurs Microsoft sur les campagnes en cours.

## <a name="februarymarch-2021"></a>Février/mars 2021

- Intégration de l’ID d’alerte (recherche à l’aide de l’ID d’alerte et Alert-Explorer navigation) dans les expériences [de recherche](threat-explorer.md)
- Augmentation des limites d’exportation des enregistrements de 9990 à 200 000 dans les expériences [de recherche](threat-explorer.md)
- Extension de la limite de rétention et de recherche des données de l’Explorateur (et des détections en temps réel) pour les clients d’essai de 7 (limite précédente) à 30 jours dans les expériences de [repérage](threat-explorer.md)
- Nouveaux pivots  de repérage appelés domaine emprunt d’identité et utilisateur dont l’identité est usurpée dans l’Explorateur (et détections en temps réel) pour rechercher des attaques d’emprunt d’identité contre des utilisateurs ou des domaines protégés.  Pour plus d’informations, voir [les détails.](threat-explorer.md#view-phishing-emails-sent-to-impersonated-users-and-domains) (Microsoft Defender pour Office 365 Plan 1 ou Plan 2)

## <a name="december-2020"></a>Décembre 2020

- [Sécurisé par défaut dans Office 365](secure-by-default.md)
- Améliorations de l’examen automatisé : alertes générales pour les enquêtes de courrier déclenchées manuellement, traitement des modifications de boîte aux lettres comme une catégorie d’entité distincte, suppression des actions de blocage d’URL redondantes et création de clusters de courrier sortant pour les enquêtes compromises par l’utilisateur.

## <a name="november-2020"></a>Novembre 2020

- Mises à jour des limites d’exportation dans le Centre de >'action > correction à partir de l’envoi du courrier électronique et du journal des actions (Defender for Office 365 Plan 2)

## <a name="septemberoctober-2020"></a>Septembre/Octobre 2020

- Nouveau premier contact conseil de sécurité le moment où les destinataires reçoivent pour la première fois un message électronique d’un expéditeur ou ne reçoivent pas souvent de courriers électroniques d’un expéditeur. Pour plus d’informations sur ce paramètre et comment le configurer à l’aide Exchange règles de flux de messagerie (également appelées règles de transport), voir [First contact conseil de sécurité](set-up-anti-phishing-policies.md#first-contact-safety-tip).
- [Vérifier vos stratégies à l’aide de l’Analyseur de configuration](configuration-analyzer-for-security-policies.md)
- Fonctionnalités étendues dans l’Explorateur de [menaces,](threat-explorer.md#new-features-in-threat-explorer-and-real-time-detections) y compris les utilisateurs les plus ciblés, les règles de transport et les connecteurs (defender pour les informations de Office 365 dans l’Explorateur de menaces [(le](threat-explorer.md) courrier électronique a été autorisé/bloqué par la stratégie client/utilisateur) (Defender pour Office 365 Plan 2)
- Surfacing URL threats in [Threat Explorer](threat-explorer.md#threats-in-urls) (malware, phish, spam, or none) (Defender for Office 365 Plan 2)
- [Améliorations apportées à l’Explorateur](threat-explorer.md#improvements-to-the-threat-hunting-experience-upcoming) de menaces d’expérience de recherche avec les mises à jour autour des menaces, des actions supplémentaires, des emplacements de remise et de la chronologie mise à jour (Defender pour Office 365 Plan 2)

## <a name="julyaugust-2020"></a>Juillet/août 2020

- [Améliorations de l’expérience de](threat-explorer.md#improvements-to-threat-hunting-experience) recherche (Microsoft Defender pour Office 365 Plan 1 ou Plan 2)
- [Appliquer facilement les paramètres recommandés à l’aide de stratégies de sécurité prédéfinées](preset-security-policies.md)

## <a name="marchapril-2020"></a>Mars/Avril 2020

- La possibilité de résoudre [les comptes d’utilisateur compromis à l’grâce d’un examen](address-compromised-users-quickly.md) et d’une réponse automatisés est désormais généralement disponible. (Microsoft Defender pour Office 365 Plan 2)

## <a name="januaryfebruary-2020"></a>Janvier/février 2020

- [Disponibilité générale des affichages campagne](campaigns.md) dans Microsoft Defender pour Office 365 (Microsoft Defender pour Office 365 Plan 2)
- Améliorations apportées à l’Explorateur de menaces pour [](investigate-malicious-email-that-was-delivered.md)permettre aux équipes d’opérations de sécurité de rechercher et de filtrer sur plusieurs champs lors de l’étude de la messagerie électronique : (Microsoft Defender pour Office 365 Plan 2) [](threat-explorer.md)
  - Emplacement de remise et actions spéciales
  - Direction (entrant, sortant ou intra-organisationnel)
  - Filtres NOT avancés (il s’agit d’options de filtrage avancées qui incluent ne contient pas, n’inclut pas, etc.)
  - Filtres de temps granulaires (jour, heure, demi-heure)

- Le widget **Incidents** est désormais le widget **Centre de l’action.** (Pour afficher vos widgets de sécurité dans le Centre de sécurité & conformité, consultez La gestion **des menaces** \> **Review**.) (Microsoft Defender pour Office 365 Plan 2)

- [Coffre documents en Microsoft 365](safe-docs.md) **(prévisualisation)**

## <a name="december-2019"></a>Décembre 2019

- [Exporter les données de clic d’URL](threat-explorer.md#new-features-in-threat-explorer-and-real-time-detections) pour l’analyse hors connexion (Microsoft Defender pour Office 365 Plan 1 ou Plan 2)

- [Utiliser les affichages campagne dans Microsoft Defender pour Office 365 **(prévisualisation)**](campaigns.md) (Microsoft Defender pour Office 365 Plan 2)

## <a name="november-2019"></a>Novembre 2019

- [Découvrez les nouvelles fonctionnalités de](address-compromised-users-quickly.md) détection et de réponse utilisateur compromises **(prévisualisation)**(Microsoft Defender pour Office 365 Plan 2)

## <a name="september-2019"></a>Septembre 2019

- [Utiliser des fonctionnalités automatisées](automated-investigation-response-office.md) d’examen et de réponse (Microsoft Defender pour Office 365 Plan 2)

- [Intégration à Microsoft Defender pour Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema) événements d’investigation et de réponse automatisés à l’aide de l’API activité de gestion Office 365 (Defender for Office 365 Plan 2)

- [Afficher les en-têtes de courrier électronique et télécharger](investigate-malicious-email-that-was-delivered.md) le corps de l’e-mail (Microsoft Defender pour Office 365 Plan 1 ou Plan 2)

## <a name="august-2019"></a>Août 2019

- [Afficher la chronologie du courrier](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email) électronique (Microsoft Defender pour Office 365 Plan 1 ou Plan 2)

## <a name="july-2019"></a>Juillet 2019

- [Vérifier l’action de remise et l’emplacement](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location) des messages électroniques (Microsoft Defender pour Office 365 Plan 1 ou 2)

## <a name="june-2019"></a>Juin 2019

- [Afficher les URL de hameçonnage et cliquer sur les](threat-explorer.md#view-phishing-url-and-click-verdict-data) données de verdict (Microsoft Defender pour Office 365 Plan 1 ou Plan 2)

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender pour Office 365 Plan 1 et Plan 2

Savez-vous que Microsoft Defender pour Office 365 est disponible dans deux plans ? [En savoir plus sur ce que chaque plan inclut.](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2)

## <a name="see-also"></a>Voir aussi

[Microsoft 365 feuille de route](https://www.microsoft.com/microsoft-365/roadmap)

[Description du service Microsoft Defender Office 365 service](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)
