---
title: Collecter des pièces jointes cloud dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
ms.reviewer: nickrob
manager: laurawi
ms.date: 06/03/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Utilisez des collections dans Microsoft Purview eDiscovery (Premium) pour collecter des pièces jointes cloud à examiner dans une enquête ou un cas.
ms.openlocfilehash: e59b4720613572763b300517c0b603493ab5a9de
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636940"
---
# <a name="collect-cloud-attachments-in-microsoft-purview-ediscovery-premium"></a>Collecter des pièces jointes cloud dans Microsoft Purview eDiscovery (Premium)

Les pièces jointes cloud sont des liens vers des documents qui sont généralement stockés dans le site SharePoint et OneDrive. Par conséquent, au lieu d’attacher une copie réelle d’un document dans un e-mail ou une conversation de conversation Teams, vous avez la possibilité de partager un lien vers le fichier. Les pièces jointes cloud sont un moyen efficace de partager des documents et de collaborer avec d’autres personnes de votre organisation. Toutefois, les pièces jointes cloud présentent des difficultés pendant le flux de travail eDiscovery, car seul le lien de pièce jointe cloud et non le contenu réel du document partagé sont retournés dans une recherche eDiscovery. Pour relever ce défi, eDiscovery (Premium) fournit deux solutions pour collecter des pièces jointes cloud :  

- Collecte de la version active d’un document lié dans une pièce jointe cloud.

- Collecte de la version du document au moment où il a été partagé dans une pièce jointe cloud.

## <a name="collecting-cloud-attachments"></a>Collecte de pièces jointes cloud

Lorsque vous créez un brouillon de collection et que les résultats de la recherche contiennent des éléments qui incluent des pièces jointes cloud, vous avez la possibilité de collecter la cible de la pièce jointe cloud lorsque vous validez le brouillon de la collection dans un jeu de révision. Lorsque vous sélectionnez cette option, eDiscovery (Premium) ajoute les documents liés dans la pièce jointe cloud au jeu de révision. Cela vous permet d’examiner les documents cibles et de déterminer si le document est pertinent pour votre cas ou votre enquête.

La capture d’écran suivante montre l’option permettant d’inclure les cibles des pièces jointes cloud lorsque vous validez une collection dans un jeu de révisions.

![Option permettant d’inclure des pièces jointes cloud lors de la validation d’un regroupement dans un ensemble de révisions](../media/CollectCloudAttachments1.png)

> [!NOTE]
>- Si vous utilisez le [nouveau format de cas](advanced-ediscovery-new-case-format.md) dans eDiscovery (Premium), l’option d’inclure des pièces jointes cloud dans le jeu de révision est sélectionnée par défaut et ne peut pas être désélectionnée.<br/>
>- Vous avez également la possibilité d’inclure toutes les versions (en plus de la version partagée) des pièces jointes cloud dans le jeu de révision.  
Pour obtenir des instructions sur la validation d’un regroupement dans un ensemble de révisions, consultez [Valider un brouillon de collection dans un ensemble de révisions](commit-draft-collection.md).

## <a name="collecting-the-version-shared-in-a-cloud-attachment-preview"></a>Collecte de la version partagée dans une pièce jointe cloud (préversion)

Le flux de travail eDiscovery (Premium) pour la collecte des pièces jointes cloud inclut uniquement l’ajout de la version la plus récente d’une pièce jointe cloud à un jeu de révision. Cela signifie que la version collectée et ajoutée à un ensemble de révisions peut être différente de la version initialement partagée dans la pièce jointe cloud. Il est donc possible que le contenu présent dans la pièce jointe cloud au moment où il a été partagé ait été supprimé et n’existe pas dans la version actuelle ajoutée au jeu de révision.

Les organisations ont désormais la possibilité d’utiliser des étiquettes de rétention Microsoft 365 pour conserver la version d’un document au moment où il a été partagé en tant que pièce jointe cloud. Pour ce faire, votre organisation peut créer une étiquette de rétention, choisir l’option appliquer l’étiquette aux pièces jointes cloud, puis appliquer automatiquement l’étiquette aux documents stockés dans SharePoint et OneDrive. Après avoir configuré cette configuration, une copie d’un document est créée au moment où le fichier est partagé. En outre, si le document est modifié et partagé à nouveau en tant que pièce jointe cloud, la version modifiée est également conservée. Si le fichier est modifié et partagé à nouveau, une nouvelle copie du fichier en tant que nouvelle version est conservée.

La conservation des versions partagées des pièces jointes cloud peut aider votre organisation à étendre la conservation et la collecte du contenu potentiellement pertinent à la version spécifique du document qui a été partagée plutôt que la version active actuelle. Après avoir implémenté cette solution de rétention, la version active actuelle d’une pièce jointe cloud et la version partagée dans la pièce jointe cloud sont collectées et ajoutées à un ensemble de révisions.

Pour obtenir des instructions sur la configuration d’une étiquette de rétention et son application automatique aux pièces jointes cloud, consultez [Appliquer automatiquement des étiquettes aux pièces jointes cloud](apply-retention-labels-automatically.md#auto-apply-labels-to-cloud-attachments).

La capture d’écran suivante montre un document de pièce jointe cloud, nommé *XYZ Research.docx*, qui a été ajouté à un jeu de révision. Le document a été partagé en tant que pièce jointe cloud dans une conversation de conversation Teams. L’ensemble de révision contient également la version qui a été partagée à l’origine dans la pièce jointe cloud. Notez que le nom de cette version de la pièce jointe cloud est généré par le système et que l’auteur est identifié comme **SharePoint**.

![Version d’une pièce jointe cloud qui a été partagée affichée dans un ensemble de révisions](../media/CollectCloudAttachments2.png)

En outre, la version active actuelle et la version qui a été partagée ont la même valeur de propriété **FamilyId** , qui est identique à **l’ID de** famille pour l’objet parent (par exemple, un e-mail ou une conversation de conversation Teams). Cela vous permet de regrouper les pièces jointes cloud avec l’élément dans lequel elles ont été partagées.

Une fois que vous avez implémenté l’étiquette de rétention et appliqué automatiquement l’étiquette aux documents SharePoint, vous sélectionnez toujours l’option permettant de collecter des pièces jointes cloud lors de la validation d’un brouillon de collection dans un ensemble de révisions. Lorsque les pièces jointes cloud sont collectées, la version active actuelle et la version qui a été partagée à l’origine sont ajoutées au jeu de révision.
