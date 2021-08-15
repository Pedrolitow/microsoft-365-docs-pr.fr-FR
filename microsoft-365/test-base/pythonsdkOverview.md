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
localization_priority: Normal
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 64c47566959cbe83088ac7855f8f3cd6a8473d2ad86d5ab2957fbbdf41d10bf7
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53852958"
---
# <a name="test-base-sdk-for-python"></a>SDK de base de test pour Python

## <a name="overview"></a>Vue d’ensemble
Le SDK de base de test peut être utilisé pour interagir avec la ressource de base de test Azure. (c’est-à-dire, gérer votre package d’application, inclure créer un package, modifier un package et supprimer un package)

Avec le SDK, le résumé du test et le résultat d’analyse qui peuvent être obtenus incluent : scriptExecution, fiabilité, memoryUtilization, cpuUtilization, memoryRegression, cpuRegression.

Avec le SDK de base de test, vous pouvez intégrer la base de test dans votre pipeline CI/CD.

## <a name="client-library"></a>Bibliothèque cliente

Installez le package de base de test avec un pip.

~~~
pip install  Microsoft.Testbase
~~~
 
## <a name="example"></a>Exemple
