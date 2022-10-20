---
title: Gérer les exclusions du dossier d’automatisation
description: Ajoutez des exclusions de dossier Automation pour contrôler les fichiers exclus d’une investigation automatisée.
keywords: gérer, automatiser, exclure, bloquer, nettoyer, malveillant
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: d7dd4fd8fe8961bc18dccc4720effc62de493768
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68633700"
---
# <a name="manage-automation-folder-exclusions"></a>Gérer les exclusions du dossier d’automatisation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationexclusionfolder-abovefoldlink)

Les exclusions de dossier Automation vous permettent de spécifier les dossiers que l’investigation automatisée ignore.

Vous pouvez contrôler les attributs suivants sur le dossier que vous souhaitez ignorer :

- **Dossiers** : vous pouvez spécifier un dossier et ses sous-dossiers à ignorer.

  > [!NOTE]
  > Pour l’instant, l’utilisation de caractères génériques comme moyen d’exclure des fichiers sous un répertoire n’est pas encore prise en charge.

- **Extensions des fichiers** : vous pouvez spécifier les extensions à exclure dans un répertoire spécifique. Les extensions permettent d’empêcher un attaquant d’utiliser un dossier exclu pour masquer un exploit. Les extensions définissent explicitement les fichiers à ignorer.

- **Noms de fichiers** : vous pouvez spécifier les noms de fichiers que vous souhaitez exclure dans un répertoire spécifique. Les noms sont un moyen d’empêcher un attaquant d’utiliser un dossier exclu pour masquer un exploit. Les noms définissent explicitement les fichiers à ignorer.

## <a name="add-an-automation-folder-exclusion"></a>Ajouter une exclusion de dossier Automation

1. Dans le volet de navigation, sélectionnez **Les exclusions** de **dossiers** Paramètres \> **de points de terminaison** \> **Rules** \> Automation.

2. Cliquez sur **Nouvelle exclusion de dossier**.

3. Entrez les détails du dossier :

    - Folder
    - Extensions
    - Noms de fichiers
    - Description

4. Cliquez sur **Enregistrer**.

> [!NOTE]
> Les commandes Live Response pour collecter ou examiner les fichiers exclus échouent avec l’erreur : « Le fichier est exclu ». En outre, les enquêtes automatisées ignorent les éléments exclus.

## <a name="edit-an-automation-folder-exclusion"></a>Modifier une exclusion de dossier Automation

1. Dans le volet de navigation, sélectionnez **Les exclusions** de **dossiers** Paramètres \> **de points de terminaison** \> **Rules** \> Automation.
2. Cliquez sur **Modifier** dans l’exclusion de dossier.
3. Mettez à jour les détails de la règle, puis cliquez sur **Enregistrer**.

## <a name="remove-an-automation-folder-exclusion"></a>Supprimer une exclusion de dossier Automation

1. Dans le volet de navigation, sélectionnez **Les exclusions** de **dossiers** Paramètres \> **de points de terminaison** \> **Rules** \> Automation.
2. Cliquez sur **Supprimer l’exclusion**.

## <a name="related-topics"></a>Voir aussi

- [Gérer les listes d’automatisation autorisées/bloquées](manage-indicators.md)
- [Gérer les chargements du fichier d’automatisation](manage-automation-file-uploads.md)
