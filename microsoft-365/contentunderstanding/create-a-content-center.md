---
title: Créer un centre de contenu dans Microsoft SharePoint Syntex
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
localization_priority: Priority
description: Découvrez comment créer un centre de contenu.
ms.openlocfilehash: 34ba45cd62214743e5a6784893e0f24e9815fdfb
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50905823"
---
# <a name="create-a-content-center-in-microsoft-sharepoint-syntex"></a>Créer un centre de contenu dans Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CPSF]

</br>

Pour créer et gérer des modèles de présentation de documents, vous devez d’abord utiliser un centre de contenu. Le centre de contenu est l’interface de création de modèles et contient également des informations sur les bibliothèques de documents auxquelles les modèles publiés ont été appliqués.</br>

   ![Sélectionner une bibliothèque de documents](../media/content-understanding/content-center-page.png)</br>

Vous créez un centre de contenu par défaut lors de [l’installation](set-up-content-understanding.md). Mais un administrateur SharePoint peut également choisir de créer d’autres centres au besoin. Bien qu’il soit possible qu’un seul centre de contenu soit adapté aux environnements pour lesquels vous voulez regrouper toutes les activités du modèle, vous souhaiterez peut-être disposer de centres supplémentaires pour plusieurs services au sein de votre organisation, lesquels peuvent avoir des besoins et des autorisations différents pour leurs modèles.

> [!NOTE]
> Dans un [Microsoft 365 Multigéographie](../enterprise/microsoft-365-multi-geo.md), si vous avez un centre de contenu par défaut unique dans votre emplacement central, vous pouvez seulement fournir un suivi de l’activité du modèle à partir de cet emplacement. Vous ne pouvez pas actuellement obtenir de déploiement de l’activité de modèle au-delà des limites de la batterie de serveurs dans l’environnement multigéographique. 


## <a name="create-a-content-center"></a>Créer un centre de contenu

Un administrateur SharePoint peut créer un site de centre de contenu comme ils peuvent [créer n’importe quel autre site SharePoint](/sharepoint/create-site-collection) via le panneau de configuration du site Centre d’administration.

Pour créer un nouveau centre de contenu, procédez comme suit :

1. Dans le centre d’administration Microsoft 365, accédez au centre d’administration SharePoint.

2. Dans le Centre d’administration SharePoint, sous **Sites** sélectionnez **Sites actifs**.

3. Dans la page **Sites actifs**, cliquez sur **Créer**, puis sélectionnez **Autres options**.

4. Dans le menu **Choisir un modèle** , sélectionnez **Centre de contenu**.

5. Pour le nouveau site, fournissez un **Nom de site**, **Administrateur principal** et une **Langue**.</br>

   > [!NOTE] 
   > Vous pouvez sélectionner un site de centre de contenu à afficher dans l’une des langues disponibles, mais notez que les modèles actuellement peuvent uniquement être créés pour les fichiers en anglais. Notez également que comme les autres modèles de site, la langue du site par défaut ne peut pas être modifiée une fois le site créé.</br>

6. Sélectionnez **Terminé**.
 
Une fois que vous avez créé un site de centre de contenu, celui-ci est répertorié sur la page **Sites actifs** dans le centre d’administration SharePoint. 

### <a name="give-access-to-additional-users"></a>Accorder l’accès à d’autres utilisateurs
 
Une fois le site créé, vous pouvez autoriser d’autres utilisateurs à accéder au site via le [modèle d’autorisations de site SharePoint](/sharepoint/modern-experience-sharing-permissions) standard.

## <a name="see-also"></a>Voir aussi
[Créer un classificateur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)

[Créer un centre de contenu](create-a-content-center.md)

[Présentation de la présentation des documents](document-understanding-overview.md)

[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)

[Appliquer un modèle](apply-a-model.md)