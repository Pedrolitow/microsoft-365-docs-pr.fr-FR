---
title: Charger des données non-Microsoft 365 dans un groupe de révision
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment importer des données non Microsoft 365 dans un ensemble de révisions à des fins d’analyse dans un cas eDiscovery (Premium).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 41ba0a3d9f1989cff2bdffdab38f7eee020d7b5d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095815"
---
# <a name="load-non-microsoft-365-data-into-a-review-set"></a>Charger des données non-Microsoft 365 dans un groupe de révision

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Tous les documents que vous devez analyser dans Microsoft Purview eDiscovery (Premium) ne se trouvent pas dans Microsoft 365. Avec la fonctionnalité d’importation de données non Microsoft 365 dans eDiscovery (Premium), vous pouvez charger des documents qui ne se trouvent pas dans Microsoft 365 dans un jeu de révision. Cet article vous montre comment intégrer vos documents non Microsoft 365 dans eDiscovery (Premium) à des fins d’analyse.

## <a name="requirements-to-upload-non-office-365-content"></a>Configuration requise pour charger du contenu non Office 365

L’utilisation de la fonctionnalité de chargement non Microsoft 365 décrite dans cet article nécessite les éléments suivants :

- La licence appropriée doit être attribuée à tous les consignats auxquels vous souhaitez associer du contenu non Microsoft 365. Pour plus d’informations, consultez [Démarrage avec eDiscovery (Premium).](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses)

- Cas eDiscovery (Premium) existant.

- Les consignats doivent être ajoutés au cas avant de pouvoir charger et associer les données non Microsoft 365.

- Les données non Microsoft 365 doivent être un type de fichier pris en charge par eDiscovery (Premium). Pour plus d’informations, consultez [types de fichiers pris en charge dans eDiscovery (Premium).](supported-filetypes-ediscovery20.md)

- Tous les fichiers chargés dans un jeu à réviser doivent se trouver dans des dossiers, chaque dossier étant associé à un dépositaire spécifique. Les noms de ces dossiers doivent être au format suivant : *alias@nom_domaine*. La valeur alias@nom_domaine doit correspondre à l’alias Microsoft 365 et au domaine de l’utilisateur. Vous pouvez collecter tous les dossiers alias@domainname dans un dossier racine. Le dossier racine ne peut contenir que les dossiers alias@domainname. Les fichiers libres dans le dossier racine ne sont pas pris en charge.

   La structure des dossiers pour les données non Microsoft 365 que vous souhaitez charger est similaire à l’exemple suivant :

   - c:\nonO365\abraham.mcmahon@contoso.com
   - c:\nonO365\jewell.gordon@contoso.com
   - c:\nonO365\staci.gonzalez@contoso.com

   Où abraham.mcmahon@contoso.com, jewell.gordon@contoso.com et staci.gonzalez@contoso.com sont les adresses SMTP des consignatateurs dans le cas.

   ![Structure de dossiers de chargement de données non Microsoft 365.](../media/3f2dde84-294e-48ea-b44b-7437bd25284c.png)

- Compte affecté au groupe de rôles gestionnaire eDiscovery (et ajouté en tant qu’administrateur eDiscovery).

- Outil AzCopy v8.1 installé sur un ordinateur qui a accès à la structure de dossiers de contenu non Microsoft 365. Pour installer AzCopy, consultez [Transférer des données avec AzCopy v8.1 sur Windows](/previous-versions/azure/storage/storage-use-azcopy). Veillez à installer AzCopy à l’emplacement par défaut, à savoir **%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy**. Vous devez utiliser AzCopy v8.1. D’autres versions d’AzCopy peuvent ne pas fonctionner lors du chargement de données non Microsoft 365 dans eDiscovery (Premium).


## <a name="upload-non-microsoft-365-content-into-ediscovery-premium"></a>Télécharger contenu non Microsoft 365 dans eDiscovery (Premium)

1. En tant qu’administrateur eDiscovery Manager ou eDiscovery, ouvrez eDiscovery (Premium) et accédez au cas où les données non Microsoft 365 seront chargées.  

2. Cliquez sur **Ensembles** de révision, puis sélectionnez l’ensemble de révisions dans lequel charger les données non Microsoft 365.  Si vous n’avez pas de jeu de révision, vous pouvez en créer un. 
 
3. Ouvrez l’ensemble de révisions en cliquant dessus ou en le sélectionnant et en cliquant sur **Ouvrir le jeu de révisions**.

4. Dans l’ensemble de révisions, cliquez sur **Gérer le jeu de révision** (flèche vers le bas juste après l’option **Actions**), puis cliquez sur l’option **De données non Office 365**.

5. Cliquez sur **Charger des fichiers** pour démarrer l’Assistant importation de données.

   ![Télécharger fichiers.](../media/574f4059-4146-4058-9df3-ec97cf28d7c7.png)

   La première étape de l’Assistant prépare un emplacement de stockage Azure sécurisé fourni par Microsoft pour charger les fichiers.  Une fois la préparation terminée, le bouton **Suivant : charger des fichiers** devient actif.

   ![Importation non Microsoft 365 : préparer.](../media/0670a347-a578-454a-9b3d-e70ef47aec57.png)
 
5. Cliquez sur **Suivant : charger des fichiers**.

6. Dans la page **Télécharger fichiers**, procédez comme suit :

   ![Importation non Microsoft 365 : fichiers Télécharger.](../media/3ea53b5d-7f9b-4dfc-ba63-90a38c14d41a.png)

   a. Dans la zone **Chemin d’accès à l’emplacement des fichiers**, vérifiez ou tapez l’emplacement du dossier racine où vous avez stocké les données non Microsoft 365 que vous souhaitez charger. Par exemple, pour l’emplacement des exemples de fichiers indiqués dans la **section Avant de commencer**, vous devez taper **%USERPROFILE\Downloads\nonO365**. Si vous indiquez l’emplacement approprié, la commande AzCopy affichée dans la zone sous le chemin d’accès est correctement mise à jour.

   b. Cliquez sur **Copier dans le Presse-papiers** pour copier la commande affichée dans la zone.

7. Démarrez une invite de commandes Windows, collez la commande que vous avez copiée à l’étape précédente, puis **appuyez sur Entrée** pour démarrer la commande AzCopy.  Une fois la commande démarrée, les fichiers non Microsoft 365 sont chargés à l’emplacement stockage Azure préparé à l’étape 4.

   ![Importation non Microsoft 365 : AzCopy.](../media/504e2dbe-f36f-4f36-9b08-04aea85d8250.png)

   > [!NOTE]
   > Comme indiqué précédemment, vous devez utiliser AzCopy v8.1 pour utiliser correctement la commande fournie sur la page **de fichiers Télécharger**. Si la commande AzCopy fournie échoue, consultez [Résolution des problèmes liés à AzCopy dans eDiscovery (Premium)](troubleshooting-azcopy.md).

8. Retour au portail de conformité Microsoft Purview, puis cliquez sur **Suivant : Traiter les fichiers** dans l’Assistant.  Cette opération initie le traitement, l’extraction de texte et l’indexation des fichiers non-Microsoft 365 qui ont été téléchargés vers l’emplacement de stockage Azure.  

9. Suivez la progression du traitement des fichiers dans la page **Traiter les fichiers** ou sous l’onglet **Travaux** en affichant un travail nommé **Ajouter des données non Microsoft 365 à un jeu de révision**.  Une fois le travail terminé, les nouveaux fichiers sont disponibles dans le jeu de révision.

   ![Importation non Microsoft 365 : traiter les fichiers.](../media/218b1545-416a-4a9f-9b25-3b70e8508f67.png)

10. Une fois le traitement terminé, vous pouvez fermer l’Assistant.
