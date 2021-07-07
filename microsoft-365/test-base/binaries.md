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
ms.openlocfilehash: 1c4ff6ac03989cc9be70e18a1b8634f2da11e721
ms.sourcegitcommit: b0f464b6300e2977ed51395473a6b2e02b18fc9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2021
ms.locfileid: "53322816"
---
# <a name="step-3-upload-your-binaries-dependencies-and-scripts"></a>Étape 3 : Télécharger vos binaires, dépendances et scripts

Sous cet onglet, vous allez télécharger un package zip unique contenant vos fichiers binaires, dépendances et scripts utilisés pour exécuter votre suite de test.

## <a name="upload-package-zip-file"></a>Télécharger fichier zip du package

![Télécharger vos binaires](Media/AddBinaries.png)

  - Les dépendances téléchargées peuvent inclure des frameworks de test, des moteurs de script ou des données accessibles pour exécuter votre application ou des cas de test. Par exemple, vous pouvez télécharger Selenium et un programme d’installation webdriver pour vous aider à exécuter des tests basés sur le navigateur.
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

