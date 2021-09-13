---
title: Créer un centre de contenu dans Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
localization_priority: Priority
description: Découvrez comment créer un centre de contenu dans Microsoft SharePoint Syntex.
ms.openlocfilehash: a50a31d29cc53a70a7e13f9cd83e76933aa39cf8
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59179835"
---
# <a name="create-a-content-center-in-microsoft-sharepoint-syntex"></a>Créer un centre de contenu dans Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CPSF]

</br>

Pour créer et gérer des modèles de présentation de documents, vous devez d’abord utiliser un centre de contenu. Le centre de contenu est l’interface de création de modèles et contient également des informations sur les bibliothèques de documents auxquelles les modèles publiés ont été appliqués.

   ![Sélectionnez une bibliothèque de documents.](../media/content-understanding/content-center-page.png)

Vous créez un centre de contenu par défaut lors de [l’installation](set-up-content-understanding.md). Mais un administrateur SharePoint peut également choisir de créer d’autres centres au besoin. Bien qu’il soit possible qu’un seul centre de contenu soit adapté aux environnements pour lesquels vous voulez regrouper toutes les activités du modèle, vous souhaiterez peut-être disposer de centres supplémentaires pour plusieurs services au sein de votre organisation, lesquels peuvent avoir des besoins et des autorisations différents pour leurs modèles.

En outre, si vous souhaitez essayer SharePoint Syntex, vous pouvez créer un centre de contenu à l’aide des instructions de cet article sans acheter de licences. Les utilisateurs sans licence peuvent créer des modèles de compréhension de document, mais ne peuvent pas les appliquer à une bibliothèque de documents.

> [!NOTE]
> Dans un [Microsoft 365 Multigéographie](../enterprise/microsoft-365-multi-geo.md), si vous avez un centre de contenu par défaut unique dans votre emplacement central, vous pouvez seulement fournir un suivi de l’activité du modèle à partir de cet emplacement. Vous ne pouvez pas actuellement obtenir de déploiement de l’activité de modèle au-delà des limites de la batterie de serveurs dans l’environnement multigéographique. 

## <a name="create-a-content-center"></a>Créer un centre de contenu

Un administrateur SharePoint peut créer un site de centre de contenu comme ils peuvent [créer n’importe quel autre site SharePoint](/sharepoint/create-site-collection) via le panneau de configuration du site Centre d’administration.

Pour créer un nouveau centre de contenu, procédez comme suit :

1. Dans le Centre d’administration Microsoft 365, accédez à la page [Centre d’administration SharePoint **Sites** actifs](https://admin.microsoft.com/sharepoint?page=siteManagement&modern=true).

2. Dans la page **Sites actifs**, cliquez sur **Créer**, puis sélectionnez **Autres options**.

3. Dans le menu **Choisir un modèle** , sélectionnez **Centre de contenu**.

4. Pour le nouveau site, fournissez un **Nom de site**, **Administrateur principal** et une **Langue**.</br>

   > [!NOTE] 
   > Vous pouvez sélectionner un site de centre de contenu à afficher dans l’une des langues disponibles, mais notez que les modèles actuellement peuvent uniquement être créés pour les fichiers en anglais. Notez également que comme les autres modèles de site, la langue du site par défaut ne peut pas être modifiée une fois le site créé.

5. Sélectionnez **Terminé**.
 
Une fois que vous avez créé un site de centre de contenu, celui-ci est répertorié sur la page **Sites actifs** dans le centre d’administration SharePoint. 

### <a name="give-access-to-additional-users"></a>Accorder l’accès à d’autres utilisateurs
 
Une fois le site créé, vous pouvez autoriser d’autres utilisateurs à accéder au site via le [modèle d’autorisations de site SharePoint](/sharepoint/modern-experience-sharing-permissions) standard.

### <a name="roll-up-of-models-in-the-default-content-center"></a>Cumul des modèles dans le centre de contenu par défaut

Dans SharePoint Syntex, le premier centre de contenu créé lors de l’installation est le *centre de contenu par défaut*. Si des centres de contenu suivants sont créés, leurs modèles sont affichés dans la vue du centre de contenu par défaut.

![Capture d’écran de la bibliothèque de modèles dans le centre de contenu par défaut.](../media/content-understanding/model-library-default-content-center.png)

La bibliothèque de **Modèles** dans l’affichage centre de contenu par défaut regroupe les modèles créés par centre de contenu pour obtenir une vue récapitulative de tous les modèles de compréhension de document et modèles de traitement de formulaire qui ont été créés.

> [!NOTE]
> Vous ne pouvez pas modifier le centre de contenu par défaut désigné. Il s’agit toujours du premier centre de contenu créé lors de l’installation. 

## <a name="see-also"></a>Voir aussi
[Créer un classifieur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)

[Créer un centre de contenu](create-a-content-center.md)

[Présentation de la présentation des documents](document-understanding-overview.md)

[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)

[Appliquer un modèle](apply-a-model.md)