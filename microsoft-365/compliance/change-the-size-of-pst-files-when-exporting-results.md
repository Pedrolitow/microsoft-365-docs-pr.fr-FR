---
title: Modifier la taille des fichiers PST lors de l’exportation des résultats de recherche eDiscovery
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/12/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 04e9de2d-765b-457b-a98a-d0f60bfb13f2
description: Vous pouvez modifier la taille par défaut des fichiers PST téléchargés sur votre ordinateur lorsque vous exportez les résultats de la recherche eDiscovery.
ms.openlocfilehash: e7bdce22aa573ab74e9432dbc0c2c6b60109cac6
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67818696"
---
# <a name="change-the-size-of-pst-files-when-exporting-ediscovery-search-results"></a>Modifier la taille des fichiers PST lors de l’exportation des résultats de recherche eDiscovery

Lorsque vous utilisez l’outil d’exportation eDiscovery pour exporter les résultats d’une recherche eDiscovery à partir des différents outils Microsoft eDiscovery, la taille par défaut d’un fichier PST pouvant être exporté est de 10 Go. Si vous souhaitez modifier cette taille par défaut, vous pouvez modifier le Registre Windows sur l’ordinateur que vous utilisez pour exporter les résultats de la recherche. Une raison de le faire est qu’un fichier PST peut tenir sur un support amovible, tel qu’un DVD, un disque compact ou un lecteur USB. 
  
> [!NOTE]
> L’outil d’exportation eDiscovery est utilisé pour exporter les résultats de recherche lors de l’utilisation de l’outil de recherche de contenu dans le portail de conformité Microsoft Purview.
  
## <a name="create-a-registry-setting-to-change-the-size-of-pst-files-when-you-export-ediscovery-search-results"></a>Créer un paramètre de Registre pour modifier la taille des fichiers PST lorsque vous exportez des résultats de recherche eDiscovery

Effectuez la procédure suivante sur l’ordinateur que vous allez utiliser pour exporter les résultats d’une recherche eDiscovery.
  
1. Fermez l’outil d’exportation eDiscovery s’il est ouvert. 
    
2. Enregistrez le texte suivant dans un fichier de Registre Window à l’aide d’un suffixe de nom de fichier .reg ; par exemple, PstExportSize.reg. 
    
    ```text
    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool]
    "PstSizeLimitInBytes"="1073741824"
    ```

    Dans l’exemple ci-dessus, la  `PstSizeLimitInBytes` valeur est définie sur 1 073 741 824 octets, soit environ 1 Go. Voici quelques autres exemples de valeurs pour le  `PstSizeLimitInBytes` paramètre. 
    
    |**Taille en Go (environ.)**|**Taille en octets**|
    |:-----|:-----|
    |0,7 Go (700 Mo)  <br/> |751619277  <br/> |
    |2 Go  <br/> |2147483648  <br/> |
    |4 Go  <br/> |4294967296  <br/> |
    |8 Go  <br/> |8589934592  <br/> |
   
3. Remplacez la `PstSizeLimitInBytes` valeur par la taille maximale souhaitée d’un fichier PST lorsque vous exportez les résultats de la recherche, puis enregistrez le fichier. 
    
4. Dans l’Explorateur Windows, cliquez ou double-cliquez sur le fichier .reg que vous avez créé dans les étapes précédentes.
    
5. Dans la fenêtre Access Control utilisateur, cliquez sur **Oui** pour permettre à l’Éditeur du Registre d’apporter la modification. 
    
6. Lorsque vous êtes invité à continuer, cliquez sur **Oui**.
    
    L’Éditeur du Registre affiche un message indiquant que le paramètre a été correctement ajouté au Registre.
    
7. Vous pouvez répéter les étapes 3 à 6 pour modifier la valeur du paramètre de  `PstSizeLimitInBytes` Registre. 
  
## <a name="frequently-asked-questions-about-changing-the-default-size-of-pst-files-when-you-export-ediscovery-search-results"></a>Forum aux questions sur la modification de la taille par défaut des fichiers PST lorsque vous exportez des résultats de recherche eDiscovery

 **Pourquoi la taille par défaut est-elle de 10 Go ?**
  
La taille par défaut de 10 Go était basée sur les commentaires des clients ; 10 Go est un bon équilibre entre la quantité optimale de contenu dans un seul PST et avec un risque minimal d’altération des fichiers.
  
 **Dois-je augmenter ou diminuer la taille par défaut des fichiers PST ?**
  
Les clients ont tendance à réduire la limite de taille afin que les résultats de la recherche s’adaptent aux supports amovibles qu’ils peuvent envoyer physiquement à d’autres emplacements de leur organisation. Nous vous déconseillons d’augmenter la taille par défaut, car les fichiers PST supérieurs à 10 Go peuvent rencontrer des problèmes d’altération.
  
 **Sur quel ordinateur dois-je procéder ?**
  
Vous devez modifier le paramètre de Registre sur n’importe quel ordinateur local sur lequel vous exécutez l’outil d’exportation eDiscovery.
  
 **Après avoir modifié ce paramètre, dois-je redémarrer l’ordinateur ?**
  
Non, vous n’avez pas besoin de redémarrer l’ordinateur. Toutefois, si l’outil d’exportation eDiscovery est en cours d’exécution, vous devez le fermer et le redémarrer après avoir modifié ce paramètre.
  
 **Une clé de Registre existante est-elle modifiée ou une nouvelle clé est-elle créée ?**
  
Une nouvelle clé de Registre est créée la première fois que vous exécutez le fichier .reg que vous avez créé dans cette procédure. Ensuite, le paramètre est modifié chaque fois que vous modifiez et réexécutez le fichier d’édition .reg.
