---
title: Importer un exemple de modèle de compréhension de document pour Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.custom: intro-get-started
ms.service: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez les modèles de présentation des documents via le modèle d’échantillon.
ms.openlocfilehash: 06f38e44162b5091607281c9aa34ce7dc721b647
ms.sourcegitcommit: ca082da1c51a3f643f152492579eef5679d52bd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68547486"
---
# <a name="import-a-sample-document-understanding-model-for-microsoft-syntex"></a>Importer un exemple de modèle de compréhension de document pour Microsoft Syntex

Microsoft Syntex vous fournit un exemple de modèle que vous pouvez utiliser pour examiner, ce qui vous permet de mieux comprendre comment créer vos propres modèles. Ce modèle d’échantillon vous permet également d’examiner les composants du modèle, tels que son classifieur, ses extracteurs et ses explications. Vous pouvez également utiliser les fichiers échantillons pour former le modèle.

## <a name="import-the-sample-model"></a>Importer le modèle d’échantillon

Avant d’accéder au modèle d’échantillon, vous devez l’importer dans votre centre de contenu.

1. Dans le centre de contenu, sélectionnez **Modèles** pour afficher votre liste de modèles.</br>
2. Dans la page **Modèles**, sélectionnez **Importer un modèle d’échantillon**.</br>

    ![Importer un modèle d’échantillon.](../media/content-understanding/import-sample-model.png) </br>

3. Une fois l’importation terminée, la page d’accueil du modèle **BenefitsChangeNotice** s’ouvre. Si vous devez ouvrir le modèle d’échantillon ultérieurement, vous pouvez, pour cela, utiliser la liste des modèles dans le centre de contenu. </br>

     ![Page d'accueil Échantillon.](../media/content-understanding/sample-home-page.png)</br>

Vous ne pouvez pas seulement examiner et analyser le modèle d’échantillon pour mieux comprendre sa structure. Il sert également, en tant que modèle de travail, à effectuer des actions comme :

- Ajouter un autre extracteur. Par exemple, ajoutez-en un qui extrait les *taux d’escompte*.
- Appliquez le modèle à une bibliothèque de documents, puis chargez certains fichiers de formation vers celle-ci. Vous saurez ainsi comment le modèle classe les fichiers et en extrait les données.

## <a name="get-sample-models"></a>Obtenir des exemples de modèles

Vous pouvez accéder au [référentiel d’exemples Syntex](https://github.com/pnp/syntex-samples), qui contient des exemples de communauté qui illustrent différents modèles d’utilisation des modèles de compréhension des documents. Les exemples de ce référentiel contiennent à la fois les fichiers de modèle de compréhension de document et les fichiers utilisés pour entraîner le modèle. Une fois importés, vous pouvez utiliser ces modèles pour traiter des fichiers et afficher et modifier le classifieur et les extracteurs.

## <a name="see-also"></a>Voir aussi
[Créer un classifieur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)

[Présentation de la compréhension de document](document-understanding-overview.md)

[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)  
