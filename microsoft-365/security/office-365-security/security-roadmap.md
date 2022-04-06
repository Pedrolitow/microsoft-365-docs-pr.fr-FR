---
title: 'Microsoft 365 sécurité : principales priorités'
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
description: Recommandations principales de l’équipe de cybersécurité de Microsoft pour implémenter des fonctionnalités de sécurité pour protéger Microsoft 365 environnement.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7ffdcb8e6f1a3cb167ec3ce8d7ac5a9225b05356
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683228"
---
# <a name="security-roadmap---top-priorities-for-the-first-30-days-90-days-and-beyond"></a>Feuille de route de sécurité : principales priorités pour les 30 premiers jours, 90 jours et au-delà

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Cet article inclut les principales recommandations de l’équipe de cybersécurité de Microsoft pour implémenter des fonctionnalités de sécurité pour protéger Microsoft 365 environnement. Cet article est adapté à partir d’une session Microsoft Ignite [— Secure Microsoft 365 like a cybersecurity pro: Top priorities for the first 30 days, 90 days, and beyond](https://www.youtube.com/watch?v=luignzNyR-o). Cette session a été développée et présentée par Mark Simos et Matt Kemelhar, architectes Enterprise cyber-sécurité.

Contenu de cet article :

- [Résultats de la feuille de route](security-roadmap.md#Roadmap)
- [30 jours : puissantes et rapides](security-roadmap.md#Thirdaydays)
- [90 jours : protections améliorées](security-roadmap.md#Ninetydays)
- [Au-delà](security-roadmap.md#Beyond)

## <a name="roadmap-outcomes"></a>Résultats de la feuille de route
<a name="Roadmap"> </a>

Ces recommandations de feuille de route sont organisées en trois phases dans un ordre logique avec les objectifs suivants.

|Période|Résultats|
|---|---|
|30 jours|Configuration rapide : <ul><li>Protections d’administration de base.</li><li>Journalisation et analyse.</li><li>Protections d’identité de base.</li></ul> <p> Configuration du client. <p> Préparez les parties prenantes.|
|90 jours|Protections avancées : <ul><li>Comptes d’administrateur.</li><li>Les données et les comptes d’utilisateur.</li></ul> <p> Visibilité de la conformité, des menaces et des besoins des utilisateurs. <p> Adaptez et implémentez les stratégies et protections par défaut.|
|Au-delà|Ajuster et affiner les stratégies et les contrôles clés. <p> Étendre les protections aux dépendances sur site. <p> Intégration aux processus d’entreprise et de sécurité (juridique, menace interne, etc.).|

## <a name="30-days--powerful-quick-wins"></a>30 jours : puissantes et rapides
<a name="Thirdaydays"> </a>

Ces tâches peuvent être accomplies rapidement et ont un faible impact sur les utilisateurs.

|Zone|Tâches|
|---|---|
|Gestion de la sécurité|<ul><li>Vérifiez le niveau de sécurisation et prenez note de votre score actuel (<https://security.microsoft.com/securescore>).</li><li>Activer la journalisation d’audit Office 365. Voir [Rechercher dans le journal d’audit](../../compliance/search-the-audit-log-in-security-and-compliance.md).</li><li>[Configurez Microsoft 365 pour une sécurité accrue](tenant-wide-setup-for-increased-security.md).</li><li>Examinez régulièrement les tableaux de bord et les rapports dans le portail Microsoft 365 Defender et Defender pour les applications cloud.</li></ul>|
|Protection contre les menaces|[Connecter Microsoft 365 à Microsoft Defender pour les applications cloud pour](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) commencer à surveiller les comportements anormaux à l’aide des stratégies de détection des menaces par défaut. La construction d’une base de référence pour la détection des anomalies prend sept jours. <p>  Implémenter la protection des comptes d’administrateur :<ul><li>Utilisez des comptes d’administrateur dédiés pour l’activité de l’administrateur.</li><li>Appliquer l’authentification multifacteur (MFA) pour les comptes d’administrateur.</li><li>Utilisez un appareil [de Windows hautement sécurisé pour l’activité](/windows-hardware/design/device-experiences/oem-highly-secure) de l’administrateur.</li></ul>|
|Gestion des identités et des accès|<ul><li>[Activez Azure Active Directory Identity Protection](/azure/active-directory/active-directory-identityprotection-enable).</li><li>Pour les environnements d’identité fédérée, appliquez la sécurité des comptes (longueur du mot de passe, âge, complexité, etc.).</li></ul>|
|Protection des informations|Examinez les exemples de recommandations en matière de protection des informations. La protection des informations nécessite une coordination au sein de votre organisation. Commencez à utiliser ces ressources :<ul><li>[Protection des informations Office 365 pour le RGPD](/compliance/regulatory/gdpr)</li><li>[Configurer Teams avec trois niveaux de protection](../../solutions/configure-teams-three-tiers-protection.md) (notamment le partage, la classification, la protection contre la perte de données et Azure Information Protection)</li></ul>|

## <a name="90-days--enhanced-protections"></a>90 jours : protections améliorées
<a name="Ninetydays"> </a>

Ces tâches prennent un peu plus de temps à planifier et à implémenter, mais augmentent considérablement votre posture de sécurité.

|Zone|Tâche|
|---|---|
|Gestion de la sécurité|<ul><li>Vérifiez le score de sécurité pour les actions recommandées pour votre environnement (<https://security.microsoft.com/securescore>).</li><li>Continuez à consulter régulièrement les tableaux de bord et les rapports dans le portail Microsoft 365 Defender, Defender pour les applications cloud et les outils SIEM.</li><li>Recherchez et implémentez des mises à jour logicielles.</li><li>Effectuez des simulations d’attaques pour le harponnage, la pulvérisation de mots de passe et les attaques par mot de passe en force brute à l’aide d’une formation sur la [simulation](attack-simulation-training.md) d’attaques (incluse dans [Office 365 Threat Intelligence](office-365-ti.md).</li><li>Recherchez les risques de partage en  examineant les rapports intégrés dans Defender pour les applications cloud (sous l’onglet Examiner).</li><li>[Consultez le Gestionnaire](../../compliance/compliance-manager.md) de conformité pour vérifier l’état des réglementations qui s’appliquent à votre organisation (par exemple, R GDPR, NIST 800-171).</li></ul>|
|Protection contre les menaces|Implémenter des protections améliorées pour les comptes d’administrateur : <ul><li>Configurez [les stations de travail à accès privilégié](/security/compass/privileged-access-devices) (PAW) pour l’activité de l’administrateur.</li><li>Configurez [Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).</li><li>Configurez un outil de gestion des événements et des informations de sécurité (SIEM) pour collecter des données de journalisation à partir de Office 365, Defender pour les applications cloud et d’autres services, y compris AD FS. Le journal d’audit stocke les données pendant 90 jours seulement. La capture de ces données dans l’outil SIEM vous permet de stocker les données pendant une période plus longue.</li></ul>|
|Gestion des identités et des accès|<ul><li>Activez et appliquez l’mf pour tous les utilisateurs.</li><li>Implémenter un ensemble [d’accès conditionnel et de stratégies associées](microsoft-365-policies-configurations.md).</li></ul>|
|Protection des informations| Adaptez et implémentez des stratégies de protection des informations. Ces ressources incluent des exemples : <ul><li>[Protection des informations Office 365 pour le RGPD](/compliance/regulatory/gdpr)</li><li>[Configurer Teams avec trois niveaux de protection](../../solutions/configure-teams-three-tiers-protection.md)</li></ul> <p> Utilisez des stratégies de protection contre la perte de données et des outils de surveillance dans Microsoft 365 pour les données stockées dans Microsoft 365 (au lieu de Defender pour les applications cloud). <p> Utilisez Defender pour les applications cloud avec Microsoft 365 fonctionnalités d’alerte avancées (autres que la protection contre la perte de données).|

## <a name="beyond"></a>Au-delà
<a name="Beyond"> </a>

Voici des mesures de sécurité importantes qui s’appuient sur les travaux précédents.

|Zone|Tâche|
|---|---|
|Gestion de la sécurité|<ul><li>Continuez à planifier les actions suivantes à l’aide du niveau de sécurité (<https://security.microsoft.com/securescore>).</li><li>Continuez à consulter régulièrement les tableaux de bord et les rapports dans le portail Microsoft 365 Defender, Defender pour les applications cloud et les outils SIEM.</li><li>Continuez à rechercher et implémenter des mises à jour logicielles.</li><li>Intégrez eDiscovery à vos processus de réponse aux menaces et juridiques.</li></ul>|
|Protection contre les menaces|<ul><li>[Implémenter l’accès privilégié](/windows-server/identity/securing-privileged-access/securing-privileged-access) sécurisé (SPA) pour les composants d’identité locaux (AD, AD FS).</li><li>Utilisez Defender pour les applications cloud pour surveiller les menaces internes.</li><li>Découvrez l’utilisation de shadow IT SaaS à l’aide de Defender pour les applications cloud.</li></ul>|
|Gestion des identités et des accès|<ul><li>Affiner les stratégies et les processus opérationnels.</li><li>Utilisez Azure AD Identity Protection pour identifier les menaces internes.</li></ul>|
|Protection des informations|Affiner les stratégies de protection des informations : <ul><li>Microsoft 365 et Office 365 étiquettes de sensibilité et protection contre la perte de données (DLP) ou Azure Information Protection.</li><li>Stratégies et alertes de Defender for Cloud Apps.</li></ul>|

Voir aussi : [Comment atténuer les cyberattaques rapides telles que Petya et WannaCrypt](https://cloudblogs.microsoft.com/microsoftsecure/2018/02/21/how-to-mitigate-rapid-cyberattacks-such-as-petya-and-wannacrypt/).
