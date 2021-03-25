---
title: Gérer les exclusions de dossiers d’automatisation
description: Ajoutez des exclusions de dossier d’automatisation pour contrôler les fichiers exclus d’un examen automatisé.
keywords: gérer, automatisation, exclusion, bloquer, nettoyer, malveillant
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 37a251acd3b7631cffffaf2eb76bf0f2b4954ee6
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51185836"
---
# <a name="manage-automation-folder-exclusions"></a>Gérer les exclusions de dossiers d’automatisation 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-automationexclusionfolder-abovefoldlink)

Les exclusions de dossiers Automation vous permettent de spécifier les dossiers que l’examen automatisé ignorera. 

Vous pouvez contrôler les attributs suivants concernant le dossier que vous souhaitez ignorer :
- Folders 
- Extensions des fichiers
- Noms de fichiers


**Dossiers**<br>
Vous pouvez spécifier un dossier et ses sous-dossiers à ignorer. 


>[!NOTE]
>Pour l’instant, l’utilisation de caractères wild cards comme moyen d’exclure des fichiers sous un répertoire n’est pas encore prise en charge. 


**Extensions**<br>
Vous pouvez spécifier les extensions à exclure dans un répertoire spécifique. Les extensions sont un moyen d’empêcher un attaquant d’utiliser un dossier exclu pour masquer une attaque. Les extensions définissent explicitement les fichiers à ignorer. 

**Noms de fichiers**<br>
Vous pouvez spécifier les noms de fichiers que vous souhaitez exclure dans un répertoire spécifique. Les noms sont un moyen d’empêcher un attaquant d’utiliser un dossier exclu pour masquer une attaque. Les noms définissent explicitement les fichiers à ignorer. 



## <a name="add-an-automation-folder-exclusion"></a>Ajouter une exclusion de dossier d’automatisation
1. Dans le volet de navigation, sélectionnez **Exclusions** du dossier Settings  >  **Automation.**  

2. Cliquez **sur Exclusion de nouveau dossier.**  

3. Entrez les détails du dossier :

    - Folder
    - Extensions
    - Noms de fichiers
    - Description
    

4. Cliquez sur **Enregistrer**.

>[!NOTE]
> Les commandes Live Response pour collecter ou examiner les fichiers exclus échouent avec l’erreur : « Le fichier est exclu ». En outre, les examens automatisés ignorent les éléments exclus.

## <a name="edit-an-automation-folder-exclusion"></a>Modifier une exclusion de dossier d’automatisation 
1. Dans le volet de navigation, sélectionnez **Exclusions** du dossier Settings  >  **Automation.** 

2. Cliquez **sur Modifier** sur l’exclusion de dossier.  

3. Mettez à jour les détails de la règle et cliquez sur **Enregistrer.**

## <a name="remove-an-automation-folder-exclusion"></a>Supprimer une exclusion de dossier d’automatisation 
1. Dans le volet de navigation, sélectionnez **Exclusions** du dossier Settings  >  **Automation.**  
2. Cliquez sur **Supprimer l’exclusion.** 


## <a name="related-topics"></a>Voir aussi
- [Gérer les listes d’automatisation autorisées/bloquées](manage-indicators.md)
- [Gérer les téléchargements de fichiers d’automatisation](manage-automation-file-uploads.md)
