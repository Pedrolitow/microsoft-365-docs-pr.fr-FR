---
title: Alertes de service des destinataires externes
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/31/2022
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
f1.keywords:
- NOCSH
description: Utilisez des alertes de service de destinataires externes pour surveiller les boîtes aux lettres en attente qui atteignent leur quota de boîtes aux lettres.
ROBOTS: NOINDEX
ms.openlocfilehash: 417dc0d7a545b1b345e20806a571760480f426d3
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68172486"
---
# <a name="service-alerts-for-messages-pending-delivery-to-external-recipients-in-exchange-online-monitoring"></a>Alertes de service pour les messages en attente de remise aux destinataires externes dans Exchange Online surveillance

Les alertes de service informent les administrateurs de la mise en file d’attente de courrier aux destinataires externes en dehors de Exchange Online. Ces alertes peuvent nécessiter des actions de correction en dehors de Microsoft, mais elles peuvent vous fournir les informations nécessaires pour y remédier.

Ces alertes de service sont affichées dans le Centre d'administration Microsoft 365. Pour afficher ces alertes de service, accédez à **Health** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**État des services**</a> >  **Exchange Online**, puis cliquez sur l’onglet **Problèmes actifs**. Le nom de ces alertes de service est « File d’attente de messages vers des destinataires externes au-dessus des seuils ».

![Alerte de service pour les messages en attente de remise aux destinataires externes affichés dans le tableau de bord de surveillance Exchange Online.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts1.png)

Lorsque vous double-cliquez sur l’alerte de service, une page de menu volant similaire à ce qui suit s’affiche.

![Contenu de l’alerte de service pour les messages en attente de remise aux destinataires externes.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts2.png)

## <a name="what-do-these-service-alerts-indicate"></a>Qu’indiquent ces alertes de service ?

Les alertes de service pour les messages en attente de remise aux destinataires externes vous informent que les messages destinés aux destinataires en dehors de Exchange Online peuvent être retardés. La mise en file d’attente des messages peut être due à votre environnement local ou à une solution de messagerie ou de journalisation tierce.

Voici quelques raisons courantes pour mettre en file d’attente des messages vers des destinataires externes. Toutefois, les problèmes à l’origine de ces alertes de service peuvent ne pas être limités à ces raisons.

- Modifications DNS

- Taux d’envoi excessifs

- Agents de transfert de messages locaux (MTA) ou solutions de journalisation avec peu ou pas d’espace disque libre

- MtAs in backpressure

- Problèmes réseau, y compris les équilibreurs de charge

- Problèmes de certificat

Chaque alerte de service contient des recommandations générales pour résoudre le problème. L’alerte de service indique également le nombre de messages mis en file d’attente au moment de l’alerte, le domaine vers lequel les messages sont mis en file d’attente et le code d’erreur SMTP associé à la plupart des messages en file d’attente.

Pour plus d’informations sur la détermination de la cause racine de ces alertes de service, consultez [l’intelligence du flux de courrier dans Exchange Online](../security/office-365-security/mail-flow-intelligence-in-office-365.md). Cet article inclut également des actions suggérées pour corriger la cause racine.

> [!NOTE]
> Microsoft ne peut pas tenir compte de chaque code d’erreur SMTP fourni par des fournisseurs tiers. Par conséquent, les administrateurs peuvent être tenus d’examiner les codes d’erreur spécifiques à leurs solutions MTA ou de journalisation utilisées par leur organisation.

## <a name="more-information"></a>Plus d’informations

Si votre organisation a récemment créé ou modifié des connecteurs de flux de messagerie dans votre organisation locale ou Exchange Online, consultez les articles suivants pour plus d’informations.

- [Configurer le flux de messagerie à l’aide de connecteurs dans Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)

- [Configurer des connecteurs pour acheminer le courrier électronique](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail)

- [Meilleures pratiques pour le flux de Messagerie](/exchange/mail-flow-best-practices/mail-flow-best-practices)

- [Informations sur le flux de messagerie dans le centre de sécurité et conformité](/microsoft-365/security/office-365-security/mail-flow-insights-v2)

- [Informations sur les files d’attente dans le tableau de bord de flux de messagerie](/microsoft-365/security/office-365-security/mfi-queue-alerts-and-queues#queues-insight-in-the-mail-flow-dashboard)

- [Trace d’un e-mail dans Exchange Online](/exchange/monitoring/trace-an-email-message/trace-an-email-message)
