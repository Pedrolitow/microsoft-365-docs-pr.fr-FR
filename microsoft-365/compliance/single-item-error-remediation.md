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
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Vous pouvez corriger une erreur de traitement dans un document dans un groupe de révision dans Advanced eDiscovery sans avoir à suivre le processus de correction des erreurs en bloc.
ms.openlocfilehash: 038be8d60851dcbd14452d293bad29be4f9de3f8b4c86aab6e7ee7e905b2d13a
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53830567"
---
# <a name="single-item-error-remediation-in-advanced-ediscovery"></a>Correction des erreurs d’élément unique Advanced eDiscovery

La correction des Advanced eDiscovery permet aux utilisateurs de corriger les problèmes de données qui empêchent Advanced eDiscovery traiter correctement le contenu. Par exemple, les fichiers protégés par mot de passe ne peuvent pas être traitées, car ces fichiers sont verrouillés ou chiffrés. Auparavant, vous pouviez uniquement corriger les erreurs en bloc à l’aide [de ce flux de travail.](error-remediation-when-processing-data-in-advanced-ediscovery.md) Mais parfois, il n’est pas logique de corriger les erreurs dans plusieurs fichiers lorsque vous ne savez pas si l’un de ces fichiers répond au cas que vous examinez. Il peut également ne pas être utile de corriger les erreurs avant d’avoir eu la possibilité de passer en revue les métadonnées de fichier (par exemple, l’emplacement du fichier ou les personnes ayant accès) pour vous aider à prendre des décisions à l’avance en matière de réactivité. Une nouvelle  fonctionnalité appelée correction d’erreur d’élément unique permet aux gestionnaires eDiscovery d’afficher les métadonnées des fichiers avec une erreur de traitement et, si nécessaire, de corriger l’erreur directement dans le jeu à réviser. L’article explique comment identifier, ignorer et corriger les fichiers avec des erreurs de traitement dans un jeu à réviser.

## <a name="identify-documents-with-errors"></a>Identifier les documents avec des erreurs

Les documents avec des erreurs de traitement dans un jeu à réviser sont désormais identifiés (avec une bannière). Vous pouvez corriger ou ignorer l’erreur. La capture d’écran suivante montre la bannière d’erreur de traitement d’un document Word dans un jeu à réviser protégé par mot de passe. Notez également que vous pouvez afficher les métadonnées de fichier des documents avec des erreurs de traitement.

![Bannière affichée pour le document avec erreur de traitement](../media/SIERimage1.png)

Vous pouvez également rechercher des documents qui ont des erreurs de traitement à l’aide de la **condition** d’état de traitement lors de l’interrogation des documents dans un jeu [à réviser.](review-set-search.md)

![Utiliser la condition d’état de traitement pour rechercher des documents d’erreur](../media/SIERimage2.png)

### <a name="ignore-errors"></a>Ignorer les erreurs

Vous pouvez ignorer une erreur de traitement en cliquant sur **Ignorer** dans la bannière d’erreur de traitement. Lorsque vous ignorez une erreur, le document est supprimé du flux de travail de correction des [erreurs en bloc.](error-remediation-when-processing-data-in-advanced-ediscovery.md) Une fois qu’une erreur est ignorée, la bannière de document change de couleur et indique que l’erreur de traitement a été ignorée. À tout moment, vous pouvez revenir à la décision d’ignorer l’erreur en cliquant sur **Revert**.

![Cliquez sur Ignorer pour ignorer l’erreur de traitement](../media/SIERimage3.png)

Vous pouvez également rechercher tous les documents dont l’erreur de traitement a été ignorée à l’aide de la *condition* d’erreurs de traitement ignorée lors de l’interrogation de documents dans un jeu à réviser.

![Utiliser la condition Des erreurs de traitement ignorées pour rechercher des documents d’erreur ignorés](../media/SIERimage4.png)

## <a name="remediate-a-document-with-errors"></a>Corriger un document avec des erreurs

Parfois, il peut vous être demandé de corriger une erreur de traitement dans les documents (en supprimant un mot de passe, en déchiffrant un fichier chiffré ou en récupérant un document endommagé), puis d’ajouter le document corrigé au jeu à réviser. Cela vous permet de consulter et d’exporter le document d’erreurs avec les autres documents du jeu à réviser. 

Pour corriger un document unique, suivez les étapes suivantes :

1. Cliquez **sur Télécharger**  >  **l’original** pour télécharger une copie du fichier sur un ordinateur local.

   ![Télécharger le document avec l’erreur de traitement](../media/SIERimage5.png)

2. Corriger l’erreur dans le fichier hors connexion. Pour les fichiers chiffrés, qui nécessitent un logiciel de déchiffrement, pour supprimer la protection par mot de passe, fournissez le mot de passe et enregistrez le fichier ou utilisez un logiciel de déchiffrement de mot de passe. Après avoir corrigé le fichier, allez à l’étape suivante.

3. Dans le jeu à réviser, sélectionnez le fichier avec l’erreur de traitement que vous avez corrigé, puis cliquez sur **Correction.**

   ![Cliquez sur Correction dans la bannière du document avec erreur de traitement](../media/SIERimage6.png)


4. Cliquez **sur** Parcourir, accédez à l’emplacement du fichier corrigé sur votre ordinateur local, puis sélectionnez le fichier.

   ![Cliquez sur Parcourir et sélectionnez le fichier corrigé sur votre ordinateur local](../media/SIERimage7.png)

    Après avoir sélectionné le fichier corrigé, il est automatiquement chargé dans le jeu à réviser. Vous pouvez suivre l’état de traitement du fichier.

    ![L’état du processus de correction s’affiche](../media/SIERimage8.png)

   Une fois le traitement terminé, vous pouvez afficher le document corrigé.

    ![Vous pouvez afficher le fichier corrigé au format natif dans le jeu à réviser](../media/SIERimage9.png)

Pour plus d’informations sur ce qui se produit lorsqu’un document est corrigé, voir Ce qui se produit [lorsque des fichiers sont corrigés.](error-remediation-when-processing-data-in-advanced-ediscovery.md#what-happens-when-files-are-remediated)

## <a name="search-for-remediated-documents"></a>Rechercher des documents corrigés

Vous pouvez rechercher tous les documents d’un jeu à réviser qui ont été corrigés à l’aide de la condition **Keywords** et en spécifiant la paire property:value suivante : **IsFromErrorRemediation:true**. Cette propriété est également disponible dans le fichier de chargement d’exportation lorsque vous exportez des documents à partir d’un jeu à réviser.
