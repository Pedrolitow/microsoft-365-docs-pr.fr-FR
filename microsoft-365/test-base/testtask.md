---
title: Définir vos tâches de test
description: Définir vos tâches de test
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
ms.openlocfilehash: 3356fc09609601d1974cb3daea7ea7aeb6ac979e
ms.sourcegitcommit: eb81b49205cbc66b021326b8e2c00a8336b4a2fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67316334"
---
# <a name="step-4-the-tasks-tab"></a>Étape 4 : Onglet Tâches

Sous l’onglet Tâches, vous êtes censé fournir les chemins d’accès à vos scripts de test qui se trouvent dans le dossier zip que vous avez chargé sous l’onglet Binaires.

  - **Scripts de test out of box :** Tapez les chemins relatifs de vos scripts d’installation, de lancement, de fermeture et de désinstallation. Vous pouvez également sélectionner des paramètres supplémentaires pour le script d’installation.
  - **Scripts de test fonctionnel :** Tapez le chemin relatif de chaque script de test fonctionnel chargé. Vous pouvez ajouter des scripts de test fonctionnels supplémentaires à l’aide du ```Add Script``` bouton. Vous avez besoin d’au moins un (1) script et pouvez ajouter jusqu’à huit (8) scripts de test fonctionnels. 
  
    Les scripts s’exécutent dans la séquence dans laquelle ils sont répertoriés. Un échec dans un script particulier empêche l’exécution des scripts suivants.
    Vous avez également la possibilité de sélectionner des paramètres supplémentaires pour chaque script fourni.

## <a name="set-script-path"></a>Définir le chemin d’accès du script

![Image de la tâche de test.](Media/testtask.png)

Voici un exemple de comment fournir le chemin relatif sur une structure de dossiers :

_**Zip_file_uploaded**_
~~~
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
~~~
  - **ScriptX.ps1l’aurais** fait. _ScriptX.ps1_ comme chemin d’accès relatif.
  - **Script.ps1** aurait _dossier1/script.ps1_ comme chemin d’accès relatif.


## <a name="next-steps"></a>Prochaines étapes

Afficher les détails de l’onglet Options de test dans l’article suivant 
> [!div class="nextstepaction"]
> [Étape suivante](testoptions.md)
