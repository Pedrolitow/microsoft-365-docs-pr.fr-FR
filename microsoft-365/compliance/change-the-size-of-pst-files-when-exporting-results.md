---
title: Modifier la taille des fichiers PST lors de l’exportation des résultats de recherche eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 10/12/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid: MOE150
ms.assetid: 04e9de2d-765b-457b-a98a-d0f60bfb13f2
description: Vous pouvez modifier la taille par défaut des fichiers PST téléchargés sur votre ordinateur lorsque vous exportez les résultats de recherche de découverte électronique.
ms.openlocfilehash: f5fde9bbb37f6e22c49049c892a1b69b07d15bef
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43636322"
---
# <a name="change-the-size-of-pst-files-when-exporting-ediscovery-search-results"></a>Modifier la taille des fichiers PST lors de l’exportation des résultats de recherche eDiscovery

Lorsque vous utilisez l’outil d’exportation de découverte électronique pour exporter les résultats de la messagerie électronique d’une recherche de découverte électronique à partir des différents outils eDiscovery de Microsoft, la taille par défaut d’un fichier PST pouvant être exporté est de 10 Go. Si vous souhaitez modifier cette taille par défaut, vous pouvez modifier le Registre Windows sur l’ordinateur que vous utilisez pour exporter les résultats de la recherche. L’une des raisons pour y parvenir est qu’un fichier PST peut tenir sur un support amovible, un DVD, un disque compact ou un lecteur USB. 
  
> [!NOTE]
> L’outil d’exportation de découverte électronique est utilisé pour exporter les résultats de la recherche lors de l’utilisation de l’outil de recherche de contenu dans le centre de sécurité & conformité, la découverte électronique inaltérable dans Exchange Online et le centre eDiscovery dans SharePoint Online.
  
## <a name="create-a-registry-setting-to-change-the-size-of-pst-files-when-you-export-ediscovery-search-results"></a>Créer un paramètre de Registre pour modifier la taille des fichiers PST lors de l’exportation des résultats de recherche de découverte électronique

Effectuez la procédure suivante sur l’ordinateur que vous allez utiliser pour exporter les résultats d’une recherche de découverte électronique.
  
1. Fermez l’outil d’exportation de découverte électronique s’il est ouvert. 
    
2. Enregistrez le texte suivant dans un fichier de Registre Windows à l’aide d’un suffixe de nom de fichier. reg ; par exemple, PstExportSize. reg. 
    
    ```text
    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool]
    "PstSizeLimitInBytes"="1073741824"
    ```

    Dans l’exemple ci-dessus `PstSizeLimitInBytes` , la valeur est définie sur 1 073 741 824 octets ou environ 1 Go. Voici d’autres exemples de valeurs pour le `PstSizeLimitInBytes` paramètre. 
    
    |**Taille en Go (env.)**|**Taille en octets**|
    |:-----|:-----|
    |0,7 GO (700 MO)  <br/> |751619277  <br/> |
    |2 Go  <br/> |2147483648  <br/> |
    |4 Go  <br/> |4294967296  <br/> |
    |8 Go  <br/> |8589934592  <br/> |
   
3. Remplacez la `PstSizeLimitInBytes` valeur par la taille maximale de fichier PST souhaitée lorsque vous exportez les résultats de la recherche, puis enregistrez le fichier. 
    
4. Dans l’Explorateur Windows, cliquez ou double-cliquez sur le fichier. reg que vous avez créé au cours des étapes précédentes.
    
5. Dans la fenêtre contrôle d’accès des utilisateurs, cliquez sur **Oui** pour permettre à l’éditeur du registre de procéder à la modification. 
    
6. Lorsque vous êtes invité à continuer, cliquez sur **Oui**.
    
    L’éditeur du Registre affiche un message indiquant que le paramètre a été ajouté avec succès au registre.
    
7. Vous pouvez répéter les étapes 3-6 pour modifier la valeur du `PstSizeLimitInBytes` paramètre de registre. 
  
## <a name="frequently-asked-questions-about-changing-the-default-size-of-pst-files-when-you-export-ediscovery-search-results"></a>Forum aux questions sur la modification de la taille par défaut des fichiers PST lors de l’exportation des résultats de recherche de découverte électronique

 **Pourquoi la taille par défaut est-elle de 10 Go ?**
  
La taille par défaut de 10 Go était basée sur les commentaires des clients ; 10 Go constitue un bon équilibre entre la quantité optimale de contenu dans un seul fichier PST et une probabilité minimale d’endommagement des fichiers.
  
 **Dois-je augmenter ou réduire la taille par défaut des fichiers PST ?**
  
Les clients ont tendance à réduire la limite de taille afin que les résultats de la recherche tiennent sur des supports amovibles qu’ils peuvent expédier physiquement à d’autres emplacements de leur organisation. Il n’est pas recommandé d’augmenter la taille par défaut, car les fichiers PST de plus de 10 Go peuvent présenter des problèmes d’endommagement.
  
 **Sur quel ordinateur dois-je effectuer cette opération ?**
  
Vous devez modifier le paramètre de Registre sur n’importe quel ordinateur local sur lequel vous exécutez l’outil d’exportation de découverte électronique.
  
 **Après avoir modifié ce paramètre, dois-je redémarrer l’ordinateur ?**
  
Non, vous n’avez pas besoin de redémarrer l’ordinateur. Toutefois, si l’outil d’exportation de découverte électronique est en cours d’exécution, vous devez le fermer et le redémarrer une fois que vous avez modifié ce paramètre.
  
 **Une clé de Registre existante est-elle modifiée ou une nouvelle clé est-elle créée ?**
  
Une nouvelle clé de Registre est créée lors de la première exécution du fichier. reg que vous avez créé au cours de cette procédure. Le paramètre est ensuite modifié chaque fois que vous modifiez et réexécutez le fichier de modification. reg.
