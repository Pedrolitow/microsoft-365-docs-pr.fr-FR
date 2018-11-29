---
title: 'Étape 1 : disponibilité des applications et des périphériques'
ms.author: jogruszc
author: JGruszczyk
manager: jemed
ms.date: 09/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Apprenez à évaluer la disponibilité des applications et des périphériques et dans l’environnement.
ms.openlocfilehash: a9fa85ea37de06399aa2264b09c61e588edc2107
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867487"
---
# <a name="step-1-device-and-app-readiness"></a>Étape 1 : disponibilité des applications et des périphériques

Commencez votre projet de déploiement d’ordinateurs de bureau par un inventaire de vos périphériques et applications, puis classez-les par ordre de priorité. Testez les périphériques et les applications privilégiés, puis faites les corrections nécessaires en vue du déploiement.

![](media/step-1-device-and-app-readiness-media/step-1-device-and-app-readiness-media-1.png)

<table>
<thead>
<td><img src="media/desktop-deployment-center-home-media/desktop-deployment-center-home-media-3.png" alt="Step 1" height="130" width="130" /></td>
<td><p><strong>Étape 1 : disponibilité des applications et des périphériques</strong></p>
<p>Commencez votre projet de déploiement d’ordinateurs de bureau par un inventaire de vos périphériques et applications, puis classez-les par ordre de priorité. Testez les périphériques et les applications privilégiés, puis faites les corrections nécessaires en vue du déploiement.</p></td>
<td><a href="https://aka.ms/ddev1" target="_blank"><img src="media/desktop-deployment-center-home-media/desktop-deployment-center-home-media-14.png" alt="Step 1" height="120" width="213" /></a></td>
</thead>
</table>

>[!NOTE]
>La disponibilité des applications et des périphériques est la première étape de notre processus de déploiement recommandé en couvrant les aspects holistiques de la compatibilité du matériel et des applications. Pour afficher l’ensemble du processus de déploiement d’ordinateurs de bureau, visitez le [centre de déploiement moderne d’ordinateurs de bureau](https://aka.ms/HowToShift).
>

La compatibilité du matériel et des applications était autrefois un obstacle majeur à la mise à niveau des ordinateurs de bureau des utilisateurs. La bonne nouvelle lorsque vous planifiez votre déploiement vers Windows 10 et Office 365 ProPlus est que la grande majorité des applications créées au cours des 10 dernières années s’exécute sur Windows 10, et les compléments COM et les macros VBA utilisés par votre organisation sur les versions d’Office remontant jusqu’à Office 2010 continueront de fonctionner avec les dernières versions d’Office, sans modification.

Cela étant dit, selon la taille et l’âge de votre organisation, vérifier la compatibilité du matériel et des applications est probablement toujours une étape essentielle initiale de notre processus de déploiement de 8 étapes recommandé.

Dans cet article, nous vous présentons cette première phase (disponibilité des applications et des périphériques) utilisant le nouvel outil de préparation de mise à niveau Windows Analytics, une solution informatique intelligente livrée avec votre licence Windows.

Si Windows Analytics n’est actuellement pas configuré pour votre environnement ou si vous souhaitez télécharger une version d’évaluation, accédez à la [page Windows Analytics](http://www.aka.ms/windowsanalytics) et lancez-vous.

## <a name="recommended-tool-windows-analytics-upgrade-readiness"></a>Outil recommandé : préparation de mise à niveau Windows Analytics

L’outil de préparation de mise à niveau Windows Analytics offre de nombreux avantages par rapport aux systèmes de gestion d’ordinateurs de bureau classiques. C’est l’outil que nous recommandons. Il est sans agent ; il vous guide à travers les actions à exécuter ; et il utilise les informations de compatibilité du pilote et des applications recueillies via la mise à niveau de centaines de millions de PC grand public, afin de vous offrir une évaluation détaillée, identifiant les problèmes de compatibilité qui peuvent empêcher la mise à niveau avec des liens vers les correctifs suggérés et connus par Microsoft.

Pour configurer l’outil de préparation de mise à niveau Windows Analytics, vous devez tout d’abord configurer un abonnement Azure et y inclure un espace de travail Azure Log Analytics. Une fois que le service de préparation de mise à niveau Windows Analytics est en cours d’exécution, vous pouvez inscrire n’importe quel périphérique connecté à Internet et exécutant Windows 7 SP1 ou une version plus récente via les paramètres de stratégie de groupe. C’est aussi simple que cela. Il n’y a aucun agent à déployer et le flux de travail visuel de l’outil de préparation de mise à niveau Windows Analytics vous guide du pilote au déploiement en production. Si vous le souhaitez, vous pouvez exporter des données de l’outil de préparation de mise à niveau Windows Analytics vers des outils de déploiement de logiciels tels que System Center Configuration Manager, directement vers des PC cibles et créer des collections de sites dès que celles-ci sont prêtes pour le déploiement.

## <a name="device-and-app-readiness-process"></a>Processus de disponibilité des applications et des périphériques

La disponibilité des applications et des périphériques comprend quatre étapes : 1. Inventaire, 2. Hiérarchisation, 3. Test et 4. Mesures correctives. Examinons chacune d’entre elles.

### <a name="1-inventory"></a>1\. Inventaire

Le service de préparation de mise à niveau Windows Analytics utilise un processus sans agent pour faire l’inventaire des ordinateurs, des applications et des compléments Office au sein de votre parc d’ordinateurs de bureau.

![](media/step-1-device-and-app-readiness-media/step-1-device-and-app-readiness-media-3.png)

Il fournit également des rapports sur les applications et les sites Internet très régulièrement consultés, et les emplacements intranet pour vous aider avec les tests de compatibilité ultérieurement.

![](media/step-1-device-and-app-readiness-media/step-1-device-and-app-readiness-media-4.png)

### <a name="2-prioritize"></a>2\. Hiérarchisation

Avec l’inventaire, l’outil de préparation de mise à niveau Windows Analytics vous aide à identifier et à hiérarchiser les applications et le matériel les plus fréquemment utilisés dans votre organisation et les tâches à prioriser pour débloquer autant de PC que possible pour le déploiement,

![](media/step-1-device-and-app-readiness-media/step-1-device-and-app-readiness-media-5.png)

en fournissant également des conseils pour vous aider à évaluer les mises à jour nécessaires pour résoudre les problèmes lors de l’étape suivante : test.

### <a name="3-testing"></a>3\. Test

Vous constaterez que la plupart des applications, des pilotes et des compléments répertoriés fonctionnent tel quel. Pour les éléments pour lesquels l’outil de préparation de mise à niveau Windows Analytics a identifié des problèmes, cet outil vous fournit des informations connues, notamment où trouver des mises à jour de version pour résoudre les problèmes de compatibilité. Au lieu de consacrer du temps et des ressources à tenter de résoudre des problèmes complexes sur des applications non essentielles, des applications faiblement déployées et des périphériques plus anciens, invitez les utilisateurs à retirer et à remplacer ces éléments.

Vous pouvez aussi utiliser l’outil de préparation de mise à niveau Windows Analytics pour évaluer les problèmes de compatibilité sur navigateur, identifier les applications et sites web consultés par les utilisateurs utilisant encore les contrôles ActiveX, Browser Helper Objects, VBScript ou d’autres technologies héritées non prises en charge par le navigateur Microsoft Edge. Les utilisateurs devront quand même utiliser Internet Explorer 11 pour ces sites et vous pouvez les ajouter à la [liste de sites du mode Entreprise](https://docs.microsoft.com/fr-FR/microsoft-edge/deploy/emie-to-improve-compatibility) à l’aide du gestionnaire de listes de sites du mode Entreprise.

En outre, pour vous aider dans votre migration vers Office 365 ProPlus, vous pouvez utiliser le [Kit de ressources de préparation pour Office](https://docs.microsoft.com/fr-FR/deployoffice/use-the-readiness-toolkit-to-assess-application-compatibility-for-office-365-pro) pour tester la compatibilité de vos compléments et des macros Microsoft Visual Basic pour Applications (VBA).

![](media/step-1-device-and-app-readiness-media/step-1-device-and-app-readiness-media-6.png)

### <a name="4-remediation"></a>4\. Mesures correctives

La phase finale de la disponibilité des applications et des périphériques consiste à « corriger ». Ici, vous allez collecter les packages de pilotes et de logiciels requis et vous allez les utiliser pour remplacer ou mettre à jour les versions antérieures dans le cadre du processus de déploiement.

![](media/step-1-device-and-app-readiness-media/step-1-device-and-app-readiness-media-7.png)

À mesure que vous avancez dans la liste et que vous corrigez les problèmes, vous observez que de plus en plus de PC deviennent « Prêt pour le déploiement ». Cela signifie que les pilotes et les applications sur les PC sont indiqués comme étant compatibles avec la version de Windows 10 que vous ciblez pour le déploiement.

## <a name="continued-use-of-telemetry-tools"></a>Utilisation en continu des outils de télémétrie

L’outil de préparation de mise à niveau Windows Analytics n’est pas simplement un outil pour migrer vers Windows 10 et Office 365 ProPlus. Une fois que vos ordinateurs de bureau exécutent Windows 10 et Office 365, vous pouvez l’utiliser pour vous aider à maintenir votre déploiement et à gérer les mises à jour de fonctionnalités semi-annuelles afin de rester à jour.

## <a name="next-step"></a>Étape suivante 

## <a name="step-2-directory-and-network-readinesshttpsakamsmdd2"></a>[Étape 2 : disponibilité des répertoires et des réseaux](https://aka.ms/mdd2)