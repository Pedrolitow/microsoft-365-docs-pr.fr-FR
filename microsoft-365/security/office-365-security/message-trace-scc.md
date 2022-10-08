---
title: Suivi des messages dans le portail Microsoft 365 Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.collection: m365-security
ms.localizationpriority: medium
ms.assetid: 3e64f99d-ac33-4aba-91c5-9cb4ca476803
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent utiliser le lien de suivi des messages dans le portail Microsoft 365 Defender pour savoir ce qui est arrivé aux messages.
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: 7412cade7e934ca7095e308a40558084a8404ddf
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68086937"
---
# <a name="message-trace-in-the-microsoft-365-defender-portal"></a>Suivi des messages dans le portail Microsoft 365 Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Le suivi des message suit les messages électroniques pendant leur circulation dans votre organisation Exchange Online. Vous pouvez déterminer si un message a été reçu, rejeté, différé ou remis par le service. Cela indique également les actions entamées par rapport au message avant qu'il atteigne son statut final.

Vous pouvez utiliser les informations de la trace des messages pour répondre efficacement aux questions des utilisateurs sur ce qui est arrivé aux messages, résoudre les problèmes de flux de courrier et valider les modifications de stratégie.

> [!NOTE]
> La trace des messages dans le portail Microsoft 365 Defender n’est qu’une transmission à la trace des messages dans le Centre d’administration Exchange. Pour plus d’informations, consultez [la trace des messages dans le centre d’administration Exchange moderne](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous devez être membre des groupes de **rôles Gestion de l’organisation**, **Gestion de la conformité** ou **Support technique** dans **Exchange Online** pour utiliser la trace des messages. Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** : L’appartenance au rôle Azure Active Directory correspondant dans le Centre d'administration Microsoft 365 donne aux utilisateurs les autorisations _et_ autorisations nécessaires pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

- Le nombre maximal de messages affichés dans les résultats d’une trace de message dépend du type de rapport que vous avez sélectionné (voir la section [Choisir le type de rapport](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac#choose-report-type) pour plus d’informations). L’applet [de commande Get-HistoricalSearch](/powershell/module/exchange/get-historicalsearch) dans Exchange Online PowerShell ou EOP PowerShell autonome retourne tous les messages dans les résultats.

## <a name="open-message-trace"></a>Ouvrir la trace des messages

Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & **trace des messages Exchange** de **collaboration**\>. Pour accéder directement à la page de suivi des messages, utilisez <https://admin.exchange.microsoft.com/#/messagetrace>.

À ce stade, la trace des messages dans le Centre d’administration des messages s’ouvre. Pour plus d’informations, consultez [la trace des messages dans le centre d’administration Exchange moderne](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
