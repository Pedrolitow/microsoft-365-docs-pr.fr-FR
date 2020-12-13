---
title: Importer du contenu non-Microsoft 365 pour une analyse avancée de la découverte électronique
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- OEC150
- MET150
ms.assetid: 0ee60763-a30b-495b-8543-971c3384a801
description: Procédure d’importation du contenu qui n’est pas stocké dans Microsoft 365 dans un objet BLOB Azure afin qu’il puisse être analysé avec AeD
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 03220e6baf16662ad8dfa970ef4d7077d08b0826
ms.sourcegitcommit: 47de4402174c263ae8d70c910ca068a7581d04ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "49662899"
---
# <a name="import-non-microsoft-365-content-for-advanced-ediscovery-classic-analysis"></a>Importer du contenu non-Microsoft 365 pour l’analyse avancée eDiscovery (classique)

Tous les documents que vous devrez peut-être analyser avec Advanced eDiscovery ne seront pas opérationnels dans Microsoft 365. Avec la fonctionnalité d’importation de contenu non-Microsoft 365 dans Advanced eDiscovery, vous pouvez télécharger des documents qui ne résident pas dans Microsoft 365 (à l’exception des fichiers PST) dans un objet blob de stockage associé à une casse, et les analyser avec Advanced eDiscovery. Cette procédure vous montre comment intégrer des documents non-Microsoft 365 dans Advanced eDiscovery pour les analyser.
  
> [!NOTE]
> Pour utiliser Advanced eDiscovery, votre organisation doit souscrire un abonnement Office 365 E3 avec le module complémentaire Conformité avancée ou un abonnement E5. Si vous ne disposez pas d’un abonnement et que vous souhaitez essayer Advanced eDiscovery, vous pouvez vous [inscrire pour utiliser une version d’évaluation d’Office 365 Entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279). 
  
> [!NOTE]
> Vous pouvez acheter un abonnement de complément de stockage de données eDiscovery avancé pour votre contenu non-Microsoft 365. Cette fonctionnalité est exclusivement disponible pour le contenu qui doit être analysé avec Advanced eDiscovery. Suivez les étapes de la procédure [acheter ou modifier un module complémentaire pour Microsoft 365 pour les entreprises](https://docs.microsoft.com/microsoft-365/commerce/buy-or-edit-an-add-on) et acheter le complément de stockage avancé eDiscovery. 
  
## <a name="requirements-to-upload-non-office-365-content"></a>Conditions requises pour télécharger du contenu non-Office 365

L’utilisation de la fonctionnalité Télécharger non-Office 365 comme décrit dans cette procédure nécessite que vous ayez les éléments suivants :
  
- Un Office 365 E3 avec le complément de conformité avancé ou l’abonnement E5.
    
- Tous les dépositaires dont le contenu n’est pas Office 365 seront chargés doivent disposer de E3 avec un complément de conformité avancé ou des licences E5.
    
- Un cas eDiscovery existant.
    
- Tous les fichiers de téléchargement rassemblé dans des dossiers où se trouve un dossier par dépositaire et le nom de ces dossiers est au format  *alias@domainname*  . Le  *alias@domainname*  doit être l’alias et le domaine Office 365 utilisateurs. Vous pouvez collecter tous les dossiers  *alias@domainname*  dans un dossier racine. Le dossier racine ne peut contenir que les dossiers  *alias@domainname*  , il ne doit pas y avoir de fichiers libres dans le dossier racine.
    
- Un compte qui soit un gestionnaire eDiscovery ou un administrateur eDiscovery.
    
- [Outils de stockage Microsoft Azure](https://aka.ms/downloadazcopy) installés sur un ordinateur ayant accès à la structure de dossiers de contenu non Office 365. 
    
## <a name="upload-non-office-365-content-into-advanced-ediscovery"></a>Chargement de contenu non-Office 365 dans Advanced eDiscovery


1. En tant que gestionnaire eDiscovery ou administrateur eDiscovery, ouvrez **eDiscovery** et ouvrez le cas où les données non Office 365 seront téléchargées vers. Si vous devez créer un cas, voir [Manage eDiscovery cases dans le centre de sécurité &amp; conformité](ediscovery-cases.md).
    
2. Cliquez sur **basculer vers Advanced eDiscovery**.

3. Sélectionnez **examiner les jeux** dans le menu.

4. Sélectionnez un ensemble de validation existant ou choisissez **Ajouter un ensemble de réexamens**.

5. Sélectionnez **Manage Review Set**.

6. Dans la carte de données autres que Office 365, sélectionnez **afficher les téléchargements**.

7. Choisissez **Télécharger les fichiers** pour démarrer l’Assistant chargement de fichiers.

8. Le premier onglet est **1. Étape de préparation**. Sélectionnez **suivant : charger les fichiers**.

9. Sur le **2. Onglet charger les fichiers** vous êtes invité à télécharger AzCopy.exe si vous ne l’avez pas déjà fait, puis à indiquer le chemin d’accès à l’emplacement du fichier. Par exemple, `C:\Upload`  vous donnera la commande pour exécuter AzCopy.exe. À l’aide `C:\Upload` de, vous verrez :

   `"%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy\AzCopy.exe" /Source:"c:\upload" /Dest:"https://spnam03salinkexternal003.blob.core.windows.net/16d13440-a6a4-4bc5-a82b-10ac9cfe9d7c-1601401811-externalstore?sv=2017-07-29&sr=c&si=ExternalStore63%7C0&sig=9Dq5v20TwkxByYDHhIEx%2FHSLlmlqUjY0njkJyTO0zGA%3D" /s`
  
10. Ouvrez une fenêtre d’invite de commandes et exécutez la commande AzCopy.exe pour importer les données dans Azure. Une fois toutes les données chargées, sélectionnez **suivant : traiter les fichiers**.

11. L’onglet suivant est **3. Traitez les fichiers** dans lesquels vous verrez les dépositaires auxquels des données sont associées et vous verrez également la progression des données importées.
        
    Pour plus d’informations sur la syntaxe Azcopy, consultez [la rubrique transférer des données avec le Azcopy sur Windows](https://docs.microsoft.com/azure/storage/common/storage-use-azcopy). 
    
    Pour plus d’informations sur le traitement de la découverte électronique avancée, voir [exécuter le module de processus et charger des données dans Advanced eDiscovery (classique)](run-the-process-module-and-load-data-in-advanced-ediscovery.md). 
    
    > [!IMPORTANT]
    > Il doit y avoir un dossier racine par utilisateur et le nom du dossier doit être au format <b>alias@domainname</b>  . 
   
    > [!IMPORTANT]
    > Une fois que le conteneur a été traité avec succès dans Advanced eDiscovery, vous ne pourrez plus ajouter de nouveau contenu au stockage SAS dans Azure. Si vous recueillez du contenu supplémentaire et que vous souhaitez l’ajouter à la demande d’analyse avancée de la découverte électronique, vous devez créer un conteneur de **données non-Office 365** et répéter cette procédure. 
  
    > [!NOTE]
    > Si le conteneur  *ne traite pas correctement en raison de problèmes d’attribution de nom de dossier*  et que vous résolvez les problèmes, vous devrez tout de même créer un nouveau conteneur et reconnecter et télécharger à nouveau à l’aide des procédures décrites dans cet article.
