---
title: Informations sur les flux de courrier sortants et entrants dans le tableau de bord flux de courrier
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: f2738dec-41b0-43c4-b814-84c0a4e45c6d
description: Les administrateurs peuvent en savoir plus sur les insights de flux de courrier sortant et entrant dans le tableau de bord flux de courrier du Centre de sécurité & conformité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f856e2b9a4829531966802f2594f26c19e6ab7e5
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131193"
---
# <a name="outbound-and-inbound-mail-flow-insight-in-the-security--compliance-center"></a>Informations sur les flux de courrier sortants et entrants dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

L’insight de **flux de courrier sortant et entrant** dans le [tableau de bord flux de](mail-flow-insights-v2.md) messagerie du [Centre de sécurité & conformité](https://protection.office.com) combine les informations du [rapport connecteur](view-mail-flow-reports.md#connector-report) et de l’ancien **rapport de vue d’ensemble TLS** à un seul emplacement.

Le widget affiche le chiffrement TLS utilisé pour la connexion lorsque des messages sont remis à et à partir de votre organisation. Les connexions établies avec d’autres services de messagerie sont chiffrées par TLS lorsque TLS est proposé par les deux côtés. Le widget offre un instantané de la dernière semaine de flux de courrier.

:::image type="content" source="../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png" alt-text="Widget de flux de courrier sortant et entrant dans le tableau de bord flux de courrier du Centre de sécurité & conformité" lightbox="../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png":::

Les informations contenues dans le widget sont liées aux connecteurs et à la protection des messages TLS dans Microsoft 365. Pour plus d'informations, voir les rubriques suivantes :

- [Configurer le flux de messagerie à l’aide des connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
- [Mode d’utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie](../../compliance/exchange-online-uses-tls-to-secure-email-connections.md)
- [Informations de référence techniques sur le chiffrement dans Microsoft 365](../../compliance/technical-reference-details-about-encryption.md)

## <a name="message-protected-in-transit-by-tls"></a>Message protégé en transit (par TLS)

Lorsque vous cliquez sur **Afficher les détails** sur le widget, le menu volant **Message protégé en transit (par TLS)** affiche la protection TLS pour les messages entrant et sortant de votre organisation.

:::image type="content" source="../../media/mfi-outbound-and-inbound-mail-flow-report-details.png" alt-text="Menu volant Messages protégés en transit (par TLS) qui s’affiche après avoir cliqué sur Afficher les détails sur le widget de courrier sortant et entrant" lightbox="../../media/mfi-outbound-and-inbound-mail-flow-report-details.png":::

Actuellement, TLS 1.2 est la version la plus sécurisée de TLS offerte par Microsoft 365. Souvent, vous devez connaître le chiffrement TLS utilisé pour les audits de conformité. Vous n’avez probablement pas de relation directe avec la plupart des serveurs de messagerie source et de destination (vous ne les possédez pas et Microsoft non plus), vous n’avez donc pas beaucoup d’options pour améliorer le chiffrement TLS utilisé par ces serveurs.

Toutefois, vous pouvez utiliser [des connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) pour garantir la meilleure protection TLS disponible pour les messages envoyés entre vos serveurs de messagerie et Microsoft 365. Le flux de courrier entre Microsoft 365 et vos propres serveurs de messagerie ou serveurs qui appartiennent à vos partenaires est souvent plus important et sensible que les messages standard. Vous souhaiterez donc appliquer une sécurité et une vigilance supplémentaires à ces messages.

Vous pouvez mettre à niveau ou corriger vos propres serveurs de messagerie pour améliorer le chiffrement TLS utilisé, ou contacter vos partenaires pour faire de même. Le **rapport du connecteur** affiche à la fois le volume de flux de messagerie et le chiffrement TLS pour les messages qui utilisent vos connecteurs Microsoft 365.

Vous pouvez cliquer sur le lien **du rapport connecteur** pour accéder au [rapport connecteur](view-mail-flow-reports.md#connector-report). Les insights suivants peuvent être disponibles sur la page de **rapport du connecteur** si la condition associée a été détectée :

- **Connecteur partenaire entrant qui voit un flux de messagerie TLS1.0 significatif**
- **Le connecteur OnPremises entrant voit un flux de messagerie TLS1.0 significatif**

Pour les connexions TLS 1.0, vous devez vraiment mettre à niveau votre serveur de messagerie ou le serveur de votre partenaire afin d’éviter tout problème lorsque la prise en charge de TLS 1.0 est éventuellement dépréciée dans Microsoft 365.

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, consultez [les insights de flux de courrier dans le Centre de sécurité & conformité](mail-flow-insights-v2.md).
