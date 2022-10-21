---
title: Créer un centre de contenu dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.service: microsoft-syntex
search.appverid: ''
ms.custom: admindeeplinkSPO
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment créer un centre de contenu dans Microsoft Syntex.
ms.openlocfilehash: aa74e6bb350074586ba233f9d88d41da2505f8ce
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68660398"
---
# <a name="create-a-content-center-in-microsoft-syntex"></a>Créer un centre de contenu dans Microsoft Syntex

<sup>**S’applique à :**  &ensp; &#10003; Tous les modèles &ensp; | &ensp; personnalisés &#10003; Tous les modèles prédéfinis</sup>

<!---
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CPSF]

</br>
--->

Pour créer et gérer des modèles d’entreprise, vous avez d’abord besoin d’un centre de contenu. Le centre de contenu est l’interface de création de modèles et contient également des informations sur les bibliothèques de documents auxquelles les modèles publiés ont été appliqués.

   ![Sélectionnez une bibliothèque de documents.](../media/content-understanding/content-center-page.png)

Vous créez un centre de contenu par défaut lors de [l’installation](set-up-content-understanding.md). Mais un administrateur SharePoint peut également choisir de créer d’autres centres au besoin. Bien qu’un seul centre de contenu puisse convenir pour les environnements pour lesquels vous souhaitez un cumul de toutes les activités de modèle, vous souhaiterez peut-être avoir des centres supplémentaires pour plusieurs services au sein de votre organisation, qui peuvent avoir des besoins et des exigences d’autorisation différents pour leurs modèles.

En outre, si vous souhaitez essayer Syntex, vous pouvez créer un centre de contenu en suivant les instructions de cet article sans acheter de licences. Les utilisateurs sans licence peuvent créer des modèles, mais ne peuvent pas les appliquer à une bibliothèque de documents.

> [!NOTE]
> Dans un [Microsoft 365 Multigéographie](../enterprise/microsoft-365-multi-geo.md), si vous avez un centre de contenu par défaut unique dans votre emplacement central, vous pouvez seulement fournir un suivi de l’activité du modèle à partir de cet emplacement. Vous ne pouvez pas actuellement obtenir de déploiement de l’activité de modèle au-delà des limites de la batterie de serveurs dans l’environnement multigéographique. 

## <a name="create-a-content-center"></a>Créer un centre de contenu

Un administrateur SharePoint peut créer un site de centre de contenu comme ils peuvent [créer n’importe quel autre site SharePoint](/sharepoint/create-site-collection) via le panneau de configuration du site Centre d’administration.

Pour créer un nouveau centre de contenu, procédez comme suit :

1. Dans la Centre d'administration Microsoft 365, accédez au <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">Centre  > **d’administration SharePoint****Sites actifs**</a>.

2. Dans la page **Sites actifs** , sélectionnez **Créer**, puis **Autres options**.

3. Dans le menu **Choisir un modèle** , sélectionnez **Centre de contenu**.

4. Pour le nouveau site, indiquez un **nom de site**, un **administrateur principal** et une **langue**.</br>

   > [!NOTE] 
   > Vous pouvez sélectionner un site de centre de contenu à afficher dans l’une des langues disponibles, mais notez que les modèles actuellement peuvent uniquement être créés pour les fichiers en anglais. Notez également que comme les autres modèles de site, la langue du site par défaut ne peut pas être modifiée une fois le site créé.

5. Sélectionnez **Terminé**.
 
Une fois que vous avez créé un site de centre de contenu, celui-ci est répertorié sur <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Sites actifs**</a> dans le Centre d’administration SharePoint. 

### <a name="give-access-to-additional-users"></a>Accorder l’accès à d’autres utilisateurs
 
Une fois le site créé, vous pouvez autoriser d’autres utilisateurs à accéder au site via le [modèle d’autorisations de site SharePoint](/sharepoint/modern-experience-sharing-permissions) standard.

### <a name="roll-up-of-models-in-the-default-content-center"></a>Cumul des modèles dans le centre de contenu par défaut

Dans Syntex, le premier centre de contenu créé pendant l’installation est le *centre de contenu par défaut*. Si des centres de contenu suivants sont créés, leurs modèles sont affichés dans la vue du centre de contenu par défaut.

![Capture d’écran de la bibliothèque de modèles dans le centre de contenu par défaut.](../media/content-understanding/model-library-default-content-center.png)

La bibliothèque **De modèles** dans l’affichage centre de contenu par défaut regroupe les modèles créés par centre de contenu pour une vue récapitulative de tous les modèles qui ont été créés.

> [!NOTE]
> Vous ne pouvez pas modifier le centre de contenu par défaut désigné. Il s’agit toujours du premier centre de contenu créé lors de l’installation. 

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des types de modèle](model-types-overview.md)


