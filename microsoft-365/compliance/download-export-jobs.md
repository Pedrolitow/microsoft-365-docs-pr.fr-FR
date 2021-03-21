---
title: Télécharger des travaux d’exportation pour un cas advanced eDiscovery
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
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-mar2020
description: Installez et utilisez l’Explorateur de stockage Azure pour télécharger les documents qui ont été exportés à partir d’un jeu à réviser dans Advanced eDiscovery.
ms.openlocfilehash: 0a73d157b2661202507883dd6542cdf6c6b482f8
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50926620"
---
# <a name="download-export-jobs-in-an-advanced-ediscovery-case"></a>Télécharger des travaux d’exportation dans un cas advanced eDiscovery

Lorsque vous exportez des documents à partir d’un groupe de révision dans un cas Advanced eDiscovery, les documents sont téléchargés vers un emplacement de stockage Azure fourni par Microsoft ou vers un emplacement de stockage Azure géré par votre organisation. Le type d’emplacement de stockage Azure utilisé dépend de l’option sélectionnée lors de l’exportation des documents.

Cet article fournit des instructions sur l’utilisation de l’Explorateur de stockage Microsoft Azure pour se connecter à un emplacement de stockage Azure pour parcourir et télécharger les documents exportés. Pour plus d’informations sur l’Explorateur de stockage Azure, voir Démarrage rapide : [utiliser l’Explorateur de stockage Azure.](/azure/storage/blobs/storage-quickstart-blobs-storage-explorer)

## <a name="step-1-install-the-azure-storage-explorer"></a>Étape 1 : Installer l’Explorateur de stockage Azure

La première étape consiste à télécharger et installer l’Explorateur de stockage Azure. Pour obtenir des instructions, [consultez l’outil Azure Storage Explorer.](https://go.microsoft.com/fwlink/p/?LinkId=544842) Vous utilisez cet outil pour vous connecter aux documents exportés et les télécharger à l’étape 3.

## <a name="step-2-obtain-the-sas-url-from-the-export-job"></a>Étape 2 : Obtenir l’URL SAS à partir de la tâche d’exportation

L’étape suivante consiste à obtenir l’URL de signature d’accès partagé (SAS) générée lorsque vous avez créé la tâche d’exportation pour exporter des documents à partir d’un ensemble [de révision.](export-documents-from-review-set.md) Vous pouvez copier l’URL SAS pour les documents téléchargés vers un emplacement de stockage Azure fourni par Microsoft ou un emplacement de stockage Azure géré par votre organisation. Dans les deux cas, vous utilisez l’URL SAS pour vous connecter à l’emplacement de stockage Azure à l’étape 3.

1. Dans la page **Advanced eDiscovery,** consultez le cas, puis cliquez sur **l’onglet** Exportation.

2. Dans l'onglet **Exportations** cliquez sur la tâche d'exportation que vous souhaitez télécharger.

3. Dans la page volante, sous **Emplacements,** copiez l’URL SAS qui s’affiche. Si nécessaire, vous pouvez l’enregistrer dans un fichier pour y accéder à l’étape 3.
 
   ![Copier l’URL SAS affichée sous Emplacements](../media/eDiscoExportJob.png)

## <a name="step-3-connect-to-the-azure-storage-location"></a>Étape 3 : Se connecter à l’emplacement de stockage Azure

La dernière étape consiste à utiliser l’Explorateur de stockage Azure et l’URL SAS pour vous connecter à l’emplacement de stockage Azure et télécharger les documents que vous avez exportés vers un ordinateur local.

1. Ouvrez l’Explorateur de stockage Azure que vous avez installé à l’étape 1.

2. Cliquez sur **l’icône Ajouter un** compte. Vous pouvez également cliquer avec le bouton droit sur **Comptes de stockage.**

   ![Cliquez sur l’icône Ajouter un compte](../media/AzureStorageConnect.png)

3. Dans la page **Se connecter à Azure Storage,** cliquez sur Utiliser un URI de signature d’accès partagé **(SAS),** puis cliquez sur **Suivant**.

    ![Cliquez sur Utiliser un URI de signature d’accès partagé (SAS), puis sur Suivant](../media/AzureStorageConnect2.png)

4. Dans la page Attacher **avec l’URI SAS,** cliquez dans la zone URI, puis collez l’URL SAS obtenue à l’étape 2. 

    ![Coller l’URL SAS dans la zone URI](../media/AzureStorageConnect3.png)

    Notez qu’une partie de l’URL SAS est affichée dans la zone Nom **complet.** Il sera utilisé comme nom d’affichage du conteneur  créé sous les comptes de stockage après la connexion à l’emplacement de stockage. Ce nom est constitué de l'identifiant de l'affaire Advanced eDiscovery et d'un identifiant unique. Vous pouvez conserver le nom d'affichage par défaut ou le changer. Si vous le changez, le nom d'affichage doit être unique.

5. Cliquez sur **Suivant**.

    La page **récapitulatif des connexions** s’affiche.

    ![Cliquez sur Se connecter sur la page récapitulatif des connexions pour vous connecter à l’emplacement de stockage Azure](../media/AzureStorageConnect4.png)

6. Dans la page **Résumé des connexions,** examinez les informations de connexion, puis cliquez sur **Se connecter.**

    Le **nœud conteneurs Blob** (sous Comptes de stockage (conteneurs **attachés)**  >   \> est ouvert.

    ![Exporter des travaux dans le nœud conteneurs Blobs](../media/AzureStorageConnect5.png)

    Il contient un conteneur nommé avec le nom complet de l’étape 4. Ce conteneur contient un dossier pour chaque tâche d’exportation que vous avez créée. Ces dossiers sont nommés avec un ID qui correspond à l’ID de la tâche d’exportation. Vous trouverez ces ID d’exportation (et le  nom de l’exportation)  sous Les informations de support sur la page volante pour chaque tâche de préparation de l’exportation répertoriée sous l’onglet **Travaux.**

7. Double-cliquez sur le dossier du travail d’exportation pour l’ouvrir.

   Une liste de dossiers et de rapports d’exportation s’affiche.
   
    ![Le dossier d’exportation contient les fichiers exportés et les rapports d’exportation](../media/AzureStorageConnect6.png)

   Le dossier du travail d’exportation contient les éléments suivants. Les éléments réels dans le dossier d’exportation sont déterminés par les options d’exportation configurées lors de la création de la tâche d’exportation. Pour plus d’informations, [voir Exporter des documents à partir d’un jeu à réviser.](export-documents-from-review-set.md)

    - Export_load_file.csv : ce fichier CSV est un rapport d’exportation détaillé qui contient des informations sur chaque document exporté. Le fichier se compose d’une colonne pour chaque propriété de métadonnées d’un document. Pour obtenir la liste et la description des métadonnées incluses dans ce rapport, voir la colonne Nom de champ exporté dans la table dans les champs de métadonnées de document dans [Advanced eDiscovery](document-metadata-fields-in-advanced-ediscovery.md). 
    
    - Summary.txt : fichier texte qui contient un résumé de l’exportation, y compris les statistiques d’exportation.
    
    - Extracted_text_files : ce dossier contient une version de fichier texte de chaque document exporté.
     
    - NativeFiles : ce dossier contient une version de fichier native de chaque document exporté.
    
    - Error_files : ce dossier inclut les éléments suivants lorsque la tâche d’exportation contient des fichiers d’erreur : 
        
      - ExtractionError.csv : ce fichier CSV contient les métadonnées disponibles pour les fichiers qui n’ont pas été correctement extraits de leur élément parent.
        
      - ProcessingError : ce dossier contient des documents contenant des erreurs de traitement. Ce contenu est au niveau de l’élément, ce qui signifie que si une pièce jointe a une erreur de traitement, le document qui contient la pièce jointe est également inclus dans ce dossier.
 
8. Pour exporter tous les contenus de l'exportation, sélectionnez le dossier d'exportation, puis cliquez sur **Télécharger**.

9. Indiquez l'endroit où vous souhaitez télécharger les fichiers exportés, puis cliquez sur Sélectionnez le dossier.

    L’Explorateur de stockage Azure démarre le processus d’exportation. L’état du téléchargement des éléments exportés s’affiche dans **le volet** Activités. Un message s’affiche lorsque le téléchargement est terminé.

    ![Un message s’affiche lorsque le téléchargement est terminé.](../media/AzureStorageConnect8.png)

> [!NOTE]
> Au lieu de télécharger l'ensemble du travail d'exportation, vous pouvez sélectionner des éléments spécifiques à télécharger. Et au lieu de télécharger des éléments, vous pouvez faire double-cliquer sur un élément pour le visualiser.