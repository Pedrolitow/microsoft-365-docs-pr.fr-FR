---
title: Valeurs de niveau de réclamation en bloc, expéditeurs de courrier indésirable, niveaux BCL, fonctionnement de BCL, indices BCL, courrier indésirable, en-tête de courrier indésirable, filtrage du courrier en nombre
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/23/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a5b03b3c-37dd-429e-8e9b-2c1b25031794
ms.collection:
- M365-security-compliance
description: Découvrez les valeurs de niveau de courrier en bloc (BCL) dans Office 365.
ms.openlocfilehash: b0eb922323421834eae77b8c5430f1bd8f48c8ee
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41599721"
---
# <a name="bulk-complaint-level-values"></a>Valeurs BCL

Les vers de publipostage en bloc ont des modèles d'envoi différents, ainsi que des pratiques de création de contenu et d'acquisition de liste variées. Certains sont de bons vers de publipostage en bloc et envoient des messages désirés comportant un contenu pertinent à leurs abonnés. Ces messages entraînent peu de réclamations de la part des destinataires. D'autres vers de publipostage en bloc envoient des messages non sollicités qui s'apparentent fortement à du courrier indésirable et entraînent de nombreuses réclamations de la part des destinataires.

Pour distinguer ces types de vers de publipostage en bloc, une évaluation BCL (Bulk Complaint Level) est réalisée sur les messages qui en proviennent. Les évaluations BCL vont de 1 à 9 selon la probabilité de réclamations dues au ver de publipostage en bloc. Un expéditeur disposant d'une évaluation BCL de 9 peut entraîner un grand nombre de réclamations de la part des destinataires, tandis qu'un autre expéditeur ayant une évaluation BCL de 3 n'en générera probablement pas beaucoup. Microsoft utilise des sources internes et tierces pour identifier le courrier en masse et déterminer l'évaluation BCL appropriée. Pour plus d'informations sur cet en-tête de message, voir [En-têtes de messages anti-courrier indésirable](anti-spam-message-headers.md).

Dans la mesure où un expéditeur de courrier en nombre avec une note de 9 est susceptible de générer des plaintes, le BCL par défaut est 7. Cela signifie que les courriers en masse seront acceptés jusqu’à ce que le niveau de réclamation de 7 et que le courrier ne soit accepté par la suite. Plus le taux est faible, moins le courrier en masse est accepté. Si vos utilisateurs sont, et que leur travail est, confidentiel à envoyer du courrier en nombre et que votre BCL est défini sur 4, aucun courrier en masse avec une BCL plus élevée ne sera accepté.

Vous pouvez vous servir des valeurs BCL pour définir le niveau de filtrage en bloc souhaité pour votre organisation en suivant les étapes décrites dans la rubrique [Configuration de vos stratégies de filtrage du courrier indésirable](configure-your-spam-filter-policies.md).

Le tableau suivant décrit les valeurs BCL actuellement utilisées.

|||
|:-----|:-----|
|**Valeur BCL**|**Description**|
|0|Le message ne provient pas d'un expéditeur en bloc.|
|1, 2, 3|Le message provient d'un expéditeur en bloc qui génère peu de réclamations.|
|4, 5, 6, 7|Le message provient d'un expéditeur en bloc qui génère un nombre moyen de réclamations.|
|8, 9|Le message provient d’un expéditeur en bloc qui génère un grand nombre de réclamations.|
