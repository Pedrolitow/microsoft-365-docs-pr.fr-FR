---
title: Détection des quasi-doublons - eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez la détection des quasi-doublons pour grouper des documents textuellement similaires lors de l’analyse des données de cas Advanced eDiscovery.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 255531897a1706904005034c56cab00d0032b7f3
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59206171"
---
# <a name="near-duplicate-detection-in-advanced-ediscovery"></a>Détection des quasi-doublons dans Advanced eDiscovery

Considérons un ensemble de documents à examiner dans lequel un sous-ensemble est basé sur le même modèle et a principalement le même langage réutilisable, avec quelques différences ici et là. Si un réviseur peut identifier ce sous-ensemble, passer en revue l’un d’entre eux minutieusement et examiner les différences pour le reste, il n’aurait manqué aucune information unique tout en ne prenant qu’une fraction de temps qui l’aurait conduit à lire tous les documents à couvrir. La détection des quasi-doublons regroupe les documents textuellement similaires afin de renforcer l’efficacité du processus d’examen.

## <a name="how-does-it-work"></a>Comment cela fonctionne-t-il ?

Lorsqu’il procède à la détection des quasi-doublons, le système analyse tous les documents contenant du texte. Il les compare ensuite afin de déterminer si leur niveau de similarité est supérieur à un seuil défini. Si c’est le cas, les documents sont regroupés. Une fois tous les documents comparés et regroupés, un document de chaque groupe est désigné comme « pivot ». Lorsque vous procédez par la suite à l’examen des documents, vous pouvez commencer par le pivot avant de vous pencher sur les autres documents du groupe de quasi-doublons, en vous attachant à chaque fois à repérer la différence entre le pivot et l’autre document examiné.
