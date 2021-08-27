---
title: Charger des données non-Microsoft 365 dans un groupe de révision
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment importer des données non Microsoft 365 dans un groupe de révision pour analyse dans Advanced eDiscovery cas.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 65244b74cd868c4ec308327d15a070e67b9ac551
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58569044"
---
# <a name="load-non-microsoft-365-data-into-a-review-set"></a>Charger des données non-Microsoft 365 dans un groupe de révision

Tous les documents que vous devez analyser dans Advanced eDiscovery sont situés dans Microsoft 365. Avec la fonctionnalité d’importation de données non-Microsoft 365 dans Advanced eDiscovery, vous pouvez télécharger des documents qui ne se trouvent pas dans Microsoft 365 dans un groupe de révision. Cet article vous montre comment faire entrer vos documents non Microsoft 365 dans des Advanced eDiscovery pour analyse.

## <a name="requirements-to-upload-non-office-365-content"></a>Conditions requises pour télécharger du contenu non Office 365 contenu

L’utilisation de la fonctionnalité de chargement non Microsoft 365 décrite dans cet article nécessite que vous disposez des éléments suivants :

- Tous les dépositaires à qui vous souhaitez associer du contenu non Microsoft 365 doivent se voir attribuer la licence appropriée. Pour plus d’informations, [voir La mise en Advanced eDiscovery](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

- Un cas de Advanced eDiscovery existant.

- Les dépositaires doivent être ajoutés au cas avant de pouvoir charger et associer les données Microsoft 365 données non associées.

- Les données ne relevant pas de Microsoft 365 doivent correspondre à un type de fichier pris en charge par Advanced eDiscovery. Pour plus d’informations, voir [Types de fichiers pris en charge dans eDiscovery avancée](supported-filetypes-ediscovery20.md).

- Tous les fichiers chargés dans un jeu à réviser doivent se trouver dans des dossiers, chaque dossier étant associé à un dépositaire spécifique. Les noms de ces dossiers doivent être au format suivant : *alias@nom_domaine*. La valeur alias@nom_domaine doit correspondre à l’alias Microsoft 365 et au domaine de l’utilisateur. Vous pouvez collecter tous les alias@domainname dossiers d’un dossier racine. Le dossier racine ne peut contenir que les alias@domainname dossiers. Les fichiers libres dans le dossier racine ne sont pas pris en charge.

   La structure de dossiers pour les données non Microsoft 365 que vous souhaitez télécharger serait similaire à l’exemple suivant :

   - c:\nonO365\abraham.mcmahon@contoso.com
   - c:\nonO365\jewell.gordon@contoso.com
   - c:\nonO365\staci.gonzalez@contoso.com

   Où abraham.mcmahon@contoso.com, jewell.gordon@contoso.com et staci.gonzalez@contoso.com sont les adresses SMTP des dépositaires dans le cas.

   ![Structure de dossiers de chargement Microsoft 365 données non complexes.](../media/3f2dde84-294e-48ea-b44b-7437bd25284c.png)

- Compte affecté au groupe de rôles Gestionnaire eDiscovery (et ajouté en tant qu’administrateur eDiscovery).

- L’outil AzCopy v8.1 installé sur un ordinateur qui a accès à la structure de dossiers de contenu non Microsoft 365 de contenu. Pour installer AzCopy, voir Transférer des données avec [AzCopy v8.1 sur Windows](/previous-versions/azure/storage/storage-use-azcopy). Assurez-vous d’installer AzCopy à l’emplacement par défaut, à savoir **%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy**. Vous devez utiliser AzCopy v8.1. D’autres versions d’AzCopy peuvent ne pas fonctionner lors du chargement de données non Microsoft 365 dans Advanced eDiscovery.


## <a name="upload-non-microsoft-365-content-into-advanced-ediscovery"></a>Télécharger contenu non Microsoft 365 contenu dans Advanced eDiscovery

1. En tant que gestionnaire eDiscovery ou administrateur eDiscovery, ouvrez Advanced eDiscovery et sélectionnez le cas où les données non Microsoft 365 seront téléchargées.  

2. Cliquez **sur Ensembles** de révision, puis sélectionnez le jeu à réviser vers Microsoft 365 données non définies.  Si vous n’avez pas de jeu à réviser, vous pouvez en créer un. 
 
3. Dans l’ensemble de révision, cliquez sur **Gérer l’ensemble de révision**, puis cliquez sur **Afficher les téléchargements** sur la mosaïque **Données non-Microsoft 365**.

4. Cliquez sur **Charger des fichiers** pour démarrer l’Assistant importation de données.

   ![Télécharger fichiers.](../media/574f4059-4146-4058-9df3-ec97cf28d7c7.png)

   La première étape de l’Assistant prépare un emplacement de stockage Azure sécurisé fourni par Microsoft pour charger les fichiers.  Une fois la préparation terminée, le bouton **Suivant : charger des fichiers** devient actif.

   ![Importation non Microsoft 365 : Préparer.](../media/0670a347-a578-454a-9b3d-e70ef47aec57.png)
 
5. Cliquez sur **Suivant : charger des fichiers**.

6. Dans la page **Télécharger fichiers,** faites les choses suivantes :

   ![Importation non Microsoft 365 : Télécharger fichiers.](../media/3ea53b5d-7f9b-4dfc-ba63-90a38c14d41a.png)

   a. Dans **la** zone Chemin d’accès à l’emplacement des fichiers, vérifiez ou tapez l’emplacement du dossier racine dans lequel vous avez stocké les données non Microsoft 365 que vous souhaitez télécharger. Par exemple, pour l’emplacement des exemples de fichiers indiqués dans la **section** Avant de commencer, tapez **%USERPROFILE\Downloads\nonO365**. La fourniture de l’emplacement correct garantit que la commande AzCopy affichée dans la zone sous le chemin d’accès est correctement mise à jour.

   b. Cliquez **sur Copier dans le Presse-papiers** pour copier la commande affichée dans la zone.

7. Démarrez une invite Windows commande, collez la commande que vous avez copiée à l’étape précédente, puis appuyez sur **Entrée** pour démarrer la commande AzCopy.  Une fois que vous avez lancé la commande, les fichiers non Microsoft 365 seront téléchargés vers l’emplacement stockage Azure qui a été préparé à l’étape 4.

   ![Importation non Microsoft 365 : AzCopy.](../media/504e2dbe-f36f-4f36-9b08-04aea85d8250.png)

   > [!NOTE]
   > Comme indiqué précédemment, vous devez utiliser AzCopy v8.1 pour utiliser correctement la commande fournie dans la page Télécharger **fichiers.** Si la commande AzCopy fournie échoue, consultez Résoudre les problèmes [d’AzCopy dans Advanced eDiscovery](troubleshooting-azcopy.md).

8. Revenir à la Centre de conformité Microsoft 365, puis cliquez sur **Suivant : Traiter les fichiers dans** l’Assistant.  Cette opération initie le traitement, l’extraction de texte et l’indexation des fichiers non-Microsoft 365 qui ont été téléchargés vers l’emplacement de stockage Azure.  

9. Suivez la progression du traitement des fichiers sur  la **page** Des fichiers de processus ou sous l’onglet Travaux en visualisation d’un travail nommé Ajout de données non Microsoft 365 à un jeu **à réviser.**  Une fois le travail terminé, les nouveaux fichiers sont disponibles dans le jeu à réviser.

   ![Importation non Microsoft 365 : traiter les fichiers.](../media/218b1545-416a-4a9f-9b25-3b70e8508f67.png)

10. Une fois le traitement terminé, vous pouvez fermer l’Assistant.