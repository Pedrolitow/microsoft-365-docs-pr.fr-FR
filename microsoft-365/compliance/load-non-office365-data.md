---
title: Charger des données non-Microsoft 365 dans la preuve
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
description: Découvrez comment utiliser la fonctionnalité d’importation de contenu autre qu’Office 365 pour télécharger des documents non Office 365 dans des preuves dans une enquête de données.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 9bfebc6aad9bc37d7d78ec4a0d50e6de967ac7d1
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44815481"
---
# <a name="load-non-microsoft-365-data-into-evidence"></a>Charger des données non-Microsoft 365 dans la preuve

Tous les documents que vous devrez peut-être analyser dans une enquête sur les données se trouvent dans Microsoft 365. Avec la fonctionnalité d’importation de contenu non-Microsoft 365, vous pouvez télécharger des documents qui ne résident pas dans Microsoft 365 dans des preuves afin qu’ils puissent être analysés lors d’une enquête de données.

## <a name="requirements-to-upload-non-office-365-content"></a>Conditions requises pour télécharger du contenu non-Office 365

L’utilisation de la fonctionnalité Télécharger non-Microsoft 365, comme décrit dans cette procédure, nécessite que vous disposiez des éléments suivants :

- Un abonnement Microsoft 365 ou Office 365 E5.

- Tous les intérêts dont le contenu n’est pas Microsoft 365 seront téléchargés doivent disposer de la licence de complément E5 ou E5 appropriée.

- Un cas eDiscovery existant.

- Tous les fichiers de téléchargement rassemblé dans des dossiers où se trouve un dossier par dépositaire et le nom de ces dossiers est au format *alias@domainname*. Le *alias@domainname* doit être l’alias et le domaine de l’utilisateur. Vous pouvez collecter tous les dossiers *alias@domainname* dans un dossier racine. Le dossier racine ne peut contenir que les dossiers *alias@domainname* , il ne doit pas y avoir de fichiers libres dans le dossier racine.

- Un compte qui est un gestionnaire eDiscovery ou un administrateur eDiscovery outils de stockage Microsoft Azure installé sur un ordinateur ayant accès à la structure de dossiers de contenu non-Microsoft 365.

- Installez AzCopy, que vous pouvez faire à partir de la [prise en main de AzCopy](https://docs.microsoft.com/azure/storage/common/storage-use-azcopy).

## <a name="upload-non-microsoft-365-content-in-to-a-data-investigation"></a>Télécharger du contenu non-Microsoft 365 dans une enquête de données

1. Ouvrez les **enquêtes de données** et accédez à l’enquête sur laquelle les données non Microsoft 365 seront téléchargées.  Cliquez sur l’onglet **Evidence** , puis sélectionnez l’ensemble de preuves sur lequel vous souhaitez charger les données.  Si vous n’avez pas encore créé d’ensemble de preuves, vous pouvez le faire maintenant.  Enfin, cliquez sur **gérer les preuves** , puis afficher les **téléchargements** dans la section données.

2. Cliquez sur le bouton **Télécharger les fichiers** pour démarrer l’Assistant importation de données non-Microsoft 365.

![Charger des fichiers](../media/574f4059-4146-4058-9df3-ec97cf28d7c7.png)

3. La première étape de l’Assistant consiste à préparer un objet BLOB Azure sécurisé pour les fichiers à charger.  Une fois la préparation terminée, cliquez sur le bouton **suivant : charger des fichiers** .

![Préparation à l’importation de données non Microsoft 365](../media/0670a347-a578-454a-9b3d-e70ef47aec57.png)
 
4. Dans l’étape **Télécharger les fichiers** , spécifiez le chemin d' **accès à l’emplacement des fichiers**, c’est ici que se trouvent les données autres que Microsoft 365 que vous prévoyez d’importer.  La définition de l’emplacement correct garantit la mise à jour correcte de la commande AzCopy.

> [!NOTE]
> Si vous n’avez pas encore installé AzCopy, vous pouvez le faire à partir de là :https://docs.microsoft.com/azure/storage/common/storage-use-azcopy

5. Copiez la commande prédéfinie en cliquant sur le lien **copier dans le presse-papiers** . Démarrez une invite de commandes Windows, collez la commande et appuyez sur entrée.  Les fichiers sont téléchargés vers le stockage BLOB Azure sécurisé pour l’étape suivante.

![Charger des fichiers pour l’importation de données non Microsoft 365](../media/3ea53b5d-7f9b-4dfc-ba63-90a38c14d41a.png)

![Utiliser AzCopy pour importer des données non-Microsoft 365](../media/504e2dbe-f36f-4f36-9b08-04aea85d8250.png)

6. Enfin, revenez à la sécurité & conformité et cliquez sur le bouton **suivant : traiter les fichiers** .  Cela lance le traitement, l’extraction de texte et l’indexation des fichiers téléchargés.  Vous pouvez suivre la progression du traitement ou dans l’onglet **travaux** .  Une fois terminé, les nouveaux fichiers sont disponibles dans l’ensemble de preuves.  Une fois le traitement terminé, vous pouvez faire disparaître l’Assistant.

![Fichiers de processus d’importation non-Microsoft 365](../media/218b1545-416a-4a9f-9b25-3b70e8508f67.png)

