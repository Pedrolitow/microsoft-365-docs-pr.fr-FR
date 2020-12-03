---
title: Feuille de route Microsoft 365 Security-principales priorités
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 10/08/2018
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
ms.assetid: 28c86a1c-e4dd-4aad-a2a6-c768a21cb352
description: 'Principales recommandations de l’équipe Cybersecurity de Microsoft pour la mise en œuvre de fonctionnalités de sécurité pour protéger votre environnement Microsoft 365. '
ms.openlocfilehash: d62db9206a98078ae5adaad220a7c9b53ff116cd
ms.sourcegitcommit: 4debeb8f0fce67f361676340fc390f1b283a3069
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "49561694"
---
# <a name="security-roadmap---top-priorities-for-the-first-30-days-90-days-and-beyond"></a>Feuille de route de sécurité-priorités principales des 30 premiers jours, 90 jours, et au-delà

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Cet article présente les principales recommandations de l’équipe Cybersecurity de Microsoft pour la mise en œuvre de fonctionnalités de sécurité pour protéger votre environnement Microsoft 365. Cet article est adapté à partir d’une session Microsoft enflamme, [Secure microsoft 365 comme un Cybersecurity Pro : les principales priorités pour les 30 premiers jours, 90 jours et au-delà](https://www.youtube.com/watch?v=luignzNyR-o). Cette session a été développée et présentée par Mark Simos et Matt Kemelhar, Enterprise Cybersecurity Architects.

Contenu de cet article :

- [Résultats de la feuille de route](security-roadmap.md#Roadmap)
- [30 jours — un succès rapide puissant](security-roadmap.md#Thirdaydays)
- [90 jours — amélioration des protections](security-roadmap.md#Ninetydays)
- [Après](security-roadmap.md#Beyond)

## <a name="roadmap-outcomes"></a>Résultats de la feuille de route
<a name="Roadmap"> </a>

Ces recommandations de feuille de route sont échelonnées sur trois phases dans un ordre logique avec les objectifs suivants.

****

|Intervalle de temps|Résultats|
|---|---|
|30 jours|Configuration rapide : <ul><li>Protections d’administration de base.</li><li>Journalisation et analyse.</li><li>Protections d’identité de base.</li></ul> <p> Configuration du client. <p> Préparez les parties prenantes.|
|90 jours|Protections avancées : <ul><li>Comptes d’administrateur.</li><li>Données et comptes d’utilisateur.</li></ul> <p> Visibilité des besoins en matière de conformité, de menace et d’utilisateur. <p> Adaptez et implémentez les stratégies et les protections par défaut.|
|Après|Ajuster et affiner les stratégies et les contrôles clés. <p> Étendez les protections aux dépendances locales. <p> Intégration aux processus métier et de sécurité (menace légale, Insider, etc.).|
|

## <a name="30-days--powerful-quick-wins"></a>30 jours — un succès rapide puissant
<a name="Thirdaydays"> </a>

Ces tâches peuvent être accomplies rapidement et ont un faible impact sur les utilisateurs.

****

|Domaine|Tâches|
|---|---|
|Gestion de la sécurité|<ul><li>Vérifier le score sécurisé et noter votre score actuel ( <https://securescore.office.com> ).</li><li>Activez la journalisation d’audit pour Office 365. Consultez [la rubrique Rechercher dans le journal d’audit](../../compliance/search-the-audit-log-in-security-and-compliance.md).</li><li>[Configurez Microsoft 365 pour renforcer la sécurité](tenant-wide-setup-for-increased-security.md).</li><li>Examinez régulièrement les tableaux de bord et les rapports dans le centre de sécurité Microsoft 365 et dans le Cloud App Security.</li></ul>|
|Protection contre les menaces|[Connectez microsoft 365 à Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) pour démarrer la surveillance à l’aide des stratégies de détection des menaces par défaut pour les comportements anormaux. Il faut sept jours pour créer une ligne de base pour la détection des anomalies. <p>  Implémenter la protection pour les comptes d’administrateur :<ul><li>Utilisez des comptes d’administration dédiés pour l’activité d’administration.</li><li>Appliquer l’authentification multifacteur (MFA) pour les comptes d’administrateur.</li><li>Utilisez un [appareil Windows 10 hautement sécurisé](https://docs.microsoft.com/windows-hardware/design/device-experiences/oem-highly-secure) pour l’activité de l’administrateur.</li></ul>|
|Gestion des identités et des accès|<ul><li>[Activer la protection des identités Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection-enable).</li><li>Pour les environnements d’identité fédérée, appliquez la sécurité des comptes (longueur du mot de passe, âge, complexité, etc.).</li></ul>|
|Protection des informations|Consultez l’exemple de recommandations pour la protection des informations. La protection des informations nécessite une coordination au sein de votre organisation. Commencez à utiliser ces ressources :<ul><li>[Protection des informations Office 365 pour le RGPD](https://aka.ms/o365gdpr)</li><li>[Configurer teams avec trois niveaux de protection](../../solutions/configure-teams-three-tiers-protection.md) (y compris le partage, la classification, la protection contre la perte de données et Azure information protection)</li></ul>|
|

## <a name="90-days--enhanced-protections"></a>90 jours — amélioration des protections
<a name="Ninetydays"> </a>

Ces tâches prennent un peu plus de temps à planifier et à implémenter, mais augmentent considérablement votre posture de sécurité.

****

|Domaine|Tâche|
|---|---|
|Gestion de la sécurité|<ul><li>Vérifiez le score de sécurité pour les actions recommandées pour votre environnement ( [https://securescore.office.com](https://securescore.office.com) ).</li><li>Poursuivez régulièrement l’examen des tableaux de bord et des rapports dans le centre de sécurité Microsoft 365, dans la sécurité des applications Cloud et dans les outils SIEM.</li><li>Recherchez et implémentez les mises à jour logicielles.</li><li>Effectuez des simulations d’attaque pour le Spear Phishing, la vaporisation des mots de passe et les attaques de mot de passe en force à l’aide d’un [simulateur d’attaque](attack-simulator.md) (inclus avec [Office 365 Threat Intelligence](office-365-ti.md)).</li><li>Recherchez le risque de partage en examinant la sécurité des rapports intégrés dans Cloud App Security (sous l’onglet examiner).</li><li>Vérifiez le [Gestionnaire de conformité](https://docs.microsoft.com/microsoft-365/compliance/compliance-manager) pour vérifier l’état des réglementations qui s’appliquent à votre organisation (par exemple, RGPD, NIST 800-171).</li></ul>|
|Protection contre les menaces|Implémenter des protections améliorées pour les comptes d’administrateur : <ul><li>Configurez les [stations de travail d’accès privilégié](https://docs.microsoft.com/windows-server/identity/securing-privileged-access/privileged-access-workstations) (pattes) pour l’activité d’administration.</li><li>Configurez [Azure ad Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</li><li>Configurer un outil de gestion des événements et des informations de sécurité (SIEM) pour collecter les données de journalisation à partir d’Office 365, de la sécurité des applications Cloud et d’autres services, y compris AD FS. Le journal d’audit stocke les données de 90 jours seulement. La capture de ces données dans l’outil SIEM vous permet de stocker des données pendant une période plus longue.</li></ul>|
|Gestion des identités et des accès|<ul><li>Activer et appliquer l’authentification multifacteur pour tous les utilisateurs.</li><li>Implémentez un ensemble d' [accès conditionnel et de stratégies associées](microsoft-365-policies-configurations.md).</li></ul>|
|Protection des informations| Adaptez et implémentez les stratégies de protection des informations. Ces ressources incluent des exemples : <ul><li>[Protection des informations Office 365 pour le RGPD](https://aka.ms/o365gdpr)</li><li>[Configurer Teams avec trois niveaux de protection](../../solutions/configure-teams-three-tiers-protection.md)</li></ul> <p> Utilisez les stratégies de protection contre la perte de données et les outils de surveillance de Microsoft 365 pour les données stockées dans Microsoft 365 (au lieu de la sécurité des applications Cloud). <p> Utilisez la sécurité des applications Cloud avec Microsoft 365 pour les fonctionnalités d’alerte avancées (autres que la protection contre la perte de données).|
|

## <a name="beyond"></a>Après
<a name="Beyond"> </a>

Il s’agit de mesures de sécurité importantes qui s’appuient sur le travail précédent.

****

|Domaine|Tâche|
|---|---|
|Gestion de la sécurité|<ul><li>Poursuivez la planification des actions suivantes à l’aide du score de sécurité ( <https://securescore.office.com> ).</li><li>Poursuivez régulièrement l’examen des tableaux de bord et des rapports dans le centre de sécurité Microsoft 365, dans la sécurité des applications Cloud et dans les outils SIEM.</li><li>Continuez à rechercher et à mettre en œuvre des mises à jour logicielles.</li><li>Intégrez eDiscovery à vos processus de réponse légale et de menace.</li></ul>|
|Protection contre les menaces|<ul><li>Implémenter un [accès privilégié sécurisé](https://docs.microsoft.com/windows-server/identity/securing-privileged-access/securing-privileged-access) (Spa) pour les composants d’identité sur site (AD, AD FS).</li><li>Utilisez Cloud App Security pour surveiller les menaces d’initiés.</li><li>Découvrez l’utilisation de la sécurité des applications Cloud pour les applications SaaS.</li></ul>|
|Gestion des identités et des accès|<ul><li>Affiner les stratégies et les processus opérationnels.</li><li>Utiliser Azure AD Identity Protection pour identifier les menaces pour les initiés.</li></ul>|
|Protection des informations|Affiner les stratégies de protection des informations : <ul><li>Étiquettes de confidentialité Microsoft 365 et Office 365, protection contre la perte de données (DLP) ou Azure information protection.</li><li>Alertes et stratégies de sécurité des applications Cloud.</li></ul>|
|

Voir aussi : [Comment limiter les cyberattaques rapides telles que Petya et WannaCrypt](https://cloudblogs.microsoft.com/microsoftsecure/2018/02/21/how-to-mitigate-rapid-cyberattacks-such-as-petya-and-wannacrypt/).
