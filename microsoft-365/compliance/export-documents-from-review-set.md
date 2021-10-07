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
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment sélectionner et exporter du contenu à partir d’un ensemble Advanced eDiscovery révision pour les présentations ou les avis externes.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: dba9708bfda6d1b98a2861615e56518067822100
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60175166"
---
# <a name="export-documents-from-a-review-set-in-advanced-ediscovery"></a>Exporter des documents à partir d’un groupe de révision dans Advanced eDiscovery

L’exportation permet aux utilisateurs de personnaliser le contenu inclus dans le package de téléchargement lorsque vous exportez le document à partir d’un ensemble de révisions dans Advanced eDiscovery.

Exporter les documents d’un jeu à réviser :

1. Dans la Centre de conformité Microsoft 365, ouvrez le cas Advanced eDiscovery,  sélectionnez l’onglet Ensembles de révision, puis sélectionnez le jeu à réviser à exporter.

2. Dans le jeu à réviser, cliquez sur **Exporter l’action.**  >  

   L’outil Exporter affiche la page de menu volant avec les paramètres pour configurer l’exportation. Certaines options sont sélectionnées par défaut, mais vous pouvez les modifier. Consultez la section suivante pour obtenir des descriptions des options d’exportation que vous pouvez configurer.

   ![Options de configuration pour l’exportation d’éléments à partir d’un jeu à réviser.](../media/bcfc72c7-4a01-4697-9e16-2965b7f04fdb.png)

3. Après avoir configuré l’exportation, cliquez sur **Exporter** pour démarrer le processus d’exportation. Selon l’option que vous avez sélectionnée dans la section **Options** de sortie, vous pouvez accéder aux fichiers d’exportation en téléchargement direct ou dans le compte stockage Azure de votre organisation.

> [!NOTE]
> Les travaux d’exportation sont conservés pendant toute la durée de vie du cas. Toutefois, vous devez télécharger le contenu à partir d’une tâche d’exportation dans les 30 jours suivant la fin de la tâche d’exportation.

## <a name="export-options"></a>Options d’exportation

Utilisez les options suivantes pour configurer l’exportation. Toutes les options ne sont pas autorisées pour certaines options de sortie, notamment l’exportation de fichiers texte et de fichiers pdf expurgées qui ne sont pas autorisées lors de l’exportation au format PST.

- **Nom d’exportation**: nom de la tâche d’exportation. Il sera utilisé pour nommer les fichiers ZIP qui seront téléchargés.

- **Description**: champ de texte libre pour ajouter une description.

- **Exporter ces documents**

  - Documents sélectionnés uniquement : cette option exporte uniquement les documents actuellement sélectionnés. Cette option est disponible uniquement lorsque les éléments sont sélectionnés dans un jeu à réviser.
  
  - Tous les documents filtrés : cette option exporte les documents dans un filtre actif. Cette option est disponible uniquement lorsqu’un filtre est appliqué au jeu à réviser.
  
  - Tous les documents du jeu à réviser : cette option exporte tous les documents du jeu à réviser.

- **Options de** sortie : le contenu exporté peut être téléchargé directement via un navigateur web ou peut être envoyé à un stockage Azure client. Les deux premières options permettent le téléchargement direct.
  
  - Rapports uniquement : seuls le fichier récapitulatif et le fichier de chargement sont créés.
  
  - Fichiers libres et fichiers PST (le courrier électronique est ajouté aux fichiers PST lorsque cela est possible) : les fichiers sont exportés dans un format qui ressemble à la structure de répertoires d’origine visible par les utilisateurs dans leurs applications natives.  Pour plus d’informations, voir la section Sur les fichiers libres et [la structure d’exportation PST.](#loose-files-and-pst-export-structure)
  
  - Structure du répertoire condensé : les fichiers sont exportés et inclus dans le téléchargement.
  
  - Structure de répertoire condensée exportée vers votre compte stockage Azure : les fichiers sont exportés vers le compte stockage Azure de votre organisation. Pour cette option, vous devez fournir l’URL du conteneur dans votre compte stockage Azure pour exporter les fichiers. Vous devez également fournir le jeton de signature d’accès partagé (SAS) pour stockage Azure compte. Pour plus d’informations, [voir Exporter des documents dans une révision définie sur un compte stockage Azure.](download-export-jobs.md)

- **Include**
  
  - Balises : lorsqu’elles sont sélectionnées, les informations de marquage sont incluses dans le fichier de chargement.
  
  - Fichiers texte : cette option inclut les versions texte extraites des fichiers natifs dans l’exportation.
  
  - Remplacez les natifs rédigés par des fichiers PDF convertis : si des fichiers PDF rédigés sont générés au cours de la révision, ces fichiers peuvent être exportés. Vous pouvez choisir d’exporter uniquement les fichiers natifs qui ont été rédigés (en ne sélectionnant pas cette option) ou vous pouvez sélectionner cette option pour exporter les fichiers PDF qui contiennent les actions.

  - Fichiers PDF de conversation au lieu de messages de conversation individuels : cochez cette case pour exporter les conversations dans un fichier PDF. Tous les messages de conversation de la même conversation sont exportés dans le même fichier PDF. Si vous ne cochez pas cette case, chaque message unique d’une conversation est exporté en tant qu’élément autonome. Le fichier est exporté au même format que dans la boîte aux lettres. Pour une conversation spécifique, vous recevez plusieurs fichiers .msg.

Les sections suivantes décrivent la structure des dossiers pour les fichiers libres et les options de structure de répertoire condensé. Les exportations sont partitionées dans des fichiers ZIP avec une taille maximale de contenu non compressé de 75 Go. Si la taille de l’exportation est inférieure à 75 Go, l’exportation se compose d’un fichier récapitulatif et d’un fichier ZIP unique. Pour les exportations dont la taille est supérieure à 75 Go de données non compressées, plusieurs fichiers ZIP sont créés. Une fois téléchargés, les fichiers ZIP peuvent être décompressés dans un seul emplacement pour recréer l’exportation complète.

### <a name="loose-files-and-pst-export-structure"></a>Fichiers libres et structure d’exportation PST

Si vous sélectionnez cette option d’exportation, le contenu exporté est organisé dans la structure suivante :

- Summary.csv : inclut un résumé du contenu exporté à partir du jeu à réviser

- Dossier racine : ce dossier nommé [Nom d’exportation] x de z.zip est répété pour chaque partition de fichier ZIP.
  
  - Export_load_file_x de z.csv : le fichier de métadonnées.
  
  - Avertissements et erreurs x de z.csv : ce fichier inclut des informations sur les erreurs rencontrées lors de la tentative d’exportation à partir du jeu à réviser.
  
  - Exchange : ce dossier contient tout le contenu des Exchange stockés dans des fichiers PST. Les fichiers PDF rédigés ne peuvent pas être inclus dans cette option. Si une pièce jointe est sélectionnée dans le jeu à réviser, le courrier électronique parent est exporté avec la pièce jointe jointe.
  
  - SharePoint : ce dossier contient tout le contenu natif de SharePoint dans un format de fichier natif. Les fichiers PDF rédigés ne peuvent pas être inclus dans cette option.

### <a name="condensed-directory-structure"></a>Structure du répertoire condensé

- Summary.csv : inclut un résumé du contenu exporté à partir du jeu à réviser

- Dossier racine : ce dossier nommé [Nom d’exportation] x de z.zip est répété pour chaque partition de fichier ZIP.
  
  - Export_load_file_x de z.csv : le fichier de métadonnées et inclut également l’emplacement de chaque fichier stocké dans le fichier ZIP.
  
  - Avertissements et erreurs x de z.csv : ce fichier inclut des informations sur les erreurs rencontrées lors de la tentative d’exportation à partir du jeu à réviser.

  - NativeFiles : ce dossier contient tous les fichiers natifs qui ont été exportés. Les fichiers natifs sont remplacés par des fichiers PDF rédigés si vous avez sélectionné l’option Remplacer les natifs rédigés par des fichiers *pdf convertis.*
  
  - Error_files : ce dossier contient des fichiers dont l’extraction ou une autre erreur de traitement s’est produite. Les fichiers sont placés dans des dossiers distincts, ExtractionError ou ProcessingError. Ces fichiers sont répertoriés dans le fichier de chargement.

  - Extracted_text_files : ce dossier contient tous les fichiers texte extraits qui ont été générés lors du traitement.

### <a name="condensed-directory-structure-exported-to-your-azure-storage-account"></a>Structure de répertoire condensé exportée vers votre compte stockage Azure client

Cette option utilise la même structure générale que la *structure* du répertoire condensé, mais le contenu n’est pas compressé et les données sont enregistrées dans stockage Azure compte. Cette option est généralement utilisée lorsque vous travaillez avec un fournisseur eDiscovery tiers. Pour plus d’informations sur l’utilisation de cette option, voir Exporter des documents dans une révision [définie sur un compte stockage Azure.](download-export-jobs.md)
