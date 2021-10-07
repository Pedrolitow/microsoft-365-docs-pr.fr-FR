---
title: SDK de base de test pour Python
description: Informations sur la compréhension du SDK test base pour Python
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: article
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 9a4f64afbf02853ccb68098995c0f05baf2c9b01
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60211764"
---
# <a name="test-base-sdk-for-python"></a>SDK de base de test pour Python

## <a name="overview"></a>Présentation
Le SDK de base de test peut être utilisé pour interagir avec la ressource de base de test Azure. (c’est-à-dire, gérer votre package d’application, inclure créer un package, modifier un package et supprimer un package)

Avec le SDK, le résumé du test et le résultat d’analyse qui peuvent être obtenus incluent : scriptExecution, fiabilité, memoryUtilization, cpuUtilization, memoryRegression, cpuRegression.

Avec le SDK de base de test, vous pouvez intégrer la base de test dans votre pipeline CI/CD.

## <a name="client-library"></a>Bibliothèque cliente

Installez le package de base de test avec un pip.

~~~
pip install  Microsoft.Testbase
~~~
 
## <a name="example"></a>Exemple
