---
title: Test Base API & SDK
description: Test Base API & SDK
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
ms.openlocfilehash: 9e2c52d23c0e0c949059dc37eee4c1a59b35964e
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60704942"
---
# <a name="manage-your-resource-with-sdk--apis"></a>Gérer votre ressource avec les API de & SDK
L’automatisation est un aspect clé de DevOps développement agile. Souhaitez-vous gérer la Base de test pour Microsoft 365 ressources de test, obtenir les résultats des tests par programme et les intégrer à nos outils CI ? Les API de base de test/SDK peuvent vous aider à atteindre tous ces objectifs et bien plus encore ! 

Ces API/SDK permettent aux professionnels de l’informatique et aux développeurs d’applications de : 
- Gérer les comptes de base de test, y compris créer, mettre à jour et horsboard. 
- Gérer les packages d’application, y compris créer, mettre à jour, supprimer et télécharger un package. 
- Obtenez le résumé des tests, les résultats détaillés des tests et les résultats de l’analyse. Le résultat de l’analyse inclut l’analyse de la régression du processeur, l’analyse de l’utilisation du processeur, l’analyse de la régression de la mémoire et l’analyse de l’utilisation de la mémoire. 
- Téléchargez les résultats des tests et testez l’enregistrement vidéo de l’exécution.  

Consultez le plan pas à pas ci-dessous pour savoir comment accéder à cette nouvelle fonctionnalité dans la base de test Microsoft 365 service.

## <a name="a-step-by-step-example-of-test-base-account-creation-by-using-python-sdk"></a>Exemple pas à pas de création de compte de base de test à l’aide du SDK Python

1. Conditions préalables : 

- Installez les composants requis ci-dessous : 

    [Compte Azure avec un abonnement actif](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup) si vous n’avez pas d’abonnement<br>
    [Python 2.7+ ou 3.6+](https://www.python.org/downloads)<br>
    [Interface Command-Line Azure (CLI)](/cli/azure/install-azure-cli) <br>

- Installer des packages de bibliothèque à l’aide de l’installation de pip à partir de la console 

```
pip install azure-identity 
pip install azure-mgmt-testbase  
```

- Authentification dans l’environnement dev 

Lors du débogage et de l’exécution de code localement, il est courant pour les développeurs d’utiliser leurs propres comptes pour authentifier les appels aux services Azure. Le package azure-identity prend en charge l’authentification via Azure CLI pour simplifier le développement local. Pour vous inscrire à Azure CLI, exécutez ```az login ``` . Sur un système avec un navigateur web par défaut, azure CLI lance le navigateur pour authentifier un utilisateur. 

Vérifiez [comment authentifier les applications Python avec les services Azure| Microsoft Docs et](/azure/developer/python/azure-sdk-authenticate)  pour [https://pypi.org/project/azure-identity/](https://pypi.org/project/azure-identity/) d’autres méthodes d’authentification pris en charge. 

 - Créez un groupe de ressources avec le nom souhaité qui sera utilisé dans les étapes suivantes. 

2. L’extrait de code ci-dessous couvre le flux pour créer un compte de base de test, y compris 

- Demander des informations d’identification via Azure CLI pour l’interaction avec Azure 
- Initialiser le client SDK de base de test avec les informations d’identification et l’ID d’abonnement pour les opérations ultérieures 
- Appeler begin_create à partir test_base_accounts modèle de test pour créer un compte de base de test 

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


## <a name="learn-more"></a>Si vous souhaitez en savoir plus 

Consultez les liens ci-dessous pour en savoir plus sur l’API & SDK. 

**Abonnement Azure** 

- [Compte Azure avec un abonnement actif](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup) 

**Kit de développement logiciel Python** 

- [Test Base Python SDK Documentation](/python/api/overview/azure/mgmt-testbase-readme?view=azure-python-preview)
- [Exemple de SDK Python de base de test](https://aka.ms/testbase-sample-py) 
- [Modèle d’utilisation générale Azure du SDK Python](/azure/developer/python/azure-sdk-overview#provision-and-manage-azure-resources-with-management-libraries) 

**API REST**  

- [Documentation de l’API REST](https://aka.ms/testbase-api)  
