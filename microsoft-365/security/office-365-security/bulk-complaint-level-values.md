---
title: Valeurs de niveau de réclamation en bloc, expéditeurs de courrier indésirable, niveaux BCL, fonctionnement de BCL, indices BCL, courrier indésirable, en-tête de courrier indésirable, filtrage du courrier en nombre
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
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
description: En savoir plus sur les valeurs de niveau de conformité en bloc dans Office 365.
ms.openlocfilehash: aa839fc1bcab141fe71c76e7f27b4f6bb23048b2
ms.sourcegitcommit: ce6121a8e3ca7438071d73b0c76e2b6f33ac1cf7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "43030150"
---
# <a name="bulk-complaint-level-bcl-in-office-365"></a>Niveau de réclamation en bloc (BCL) dans Office 365

Les expéditeurs de courriers électroniques varient en fonction de leurs modèles d’envoi, de création de contenu et d’acquisition de destinataires. Certains sont des expéditeurs de publipostage en bloc qui envoient des messages désirés avec du contenu pertinent à leurs abonnés. Ces messages entraînent peu de réclamations de la part des destinataires. D'autres vers de publipostage en bloc envoient des messages non sollicités qui s'apparentent fortement à du courrier indésirable et entraînent de nombreuses réclamations de la part des destinataires. Les messages provenant d’un expéditeur de courrier indésirable sont connus sous le nom de courrier en nombre ou de courrier gris.

Pour distinguer les messages provenant de différents types de publipostages en bloc, le courrier électronique entrant en provenance de courriers électroniques entrants vers Office 365 (Exchange Online ou autonome Exchange Online Protection (EOP) sans boîte aux lettres Exchange Online) est affecté à un niveau de réclamation en bloc (BCL) qui est ajouté à message dans un en-tête X. Le BCL est similaire au [seuil de probabilité de courrier indésirable (SCL)](spam-confidence-levels.md) utilisé pour identifier les messages comme courrier indésirable. Une BCL plus élevée indique qu’un message en bloc est plus susceptible de générer des plaintes (et, par conséquent, plus vraisemblablement un courrier indésirable). Microsoft utilise des sources internes et tierces pour identifier le courrier en nombre et déterminer le BCL approprié.

 Le filtrage du courrier indésirable marque les messages en tant que **courrier en masse** en fonction du seuil BCL (valeur par défaut ou valeur que vous spécifiez) et prend l’action spécifiée sur le message (l’action par défaut consiste à envoyer le message vers le dossier de courrier indésirable du destinataire). Pour plus d’informations, consultez la rubrique [configurer des stratégies de blocage du](configure-your-spam-filter-policies.md) courrier indésirable dans Office 365 et [quelle est la différence entre courrier indésirable et courrier électronique en masse ?](what-s-the-difference-between-junk-email-and-bulk-email.md)

Les seuils BCL sont décrits dans le tableau suivant.

|||
|:---:|---|
|**BCL**|**Description**|
|0|Le message ne provient pas d'un expéditeur en bloc.|
|1, 2, 3|Le message provient d'un expéditeur en bloc qui génère peu de réclamations.|
|4, 5, 6, 7|Le message provient d'un expéditeur en bloc qui génère un nombre moyen de réclamations.|
|8, 9|Le message provient d’un expéditeur en bloc qui génère un grand nombre de réclamations.|
|
