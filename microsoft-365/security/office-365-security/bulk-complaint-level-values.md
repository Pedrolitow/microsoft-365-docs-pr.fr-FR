---
title: Valeurs de niveau de réclamation en bloc
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a5b03b3c-37dd-429e-8e9b-2c1b25031794
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent en savoir plus sur les valeurs BCL (bulk complaint level) utilisées dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 11f884ec6b32795deba09c0f1ba88055a6422e9b
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59183071"
---
# <a name="bulk-complaint-level-bcl-in-eop"></a>Niveau de réclamation en bloc (BCL) dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres en Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, EOP affecte un niveau de réclamation en bloc (BCL) aux messages entrants provenant de publipostages en masse. Le bcl est ajouté au message dans un en-tête X et est similaire au niveau de confiance du courrier indésirable [(SCL)](spam-confidence-levels.md) utilisé pour identifier les messages comme courrier indésirable. Une valeur BCL supérieure indique qu’un message en nombre est plus susceptible de générer des réclamations (et est donc plus susceptible d’être du courrier indésirable). Microsoft utilise des sources internes et tierces pour identifier le courrier en nombre et déterminer le bcl approprié.

Les publipostages en nombre varient selon les modèles d’envoi, la création de contenu et les pratiques d’acquisition des destinataires. Les expéditeurs de courrier en nombre de bonne qualité envoient les messages souhaités avec du contenu pertinent à leurs abonnés. Ces messages entraînent peu de réclamations de la part des destinataires. D'autres vers de publipostage en bloc envoient des messages non sollicités qui s'apparentent fortement à du courrier indésirable et entraînent de nombreuses réclamations de la part des destinataires. Les messages provenant d’un publipostage en masse sont appelés courriers en masse ou gris.

 Le filtrage du  courrier indésirable marque les messages en tant que messages électroniques en bloc en fonction du seuil BCL (valeur par défaut ou valeur que vous spécifiez) et prend l’action spécifiée sur le message (l’action par défaut consiste à remettre le message dans le dossier Courrier indésirable du destinataire). Pour plus d’informations, voir Configurer des [stratégies anti-courrier](configure-your-spam-filter-policies.md) indésirable et quelle est la différence entre le courrier indésirable et le [courrier en masse ?](what-s-the-difference-between-junk-email-and-bulk-email.md)

Vous pouvez utiliser la liste d’adresses client autoriser/bloquer pour configurer des exceptions pour le filtrage du courrier en bloc. Les messages provenant d’expéditeurs dans les domaines spécifiés ne reçoivent pas l’action du verdict de filtrage du courrier indésirable en bloc dans les stratégies anti-courrier indésirable.  Pour plus d’informations, [voir Manage the Tenant Allow/Block List](tenant-allow-block-list.md).

Les seuils BCL sont décrits dans le tableau suivant.

****

|BCL|Description|
|:---:|---|
|0|Le message ne provient pas d'un expéditeur en bloc.|
|1, 2, 3|Le message provient d'un expéditeur en bloc qui génère peu de réclamations.|
|4, 5, 6, 7<sup>\*</sup>|Le message provient d'un expéditeur en bloc qui génère un nombre moyen de réclamations.|
|8, 9|Le message est provenant d’un expéditeur en bloc qui génère un nombre élevé de réclamations.|
|

<sup>\*</sup> Il s’agit de la valeur de seuil par défaut utilisée dans les stratégies anti-courrier indésirable.
