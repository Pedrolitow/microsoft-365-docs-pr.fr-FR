---
title: 'Étape 7 : maintenance de Windows et d’Office'
f1.keywords:
- NOCSH
ms.author: jogruszc
author: JGruszczyk
manager: jemed
ms.date: 05/20/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Découvrez comment préparer la maintenance de Windows et d’Office au sein de votre environnement.
ms.openlocfilehash: e9de339c6bc66e5cd3c02af5f6a53c32b7573b1f
ms.sourcegitcommit: 584e2e9db8c541fe32624acdca5e12ee327fdb63
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "44679001"
---
# <a name="step-7-windows-and-office-servicing"></a>Étape 7 : maintenance de Windows et d’Office

![](../media/step-7-windows-and-office-as-a-service-media/step-7-windows-and-office-as-a-service-media-1.png)

<table>
<thead>
<td><img src="../media/desktop-deployment-center-home-media/desktop-deployment-center-home-media-10.png" alt="Step 7" height="144" width="144" /></td>
<td><p><strong>Étape 7 : maintenance de Windows et d’Office</strong></p>
<p>Both Windows 10 and Microsoft 365 Apps for enterprise continually add new capabilities to keep bringing user experiences and security forward with the latest innovations. Learn how to stay current with semi-annual and monthly updates, how the new servicing model works and the tools and options you have.</p></td>
<td><a href="https://aka.ms/ddev7" target="_blank"><img src="../media/desktop-deployment-center-home-media/desktop-deployment-center-home-media-20.png" alt="Step 7" height="130" width="231" /></a></td>
</thead>
</table>

>[!NOTE]
>La maintenance de Windows et d’Office est la septième étape de notre processus de déploiement recommandé. Elle couvre le volet planification de la préparation du déploiement des mises à jours semi-annuelles des fonctionnalités. Pour voir le processus complet de déploiement du bureau, visitez le [Centre de déploiement du bureau moderne](https://aka.ms/HowToShift).
>

Windows 10 et Microsoft 365 Apps pour entreprise introduisent de nouveaux modèles de support, options de maintenance et chronologies de mise à jour. Ces modifications simplifient le processus de mise à jour des fonctionnalités. Ces mises à jour sont accompagnées de nouvelles options de configuration permettant de mettre en œuvre des plans de maintenance conformes à vos besoins. Apprenons à préparer les mises à jour du canal semestriel de façon à bénéficier des nouvelles fonctionnalités et fonctionnalités de Windows 10 et de Microsoft 365 Apps pour entreprise, tout en tirant parti des nouvelles fonctionnalités dans Microsoft Endpoint Configuration Manager (Current Branch).

[Aider les clients à passer à Windows 10 et Microsoft 365 Apps pour entreprise](https://www.microsoft.com/microsoft-365/blog/2018/09/06/helping-customers-shift-to-a-modern-desktop/)

## <a name="update-types"></a>Types de mise à jour

Les mises à jour se répartissent en deux grandes catégories : les mises à jour de fonctionnalités, et les mises à jour de qualité et de sécurité contenant des correctifs cumulatifs de sécurité, de fiabilité et de bogues. En termes de fréquence, Windows et Office proposent un canal semi-annuel qui fournit de nouvelles fonctionnalités deux fois par an, aux alentours de mars et de septembre, tandis que les mises à jour de qualité et de sécurité sont publiées mensuellement. De plus, pour les applications Office 365, nous proposons un canal actuel entièrement pris en charge fournissant des mises à jour de fonctionnalités et de qualité.

Si vous avez l’habitude d’un cycle lent entre le système d’exploitation du bureau et les mises à jour de l’application, vous vous posez sûrement des questions :

  - Les mises à jour seront-elles compatibles ?

  - Devrai-je continuer de former mes utilisateurs ?

  - Quels sont les risques ?

Pour répondre à ces questions et vous expliquer pourquoi nous avons décidé de vous proposer de nouvelles fonctionnalités plus régulièrement, nous vous présentons quelques-uns des avantages de cette approche.

### <a name="feature-update-benefits"></a>Avantages des mises à jour de fonctionnalité

First, we’ve moved away from the model of the past that would introduce huge waves of change around every three years to now incremental smaller changes with feature updates twice per year. Why? With technology trends moving so fast in addition to rapidly evolving security threats, this keeps experiences and protections current. Some of the security related updates for example can’t just be delivered by monthly security updates or antivirus signature files; they may be low-level changes platform, like virtualization-based security.

[Guide rapide sur Windows as a Service](https://docs.microsoft.com/windows/deployment/update/waas-quick-start)

[Atténuation des menaces à l’aide des fonctionnalités de sécurité Windows 10](https://docs.microsoft.com/windows/security/threat-protection/overview-of-threat-mitigations-in-windows-10%20%20)

### <a name="cumulative-update-model-benefits"></a>Avantages du modèle des mises à jour cumulatives

Second delivering quality and security updates as a cumulative update package corrects many of the issues of the past. It used to be that you might pick and choose sometimes from a dozen updates or more each month for both Windows and Office. As you can imagine, this creates a nearly impossible set of test matrices for support. Also, if you install a version of Windows or Office that is a year or more old, it might take hours or sometimes days to apply all updates delivered since that version was released.

With the cumulative model, you’re always one update away from being current and in doing so the number of monthly updates that you need to deploy is reduced. Each update builds upon updates from previous months and contains all of the fixes that you need to get current. Cumulative updates are especially helpful when PCs has been turned off for several months because they are in storage waiting to be reassigned to a different user.

### <a name="expanded-validation-of-updates"></a>Validation étendue des mises à jour

Un autre avantage est qu’avant de déployer des mises à jour pour un déploiement de grande ampleur, nous publions des builds via les programmes Insider pour [Office](https://products.office.com/office-insider?tab=Windows-Desktop) et [Windows](https://insider.windows.com/) de façon à recueillir des données de diagnostic et des commentaires avant de publier les mises à jour à grande échelle. Les programmes Insider étant désormais ouverts à tous les utilisateurs, vous pouvez prendre une longueur d’avance dans la compréhension des mises à jour. Avant de publier les mises à jour, nous récoltons des données de diagnostic de millions de configurations de sorte que, lors du déploiement, la qualité est plus prévisible.

De plus, dans la mesure où les builds Insider de Microsoft 365 Apps pour entreprise reflètent les mises à jour du canal mensuel, si vous utilisez le canal semestriel d’Office pour distribuer deux fois par an des mises à jour de fonctionnalité compatibles avec Windows, vous pouvez rapidement valider les builds à l’aide des versions du canal entreprise semestriel (préversion).

### <a name="supporting-management-tools"></a>Prise en charge des outils de gestion

We've also thought through how to make the deployment of updates seamless to you. Configuration Manager (Current Branch) is updated frequently to support the roll-out of these updates to Windows and Office and any new capabilities.

[Déployer les mises à jour de Windows 10 avec le gestionnaire de configuration](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-configuration-manager)

[Gérer les applications Microsoft 365 Apps pour entreprise avec le Gestionnaire de configuration](https://docs.microsoft.com/mem/configmgr/sum/deploy-use/manage-office-365-proplus-updates)

## <a name="overview-of-windows-and-office-channels"></a>Vue d’ensemble des canaux Windows et Office

Windows 10 offre trois canaux de maintenance :

- [**Programme Windows Insider**](https://docs.microsoft.com/windows/deployment/update/waas-overview#windows-insider) permettant aux organisations de tester et commenter les fonctionnalités de la prochaine mise à jour fonctionnelle
- **Canal semi-annuel** délivrant de nouvelles fonctionnalités au travers deux publications annuelles de mises à jour de fonctionnalités
- **Canal de maintenance à long terme** destiné uniquement à des appareils spécialisés nécessitant une option de maintenance plus longue

Microsoft 365 propose quatre canaux de maintenance :

- [**Programme Office Insider** ](https://products.office.com/office-insider) permettant aux organisations de tester et commenter les nouvelles fonctions et fonctionnalités d’Office en cours de développement
- **Canal actuel** fournissant aux utilisateurs les fonctionnalités Office les plus récentes dès qu’elles sont disponibles
- **Canal entreprise semi-annuel** fournissant de nouvelles fonctionnalités deux fois par an
- **Canal entreprise semi-annuel (préversion)** version d’Office bénéficiant d’un support intégral, qui permet à des utilisateurs pilotes ainsi qu’à des testeurs de compatibilité de tester et valider le canal entreprise semi-annuel suivant

Pour plus d’informations sur les canaux de maintenance de Windows et d’Office, voir la documentation ci-dessous :

- [Vue d’ensemble de Windows as a service](https://docs.microsoft.com/windows/deployment/update/waas-overview#servicing-channels)
- [Présentation des canaux de mise à jour des Applications Microsoft 365](https://docs.microsoft.com/DeployOffice/overview-update-channels#BKMK_SAC)

## <a name="phased-deployment-of-updates"></a>Déploiement progressif des mises à jour

Now let’s shift gears to how you will roll out these updates. For any release, we recommend at least three deployment phases for IT – validation, piloting and broad production deployment. Once you’re up and running on Windows 10 and Microsoft 365 Apps for enterprise, you'll use monthly servicing to stay current with critical security and quality updates, then you’ll move to semi-annual servicing for new features.

### <a name="monthly-updating"></a>Mise à jour mensuelle

The service model is designed so you can choose to limit the roll-out of new features to twice per year, and if needed you can even skip a semi-annual update and continue receiving quality and security updates. As mentioned, the cumulative nature of monthly updates means each will increase in size per month.

#### <a name="express-updates"></a>Mises à jour rapides

Using a technology called "Express Updates" in Windows and Binary Delta Compression in Office, we can reduce the download size significantly. In both approaches, the update engines compare what’s on the PC and finds only the differentials needed to update what’s there.

[Explication des mises à jour de qualité Windows 10 et fin des mises à jour delta](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-10-quality-updates-explained-amp-the-end-of-delta/ba-p/214426)

Windows Update pour Entreprise et Windows Server Update Services ont pris en charge les mises à jour rapides pendant un certain temps. Désormais, les mises à jour rapides sont aussi prises en charge dans le gestionnaire de configuration Microsoft Endpoint (Current Branch).

![](../media/step-7-windows-and-office-as-a-service-media/step-7-windows-and-office-as-a-service-media-3.png)

#### <a name="binary-delta-compression"></a>Compression Delta binaire

Dans Office, la Compression Delta binaire est utilisée seulement si vous mettez à jour la version la plus récente de Microsoft 365 Apps pour entreprise. Ainsi, pour utiliser cette approche, mettez à jour le build précédent et installez toutes les mises à jour sans exception.

Windows and Office update channels can be managed via Configuration Manager using the standard approval and targeting process. Additionally, you can use policy settings in Office and Windows to enforce update channels used, as well as related settings.

### <a name="semi-annual-updates"></a>Mises à jour semi-annuelles

Vous savez tout sur les mises à jour mensuelles. Maintenant, nous allons nous pencher sur les mises à jour semi-annuelles.

Comme nous l’avons abordé dans l’article sur la préparation des applications et des appareils, nous vous recommandons de commencer à préparer le déploiement de ces mises à jour volumineuses en utilisant les mêmes outils de préparation configurés à l’étape 1 du processus de déploiement.

As for tooling, you can use policy settings with Windows Update for Business, software update management via Microsoft Endpoint Configuration Manager (Current Branch), Windows Server Update Services (WSUS), or update policies set by Microsoft Intune. If you are concerned about network bandwidth, see Step 2: Directory and Network Readiness, to learn about your options to reduce network traffic via Delivery Optimization and other peer to peer caching technologies.

![](../media/step-7-windows-and-office-as-a-service-media/step-7-windows-and-office-as-a-service-media-4.png)

[Canal semi-annuel Windows](https://docs.microsoft.com/windows/deployment/update/waas-overview#semi-annual-channel)

[Canal entreprise semi-annuel pour Microsoft 365 Apps](https://docs.microsoft.com/DeployOffice/overview-update-channels#BKMK_SAC)

#### <a name="upgrade-task-sequences"></a>Séquences de tâches de mise à niveau

L’installation des mises à jour de fonctionnalité volumineuses en utilisant des méthodes de gestion de mise à jour logicielle standard est prise en charge, mais bon nombre d’organisations choisiront d’utiliser une séquence de tâches de mise à niveau avec le gestionnaire de configuration Microsoft Endpoint (Current Branch) ou Microsoft Deployment Toolkit.

Une séquence de tâches vous permet de créer des vérifications ou des tâches personnalisées AVANT d’installer la mise à jour de fonctionnalité et d’exécuter des tâches personnalisées APRÈS l’installation de la mise à jour. Les tâches postérieures à la mise à jour peuvent inclure des services de suspension temporaire si besoin pendant la mise à jour, l’installation et le remplacement du pilote, les mises à niveau ou la barre des tâches de l’application, et les paramètres de personnalisation du démarrage de Windows 10.

![](../media/step-7-windows-and-office-as-a-service-media/step-7-windows-and-office-as-a-service-media-5.png)

If you’re already using task sequences to migrate your Windows 7 machines to Windows 10 and are well-versed with those tools, this is a great place to start and provides ultimate control. While you can use a single task sequence for the entire upgrade, it is quite common that organizations use two task sequences. One task sequence for making sure the machines are ready for the upgrade, that silently pre-stages all the required setup files on target computers, and one to do the actual upgrade. This approach ensures that your user productivity is less impacted.

[Créer une séquence de tâches pour mettre à niveau un système d’exploitation dans le gestionnaire de configuration](https://docs.microsoft.com/mem/configmgr/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system)

#### <a name="semi-annual-channel-support-for-feature-updates"></a>Prise en charge du canal semi-annuel pour les mises à jour de fonctionnalité

[Comme annoncé en septembre 2018](https://www.microsoft.com/microsoft-365/blog/2018/09/06/helping-customers-shift-to-a-modern-desktop/), le calendrier de prise en charge des mises à jour du canal semi-annuel suivra le modèle suivant.

  - Toutes les mises à jour de fonctionnalité de Windows 10 Entreprise et Éducation actuellement prises en charge, dès la version 1607, seront prises en charge pendant 30 mois à compter de la date de publication de leur version originale.

  - Toutes les futures mises à jour de fonctionnalité, dès la version 1809, prévue en septembre, seront prises en charge pendant 30 mois à compter de la date de leur publication.

  - Les mises à jour de fonctionnalité prévues en mars, dès la version 1903, continueront d’être prises en charge pendant 18 mois à compter de la date de leur publication.

  - Les mises à jour semestrielles de Microsoft 365 Apps pour entreprise continuent d’être prises en charge pendant 18 mois.

#### <a name="additional-setup-automation-options-outside-of-task-sequences"></a>Autres options d’installation automatisée en dehors des séquences de tâches

Si vous n’utilisez pas les séquences de tâches de mise à niveau, vous pouvez désormais exécuter des actions personnalisées ou appliquer des fichiers du pilote pendant les mises à jour de fonctionnalité durant la phase préalable à l’installation (avant que le programme d’installation exécute ses vérifications de compatibilité), ou durant la phase préalable à la validation (avant l’application de la mise à niveau).

[Nouveautés concernant l’installation de la version 1803 de Windows 10](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1803%23windows-setup)

## <a name="next-step"></a>Étape suivante 

## <a name="step-8-user-communications-and-training"></a>[Étape 8 : formation et communications des utilisateurs](https://aka.ms/mdd8)

## <a name="previous-step"></a>Étape précédente 

## <a name="step-6-os-deployment-and-feature-updates"></a>[Étape 6 : déploiement du système d’exploitation et mises à jour des fonctionnalités](https://aka.ms/mdd6)
