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
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a5b03b3c-37dd-429e-8e9b-2c1b25031794
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent en savoir plus sur les valeurs de niveau de réclamation en bloc (BCL) utilisées dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 08e747b704faa18aa73110256624d70c79d0307b
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647378"
---
# <a name="bulk-complaint-level-bcl-in-eop"></a>Niveau de réclamation en bloc (BCL) dans EOP

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, EOP affecte un niveau de réclamation en bloc (BCL) aux messages entrants provenant de expéditeurs en bloc. Le fichier BCL est ajouté au message dans un en-tête X et est similaire au [niveau de confiance du courrier indésirable (SCL)](spam-confidence-levels.md) utilisé pour identifier les messages comme courrier indésirable. Une bcl plus élevée indique qu’un message en bloc est plus susceptible de générer des plaintes (et est donc plus susceptible d’être du courrier indésirable). Microsoft utilise des sources internes et tierces pour identifier le courrier en bloc et déterminer le bcl approprié.

Les expéditeurs en bloc varient selon leurs modèles d’envoi, leur création de contenu et leurs pratiques d’acquisition de destinataires. Les bons expéditeurs de courrier en bloc envoient les messages souhaités avec le contenu approprié à leurs abonnés. Ces messages entraînent peu de réclamations de la part des destinataires. D'autres vers de publipostage en bloc envoient des messages non sollicités qui s'apparentent fortement à du courrier indésirable et entraînent de nombreuses réclamations de la part des destinataires. Les messages d’un expéditeur en bloc sont appelés courrier en bloc ou courrier gris.

 Le filtrage du courrier indésirable marque les messages en tant que **courrier électronique en bloc** en fonction du seuil BCL (valeur par défaut ou valeur que vous spécifiez) et effectue l’action spécifiée sur le message (l’action par défaut consiste à remettre le message au dossier Courrier indésirable du destinataire). Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md) et [quelle est la différence entre le courrier indésirable et le courrier en bloc ?](what-s-the-difference-between-junk-email-and-bulk-email.md)

Les seuils BCL sont décrits dans le tableau suivant.

|BCL|Description|
|:---:|---|
|0|Le message ne provient pas d'un expéditeur en bloc.|
|1, 2, 3|Le message provient d'un expéditeur en bloc qui génère peu de réclamations.|
|4, 5, 6, 7<sup>\*</sup>|Le message provient d'un expéditeur en bloc qui génère un nombre moyen de réclamations.|
|8, 9|Le message vient d’un expéditeur en bloc qui génère un grand nombre de plaintes.|

<sup>\*</sup> Il s’agit de la valeur de seuil par défaut utilisée dans les stratégies anti-courrier indésirable.
