---
title: Détection des doublons proches dans eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez la détection en quasi-double pour regrouper des documents textuels similaires lors de l’analyse des données de cas dans eDiscovery (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 4b6ad8a3a3775c8389e943aa249cffd16b6b84d2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096631"
---
# <a name="near-duplicate-detection-in-ediscovery-premium"></a>Détection des doublons proches dans eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Considérez un ensemble de documents à examiner dans lequel un sous-ensemble est basé sur le même modèle et a principalement le même langage réutilisable, avec quelques différences ici et là. Si un réviseur pouvait identifier ce sous-ensemble, examiner l’un d’eux de manière approfondie et examiner les différences pour le reste, il n’aurait pas manqué d’informations uniques tout en prenant seulement une fraction de temps qui l’aurait amené à lire tous les documents couverts pour couvrir. La détection des quasi-doublons regroupe les documents textuellement similaires afin de renforcer l’efficacité du processus d’examen.

## <a name="how-does-it-work"></a>Comment cela fonctionne-t-il ?

Lorsqu’il procède à la détection des quasi-doublons, le système analyse tous les documents contenant du texte. Il les compare ensuite afin de déterminer si leur niveau de similarité est supérieur à un seuil défini. Si c’est le cas, les documents sont regroupés. Une fois tous les documents comparés et regroupés, un document de chaque groupe est désigné comme « pivot ». Lorsque vous procédez par la suite à l’examen des documents, vous pouvez commencer par le pivot avant de vous pencher sur les autres documents du groupe de quasi-doublons, en vous attachant à chaque fois à repérer la différence entre le pivot et l’autre document examiné.
