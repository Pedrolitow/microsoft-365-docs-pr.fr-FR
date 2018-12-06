---
title: 'Étape 2 : préparation des répertoires et du réseau'
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
description: Découvrez comment évaluer l’état de préparation des répertoires et du réseau dans votre environnement.
ms.openlocfilehash: e690e99110e647ffc06c9ff7d40b789d8670e571
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866858"
---
# <a name="step-2-directory-and-network-readiness"></a>Étape 2 : préparation des répertoires et du réseau

Vérifiez que votre répertoire et le réseau sont configurés et prêts pour la migration vers Windows 10 et Office 365 ProPlus. Les services Azure Active Directory devront être mis à disposition des utilisateurs et votre réseau doit être capable de gérer ses trafics réguliers et le déplacement éventuel d’importants volumes de données pendant la mise à niveau des PC et de la restauration des fichiers, des paramètres et des applications des utilisateurs.

![](media/step-2-directory-and-network-readiness-media/step-2-directory-and-network-readiness-media-1.png)

<table>
<thead>
<td><img src="media/desktop-deployment-center-home-media/desktop-deployment-center-home-media-5.png" alt="Step 2" height="144" width="144" /></td>
<td><p><strong>Étape 2 : préparation des répertoires et du réseau</strong></p>
<p>Les services connectés au cloud dans Office 365 ProPlus et les nouvelles options de déploiement, telles que Windows Autopilot, nécessitent Azure Active Directory. Votre réseau et votre connectivité sont également des aspects importants pour planifier le déplacement des images, des applications, des pilotes Windows et des fichiers connexes sur votre PC. Découvrez comment les nouveaux outils et les nouvelles options de déploiement réduisent et rationalisent le trafic réseau.</p></td>
<td><a href="https://aka.ms/ddev2" target="_blank"><img src="media/desktop-deployment-center-home-media/desktop-deployment-center-home-media-15.png" alt="Step 2" height="130" width="231" /></a></td>
</thead>
</table>

>[!NOTE]
>La préparation des répertoires et du réseau est la deuxième étape de notre processus de déploiement recommandé. Elle s’articule autour d’Azure Active Directory et l’optimisation du réseau. Pour connaître l’ensemble du processus de déploiement de bureau, accédez au [centre de déploiement de bureau moderne](https://aka.ms/HowToShift).
>

La préparation des répertoires et du réseau est fondamentale pour garantir un déploiement fluide du système d’exploitation et du bureau. Comme dans tout déploiement automatisé, il est important de vérifier que vos partages de fichiers sont accessibles et que votre réseau pourra supporter le transfert de fichiers très volumineux vers des centaines voire des milliers de PC en même temps.

Après la migration vers Windows 10 et Office 365 ProPlus, assurez-vous également que l’identité basée sur le cloud est configurée avec Azure Active Directory. En plus d’activer Office 365 ProPlus, il vous permet de tirer parti des solutions de mise en service modernes, telles que Windows Autopilot.

Dans cet article, nous allons explorer les outils et les options pour préparer vos services d’annuaire, et les autorisations des appareils et des utilisateurs nécessaires pour déployer Windows 10 et Office 365 ProPlus.

## <a name="adding-azure-active-directory"></a>Ajout d’Azure Active Directory

Si votre organisation utilise Office 365, Exchange Online, Microsoft Intune ou d’autres services Microsoft Online, vous utilisez probablement déjà Azure Active Directory. Dans ce cas, vérifiez que les utilisateurs ciblés pour le déploiement du bureau figurent dans votre répertoire Azure Active Directory et que les licences ont été affectées.

Si vous n’utilisez pas Azure Active Directory, il existe [un grand nombre de ressources](https://docs.microsoft.com/fr-FR/azure/active-directory/) pour vous aider à le configurer. Vous pouvez également bénéficier d’une aide personnalisée via Microsoft FastTrack, comprise dans votre licence Office 365. Pour en savoir plus sur Microsoft Fastrack, cliquez [ici](https://fasttrack.microsoft.com).

Une fois Azure Active Directory configuré, vos utilisateurs peuvent se connecter aux applications Office 365 ProPlus et les activer. Vous pouvez aussi utiliser le déploiement Microsoft Intune ou Windows Autopilot pour déployer automatiquement des applications et des stratégies.

## <a name="network-readiness"></a>Préparation du réseau

Il est crucial d’évaluer les besoins en bande passante quand vous planifiez vos déploiements. Lors d’un déploiement, vous devez prendre en comptre trois composants clés qui influeront sur votre réseau : l’imagerie PC, les mises à jour logicielles et la personnalisation utilisateur. Au total, ces trois composants peuvent représenter plus de 20 Go par PC pour la migration initiale, et 1 Go ou plus par mois par PC pour les mises à jour.

Penchons-nous quelques instants sur la configuration requise pour chacun de ces trois composants :

### <a name="pc-imaging"></a>Imagerie PC

Le graphique ci-dessous vous permet de définir votre planification en fonction de la taille de l’image. Pour les images Windows sans personnalisation, prévoyez 3 Go par PC, tandis que pour les images personnalisées avec des applications, envisagez 6 Go voire plus. Prenez également en compte les packages de pilotes ; ils peuvent représenter quelques centaines de mégaoctets par PC, parfois jusqu’à 1 Go.

### <a name="software-updates"></a>Mises à jour logicielles

Il est important de planifier la bande passante réseau requise pour les mises à jour logicielles. Windows 10 et Office 365 ProPlus utilisent un nouveau modèle de service qui fournit des mises à jour mensuelles et semestrielles. Si vous ne connaissez pas ce modèle, vous pouvez en apprendre davantage sur son fonctionnement [ici](https://docs.microsoft.com/fr-FR/windows/deployment/update/waas-overview).

Le nouveau modèle de service propose des mises à jour de fonctionnalité semestrielles pour Windows, des mises à jour de canal semestrielles et des mises à jour de qualité mensuelles. Les mises à jour de fonctionnalité représentent généralement 2-4 Go et les mises à jour de canal Office semestrielles correspondent à 300-400 Mo par mise à jour. Quant aux mises à jour de qualité mensuelles, elles peuvent représenter entre quelques centaines de mégaoctets et un gigaoctet ou plus. Comme ces mises à jour mensuelles sont cumulatives, leur taille augmente pendant toute la durée de service de chaque version de Windows 10. Des outils peuvent vous aider à réduire le volume de données qui transitent sur le réseau pour implémenter les mises à jour. Nous aborderons ce sujet plus en détail plus loin dans cet article.

### <a name="user-personalization"></a>Personnalisation utilisateur

Le troisième composant à prendre en compte est la personnalisation utilisateur. La bande passante réseau doit pouvoir supporter la restauration des fichiers utilisateur, de leurs paramètres et de leurs applications dans le cadre du processus d’actualisation ou de remplacement des PC. Au total, ces éléments représentent souvent plus de 20 Go par PC. Pour certains utilisateurs, ils peuvent correspondre à plus de 100 Go.

## <a name="limiting-bandwidth"></a>**Limitation de la bande passante**

Pour limiter l’impact du trafic lié au déploiement sur le réseau, vous pouvez limiter la bande passante réseau à l’aide du paramètre BITS (Background Intelligent Transfer Service) disponible sur les clients. BITS utilise un débit binaire adaptatif (Adaptive Bit Rate, ABR) pour ajuster la bande passante nécessaire au déploiement. Il peut être configuré sur les clients à l’aide d’une stratégie de groupe.

[À propos de BITS](https://docs.microsoft.com/fr-FR/windows/desktop/bits/about-bits)

Si vous utilisez le System Center Configuration Manager, vous pouvez également configurer les Points de distribution BITS ou activer la multidiffusion avec WDS.

En limitant un trafic spécifique, vous pouvez réduire l’impact du téléchargement des mises à jour et des applications des PC sur le trafic réseau normal. Le fait de dissocier un certain pourcentage de bande passante pour ces tâches vous permet d’éviter que le déploiement de Windows ou d’Office affecte la productivité et de veiller à ce que les processus continuent d’être exécutés au besoin. Le temps d’arrêt lié au déploiement peut être plus long et les utilisateurs ne peuvent pas accéder à leur ordinateur pendant l’exécution d’un déploiement.

Heureusement, il existe de nouveaux outils pour vous aider à gérer facilement l’impact d’un déploiement de bureau de grande échelle sur le réseau, tels que LEDBAT pour optimiser l’utilisation de la bande passante disponible, et les options pair à pair pour déplacer le trafic de déploiement du centre du réseau vers le réseau de périmètre.

![](media/step-2-directory-and-network-readiness-media/step-2-directory-and-network-readiness-media-3.png)

## <a name="scavenging-bandwidth"></a>**Nettoyage de la bande passante**

L’option LEDBAT (Low Extra Delay Background Transport), pris en charge dans Windows Server 2019 et la version 1806 du System Center Configuration Manager, est conçue pour optimiser le trafic réseau des clients Windows.

[10 fonctionnalités de mise en réseau dans Windows Server 2019 : \#9 LEDBAT](https://blogs.technet.microsoft.com/networking/2018/07/25/ledbat/)

Contrairement aux options de limitation traditionnelles, LEDBAT peut utiliser toute la bande passante réseau disponible comme tâche en arrière-plan, produisant instantanément de la bande passante quand un autre trafic en demande. Contrairement à BITS, LEDBAT agit sans délai. Tout est automatisé (pas de planification ou de réglage manuel) et tout est configuré côté serveur. Cela peut générer des gains de performances considérables.

![](media/step-2-directory-and-network-readiness-media/step-2-directory-and-network-readiness-media-4.png)

## <a name="peer-to-peer-options"></a>**Options pair à pair**

Les options pair à pair sont progressivement utilisées dans les migrations de Windows 10 (imagerie PC, mises à jour logicielles et personnalisation utilisateur). Elles sont également utiles pour faciliter les mises à niveau build à build après le déploiement initial de Windows 10. Ici, nous allons vous présenter plusieurs exemples pour vous aider à éloigner le trafic lié à Windows 10 et Office du centre de réseau, en évitant de limiter la bande passante tout en aidant les PC à trouver les fichiers de mise à jour nécessaires sur des PC homologues de leur réseau local, au lieu de les télécharger à partir d’un point de distribution ou d’Internet.

**BranchCache** peut vous aider à télécharger du contenu dans des environnements distribués sans saturer le réseau. Il propose deux options : le mode Cache hébergé, qui vous permet d’utiliser des serveurs locaux pour mettre en cache du contenu, et le mode Cache distribué (mode pris en charge dans le System Center Configuration Manager), qui permet aux clients de partager du contenu déjà téléchargé entre eux.

**Cache d’homologue** Les clients pris en charge par le System Center Configuration Manager peuvent également utiliser le Cache d’homologue. Ainsi, les PC fiables disponibles sur le réseau peuvent héberger la source du contenu pour la distribuer. Nous vous conseillons de ne pas activer cette option sur tous vos PC. (Ciblez uniquement les PC avec des connexions réseau fiables, tels que des ordinateurs de bureau, des tours ou des minitours). Le Cache d’homologue peut même travailler sur les tâches de déploiement exécutées dans les phases de l’environnement de préinstallation Windows (WinPE) pendant la configuration.

Remarque : BranchCache et le cache d’homologue sont complémentaires et peuvent travailler ensemble dans le même environnement.

[BranchCache et cache d’homologue](https://blogs.technet.microsoft.com/swisspfe/2018/01/25/branch-cache-vs-peer-cache/)

**Optimisation de la distribution** L’Optimisation de la distribution est une autre technologie de mise en cache pair à pair, qui fournit des contrôles réseau pour les déploiements de Windows. L’Optimisation de distribution Windows 10 vous permet de mettre à jour les applications UWP intégrées et d’installer les applications provenant de la Boutique Microsoft et les mises à jour logicielles à l’aide des mises à jour expresses. Cette technologie est disponible depuis les versions antérieures de Windows 10, même si elle a récemment été intégrée avec le System Center Configuration Manager. Depuis la publication des nouvelles options de configuration de la version 1803 de Windows 10, vous pouvez définir séparément des limites de bande passante pour les mises à jour en arrière-plan et les tâches de premier plan, telles que l’installation d’une application à partir de la Boutique.

![](media/step-2-directory-and-network-readiness-media/step-2-directory-and-network-readiness-media-5.png)

**Autres considérations liées à Office 365 ProPlus**

Voici trois éléments qui réduiront votre charge réseau pendant les déploiements d’Office 365 ProPlus.

**Compression Delta binaire** Office 365 ProPlus utilise la Compression Delta binaire pour réduire la bande passante consommée par les mises à jour logicielles de la version la plus récente d’Office 365 ProPlus vers la version suivante. En chargeant uniquement les modifications au niveau binaire à partir de la version précédente, vous réduisez l’impact des mises à jour cumulatives qui s’enrichissent de mois en mois. Ainsi, vous économisez plusieurs centaines de mégaoctets de données par PC tous les mois. Cependant, pour utiliser cette fonctionnalité, vous ne pouvez pas sauter une version sinon la mise à jour cumulative complète doit être téléchargée.

[Téléchargement des mises à jour pour Office 365](https://docs.microsoft.com/fr-FR/deployoffice/overview-of-the-update-process-for-office-365-proplus#download-the-updates-for-office-365-proplus)

**Fichiers de données Outlook** Outlook est souvent configuré pour mettre en cache toute la boîte aux lettres des utilisateurs en local, pour pouvoir l’utiliser en mode hors connexion. Dans tout déploiement Windows, à l’exception d’une mise à niveau sur place, les fichiers de données Outlook des utilisateurs doivent se reconstruire après la mise à niveau. Ce processus est automatisé, mais les boîtes aux lettres Outlook ne peuvent généralement pas contenir plus de 100 Go de données, et la remise en cache de la boîte aux lettres entière, en local, pour tous les utilisateurs, représente un transfert volumineux de données. Pour réduire la charge réseau, nous vous recommandons d’utiliser une stratégie de groupe pour réduire le paramètre « Courrier à conserver hors connexion ». Dans Outlook d’Office 365 ProPlus ou Outlook 2016, la valeur par défaut est définie sur 12 mois. Nous vous conseillons de définir la durée du cache en mode hors connexion entre 1 à 6 mois. Le fait de modifier ce paramètre n’affecte pas la taille de la boîte aux lettres en ligne, et vous pouvez toujours faire des recherches dans la boîte aux lettres entière via Outlook quand vous êtes connecté.

![](media/step-2-directory-and-network-readiness-media/step-2-directory-and-network-readiness-media-6.png)

**Fichiers à la demande et fonctionnalité « Known Folder Move » de OneDrive** OneDrive vous permet de synchroniser et de protéger les fichiers utilisateur de différents PC et appareils dans le cloud. Avec la fonctionnalité « Known Folder Move », vous pouvez également synchroniser des fichiers à partir des dossiers Bureau, Documents et Images d’un utilisateur avec OneDrive, pour faciliter l’accès de ces fichiers quand vous vous connectez à un nouvel appareil ou à un PC remis en image. Cependant, en raison de la taille et du nombre de fichiers conservés dans les dossiers Bureau, Documents et Images, nous vous conseillons de planifier le déploiement des stratégies d’activation et d’application de OneDrive sur vos PC. Pour cela, vous pouvez utiliser les contrôles réseau de la stratégie de groupe pour limiter la bande passante utilisée par le service de synchronisation OneDrive.

![](media/step-2-directory-and-network-readiness-media/step-2-directory-and-network-readiness-media-7.png)

[Configuration de la fonctionnalité « Known Folder Move »](https://techcommunity.microsoft.com/t5/Microsoft-OneDrive-Blog/Migrate-Your-Files-to-OneDrive-Easily-with-Known-Folder-Move/ba-p/207076)

[Fichiers à la demande OneDrive](https://www.microsoft.com/fr-FR/microsoft-365/blog/2017/05/11/introducing-onedrive-files-on-demand-and-additional-features-making-it-easier-to-access-and-share-files/)

Si vous n’avez pas encore déployé OneDrive, la migration de Windows 7 vers Windows 10 est l’occasion idéale pour activer OneDrive qui s’intègre parfaitement avec Office 365 ProPlus. Nous vous conseillons de commencer ce déploiement au moment de la préparation de vos applications et de vos appareils. Ainsi, la synchronisation des fichiers pourra démarrer avant que vous ne déplaciez les images de Windows et ne déployiez des applications sur votre réseau.

## <a name="next-step"></a>Étape suivante 

## <a name="step-3-office-and-lob-app-deliveryhttpsakamsmdd3"></a>[Étape 3 : livraison d’Office et d’applications métier](https://aka.ms/mdd3)

## <a name="previous-step"></a>Étape précédente :

## <a name="step-1-device-and-app-readinesshttpsakamsmdd1"></a>[Étape 1 : préparation des applications et des appareils](https://aka.ms/mdd1)

## <a name="feedback"></a>Commentaires

Votre avis nous intéresse. Choisissez le type de commentaire dont vous aimeriez nous faire part :

Commentaire sur un produit Se connecter pour envoyer un commentaire sur la documentation

Notre nouveau système de commentaires repose sur les Problèmes GitHub. Lisez notre billet de blog pour en savoir plus sur cette nouveauté.
