---
title: 3. Déployer la gestion des points de terminaison pour vos appareils, PC et autres points de terminaison
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: laurawi
ms.date: 05/01/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Priority
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
ms.custom:
- M365solutions
description: Utilisez Microsoft Endpoint Manager pour gérer vos appareils de gestion, PC et autres points de terminaison.
ms.openlocfilehash: 2a5b047aabb95d0b60c46fe3bec339e723adee0e
ms.sourcegitcommit: 5476c2578400894640ae74bfe8e93c3319f685bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "44049581"
---
# <a name="3-deploy-endpoint-management-for-your-devices-pcs-and-other-endpoints"></a>3. Déployer la gestion des points de terminaison pour vos appareils, PC et autres points de terminaison

Avec les travailleurs à distance, vous devez prendre en charge un nombre croissant d’appareils personnels. La gestion des points de terminaison est une approche de sécurité, basée sur des stratégies, qui exige que les appareils respectent des critères spécifiques avant de pouvoir accéder aux ressources. Microsoft Endpoint Manager offre un lieu de travail et des capacités de gestion modernes pour sécuriser vos données dans le cloud et en local. 

Endpoint Manager fournit des services et des outils pour gérer les appareils mobiles, les ordinateurs de bureau, les machines virtuelles, les appareils intégrés et les serveurs, en combinant les services suivants, que vous connaissez peut-être déjà et que vous utilisez.

![Composants de gestion des points de terminaison](../media/empower-people-to-work-remotely/endpoint-managment-step-grid.png)

## <a name="microsoft-intune"></a>Microsoft Intune

Intune est conçu pour vous aider à protéger vos données lorsque vous ne gérez pas les appareils utilisés pour accéder aux données de l’organisation. Les stratégies de protection des applications Intune, combinées à l’accès conditionnel Azure AD, offrent un contrôle granulaire des données sur les appareils mobiles. Intune vous permet également de définir des stratégies complètes, qui permettent uniquement aux personnes autorisées, et dans les bonnes conditions, d’accéder aux données de votre entreprise et de garantir que ces données restent protégées, en contrôlant la façon dont elles sont utilisées dans Office, Outlook et d’autres applications mobiles.

Si vous souhaitez en savoir plus, consultez la page [Présentation de Microsoft Intune](https://docs.microsoft.com/intune/fundamentals/what-is-intune).

## <a name="configuration-manager"></a>Configuration Manager

Configuration Manager est une solution de gestion locale qui vous permet de gérer les ordinateurs de bureau, les serveurs et les ordinateurs portables qui se trouvent sur votre réseau ou sur Internet. Vous pouvez l’activer dans le cloud pour l’intégrer à Intune, Azure AD, Microsoft Defender - Protection avancée contre les menaces, et d’autres services cloud. Utilisez Configuration Manager pour déployer des applications, des mises à jour logicielles et des systèmes d’exploitation. Vous pouvez également surveiller la conformité, interroger et agir sur les clients en temps réel, et bien plus encore.

Si vous souhaitez en savoir plus, consultez la page [Présentation de Configuration Manager](https://docs.microsoft.com/mem/configmgr/core/understand/introduction).

## <a name="co-management"></a>Cogestion

La cogestion combine votre investissement Configuration Manager local existant avec le cloud, à l’aide d’Intune et d’autres services cloud Microsoft 365. Vous devez choisir entre Configuration Manager ou Intune et décidez lequel doit être l’autorité de gestion pour les sept groupes de charges de travail différents.

Dans Endpoint Manager, la cogestion utilise des fonctionnalités cloud, notamment l’accès conditionnel. Vous conservez certaines tâches en local, tout en exécutant d’autres tâches dans le cloud avec Intune.

Si vous souhaitez en savoir plus, consultez la page [Présentation de la cogestion](https://docs.microsoft.com/mem/configmgr/comanage/overview).

## <a name="desktop-analytics"></a>Analyses du bureau

L’Analyse du bureau est un service basé sur le cloud, qui s’intègre à Configuration Manager et vous fournit des informations et des renseignements, afin que vous puissiez prendre des décisions éclairées concernant vos clients Windows. Elle combine des données de votre organisation à des données cumulées à partir de millions d’appareils connectés à des services cloud de Microsoft. L’Analyse de bureau vous permet de créer un inventaire des applications exécutées au sein de votre organisation, d’évaluer la compatibilité des applications avec les dernières mises à jour des fonctionnalités de Windows 10, d’identifier les problèmes de compatibilité et de recevoir des suggestions d’atténuation basées sur les données orientées cloud. Cela vous permet également de créer des groupes pilotes qui représentent l’ensemble des applications et des pilotes sur un ensemble minimal d’appareils, et de déployer Windows 10 sur des appareils pilotes et gérés par la production.

Si vous souhaitez en savoir plus, consultez la page [Présentation de l’Analyse du bureau](https://docs.microsoft.com/mem/configmgr/desktop-analytics/overview).

## <a name="windows-autopilot"></a>Windows Autopilot

Windows Autopilot offre une plateforme de déploiement Windows sans intervention et en libre-service. C’est un ensemble de technologies, utilisées pour configurer et préconfigurer de nouveaux appareils, de manière à les préparer à une utilisation productive. Vous pouvez également utiliser Windows Autopilot pour réinitialiser, réaffecter et récupérer des appareils. Cette solution permet à un service informatique d’obtenir ce qui précède avec peu ou pas d’infrastructure à gérer et avec un processus simple et facile. En ce qui concerne l’utilisateur, seulement quelques opérations sont nécessaires pour avoir un appareil prêt à l’emploi. Du point de vue des professionnels de l’informatique, la seule interaction requise de l’utilisateur final est de se connecter à un réseau et de vérifier ses informations d’identification.

Si vous souhaitez en savoir plus, consultez la page [Présentation de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot).

## <a name="admin-technical-resources-for-endpoint-management"></a>Ressources techniques dédiées aux administrateurs pour la gestion des points de terminaison

- [Inscrire les appareils gérés pour la sécurité, utiliser les paramètres de l’application pour les appareils non gérés et utiliser les stratégies d’appareil et d’application](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure)
- [Comment inscrire différents types d’appareils pour la gestion des périphériques mobiles](https://docs.microsoft.com/mem/intune/enrollment/device-enrollment)
- [Comment former vos utilisateurs finaux à Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/end-user-educate)
 
## <a name="results-of-step-3"></a>Résultats de l’étape 3

Vous utilisez la suite des fonctionnalités et des capacités de Endpoint Manager pour gérer les appareils mobiles, les ordinateurs de bureau, les machines virtuelles, les appareils incorporés et les serveurs.

## <a name="next-step"></a>Étape suivante

Passez à l’[étape 4](empower-people-to-work-remotely-teams-productivity-apps.md) pour fournir l’accès à distance aux applications et services locaux.
