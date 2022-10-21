---
title: Appliquer une étiquette de confidentialité à un modèle dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment appliquer une étiquette de confidentialité à un modèle dans Microsoft Syntex.
ms.openlocfilehash: b38cbdd23270a16a7f912fe78dff920c670cfe95
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68660882"
---
# <a name="apply-a-sensitivity-label-to-a-model-in-microsoft-syntex"></a>Appliquer une étiquette de confidentialité à un modèle dans Microsoft Syntex

<sup>**S’applique à :**  &ensp; &#10003; traitement de documents non structurés</sup>

Vous pouvez facilement appliquer une [étiquette de confidentialité](../compliance/sensitivity-labels.md) aux modèles de traitement de documents non structurés dans Microsoft Syntex. 

> [!Note]
> Les étiquettes de confidentialité ne sont pas encore disponibles pour les modèles prédéfinis ou pour les modèles de traitement de documents structurés ou de forme libre.

Les étiquettes de confidentialité vous permettent d’appliquer le chiffrement aux documents identifiés par vos modèles. Par exemple, vous souhaitez que votre modèle identifie non seulement les documents financiers qui contiennent des numéros de compte bancaire ou de carte de crédit chargés dans votre bibliothèque de documents, mais également qu’il applique une étiquette de confidentialité configurée avec des paramètres de chiffrement pour restreindre les personnes autorisées à accéder à ce contenu et la façon dont il peut être utilisé. Les modèles Syntex respectent les règles [d’ordre des étiquettes](../compliance/apply-sensitivity-label-automatically.md#how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label) et ne remplacent pas non plus une étiquette existante qui a été appliquée manuellement par un utilisateur au fichier. 

Vous pouvez appliquer une étiquette de confidentialité préexistante à votre modèle via les paramètres du modèle sur la page d’accueil de celui-ci. L’étiquette doit déjà être publiée pour pouvoir être sélectionnée dans les paramètres du modèle. Les étiquettes s’appliquent aux fichiers Office pour Word (.docx), PowerPoint (.pptx) et Excel (.xlsx). 

> [!Important]
> Pour que les étiquettes de confidentialité soient disponibles pour s’appliquer à vos modèles, elles doivent être [créées et publiées dans le portail de conformité Microsoft Purview](../admin/security-and-compliance/set-up-compliance.md).

## <a name="add-a-sensitivity-label-to-a-model"></a>Ajouter une étiquette de confidentialité à un modèle

1. Sur la page d’accueil du modèle, sélectionnez **Paramètres du modèle**.

   ![Capture d’écran de la page Modèles avec l’option Paramètres du modèle mise en évidence.](../media/content-understanding/sensitivity-model-settings.png)

2. Dans le volet **Paramètres du modèle**, dans la section **Conformité**, sélectionnez le menu **Étiquette de confidentialité** pour afficher la liste des étiquettes de confidentialité que vous pouvez appliquer au modèle.

   ![Capture d’écran du volet Paramètres du modèle montrant le menu d’étiquette de confidentialité.](../media/content-understanding/sensitivity-model-settings-pane.png) 

3. Sélectionnez l’étiquette de confidentialité que vous souhaitez appliquer au modèle, puis **Enregistrer**.

Après avoir appliqué l’étiquette de confidentialité à votre modèle, vous pouvez l’appliquer à une :

- nouvelle bibliothèque de documents
- bibliothèque de documents à laquelle le modèle est déjà appliqué
 
### <a name="apply-the-sensitivity-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Appliquer l’étiquette de confidentialité à une bibliothèque de documents à laquelle le modèle est déjà appliqué

Si votre modèle a déjà été appliqué à une bibliothèque de documents, vous pouvez effectuer les opérations suivantes pour synchroniser la mise à jour de votre étiquette de confidentialité afin de l’appliquer à la bibliothèque de documents :

1. Sur la page d’accueil du modèle, dans la section **Bibliothèques avec ce modèle**, sélectionnez la bibliothèque de documents à laquelle vous souhaitez appliquer la mise à jour de l’étiquette de confidentialité.

2. Sélectionnez **Synchroniser**.

   ![Capture d’écran montrant les bibliothèques avec cette section de modèle avec La synchronisation mise en surbrillance.](../media/content-understanding/sensitivity-libraries-sync.png)

Après avoir appliqué la mise à jour et l'avoir synchronisée avec votre modèle, vous pouvez confirmer qu'elle a été appliquée en procédant comme suit :

1. Dans le centre de contenu, dans la section **Bibliothèques avec ce modèle**, sélectionnez la bibliothèque à laquelle votre modèle mis à jour a été appliqué. 

2. Dans l’affichage de votre bibliothèque de documents, sélectionnez l’icône Information pour vérifier les propriétés du modèle.

3. Dans la liste **Modèles actifs**, sélectionnez votre modèle mis à jour.

4. Dans la section **Étiquette de confidentialité**, vous verrez le nom de l’étiquette de confidentialité appliquée.

Sur la page d’affichage de votre modèle, dans votre bibliothèque de documents, une nouvelle colonne **Étiquette de confidentialité** s’affiche. Lorsque votre modèle classe les fichiers qu’il identifie comme appartenant à son type de contenu et les répertorie dans l’affichage de la bibliothèque, la colonne **Éiquette de confidentialité** affiche également le nom de l’étiquette de confidentialité qui lui a été appliquée via le modèle.

Par exemple, tous les documents financiers identifiés par votre modèle auront également l’étiquette de confidentialité *Chiffrement* appliquée, ce qui les empêchera d’être accessibles par des personnes non autorisées. Si une personne non autorisée tente d’accéder au fichier à partir de la bibliothèque de documents, une erreur s’affiche indiquant qu’il n’est pas autorisé en raison de l’étiquette de confidentialité appliquée.

## <a name="see-also"></a>Voir aussi

[Appliquer une autre étiquette de rétention](apply-a-retention-label-to-a-model.md)

