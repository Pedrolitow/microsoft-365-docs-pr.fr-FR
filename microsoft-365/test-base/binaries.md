---
title: Télécharger Binaires d’application
description: Comment commencer à utiliser la base de test pour M365
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
localization_priority: Normal
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 38c21f69680d6e9d6a3231c8bf2dc44f15e057f6
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59208531"
---
# <a name="step-3-upload-your-binaries-dependencies-and-scripts"></a>Étape 3 : Télécharger vos binaires, dépendances et scripts

Sous cet onglet, vous allez télécharger un package zip unique contenant vos fichiers binaires, dépendances et scripts utilisés pour exécuter votre suite de test.

## <a name="upload-package-zip-file"></a>Télécharger fichier zip de package

![Télécharger vos binaires.](Media/AddBinaries.png)

  - Les dépendances téléchargées peuvent inclure des frameworks de test, des moteurs de script ou des données accessibles pour exécuter votre application ou des cas de test. Par exemple, vous pouvez charger Selenium et un programme d’installation webdriver pour vous aider à exécuter des tests basés sur le navigateur.
  - Il est préférable de s’assurer que vos activités de script restent modulaires, c’est-à-dire. 
    - Le ```Install``` script effectue uniquement des opérations d’installation.
    - Le ```Launch``` script lance uniquement l’application.
    - Le ```Close``` script ferme uniquement l’application.
    - Le ```Uninstall``` script facultatif désinstalle uniquement l’application.

**Actuellement, le portail prend uniquement en charge les scripts PowerShell.**


## <a name="next-steps"></a>Étapes suivantes 

Passer à l’article suivant pour passer à l’étape 4 : **Définir vos tâches de test.**
> [!div class="nextstepaction"]
> [Retour](uploadApplication.md)
> [!div class="nextstepaction"]
> [Étape suivante](testtask.md)

