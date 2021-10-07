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
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 200da9ca73bc666f3f11fc3fda95493d2c0954fb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60180638"
---
# <a name="step-3-upload-your-binaries-dependencies-and-scripts"></a>Étape 3 : Télécharger vos binaires, dépendances et scripts

Sous cet onglet, vous allez télécharger un package zip unique contenant vos fichiers binaires, dépendances et scripts utilisés pour exécuter votre suite de test.

> [!NOTE]
> La taille du package zip doit être entre 10 Mo et 2 Go au maximum.

## <a name="upload-package-zip-file"></a>Télécharger fichier zip de package

:::image type="content" alt-text="Télécharger vos binaires." source="Media/AddBinaries.png":::

  - Les dépendances téléchargées peuvent inclure des frameworks de test, des moteurs de script ou des données accessibles pour exécuter votre application ou des cas de test. Par exemple, vous pouvez télécharger Selenium et un programme d’installation de pilotes web pour vous aider à exécuter des tests basés sur le navigateur.
  - Il est préférable de s’assurer que vos activités de script restent modulaires, c’est-à-dire. 
    - Le `Install` script effectue uniquement des opérations d’installation.
    - Le `Launch` script lance uniquement l’application.
    - Le `Close` script ferme uniquement l’application.
    - Le `Uninstall` script facultatif désinstalle uniquement l’application.

**Actuellement, le portail prend uniquement en charge les scripts PowerShell.**


## <a name="next-steps"></a>Étapes suivantes 

Passer à l’article suivant pour passer à l’étape 4 : **Définir vos tâches de test.**
> [!div class="nextstepaction"]
> [Retour](uploadApplication.md)
> [!div class="nextstepaction"]
> [Étape suivante](testtask.md)

