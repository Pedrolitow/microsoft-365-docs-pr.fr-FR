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
description: Découvrez comment sélectionner et exporter du contenu à partir d’un jeu à réviser Advanced eDiscovery pour les présentations ou les avis externes.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 0752c5272d078e75e3bdbfb9cf7af7e49c78e65c
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51581016"
---
# <a name="export-documents-from-a-review-set-in-advanced-ediscovery"></a>Exporter des documents à partir d’un jeu à réviser dans Advanced eDiscovery

L’exportation permet aux utilisateurs de personnaliser le contenu inclus dans le package de téléchargement lorsque vous exportez un document à partir d’un ensemble de révisions dans Advanced eDiscovery.

Pour exporter des documents à partir d’un jeu à réviser :

1. Dans le Centre de conformité Microsoft 365, ouvrez le  cas Advanced eDiscovery, sélectionnez l’onglet Ensembles de révision, puis sélectionnez le jeu à réviser à exporter.

2. Dans le jeu à réviser, cliquez sur **Exporter l’action.**  >  

   L’outil Export affiche la page de présentation avec les paramètres permettant de configurer l’exportation. Certaines options sont sélectionnées par défaut, mais vous pouvez les modifier. Consultez la section suivante pour obtenir des descriptions des options d’exportation que vous pouvez configurer.

   ![Options de configuration pour l’exportation d’éléments à partir d’un jeu à réviser](../media/bcfc72c7-4a01-4697-9e16-2965b7f04fdb.png)

3. Après avoir configuré l’exportation, cliquez sur **Exporter** pour démarrer le processus d’exportation. Selon l’option que vous avez sélectionnée dans la section **Options** de sortie, vous pouvez accéder aux fichiers d’exportation en téléchargement direct ou dans le compte de stockage Azure de votre organisation.

> [!NOTE]
> Les travaux d’exportation sont conservés pendant toute la durée de vie du cas. Toutefois, vous devez télécharger le contenu à partir d’une tâche d’exportation dans les 30 jours suivant la fin de la tâche d’exportation.

## <a name="export-options"></a>Options d’exportation

Utilisez les options suivantes pour configurer l’exportation.

- **Nom d’exportation**: nom de la tâche d’exportation.

- **Description**: champ de texte libre pour ajouter une description.

- **Exporter ces documents**

  - **Documents sélectionnés uniquement**: cette option exporte uniquement les documents actuellement sélectionnés.
  
  - **Tous les documents du jeu à réviser :** cette option exporte tous les documents du jeu à réviser.

- **Métadonnées**
  
  - **Fichier de chargement**: ce fichier contient les métadonnées de chaque fichier. Ce fichier peut généralement être ingéré par des outils eDiscovery tiers. Pour plus d’informations sur les champs inclus, voir Champs de métadonnées de document dans [Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).
  
  - **Balises**: lorsqu’elles sont sélectionnées, les informations de marquage sont incluses dans le fichier de chargement.

- **Content**
  
  - **Fichiers natifs**: cochez cette case pour inclure les fichiers natifs des documents dans le jeu à réviser. Si vous choisissez d’exporter des fichiers natifs, vous avez les options suivantes pour exporter des conversations de conversation.
  
  - **Options de conversation**

    - **Fichiers de conversation**: cette option exporte les conversations de conversation reconstruites. Ce format présente les conversations sous une forme semblable à ce que voient les utilisateurs dans l’application native.

    - **Messages de conversation** individuels : cette option exporte les fichiers de conversation d’origine tels qu’ils sont stockés dans Microsoft 365.

- **Options**

  - **Fichiers texte**: - Cette option inclut les versions texte extraites des fichiers natifs dans l’exportation.
  
  - **Remplacez les natifs rédigés** par des fichiers PDF convertis : si des fichiers PDF rédigés sont générés lors de la révision, ces fichiers sont disponibles à l’exportation. Vous pouvez choisir d’exporter uniquement les fichiers natifs qui ont été rédigés (en ne sélectionnant pas cette option) ou vous pouvez sélectionner cette option pour exporter les fichiers PDF qui contiennent les actions.

- **Options de sortie**: le contenu exporté peut être téléchargé directement via un navigateur web ou peut être envoyé à un compte de stockage Azure. Les deux premières options permettent le téléchargement direct.
  
  - Fichiers libres et **fichiers PST (la** messagerie électronique est ajoutée aux fichiers PST lorsque cela est possible) : les fichiers sont exportés dans un format qui ressemble à la structure de répertoires d’origine visible par les utilisateurs dans leurs applications natives.  Pour plus d’informations, voir la section Sur les fichiers libres et [la structure d’exportation PST.](#loose-files-and-pst-export-structure)
  
  - **Structure du répertoire condensé :** les fichiers sont exportés et inclus dans le téléchargement.
  
  - **Structure de répertoire condensée exportée** vers votre compte de stockage Azure : les fichiers sont exportés vers le compte de stockage Azure de votre organisation. Pour cette option, vous devez fournir l’URL du conteneur dans votre compte de stockage Azure vers qui exporter les fichiers. Vous devez également fournir le jeton de signature d’accès partagé (SAS) pour votre compte de stockage Azure. Pour plus d’informations, [voir Exporter des documents dans une révision définie sur un compte de stockage Azure.](download-export-jobs.md)

Les sections suivantes décrivent la structure des dossiers pour les fichiers libres et les options de structure de répertoire condensé.

### <a name="loose-files-and-pst-export-structure"></a>Fichiers libres et structure d’exportation PST

Si vous sélectionnez cette option d’exportation, le contenu exporté est organisé dans la structure suivante :

- Dossier racine : ce dossier dans le dossier nommé ExportName.zip
  
  - Export_load_file.csv : fichier de métadonnées.
  
  - Summary.csv : fichier récapitulatif qui contient également des statistiques d’exportation.
  
  - Exchange : ce dossier contient tout le contenu d’Exchange au format de fichier natif. Les fichiers natifs sont remplacés par des fichiers PDF rédigés si vous avez sélectionné l’option Remplacer les natifs rédigés par des fichiers **pdf convertis.**
  
  - SharePoint : ce dossier contient tout le contenu natif de SharePoint dans un format de fichier natif. Les fichiers natifs sont remplacés par des fichiers PDF rédigés si vous avez sélectionné l’option Remplacer les natifs rédigés par des fichiers **pdf convertis.**

### <a name="condensed-directory-structure"></a>Structure du répertoire condensé

- Dossier racine : ce dossier est nommé ExportName.zip
  
  - Export_load_file.csv : fichier de métadonnées.
  
  - Summary.txt : fichier récapitulatif qui contient également des statistiques d’exportation.
  
  - NativeFiles : ce dossier contient tous les fichiers natifs qui ont été exportés. Si vous exportez des fichiers PDF rédigés, ils ne sont pas placés dans des fichiers PST. Au lieu de cela, ils sont ajoutés à un dossier séparé.
  
  - Error_files : ce dossier contient les fichiers d’erreur suivants, s’ils sont inclus dans l’exportation :

    - ExtractionError : fichier CSV qui contient toutes les métadonnées disponibles des fichiers qui n’ont pas été correctement extraits des fichiers parents.

    - ProcessingError : ce fichier contient une liste de documents contenant des erreurs de traitement. Ce contenu est au niveau de l’élément, ce qui signifie que si une pièce jointe a entraîné une erreur de traitement, le message électronique qui contient la pièce jointe est inclus dans ce dossier.
  
  - Extracted_text_files : ce dossier contient tous les fichiers texte extraits qui ont été générés lors du traitement.
