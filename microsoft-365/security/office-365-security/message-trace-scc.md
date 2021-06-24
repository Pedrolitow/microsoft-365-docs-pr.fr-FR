---
title: Suivi des messages dans le portail Microsoft 365 Defender web
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
localization_priority: Normal
ms.assetid: 3e64f99d-ac33-4aba-91c5-9cb4ca476803
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent utiliser le lien de suivi des messages dans le portail Microsoft 365 Defender pour savoir ce qui est arrivé aux messages.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f7b6f7b12086e46c6ad93b60e8c510ea533815a1
ms.sourcegitcommit: ebb1c3b4d94058a58344317beb9475c8a2eae9a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2021
ms.locfileid: "53108126"
---
# <a name="message-trace-in-the-microsoft-365-defender-portal"></a>Suivi des messages dans le portail Microsoft 365 Defender web

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Le suivi des messages dans le portail Microsoft 365 Defender suit les messages électroniques lors de leur déplacement dans Exchange Online organisation. Vous pouvez déterminer si un message a été reçu, rejeté, différé ou remis par le service. Cela indique également les actions entamées par rapport au message avant qu'il atteigne son statut final.

Vous pouvez utiliser les informations du suivi des messages pour répondre efficacement aux questions des utilisateurs sur ce qui est arrivé aux messages, résoudre les problèmes de flux de messagerie et valider les modifications de stratégie.

> [!NOTE]
> Le suivi des messages dans Microsoft 365 Defender portail est simplement un accès au suivi des messages dans Exchange d’administration. Pour plus d’informations, voir [suivi des messages dans le centre d’administration Exchange moderne.](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous devez être membre des groupes  de  rôles Gestion de l’organisation, Gestion de la conformité ou Service d’Exchange Online pour utiliser le suivi des messages.  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques**: l’appartenance au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux _utilisateurs_ les autorisations et autorisations requises pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

- Le nombre maximal de messages affichés dans les résultats d’un suivi des messages dépend du type de rapport que vous avez sélectionné (voir la section Choisir le [type](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac#choose-report-type) de rapport pour plus d’informations). [L’cmdlet Get-HistoricalSearch](/powershell/module/exchange/get-historicalsearch) dans Exchange Online PowerShell ou EOP PowerShell autonome renvoie tous les messages dans les résultats.

## <a name="open-message-trace"></a>Ouvrir le suivi des messages

Dans le portail Microsoft 365 Defender ( <https://security.microsoft.com> ), go to Email & **collaboration** Exchange \> **message trace**. Ou, pour aller directement à la page de suivi des messages, utilisez <https://admin.exchange.microsoft.com/#/messagetrace> .

À ce stade, le suivi des messages dans le EAC s’ouvre. Pour plus d’informations, voir [suivi des messages dans le centre d’administration Exchange moderne.](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac)
