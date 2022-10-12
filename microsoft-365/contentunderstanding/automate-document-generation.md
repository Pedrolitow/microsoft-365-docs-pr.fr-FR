---
title: Automatiser la génération de documents avec Microsoft Syntex et Power Automate (préversion)
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: anrasto, shrganguly
ms.topic: article
ms.service: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment créer automatiquement des documents et d’autres contenus à l’aide de Microsoft Syntex et Power Automate.
ms.openlocfilehash: 616a88bf7a6de912e731fb96bc4af2f856089de0
ms.sourcegitcommit: ca082da1c51a3f643f152492579eef5679d52bd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68547815"
---
# <a name="automate-document-generation-with-microsoft-syntex-and-power-automate-preview"></a>Automatiser la génération de documents avec Microsoft Syntex et Power Automate (préversion)

À l’aide de l’assembly de contenu dans Microsoft Syntex avec Power Automate, vous pouvez automatiser la génération de documents à l’aide de modèles modernes. 

Cette préversion est une action Power Automate dans un connecteur SharePoint. L’action est nommée « Générer un document à l’aide de Syntex (préversion) » et présente des fonctionnalités limitées pour la préversion. 

## <a name="scope-of-the-preview"></a>Étendue de la préversion 

L’étendue actuelle de la préversion vous permet d’effectuer les opérations suivantes :  

- Choisissez une liste SharePoint comme point de départ pour la génération de documents. Autrement dit, vous souhaitez qu’un document soit généré à l’aide des valeurs de la liste SharePoint une fois qu’un élément de la liste a été ajouté, modifié ou supprimé. 

- Choisissez un modèle moderne et associez ses champs aux colonnes de la liste SharePoint choisie. 

La préversion est créée et testée pour fonctionner pour les trois déclencheurs suivants dans SharePoint Connector :

- Lorsqu’un élément est créé
- Lorsqu’un élément est créé ou modifié
- Lorsqu’un élément est supprimé

## <a name="automate-document-generation"></a>Automatiser la génération de documents 

Suivez ces étapes pour générer automatiquement des documents à l’aide d’un modèle moderne et de Power Automate. 

1. Connectez-vous à Power Automate.

2. Dans le volet gauche, sélectionnez **Connecteurs**. Dans la zone de recherche, recherchez *SharePoint*, puis sélectionnez le connecteur **SharePoint** .

3. Dans la page du connecteur SharePoint, sélectionnez le déclencheur que vous souhaitez utiliser pour démarrer le processus de génération de document automatisé. 

    Nous vous recommandons de commencer par l’un des trois déclencheurs suivants :

    - Lorsqu’un élément est créé
    - Lorsqu’un élément est créé ou modifié
    - Lorsqu’un élément est supprimé

4. Ensuite, configurez le déclencheur en entrant l’adresse du site SharePoint et le nom de la liste SharePoint. Sélectionnez **Nouvelle étape**. 

   ![Capture d’écran du déclencheur When a document is created or modified showing a sample site address and site name.](../media/content-understanding/document-generation-trigger.png)

5. Sélectionnez à nouveau le connecteur SharePoint. Dans la zone de recherche, recherchez et sélectionnez l’action **Générer le document à l’aide de Syntex (préversion).**

   ![Capture d’écran de l’onglet Actions du connecteur SharePoint montrant l’action Générer un document à l’aide de Syntex (préversion).](../media/content-understanding/document-generation-action.png) 

6. Entrez les informations de site et sélectionnez la bibliothèque de documents qui contient le modèle moderne. 

7. Une fois le modèle sélectionné, vous commencerez à voir les champs du modèle. Associez les champs aux colonnes de la liste. 

    > [!NOTE]
    >Le mappage des données dans le modèle n’est pas pris en charge dans cette préversion. Par exemple, si vous avez associé un champ de votre modèle à une colonne de métadonnées managées, au cours de la génération automatisée, vous pourrez associer ce champ à une colonne d’une liste. 

8. Lorsque vous avez terminé, **sélectionnez Enregistrer** pour enregistrer le flux. 

    > [!NOTE]
    > Nous vous recommandons d’utiliser des modèles qui n’ont pas besoin que les utilisateurs ajoutent manuellement des valeurs pour la génération de documents. Si le modèle a besoin d’une entrée manuelle pour un champ, vous pouvez spécifier cette valeur par rapport au champ au lieu de la mapper à une colonne de liste SharePoint.<br><br> Actuellement, seuls les documents Word (.Docx) sont pris en charge à l’aide de cette action.  

## <a name="see-also"></a>Voir aussi

 [Créer des documents à l’aide d’un assembly de contenu dans Microsoft Syntex](content-assembly.md)
