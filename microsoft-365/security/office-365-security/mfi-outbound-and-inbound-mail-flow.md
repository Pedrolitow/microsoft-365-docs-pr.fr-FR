---
title: Vue du flux de messagerie sortant et entrant dans le tableau de bord de flux de messagerie
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 8/7/2018
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: f2738dec-41b0-43c4-b814-84c0a4e45c6d
description: Les administrateurs peuvent en savoir plus sur le flux de messages entrants et sortants dans le tableau de bord de flux de messagerie dans le centre de sécurité & conformité.
ms.openlocfilehash: 347e53c51c347f12795008d39458773a94ff433f
ms.sourcegitcommit: c04f1207cfaddac2a9abef38967c17d689756a96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "46577390"
---
# <a name="outbound-and-inbound-mail-flow-insight-in-the-security--compliance-center"></a>Vue du flux de messagerie sortant et entrant dans le centre de sécurité & conformité

L’analyse du **flux de messagerie sortant et entrant** dans le [tableau de bord de flux de messagerie](mail-flow-insights-v2.md) dans le centre de sécurité & conformité combine les informations du rapport de [connecteur](view-mail-flow-reports.md#connector-report) et de l’ancien **rapport de vue d’ensemble TLS** à un seul emplacement.

Le widget affiche le chiffrement TLS utilisé pour la connexion lors de la remise de messages à votre organisation. Les connexions établies avec d’autres services de messagerie sont chiffrées par TLS lorsque TLS est offert par les deux côtés. Le widget offre un instantané de la dernière semaine du flux de messagerie.

![Widget flux de messagerie sortant et entrant dans le tableau de bord de flux de messagerie dans le centre de sécurité & conformité](../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png)

Les informations contenues dans le widget sont liées aux connecteurs et à la protection des messages TLS dans Microsoft 365. Pour plus d'informations, voir les rubriques suivantes :

- [Configurer le flux de messagerie à l’aide des connecteurs](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
- [Utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie](https://docs.microsoft.com/microsoft-365/compliance/exchange-online-uses-tls-to-secure-email-connections)
- [Informations de référence technique sur le chiffrement dans Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/technical-reference-details-about-encryption)

## <a name="message-protected-in-transit-by-tls"></a>Message protégé en transit (par TLS)

Lorsque vous cliquez sur **afficher les détails** dans le widget, le menu volant **message protégé en transit (par TLS)** vous indique la protection TLS pour les messages entrants et sortants de votre organisation.

![Messages de la fenêtre mobile protected in transit (par TLS) qui s’affiche une fois que vous avez cliqué sur Afficher les détails dans le widget courrier électronique entrant et sortant](../../media/mfi-outbound-and-inbound-mail-flow-report-details.png)

Actuellement, TLS 1,2 est la version la plus sécurisée de TLS offerte par Microsoft 365. En règle générale, vous devez déterminer le chiffrement TLS utilisé pour les audits de conformité. Vous n’avez probablement pas de relation directe avec la plupart des serveurs de messagerie source et de destination (vous n’êtes pas propriétaire, ni Microsoft), de sorte que vous n’avez pas de nombreuses options pour améliorer le chiffrement TLS utilisé par ces serveurs.

Toutefois, vous pouvez utiliser des [connecteurs](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) pour garantir la meilleure protection TLS disponible pour les messages échangés entre vos serveurs de messagerie et Microsoft 365. Le flux de messagerie entre Microsoft 365 et vos propres serveurs de messagerie ou serveurs qui appartiennent à vos partenaires est souvent plus important et plus sensible que les messages normaux, de sorte que vous souhaitez appliquer une sécurité supplémentaire et la vigilance de ces messages.

Vous pouvez mettre à niveau ou réparer vos propres serveurs de messagerie pour améliorer le chiffrement TLS utilisé ou contacter vos partenaires pour qu’ils effectuent la même opération. Le **rapport de connecteur** affiche le volume de flux de messagerie et le chiffrement TLS pour les messages qui utilisent vos connecteurs Microsoft 365.

Vous pouvez cliquer sur le lien du **rapport de connecteur** pour accéder au [rapport du connecteur](view-mail-flow-reports.md#connector-report). Les informations suivantes peuvent être disponibles sur la page de **rapport du connecteur** si la condition associée a été détectée :

- **Le connecteur de partenaire entrant voit un flux de messagerie TLS 1.0 important**
- **Connecteur OnPremises entrant présentant un flux de messagerie TLS 1.0 important**

Pour les connexions 1,0 TLS, vous devez vraiment obtenir votre serveur de messagerie ou le serveur de votre partenaire mis à niveau ou résolu afin d’éviter tout problème lorsque la prise en charge de TLS 1,0 est finalement déconseillée dans Microsoft 365.

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur les autres informations du tableau de bord de flux de messagerie, consultez [la rubrique mail Flow Insights in the Security & Compliance Center](mail-flow-insights-v2.md).
