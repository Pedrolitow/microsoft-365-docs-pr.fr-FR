---
title: Gérer les chargements du fichier d’automatisation
description: Activer l’analyse de contenu et configurer l’extension de fichier et les extensions de pièce jointe de courrier électronique qui seront soumises pour analyse
keywords: automation, fichier, chargements, contenu, analyse, fichier, extension, e-mail, pièce jointe
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.openlocfilehash: 67c5e6bfb03fd38a8f55482c4debd69dd25e8000
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67521178"
---
# <a name="manage-automation-file-uploads"></a>Gérer les chargements du fichier d’automatisation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationefileuploads-abovefoldlink)

Activez la fonctionnalité d’analyse de contenu afin que certains fichiers et pièces jointes d’e-mail puissent être automatiquement chargés dans le cloud pour une inspection supplémentaire dans l’examen automatisé.

Identifiez les fichiers et les pièces jointes d’e-mail en spécifiant les noms d’extension de fichier et les noms d’extension de pièce jointe.

Par exemple, si vous ajoutez *exe* et *bat* en tant que noms d’extension de fichier ou de pièce jointe, tous les fichiers ou pièces jointes avec ces extensions sont automatiquement envoyés au cloud pour une inspection supplémentaire pendant l’examen automatisé.

## <a name="add-file-extension-names-and-attachment-extension-names"></a>Ajoutez des noms d’extension de fichier et des noms d’extension de pièce jointe.

1. Dans le volet de navigation, sélectionnez **Paramètres des** \> **points de terminaison chargés** \> par **Rules** \> **Automation**.

2. Activez **et** **désactivez** le paramètre d’analyse de contenu.

3. Configurez les noms d’extension suivants et séparez les noms d’extension par une virgule :
   - **Noms d’extension** de fichier : les fichiers suspects, à l’exception des pièces jointes, seront soumis pour une inspection supplémentaire

## <a name="related-topics"></a>Voir aussi

- [Gérer les exclusions du dossier d’automatisation](manage-automation-folder-exclusions.md)
