---
title: Gérer les téléchargements de fichiers d’automatisation
description: Activer l’analyse de contenu et configurer l’extension de fichier et les extensions de pièce jointe de courrier électronique qui seront soumises à l’analyse
keywords: automation, fichier, téléchargements, contenu, analyse, fichier, extension, e-mail, pièce jointe
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
ms.openlocfilehash: 72405ad7500bf5d672f66ea64634e60c29ad1704
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51068873"
---
# <a name="manage-automation-file-uploads"></a>Gérer les téléchargements de fichiers d’automatisation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-automationefileuploads-abovefoldlink)

Activez la fonctionnalité d’analyse de contenu afin que certains fichiers et pièces jointes de courrier électronique soient automatiquement téléchargés vers le cloud pour une inspection supplémentaire dans l’examen automatisé.

Identifiez les fichiers et les pièces jointes en spécifiant les noms d’extension de fichier et les noms d’extension de pièce jointe de courrier électronique. 

Par exemple, si vous ajoutez *exe* et *bat* en tant que noms d’extension de fichier ou de pièce jointe, tous les fichiers ou pièces jointes avec ces extensions seront automatiquement envoyés dans le cloud pour une inspection supplémentaire au cours de l’examen automatisé. 

## <a name="add-file-extension-names-and-attachment-extension-names"></a>Ajoutez des noms d’extension de fichier et des noms d’extension de pièce jointe.

1. Dans le volet de navigation, sélectionnez **Téléchargements** de fichiers Settings  >  **Automation.** 

2. Basculez le paramètre d’analyse de contenu entre **Le et** **Le.**

3. Configurez les noms d’extension suivants et séparez les noms d’extension par une virgule :
   - **Noms d’extension de fichier** : les fichiers suspects, à l’exception des pièces jointes, seront envoyés pour inspection supplémentaire
  

## <a name="related-topics"></a>Voir aussi
- [Gérer les exclusions de dossiers d’automatisation](manage-automation-folder-exclusions.md)
