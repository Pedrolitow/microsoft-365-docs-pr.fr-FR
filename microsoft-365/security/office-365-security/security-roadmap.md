---
title: Feuille de route de sécurité Microsoft 365 - Principales priorités
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 08/20/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
ms.assetid: 28c86a1c-e4dd-4aad-a2a6-c768a21cb352
description: Principales recommandations de l’équipe de cybersécurité de Microsoft pour implémenter des fonctionnalités de sécurité pour protéger votre environnement Microsoft 365.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: ed554f008b55ee0c5441c25bfedc7db79cd538f1
ms.sourcegitcommit: ecc04b5b8f84b34255a2d5e90b5ab596af0d16c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67497244"
---
# <a name="security-roadmap---top-priorities-for-the-first-30-days-90-days-and-beyond"></a>Feuille de route de sécurité - Principales priorités pour les 30 premiers jours, 90 jours et au-delà

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

Cet article contient les principales recommandations de l’équipe de cybersécurité de Microsoft pour implémenter des fonctionnalités de sécurité afin de protéger votre environnement Microsoft 365. Cet article est adapté d’une session Microsoft Ignite — [Sécuriser Microsoft 365 comme un professionnel de la cybersécurité : Priorités principales pour les 30 premiers jours, 90 jours et au-delà](https://www.youtube.com/watch?v=luignzNyR-o). Cette session a été développée et présentée par Mark Simos et Matt Kemelhar, Architectes de cybersécurité d’entreprise.

Contenu de cet article :

- [Résultats de la feuille de route](security-roadmap.md#Roadmap)
- [30 jours — de puissantes victoires rapides](security-roadmap.md#Thirdaydays)
- [90 jours — protections améliorées](security-roadmap.md#Ninetydays)
- [Au-delà](security-roadmap.md#Beyond)

## <a name="roadmap-outcomes"></a>Résultats de la feuille de route
<a name="Roadmap"> </a>

Ces recommandations de feuille de route sont réparties en trois phases dans un ordre logique avec les objectifs suivants.

|Intervalle de temps|Résultats|
|---|---|
|30 jours|Configuration rapide : <ul><li>Protections d’administration de base.</li><li>Journalisation et analytique.</li><li>Protections d’identité de base.</li></ul> <p> Configuration du locataire. <p> Préparer les parties prenantes.|
|90 jours|Protections avancées : <ul><li>Administration comptes.</li><li>Comptes de données et d’utilisateurs.</li></ul> <p> Visibilité de la conformité, des menaces et des besoins des utilisateurs. <p> Adaptez et implémentez des stratégies et des protections par défaut.|
|Au-delà|Ajustez et affinez les stratégies et contrôles clés. <p> Étendez les protections aux dépendances locales. <p> S’intégrer aux processus métier et de sécurité (juridique, insider threat, etc.).|

## <a name="30-days--powerful-quick-wins"></a>30 jours — de puissantes victoires rapides
<a name="Thirdaydays"> </a>

Ces tâches peuvent être accomplies rapidement et ont un faible impact sur les utilisateurs.

|Zone|Tâches|
|---|---|
|Gestion de la sécurité|<ul><li>Vérifiez le degré de sécurisation et prenez note de votre score actuel (<https://security.microsoft.com/securescore>).</li><li>Activez la journalisation d’audit pour Office 365. Consultez [Rechercher dans le journal d’audit](../../compliance/search-the-audit-log-in-security-and-compliance.md).</li><li>[Configurez Microsoft 365 pour renforcer la sécurité](tenant-wide-setup-for-increased-security.md).</li><li>Passez régulièrement en revue les tableaux de bord et les rapports dans le portail Microsoft 365 Defender et Defender for Cloud Apps.</li></ul>|
|Protection contre les menaces|[Connectez Microsoft 365 à Microsoft Defender for Cloud Apps](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) pour commencer la surveillance à l’aide des stratégies de détection des menaces par défaut pour les comportements anormaux. La création d’une base de référence pour la détection des anomalies prend sept jours. <p>  Implémenter la protection pour les comptes d’administrateur :<ul><li>Utilisez des comptes d’administrateur dédiés pour l’activité d’administrateur.</li><li>Appliquer l’authentification multifacteur (MFA) pour les comptes d’administrateur.</li><li>Utilisez un [appareil Windows hautement sécurisé](/windows-hardware/design/device-experiences/oem-highly-secure) pour l’activité de l’administrateur.</li></ul>|
|Gestion des identités et des accès|<ul><li>[Activez Azure Active Directory Identity Protection](/azure/active-directory/active-directory-identityprotection-enable).</li><li>Pour les environnements d’identité fédérés, appliquez la sécurité du compte (longueur du mot de passe, âge, complexité, etc.).</li></ul>|
|Protection des informations|Passez en revue les exemples de recommandations de protection des informations. La protection des informations nécessite une coordination au sein de votre organisation. Commencez à utiliser ces ressources :<ul><li>[Protection des informations Office 365 pour le RGPD](/compliance/regulatory/gdpr)</li><li>[Configurer Teams avec trois niveaux de protection](../../solutions/configure-teams-three-tiers-protection.md) (notamment le partage, la classification, la protection contre la perte de données Microsoft Purview et Azure Information Protection)</li></ul>|

## <a name="90-days--enhanced-protections"></a>90 jours — protections améliorées
<a name="Ninetydays"> </a>

Ces tâches prennent un peu plus de temps à planifier et à implémenter, mais augmentent considérablement votre posture de sécurité.

|Zone|Tâche|
|---|---|
|Gestion de la sécurité|<ul><li>Vérifiez le degré de sécurisation pour les actions recommandées pour votre environnement (<https://security.microsoft.com/securescore>).</li><li>Passez régulièrement en revue les tableaux de bord et les rapports dans le portail Microsoft 365 Defender, defender pour les applications cloud et les outils SIEM.</li><li>Recherchez et implémentez des mises à jour logicielles.</li><li>Effectuez des simulations d’attaque pour le harponnage, la pulvérisation de mots de passe et les attaques par mot de passe par force brute à l’aide [de Exercice de simulation d'attaque](attack-simulation-training.md) (inclus avec [Office 365 Threat Intelligence](office-365-ti.md).</li><li>Recherchez le partage des risques en examinant les rapports intégrés dans Defender pour Cloud Apps (sous l’onglet Examiner).</li><li>Vérifiez [le Gestionnaire de conformité](../../compliance/compliance-manager.md) pour vérifier l’état des réglementations qui s’appliquent à votre organisation (par exemple, RGPD, NIST 800-171).</li></ul>|
|Protection contre les menaces|Implémentez des protections améliorées pour les comptes d’administrateur : <ul><li>Configurez [des stations de travail à accès privilégié](/security/compass/privileged-access-devices) (PAW) pour l’activité d’administrateur.</li><li>Configurez [azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).</li><li>Configurez un outil SIEM (Security Information and Event Management) pour collecter des données de journalisation à partir de Office 365, Defender pour Cloud Apps et d’autres services, notamment AD FS. Le journal d’audit stocke les données pendant seulement 90 jours. La capture de ces données dans l’outil SIEM vous permet de stocker des données pendant une période plus longue.</li></ul>|
|Gestion des identités et des accès|<ul><li>Activez et appliquez l’authentification multifacteur pour tous les utilisateurs.</li><li>Implémentez un ensemble [d’accès conditionnel et de stratégies associées](microsoft-365-policies-configurations.md).</li></ul>|
|Protection des informations| Adapter et implémenter des stratégies de protection des informations. Ces ressources incluent des exemples : <ul><li>[Protection des informations Office 365 pour le RGPD](/compliance/regulatory/gdpr)</li><li>[Configurer Teams avec trois niveaux de protection](../../solutions/configure-teams-three-tiers-protection.md)</li></ul> <p> Utilisez des stratégies de protection contre la perte de données et des outils de surveillance dans Microsoft Purview pour les données stockées dans Microsoft 365 (au lieu de Defender pour Cloud Apps). <p> Utilisez Defender pour Cloud Apps avec Microsoft 365 pour les fonctionnalités avancées d’alerte (autres que la protection contre la perte de données).|

## <a name="beyond"></a>Au-delà
<a name="Beyond"> </a>

Il s’agit de mesures de sécurité importantes qui s’appuient sur les travaux précédents.

|Zone|Tâche|
|---|---|
|Gestion de la sécurité|<ul><li>Continuez à planifier les actions suivantes à l’aide du degré de sécurisation (<https://security.microsoft.com/securescore>).</li><li>Passez régulièrement en revue les tableaux de bord et les rapports dans le portail Microsoft 365 Defender, defender pour les applications cloud et les outils SIEM.</li><li>Continuez à rechercher et à implémenter des mises à jour logicielles.</li><li>Intégrez eDiscovery à vos processus juridiques et de réponse aux menaces.</li></ul>|
|Protection contre les menaces|<ul><li>[Implémentez l’accès privilégié sécurisé](/windows-server/identity/securing-privileged-access/securing-privileged-access) (SPA) pour les composants d’identité locaux (AD, AD FS).</li><li>Utilisez Defender pour Cloud Apps pour surveiller les menaces internes.</li><li>Découvrez l’utilisation shadow IT SaaS à l’aide de Defender pour Cloud Apps.</li></ul>|
|Gestion des identités et des accès|<ul><li>Affinez les stratégies et les processus opérationnels.</li><li>Utilisez Azure AD Identity Protection pour identifier les menaces internes.</li></ul>|
|Protection des informations|Affiner les stratégies de protection des informations : <ul><li>Microsoft 365 et Office 365 étiquettes de confidentialité et de protection contre la perte de données (DLP) ou Azure Information Protection.</li><li>Alertes et stratégies Defender pour Cloud Apps.</li></ul>|

Voir aussi : [Comment atténuer les cyberattaques rapides telles que Petya et WannaCrypt](https://cloudblogs.microsoft.com/microsoftsecure/2018/02/21/how-to-mitigate-rapid-cyberattacks-such-as-petya-and-wannacrypt/).
