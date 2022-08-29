---
title: Charger des fichiers binaires d’application
description: Prise en main de la base de tests pour Microsoft 365
search.appverid: MET150
author: mansipatel-usl
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: test-base
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: tinachen
f1.keywords: NOCSH
ms.openlocfilehash: fdb5bfed0eb103be68e1a8967dc97f9fbe64683e
ms.sourcegitcommit: eb81b49205cbc66b021326b8e2c00a8336b4a2fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67316400"
---
# <a name="step-3-upload-your-binaries-dependencies-and-scripts"></a>Étape 3 : Charger vos fichiers binaires, dépendances et scripts

Dans cet onglet, vous allez charger un package zip unique contenant vos fichiers binaires, dépendances et scripts utilisés pour exécuter votre suite de tests.

> [!NOTE]
> La taille du package zip doit être comprise entre un minimum de 10 Mo et un maximum de 2 Go.

## <a name="upload-package-zip-file"></a>Charger le fichier zip du package

:::image type="content" alt-text="Chargez vos fichiers binaires." source="Media/AddBinaries.png":::

  - Les dépendances chargées peuvent inclure des frameworks de test, des moteurs de script ou des données accessibles pour exécuter votre application ou les cas de test. Par exemple, vous pouvez charger Selenium et un programme d’installation de pilote web pour vous aider à exécuter des tests basés sur un navigateur.
  - Il est recommandé de s’assurer que vos activités de script sont toujours modulaires, c’est-à-dire.
    - Le `Install` script effectue uniquement des opérations d’installation.
    - Le `Launch` script lance uniquement l’application.
    - Le `Close` script ferme uniquement l’application.
    - Le script facultatif `Uninstall` désinstalle uniquement l’application.

**Actuellement, le portail prend uniquement en charge les scripts PowerShell.**


## <a name="next-steps"></a>Prochaines étapes 

Passez à l’article suivant pour passer à l’étape 4 : **Définir vos tâches de test**.
> [!div class="nextstepaction"]
> [Retour](uploadApplication.md)
> [!div class="nextstepaction"]
> [Étape suivante](testtask.md)

