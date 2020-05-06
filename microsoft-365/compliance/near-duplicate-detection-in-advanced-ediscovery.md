---
title: Détection quasi-doublons-eDiscovery
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
description: Utilisez la détection presque en double pour regrouper des documents textuellement similaires lors de l’analyse des données de cas pour Advanced eDiscovery.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 4c24e1b67af68dc5fccd900fc390a63e8da3c389
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44036439"
---
# <a name="near-duplicate-detection"></a>Détection des quasi-duplicatas

Considérez un ensemble de documents à examiner dans lequel un sous-ensemble est basé sur le même modèle et qui possède essentiellement le même langage, avec quelques différences ici et là. Si un réviseur peut identifier ce sous-ensemble, passer en revue l’une d’entre elles de façon approfondie et passer en revue les différences pour le reste, il n’aurait pas manqué d’informations uniques pendant une période de temps qui aurait été utilisée pour lire tous les documents. Les groupes de détection near-duplicate regroupent des documents textuellement similaires pour vous aider à améliorer l’efficacité de votre processus de révision.

## <a name="how-does-it-work"></a>Comment cela fonctionne-t-il ?

Lorsque l’exécution de la détection de doublons est exécutée, le système analyse tous les documents avec du texte. Ensuite, il compare chaque document aux autres pour déterminer si leur similarité est supérieure au seuil défini. Si c’est le cas, les documents sont regroupés. Une fois que tous les documents ont été comparés et regroupés, un document de chaque groupe est marqué comme « tableau croisé dynamique »; lors de l’examen de vos documents, vous pouvez commencer par examiner un tableau croisé dynamique et passer en revue les autres documents dans le même jeu presque en double, en vous concentrant sur la différence entre le tableau croisé dynamique et le document en cours de révision.
