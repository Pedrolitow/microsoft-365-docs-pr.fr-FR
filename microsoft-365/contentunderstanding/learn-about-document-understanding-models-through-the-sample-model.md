---
title: En savoir plus sur les modèles de présentation des documents via le modèle d’échantillon
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: Priority
description: En savoir plus sur les modèles de présentation des documents via le modèle d’échantillon
ms.openlocfilehash: 75e17c8075fa381c68b6f85e0dfbe96e5d2ad557
ms.sourcegitcommit: f7ca339bdcad38796c550064fb152ea09687d0f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "48321264"
---
# <a name="learn-about-document-understanding-models-through-a-sample-model"></a>En savoir plus sur les modèles de présentation des documents via un modèle d’échantillon

Microsoft SharePoint Syntex offre un exemple de modèle permettant de mieux comprendre comment créer vos propres modèles. Ce modèle d’échantillon vous permet également d’examiner les composants du modèle, tels que son classifieur, ses extracteurs et ses explications. Vous pouvez également utiliser les fichiers échantillons pour former le modèle.

## <a name="import-the-sample-model"></a>Importer le modèle d’échantillon

Avant d’accéder au modèle d’échantillon, vous devez l’importer dans votre centre de contenu.

1. Dans le centre de contenu, sélectionnez **Modèles** pour afficher votre liste de modèles.</br>
2. Dans la page **Modèles**, sélectionnez **Importer un modèle d’échantillon**.</br>

    ![Importer un modèle d’échantillon](../media/content-understanding/import-sample-model.png) </br>

3. Une fois l’importation terminée, la page d’accueil du modèle **BenefitsChangeNotice** s’ouvre. Si vous devez ouvrir le modèle d’échantillon ultérieurement, vous pouvez, pour cela, utiliser la liste des modèles dans le centre de contenu. </br>

     ![Page d'accueil Échantillon](../media/content-understanding/sample-home-page.png)</br>

Vous ne pouvez pas seulement examiner et analyser le modèle d’échantillon pour mieux comprendre sa structure. Il sert également, en tant que modèle de travail, à effectuer des actions comme :

- Ajouter un autre extracteur. Par exemple, ajoutez-en un qui extrait les *taux d’escompte*.
- Appliquez le modèle à une bibliothèque de documents, puis chargez certains fichiers de formation vers celle-ci. Vous saurez ainsi comment le modèle classe les fichiers et en extrait les données.


## <a name="see-also"></a>Voir aussi
[Créer un classifieur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)

[Présentation de la compréhension de document](document-understanding-overview.md)

[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)  
