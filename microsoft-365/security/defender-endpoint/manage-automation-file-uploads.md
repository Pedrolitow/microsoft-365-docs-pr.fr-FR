---
title: Gérer les chargements du fichier d’automatisation
description: Activer l’analyse de contenu et configurer l’extension de fichier et les extensions de pièce jointe de courrier électronique qui seront soumises à l’analyse
keywords: automation, fichier, téléchargements, contenu, analyse, fichier, extension, e-mail, pièce jointe
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 6472414b2e27bbdf42f2b9508f2aff18387c0547
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60152009"
---
# <a name="manage-automation-file-uploads"></a>Gérer les chargements du fichier d’automatisation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationefileuploads-abovefoldlink)

Activez la fonctionnalité d’analyse de contenu afin que certains fichiers et pièces jointes de courrier électronique soient automatiquement téléchargés vers le cloud pour une inspection supplémentaire dans l’examen automatisé.

Identifiez les fichiers et les pièces jointes en spécifiant les noms d’extension de fichier et les noms d’extension de pièce jointe de courrier électronique.

Par exemple, si vous ajoutez *exe* et *bat* en tant que noms d’extension de fichier ou de pièce jointe, tous les fichiers ou pièces jointes avec ces extensions seront automatiquement envoyés dans le cloud pour une inspection supplémentaire au cours de l’examen automatisé.

## <a name="add-file-extension-names-and-attachment-extension-names"></a>Ajoutez des noms d’extension de fichier et des noms d’extension de pièce jointe.

1. Dans le volet de navigation, sélectionnez **Paramètres** \> **les chargements de Endpoints** \> **Rules** \> **Automation.**

2. Basculez le paramètre d’analyse de contenu entre **Le et** **Le.**

3. Configurez les noms d’extension suivants et séparez les noms d’extension par une virgule :
   - **Noms d’extension de fichier** : les fichiers suspects, à l’exception des pièces jointes, seront envoyés pour inspection supplémentaire

## <a name="related-topics"></a>Rubriques connexes

- [Gérer les exclusions du dossier d’automatisation](manage-automation-folder-exclusions.md)
