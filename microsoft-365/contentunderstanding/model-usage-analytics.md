---
title: Analyser la façon dont vos modèles sont utilisés dans Microsoft Syntex
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
description: Découvrez comment trouver plus d’informations sur les performances de vos modèles de compréhension de document et de traitement des formulaires.
ms.openlocfilehash: 2cbcabb919dc79a0c0eceaeda97d0e095b241235
ms.sourcegitcommit: 04e517c7e00323b5c33d8ea937115725cf2cfd4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2022
ms.locfileid: "68564825"
---
# <a name="analyze-how-your-models-are-used-in-microsoft-syntex"></a>Analyser la façon dont vos modèles sont utilisés dans Microsoft Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhX]  

</br>


Votre centre de contenu Microsoft Syntex vous fournit l’analytique de l’utilisation des modèles pour fournir plus d’informations sur la façon dont vos modèles publiés à partir du centre de contenu sont utilisés. La section <b>Fonctionnement de vos modèles au cours des 30 derniers jours</b> du centre de contenu inclut un regroupement de 30 jours des données d’analyse de l’utilisation fournies dans les graphiques et listes suivants :

- Classification par modèle
- Classification par bibliothèque
- Utilisation des modèles 

 ![Analyses de modèle.](../media/content-understanding/model-analytics.png) </br>

### <a name="roll-up-of-model-usage-data-in-the-default-content-center"></a>Regroupement des données d’utilisation des modèles dans le centre de contenu par défaut

Dans Syntex, le centre de contenu par défaut est créé lors de l’installation. D’autres centres de contenu peuvent également être créés en fonction des besoins. Par exemple, les services peuvent créer leurs propres centres de contenu pour créer et gérer leurs modèles. 

En ce qui concerne l’analyse de l’utilisation des modèles, notez que :

- Votre centre de contenu par défaut affiche l’analyse de l’utilisation des modèles pour tous les centres de contenu et modèles de votre organisation, y compris ceux créés dans d’autres centres de contenu. Les responsables de contenu et les autres parties prenantes bénéficient ainsi d’un portail centralisé pour gérer et superviser les centres de contenu et les modèles dans toute l’entreprise.  
- Les autres centres de contenu affichent uniquement les données d’analyse de l’utilisation des modèles pour les modèles qui y ont été créés. Cela donne aux gestionnaires de contenu des insights sur les données d’utilisation pour uniquement les modèles qui les intéressent.


## <a name="classification-by-model"></a>Classification par modèle

   ![Pourcentage total des modèles.](../media/content-understanding/total-model-percentage.png) </br>

Le graphique à secteurs **Classification par modèle** affiche les modèles qui ont classé le plus de fichiers. Il présente chaque modèle publié sous forme de pourcentage du nombre total de fichiers traités par tous les modèles publiés sur le centre de contenu.

Chaque modèle affiche également le **taux d’achèvement**, à savoir le pourcentage de fichiers chargés et correctement analysés par le modèle. Un taux d’achèvement faible peut indiquer des problèmes avec le modèle ou les fichiers en cours d’analysé.

## <a name="classification-by-library"></a>Classification par bibliothèque

   ![Fichiers traités.](../media/content-understanding/files-processed-over-time.png) </br>

Le graphique à barres **Classification par bibliothèque** vous permet de déterminer l’efficacité de la compréhension de contenu dans votre organisation.  Il n’affiche seulement le nombre de fichiers traités au fil du temps pour chaque modèle. Si vous sélectionnez une colonne dans le graphique, il affiche aussi les bibliothèques de documents auxquelles le programme a appliqué le modèle.


## <a name="model-usage"></a>Utilisation des modèles

La liste Utilisation des modèles affiche l’analyse de l’utilisation des modèles créés dans le centre de contenu.  

> [!NOTE]
> Si vous êtes dans le centre de contenu par défaut et que vous disposez de centres de contenu supplémentaires dans votre organisation, le programme regroupe la liste d’utilisation des modèles par centre de contenu.

Chaque modèle dans la liste d’utilisation des modèles affiche les données d’utilisation :

- Nombre d’éléments classés : nombre de fichiers traités par le modèle.
- Score de confiance moyen : score de précision moyenne du modèle lors de l’exécution du programme sur des fichiers.
- URL de liste cible : bibliothèque de documents SharePoint à laquelle le modèle s’applique.



## <a name="see-also"></a>Voir aussi
[Créer un classifieur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)

[Présentation de la compréhension de document](document-understanding-overview.md)

[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)  
