---
title: Test Base FAQ
description: Passer en revue les questions fréquemment posées
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
localization_priority: Normal
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 2d8e0a8cea68e969df5939691b517ee71e78472d
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53544456"
---
# <a name="test-base-faq"></a>Test Base FAQ

**Q : Comment envoyer nos packages à l’équipe de base de test ?**

**R :** Envoyez vos packages directement à l’environnement de base de test à l’aide de notre portail libre-service.

Pour soumettre votre package d’application, accédez au portail [Azure](https://www.aka.ms/testbaseportal "Page d’accueil de base de test") et téléchargez un dossier compressé contenant les fichiers binaires, les dépendances et les scripts de test de votre application via le tableau de bord du portail de base de test libre-service. 

Consultez le guide de l’utilisateur d’intégration pour plus d’informations ou contactez notre équipe pour obtenir de <testbasepreview@microsoft.com> l’aide et plus d’informations.

**Q : Que sont les tests OOB ( Out-of-Box) ?**

**R :** Les tests OOB (Out-of-Box) sont standardisés, les tests par défaut s’exécutent là où les packages d’application sont installés, lancés et fermés trente (30) fois, puis désinstallés. 

Les packages créés pour la base de test auront les scripts de test suivants : installer, lancer, fermer et éventuellement le script de désinstallation. 

Les tests OOB (Out-of-Box) vous fournissent une télémétrie normalisée sur votre application à comparer entre Windows builds.

**Q : Pouvons-nous soumettre des tests en dehors des tests pré-box (installer, lancer, fermer, désinstaller des scripts de test) ?**

**R :** Oui, les clients peuvent également télécharger des packages d’application pour les **tests fonctionnels** via le tableau de bord du portail libre-service.
**Les tests fonctionnels** sont des tests qui permettent aux clients d’exécuter leurs scripts pour exécuter des fonctionnalités personnalisées sur leur application.


## <a name="testing"></a>Tests

**Q : Prise en charge des tests fonctionnels ?**

**R :** Oui, la base de test prend en charge les tests fonctionnels. Les tests fonctionnels sont des tests qui permettent à nos clients d’exécuter leurs scripts pour exécuter des fonctionnalités personnalisées sur leur application. 

Pour soumettre votre package d’application à des tests fonctionnels, téléchargez simplement le dossier compressé contenant les fichiers binaires, les dépendances et les scripts de test de votre application via notre tableau de bord de portail libre-service. 

Consultez le guide de l’utilisateur d’intégration pour plus d’informations ou contactez notre équipe pour obtenir de <testbasepreview@microsoft.com> l’aide et plus d’informations.

**Q : Comment la base de test gère-t-elle nos données de test ?**

**R :** Test Base collecte et gère en toute sécurité vos données de test dans l’environnement Azure. 

**Q : La base de test peut-elle prendre en charge nos tests automatisés ?**

**R :** Oui, la base de test prend en charge les tests automatisés, mais nous ne prend pas en charge les tests manuels pour le moment en raison des fonctionnalités de service.

**Q : Quelles sont les langues et les frameworks des tests automatisés que vous prisez en charge ?**

**R :** Nous supportons toutes les langues et toutes les infrastructure. Nous appelons tous les scripts via PowerShell. 

Vous devez également fournir (télécharger) les fichiers binaires dépendants de l’infrastructure requise.

**Q : À combien de temps la Base de test fournit-elle les résultats des tests ?**

**R :** Pour chaque test que nous exécuterons sur les builds pré-publiées, nous fournirons des résultats dans les 48 heures sur votre tableau de bord [du portail Azure.](https://www.aka.ms/testbaseportal "Page d’accueil de base de test")

**Q : Pouvez-vous redémarrer après l’installation ?**

**R :** Oui, notre processus prend en charge le redémarrage après l’installation. N’oubliez pas de sélectionner cette option dans la liste d’attente « Paramètres facultatifs » lors de la définition de vos tâches **sur** le portail d’intégration.

Pour les tests OOB (Out-of-Box), vous pouvez spécifier si un redémarrage est nécessaire pour le _script d’installation._

![Image de redémarrage](Media/reboot.png)

Pour les tests fonctionnels, vous pouvez spécifier si un redémarrage est requis pour chaque script ajouté.

![Comment sélectionner des tests fonctionnels](Media/functionalreboot.png)

**Q : Quelles versions Windows-vous prise en charge ?**

**R :** Nous prise en charge actuellement Windows 10 clients, Windows Server 2016, Windows Server 2016 Version principale, Windows Server 2019 et Windows Server 2019 Core.

**Q : Quelle est la différence entre les tests de mise à jour de sécurité et les tests de mise à jour des fonctionnalités ?**

**R :** Pour les tests de mise à jour de sécurité, nous testons les mises à jour de sécurité mensuelles pré-publiées sur Windows qui sont **<ins>axées</ins>** sur le maintien de la sécurité et de la protection de nos utilisateurs. Pour les tests de mise à jour des fonctionnalités, nous testons les mises à jour de fonctionnalités de **<ins>pré-publication bi-annuelles</ins>** qui introduisent de nouvelles fonctionnalités et fonctionnalités sur Windows.

## <a name="debugging-options"></a>Options de débogage

**Q : Avons-nous accès aux machines virtuelles (VM) en cas de défaillance ? Qu’est-ce que le partage de base de test ?**

**R :** Pour que le service soit conforme et que les mises à jour pré-publiées soient sécurisées, seule Microsoft a accès aux VM. Toutefois, les clients peuvent afficher les résultats des tests et d’autres mesures de test sur leur tableau de bord du portail, notamment les signaux d’incident et de panne, les mesures de fiabilité, l’utilisation de la mémoire et du processeur, etc. Nous générons et fournissons également des journaux des séries de tests sur le tableau de bord pour le téléchargement et une analyse plus approfondie. 

Nous pouvons également fournir des vidages mémoire pour le débogage sur incident si nécessaire.

**Q : Si des problèmes se sont produits pendant le test, quelles sont les étapes suivantes pour résoudre ces problèmes ?**

**R :** L’équipe de base de test effectuera un processus de tri initial pour déterminer la cause première de l’erreur, puis en fonction de nos résultats, nous effectuerons un itinéraire vers le client ou les équipes internes au sein de Microsoft pour le débogage. 

Nous travaillons toujours en étroite collaboration avec nos clients pour résoudre les problèmes. 

**Q : Microsoft tient-il la publication du correctif de sécurité jusqu’à ce que le problème soit résolu ? Quelles résolutions alternatives sont disponibles ?**

**R :** L’objectif de la base de test est de s’assurer que nos clients finaux conjoints ne rencontrent aucun problème. Nous travaillerons en dur avec les éditeurs de logiciels pour résoudre les problèmes avant la publication, mais au cas où le correctif ne serait pas réalisable, nous avons d’autres résolutions telles que les shims et les blocs.

## <a name="miscellaneous"></a>Divers

**Q : Comment le service fonctionne-t-il avec un serveur sur place ?**

**R :** Pour l’instant, nous ne donnent pas de prise en charge des serveurs sur site. Toutefois, si le serveur expose le point de terminaison HTTP, nous pouvons nous y connecter via Internet.

**Q : Qui héberger les VM ?**

**R :** Microsoft propose la VM pour ce service, en prenant la charge de cette fonction du client.

**Q : Ce service prend-il en charge les applications web, mobiles ou de bureau ?**

**R :** Pour l’instant, nous nous concentrons sur les applications de bureau, mais nous envisageons d’intégrer des applications web à l’avenir, mais nous ne prisent pas en charge les applications mobiles pour le moment.

**Q : Quelle est la différence entre Base de test et LAPX ?**

**R :** La principale différence entre base de test et LAPSP est que nos partenaires ententent leurs applications dans l’environnement Azure de base de test pour la validation s’exécute sur les mises à jour pré-publiées au lieu d’effectuer les tests eux-mêmes. 

En plus des tests de mises à jour de sécurité pré-publiées, nous prise en charge des tests de mises à jour de fonctionnalités pré-publiées sur notre plateforme. Nous avons de nombreux autres types de mises à jour et de tests de système d’exploitation dans notre feuille de route.

**Q : Existe-t-il un coût associé au service ?**

**R :** Le service de base de test sera gratuit pour les utilisateurs jusqu’à la disponibilité générale. À ce moment-là, nous annoncerons une structure de coûts qui sera en vigueur pour tous les clients. 

**Q : Comment puis-je fournir des commentaires sur la Base de test ?**

**R :** Pour partager vos commentaires sur la base de test, sélectionnez l’icône **Commentaires** en bas à gauche du portail. Incluez une capture d’écran avec votre soumission pour aider Microsoft à mieux comprendre vos commentaires. 

Vous pouvez également soumettre des suggestions de produit et soumettre d’autres idées sur <testbasepreview@microsoft.com> .
