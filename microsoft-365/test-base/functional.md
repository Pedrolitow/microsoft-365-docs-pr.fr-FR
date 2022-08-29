---
title: Test fonctionnel sur la base de test
description: Détails sur la façon de tester votre application avec vos tests fonctionnels automatisés existants
search.appverid: MET150
author: mansipatel-usl
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: test-base
ms.localizationpriority: medium
ms.collection: TestBase-Microsoft 365
ms.custom: ''
ms.reviewer: tinachen
f1.keywords: NOCSH
ms.openlocfilehash: 566ca739c15920d1d9c1260d7b7e771dd984b9d8
ms.sourcegitcommit: eb81b49205cbc66b021326b8e2c00a8336b4a2fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67315485"
---
# <a name="functional-testing"></a>Test fonctionnel

En tant qu’éditeur de logiciels, vous pouvez désormais effectuer des tests fonctionnels personnalisés à l’aide de l’infrastructure de test de votre choix, via la base de test libre-service pour le portail Microsoft 365. 

Lorsque nous avons lancé le service au départ, nous avons proposé les tests out-of-box, qui est un ensemble prédéfini de tests pilotés par le biais de scripts standardisés. Toutefois, cela n’a pas pu obtenir une couverture complète des tests pour de nombreux éditeurs de logiciels indépendants (ISV). 

Par conséquent, en réponse à vos commentaires, nous fournissons à nos éditeurs de logiciels indépendants la possibilité de charger des tests fonctionnels automatisés.

Pour utiliser cette fonctionnalité, suivez les étapes ci-dessous :

1. Chargez vos fichiers (fichiers binaires, dépendances et scripts) en tant que package .zip unique.
2. Choisissez si vous souhaitez redémarrer le test Machines Virtuelles (machines virtuelles) à différents points d’exécution.
3. Gérez les options disponibles pour vos scripts.
4. Choisissez quand appliquer la mise à jour Windows sur la machine virtuelle pendant l’exécution.

Les descriptions détaillées des étapes ci-dessus sont mises en évidence ci-dessous :

**Charger un package de test fonctionnel**

Pour commencer, accédez à la page Charger, sélectionnez Charger une nouvelle application sous le catalogue d’applications dans le menu de navigation de gauche du portail De base de test pour M365 dans Azure. À partir de là :

Onglet 1 - Entrez les informations de base. Indiquez le nom et la version de votre application. Dans l’option Type de test, sélectionnez ```Functional tests```. 

*L’option OOB (Out-of-Box) est requise par défaut.*


![Sélectionnez l’onglet Test fonctionnel.](Media/functional_testing_tab1.png)

Onglet 2 : Chargez les composants de votre package en chargeant un fichier zip avec l’intégralité de votre test (fichiers binaires, dépendances, scripts, etc.). 

Pour plus d’informations, consultez aka.ms/usl-package-outline. (Remarque : les scripts de test out-of-box et le contenu du test fonctionnel doivent être placés dans le même fichier zip). Actuellement, la taille du fichier est limitée à 2 Go.

Onglet 3 : Configurer les tâches de test out-of-box et fonctionnelles. Ici, choisissez le ou les chemins d’accès aux scripts PowerShell qui installeront, lanceront, fermeront et désinstalleront votre application (pour Out-of-Box) et le ou les chemins d’accès à tous vos scripts personnalisés pour effectuer votre test fonctionnel. **(Remarque : un script pour désinstaller votre application est facultatif).**

Actuellement, vous pouvez charger 1 à 8 scripts pour vos tests fonctionnels. (Veuillez commenter ce billet si vous avez besoin de scripts supplémentaires !)

![Chargez jusqu’à 8 scripts avec des tests fonctionnels.](Media/functional_testing_tab3.png)

(Facultatif) Vous pouvez configurer un redémarrage après l’installation. Certaines applications nécessitent un redémarrage après l’installation. 

Sélectionnez ```Reboot After Execution``` le script spécifique dans l’onglet Tâches si vous souhaitez qu’un redémarrage soit effectué après l’exécution de ce script.

Onglet 4 - Choisir quand la mise à jour Windows est installée : l’application du correctif Windows Update est effectuée avant tout script de votre choix. Il est recommandé d’installer une mise à jour Windows après l’installation de l’application pour imiter étroitement les scénarios d’utilisation de votre application réelle.

![La mise à jour Windows peut être installée après un script spécifique.](Media/functional_testing_tab4.png)

Onglet 5 : examinez et créez le package. Une fois que vous avez terminé les étapes répertoriées ci-dessus, sélectionnez ```Create``` cette option pour terminer le processus de chargement.

Une fois votre package créé, vous pouvez vérifier l’état de vérification de votre package.

Nous exécutons un test initial pour installer, lancer, fermer et désinstaller votre application. Cela nous permet de vérifier que votre package peut être installé sur notre service sans erreur.

Le processus de vérification peut prendre jusqu’à 24 heures. Une fois la vérification terminée, vous pouvez voir l’état dans le ```Manage packages``` menu, qui serait l’une des deux entrées suivantes :

1. La vérification réussit : le package est automatiquement testé par rapport aux mises à jour Windows en préversion pour les builds de système d’exploitation que vous avez sélectionnées.
ou
2. Échec de la vérification : vous devez examiner les raisons de l’échec, résoudre le problème et recharger votre package.

Vous serez également averti de l’un ou l’autre des résultats via l’icône de notification dans le Portail Azure.
