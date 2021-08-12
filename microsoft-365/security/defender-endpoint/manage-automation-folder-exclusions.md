---
title: Gérer les exclusions du dossier d’automatisation
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
ms.openlocfilehash: e469bc9d9ce3de8cd1425231f4b4b90247da2317a6ffc90ded86f5e4880563cc
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53806747"
---
# <a name="manage-automation-folder-exclusions"></a>Gérer les exclusions du dossier d’automatisation 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationexclusionfolder-abovefoldlink)

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
1. Dans le volet de navigation, **sélectionnez** Paramètres exclusions de  >  **dossiers Endpoints**  >  **Rules**  >  **Automation.**  

2. Cliquez **sur Exclusion de nouveau dossier.**  

3. Entrez les détails du dossier :

    - Folder
    - Extensions
    - Noms de fichiers
    - Description

4. Cliquez sur **Save (Enregistrer)**.

>[!NOTE]
> Les commandes Live Response pour collecter ou examiner les fichiers exclus échouent avec l’erreur : « Le fichier est exclu ». En outre, les examens automatisés ignorent les éléments exclus.

## <a name="edit-an-automation-folder-exclusion"></a>Modifier une exclusion de dossier d’automatisation 
1. Dans le volet de navigation, **sélectionnez** Paramètres exclusions de  >  **dossiers Endpoints**  >  **Rules**  >  **Automation.** 

2. Cliquez **sur Modifier** sur l’exclusion de dossier.  

3. Mettez à jour les détails de la règle et cliquez sur **Enregistrer.**

## <a name="remove-an-automation-folder-exclusion"></a>Supprimer une exclusion de dossier d’automatisation 
1. Dans le volet de navigation, **sélectionnez** Paramètres exclusions de  >  **dossiers Endpoints**  >  **Rules**  >  **Automation.**  
2. Cliquez sur **Supprimer l’exclusion.** 


## <a name="related-topics"></a>Sujets connexes
- [Gérer les listes d’automatisation autorisées/bloquées](manage-indicators.md)
- [Gérer les chargements du fichier d’automatisation](manage-automation-file-uploads.md)
