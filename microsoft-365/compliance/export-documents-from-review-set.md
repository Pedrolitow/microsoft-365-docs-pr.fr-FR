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
description: Découvrez comment sélectionner et exporter du contenu à partir d’un jeu à réviser pour des présentations ou des avis externes.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: b3be21d4c90c861c83acf612e9aadc373189f7ba
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285360"
---
# <a name="export-documents-from-a-review-set-in-advanced-ediscovery"></a>Exporter des documents à partir d’un jeu à réviser dans Advanced eDiscovery

L’exportation permet aux utilisateurs de personnaliser le contenu inclus dans le package de téléchargement. L’outil d’exportation fournit une page de configuration avec les paramètres suivants :

![Options d’exportation d’éléments à partir d’un jeu à réviser](../media/bcfc72c7-4a01-4697-9e16-2965b7f04fdb.png)

## <a name="export-options"></a>Options d’exportation

- Nom d’exportation : nom de la tâche d’exportation.

- Description : champ de texte libre pour ajouter une description.

- Exporte les documents ci-après :

  - Documents sélectionnés uniquement : exporte uniquement les documents actuellement sélectionnés.
  
  - Tous les documents du jeu à réviser : exporte tous les documents du jeu à réviser

- Métadonnées
  
  - Charger un fichier : ce fichier contient les métadonnées de chaque fichier. voir [Champs de métadonnées de document dans Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md) pour plus d’informations sur les champs inclus. Ce fichier peut généralement être ingéré par des outils eDiscovery tiers.
  
  - Balises : lorsqu’elles sont sélectionnées, les informations de marquage sont incluses dans le fichier de chargement.

- Contenu
  
  - Fichiers natifs : cochez cette case pour inclure les fichiers natifs.
  
  - Options de conversation
    
    - Fichiers de conversation : exporter les messages de conversation reconstruits. Ce format présente les conversations sous une forme semblable à ce que voient les utilisateurs dans l’application native.
    
    - Messages de conversation individuels : exportez les fichiers de conversation d’origine tels qu’ils sont stockés dans Microsoft 365.

- Options

  - Fichiers texte : inclure les versions texte extraites des fichiers natifs.
  
  - Remplacez les natifs rédigés par des fichiers PDF convertis : si des fichiers PDF rédigés sont générés au cours de la révision, ces fichiers peuvent être exportés. Vous pouvez choisir d’exporter uniquement les fichiers natifs qui ont été rédigés (en ne sélectionnant pas cette option) ou vous pouvez sélectionner cette option pour exporter les fichiers PDF qui contiennent les actions.

- Options de sortie (le contenu exporté peut être téléchargé directement via un navigateur web ou peut être envoyé à un compte de stockage Azure. Les deux premières options activent le téléchargement direct.)
  
  - Fichiers libres et fichiers PST (le courrier électronique est ajouté aux fichiers PST lorsque cela est possible) : les fichiers sont exportés dans un format qui ressemble à la structure de répertoires d’origine visible par les utilisateurs dans leurs applications natives.  Pour plus d’informations, voir la section Sur les fichiers libres et [la structure d’exportation PST.](#loose-files-and-pst-export-structure)
  
  - Structure du répertoire condensé : les fichiers sont exportés et inclus dans le téléchargement.
  
  - Structure de répertoire condensée exportée vers votre compte de stockage Azure : les fichiers sont exportés vers l’accès au stockage Azure de votre organisation.

## <a name="loose-files-and-pst-export-structure"></a>Fichiers libres et structure d’exportation PST

Si vous sélectionnez cette option d’exportation, le contenu exporté est organisé dans la structure suivante :

- Dossier racine : ce dossier dans le dossier nommé ExportName.zip
  
  - Export_load_file.csv - Fichier de métadonnées.
  
  - Summary.csv : fichier récapitulatif qui contient également des statistiques d’exportation.
  
  - Exchange : ce dossier contient tout le contenu d’Exchange au format de fichier natif. Les fichiers natifs sont remplacés par des fichiers PDF rédigés si vous avez sélectionné l’option Remplacer les natifs rédigés par des fichiers **pdf convertis.**
  
  - SharePoint = Ce dossier contient tout le contenu natif de SharePoint dans un format de fichier natif. Les fichiers natifs sont remplacés par des fichiers PDF rédigés si vous avez sélectionné l’option Remplacer les natifs rédigés par des fichiers **PDF convertis.**

## <a name="condensed-directory-structure"></a>Structure du répertoire condensé

- Dossier racine : ce dossier est nommé ExportName.zip
  
  - Export_load_file.csv - Fichier de métadonnées.
  
  - Summary.txt : fichier récapitulatif qui contient également des statistiques d’exportation.
  
  - Input_or_native_files - Ce dossier contient tous les fichiers natifs qui ont été exportés. Si vous exportez des fichiers PDF rédigés, ils ne sont pas placés dans des fichiers PST. Au lieu de cela, ils sont ajoutés à un dossier séparé.
  
  - Error_files - Ce dossier contient les fichiers d’erreur suivants, s’ils sont inclus dans l’exportation :
    
    - ExtractionError. Un fichier CSV qui contient toutes les métadonnées disponibles des fichiers qui n’ont pas été correctement extraits des fichiers parents.
    
    - ProcessingError : ce fichier contient une liste de documents avec des erreurs de traitement. Ce contenu est au niveau de l’élément, ce qui signifie que si une pièce jointe a entraîné une erreur de traitement, le message électronique qui contient la pièce jointe est inclus dans ce dossier.
  
  - Extracted_text_files - Ce dossier contient tous les fichiers texte extraits qui ont été générés lors du traitement.

> [!NOTE]
> Les travaux d’exportation sont conservés pendant la durée de vie du cas et peuvent être téléchargés tant que le cas n’est pas supprimé.
