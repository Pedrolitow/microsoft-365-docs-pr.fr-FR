---
title: Définir vos tâches de test
description: Définir vos tâches de test
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
ms.openlocfilehash: 64abb5b10e3dc1d52b6baf8ceccd5aff2baacefe
ms.sourcegitcommit: b0f464b6300e2977ed51395473a6b2e02b18fc9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2021
ms.locfileid: "53322691"
---
# <a name="step-4-the-tasks-tab"></a>Étape 4 : onglet Tâches

Sous l’onglet Tâches, vous devez fournir les chemins d’accès à vos scripts de test qui se trouveraient dans le dossier zip que vous avez chargé sous l’onglet fichiers binaires.

  - **Scripts de test out-of-box :** Tapez les chemins d’accès relatifs à vos scripts d’installation, de lancement, de fermeture et de désinstallation. Vous avez également la possibilité de sélectionner des paramètres supplémentaires pour le script d’installation.
  - **Scripts de test fonctionnels :** Tapez le chemin d’accès relatif à chaque script de test fonctionnel téléchargé. Des scripts de test fonctionnels supplémentaires peuvent être ajoutés à l’aide ```Add Script``` du bouton. Vous avez besoin d’au moins un script (1) et pouvez ajouter jusqu’à huit (8) scripts de test fonctionnels. 
  
    Les scripts sont exécutés dans la séquence de chargement et un échec dans un script particulier arrête l’exécution des scripts suivants.
    Vous avez également la possibilité de sélectionner des paramètres supplémentaires pour chaque script fourni.

## <a name="set-script-path"></a>Définir le chemin d’accès au script

![Image de la tâche de test](Media/testtask.png)

Voici un exemple de la façon de fournir le chemin d’accès relatif sur une structure de dossiers :

_**Zip_file_uploaded**_
~~~
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
~~~
  - **ScriptX.ps1** aurait été le cas. _ScriptX.ps1_ comme chemin d’accès relatif.
  - **Script.ps1** _dossier1/script.ps1_ comme chemin d’accès relatif.


## <a name="next-steps"></a>Étapes suivantes

Afficher les détails de l’onglet Options de test dans l’article suivant 
> [!div class="nextstepaction"]
> [Étape suivante](testoptions.md)
