---
title: 'Phase 4 : Microsoft 365 Apps pour entreprise'
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/23/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Les étapes du déploiement de l’infrastructure Microsoft 365 Apps pour entreprise pour Microsoft 365 Entreprise.
ms.openlocfilehash: fe29b8025a8ccf5babf2c52cd62ebc72860a8a5c
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43631428"
---
# <a name="phase-4-microsoft-365-apps-for-enterprise"></a>Phase 4 : Microsoft 365 Apps pour entreprise

![Phase 4 : Microsoft 365 Apps pour entreprise](../media/deploy-foundation-infrastructure/O365proplus_icon.png)

*Cela s’applique aux versions E3 et E5 de Microsoft 365 Entreprise et Microsoft 365 Éducation*

Microsoft 365 Entreprise inclut Microsoft 365 Apps pour entreprise, la version d’abonnement de Microsoft Office. Comme Office 2019, Microsoft 365 Apps pour entreprise inclut toutes les applications d’Office. Ces applications sont installées directement sur vos appareils clients. Contrairement à Office 2019, Microsoft 365 Apps pour entreprise est mis à jour régulièrement avec de nouvelles fonctionnalités et offre un modèle de licence basé sur l’utilisateur qui permet aux utilisateurs d’installer Office sur plusieurs appareils. Pour plus d’informations, consultez la rubrique [À propos de Microsoft 365 Apps pour entreprise dans l’entreprise](https://docs.microsoft.com/deployoffice/about-office-365-proplus-in-the-enterprise).

Dans cette phase, vous déployez Microsoft 365 Apps pour entreprise sur les appareils clients dans le cadre de Microsoft 365 Entreprise. En plus de ces instructions, nous vous recommandons d’utiliser [Microsoft Fastrack](https://fasttrack.microsoft.com/office) pour vous aider à effectuer votre déploiement. 

Si vous avez déjà déployé Microsoft 365 Apps pour entreprise, consultez les [critères de sortie](office365proplus-exit-criteria.md) de cette phase pour vous assurer que vous répondez aux conditions requises pour Microsoft 365 Entreprise.

>[!Note]
>Pour déployer ensemble Windows 10 Entreprise et Microsoft 365 Apps pour entreprise, voir le [Centre de déploiement de bureau](desktop-deployment-center-home.md).
>

## <a name="step-1-assess-your-environment"></a>Étape 1 : évaluer votre environnement

Avant de déployer Microsoft 365 Apps pour entreprise, suivez les instructions indiquées dans l’article [Évaluation de votre environnement et de sa configuration requise pour déployer Microsoft 365 Apps pour entreprise](https://docs.microsoft.com/DeployOffice/assess-office-365-proplus). Cette évaluation inclut la configuration requise, les informations des appareils de vos clients (par exemple, les architectures et les langues requises), les conditions de licence, la capacité réseau et la compatibilité des applications. L’exécution de l’évaluation vous aidera à prendre des décisions clés dans le cadre de la planification de votre déploiement.

## <a name="step-2-plan-your-deployment"></a>Étape 2 : planifier votre déploiement

Après avoir évalué votre environnement, suivez les instructions indiquées dans l’article [Planification de votre déploiement de Microsoft 365 Apps pour entreprise](https://docs.microsoft.com/DeployOffice/plan-office-365-proplus) pour créer un plan de déploiement. Ce plan implique les décisions suivantes : 

- Déploiement d’Office, notamment quel outil utiliser (par exemple, Microsoft Endpoint Configuration Manager ou l’outil Déploiement d’Office) et où installer Office
- Comment gérer les mises à jour d’Office
- Les canaux de mise à jour à utiliser (les canaux de mise à jour pour Office contrôlent la fréquence à laquelle vos utilisateurs reçoivent des mises à jour de fonctionnalités pour leurs applications Office)
- Les packages d’installation Office et les groupes de déploiement que vous voulez utiliser, y compris les applications Office et les langues qui doivent être installées pour les utilisateurs

L’[article de planification](https://docs.microsoft.com/DeployOffice/plan-office-365-proplus) comporte des recommandations pour toutes ces options, y compris la gestion de votre déploiement, la gestion de vos mises à jour, la définition des packages d’installation et la création de groupes de déploiement. 

## <a name="step-3-deploy"></a>Étape 3 : déployer

En fonction de votre plan de déploiement, choisissez le mode de déploiement parmi les possibilités suivantes :

- **[Déployer Microsoft 365 Apps pour entreprise avec le Gestionnaire de configuration](https://docs.microsoft.com/deployoffice/deploy-office-365-proplus-with-system-center-configuration-manager) :** gérez votre déploiement avec le Gestionnaire de configuration, puis téléchargez et déployez Office à partir de points de distribution sur votre réseau.

- **[Déployer Microsoft 365 Apps pour entreprise avec l’outil Déploiement d’Office à partir du cloud](https://docs.microsoft.com/deployoffice/deploy-office-365-proplus-from-the-cloud) :** gérez votre déploiement avec l’outil Déploiement d’Office et installez Office directement sur des appareils clients à partir du CDN d’Office
 
- **[Installer soi-même Microsoft 365 Apps pour entreprise à partir du portail Office](https://docs.microsoft.com/deployoffice/manage-software-download-settings-office-365) :** gérez votre déploiement à partir du portail Office et demandez à vos utilisateurs d’installer Office directement sur leurs appareils clients à partir du portail

De nombreuses organisations utilisent une combinaison de ces options pour différents utilisateurs. Par exemple, une organisation peut utiliser Configuration Manager pour déployer Office pour la plupart de ses utilisateurs, mais activer l’installation autonome pour un petit groupe de collaborateurs qui ne sont pas fréquemment connectés au réseau interne. 

Si votre organisation utilise Configuration Manager, nous vous recommandons de procéder à la mise à niveau vers la branche actuelle et de procéder à la mise à jour vers la version actuelle. Pour obtenir plus d’informations, consultez l’article [Quelle branche de Configuration Manager dois-je utiliser ?](https://docs.microsoft.com/configmgr/core/understand/which-branch-should-i-use)

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Découvrez comment les experts Microsoft [déploient et gèrent les mises à jour de Microsoft 365 Apps pour entreprise](https://www.microsoft.com/itshowcase/deploying-and-managing-microsoft-365#primaryR7).

## <a name="how-contoso-did-microsoft-365-enterprise"></a>Comment Contoso est-elle passée à Microsoft 365 Entreprise ?

Découvrez comment Contoso Corporation, une entreprise multinationale fictive mais représentative, [a déployé Microsoft 365 Apps pour entreprise](contoso-o365pp.md).

![Société Contoso](../media/contoso-overview/contoso-icon.png)

## <a name="next-step"></a>Étape suivante

[Critères de sortie de l’infrastructure Microsoft 365 Apps pour entreprise](office365proplus-exit-criteria.md)
