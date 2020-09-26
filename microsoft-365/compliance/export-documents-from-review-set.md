---
title: Exporter des documents d’un jeu à réviser
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment sélectionner et exporter du contenu à partir d’un jeu de révision pour des présentations ou des révisions externes.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: b3be21d4c90c861c83acf612e9aadc373189f7ba
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285360"
---
# <a name="export-documents-from-a-review-set-in-advanced-ediscovery"></a>Exporter des documents à partir d’un jeu de révision dans Advanced eDiscovery

Exporter permet aux utilisateurs de personnaliser le contenu qui est inclus dans le package de téléchargement. L’outil d’exportation fournit une page de configuration avec les paramètres suivants :

![Options d’exportation des éléments à partir d’un ensemble de révision](../media/bcfc72c7-4a01-4697-9e16-2965b7f04fdb.png)

## <a name="export-options"></a>Options d’exportation

- Nom de l’exportation : nom de la tâche d’exportation.

- Description : champ de texte libre vous permettant d’ajouter une description.

- Exportez les documents suivants :

  - Documents sélectionnés uniquement : exporte uniquement les documents actuellement sélectionnés.
  
  - Tous les documents de l’ensemble de révision : exporte tous les documents dans l’ensemble de révision.

- Métadonnées
  
  - Charger un fichier : ce fichier contient des métadonnées pour chaque fichier. Pour plus d’informations sur les champs inclus, voir [champs de métadonnées de document dans Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md) . Ce fichier peut généralement être ingéré par des outils eDiscovery tiers.
  
  - Tags : lorsque cette option est sélectionnée, les informations de marquage sont incluses dans le fichier de chargement.

- Contenu
  
  - Fichiers natifs : activez cette case à cocher pour inclure les fichiers natifs.
  
  - Options de conversation
    
    - Fichiers de conversation : exporter les messages de conversation reconstruits. Ce format présente les conversations sous une forme semblable à celle que voient les utilisateurs dans l’application native.
    
    - Messages de conversation individuels : exportez les fichiers de conversation d’origine au fur et à mesure qu’ils sont stockés dans Microsoft 365.

- Options

  - Fichiers texte : inclut les versions texte extraites des fichiers natifs.
  
  - Remplacer les formats natifs biffés par des fichiers PDF convertis : si des fichiers. PDF biffés sont générés lors de la révision, ces fichiers sont disponibles pour l’exportation. Vous pouvez choisir d’exporter uniquement les fichiers natifs qui ont été rédigés (sans sélectionner cette option) ou vous pouvez sélectionner cette option pour exporter les fichiers PDF qui contiennent la Redactions réelle.

- Options de sortie (le contenu exporté est disponible pour téléchargement directement par le biais d’un navigateur Web ou peut être envoyé à un compte de stockage Azure. Les deux premières options activent le téléchargement direct.)
  
  - Fichiers libres et fichiers PST (le courrier électronique est ajouté aux fichiers PST dans la mesure du possible) : les fichiers sont exportés dans un format qui ressemble à la structure de répertoires d’origine vue par les utilisateurs dans leurs applications natives.  Pour plus d’informations, reportez-vous à la section [fichiers libres et structure d’exportation PST](#loose-files-and-pst-export-structure) .
  
  - Structure d’annuaire condensé : les fichiers sont exportés et inclus dans le téléchargement.
  
  - La structure de répertoire condensé exportée vers votre compte de stockage Azure-les fichiers sont exportés vers le accouunt de stockage Azure de votre organisation.

## <a name="loose-files-and-pst-export-structure"></a>Fichiers libres et structure d’exportation PST

Si vous sélectionnez cette option d’exportation, le contenu exporté est organisé selon la structure suivante :

- Dossier racine : ce dossier dans nommé ExportName.zip
  
  - Export_load_file.csv-fichier de métadonnées.
  
  - Summary.csv-fichier de résumé qui contient également des statistiques d’exportation.
  
  - Exchange : ce dossier contient tout le contenu d’Exchange au format de fichier natif. Les fichiers natifs sont remplacés par des fichiers PDF biffés si vous avez sélectionné l’option remplacer les fichiers **natifs biffés avec des fichiers PDF convertis** .
  
  - SharePoint = ce dossier contient tout le contenu natif de SharePoint dans un format de fichier natif. Les fichiers natifs sont remplacés par des fichiers PDF biffés si vous avez sélectionné l’option remplacer les fichiers **natifs biffés avec des fichiers PDF convertis** .

## <a name="condensed-directory-structure"></a>Structure de répertoire condensé

- Dossier racine : ce dossier est nommé ExportName.zip
  
  - Export_load_file.csv-fichier de métadonnées.
  
  - Summary.txt-fichier de résumé qui contient également des statistiques d’exportation.
  
  - Input_or_native_files-ce dossier contient tous les fichiers natifs qui ont été exportés. Si vous exportez des fichiers PDF biffés, ils ne sont pas placés dans des fichiers PST. Au lieu de cela, ils sont ajoutés à un dossier séparé.
  
  - Error_files-ce dossier contient les fichiers d’erreurs suivants, s’ils sont inclus dans l’exportation :
    
    - ExtractionError. Fichier CSV qui contient les métadonnées de fichiers disponibles qui n’ont pas été correctement extraites des fichiers parents.
    
    - ProcessingError : ce fichier contient la liste des documents contenant des erreurs de traitement. Ce contenu est au niveau de l’élément, ce qui signifie que si une pièce jointe a généré une erreur de traitement, le message électronique qui contient la pièce jointe est inclus dans ce dossier.
  
  - Extracted_text_files-ce dossier contient tous les fichiers texte extraits qui ont été générés lors du traitement.

> [!NOTE]
> Les travaux d’exportation sont conservés pendant toute la durée de la demande de devis et peuvent être téléchargés tant que le cas n’est pas supprimé.
