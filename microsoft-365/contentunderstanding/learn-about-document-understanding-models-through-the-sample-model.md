---
title: Importer un exemple de modèle pour Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.custom: intro-get-started
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez les modèles de traitement de documents non structurés dans Microsoft Syntex à l’aide de l’exemple de modèle.
ms.openlocfilehash: 1cc865ba121be342821999924a31d1ba8082bd94
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68659562"
---
# <a name="import-a-sample-model-for-microsoft-syntex"></a>Importer un exemple de modèle pour Microsoft Syntex

Microsoft Syntex vous fournit un exemple de modèle de traitement de document non structuré que vous pouvez utiliser pour examiner, ce qui vous permet de mieux comprendre comment créer vos propres modèles. Ce modèle d’échantillon vous permet également d’examiner les composants du modèle, tels que son classifieur, ses extracteurs et ses explications. Vous pouvez également utiliser les fichiers échantillons pour former le modèle.

## <a name="import-the-sample-model"></a>Importer le modèle d’échantillon

Avant d’accéder au modèle d’échantillon, vous devez l’importer dans votre centre de contenu.

1. Dans le centre de contenu, sélectionnez **Modèles** pour afficher votre liste de modèles.

2. Dans la page **Modèles**, sélectionnez **Importer un modèle d’échantillon**.

    ![Importer un modèle d’échantillon.](../media/content-understanding/import-sample-model.png) 

3. Une fois l’importation terminée, la page d’accueil du modèle **BenefitsChangeNotice** s’ouvre. Si vous devez ouvrir l’exemple de modèle à l’avenir, vous pouvez l’ouvrir à partir de la liste des modèles dans le centre de contenu.

    ![Page d'accueil Échantillon.](../media/content-understanding/sample-home-page.png)

Non seulement vous pouvez examiner l’analyse de l’exemple de modèle pour mieux comprendre la façon dont le modèle est construit, mais en tant que modèle opérationnel, vous pouvez aller plus loin et faire des choses telles que :

- Ajoutez un autre extracteur. Par exemple, ajoutez-en un qui extrait les *taux d’escompte*.

- Appliquez le modèle à une bibliothèque de documents, puis chargez certains fichiers de formation vers celle-ci. Vous saurez ainsi comment le modèle classe les fichiers et en extrait les données.

## <a name="get-sample-models"></a>Obtenir des exemples de modèles

Vous pouvez accéder au [référentiel d’exemples Syntex](https://github.com/pnp/syntex-samples), qui contient des exemples de communauté qui illustrent différents modèles d’utilisation des modèles de traitement de documents non structurés. Les exemples de ce référentiel contiennent à la fois les fichiers de modèle et les fichiers utilisés pour entraîner le modèle. Une fois importés, vous pouvez utiliser ces modèles pour traiter des fichiers et pour afficher et modifier le classifieur et les extracteurs.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du traitement de documents non structurés](document-understanding-overview.md)

[Créer un classifieur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)