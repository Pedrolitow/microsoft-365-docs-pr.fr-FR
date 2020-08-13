---
title: Valeurs de niveau de réclamation en bloc
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a5b03b3c-37dd-429e-8e9b-2c1b25031794
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent en savoir plus sur les valeurs de niveau de conformité en bloc utilisées dans Exchange Online Protection (EOP).
ms.openlocfilehash: 19fa7172bd242852d03822c588e163b7a13f9201
ms.sourcegitcommit: 6a1a8aa024fd685d04da97bfcbc8eadacc488534
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46653208"
---
# <a name="bulk-complaint-level-bcl-in-eop"></a>Niveau de réclamation en bloc (BCL) dans EOP

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online, EOP affecte un niveau de conformité en bloc (BCL) aux messages entrants provenant de publipostages en bloc. La bibliothèque de BCL est ajoutée au message dans un en-tête X et est similaire au [seuil de probabilité de courrier indésirable (SCL)](spam-confidence-levels.md) utilisé pour identifier les messages comme courrier indésirable. Une BCL plus élevée indique qu’un message en bloc est plus susceptible de générer des plaintes (et, par conséquent, plus vraisemblablement un courrier indésirable). Microsoft utilise des sources internes et tierces pour identifier le courrier en nombre et déterminer le BCL approprié.

Les expéditeurs de courriers électroniques varient en fonction de leurs modèles d’envoi, de création de contenu et d’acquisition de destinataires. Les expéditeurs de courriers en bloc envoient des messages pertinents avec le contenu pertinent à leurs abonnés. Ces messages entraînent peu de réclamations de la part des destinataires. D'autres vers de publipostage en bloc envoient des messages non sollicités qui s'apparentent fortement à du courrier indésirable et entraînent de nombreuses réclamations de la part des destinataires. Les messages provenant d’un expéditeur de courrier indésirable sont connus sous le nom de courrier en nombre ou de courrier gris.

 Le filtrage du courrier indésirable marque les messages en tant que **courrier en masse** en fonction du seuil BCL (valeur par défaut ou valeur que vous spécifiez) et prend l’action spécifiée sur le message (l’action par défaut consiste à envoyer le message vers le dossier de courrier indésirable du destinataire). Pour plus d’informations, consultez la rubrique [configurer des stratégies anti-courrier](configure-your-spam-filter-policies.md) indésirable et [quelle est la différence entre courrier indésirable et courrier électronique en masse ?](what-s-the-difference-between-junk-email-and-bulk-email.md)

Les seuils BCL sont décrits dans le tableau suivant.

****

|BCL|Description|
|:---:|---|
|0|Le message ne provient pas d'un expéditeur en bloc.|
|1, 2, 3|Le message provient d'un expéditeur en bloc qui génère peu de réclamations.|
|4, 5, 6, 7|Le message provient d'un expéditeur en bloc qui génère un nombre moyen de réclamations.|
|8, 9|Le message provient d’un expéditeur en bloc qui génère un grand nombre de réclamations.|
|
