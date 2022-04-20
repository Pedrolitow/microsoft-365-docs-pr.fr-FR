---
title: Correction d’erreur sur élément unique
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Vous pouvez corriger une erreur de traitement dans un document d’un jeu de révision dans eDiscovery (Premium) sans avoir à suivre le processus de correction des erreurs en bloc.
ms.openlocfilehash: d3b90f0f2d396b6304bb85b46bc5b018802101eb
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993993"
---
# <a name="single-item-error-remediation-in-ediscovery-premium"></a>Correction des erreurs d’élément unique dans eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

La correction des erreurs permet aux utilisateurs de Microsoft Purview eDiscovery (Premium) de corriger les problèmes de données qui empêchent eDiscovery (Premium) de traiter correctement le contenu. Par exemple, les fichiers protégés par mot de passe ne peuvent pas être traités, car ces fichiers sont verrouillés ou chiffrés. Auparavant, vous ne pouviez corriger les erreurs en bloc qu’à l’aide de [ce flux de travail](error-remediation-when-processing-data-in-advanced-ediscovery.md). Mais parfois, il n’est pas judicieux de corriger les erreurs dans plusieurs fichiers lorsque vous ne savez pas si l’un de ces fichiers répond au cas que vous examinez. Il peut également ne pas être judicieux de corriger les erreurs avant que vous ayez eu l’occasion de passer en revue les métadonnées de fichier (par exemple, l’emplacement du fichier ou qui avaient accès) pour vous aider à prendre des décisions préalables en matière de réactivité. Une nouvelle fonctionnalité appelée *correction d’erreur d’élément unique* permet aux gestionnaires eDiscovery d’afficher les métadonnées des fichiers avec une erreur de traitement et, si nécessaire, de corriger l’erreur directement dans le jeu de révision. L’article explique comment identifier, ignorer et corriger des fichiers avec des erreurs de traitement dans un ensemble de révisions.

## <a name="identify-documents-with-errors"></a>Identifier les documents avec des erreurs

Les documents avec des erreurs de traitement dans un jeu de révision sont désormais identifiés (avec une bannière). Vous pouvez corriger ou ignorer l’erreur. La capture d’écran suivante montre la bannière d’erreur de traitement d’un document Word dans un jeu de révision protégé par mot de passe. Notez également que vous pouvez afficher les métadonnées de fichier des documents avec des erreurs de traitement.

![Bannière affichée pour le document avec erreur de traitement.](../media/SIERimage1.png)

Vous pouvez également rechercher des documents qui ont des erreurs de traitement à l’aide de la condition **d’état de** traitement lors [de l’interrogation des documents dans un jeu de révision](review-set-search.md).

![Utilisez la condition d’état de traitement pour rechercher des documents d’erreur.](../media/SIERimage2.png)

### <a name="ignore-errors"></a>Ignorer les erreurs

Vous pouvez ignorer une erreur de traitement en cliquant sur **Ignorer** dans la bannière d’erreur de traitement. Lorsque vous ignorez une erreur, le document est supprimé du [flux de travail de correction des erreurs en bloc](error-remediation-when-processing-data-in-advanced-ediscovery.md). Une fois qu’une erreur est ignorée, la bannière de document change de couleur et indique que l’erreur de traitement a été ignorée. À tout moment, vous pouvez annuler la décision d’ignorer l’erreur en cliquant sur **Rétablir**.

![Cliquez sur Ignorer pour ignorer l’erreur de traitement.](../media/SIERimage3.png)

Vous pouvez également rechercher tous les documents qui avaient une erreur de traitement qui a été ignorée à l’aide de la condition *d’erreurs de traitement ignorée* lors de l’interrogation de documents dans un jeu de révision.

![Utilisez la condition d’erreurs de traitement ignorée pour rechercher les documents d’erreur ignorés.](../media/SIERimage4.png)

## <a name="remediate-a-document-with-errors"></a>Corriger un document avec des erreurs

Il peut arriver que vous deviez corriger une erreur de traitement dans des documents (en supprimant un mot de passe, en déchiffrant un fichier chiffré ou en récupérant un document endommagé), puis en ajoutez le document corrigé au jeu de révisions. Cela vous permet d’examiner et d’exporter le document d’erreur avec les autres documents du jeu de révision. 

Pour corriger un document unique, procédez comme suit :

1. Cliquez sur **DownloadDownload**  >  original pour télécharger une copie du fichier sur un ordinateur local.

   ![Téléchargez le document avec l’erreur de traitement.](../media/SIERimage5.png)

2. Corrigez l’erreur dans le fichier hors connexion. Pour les fichiers chiffrés, qui nécessitent un logiciel de déchiffrement, pour supprimer la protection par mot de passe, fournissez le mot de passe et enregistrez le fichier ou utilisez un pirate de mot de passe. Après avoir corriger le fichier, passez à l’étape suivante.

3. Dans le jeu de révision, sélectionnez le fichier avec l’erreur de traitement que vous avez corrigée, puis cliquez sur **Correction**.

   ![Cliquez sur Correction dans la bannière du document avec une erreur de traitement.](../media/SIERimage6.png)


4. Cliquez sur **Parcourir**, accédez à l’emplacement du fichier corrigé sur votre ordinateur local, puis sélectionnez le fichier.

   ![Cliquez sur Parcourir et sélectionnez le fichier corrigé sur votre ordinateur local.](../media/SIERimage7.png)

    Après avoir sélectionné le fichier corrigé, il est automatiquement chargé dans le jeu de révisions. Vous pouvez suivre l’état de traitement du fichier.

    ![L’état du processus de correction s’affiche.](../media/SIERimage8.png)

   Une fois le traitement terminé, vous pouvez afficher le document corrigé.

    ![Vous pouvez afficher le fichier corrigé au format natif dans l’ensemble de révisions.](../media/SIERimage9.png)

Pour plus d’informations sur ce qui se passe lorsqu’un document est corrigé, consultez [Ce qui se passe quand des fichiers sont corrigés](error-remediation-when-processing-data-in-advanced-ediscovery.md#what-happens-when-files-are-remediated).

## <a name="search-for-remediated-documents"></a>Rechercher des documents corrigés

Vous pouvez rechercher tous les documents d’un jeu de révision qui ont été corrigés à l’aide de la condition **Keywords** et en spécifiant la paire property:value suivante : **IsFromErrorRemediation:true**. Cette propriété est également disponible dans le fichier de chargement d’exportation lorsque vous exportez des documents à partir d’un ensemble de révisions.
