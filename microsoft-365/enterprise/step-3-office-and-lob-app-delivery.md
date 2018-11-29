---
title: 'Étape 3 : livraison d’Office et d’applications métier'
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
description: Découvrez comment livrer Office et des applications métier.
ms.openlocfilehash: 2bae1f159f7c8ae947d4afddfe1e608cdd8bc85b
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867493"
---
# <a name="step-3-office-and-lob-app-delivery"></a>Étape 3 : livraison d’Office et d’applications métier

Vous êtes désormais prêt à livrer Office et votre ligne d’applications métier. Pour ce faire, il existe plusieurs méthodes, y compris de nouvelles options intéressantes. Prenez le temps d’examiner et de choisir les meilleures méthodes pour vos besoins actuels.

![](media/step-3-office-and-lob-app-delivery-media/step-3-office-and-lob-app-delivery-media-1.png)

<table>
<thead>
<td><img src="media/desktop-deployment-center-home-media/desktop-deployment-center-home-media-6.png" alt="Step 3" height="130" width="130" /></td>
<td><p><strong>Étape 3 : livraison d’Office et d’applications métier</strong></p>
<p>Vérifiez que vos applications sont empaquetées et prêtes pour l’installation automatisée. Découvrez comment l’empaquetage Démarrer en un clic avec Office 365 ProPlus vous offre de nouvelles options pour configurer, livrer et actualiser vos applications Office.</p></td>
<td><a href="https://aka.ms/ddev3" target="_blank"><img src="media/desktop-deployment-center-home-media/desktop-deployment-center-home-media-16.png" alt="Step 3" height="120" width="213" /></a></td>
</thead>
</table>

>[!NOTE]
>La livraison d’Office et d’applications métier est la troisième étape de notre processus de déploiement recommandé couvrant les options d’installation et de gestion d’Office et métiers. Pour un déploiement réussi, ne sautez pas les deux premières étapes. Pour afficher l’ensemble du processus de déploiement de bureaux, visitez le [centre de déploiement de bureaux moderne](https://aka.ms/HowToShift).
>

Tandis que certaines applications ne soient disponibles qu’en version compilée 32 bits ou 64 bits, d’autres applications, notamment Office 365 ProPlus, le sont en tant que code natif compilé à la fois 32 bits et 64 bits ; l’une des principales décisions que vous devez prendre sera de choisir la version à déployer. Pour profiter de la meilleure puissance de calcul et de la RAM supplémentaire sur les nouveaux périphériques, vous pouvez utiliser la version 64 bits, mais, avant de procéder, vous devez résoudre tous les problèmes de compatibilité liés aux fichiers ou aux compléments que vous rencontrez. Vous devrez peut-être revoir l’étape 1 (disponibilité des applications et des périphériques) avant de poursuivre.

Si rien ne vous en empêche, nous vous recommandons de déployer les versions 64 bits de toutes les applications, y compris Microsoft Office. Les applications natives compilées 64 bits offrent les meilleures performances et constituent le choix le plus fiable.

Il existe beaucoup de méthodes et de modèles permettant l’installation d’applications sur Windows. Examinons vos options de livraison.

[Gestion des applications Windows 10](https://docs.microsoft.com/fr-FR/windows/application-management/)

## <a name="msi-based-deployments"></a>Déploiements basés sur MSI

Pour votre ligne d’applications métier, vous allez probablement utiliser des packages basés sur MSI ou des fichiers exécutables et installer des applications dans le cadre d’une séquence de tâches de déploiement de systèmes d’exploitation. Windows 10 continue de fonctionner avec ces packages

Les outils de déploiement de logiciels tels que System Center Configuration Manager et Microsoft Intune sont également optimisés pour livrer des applications empaquetées par MSI. Une fois que vous avez validé vos applications sur Windows 10, vous pouvez utiliser System Center Configuration Manager (branche actuelle) pour la livraison des applications. Si vous utilisez le portail d’entreprise dans Microsoft Intune, vous pouvez étendre le choix des applications informatiques sanctionnées disponibles à votre organisation pour inclure les applications les plus récentes et permettre aux utilisateurs de sélectionner eux-mêmes ce dont ils ont besoin.

![](media/step-3-office-and-lob-app-delivery-media/step-3-office-and-lob-app-delivery-media-3.png)

## <a name="pc-imaging"></a>Imagerie PC

Une autre méthode populaire de livraison d’applications est l’imagerie PC. Dans ce cas, les applications sont installées soit via une séquence de tâches soit manuellement sur un exemple de PC, puis une image système est capturée avec les applications requises déjà installées. L’approche d’imagerie permettant de concevoir et d’effectuer des captures peut vous faire gagner du temps lors de la mise en service de nouveaux PC, mais n’oubliez pas que les systèmes d’exploitation et les applications au sein de l’image peuvent rapidement devenir obsolètes. Le modèle de mise à jour cumulative dans Windows 10 et Office 365 ProPlus vous aide à pallier ce problème, mais ne l’élimine pas complètement. Par conséquent, nous vous recommandons d’utiliser une approche d’imagerie fine, où vos applications sont installées en dehors de l’image lors du déploiement.

![](media/step-3-office-and-lob-app-delivery-media/step-3-office-and-lob-app-delivery-media-4.png)

Si vous ne voulez pas inclure Office 365 ProPlus dans votre image, n’oubliez pas que cette approche utilise une activation utilisateur ; elle ne peut pas être activée au préalable par l’administrateur système. Utilisez l’outil Déploiement d’Office pour installer préalablement Office sur le périphérique dont vous présentez l’imagerie et ignorer la connexion utilisateur. Les utilisateurs peuvent se connecter, recevoir l’activation et profiter des autres fonctionnalités qui exploitent la connexion lors de la première utilisation.

[Créer une séquence de tâches pour installer un système d’exploitation](https://docs.microsoft.com/fr-FR/sccm/osd/deploy-use/create-a-task-sequence-to-install-an-operating-system)

## <a name="click-to-run"></a>Démarrer en un clic 

Office 365 ProPlus s’installe à l’aide de la fonction Démarrer en un clic qui remplace l’empaquetage basé sur MSI pour toutes les versions de la prochaine version Office 2019 de Windows. Elle comporte de nombreux avantages, y compris des installations plus rapides, une mise à jour plus rapide et plus efficace et une désinstallation plus claire.

Les programmes livrés via Démarrer en un clic s’exécutent dans un environnement virtuel d’applications sur votre ordinateur et coexistent donc avec d’autres applications sans conflit ; ils prennent également environ la moitié de l’espace disque comme le ferait tout package MSI. Étant donné que Démarrer en un clic prend en charge la diffusion en continu des programmes, en diffusant tout d’abord les fonctionnalités les plus fréquemment utilisées, les utilisateurs peuvent commencer à utiliser les applications Office en seulement quelques minutes, plutôt que d’attendre la fin de l’installation d’Office. Ceci est important pour le déploiement initial, mais cela signifie aussi que les mises à jour peuvent être diffusées en continu en toute transparence en arrière-plan avec un impact minimal sur les utilisateurs.

Si vous utilisez l’outil System Center Configuration Manager, vous pouvez toujours l’utiliser pour le déploiement large d’Office 365 ProPlus. System Center Configuration Manager (branche actuelle) assure la prise en charge native de l’outil de personnalisation Office mis à jour, la personnalisation de package pour Démarrer en un clic au moment de l’installation et la prise en charge native pour la gestion des mises à jour logicielles après l’installation.

[Guide de déploiement pour Office 365 ProPlus](https://docs.microsoft.com/fr-FR/deployoffice/deployment-guide-for-office-365-proplus)

[Suppression des versions MSI existantes d’Office lors de la mise à niveau vers Office 365 ProPlus](https://docs.microsoft.com/fr-FR/deployoffice/upgrade-from-msi-version)

[Gérer Office 365 ProPlus avec le gestionnaire de configuration](https://docs.microsoft.com/fr-FR/sccm/sum/deploy-use/manage-office-365-proplus-updates)

[Affecter des applications Office 365 à des périphériques Windows 10 avec Microsoft Intune](https://docs.microsoft.com/fr-FR/intune/apps-add-office365)

## <a name="browser-based-apps"></a>Applications basées sur navigateur

Voici quelques points à prendre en compte pour vous assurer que vos applications sur navigateur continuent de fonctionner comme prévu. Si vous avez des applications et des sites web spécifiques ayant des problèmes de compatibilité avec Microsoft Edge, vous pouvez utiliser la liste de sites du mode Entreprise afin que les sites web s’ouvrent automatiquement à l’aide d’Internet Explorer 11.

De plus, si vous savez que vos sites intranet ne vont pas fonctionner correctement avec Microsoft Edge, vous pouvez configurer tous les sites intranet de façon à ce qu’ils s’ouvrent automatiquement avec Internet Explorer 11. Ce processus utilise un fichier XML pour déterminer si Internet Explorer 11 est utilisé pour chaque site et une stratégie de groupe pour appliquer les paramètres.

Jusqu’à présent, nous avons abordé les méthodes de déploiement connues. Cependant, il existe deux nouvelles approches permettant de déployer les applications à prendre en considération.

[Présentation du mode Entreprise](https://docs.microsoft.com/fr-FR/internet-explorer/ie11-deploy-guide/what-is-enterprise-mode#what-is-enterprise-mode)

## <a name="microsoft-store-for-business"></a>Microsoft Store pour Entreprises 

Microsoft Store pour Entreprises offre un cadre flexible pour découvrir, acquérir, gérer et distribuer les applications gratuites et payantes pour les périphériques Windows 10 à l’échelle. En tant qu’administrateur informatique, vous pouvez publier des applications sélectionnées du Microsoft Store, ainsi que vos propres applications personnalisées, sur votre magasin privé, et attribuer et réutiliser les licences selon vos besoins. Vos utilisateurs sont dirigés exclusivement vers cette boutique et peuvent uniquement rechercher et installer les applications approuvées.

Les applications Store peuvent être créées de manière native en tant qu’applications UWP ou vous pouvez utiliser le Pont du bureau pour empaqueter à nouveau vos applications existantes pour le Store et ajouter des expériences modernes pour Windows 10. Excepté le code que vous utilisez pour égayer vos expériences Windows 10, votre application reste inchangée et continue de s’exécuter en mode utilisateur de confiance totale.

## <a name="msix-containerization"></a>Mise en conteneur MSIX

MSIX est une nouvelle option d’empaquetage d’applications. MSIX utilise la technologie de mise en conteneur disponible dans Windows, combinant les meilleurs aspects de Démarrer en un clic, UWP et l’empaquetage MSI. Grâce à des outils permettant la migration directe de programmes d’installation existants comme EXE, MSI, APPV et APPX vers MSIX, nous constatons que la mise en conteneur MSIX fournit un chemin d’accès unifié pour les nombreuses technologies d’installation utilisées aujourd’hui. La prise en charge de MSIX est incluse dans les versions actuelles de Windows : tout périphérique exécutant Windows 10 RS5 ou une version ultérieure dispose de tout ce dont vous avez besoin pour installer et exécuter des applications empaquetées dans MSIX. Windows 10 intègre dynamiquement les conteneurs MSIX reçus, tout en conservant les applications à l’écart du système d’exploitation.

La mise en conteneur suppose la désinstallation et la suppression nettes de packages, contrairement à un grand nombre de packages basés sur MSI et EXE pouvant laisser des éléments sur le système. Cela signifie également que seules les informations d’identification d’utilisateur standard sont nécessaires pour installer les applications : vous n’avez pas besoin d’avoir des informations d’identification d’administrateur pour installer les conteneurs MSIX. Les conteneurs MSIX sont aussi plus efficaces à mettre à jour. Lorsqu’une mise à jour est publiée, l’utilisation des écarts de niveau de bloc signifie que seuls de nouveaux fichiers binaires sont appliqués, réduisant ainsi la charge de mise à jour pour assurer des déploiements plus rapides et la réduction de la consommation de la bande passante du réseau.

Vous trouverez plus d’informations sur MSIX via le [site MSIX Tech Community](https://techcommunity.microsoft.com/t5/MSIX/ct-p/MSIX)

## <a name="next-step"></a>Étape suivante

## <a name="step-4-user-files-and-settingshttpsakamsmdd4"></a>[Étape 4 : fichiers et paramètres utilisateur](https://aka.ms/mdd4)

## <a name="previous-step"></a>Étape précédente

## <a name="step-2-directory-and-network-readinesshttpsakamsmdd2"></a>[Étape 2 : disponibilité des répertoires et des réseaux](https://aka.ms/mdd2) 