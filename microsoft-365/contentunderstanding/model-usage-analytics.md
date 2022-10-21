---
title: Analyser l’utilisation de vos modèles dans Microsoft Syntex
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
description: Découvrez comment trouver plus d’informations sur les performances de vos modèles IA dans Microsoft Syntex.
ms.openlocfilehash: 0878893af1ec00ed2b3e4d2c7e24bf4649302995
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68659958"
---
# <a name="analyze-how-your-models-are-used-in-microsoft-syntex"></a>Analyser l’utilisation de vos modèles dans Microsoft Syntex

<sup>**S’applique à :**  &ensp; &#10003; Tous les modèles &ensp; | &ensp; personnalisés &#10003; Tous les modèles prédéfinis</sup>

<!---
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhX]  

</br>
--->

Votre centre de contenu dans Microsoft Syntex vous fournit des analyses d’utilisation des modèles pour fournir plus d’informations sur la façon dont vos modèles publiés à partir du centre de contenu sont utilisés. La section **Fonctionnement de vos modèles au cours des 30 derniers jours** du centre de contenu inclut un regroupement de 30 jours des données d’analyse de l’utilisation fournies dans les graphiques et listes suivants :

- Classification par modèle
- Classification par bibliothèque
- Utilisation des modèles 

 ![Analyses de modèle.](../media/content-understanding/model-analytics.png) 

### <a name="roll-up-of-model-usage-data-in-the-default-content-center"></a>Regroupement des données d’utilisation des modèles dans le centre de contenu par défaut

Dans Syntex, le centre de contenu par défaut est créé pendant l’installation. D’autres centres de contenu peuvent également être créés en fonction des besoins. Par exemple, les services peuvent créer leurs propres centres de contenu pour créer et gérer leurs modèles. 

En ce qui concerne l’analytique de l’utilisation des modèles, notez que :

- Votre centre de contenu par défaut affiche l’analytique de l’utilisation des modèles pour tous les centres de contenu et modèles de votre organisation, y compris ceux créés dans d’autres centres de contenu. Les responsables de contenu et les autres parties prenantes bénéficient ainsi d’un portail centralisé pour gérer et superviser les centres de contenu et les modèles dans toute l’entreprise.
 
- Les autres centres de contenu affichent uniquement les données d’analyse de l’utilisation des modèles pour les modèles qui y ont été créés. Cela donne aux gestionnaires de contenu des informations sur les données d’utilisation pour les modèles qui les concernent uniquement.

## <a name="classification-by-model"></a>Classification par modèle

   ![Pourcentage total des modèles.](../media/content-understanding/total-model-percentage.png) 

Le graphique à secteurs **Classification par modèle** affiche les modèles qui ont classé le plus de fichiers. Il présente chaque modèle publié sous forme de pourcentage du nombre total de fichiers traités par tous les modèles publiés sur le centre de contenu.

Chaque modèle affiche également le **taux d’achèvement**, à savoir le pourcentage de fichiers chargés et correctement analysés par le modèle. Un taux d’achèvement faible peut indiquer des problèmes avec le modèle ou les fichiers en cours d’analysé.

## <a name="classification-by-library"></a>Classification par bibliothèque

   ![Fichiers traités.](../media/content-understanding/files-processed-over-time.png) 

Le graphique à barres **Classification par bibliothèque** vous permet de déterminer l’efficacité de la compréhension de contenu dans votre organisation. Il n’affiche seulement le nombre de fichiers traités au fil du temps pour chaque modèle. Si vous sélectionnez une colonne dans le graphique, il affiche aussi les bibliothèques de documents auxquelles le programme a appliqué le modèle.


## <a name="model-usage"></a>Utilisation des modèles

La liste d’utilisation des modèles affiche l’analyse de l’utilisation des modèles créés via le centre de contenu.  

> [!NOTE]
> Si vous êtes dans le centre de contenu par défaut et que vous disposez de centres de contenu supplémentaires dans votre organisation, le programme regroupe la liste d’utilisation des modèles par centre de contenu.

Chaque modèle dans la liste d’utilisation des modèles affiche les données d’utilisation :

- Nombre d’éléments classés : nombre de fichiers traités par le modèle.
- Score de confiance moyen : score de précision moyenne du modèle lors de l’exécution du programme sur des fichiers.
- URL de liste cible : bibliothèque de documents SharePoint à laquelle le modèle s’applique.

