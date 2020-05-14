---
title: Importer du contenu non-Microsoft 365 pour une analyse avancée de la découverte électronique
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
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
ms.openlocfilehash: be49e7d44c56988baa3cdc718498a03ee4acd50b
ms.sourcegitcommit: 1c90bcc5c56f24895f01c3e0423c3f6b73715c13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "44214538"
---
# <a name="import-non-microsoft-365-content-for-advanced-ediscovery-classic-analysis"></a>Importer du contenu non-Microsoft 365 pour l’analyse avancée eDiscovery (classique)

Tous les documents que vous devrez peut-être analyser avec Advanced eDiscovery ne seront pas opérationnels dans Microsoft 365. Avec la fonctionnalité d’importation de contenu non-Microsoft 365 dans Advanced eDiscovery, vous pouvez télécharger des documents qui ne résident pas dans Microsoft 365 (à l’exception des fichiers PST) dans un objet blob de stockage associé à une casse, et les analyser avec Advanced eDiscovery. Cette procédure vous montre comment intégrer des documents non-Microsoft 365 dans Advanced eDiscovery pour les analyser.
  
> [!NOTE]
> Pour utiliser Advanced eDiscovery, votre organisation doit souscrire un abonnement Office 365 E3 avec le module complémentaire Conformité avancée ou un abonnement E5. Si vous ne disposez pas d’un abonnement et que vous souhaitez essayer Advanced eDiscovery, vous pouvez vous [inscrire pour utiliser une version d’évaluation d’Office 365 Entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279). 
  
> [!NOTE]
> Vous pouvez acheter un abonnement de complément de stockage de données eDiscovery avancé pour votre contenu non-Microsoft 365. Cette fonctionnalité est exclusivement disponible pour le contenu qui doit être analysé avec Advanced eDiscovery. Suivez les étapes de la procédure [acheter ou modifier un module complémentaire pour Microsoft 365 pour les entreprises](https://docs.microsoft.com/microsoft-365/commerce/buy-or-edit-an-add-on) et acheter le complément de stockage avancé eDiscovery. 
  
## <a name="before-you-begin"></a>Avant de commencer

L’utilisation de la fonctionnalité Télécharger non-Office 365 comme décrit dans cette procédure nécessite que vous ayez les éléments suivants :
  
- Une application Office 365 E3 avec un complément de conformité avancé ou un abonnement E5
    
- Tous les dépositaires dont le contenu n’est pas Office 365 seront chargés doivent disposer de E3 avec un complément de conformité avancé ou des licences E5.
    
- Un cas eDiscovery existant
    
- Tous les fichiers de téléchargement rassemblé dans des dossiers où se trouve un dossier par dépositaire et le nom de ces dossiers est au format *alias@domainname* . Le *alias@domainname* doit être l’alias et le domaine Office 365 utilisateurs. Vous pouvez collecter tous les dossiers *alias@domainname* dans un dossier racine. Le dossier racine ne peut contenir que les dossiers *alias@domainname* , il ne doit pas y avoir de fichiers libres dans le dossier racine. 
    
- Un compte qui est un gestionnaire eDiscovery ou un administrateur eDiscovery
    
- [Outils de stockage Microsoft Azure](https://aka.ms/downloadazcopy) installés sur un ordinateur ayant accès à la structure de dossiers de contenu non Office 365. 
    
## <a name="upload-non-office-365-content-into-advanced-ediscovery"></a>Chargement de contenu non-Office 365 dans Advanced eDiscovery


1. En tant que gestionnaire eDiscovery ou administrateur eDiscovery, ouvrez **eDiscovery**et ouvrez le cas où les données non Office 365 seront téléchargées vers. Si vous devez créer un cas, reportez-vous à [la rubrique gestion des cas eDiscovery dans le centre de sécurité &amp; conformité](ediscovery-cases.md)
    
2. Cliquer sur **basculer vers Advanced eDiscovery**
    
3. Sous **type** de source **, sélectionnez données non Office 365**.
    
4. Cliquez sur **Ajouter un conteneur**. Nommez le conteneur et ajoutez une description.
    
5. Sélectionnez le conteneur nouvellement ajouté dans la liste du conteneur et copiez l’URL qui apparaît dans le volet d’informations du conteneur, puis fermez le volet.
    
6. Ouvrez une invite de commandes en tant qu’administrateur et accédez au répertoire dans lequel vous avez installé AzCopy..
    
7. Construisez la ligne de commande AzCopy pour télécharger les fichiers comme suit :
    
    AzCopy/source : " *chemin d’accès complet au dossier racine sur l’ordinateur local* "/dest : " *URL de conteneur jusqu’à et n’incluant pas l' ?*  « /DestSAS : » *reste de l’URL du conteneur à partir du ? jusqu’à la fin* «/S. 
    
    Par exemple, à l’aide des valeurs suivantes : 
    
  - dossier racine-données C:\Collected 
    
  - URL du conteneur- https://zoomsabcprodeuss114.blob.core.windows.net/ingestion53d059efe5f74784afb308f66cdebf17?sv=2015-04-05&amp ; SR = c &amp; si = NonOfficeData15% 7C0 &amp; SIG = Bk5INP8CUfv1y4CSJiJl3pJt3Ekvu8GS3P8NkOvoQxA% 3D
    
    la syntaxe de la ligne de commande AzCopy est la suivante :
    
     `AzCopy /Source:"C:\CollectedData" /Dest:"https://zoomsabcprodeuss114.blob.core.windows.net/ingestion53d059efe5f74784afb308f66cdebf17" /DestSAS:"?sv=2015-04-05&amp;sr=c&amp;si=NonOfficeData15%7C0&amp;sig=Bk5INP8CUfv1y4CSJiJl3pJt3Ekvu8GS3P8NkOvoQxA%3D" /S`
    
    Pour plus d’informations sur la syntaxe Azcopy, reportez-vous à [la rubrique transférer des données avec le Azcopy sur Windows](https://docs.microsoft.com/azure/storage/common/storage-use-azcopy) . 
    
    > [!IMPORTANT]
    > Il doit y avoir un dossier racine par utilisateur et le nom du dossier doit être au format *alias@domainname* . 
  
8. Une fois le téléchargement des dossiers terminé, revenez à Advanced eDiscovery. Le contenu des dossiers téléchargés est maintenant prêt à être traité dans Advanced eDiscovery. Sélectionnez le conteneur, puis cliquez sur le bouton processus. Pour plus d’informations sur le traitement eDiscovery avancé, reportez-vous à [la rubrique exécuter le module de processus et charger des données dans Advanced eDiscovery](run-the-process-module-and-load-data-in-advanced-ediscovery.md)
    
    > [!IMPORTANT]
    > Une fois que le conteneur a été traité avec succès dans Advanced eDiscovery, vous ne pourrez plus ajouter de nouveau contenu au stockage SAS dans Azure. Si vous recueillez du contenu supplémentaire et que vous souhaitez l’ajouter à la demande d’analyse avancée de la découverte électronique, vous devez créer un conteneur de **données non-Office 365** et répéter cette procédure. 
  
    > [!NOTE]
    > Si le conteneur *ne traite pas correctement en raison de problèmes d’attribution de nom de dossier* et que vous résolvez les problèmes, vous devrez tout de même créer un nouveau conteneur et reconnecter et télécharger à nouveau à l’aide des procédures décrites dans cet article.
