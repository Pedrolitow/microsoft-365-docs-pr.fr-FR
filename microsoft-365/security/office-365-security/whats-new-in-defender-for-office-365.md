---
title: Nouveautés de Microsoft Defender pour Office 365
description: Découvrez les nouvelles fonctionnalités disponibles dans la dernière version de Microsoft Defender pour Office 365.
keywords: nouveautés de Microsoft Defender pour Office 365, disponibilité générale, fonctionnalités, disponible, nouveau
search.appverid: met150
ms.sitesec: library
ms.pagetype: security
f1.keywords: NOCSH
ms.author: tracyp
author: msfttracyp
ms.localizationpriority: medium
ms.date: 09/20/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365initiative-defender-office365
ms.topic: conceptual
ms.custom: seo-marvel-apr2020
ms.reviewer: vippand
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 5fd3435be3d0ec64f8d501cc6957578dbe4c2458
ms.sourcegitcommit: a250d043a2e42ecbc7b86147468d1660af5a6ba7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68672821"
---
# <a name="whats-new-in-microsoft-defender-for-office-365"></a>Nouveautés de Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**

- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cet article répertorie les nouvelles fonctionnalités de la dernière version de Microsoft Defender pour Office 365. Les fonctionnalités actuellement en préversion sont indiquées avec **(préversion).**

Pour en savoir plus, regardez [cette vidéo](https://www.youtube.com/watch?v=Tdz6KfruDGo&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=3).

Pour plus d’informations sur les nouveautés des autres produits de sécurité Microsoft Defender, consultez :

- [Nouveautés de Microsoft 365 Defender](../defender/whats-new.md)
- [Nouveautés dans Microsoft Defender pour point de terminaison](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Nouveautés de Microsoft Defender pour Identity](/defender-for-identity/whats-new)
- [Nouveautés de Microsoft Defender for Cloud Apps](/cloud-app-security/release-notes)

## <a name="october-2022"></a>Octobre 2022

- **[Gérez vos permis et blocs dans la liste verte/bloquée du locataire](manage-tenant-allow-block-list.md) :**
  - Avec **autoriser la gestion de l’expiration** (actuellement en préversion privée), si Microsoft n’a pas appris de l’autorisation, Microsoft étendra automatiquement le délai d’expiration des permis, qui expireront bientôt, de 30 jours pour empêcher les e-mails légitimes d’être à nouveau mis en quarantaine ou indésirables.
  - Les clients dans les environnements cloud du secteur public pourront désormais créer des entrées d’autorisation et de blocage pour les URL et les pièces jointes dans la liste verte/bloquée du locataire à l’aide de l’URL de l’administrateur et des envois de pièces jointes par e-mail. Les données envoyées via l’expérience de soumission ne quitteront pas le locataire client, répondant ainsi aux engagements de résidence des données pour les clients cloud du secteur public.
- **Amélioration des alertes de clic d’URL :**
  - Avec le nouveau scénario de recherche arrière, l’alerte « Un clic d’URL potentiellement malveillant a été détecté » inclut désormais tous les clics au cours des _dernières 48 heures_ (pour les e-mails) à partir du moment où le verdict de l’URL malveillante est identifié. 

## <a name="september-2022"></a>Septembre 2022

**Redirection automatique du Centre de sécurité et de conformité Office 365 vers Microsoft 365 Defender portail :** la redirection automatique commence pour les utilisateurs qui accèdent aux solutions de sécurité dans Office 365 Centre de sécurité et de conformité (protection.office.com) vers les solutions appropriées dans portail Microsoft 365 Defender (security.microsoft.com). Il s’agit de tous les workflows de sécurité tels que : alertes, gestion des menaces et rapports. 
- URL de redirection :
    - Environnement GCC :
        - À partir de l’URL Office 365 Security & Compliance Center : protection.office.com
        - Pour Microsoft 365 Defender URL : security.microsoft.com
    - environnement GCC-High :
        - À partir de l’URL du Centre de conformité Office 365 Security & : scc.office365.us
        - Pour Microsoft 365 Defender URL : security.microsoft.us
    - Environnement DoD :
        - À partir de l’URL Office 365 Security & Compliance Center : scc.protection.apps.mil
        - Pour Microsoft 365 Defender URL : security.apps.mil
- Les éléments du Centre de sécurité et de conformité Office 365 qui ne sont pas liés à la sécurité ne sont pas redirigés vers Microsoft 365 Defender. Pour la redirection des solutions de conformité vers le Centre de conformité Microsoft 365, consultez la publication du Centre de messages 244886. 
- Il s’agit d’une continuation de [Microsoft 365 Defender offre une expérience XDR unifiée aux clients gcc, GCC High et DoD , Microsoft Tech Community](https://techcommunity.microsoft.com/t5/public-sector-blog/microsoft-365-defender-delivers-unified-xdr-experience-to-gcc/ba-p/3263702), annoncée en mars 2022.
- Cette modification permet aux utilisateurs d’afficher et de gérer des solutions de sécurité Microsoft 365 Defender supplémentaires dans un portail.
- Cette modification affecte tous les clients qui utilisent le Centre de sécurité et de conformité Office 365 (protection.office.com), y compris Microsoft Defender pour Office (plan 1 ou plan 2), Microsoft 365 E3/E5, Office 365 E3/E5 et Exchange Online Protection. Pour obtenir la liste complète, consultez [Security & Compliance Center - Service Descriptions | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)
- Cette modification affecte tous les utilisateurs qui se connectent au portail Office 365 sécurité et conformité (protection.office.com), y compris les équipes de sécurité et les utilisateurs finaux qui accèdent à l’expérience de mise en quarantaine Email, sur le **portail** >  Microsoft Defender **Examiner** >  la **quarantaine**.
- La redirection est activée par défaut et affecte tous les utilisateurs du locataire.
- Les administrateurs généraux et les administrateurs de la sécurité peuvent activer ou désactiver la redirection dans le portail Microsoft 365 Defender en accédant à **Paramètres** >  Email &**redirection du portail** **de collaboration** >  et en basculant la redirection.
- **Protection intégrée** : profil qui permet un niveau de base de protection des liens fiables et des pièces jointes fiables activé par défaut pour tous les clients Defender pour Office 365. Pour en savoir plus sur cette nouvelle stratégie et l’ordre de priorité, consultez [Stratégies de sécurité prédéfinies](preset-security-policies.md) et pour en savoir plus sur les contrôles de liens fiables et de pièces jointes fiables définis, consultez [Paramètres des pièces jointes fiables](recommended-settings-for-eop-and-office365.md#safe-attachments-settings) et [paramètres des liens fiables](recommended-settings-for-eop-and-office365.md#safe-links-settings).
- **Le niveau de plainte en bloc** est désormais disponible dans la table EmailEvents de la chasse avancée avec des valeurs BCL numériques comprises entre 0 et 9. Un score BCL plus élevé indique que les messages en bloc sont plus susceptibles de générer des plaintes et sont plus susceptibles d’être du courrier indésirable.

## <a name="july-2022"></a>Juillet 2022

- [Présentation d’actions dans la page d’entité de messagerie](mdo-email-entity-page.md) : les administrateurs peuvent effectuer des actions préventives, correctives et de soumission à partir de la page d’entité de messagerie.

## <a name="june-2022"></a>Juin 2022

- [Utilisez le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les expéditeurs usurpés dans le portail Soumissions](allow-block-email-spoof.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-spoofed-senders-in-the-submissions-portal) : Créez des entrées d’expéditeur usurpées autorisées à l’aide de la liste verte/bloquée du locataire.

- [L’emprunt d’identité autorise l’utilisation de la soumission par l’administrateur](allow-block-email-spoof.md#about-impersonated-domains-or-senders) : Ajouter autorise les expéditeurs emprunts d’identité à l’aide de la page Soumissions dans Microsoft 365 Defender.

- [Afficher la soumission d’administrateur convertie à partir de la soumission de l’utilisateur](admin-submission.md#convert-user-reported-messages-from-the-custom-mailbox-into-an-admin-submission) : configurez la boîte aux lettres personnalisée pour intercepter les messages signalés par l’utilisateur sans envoyer les messages à Microsoft à des fins d’analyse.

- [Afficher l’alerte associée pour les soumissions d’utilisateurs et d’administrateurs](admin-submission.md#view-associated-alert-for-user-and-admin-email-submissions) : affichez l’alerte correspondante pour chaque message d’hameçonnage signalé par l’utilisateur et l’envoi d’e-mail administrateur.

- [Utilisateurs et domaines personnalisés configurables de protection contre l’emprunt d’identité et étendue accrue dans les stratégies prédéfinies](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/configurable-impersonation-protection-and-scope-for-preset/ba-p/3294459) :
  - (Choisir vers) Appliquez des stratégies prédéfinies strictes/standard à l’ensemble de l’organisation et évitez les tracas liés à la sélection d’utilisateurs, de groupes ou de domaines destinataires spécifiques, ce qui sécurise tous les utilisateurs destinataires de votre organisation.
  - Configurez les paramètres de protection contre l’emprunt d’identité pour les utilisateurs personnalisés et les domaines personnalisés dans les stratégies prédéfinies Strict/Standard et protégez automatiquement vos utilisateurs ciblés et votre domaine ciblé contre les attaques d’emprunt d’identité.

- [Simplification de l’expérience de quarantaine (deuxième partie) dans Microsoft 365 Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/simplifying-the-quarantine-experience-part-two/ba-p/3354687) : met en évidence des fonctionnalités supplémentaires pour rendre l’expérience de quarantaine encore plus facile à utiliser.

- [Présentation de la protection différenciée pour les comptes prioritaires dans Microsoft Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/introducing-differentiated-protection-for-priority-accounts-in/ba-p/3283838) : Présentation de la disponibilité GCC, GCC-H et DoD de la protection différenciée pour les comptes prioritaires.

## <a name="april-2022"></a>Avril 2022

- [Présentation de la table URLClickEvents dans Microsoft 365 Defender Repérage avancé](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/introducing-the-urlclickevents-table-in-advanced-hunting-with/ba-p/3295096) : Présentation de la table UrlClickEvents dans la chasse avancée avec Microsoft Defender pour Office 365.
- Améliorations apportées à la [correction manuelle des e-mails](/microsoft-365/security/office-365-security/remediate-malicious-email-delivered-office-365) : Ajout d’actions de vidage manuel des e-mails effectuées dans Microsoft Defender pour Office 365 dans le Centre de notifications unifié Microsoft 365 Defender (M365D) à l’aide d’une nouvelle investigation axée sur les actions.
- [Introduction de la protection différenciée pour les comptes prioritaires dans Microsoft Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/introducing-differentiated-protection-for-priority-accounts-in/ba-p/3283838) : Présentation de la disponibilité générale de la protection différenciée pour les comptes prioritaires.

## <a name="march-2022"></a>Mars 2022

- [Simplification de l’expérience de soumission dans Microsoft Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/streamlining-the-submissions-experience-in-microsoft-defender/ba-p/3152080) : présentation du nouveau processus de soumission unifié et simplifié pour simplifier votre expérience.

## <a name="january-2022"></a>Janvier 2022

- [Mises à jour des expériences de chasse et d’investigation pour Microsoft Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/updated-hunting-and-investigation-experiences-for-microsoft/ba-p/3002015) : présentation du panneau récapitulatif des e-mails pour les expériences dans Defender pour Office 365, ainsi que des mises à jour de l’expérience pour l’Explorateur de menaces et les détections en temps réel.

## <a name="october-2021"></a>Octobre 2021

- [Amélioration avancée de DKIM de livraison](configure-advanced-delivery.md) : ajout de la prise en charge de l’entrée de domaine DKIM dans le cadre de la configuration de simulation d’hameçonnage tierce.
- [Sécurisé par défaut](secure-by-default.md) : secure by default extended pour les règles de flux de messagerie Exchange (également appelées règles de transport).

## <a name="september-2021"></a>Septembre 2021

- [Amélioration de l’expérience de création de rapports dans Defender pour Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/improving-the-reporting-experience-in-microsoft-defender-for/ba-p/2760898)
- [Stratégies de mise en quarantaine](quarantine-policies.md) : les administrateurs peuvent configurer un contrôle granulaire pour l’accès des destinataires aux messages mis en quarantaine et personnaliser les notifications de courrier indésirable des utilisateurs finaux.
  - [Vidéo de l’expérience de l’administrateur](https://youtu.be/vnar4HowfpY)
  - [Vidéo de l’expérience de l’utilisateur final](https://youtu.be/s-vozLO43rI)
  - D’autres nouvelles fonctionnalités de l’expérience de quarantaine sont décrites dans ce billet de blog : [Simplification de l’expérience de quarantaine](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/simplifying-the-quarantine-experience/ba-p/2676388).
- La redirection du portail par défaut commence, redirigeant les utilisateurs de Security & Compliance vers Microsoft 365 Defender <https://security.microsoft.com>. Pour plus d’informations à ce sujet, consultez [: Redirection de comptes à partir du Centre de conformité Office 365 Security & vers Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-security-mdo-redirection)

## <a name="august-2021"></a>Août 2021

- [Administration révision des messages signalés](admin-review-reported-message.md) : les administrateurs peuvent désormais renvoyer des messages avec modèle aux utilisateurs finaux après avoir examiné les messages signalés. Les modèles peuvent être personnalisés pour votre organisation et en fonction du verdict de votre administrateur.
- ou peut maintenant ajouter des entrées d’autorisation à la liste verte/bloquée du locataire si le message bloqué a été envoyé dans le cadre du processus de soumission de l’administrateur. Selon la nature du bloc, l’URL, le fichier et/ou l’autorisation de l’expéditeur envoyés sont ajoutés à la liste verte/bloquée du locataire. Dans la plupart des cas, les autorisations sont ajoutées pour donner au système un certain temps et le laisser naturellement si nécessaire. Dans certains cas, Microsoft gère l’autorisation pour vous. Pour plus d’informations, consultez l’article suivant :
  - [Utiliser le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les URL dans le portail soumissions](allow-block-urls.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-urls-in-the-submissions-portal)
  - [Utiliser le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les fichiers dans le portail soumissions](allow-block-files.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-files-in-the-submissions-portal)
  - [Utiliser le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les domaines et les adresses e-mail dans le portail soumissions](allow-block-email-spoof.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-domains-and-email-addresses-in-the-submissions-portal)

## <a name="july-2021"></a>Juillet 2021

- [Email améliorations de l’analyse dans les enquêtes automatisées](email-analysis-investigations.md)
- [Remise avancée](configure-advanced-delivery.md) : introduction d’une nouvelle fonctionnalité pour la configuration de la remise de simulations d’hameçonnage tierces aux utilisateurs et aux messages non filtrés vers des boîtes aux lettres d’opérations de sécurité.
- [Liens fiables pour Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams)
- Nouvelles stratégies d’alerte pour les scénarios suivants : boîtes aux lettres compromises, hameçonnage de formulaires, courriers malveillants remis en raison de substitutions et arrondissement zap
  - Activité suspecte de transfert d’e-mail
  - L’utilisateur ne peut pas partager de formulaires et collecter des réponses.
  - Formulaire bloqué en raison d’une tentative d’hameçonnage potentielle
  - Formulaire marqué d'un indicateur et confirmé comme hameçonnage
  - [Nouvelles stratégies d’alerte pour ZAP](../../compliance/new-defender-alert-policies.md)
- les alertes Microsoft Defender pour Office 365 sont désormais intégrées à Microsoft 365 Defender : [Microsoft 365 Defender file d’attente d’alertes unifiées et file d’attente d’alertes unifiées](../defender/investigate-alerts.md)
- [Les étiquettes utilisateur](user-tags.md) sont désormais intégrées à Microsoft Defender pour Office 365 expériences d’alerte, notamment : la file d’attente des alertes et les détails dans Office 365 Sécurité & Conformité, ainsi que des stratégies d’alerte personnalisées pour les étiquettes utilisateur pour créer des stratégies d’alerte ciblées.
  - Les balises sont également disponibles dans la file d’attente des alertes unifiées du portail Microsoft 365 Defender (Microsoft Defender pour Office 365 Plan 2)

## <a name="june-2021"></a>Juin 2021

- Nouveau paramètre de conseil de sécurité de premier contact dans les stratégies anti-hameçonnage. Ce conseil de sécurité s’affiche lorsque les destinataires reçoivent pour la première fois un e-mail d’un expéditeur ou ne reçoivent pas souvent d’e-mail d’un expéditeur. Pour plus d’informations sur ce paramètre et sur la façon de le configurer, consultez les articles suivants :
  - [Conseil de sécurité du premier contact](set-up-anti-phishing-policies.md#first-contact-safety-tip)
  - [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md)
  - [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md)

## <a name="aprilmay-2021"></a>Avril/mai 2021

- [Email page d’entité](mdo-email-entity-page.md) : vue unifiée à 360 degrés d’un e-mail avec des informations enrichies sur les menaces, l’authentification et les détections, les détails de la détonation et une toute nouvelle expérience d’aperçu des e-mails.
- [API de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#email-message-events) : Mises à jour à EmailEvents (RecordType 28) pour ajouter l’action de remise, les emplacements de remise d’origine et les derniers et les détails de détection mis à jour.
- [Analyse des menaces pour Defender pour Office 365](/microsoft-365/security/defender/threat-analytics) : affichez les acteurs des menaces actifs, les techniques populaires et les surfaces d’attaque, ainsi que les rapports complets des chercheurs Microsoft sur les campagnes en cours.

## <a name="februarymarch-2021"></a>Février/mars 2021

- Intégration de l’ID d’alerte (recherche à l’aide de l’ID d’alerte et de la navigation Alert-Explorer) dans les [expériences de chasse](threat-explorer.md)
- Augmentation des limites pour l’exportation d’enregistrements de 9990 à 200 000 dans les [expériences de chasse](threat-explorer.md)
- Extension de la limite de rétention et de recherche des données de l’Explorateur (et des détections en temps réel) pour les locataires d’essai de 7 (limite précédente) à 30 jours dans les [expériences de chasse](threat-explorer.md)
- Nouveaux tableaux croisés dynamiques de chasse appelés **Domaine** emprunt d’identité et Utilisateur emprunt **d’identité** dans l’Explorateur (et détections en temps réel) pour rechercher des attaques d’emprunt d’identité contre des utilisateurs ou des domaines protégés. Pour plus d’informations, consultez [les détails](threat-explorer.md#view-phishing-emails-sent-to-impersonated-users-and-domains). (Microsoft Defender pour Office 365 Plan 1 ou Plan 2)

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender pour Office 365 Plan 1 et Plan 2

Saviez-vous que Microsoft Defender pour Office 365 est disponible dans deux plans? [En savoir plus sur les éléments inclus dans chaque plan](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="see-also"></a>Voir aussi

- [Feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap)
- [description du service Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)
