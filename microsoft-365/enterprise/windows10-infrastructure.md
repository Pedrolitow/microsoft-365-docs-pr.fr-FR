---
title: Infrastructure Windows 10 Enterprise pour Microsoft 365 pour entreprises
description: Fournit un guide de haut niveau sur les étapes à suivre pour déployer Windows 10 Entreprise sur les ordinateurs dans le cadre de Microsoft 365 Entreprise.
keywords: Microsoft 365, Microsoft 365 Entreprise, documentation Microsoft 365, Windows 10 Entreprise, déploiement
author: greg-lindsay
localization_priority: Normal
audience: microsoft-business
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 09/18/2018
ms.author: greglin
ms.openlocfilehash: 80d7c1b56434647387b9c428ca07effdff929abf
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866843"
---
# <a name="phase-3-windows-10-enterprise"></a>Phase 3 : Windows 10 Entreprise

![](./media/deploy-foundation-infrastructure/win10enterprise_icon.png)

Microsoft 365 entreprise inclut Windows 10 entreprise, qui fournit les outils d’en faire plus rester sécurisé. Entreprise Windows 10 :

- **Est intégré par souci de simplicité** - atelier de la puissance du cloud pour aider à réduire la complexité de la gestion d’aujourd'hui s environnement périphérique informatique moderne, quelle que soit la taille.
- **Sécurité intelligent** - il s’agit de la version de Windows plus sécurisée jamais, avec une sécurité intelligente les fonctionnalités qui sont conçues pour fonctionner ensemble afin de mieux protègent votre organisation.
- **Permet la création et le travail d’équipe** - déverrouiller la création et le travail d’équipe pour fournir plus productifs expérience qui utilisateurs et sera informatique aime.

Vous devez comprendre les différentes façons, vous pouvez déployer le système d’exploitation Windows 10 et choisir la bonne pour votre organisation. Selon votre abonnement Microsoft 365 pour entreprises, il existe également Windows 10 services et fonctionnalités de sécurité que vous aurez besoin pour tirer le meilleur parti de Windows 10.

10 Windows active ces scénarios stratégique pour Microsoft 365 pour entreprises :

- Exploiter les connaissances et l’expertise collectives en encourageant les personnes à découvrir, partager et faire circuler des fichiers, des informations et des idées au sein de votre entreprise
- Travailler en toute sécurité avec votre appareil en tout lieu et à tout moment pour atteindre plus d’objectifs, en conservant une méthode de travail flexible
- Assurer la tranquillité d’esprit grâce à des contrôles et une visibilité sur votre conformité, vérifiée par le secteur, avec les normes internationales
- Protéger vos informations et réduire le risque de perte de données
- Détecter et de protection contre l’état des menaces externes--moniteur et d’analyser les activités pour répondre rapidement pour fournir la sécurité de l’organisation
- Protéger les utilisateurs et leurs comptes
- Assurer pour votre organisation un niveau supérieur de confidentialité et de conformité au Règlement général sur la protection des données (RGPD)
- Rester informé sur vos appareils et logiciels de bureau, en réduisant les risques pour la sécurité et en maximisant l’efficacité du service informatique

Pour plus d’informations, reportez-vous à la page relative à la [transformation numérique avec Microsoft 365](http://transform.microsoft.com). 

>[!Note]
>Pour déployer Windows 10 Entreprise et Office 365 ProPlus ensemble, puis passer à un [bureau moderne](https://www.microsoft.com/microsoft-365/modern-desktop), reportez-vous au [centre de déploiement de bureau moderne](http://aka.ms/howtoshift).
>

## <a name="windows-10-deployment"></a>Déploiement de Windows 10

Il existe plusieurs façons, vous pouvez déployer Windows 10 entreprise pour votre organisation. Ici, nous nous concentrerons sur la façon dont vous pouvez configurer et déployer une image Windows 10 entreprise par le biais de ces scénarios de déploiement moderne.

| Scénario de déploiement | Quand l’utiliser |
|:--- |:--- |
| [À l’aide de System Center Configuration Manager en tant qu’une mise à niveau sur place](windows10-deploy-inplaceupgrade.md) | Sélectionnez cette option si vous devez mettre à niveau de Windows 7 ou Windows 8.1 ordinateurs vers la <a href="https://aka.ms/windows-10-release-information" target="_blank">version actuelle</a> de Windows 10 Enterprise et vos ordinateurs sont actuellement gérées avec <a href="https://aka.ms/introtosccm" target="_blank">System Center Configuration Manager (branche actuelle)</a>. |
| [À l’aide de pilote Windows](windows10-deploy-autopilot.md) | Sélectionnez cette option si vous configurez de nouveaux ordinateurs Windows qui ont Windows 10 Enterprise, version 1703 ou version ultérieure préinstallée. Les utilisateurs finaux seront démarrer le programme d’installation à l’aide de la configuration de votre choix en saisissant leur travail ou établissement des informations d’identification du compte. |

Si ces scénarios de déploiement n’entrent pas les besoins de votre organisation, vous pouvez en savoir plus sur les autres scénarios et comprendre les fonctionnalités et limitations de chaque dans [les scénarios de déploiement de Windows 10](https://docs.microsoft.com/windows/deployment/windows-10-deployment-scenarios). Vous pouvez également <a href="https://aka.ms/planforwin10deployment" target="_blank">planifier un déploiement Windows 10</a> sur votre propre.

Vous en apprendrez plus sur Windows 10 avec ces articles :

- [Page du produit Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise)
- [Windows 10](https://docs.microsoft.com/windows/windows-10)
- [Déployer et mettre à jour Windows 10](https://docs.microsoft.com/windows/deployment/)


## <a name="additional-services-and-features"></a>Fonctionnalités et services supplémentaires
Dans le cadre de votre déploiement de contenu d’entreprise Windows 10, vous pouvez ajouter ces fonctionnalités et des services supplémentaires.

### <a name="windows-analytics"></a>Windows Analytics

Windows utilise les données de diagnostic pour fournir des informations pour vous aider à comprendre en profondeur des efficacité opérationnelle et l’intégrité de Windows 10 périphériques dans votre environnement riches et exploitables.

* Mise à niveau de préparation - préparation de mise à niveau vous aidera à atteindre 10 Windows et restez informé des nouvelles mises à jour Windows 10 fonctionnalité. 
* Conformité de la mise à jour - conformité de la mise à jour est destinée à l’administrateur informatique souhaitant obtenir une vue globale de tous leurs périphériques Windows 10, sans les exigences d’infrastructure supplémentaire.
* État de santé -, vous pouvez utiliser l’intégrité du périphérique détecter de manière proactive et résoudre les problèmes de l’utilisateur final du.

Pour plus d’informations, voir [Vue d’ensemble de Windows Analytique](https://docs.microsoft.com/windows/deployment/update/windows-analytics-overview) .

### <a name="windows-security"></a>Sécurité de Windows

Windows 10 fournit des fonctionnalités pour vous aider à protéger contre les menaces, aide sécuriser vos périphériques et vous aider avec contrôle d’accès. 10 Windows, vous offre des fonctionnalités critiques de sécurité qui protègent votre droit de périphérique à partir du début. Microsoft 365 E3 ajoute des fonctionnalités de sécurité tels que Windows Hello pour les entreprises, contrôle de l’Application Windows Defender et Protection des informations. Avec Microsoft 365 E5, vous obtenez tous les la protection de sécurité Microsoft 365 E3 ainsi que des fonctionnalités de sécurité basée sur le cloud et Windows Defender avancée protection contre les menaces. 

Pour en savoir plus sur les fonctionnalités de sécurité que vous obtenez avec Windows 10 entreprise et les instructions get sur comment déployer, gérer, configurer et résoudre les trois fonctionnalités principales écurité, voir [étape 5 : fonctionnalités de sécurité déployer Windows 10 entreprise](windows10-enable-security-features.md).

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Pour lire à l’intérieur de Microsoft et découvrez comment la société planifiées pour, déployé et est la gestion des mises à jour pour Windows 10, voir :

- [Préparation de votre organisation pour un déploiement en douceur de Windows 10](https://www.microsoft.com/itshowcase/windows10deployment?wt.mc_id=bmkg_itsc)
- [Adoption de Windows as a service chez Microsoft](https://www.microsoft.com/itshowcase/Article/Content/851/Adopting-Windows-as-a-service-at-Microsoft)
- [Déploiement de Windows 10 chez Microsoft en tant que mise à niveau sur place](https://www.microsoft.com/itshowcase/Article/Content/668/Deploying-Windows-10-at-Microsoft-as-an-inplace-upgrade)
- [Implémentation d’une authentification utilisateur forte avec Windows Hello Entreprise](https://www.microsoft.com/itshowcase/Article/Content/756/Implementing-strong-user-authentication-with-Windows-Hello-for-Business)
- [Déploiement de Windows 10 : conseils et astuces de Microsoft IT](https://www.microsoft.com/itshowcase/Article/Content/951/Windows-10-deployment-tips-and-tricks-from-Microsoft-IT) (vidéo)
- [Windows Defender ATP facilite la détection des menaces complexes](https://www.microsoft.com/itshowcase/Article/Content/854/Windows-Defender-ATP-helps-detect-sophisticated-threats)
- [Sécurisation de l’entreprise moderne avec Windows Defender et Windows Defender ATP](https://www.microsoft.com/itshowcase/Article/Content/903/Securing-the-modern-enterprise-with-Windows-Defender-and-Windows-Defender-ATP) (vidéo)

## <a name="how-contoso-did-microsoft-365-enterprise"></a>Comment Contoso est-elle passée à Microsoft 365 Entreprise ?

Voir comment la société Contoso, une entreprise multinationale fictive mais représentative, [déployé Windows 10 Enterprise](contoso-win10.md).

![](./media/contoso-overview/contoso-icon.png)

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step1.png)| [Préparer votre organisation pour Windows 10 Entreprise](windows10-prepare-your-org.md) |
