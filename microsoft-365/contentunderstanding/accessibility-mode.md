---
title: 'Mode d’accessibilité syntex SharePoint '
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: Normal
description: Découvrez comment utiliser le mode d’accessibilité lors de la formation d’un modèle dans SharePoint Syntex.
ms.openlocfilehash: 32e5bd132a7a0145f03e4620545d65d1d92ff223
ms.sourcegitcommit: d354727303d9574991b5a0fd298d2c9414e19f6c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2021
ms.locfileid: "50081006"
---
# <a name="sharepoint-syntex-accessibility-mode"></a>Mode d’accessibilité syntex SharePoint

Dans [SharePoint Syntex,](index.md)les utilisateurs peuvent activer le mode accessibilité à toutes les étapes de la formation au modèle (étiquette, formation, test) lorsque vous travaillez avec des exemples de documents. L’utilisation du mode d’accessibilité permet aux utilisateurs à faible vue d’avoir plus facilement accès au clavier à mesure qu’ils naviguent et étiquetent des éléments dans la visionneuse de documents.

Cela permet aux utilisateurs d’utiliser leur clavier pour naviguer dans le texte de la visionneuse de documents et écouter une narration non seulement des valeurs sélectionnées, mais aussi des actions (telles que l’étiquetage ou la suppression de l’étiquetage du texte sélectionné) ou des valeurs d’étiquette prévues lorsque vous formez le modèle avec des exemples de documents supplémentaires. 


![Mode d’accessibilité](../media/content-understanding/accessibility-mode.png)

## <a name="requirements"></a>Configuration requise

Pour écouter l’audio de la narration, veillez à activer l’application [Narrateur](https://support.microsoft.com/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1) dans les paramètres du Narrateur sur votre système Windows 10.

![Activer le Narrateur](../media/content-understanding/narrator-settings.png)

## <a name="labeling-for-keyboard-users"></a>Étiquetage pour les utilisateurs du clavier

Pour les utilisateurs du clavier qui utilisent le mode d’accessibilité, si vous étiquetez du texte dans un exemple de document dans la visionneuse, vous pouvez utiliser les touches suivantes :

- Tabulation : vous déplace vers l’avant et sélectionne le mot suivant.
- Tab + Shift : vous déplace vers l’arrière et sélectionne le mot précédent.
- Entrée : étiquette ou supprime une étiquette du mot sélectionné.
- Flèche avant : vous déplace vers l’avant à travers des caractères individuels dans un mot sélectionné.
- Flèche vers l’arrière : vous déplace vers l’arrière à travers des caractères individuels dans un mot sélectionné.

> [!NOTE]
> Si vous étiquetez plusieurs mots pour une seule étiquette, vous devez étiqueter chaque mot.


## <a name="narration"></a>Narration

Pour les utilisateurs du Narrateur qui utilisent le mode d’accessibilité, utilisez la même navigation au clavier que les utilisateurs du clavier pour passer par l’exemple de document dans la visionneuse.

Lorsque vous parcourez les exemples de documents et les valeurs de chaîne d’étiquette, le Narrateur donne à l’utilisateur les invites audio suivantes :

- Lorsque vous utilisez le clavier pour naviguer dans la visionneuse de documents, l’audio du Narrateur indique la chaîne sélectionnée.
- Dans une chaîne sélectionnée, l’audio du Narrateur indique chaque caractère de la chaîne lorsque vous les sélectionnez à l’aide de la flèche avant ou arrière.
- Si vous sélectionnez une chaîne qui a été étiquetée, le Narrateur indique la valeur, puis « étiquetée ».  Par exemple, si la valeur de l’étiquette est « Contoso », elle indique « Labeled Costoso ». 
- Dans l’onglet formation, si vous sélectionnez une chaîne dans la visionneuse de documents qui n’a été prévue que, l’audio du Narrateur indique la valeur, puis « prévue ». Cela se produit lorsque la formation prévoit une valeur dans le fichier qui ne correspond pas à ce qui a été étiqueté par l’utilisateur.
- Dans l’onglet Formation, si vous sélectionnez une chaîne dans la visionneuse de documents qui a été étiquetée et prévue, l’audio du Narrateur indique la valeur, puis « étiqueté et prévu ». Cela se produit lorsque la formation réussit et qu’il existe une correspondance entre une valeur prévue et l’étiquette de l’utilisateur.



Une fois qu’une chaîne est étiquetée ou qu’une étiquette a été supprimée dans la visionneuse, l’audio du Narrateur vous avertit d’enregistrer vos modifications avant de quitter.

## <a name="see-also"></a>Voir aussi

[Créer un extracteur](create-an-extractor.md)</br>

[Créer un classificateur](create-a-classifier.md)</br>










 


  
  



