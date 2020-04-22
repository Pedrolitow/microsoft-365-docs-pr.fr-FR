---
title: Utiliser le portail supprimer de la liste pour vous supprimer de la liste des expéditeurs bloqués
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/18/2016
audience: ITPro
ms.topic: troubleshooting
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0bcecdd4-3343-4cc0-9e58-e19d4de515e8
ms.collection:
- M365-security-compliance
description: Vous recevez un message d’erreur lorsque vous essayez d’envoyer un message électronique à un destinataire dont l’adresse de messagerie est dans Microsoft 365 ? Si vous pensez que vous ne devriez pas recevoir le message d’erreur, vous pouvez utiliser le portail supprimer de la liste pour vous supprimer de la liste des expéditeurs bloqués.
ms.openlocfilehash: 39f2c9335f162f26e8bf07a213236e0e0eefef2a
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43636403"
---
# <a name="use-the-delist-portal-to-remove-yourself-from-the-blocked-senders-list"></a>Utiliser le portail supprimer de la liste pour vous supprimer de la liste des expéditeurs bloqués

Vous recevez un message d’erreur lorsque vous essayez d’envoyer un message électronique à un destinataire dont l’adresse de messagerie est dans Microsoft 365 ? Si vous pensez que vous ne devriez pas recevoir le message d’erreur, vous pouvez utiliser le portail supprimer de la liste pour vous supprimer de la liste des expéditeurs bloqués.

## <a name="what-is-the-blocked-senders-list"></a>Qu’est-ce que la liste des expéditeurs bloqués ?

Microsoft utilise la liste des expéditeurs bloqués pour protéger ses clients contre le courrier indésirable, l'usurpation d'identité et les attaques par hameçonnage. L’adresse IP de votre serveur de messagerie, autrement dit, l’adresse que votre serveur de messagerie utilise pour s’identifier sur Internet, a été marquée comme une menace potentielle pour Microsoft 365 pour l’une des raisons. Lorsque Microsoft 365 ajoute l’adresse IP à la liste, il empêche toute communication supplémentaire entre l’adresse IP et l’un de nos clients via nos centres de connaissances.

Vous savez que vous avez été ajouté à la liste si vous recevez une réponse à un courrier électronique incluant une erreur ressemblant à ce qui suit :

> 550 5.7.606-649 accès refusé, IP d’envoi interdit [_adresse IP_]; Pour demander la suppression de cette liste, https://sender.office.com/ visitez le site et suivez les instructions. Pour plus d’informations, consultez la rubrique [notifications de non-remise aux messages électroniques dans Exchange Online](https://docs.microsoft.com/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

où  _IP address_ est l'adresse IP de l'ordinateur sur lequel s'exécute le serveur de messagerie.

### <a name="to-use-delist-portal-to-remove-yourself-from-the-blocked-senders-list"></a>Pour utiliser le portail déliste pour vous supprimer de la liste des expéditeurs bloqués

1. Dans un navigateur web, accédez à [https://sender.office.com](https://sender.office.com).

2. Suivez les instructions de la page. Assurez-vous que vous utilisez l'adresse de messagerie à laquelle le message d'erreur a été envoyé et l'adresse IP qui est spécifiée dans le message d'erreur. Vous ne pouvez entrer qu'une adresse de messagerie et une adresse IP par visite.

3. Cliquez sur **Envoyer**.

    Le portail envoie un courrier électronique à l'adresse de messagerie que vous indiquez. Le message électronique se présente comme suit : ![capture d’écran du courrier électronique reçu lorsque vous envoyez une demande via le portail supprimer de la liste](../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png)

4. Cliquez sur le lien de confirmation dans le courrier électronique envoyé par le portail de suppression de la liste.

    Vous revenez au portail Supprimer de la liste.

5. Dans le portail Supprimer de la liste, cliquez sur **Supprimer l'adresse IP de la liste**.

    Une fois que l’adresse IP a été supprimée de la liste des expéditeurs bloqués, les messages électroniques provenant de cette adresse IP seront remis aux destinataires qui utilisent Microsoft 365. Par conséquent, assurez-vous que vous êtes sûr que les messages envoyés à partir de cette adresse IP ne seront pas injurieux ou malveillants ; dans le cas contraire, l’adresse IP peut être de nouveau bloquée.

    > [!NOTE]
    > Cette opération peut prendre jusqu’à 24 heures ou les résultats peuvent varier considérablement avant la suppression des restrictions.

Consultez la rubrique [créer des listes d’expéditeurs approuvés dans office 365](create-safe-sender-lists-in-office-365.md) et protection contre le [courrier indésirable sortant dans Office 365](outbound-spam-controls.md) pour empêcher la liste de blocage sur IP.
