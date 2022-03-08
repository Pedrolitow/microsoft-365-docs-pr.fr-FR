---
title: Alertes du service des destinataires externes
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
f1.keywords:
- NOCSH
description: Utilisez les alertes du service des destinataires externes pour surveiller les boîtes aux lettres en attente qui atteignent leur quota de boîte aux lettres.
ms.openlocfilehash: 931be51ee51bd5557633415004eed9a1c7e77888
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63331174"
---
# <a name="service-alerts-for-messages-pending-delivery-to-external-recipients-in-exchange-online-monitoring"></a>Alertes de service pour les messages en attente de remise à des destinataires externes dans Exchange Online surveillance

Les alertes de service informent les administrateurs de la file d’envoi de messages à des destinataires externes en dehors Exchange Online. Ces alertes peuvent nécessiter des actions de correction en dehors de Microsoft, mais elles peuvent vous fournir les informations nécessaires à la correction.

Ces alertes de service sont affichées dans le Centre d'administration Microsoft 365. Pour afficher ces alertes de service, allez sur **HealthService** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**health**</a> >  **Exchange Online** puis cliquez sur **l’onglet Problèmes** actifs. Le nom de ces alertes de service est « Message Queueing to External Recipients Above Thresholds ».

![Alerte de service pour les messages en attente de remise à des destinataires externes affichés dans Exchange Online tableau de bord de surveillance.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts1.png)

Lorsque vous double-cliquez sur l’alerte de service, une page volante semblable à la suivante s’affiche.

![Contenu de l’alerte de service pour les messages en attente de remise à des destinataires externes.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts2.png)

## <a name="what-do-these-service-alerts-indicate"></a>Qu’indiquent ces alertes de service ?

Les alertes de service pour les messages en attente de remise à des destinataires externes vous informent que les messages destinés à des destinataires en dehors de la Exchange Online peuvent être retardés. La file d’attente des messages peut être causée par votre environnement local ou par une solution de messagerie ou de journaling tierce.

Voici quelques raisons courantes de mettre des messages en file d’attente à des destinataires externes. Toutefois, les problèmes à l’origine de ces alertes de service peuvent ne pas être limités à ces raisons.

- Modifications DNS

- Taux d’envoi excessifs

- Agents de transfert de messages (MTA) locaux ou solutions de journaling avec un espace disque faible à nul

- MTAs dans la backpressure

- Problèmes réseau, y compris les équilibreurs de charge

- Problèmes de certificat

Chaque alerte de service contient des recommandations de haut niveau pour résoudre le problème. L’alerte de service indique également le nombre de messages mis en file d’attente au moment de l’alerte, le domaine vers lequel les messages sont mis en file d’attente et le code d’erreur SMTP associé à la plupart des messages en file d’attente.

Pour plus d’informations sur la détermination de la cause première de ces alertes de service, voir [l’intelligence du flux de messagerie dans Exchange Online](../security/office-365-security/mail-flow-intelligence-in-office-365.md). Cet article inclut également des suggestions d’actions pour résoudre la cause première.

> [!NOTE]
> Microsoft ne peut pas tenir compte de chaque code d’erreur SMTP fourni par des fournisseurs tiers. Par conséquent, les administrateurs peuvent être tenus d’examiner les codes d’erreur spécifiques à leur MTA ou solutions de journaling utilisées par leur organisation.

## <a name="more-information"></a>Plus d’informations

Si votre organisation a récemment créé ou modifié des connecteurs de flux de messagerie dans votre organisation Exchange Online ou sur site, consultez les articles suivants pour plus d’informations.

- [Configurer le flux de messagerie à l’aide de connecteurs dans Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)

- [Configurer des connecteurs pour acheminer le courrier électronique](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail)

- [Meilleures pratiques pour le flux de Messagerie](/exchange/mail-flow-best-practices/mail-flow-best-practices)

- [Informations sur le flux de messagerie dans le centre de sécurité et conformité](/microsoft-365/security/office-365-security/mail-flow-insights-v2)

- [Informations sur les files d’attente dans le tableau de bord de flux de messagerie](/microsoft-365/security/office-365-security/mfi-queue-alerts-and-queues#queues-insight-in-the-mail-flow-dashboard)

- [Suivre un message électronique dans Exchange Online](/exchange/monitoring/trace-an-email-message/trace-an-email-message)
