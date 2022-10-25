---
title: Désactiver les rapports lorsque vous exportez les résultats de recherche de contenu
description: Modifiez le Registre Windows sur votre ordinateur local pour désactiver les rapports lorsque vous exportez les résultats d’une recherche de contenu à partir du portail de conformité Microsoft Purview.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
ms.collection:
- tier1
- purview-compliance
- content-search
ms.openlocfilehash: 13e47bc69a72ef5ebfcd38f2dee4c0652b0853f2
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68687637"
---
# <a name="disable-reports-when-you-export-content-search-results"></a>Désactiver les rapports lorsque vous exportez les résultats de recherche de contenu

Lorsque vous utilisez l’outil d’exportation eDiscovery pour exporter les résultats d’une recherche de contenu dans le portail de conformité Microsoft Purview, l’outil crée et exporte automatiquement deux rapports qui contiennent des informations supplémentaires sur le contenu exporté. Ces rapports sont le fichier Results.csv et le fichier Manifest.xml (consultez la section [Forum aux questions sur la désactivation des rapports d’exportation](#frequently-asked-questions-about-disabling-export-reports) dans cet article pour obtenir des descriptions détaillées de ces rapports). Étant donné que ces fichiers peuvent être très volumineux, vous pouvez accélérer le temps de téléchargement et économiser de l’espace disque en empêchant l’exportation de ces fichiers. Pour ce faire, vous pouvez modifier le Registre Windows sur l’ordinateur que vous utilisez pour exporter les résultats de la recherche. Si vous souhaitez inclure les rapports ultérieurement, vous pouvez modifier le paramètre de Registre. 
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="create-registry-settings-to-disable-the-export-reports"></a>Créer des paramètres de Registre pour désactiver les rapports d’exportation

Effectuez la procédure suivante sur l’ordinateur que vous utiliserez pour exporter les résultats d’une recherche de contenu.
  
1. Fermez l’outil d’exportation eDiscovery s’il est ouvert.
  
2. Effectuez l’une des étapes suivantes, ou les deux, selon le rapport d’exportation que vous souhaitez désactiver.

    - **Results.csv**

      Enregistrez le texte suivant dans un fichier de Registre Windows en utilisant le suffixe de nom de fichier .reg ; par exemple, DisableResultsCsv.reg.

      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d False 
      ```

    - **Manifest.xml**

      Enregistrez le texte suivant dans un fichier de Registre Windows en utilisant le suffixe de nom de fichier .reg ; par exemple, DisableManifestXml.reg.

      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d False 
      ```

3. Dans l’Explorateur Windows, sélectionnez ou double-cliquez sur le fichier .reg que vous avez créé dans les étapes précédentes.

4. Dans la fenêtre Access Control utilisateur, sélectionnez **Oui** pour permettre à l’Éditeur du Registre d’apporter la modification. 

5. Lorsque vous êtes invité à continuer, sélectionnez **Oui**.

    L’Éditeur du Registre affiche un message indiquant que le paramètre a été correctement ajouté au Registre.
  
## <a name="edit-registry-settings-to-re-enable-the-export-reports"></a>Modifier les paramètres du Registre pour réactiver les rapports d’exportation

Si vous avez désactivé les rapports Results.csv et Manifest.xml en créant les fichiers .reg dans la procédure précédente, vous pouvez modifier ces fichiers pour réactiver un rapport afin qu’il soit exporté avec les résultats de la recherche. Là encore, effectuez la procédure suivante sur l’ordinateur que vous utiliserez pour exporter les résultats d’une recherche de contenu.
  
1. Fermez l’outil d’exportation eDiscovery s’il est ouvert.

2. Modifiez un ou les deux fichiers de modification .reg que vous avez créés dans la procédure précédente.

    - **Results.csv**

        Ouvrez le fichier DisableResultsCsv.reg dans le Bloc-notes, remplacez la valeur  `False`  `True`par , puis enregistrez le fichier. Par exemple, après avoir modifié le fichier, il ressemble à ceci :

        ```text
        Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d True
        ```

    - **Manifest.xml**

        Ouvrez le fichier DisableManifestXml.reg dans le Bloc-notes, remplacez la valeur  `False`  `True`par , puis enregistrez le fichier. Par exemple, après avoir modifié le fichier, il ressemble à ceci :

      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d True
      ```

3. Dans l’Explorateur Windows, sélectionnez ou double-cliquez sur un fichier .reg que vous avez modifié à l’étape précédente.

4. Dans la fenêtre Access Control utilisateur, sélectionnez **Oui** pour permettre à l’Éditeur du Registre d’apporter la modification. 

5. Lorsque vous êtes invité à continuer, sélectionnez **Oui**.

    L’Éditeur du Registre affiche un message indiquant que le paramètre a été correctement ajouté au Registre.
  
## <a name="frequently-asked-questions-about-disabling-export-reports"></a>Forum aux questions sur la désactivation des rapports d’exportation

**Quels sont les rapports Results.csv et Manifest.xml ?**
  
Les fichiers Results.csv et Manifest.xml contiennent des informations supplémentaires sur le contenu exporté.
  
- **Results.csv** Document Excel qui contient des informations sur chaque élément téléchargé en tant que résultat de recherche. Pour le courrier électronique, le journal des résultats contient des informations sur chaque message, y compris : 

  - l’emplacement du message dans la boîte aux lettres source (notamment si le message est dans la boîte aux lettres principale ou d’archivage) ;
  - la date à laquelle le message a été envoyé ou reçu ;
  - l’objet du message ;
  - l’expéditeur et les destinataires du message.
  - Indique si le message est un message en double si vous avez activé la déduplication lors de l’exportation des résultats de la recherche. Les messages en double ont une valeur dans la colonne **Parent ItemId** qui identifie le message en tant que doublon. La valeur dans la colonne **Parent ItemId** est identique à la valeur dans la colonne **Item DocumentId** du message qui a été exporté.

  Pour les documents provenant de sites SharePoint et OneDrive Entreprise, le journal des résultats contient des informations sur chaque document, notamment :

  - l’URL du document ;
  - l’URL de la collection de sites qui héberge le document ;
  - la date à laquelle le document a été modifié pour la dernière fois ;
  - le nom du document (qui se trouve dans la colonne Objet du journal des résultats).

- **Manifest.xml** Fichier manifeste (au format XML) qui contient des informations sur chaque élément inclus dans les résultats de la recherche. Les informations contenues dans ce rapport sont identiques à celles du rapport Results.csv, mais elles sont au format spécifié par le modèle de référence de découverte électronique (EDRM). Pour plus d’informations sur EDRM, accédez à [https://www.edrm.net](https://www.edrm.net).

**Quand dois-je désactiver l’exportation de ces rapports ?**
  
Cela dépend de vos besoins spécifiques. De nombreuses organisations n’ont pas besoin d’informations supplémentaires sur les résultats de la recherche et n’ont pas besoin de ces rapports.
  
**Sur quel ordinateur dois-je effectuer cette opération ?**
  
Vous devez modifier le paramètre de Registre sur n’importe quel ordinateur local sur lequel vous exécutez l’outil d’exportation eDiscovery. 
  
**Après avoir modifié ce paramètre, dois-je redémarrer l’ordinateur ?**
  
Non, vous n’avez pas besoin de redémarrer l’ordinateur. Toutefois, si l’outil d’exportation eDiscovery est en cours d’exécution, vous devez le fermer, puis le redémarrer après avoir modifié le paramètre de Registre.
  
**Une clé de Registre existante est-elle modifiée ou une nouvelle clé est-elle créée ?**
  
Une nouvelle clé de Registre est créée la première fois que vous exécutez le fichier .reg que vous avez créé dans la procédure décrite dans cet article. Ensuite, le paramètre est modifié chaque fois que vous modifiez et réexécutez le fichier de modification .reg.
