---
title: Désactiver les rapports lorsque vous exportez les résultats de recherche de contenu
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 12/30/2016
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: c9b0ff0c-282b-4a44-b43f-cfc5b96557f9
ms.custom:
- seo-marvel-apr2020
description: Modifiez Windows registre local pour désactiver les rapports lorsque vous exportez les résultats d’une recherche de contenu à partir du Centre de conformité Microsoft 365.
ms.openlocfilehash: efe9ea768b68524dbfda003796a10d60453862bc
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59183695"
---
# <a name="disable-reports-when-you-export-content-search-results"></a>Désactiver les rapports lorsque vous exportez les résultats de recherche de contenu

Lorsque vous utilisez l’outil Exportation de découverte électronique pour exporter les résultats d’une recherche de contenu dans le Centre de conformité Microsoft 365, l’outil crée et exporte automatiquement deux rapports qui contiennent des informations supplémentaires sur le contenu exporté. Ces rapports sont le fichier Results.csv et le fichier Manifest.xml (consultez la section Des [questions](#frequently-asked-questions-about-disabling-export-reports) fréquemment posées sur la désactivation des rapports d’exportation dans cette rubrique pour obtenir une description détaillée de ces rapports). Étant donné que ces fichiers peuvent être très importants, vous pouvez accélérer le temps de téléchargement et économiser de l’espace disque en empêchant l’exportation de ces fichiers. Pour ce faire, vous pouvez modifier Windows registre sur l’ordinateur que vous utilisez pour exporter les résultats de la recherche. Si vous souhaitez inclure les rapports ultérieurement, vous pouvez modifier le paramètre de Registre. 
  
## <a name="create-registry-settings-to-disable-the-export-reports"></a>Créer des paramètres de Registre pour désactiver les rapports d’exportation

Effectuez la procédure suivante sur l’ordinateur que vous utiliserez pour exporter les résultats d’une recherche de contenu.
  
1. Fermez l’outil d’exportation eDiscovery s’il est ouvert.
    
2. Effectuez l’une des étapes suivantes ou les deux, en fonction du rapport d’exportation que vous souhaitez désactiver.
    
    - **Results.csv**
    
      Enregistrez le texte suivant dans un Windows registre en utilisant le suffixe de nom de fichier .reg ; par exemple, DisableResultsCsv.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d False 
      ```

    - **Manifest.xml**
    
      Enregistrez le texte suivant dans un Windows registre en utilisant le suffixe de nom de fichier .reg ; par exemple, DisableManifestXml.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d False 
      ```

3. Dans Windows Explorer, cliquez ou double-cliquez sur le fichier .reg que vous avez créé aux étapes précédentes.
    
4. Dans la fenêtre Contrôle d’accès utilisateur, cliquez sur **Oui** pour laisser l’Éditeur du Registre effectuer la modification. 
    
5. Lorsque vous y sont invités, cliquez sur **Oui.**
    
    L’Éditeur du Registre affiche un message vous disant que le paramètre a été correctement ajouté au Registre.
  
## <a name="edit-registry-settings-to-re-enable-the-export-reports"></a>Modifier les paramètres du Registre pour ré-activer les rapports d’exportation

Si vous avez désactivé les rapports Results.csv et Manifest.xml en créant les fichiers .reg dans la procédure précédente, vous pouvez modifier ces fichiers pour réactiver un rapport afin qu’il soit exporté avec les résultats de la recherche. Là encore, effectuez la procédure suivante sur l’ordinateur que vous utiliserez pour exporter les résultats d’une recherche de contenu.
  
1. Fermez l’outil d’exportation eDiscovery s’il est ouvert.
    
2. Modifiez l’un ou les deux fichiers .reg edit que vous avez créés dans la procédure précédente.
    
    - **Results.csv**
    
        Ouvrez le fichier DisableResultsCsv.reg dans Bloc-notes, modifiez la valeur et `False` `True` enregistrez le fichier. Par exemple, après avoir modifié le fichier, il ressemble à ceci :
    
        ```text
        Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d True
        ```

    - **Manifest.xml**
    
        Ouvrez le fichier DisableManifestXml.reg dans Bloc-notes, modifiez la valeur et `False` `True` enregistrez le fichier. Par exemple, après avoir modifié le fichier, il ressemble à ceci :
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d True
      ```

3. Dans Windows Explorer, cliquez ou double-cliquez sur un fichier .reg que vous avez modifié à l’étape précédente.
    
4. Dans la fenêtre Contrôle d’accès utilisateur, cliquez sur **Oui** pour laisser l’Éditeur du Registre effectuer la modification. 
    
5. Lorsque vous y sont invités, cliquez sur **Oui.**
    
    L’Éditeur du Registre affiche un message vous disant que le paramètre a été correctement ajouté au Registre.
  
## <a name="frequently-asked-questions-about-disabling-export-reports"></a>Questions fréquemment posées sur la désactivation des rapports d’exportation

 **Quels sont les rapports Results.csv et Manifest.xml'informations ?**
  
Les Results.csv et Manifest.xml contiennent des informations supplémentaires sur le contenu exporté.
  
- **Results.csv** Un Excel qui contient des informations sur chaque élément téléchargé en tant que résultat de recherche. Pour le courrier électronique, le journal des résultats contient des informations sur chaque message, y compris : 
    
  - l’emplacement du message dans la boîte aux lettres source (notamment si le message est dans la boîte aux lettres principale ou d’archivage) ;
    
  - la date à laquelle le message a été envoyé ou reçu ;
    
  - l’objet du message ;
    
  - l’expéditeur et les destinataires du message.
    
  - Indique si le message est un message en double si vous avez activé la déplication lors de l’exportation des résultats de la recherche. Les messages en double auront une valeur dans la **colonne Parent ItemId** qui identifie le message en tant que doublon. La valeur de la **colonne Parent ItemId** est identique à la valeur de la colonne **Item DocumentId** du message exporté. 
    
    Pour les documents provenant SharePoint sites OneDrive Entreprise sites web, le journal des résultats contient des informations sur chaque document, notamment :
    
  - l’URL du document ;
    
  - l’URL de la collection de sites qui héberge le document ;
    
  - la date à laquelle le document a été modifié pour la dernière fois ;
    
  - le nom du document (qui se trouve dans la colonne Objet du journal des résultats).
    
- **Manifest.xml** Fichier manifeste (au format XML) qui contient des informations sur chaque élément inclus dans les résultats de la recherche. Les informations de ce rapport sont les mêmes que le rapport Results.csv, mais elles sont au format spécifié par le modèle de référence de découverte électronique (EDRM). Pour plus d’informations sur EDRM, voir [https://www.edrm.net](https://www.edrm.net) .
    
 **Quand désactiver l’exportation de ces rapports ?**
  
Cela dépend de vos besoins spécifiques. De nombreuses organisations n’ont pas besoin d’informations supplémentaires sur les résultats de la recherche et n’ont pas besoin de ces rapports.
  
 **Sur quel ordinateur dois-je faire cela ?**
  
 Vous devez modifier le paramètre de Registre sur n’importe quel ordinateur local sur qui vous exécutez l’outil d’exportation de découverte électronique. 
  
 **Après avoir changé ce paramètre, dois-je redémarrer l’ordinateur ?**
  
Non, vous n’avez pas besoin de redémarrer l’ordinateur. Toutefois, si l’outil d’exportation eDiscovery est en cours d’exécution, vous devez le fermer, puis le redémarrer après avoir changé le paramètre de Registre.
  
 **Une clé de Registre existante est-elle modifiée ou une nouvelle clé est-elle créée ?**
  
Une nouvelle clé de Registre est créée la première fois que vous exécutez le fichier .reg que vous avez créé dans la procédure de cette rubrique. Ensuite, le paramètre est modifié chaque fois que vous modifiez et ré-exécutez le fichier .reg edit.
