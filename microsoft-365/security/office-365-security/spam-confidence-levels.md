---
title: Spam confidence level
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
ms.assetid: 34681000-0022-4b92-b38a-e32b3ed96bf6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur le niveau de confiance du courrier indésirable (SCL) appliqué aux messages dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8febc1d0e0c4fd98b33fb0016beee89a30802241
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647906"
---
# <a name="spam-confidence-level-scl-in-eop"></a>Niveau de confiance du courrier indésirable (SCL) dans EOP

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, les messages entrants passent par le filtrage du courrier indésirable dans EOP et reçoivent un score de courrier indésirable. Ce score est mappé à un niveau de confiance du courrier indésirable (SCL) individuel qui est ajouté au message dans un en-tête X. Un SCL plus élevé indique qu'un message est plus susceptible d'être un courrier indésirable. EOP prend des mesures sur le message en fonction de la liste SCL.

Ce que signifie la liste de contrôle de contrôle d’accès et les actions par défaut effectuées sur les messages sont décrites dans le tableau suivant. Pour plus d’informations sur les actions que vous pouvez effectuer sur les messages en fonction du verdict de filtrage du courrier indésirable, consultez [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

|SCL|Définition|Action par défaut|
|:---:|---|---|
|-1|Le message a ignoré le filtrage du courrier indésirable. Par exemple, le message provient d’un expéditeur sûr, a été envoyé à un destinataire sécurisé ou provient d’un serveur source de courrier sur la liste d’autorisations IP. Pour plus d’informations, consultez [Créer des listes d’expéditeurs sécurisés dans EOP](create-safe-sender-lists-in-office-365.md).|Le message est remis dans la boîte aux lettres des destinataires.|
|0, 1|Le filtrage du courrier indésirable a déterminé que le message n’était pas du courrier indésirable.|Le message est remis dans la boîte aux lettres des destinataires.|
|5, 6|Filtrage du courrier indésirable marqué comme **courrier indésirable**|Le message est envoyé vers le dossier Courrier indésirable des destinataires.|
|9 |Le filtrage du courrier indésirable a marqué le message comme **courrier indésirable à haut niveau de confiance**|Le message est envoyé vers le dossier Courrier indésirable des destinataires.|

Vous remarquerez que SCL 2, 3, 4, 7 et 8 ne sont pas utilisés par le filtrage du courrier indésirable.

Vous pouvez utiliser des règles de flux de messagerie (également appelées règles de transport) pour marquer la liste de contrôle d’accès aux messages. Si vous utilisez une règle de flux de courrier pour définir la liste SCL, les valeurs 5 ou 6 déclenchent l’action de filtrage du courrier indésirable pour le **courrier indésirable**, et les valeurs 7, 8 ou 9 déclenchent l’action de filtrage du courrier indésirable pour le **courrier indésirable à haut niveau de confiance**. Pour plus d’informations, consultez [Utiliser des règles de flux de messagerie pour définir le niveau de probabilité de courrier indésirable (SCL) dans les messages](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

À l’instar de la liste SCL, le niveau de réclamation en bloc (BCL) identifie les e-mails en bloc incorrects (également appelé _courrier gris_). Un niveau BCL supérieur indique qu’un courrier en nombre est susceptible de générer des plaintes (et par conséquent plus susceptible d’être du courrier indésirable). Vous configurez le seuil BCL dans les stratégies anti-courrier indésirable. Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md), [le niveau de réclamation en bloc (BCL) dans EOP](bulk-complaint-level-values.md)) et [quelle est la différence entre le courrier indésirable et le courrier électronique en bloc ?](what-s-the-difference-between-junk-email-and-bulk-email.md)

****

![Petit icône de LinkedIn Learning.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Vous débutez avec Microsoft 365 ?** Découvrez des cours vidéo gratuits pour **les administrateurs Microsoft 365 et les professionnels de l’informatique, proposés** par LinkedIn Learning.
