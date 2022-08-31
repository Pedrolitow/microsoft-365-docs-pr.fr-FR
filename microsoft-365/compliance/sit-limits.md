---
title: Limites des types d’informations sensibles
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: En savoir plus sur le nombre d’instances et d’autres limites de type d’informations sensibles
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4a1f01e26fa36496affbc696befaba60effa6c08
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67477994"
---
# <a name="sensitive-information-type-limits"></a>Limites des types d’informations sensibles

Ces limites s’appliquent à tous les types d’informations sensibles (SIT), à l’exception des données exactes correspondant aux types d’informations sensibles qui prennent en charge jusqu’à 100.

> [!NOTE]
> Nous prenons en charge jusqu’à 100 évaluations de correspondance de données exactes (EDM). Les stratégies qui utilisent des SIT EDM ne doivent pas être écrites **avec une valeur** minimale ou **maximale** de nombre d’instances supérieure à 100.

Ces limites s’appliquent à toutes les stratégies Microsoft Purview qui utilisent des SIT.

Pour garantir des performances élevées et une latence inférieure, il existe des limitations dans les configurations SIT personnalisées.

|Limite|Valeur|
|---|---|
|nombre maximal de SIT personnalisés créés via le Centre de conformité| 500 |
|longueur maximale de l’expression régulière| 1 024 caractères|
|longueur maximale d’un terme donné dans une liste de mots clés| 50 caractères|
|nombre maximal de termes dans la liste des mots clés| 2048|
|nombre maximal d’expressions régulières distinctes par type d’informations sensibles| 20|
|taille maximale d’un dictionnaire de mots clés (après compression)| 1 Mo (~1 000 000 caractères)|
|nombre maximal de SIT basés sur un dictionnaire de mots clés dans un locataire|50 |

> [!NOTE]
> Si vous avez besoin de créer plus de 500 SIT personnalisés, veuillez créer un ticket de support.

### <a name="instance-count-supported-values-for-sit"></a>Nombre d’instances prises en charge pour SIT

La limite de nombre d’instances SIT s’applique lorsque des SIT sont utilisés dans ces solutions :

- Protection contre la perte de données Microsoft Purview stratégies
- stratégies Protection des données Microsoft Purview
- Gestion du cycle de vie des données Microsoft Purview
- Conformité des communications
- Gestion des enregistrements Microsoft Purview
- Microsoft Defender for Cloud Apps
- Microsoft Priva

Pour qu’un élément analysé réponde aux critères de règle, le nombre d’instances uniques d’un SIT dans un élément unique doit être compris entre les valeurs min et max. Il s’agit du **nombre d’instances**.

- **Champ min** : limite inférieure (nombre minimal) d’instances uniques d’un SIT qui doivent être trouvées dans un élément pour déclencher une correspondance. Le champ min prend en charge les valeurs suivantes :
  - 1 à 500
- **Champ maximal** : limite supérieure du nombre d’instances uniques d’un SIT qui se trouvent dans un élément et déclenchent toujours une correspondance. Le champ max prend en charge les valeurs suivantes :
  - 1 à 500 - Utilisez cette option lorsque vous souhaitez définir une limite supérieure spécifique de 500 ou moins sur le nombre d’instances d’un SIT dans un élément.
  - Any - Utiliser `Any` lorsque vous souhaitez que les critères de nombre d’instances uniques soient satisfaits lorsqu’un nombre non défini d’instances uniques d’un SIT est trouvé dans un élément analysé et que le nombre d’instances uniques atteint ou dépasse le nombre minimal de valeurs d’instances uniques. En d’autres termes, les critères de nombre d’instances uniques sont remplis tant que la valeur minimale est remplie.

Par exemple, si vous souhaitez que la règle déclenche une correspondance quand au moins 500 instances uniques d’un SIT sont trouvées dans un seul élément, définissez la valeur `500` **minimale** sur et la valeur **maximale** sur `Any`.



