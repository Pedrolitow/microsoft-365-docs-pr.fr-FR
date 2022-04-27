---
title: Kit de développement logiciel (SDK) d’API de base de test &
description: Kit de développement logiciel (SDK) d’API de base de test &
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 6ae0fdf9cc49faaaff84eb3f96e076d1efba8a4c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077437"
---
# <a name="manage-your-resource-with-sdk--apis"></a>Gérer votre ressource avec le Kit de développement logiciel (SDK) & DES API

L’automatisation est un aspect clé du développement DevOps et agile. Cherchez-vous à gérer la base de tests pour Microsoft 365 ressources, à obtenir des résultats de test par programme et à les intégrer à nos outils CI ? Les API de base de test/kit de développement logiciel (SDK) peuvent vous aider à atteindre tous ces objectifs et bien plus encore !

Ces API/SDK permettent aux professionnels de l’informatique et aux développeurs d’applications d’effectuer les opérations suivantes :

- Gérez les comptes de base de test, notamment la création, la mise à jour et la désintégrage.
- Gérez les packages d’application, notamment créer, mettre à jour, supprimer et télécharger le package.
- Obtenez le résumé des tests, les résultats détaillés des tests et les résultats d’analyse. Le résultat de l’analyse inclut l’analyse de régression du processeur, l’analyse de l’utilisation du processeur, l’analyse de régression de la mémoire et l’analyse de l’utilisation de la mémoire.
- Téléchargez les résultats des tests et l’enregistrement vidéo de l’exécution des tests.

Consultez le plan pas à pas ci-dessous pour savoir comment accéder à cette nouvelle fonctionnalité dans la base de test pour Microsoft 365 service.

## <a name="a-step-by-step-example-of-test-base-account-creation-by-using-python-sdk"></a>Exemple pas à pas de création de compte de base de test à l’aide du Kit de développement logiciel (SDK) Python

1. Conditions préalables :

   - Installez les composants requis ci-dessous :

     - [Compte Azure avec un abonnement actif](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup) si vous n’avez pas d’abonnement
     - [Python 2.7+ ou 3.6+](https://www.python.org/downloads)
     - [Interface de Command-Line Azure (CLI)](/cli/azure/install-azure-cli)

   - Installer des packages de bibliothèque à l’aide de l’installation pip à partir de la console

     ```console
     pip install azure-identity
     pip install azure-mgmt-testbase
     ```

   - Authentification dans un environnement de développement

     Lors du débogage et de l’exécution du code localement, il est courant pour les développeurs d’utiliser leurs propres comptes pour authentifier les appels aux services Azure. Le package azure-identity prend en charge l’authentification via Azure CLI pour simplifier le développement local. Pour vous connecter à Azure CLI, exécutez `az login`. Sur un système avec un navigateur web par défaut, Azure CLI lance le navigateur pour authentifier un utilisateur.

     Découvrez [comment authentifier des applications Python avec les services Azure| Microsoft Docs](/azure/developer/python/azure-sdk-authenticate) et <https://pypi.org/project/azure-identity/> pour d’autres méthodes d’authentification prises en charge.

   - Créez un groupe de ressources avec le nom souhaité qui sera utilisé dans les étapes suivantes.

2. L’extrait de code ci-dessous couvre le flux de création d’un compte de base de test, y compris

   - Demander des informations d’identification via Azure CLI pour une interaction avec Azure
   - Initialiser le client du Kit de développement logiciel (SDK) de base de test avec les informations d’identification et l’ID d’abonnement pour les opérations ultérieures
   - Appeler begin_create à partir d’un modèle test_base_accounts pour créer un compte de base de test

   Copiez le code dans votre environnement de développement Python et remplacez « subscription-id » par votre ID d’abonnement Azure et « resource-group-name » par votre groupe de ressources que vous avez créé ci-dessus.

   ```python
   from azure.identity import AzureCliCredential
   from azure.mgmt.testbase import TestBase
   from azure.mgmt.testbase.models import TestBaseAccountResource
   from azure.mgmt.testbase.models import TestBaseAccountSKU

   # requesting token from Azure CLI for request
   # For other authentication approaches, please see: https://pypi.org/project/azure-identity/
   credential = AzureCliCredential()
   subscription_id = "<subscription-id>"
   resource_group = "<resource-group-name>"
   testBaseAccount_name = "contoso-testbaseAccount"
   testBaseAccount_location = "global"
   sku_name = "S0"
   sku_tier = "Standard"
   sku_locations = {"global"}
  
   # Create client
   testBase_client = TestBase(credential, subscription_id)
  
   # Create sku for test base account
   sku = TestBaseAccountSKU(name=sku_name, tier=sku_tier, locations=sku_locations)
  
   # Create test base account
   parameters = TestBaseAccountResource(location=testBaseAccount_location, sku=sku)
   testBaseAccount = testBase_client.test_base_accounts.begin_create(resource_group, testBaseAccount_name, parameters).result()
   print("Create test base account:\n{}".format(testBaseAccount))
   ```

## <a name="learn-more"></a>En savoir plus

Consultez les liens ci-dessous pour en savoir plus sur le Kit de développement logiciel (SDK) & API.

**Abonnement Azure** :

- [Compte Azure avec un abonnement actif](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup)

**Kit de développement logiciel (SDK) Python** :

- [Documentation du Kit de développement logiciel (SDK) Python de base de test](/python/api/overview/azure/mgmt-testbase-readme)
- [Exemple de Kit de développement logiciel (SDK) Python de base de test](https://aka.ms/testbase-sample-py)
- [Modèle d’utilisation générale Azure du Kit de développement logiciel (SDK) Python](/azure/developer/python/sdk/azure-sdk-library-usage-patterns)

**API REST** :

- [Documentation de l’API REST](https://aka.ms/testbase-api)
