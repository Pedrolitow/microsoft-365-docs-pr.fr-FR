---
title: Infrastructure Windows 10 entreprise pour Microsoft 365 entreprise
description: Fournit un guide de haut niveau sur les étapes à suivre pour déployer Windows 10 Entreprise sur les ordinateurs dans le cadre de Microsoft 365 Entreprise.
keywords: Microsoft 365, Microsoft 365 Entreprise, documentation Microsoft 365, Windows 10 Entreprise, déploiement
author: greg-lindsay
localization_priority: Normal
ms.collection: M365-modern-desktop
audience: microsoft-business
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 09/18/2018
ms.author: greglin
ms.openlocfilehash: 450b14fb82483bd83e0c83dace173540d0281868
ms.sourcegitcommit: 12fbb429dba7517220191d90816e235583943fe0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "33623128"
---
# <a name="phase-3-windows-10-enterprise"></a>Phase 3 : Windows 10 Entreprise

![](./media/deploy-foundation-infrastructure/win10enterprise_icon.png)

Microsoft 365 Enterprise comprend Windows 10 entreprise, qui vous offre les outils permettant d’en faire plus et de rester sécurisé. Windows 10 entreprise:

- **Est intégré** à la simplicité: Tirez parti de la puissance du nuage pour réduire la complexité de la gestion de l’environnement informatique moderne d’aujourd’hui, quelle que soit la taille.
- **Offre une sécurité intelligente** : il s’agit de la version de Windows la plus sécurisée jamais créée, avec des fonctionnalités de sécurité intelligentes conçues pour collaborer davantage afin de mieux protéger votre organisation.
- **Active la créativité et le travail d’équipe** : déverrouille la créativité et le travail d’équipe pour fournir l’expérience la plus productive que les utilisateurs et le service informatique adoreront.

Vous devez comprendre les différentes façons de déployer le système d’exploitation Windows 10 et choisir celle qui convient à votre organisation. En fonction de votre abonnement entreprise Microsoft 365, il existe également des fonctionnalités de sécurité et de services Windows 10 que vous devrez configurer pour tirer le meilleur parti de Windows 10.

Windows 10 permet ces scénarios d’entreprise stratégiques pour Microsoft 365 Enterprise:

- Exploiter les connaissances et l’expertise collectives en encourageant les personnes à découvrir, partager et faire circuler des fichiers, des informations et des idées au sein de votre entreprise
- Travailler en toute sécurité avec votre appareil en tout lieu et à tout moment pour atteindre plus d’objectifs, en conservant une méthode de travail flexible
- Assurer la tranquillité d’esprit grâce à des contrôles et une visibilité sur votre conformité, vérifiée par le secteur, avec les normes internationales
- Protéger vos informations et réduire le risque de perte de données
- Détecter et se protéger contre les menaces externes: Surveillez, signalez et analysez l’activité pour réagir rapidement afin d’assurer la sécurité de l’organisation.
- Protéger vos utilisateurs et leurs comptes
- Assurer pour votre organisation un niveau supérieur de confidentialité et de conformité au Règlement général sur la protection des données (RGPD)
- Rester informé sur vos appareils et logiciels de bureau, en réduisant les risques pour la sécurité et en maximisant l’efficacité du service informatique

Pour plus d’informations, reportez-vous à la page relative à la [transformation numérique avec Microsoft 365](http://transform.microsoft.com). 

>[!Note]
>Pour déployer Windows 10 Entreprise et Office 365 ProPlus ensemble, puis passer à un [bureau moderne](https://www.microsoft.com/microsoft-365/modern-desktop), reportez-vous au [centre de déploiement de bureau moderne](http://aka.ms/howtoshift).
>

## <a name="windows-10-deployment"></a>Déploiement de Windows 10

Il existe plusieurs façons de déployer Windows 10 entreprise pour votre organisation. Ici, nous allons nous concentrer sur la configuration et le déploiement d’une image Windows 10 entreprise par le biais de ces scénarios de déploiement modernes.

| Scénario de déploiement | Quand l’utiliser |
|:--- |:--- |
| [Utilisation de System Center Configuration Manager en tant que mise à niveau sur place](windows10-deploy-inplaceupgrade.md) | Sélectionnez cette option si vous devez mettre à niveau les ordinateurs Windows 7 ou Windows 8,1 vers la <a href="https://aka.ms/windows-10-release-information" target="_blank">version actuelle</a> de Windows 10 entreprise et que vos ordinateurs sont actuellement gérés avec <a href="https://aka.ms/introtosccm" target="_blank">System Center Configuration Manager (branche actuelle)</a>. |
| [Utilisation de Windows AutoPilot](windows10-deploy-autopilot.md) | Sélectionnez cette option si vous configurez de nouveaux ordinateurs Windows sur lesquels Windows 10 entreprise, version 1703 ou ultérieure est préinstallé. Les utilisateurs finaux vont lancer le programme d’installation à l’aide de la configuration souhaitée en saisissant leurs informations d’identification de compte professionnel ou scolaire. |

Si ces scénarios de déploiement ne répondent pas aux besoins de votre organisation, vous pouvez en savoir plus sur les autres scénarios et comprendre les capacités et les limites de chacune d’elles dans les [scénarios de déploiement de Windows 10](https://docs.microsoft.com/windows/deployment/windows-10-deployment-scenarios). Vous pouvez également <a href="https://aka.ms/planforwin10deployment" target="_blank">planifier le déploiement de Windows 10 par</a> vous-même.

Pour en savoir plus sur Windows 10, consultez les articles suivants:

- [Page du produit Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise)
- [Windows 10](https://docs.microsoft.com/windows/windows-10)
- [Déployer et mettre à jour Windows 10](https://docs.microsoft.com/windows/deployment/)


## <a name="additional-services-and-features"></a>Autres services et fonctionnalités
Dans le cadre de votre déploiement de Windows 10 entreprise, vous pouvez ajouter ces services et fonctionnalités supplémentaires.

### <a name="windows-analytics"></a>Windows Analytics

Windows utilise les données de diagnostic pour fournir des informations riches et exploitables afin de vous aider à obtenir une vue d’ensemble approfondie de l’efficacité opérationnelle et de l’intégrité des appareils Windows 10 dans votre environnement.

* La préparation à la mise à niveau vous permettra de passer à Windows 10 et de rester au fait des nouvelles mises à jour de fonctionnalités Windows 10. 
* Mise à jour conformité-la conformité des mises à jour est destinée à l’administrateur informatique qui souhaite obtenir une vue holistique de tous ses appareils Windows 10, sans besoin d’infrastructure supplémentaire.
* Intégrité de l’appareil: vous pouvez utiliser l’intégrité de l’appareil pour détecter et résoudre les problèmes liés aux utilisateurs finaux de manière proactive.

Pour plus d’informations, consultez la rubrique [vue d’ensemble de Windows Analytics](https://docs.microsoft.com/windows/deployment/update/windows-analytics-overview) .

### <a name="windows-security"></a>Sécurité Windows

Windows 10 offre des fonctionnalités pour vous aider à vous protéger contre les menaces, à sécuriser vos appareils et à faciliter le contrôle d’accès. Avec Windows 10, vous disposez de fonctionnalités de sécurité importantes qui protègent votre appareil directement depuis le début. Microsoft 365 E3 ajoute des fonctionnalités de sécurité telles que Windows Hello entreprise, le contrôle d’application Windows Defender et la protection des informations Windows. Avec Microsoft 365 E5, vous bénéficiez de toutes les fonctionnalités de protection de Microsoft 365 E3 Security plus, ainsi que de la protection avancée contre les menaces Windows Defender. 

Pour en savoir plus sur les fonctionnalités de sécurité fournies avec Windows 10 entreprise et obtenir des conseils sur la façon dont vous pouvez déployer, gérer, configurer et dépanner trois fonctionnalités de la fonctionnalité ecurity, consultez [étape 5: déployer des fonctionnalités de sécurité Windows 10 entreprise](windows10-enable-security-features.md).

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Jetez un œil à Microsoft et découvrez comment l’entreprise [a déployé Windows 10 entreprise et utilise une authentification forte, Intune et Windows Defender ATP](https://www.microsoft.com/en-us/itshowcase/deploying-and-managing-microsoft-365#primaryR6).

## <a name="how-contoso-did-microsoft-365-enterprise"></a>Comment Contoso est-elle passée à Microsoft 365 Entreprise ?

Découvrez comment Contoso Corporation, une entreprise multinationale fictive mais représentative, a [déployé Windows 10 entreprise](contoso-win10.md).

![](./media/contoso-overview/contoso-icon.png)

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step1.png)| [Préparer votre organisation pour Windows 10 Entreprise](windows10-prepare-your-org.md) |
