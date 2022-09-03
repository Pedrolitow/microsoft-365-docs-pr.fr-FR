---
title: 'Étape 4 : déployer la gestion des points de terminaison pour vos appareils, PC et autres points de terminaison'
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Utilisez Microsoft Endpoint Manager pour gérer vos appareils de gestion, PC et autres points de terminaison.
ms.openlocfilehash: 62b8e106ebd4350cc1d706ae15f599676b03dbc9
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67584108"
---
# <a name="step-4-deploy-endpoint-management-for-your-devices-pcs-and-other-endpoints"></a>Étape 4 : déployer la gestion des points de terminaison pour vos appareils, PC et autres points de terminaison

Avec les travailleurs hybrides, vous devez prendre en charge un nombre croissant d’appareils personnels. La gestion des points de terminaison est une approche de sécurité, basée sur des stratégies, qui exige que les appareils respectent des critères spécifiques avant de pouvoir accéder aux ressources. Microsoft Endpoint Manager offre des capacités de gestion modernes pour sécuriser vos données dans le cloud et en local. 

[Microsoft Endpoint Manager](/mem/endpoint-manager-overview) fournit des services et des outils pour gérer les appareils mobiles, les ordinateurs de bureau, les machines virtuelles, les appareils intégrés et les serveurs, en combinant les services suivants, que vous connaissez et utilisez peut-être déjà.

:::image type="content" source="../media/empower-people-to-work-remotely/endpoint-managment-step-grid.png" alt-text="Composants de gestion des points de terminaison pour Microsoft 365" lightbox="../media/empower-people-to-work-remotely/endpoint-managment-step-grid.png":::

## <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune est un service basé sur le cloud qui se concentre sur la gestion des périphériques mobiles (MDM) et la gestion des applications mobiles (MAM) incluses dans Microsoft 365. 

- **Gestion des périphériques mobiles (MDM) :** Pour les appareils appartenant à l’organisation, vous pouvez exercer un contrôle total, y compris les paramètres, les fonctionnalités et la sécurité. Les appareils sont « inscrits » dans Intune et reçoivent ses stratégies avec les règles et les paramètres. Par exemple, vous pouvez définir les critères de mot de passe et de code confidentiel, créer une connexion VPN, configurer la protection contre les menaces, et bien plus encore.

- **GAM :** il est possible que les travailleurs à distance ne souhaitent pas que vous contrôliez complètement leurs appareils personnels, également appelés appareils Apportez votre propre appareil (BYOD). Vous pouvez fournir des options à vos travailleurs hybrides tout en continuant de protéger votre organisation. Par exemple, les employés peuvent inscrire leurs appareils s’ils veulent obtenir un accès total aux ressources de votre organisation. Vous pouvez également utiliser les stratégies de protection des applications qui requièrent l’authentification multifacteur (MFA) pour utiliser ces applications si ces utilisateurs souhaitent seulement accéder à la messagerie ou Microsoft Teams.

Pour plus d’informations, voir la solution de fondation [Gérer les appareils avec Intune](manage-devices-with-intune-overview.md).

## <a name="configuration-manager"></a>Configuration Manager

Configuration Manager est une solution de gestion locale qui vous permet de gérer les ordinateurs de bureau, les serveurs et les ordinateurs portables qui se trouvent sur votre réseau ou sur Internet. Utilisez Configuration Manager pour déployer des applications, des mises à jour logicielles et des systèmes d’exploitation. Vous pouvez également surveiller la conformité, interroger et agir sur les clients en temps réel, et bien plus encore. Vous pouvez l’activer dans le cloud pour l’intégrer à Intune, Azure AD, Microsoft Defender pour point de terminaison et d’autres services cloud. 

Si vous souhaitez en savoir plus, consultez la page [Présentation de Configuration Manager](/mem/configmgr/core/understand/introduction).

## <a name="co-management"></a>Cogestion

La cogestion combine votre investissement Configuration Manager local existant avec le cloud, à l’aide d’Intune et d’autres services cloud Microsoft 365. Vous choisissez si Gestionnaire de configuration ou Intune est l’autorité de gestion pour différentes charges de travail. 

La co-gestion utilise les fonctionnalités cloud basées sur Intune, y compris l’accès conditionnel et l’application de la conformité des appareils. Vous conservez certaines tâches en local, tout en exécutant d’autres tâches dans le cloud.

Si vous souhaitez en savoir plus, consultez la page [Présentation de la cogestion](/mem/configmgr/comanage/overview).

## <a name="endpoint-analytics"></a>Analyse des points de terminaison

Endpoint Analytics vise à améliorer la productivité des utilisateurs et à réduire les coûts de support informatique en fournissant des insights sur l’expérience utilisateur. Ces informations permettent au service informatique d'optimiser l'expérience de l'utilisateur final grâce à un support proactif, et de détecter les régressions de l'expérience utilisateur en évaluant l'impact des changements de configuration sur l'utilisateur.

Pour plus d’informations, voir cette [vue d’ensemble de Endpoint Analytics](/mem/analytics/overview)

## <a name="windows-autopilot"></a>Windows Autopilot

Windows Autopilot offre une plateforme de déploiement Windows sans intervention et en libre-service. Elle inclut un ensemble de technologies servant à configurer et à préconfigurer de nouveaux appareils pour les préparer à une utilisation productive. Vous pouvez également utiliser Windows Autopilot pour réinitialiser, réaffecter et récupérer des appareils. 

Windows Autopilot permet à un service informatique de pré-configurer des appareils avec peu ou pas d’infrastructure à gérer et avec un processus simple et facile. 

- En ce qui concerne l’utilisateur, seulement quelques opérations sont nécessaires pour avoir un appareil prêt à l’emploi. 
- Du point de vue des professionnels de l’informatique, la seule interaction requise de l’utilisateur final est de se connecter à un réseau et de vérifier ses informations d’identification.

Si vous souhaitez en savoir plus, consultez la page [Présentation de Windows Autopilot](/windows/deployment/windows-autopilot/windows-autopilot).

## <a name="admin-technical-resources-for-endpoint-management"></a>Ressources techniques dédiées aux administrateurs pour la gestion des points de terminaison

- [Gestion des appareils mobiles pour Microsoft 365](../enterprise/device-management-roadmap-microsoft-365.md)
- [Comment inscrire différents types d’appareils pour la gestion des périphériques mobiles](/mem/intune/enrollment/device-enrollment)
- [Comment former vos utilisateurs finaux à Microsoft Intune](/mem/intune/fundamentals/end-user-educate)
 
## <a name="results-of-step-4"></a>Résultats de l’étape 4

Vous utilisez la suite des fonctionnalités et des capacités de Endpoint Manager pour gérer les appareils mobiles, les ordinateurs de bureau, les machines virtuelles, les appareils incorporés et les serveurs.

## <a name="next-step"></a>Étape suivante

[![Étape 5 :Déployer les applications et les services de productivité des travailleurs à distance.](../media/empower-people-to-work-remotely/remote-workers-step-grid-5.png)](empower-people-to-work-remotely-teams-productivity-apps.md)

Passez à l’[étape 5](empower-people-to-work-remotely-teams-productivity-apps.md) pour encourager vos travailleurs hybrides à utiliser des applications de productivité Microsoft 365 telles que Microsoft Teams.