---
title: Test Base FAQ
description: Passer en revue les questions fréquemment posées
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: test-base
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: tinachen
f1.keywords: NOCSH
ms.openlocfilehash: 5d84ea6e803fba5d5f355fecaa4f6ac6776d3f60
ms.sourcegitcommit: eb81b49205cbc66b021326b8e2c00a8336b4a2fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67315457"
---
# <a name="test-base-faq"></a>Test Base FAQ

**Q : Comment soumettre nos packages à l’équipe de base de test ?**

**Un:** Envoyez vos packages directement à l’environnement de base de test à l’aide de notre portail libre-service.

Pour envoyer votre package d’application, accédez au [portail Azure](https://www.aka.ms/testbaseportal "Page d’accueil de base de test") et chargez un dossier compressé contenant les fichiers binaires, les dépendances et les scripts de test de votre application via le tableau de bord du portail de base de test libre-service.

Consultez le guide de l’utilisateur d’intégration pour plus d’informations ou contactez notre équipe <testbasepreview@microsoft.com> pour obtenir de l’aide et plus d’informations.

**Q : Qu’est-ce que les tests OOB (Out-of-box) ?**

**Un:** Les tests OOB (Out-of-Box) sont normalisés, les tests par défaut s’exécutent où les packages d’application sont installés, lancés et fermés trente (30) fois, puis désinstallés.

Les packages créés pour la base de test ont les scripts de test suivants : installer, lancer, fermer et éventuellement le script de désinstallation.

Les tests OOB (Out-of-box) vous fournissent des données de télémétrie standardisées sur votre application à comparer entre les builds Windows.

**Q : Pouvons-nous envoyer des tests en dehors des tests de démarrage (installer, lancer, fermer, désinstaller des scripts de test) ?**

**Un:** Oui, les clients peuvent également charger des packages d’application pour les **tests fonctionnels** via le tableau de bord du portail libre-service.
**Les tests fonctionnels** sont des tests qui permettent aux clients d’exécuter leurs scripts pour exécuter des fonctionnalités personnalisées sur leur application.

## <a name="testing"></a>Tests

**Q : Prenez-vous en charge les tests fonctionnels ?**

**Un:** Oui, la base de test prend en charge les tests fonctionnels. Les tests fonctionnels sont des tests qui permettent à nos clients d’exécuter leurs scripts pour exécuter des fonctionnalités personnalisées sur leur application.

Pour soumettre votre package d’application à des fins de test fonctionnel, chargez le dossier compressé contenant les fichiers binaires, les dépendances et les scripts de test de votre application via notre tableau de bord du portail libre-service.

Consultez le guide de l’utilisateur d’intégration pour plus d’informations ou contactez notre équipe <testbasepreview@microsoft.com> pour obtenir de l’aide et plus d’informations.

**Q : Comment la base de test gère-t-elle nos données de test ?**

**Un:** Test Base collecte et gère en toute sécurité vos données de test sur l’environnement Azure.

**Q : La base de tests peut-elle prise en charge nos tests automatisés ?**

**Un:** Oui, la base de tests prend en charge les tests automatisés, mais nous ne prenons pas en charge les tests manuels pour l’instant en raison des fonctionnalités de service.

**Q : Quels langages et infrastructures de tests automatisés prenez-vous en charge ?**

**Un:** Nous prenons en charge tous les langages et infrastructures. Nous venons d’appeler tous les scripts via PowerShell.

Vous devez également fournir (charger) les fichiers binaires dépendants de l’infrastructure requise.

**Q : À combien de temps la base de tests fournit-elle les résultats des tests ?**

**Un:** Pour chaque test que nous exécutons sur les builds en préversion, nous fournirons des résultats dans les 48 heures sur votre tableau de bord [du portail Azure](https://www.aka.ms/testbaseportal "Page d’accueil de base de test") .

**Q : Pouvez-vous redémarrer après l’installation ?**

**Un:** Oui, notre processus prend en charge le redémarrage après l’installation. Veillez à sélectionner cette option dans la liste déroulante « Paramètres facultatifs » lors de la définition **de vos tâches** sur le portail d’intégration.

Pour les tests OOB (Out-of-box), vous pouvez spécifier si un redémarrage est nécessaire pour le _script d’installation._

![Image de redémarrage.](Media/reboot.png)

Pendant les tests fonctionnels, vous pouvez spécifier si un redémarrage est nécessaire pour chaque script ajouté.

![Comment sélectionner des tests fonctionnels.](Media/functionalreboot.png)

**Q : Quelles versions de Windows prenez-vous en charge ?**

**Un:** Nous prenons actuellement en charge Windows 10 clients, Windows Server 2016, Windows Server 2016 version Core, Windows Server 2019 et Windows Server 2019 Core.

**Q : Quelle est la différence entre les tests de mise à jour de sécurité et les tests de mise à jour des fonctionnalités ?**

**Un:** Pour les tests de mise à jour de sécurité, nous testons les **<ins>mises à jour de sécurité mensuelles préliminaires</ins>** sur Windows, qui sont axées sur la sécurité et la protection de nos utilisateurs. Pour les tests de mise à jour des fonctionnalités, nous testons les **<ins>mises à jour de fonctionnalités préliminaires bi-annuelles</ins>** qui introduisent de nouvelles fonctionnalités et fonctionnalités sur Windows.

## <a name="debugging-options"></a>Options de débogage

**Q : Avons-nous accès au Machines Virtuelles (machines virtuelles) en cas de défaillance ? Que partage Test Base ?**

**Un:** Pour que le service soit conforme et que les mises à jour en préversion soient sécurisées, seul Microsoft a accès aux machines virtuelles. Toutefois, les clients peuvent afficher les résultats des tests et d’autres métriques de test sur leur tableau de bord du portail, notamment les signaux d’incident et de blocage, les métriques de fiabilité, l’utilisation de la mémoire et du processeur, etc. Nous générons et fournissons également des journaux d’activité des exécutions de test sur le tableau de bord pour le téléchargement et une analyse plus approfondie.

Nous pouvons également fournir des vidages de mémoire pour le débogage d’incident en fonction des besoins.

**Q : Si des problèmes sont détectés pendant le test, quelles sont les étapes suivantes pour résoudre ces problèmes ?**

**Un:** L’équipe de base de test effectue un processus de triage initial pour déterminer la cause racine de l’erreur, puis, en fonction de nos résultats, nous allons router vers le client ou les équipes internes au sein de Microsoft pour le débogage.

Nous travaillons toujours en étroite collaboration avec nos clients dans la correction conjointe pour résoudre les problèmes.

**Q : Microsoft conserve-t-il la version du correctif de sécurité jusqu’à ce que le problème soit résolu ? Quelles sont les autres résolutions disponibles ?**

**Un:** L’objectif de la base de test est de s’assurer que nos clients finaux communs ne rencontrent aucun problème. Nous travaillerons dur avec les éditeurs de logiciels pour résoudre tous les problèmes avant la publication, mais dans le cas où le correctif n’est pas possible, nous avons d’autres résolutions telles que les shims et les blocs.

## <a name="miscellaneous"></a>Divers

**Q : Comment le service fonctionnera-t-il avec un serveur local ?**

**Un:** Actuellement, nous ne prenons pas en charge les serveurs locaux. Toutefois, si le serveur expose le point de terminaison HTTP, nous pouvons nous y connecter via Internet.

**Q : Qui héberge les machines virtuelles ?**

**Un:** Microsoft provisionne la machine virtuelle pour ce service, en prenant la charge de le faire auprès du client.

**Q : Ce service prend-il en charge les applications web, mobiles ou de bureau ?**

**Un:** Actuellement, nous nous concentrons sur les applications de bureau. Toutefois, nous prévoyons d’intégrer des applications web à l’avenir, mais nous ne prenons pas en charge les applications mobiles pour l’instant.

**Q : Quelle est la différence entre Test Base et SUVP ?**

**Un:** La plus grande différence entre Test Base et SUVP est que nos partenaires intègrent leurs applications à l’environnement Azure de base de test pour les exécutions de validation par rapport aux mises à jour de préversion au lieu d’effectuer eux-mêmes les tests.

En plus des tests des mises à jour de sécurité en préversion, nous prenons en charge les tests des mises à jour de fonctionnalités en préversion sur notre plateforme. Notre feuille de route comporte de nombreux autres types de mises à jour et de tests de système d’exploitation.

**Q : Y a-t-il un coût associé au service ?**

**Un:** À compter du 1er mars 2022, vous recevrez 100 heures gratuites (d’une valeur de 800 $) arrivant à expiration dans 6 mois sous votre abonnement pour vos besoins de validation. Une fois les heures gratuites consommées (ou expirées avant d’être utilisées), vous êtes automatiquement limité à 8 $ l’heure par rapport à votre utilisation.

**Q : Comment puis-je fournir des commentaires sur la base de test ?**

**Un:** Pour partager vos commentaires sur la base de tests, sélectionnez l’icône **Commentaires** en bas à gauche du portail. Incluez une capture d’écran avec votre soumission pour aider Microsoft à mieux comprendre vos commentaires.

Vous pouvez également soumettre des suggestions de produit et proposer d’autres idées à l’adresse <testbasepreview@microsoft.com>.
