---
title: Configurez votre infrastructure pour le travail hybride avec Microsoft 365
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: high
ms.collection:
- highpri
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-overview
- M365initiative-coredeploy
ms.custom: seo-marvel-jun2020
keywords: travail à domicile, travail domicile-travail, travail hybride, travail à distance, travail hybride, employés à distance, connectivité hybride, accès à distance, télécommunications, télétravail, télétravail, travail mobile, travail à distance, travail à distance, travail en tout lieu, travail flexible
description: Traversez les couches d’infrastructure pour que vos travailleurs hybrides accèdent aux ressources locales et Microsoft 365 en toute sécurité.
ms.openlocfilehash: b79c0096139633a2ff151adce71f69aea9780b6b
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67986947"
---
# <a name="set-up-your-infrastructure-for-hybrid-work-with-microsoft-365"></a>Configurez votre infrastructure pour le travail hybride avec Microsoft 365

Pour sécuriser et optimiser la productivité et la collaboration de vos employés, vous devez autoriser les travailleurs sur site et distants à accéder facilement et en toute sécurité aux informations, outils et ressources locaux et basés sur le cloud de votre organisation. Cette solution prévoit le déploiement de couches d'infrastructure clés qui permettent à vos travailleurs de donner le meilleur d'eux-mêmes, où qu'ils soient.

Les travailleurs hybrides peuvent travailler sur site ou à distance dans une combinaison d’emplacements. Permettre aux employés de travailler hors du bureau traditionnel est important pour de nombreuses organisations :

- Embauchez et retenez des employés qui ne souhaitent pas se déplacer ou qui ont besoin d’un environnement de travail flexible.
- Réduisez les déplacements des travailleurs, en leur laissant plus de temps pour être productifs et s’adonner à des activités qui réduisent le stress en dehors du travail.
- Économisez de l’espace de bureau.

Microsoft 365 offre les fonctionnalités permettant à vos travailleurs hybrides de travailler sur site ou à distance.

![Confier des responsabilités aux travailleurs hybrides avec Microsoft 365.](../media/empower-people-to-work-remotely/2-m365-remoteworker-solution-businessoverview.png)

> [!NOTE]
> Si vous découvrez Microsoft 365 pour la première fois, consultez [ces ressources](https://www.microsoft.com/microsoft-365).

Regardez cette vidéo de présentation du processus de déploiement.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4F1af]

Pour les professionnels de l’informatique qui gèrent une infrastructure sur site et dans le cloud afin de favoriser la productivité des travailleurs hybrides, cette solution fournit les fonctionnalités clés ci-après :

- Connecté

  Où que vous soyez et à tout moment, vos employés peuvent accéder aux éléments suivants :

  - Services et données dans le cloud de votre abonnement Microsoft 365.

  - Ressources d’organisation, telles celles proposées par les centres de données d’application locaux.

- Sécurisé

  Les connexions sont sécurisées avec l’authentification multifacteur (MFA) et les fonctionnalités de sécurité intégrées de Microsoft 365 et Windows 11 ou 10 protègent contre les programmes malveillants, les attaques malveillantes et la perte de données.

- Géré

  Les appareils de votre travailleur hybride peuvent être gérés à partir du cloud avec les paramètres de sécurité, les applications autorisées et la conformité avec l’état d’intégrité du système.

- Collaboration et productivité

  Vos travailleurs hybrides peuvent être aussi productifs que localement de manière hautement collaborative avec :

  - Réunions en ligne et sessions de conversation avec Teams.

  - Les espaces de travail partagés pour le stockage de fichiers dans le Cloud avec une accessibilité globale et une collaboration en temps réel avec SharePoint et OneDrive.

  - Les tâches partagées et flux de travail pour répartir le travail et accomplir les tâches.

Pour une expérience de connexion transparente, vos comptes d’utilisateur Services de domaine Active Directory (AD DS) locaux doivent être synchronisés avec Azure Active Directory (Azure AD). Pour protéger vos appareils Windows 11 ou 10, ils doivent être inscrits dans Intune. Voici un aperçu général de l’infrastructure.

![Infrastructure de base pour les travailleurs hybrides avec Microsoft 365.](../media/empower-people-to-work-remotely/remote-workers-basic-infrastructure.png)

Pour activer les fonctionnalités de Microsoft 365 pour vos travailleurs hybrides, utilisez ces fonctionnalités Microsoft 365.

|Fonctionnalité|Description|Licence|
|---|---|---|
|Authentification multifacteur appliquée avec paramètres de sécurité par défaut|Protégez-vous contre les identités compromises et les appareils en imposant une deuxième forme d’authentification pour les connexions. La sécurité par défaut nécessite l’authentification multifacteur pour tous les comptes d’utilisateurs.|Microsoft 365 E3 ou E5|
|Authentification multifacteur appliquée avec accès conditionnel|Requiert une authentification multifacteur sur la base des propriétés de la connexion avec les stratégies d’accès conditionnel.|Microsoft 365 E3 ou E5|
|Authentification multifacteur appliquée avec accès conditionnel basé sur les risques|Exigez l'AMF en fonction du risque lié à la connexion de l'utilisateur avec Azure AD Identity Protection.|Microsoft 365 E5 ou E3 avec les licences Azure AD Premium P2|
|Réinitialisation du mot de passe libre-service (SSPR)|Autoriser vos utilisateurs à réinitialiser ou déverrouiller leur mot de passe ou leur compte.|Microsoft 365 E3 ou E5|
|Proxy d’application Azure AD|Fournir un accès à distance sécurisé pour les applications web hébergées sur les serveurs intranet.|Nécessite un abonnement Azure payé séparément|
|VPN point à site Azure|Créer une connexion sécurisée à partir de l’appareil d’un employé distant sur votre intranet via un réseau virtuel Azure.|Nécessite un abonnement Azure payé séparément|
|Windows 365|Prendre en charge les travailleurs à distance qui peuvent uniquement utiliser leurs appareils personnels et non gérés avec des PC Windows 365 Cloud.|Nécessite un abonnement Azure payé séparément|
|Bureau à distance |Autoriser les employés à se connecter à des ordinateurs Windows sur votre intranet.|Microsoft 365 E3 ou E5|
|Passerelle des services Bureau à distance|Chiffrer les communications et empêcher les hôtes RDS d’être directement exposés à Internet.|Nécessite des licences Windows Server distinctes|
|Microsoft Intune|Gérer les appareils et les applications.|Microsoft 365 E3 ou E5|
|Configuration Manager|Gérer les installations, mises à jour et paramètres logiciels de vos appareils|Nécessite des licences de gestionnaire de configuration distinctes|
|Analyse des points de terminaison|Déterminer la disponibilité des mises à jour de vos clients Windows.|Nécessite des licences de gestionnaire de configuration distinctes|
|Windows Autopilot|Configurez et préconfigurez les nouveaux appareils Windows 11 ou 10 pour une utilisation productive.|Microsoft 365 E3 ou E5|
|Microsoft Teams, Exchange Online, SharePoint Online et OneDrive, Microsoft 365 Apps, Microsoft Power Platform et Yammer|Créer, communiquer et collaborer.|Microsoft 365 E3 ou E5|
||||

Pour plus d’informations sur la sécurité et la conformité, consultez [Déployer la sécurité et la conformité des travailleurs à distance.](empower-people-to-work-remotely-security-compliance.md)

<a name="poster"></a> Pour un résumé de deux pages de cette solution, voir l’affiche [Confier des responsabilités aux travailleurs hybrides](https://download.microsoft.com/download/9/b/b/9bb5fa79-74e9-497b-87c5-4021e53d9fc2/hybrid-worker-infrastructure.pdf).

[![Affiche Autonomiser les travailleurs hybrides.](../media/empower-people-to-work-remotely/empower-remote-workers-poster.png)](https://download.microsoft.com/download/9/b/b/9bb5fa79-74e9-497b-87c5-4021e53d9fc2/hybrid-worker-infrastructure.pdf)

## <a name="provide-hybrid-working-for-all-of-your-workers"></a>Permettre à tous vos employés de travailler de manière hybride

Vous pouvez permettre à tous vos employés de rester productifs où que vous soyez grâce à ces appareils :

- Un appareil moderne, tel qu’un ordinateur portable Surface et Windows 11 ou 10, qui dispose des fonctionnalités, de la sécurité et des performances pour accéder à Microsoft 365 applications et services cloud directement sur le web.

- Any device including older laptops or desktops used from home, which can access Microsoft 365 cloud apps and services indirectly through a [Windows 365 Cloud PC](empower-people-to-work-remotely-remote-access.md#deploy-windows-365-to-provide-remote-access-for-remote-workers-using-personal-devices). This option provides high performance, strong security, and simplified IT management.

## <a name="next-steps"></a>Étapes suivantes

Procédez comme suit pour sécuriser et optimiser l’accès aux serveurs et aux services cloud de votre organisation, puis optimiser la productivité des travailleurs hybrides.

1. [Augmenter la sécurité de connexion avec l’authentification multifacteur](empower-people-to-work-remotely-secure-sign-in.md)
2. [Fournir l’accès à distance aux applications et services locaux](empower-people-to-work-remotely-remote-access.md)
3. [Déployer les services de sécurité et de conformité](empower-people-to-work-remotely-security-compliance.md)
4. [Déployer la gestion des points de terminaison pour vos appareils, PC et autres points de terminaison](empower-people-to-work-remotely-manage-endpoints.md)
5. [Déployer les applications et les services de productivité des travailleurs hybrides](empower-people-to-work-remotely-teams-productivity-apps.md)
6. [Former vos employés et répondre aux commentaires sur l’utilisation](empower-people-to-work-remotely-train-monitor-usage.md)

[![Étapes de configuration de votre infrastructure pour le travail hybride avec Microsoft 365.](../media/empower-people-to-work-remotely/remote-workers-step-grid.png)](empower-people-to-work-remotely-secure-sign-in.md)

Pour découvrir comment une organisation multinationale représentative, bien que fictive, a mis en place son infrastructure pour le travail hybride, consultez [Réponse COVID-19 et infrastructure de Contoso pour le travail hybride](contoso-remote-onsite-work.md).
