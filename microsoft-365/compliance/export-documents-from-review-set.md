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
description: ''
ms.openlocfilehash: b6f467f938ce14aacb9553b11d51dc63431ab409
ms.sourcegitcommit: 570ad1c7c334476ecec00dc355dfe52e8c2bb87b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "41862074"
---
# <a name="export-documents-from-a-review-set"></a>Exporter des documents d’un jeu à réviser

Vous pouvez exporter du contenu pour une présentation ou une révision externe à partir d’un ensemble de réexamens à l’aide de l’une des méthodes suivantes :

- [Télécharger des documents](#download-documents-from-a-review-set)
 
- [Exporter des documents](#export-documents-from-a-review-set)

## <a name="download-documents-from-a-review-set"></a>Télécharger des documents à partir d’un jeu de révision

Le téléchargement offre un moyen simple de télécharger du contenu à partir d’un jeu de révision au format natif. Il exploite les fonctionnalités de transfert de données du navigateur, de sorte qu’une invite de navigateur s’affiche une fois que le téléchargement est prêt. Les fichiers téléchargés à l’aide de cette méthode seront Zippés dans un fichier conteneur et seront des fichiers au niveau de l’élément. Cela signifie que si vous sélectionnez une pièce jointe, vous recevrez automatiquement le courrier électronique avec la pièce jointe incluse. De même, si vous sélectionnez une feuille de calcul Excel incorporée dans un document Word, vous recevrez le document Word avec la feuille de calcul Excel incorporée. Les éléments téléchargés conservent la dernière date de modification pouvant être affichée en tant que propriété de fichier.

Pour télécharger du contenu à partir d’un jeu de révision, commencez par sélectionner les fichiers que vous souhaitez télécharger, puis sélectionnez « Télécharger » sous le menu actions.

![Capture d’écran d’une description d’ordinateur générée automatiquement](media/eDiscoDownload.png)

## <a name="export-documents-from-a-review-set"></a>Exporter des documents d’un jeu à réviser

Exporter permet aux utilisateurs de personnaliser le contenu qui est inclus dans le package de téléchargement. Il fournit une page de configuration avec les paramètres suivants :

### <a name="metadata-file"></a>Fichier de métadonnées

Cela peut être considéré comme votre « fichier de chargement » qui contient les métadonnées associées aux fichiers que vous exportez. Pour obtenir la liste des champs exportés disponibles dans le fichier de métadonnées, voir [document Metadata Fields in Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md). Ce fichier peut généralement être ingéré par des outils tiers.

### <a name="tag-data"></a>Données de balise

Ce contenu est ajouté en tant que champs dans le fichier de métadonnées. Elle contient toutes les informations de balise appliquées dans les ensembles de révision.

### <a name="text-files"></a>Fichiers texte

Des fichiers texte peuvent être générés pour chaque fichier exporté à partir d’un ensemble de révision. Souvent, ces fichiers sont requis par les partenaires de services dans le cadre de l’ingestion de données dans des outils tiers.

### <a name="redacted-files"></a>Fichiers biffés

Si des fichiers au format PDF biffés sont générés lors de la révision, ces fichiers sont disponibles lors de l’exportation. Vous pouvez décider s’il faut exporter les fichiers natifs uniquement ou remplacer les fichiers natifs qui ont nécessité la biffure avec les fichiers PDF qui contiennent la Redactions réelle.

### <a name="export-location"></a>Emplacement d’exportation

Le contenu exporté est remis à un objet BLOB Azure fourni par Microsoft ou le BLOB d’un client peut être utilisé si les détails sont fournis lors de l’exportation.

### <a name="export-structure"></a>Structure d’exportation

Lorsque le contenu est exporté à partir d’un ensemble de révision, le contenu est organisé dans la structure suivante.

  - Dossier racine – ID de téléchargement
    
      - Export\_load\_file. csv = fichier de métadonnées
    
      - Summary. txt = un fichier résumé avec les statistiques d’exportation
    
      - Fichiers\_d’entrée\_ou natifs = contient tous les fichiers natifs
    
      - Fichiers\_d’erreur = contient les fichiers d’erreur inclus dans l’exportation.
        
          - ExtractionError : CSV qui contient les métadonnées de fichiers disponibles qui n’ont pas été correctement extraites des fichiers parents
        
          - ProcessingError – contenu avec des erreurs de traitement. Ce contenu est de niveau élément : si une pièce jointe a rencontré une erreur de traitement, le courrier électronique qui contient la pièce jointe est inclus dans ce dossier.
    
      - Fichiers\_texte\_extraits = contient tous les fichiers texte extraits générés lors du traitement.