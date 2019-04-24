---
title: 'Phase 4 : Office 365 ProPlus'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Étapes du déploiement de l’infrastructure Office 365 ProPlus pour Microsoft 365 Entreprise.
ms.openlocfilehash: c4fc3805dd2ea97e1a9797e5adfc31ab83f028ae
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32290939"
---
# <a name="phase-4-office-365-proplus"></a>Phase 4 : Office 365 ProPlus

![](./media/deploy-foundation-infrastructure/O365proplus_icon.png)

*Cela s’applique aux versions E3 et E5 de Microsoft 365 Entreprise et Microsoft 365 Éducation*

Microsoft 365 Entreprise inclut Office 365 ProPlus, la version par abonnement d’Office. Tout comme Office 2016, Office 365 ProPlus inclut toutes les applications Office, et ces applications sont installées directement sur vos appareils clients. Contrairement à Office 2016, Office 365 ProPlus est régulièrement mis à jour afin d’obtenir les nouvelles fonctionnalités et présente un modèle de licence utilisateur qui permet aux utilisateurs d’installer Office sur un maximum de 5 appareils. Pour obtenir plus d’informations, consultez l’article [À propos d’Office 365 ProPlus en entreprise](https://docs.microsoft.com/deployoffice/about-office-365-proplus-in-the-enterprise).

Dans cette phase, vous déployez Office 365 ProPlus sur les appareils clients dans le cadre de Microsoft 365 Entreprise. En plus de ces instructions, nous vous recommandons d’utiliser [Microsoft Fastrack](https://fasttrack.microsoft.com/office) pour vous aider à effectuer votre déploiement. 

Office 365 ProPlus permet de mettre en place les scénarios d’entreprise stratégiques suivants pour Microsoft 365 Entreprise :

- Collaborer sur des documents en temps réel ou à votre rythme afin de simplifier le processus de co-création
- Exploiter les connaissances et l’expertise collectives en encourageant les personnes à découvrir, partager et faire circuler des fichiers, des informations et des idées au sein de votre entreprise
- Permettre aux utilisateurs de transformer les processus d’entreprise et d’accroître l’efficacité
- Gérer les projets, les tâches et les délais pour atteindre vos objectifs métiers
- Utiliser l’assistance intelligente pour la création, l’écriture, la recherche de contenu et bien plus, pour valoriser votre travail
- Rechercher des informations, analyser vos données et partager vos résultats pour aider la prise de décisions éclairées
- Communiquer avec votre équipe afin de rester informé, de demander des informations et de créer une cohésion et un consensus
- Communiquer avec des partenaires, des collègues et des clients dans le monde entier lors d’appels et de réunions en ligne planifiés et ad hoc avec des groupes de toute taille
- Stocker et partager des fichiers internes ou externes à votre entreprise pour travailler en toute transparence au-delà des frontières structurelles
- Travailler en toute sécurité avec votre appareil en tout lieu et à tout moment pour atteindre plus d’objectifs, en conservant une méthode de travail flexible
- Assurer la tranquillité d’esprit grâce à des contrôles et une visibilité sur votre conformité, vérifiée par le secteur, avec les normes internationales
- Protéger vos informations et réduire le risque de perte de données
- Rester informé sur vos appareils et logiciels de bureau, en réduisant les risques pour la sécurité et en maximisant l’efficacité du service informatique

Pour plus d’informations, reportez-vous à la page relative à la [transformation numérique avec Microsoft 365](http://transform.microsoft.com). 

Si vous avez déjà déployé Office 365 ProPlus, consultez les [critères de sortie](office365proplus-exit-criteria.md) de cette phase pour vous assurer que vous répondez aux conditions requises pour Microsoft 365 Entreprise.

>[!Note]
>Pour déployer Windows 10 Entreprise et Office 365 ProPlus ensemble, puis passer à un [bureau moderne](https://www.microsoft.com/microsoft-365/modern-desktop), reportez-vous au [centre de déploiement de bureau moderne](http://aka.ms/howtoshift).
>

## <a name="step-1-assess-your-environment"></a>Étape 1 : évaluer votre environnement

Avant de déployer Office 365 ProPlus, suivez les instructions indiquées dans l’article [Évaluation de votre environnement et de sa configuration requise pour déployer Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/assess-office-365-proplus). Cette évaluation inclut la configuration requise, les informations des appareils de vos clients (par exemple, les architectures et les langues requises), les conditions de licence, la capacité réseau et la compatibilité des applications. L’exécution de l’évaluation vous aidera à prendre des décisions clés dans le cadre de la planification de votre déploiement.

## <a name="step-2-plan-your-deployment"></a>Étape 2 : planifier votre déploiement

Après avoir évalué votre environnement, suivez les instructions indiquées dans l’article [Planification de votre déploiement d’Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/plan-office-365-proplus) pour créer un plan de déploiement. Ce plan implique les décisions suivantes : 

- Comment déployer Office, notamment quel outil utiliser (par exemple, System Center Configuration Manager ou l’outil Déploiement d’Office [ODT]) et où installer Office
- Comment gérer les mises à jour d’Office
- Les canaux de mise à jour à utiliser (les canaux de mise à jour pour Office contrôlent la fréquence à laquelle vos utilisateurs reçoivent des mises à jour de fonctionnalités pour leurs applications Office)
- Les packages d’installation Office et les groupes de déploiement que vous voulez utiliser, y compris les applications Office et les langues qui doivent être installées pour les utilisateurs

L’[article de planification](https://docs.microsoft.com/DeployOffice/plan-office-365-proplus) comporte des recommandations pour toutes ces options, y compris la gestion de votre déploiement, la gestion de vos mises à jour, la définition des packages d’installation et la création de groupes de déploiement. 

## <a name="step-3-deploy"></a>Étape 3 : déployer

En fonction de votre plan de déploiement à l’étape 2, choisissez votre processus de déploiement :

- **[Déployer Office 365 ProPlus avec System Center Configuration Manager](https://docs.microsoft.com/deployoffice/deploy-office-365-proplus-with-system-center-configuration-manager) :** gérez votre déploiement avec Configuration Manager et téléchargez et déployez Office à partir de points de distribution sur votre réseau

- **[Déployer Office 365 ProPlus avec l’outil Déploiement d’Office à partir du cloud](https://docs.microsoft.com/deployoffice/deploy-office-365-proplus-from-the-cloud) :** gérez votre déploiement avec l’outil Déploiement d’Office et installez Office directement sur des appareils clients à partir du CDN d’Office
 
- **[Déployer Office 365 ProPlus avec l’outil Déploiement d’Office à partir d’une source locale](https://docs.microsoft.com/deployoffice/deploy-office-365-proplus-from-a-local-source) :** gérez votre déploiement avec l’outil Déploiement d’Office et téléchargez et déployez Office sur votre réseau à partir d’une source locale  

- **[Installer soi-même Office 365 ProPlus à partir du portail Office](https://support.office.com/article/Download-and-install-or-reinstall-Office-365-or-Office-2016-on-a-PC-or-Mac-4414EAAF-0478-48BE-9C42-23ADC4716658) :** gérez votre déploiement à partir du portail Office et demandez à vos utilisateurs d’installer Office directement sur leurs appareils clients à partir du portail

De nombreuses organisations utilisent une combinaison de ces options pour différents utilisateurs. Par exemple, une organisation peut utiliser Configuration Manager pour déployer Office pour la plupart de ses utilisateurs, mais activer l’installation autonome pour un petit groupe de collaborateurs qui ne sont pas fréquemment connectés au réseau interne. 

Si votre organisation utilise Configuration Manager, nous vous recommandons de procéder à la mise à niveau vers la branche actuelle et de procéder à la mise à jour vers la version actuelle. Pour obtenir plus d’informations, consultez l’article [Quelle branche de Configuration Manager dois-je utiliser ?](https://docs.microsoft.com/sccm/core/understand/which-branch-should-i-use)

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Découvrez comment les experts Microsoft ont planifié et déployé Office 365 ProPlus dans Microsoft 365 Entreprise avec les ressources suivantes :

- [Déploiement et mise à jour de Microsoft Office 365 ProPlus](https://www.microsoft.com/itshowcase/Article/Content/757/Deploying-and-updating-Microsoft-Office-365-ProPlus)
- [Les canaux d’automatisation et de mise à jour facilitent le déploiement de Microsoft Office 365 ProPlus](https://www.microsoft.com/itshowcase/Article/Content/794/Automation-and-update-channels-help-deploy-Microsoft-Office-365-ProPlus) (vidéo)

## <a name="how-contoso-did-microsoft-365-enterprise"></a>Comment Contoso est-elle passée à Microsoft 365 Entreprise ?

Découvrez comment Contoso Corporation, une entreprise multinationale fictive mais représentative, [a déployé Office 365 ProPlus](contoso-o365pp.md).

![](./media/contoso-overview/contoso-icon.png)

## <a name="next-step"></a>Étape suivante

[Critères de sortie de l’infrastructure Office 365 ProPlus](office365proplus-exit-criteria.md)
