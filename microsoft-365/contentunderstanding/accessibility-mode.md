---
title: Mode d’accessibilité dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.service: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment utiliser le mode fonctionnalités d’accessibilité lors de l’entraînement et de l’utilisation de modèles dans Microsoft Syntex.
ms.openlocfilehash: b3571118fe409e04140f9e45cb77e43ea7e45aca
ms.sourcegitcommit: ca082da1c51a3f643f152492579eef5679d52bd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68547377"
---
# <a name="accessibility-mode-in-microsoft-syntex"></a>Mode d’accessibilité dans Microsoft Syntex

Dans [Microsoft Syntex](index.md), les utilisateurs peuvent activer le mode d’accessibilité à toutes les étapes de l’entraînement du modèle (étiquette, apprentissage, test) lors de l’utilisation d’exemples de documents. L’utilisation du mode d’accessibilité peut aider les utilisateurs malvoyants à faciliter l’accessibilité au clavier à mesure qu’ils naviguent et étiquettent des éléments dans la visionneuse de documents.

Cela permet aux utilisateurs d’utiliser leurs claviers pour parcourir le texte dans la visionneuse de documents et entendre une narration des valeurs sélectionnées, mais aussi des actions (par exemple, l’étiquetage ou la suppression de l’étiquetage du texte sélectionné) ou des valeurs d’étiquette prédites lorsque vous entraînez le modèle avec d’autres exemples de documents. 


![Mode d’accessibilité.](../media/content-understanding/accessibility-mode.png)

## <a name="requirements"></a>Conditions requises

Pour entendre l’audio de la narration, veillez à activer [l’application Narrateur](https://support.microsoft.com/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1) dans vos paramètres du Narrateur sur votre système Windows 10.

![Activez le Narrateur.](../media/content-understanding/narrator-settings.png)

## <a name="labeling-for-keyboard-users"></a>Étiquetage pour les utilisateurs du clavier

Pour les utilisateurs du clavier qui utilisent le mode d’accessibilité, si vous étiquetez du texte dans un exemple de document dans la visionneuse, vous pouvez utiliser les touches suivantes :

- Onglet : Vous déplace vers l’avant et sélectionne le mot suivant.
- Tab + Maj : vous déplace vers l’arrière et sélectionne le mot précédent.
- Entrée : étiquette ou supprime une étiquette du mot sélectionné.
- Flèche droite : vous déplace vers l’avant à travers des caractères individuels dans un mot sélectionné.
- Flèche gauche : vous déplace vers l’arrière à travers des caractères individuels dans un mot sélectionné.

> [!NOTE]
> Si vous étiquetez plusieurs mots pour une seule étiquette, vous devez étiqueter chaque mot.


## <a name="narration"></a>Narration

Pour les utilisateurs du Narrateur qui utilisent le mode d’accessibilité, utilisez la même navigation au clavier que celle décrite pour que les utilisateurs du clavier passent par l’exemple de document dans la visionneuse.

Lorsque vous parcourez les exemples de documents et les valeurs de chaîne d’étiquette, le Narrateur donne aux utilisateurs les invites audio suivantes :

- Lorsque vous utilisez le clavier pour parcourir la visionneuse de documents, l’audio du Narrateur indique la chaîne sélectionnée.
- Dans une chaîne sélectionnée, l’audio du Narrateur indique chaque caractère de la chaîne lorsque vous les sélectionnez à l’aide des touches de direction gauche ou droite.
- Si vous sélectionnez une chaîne étiquetée, le Narrateur indique la valeur, puis « étiqueté ».  Par exemple, si la valeur d’étiquette est « Contoso », elle indique « Costoso étiqueté ». 
- Dans l’onglet Formation, si vous sélectionnez une chaîne dans la visionneuse de documents qui n’a été prédite que, l’audio du Narrateur indique la valeur, puis « prédit ». Cela se produit lorsque l’entraînement prédit une valeur dans le fichier qui ne correspond pas à ce qui a été étiqueté par l’utilisateur.
- Dans l’onglet Formation, si vous sélectionnez une chaîne dans la visionneuse de documents qui a été étiquetée et prédite, l’audio du Narrateur indique la valeur, puis « étiqueté et prédit ». Cela se produit lorsque l’entraînement réussit et qu’il existe une correspondance entre une valeur prédite et l’étiquette utilisateur.

Une fois qu’une chaîne est étiquetée ou qu’une étiquette a été supprimée dans la visionneuse, l’audio du Narrateur vous avertit d’enregistrer vos modifications avant de quitter.

## <a name="see-also"></a>Voir aussi

[Créer un extracteur](create-an-extractor.md)

[Créer un classificateur](create-a-classifier.md)










 


  
  



