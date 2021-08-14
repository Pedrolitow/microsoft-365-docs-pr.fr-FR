---
title: Supprimez-vous de la liste des expéditeurs bloqués
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/18/2016
audience: ITPro
ms.topic: troubleshooting
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0bcecdd4-3343-4cc0-9e58-e19d4de515e8
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous allez apprendre à utiliser le portail Supprimer de la liste pour vous supprimer de la liste Microsoft 365 les expéditeurs bloqués.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7beee058a85d7ab44a6a4a94b362fa669537f573754de8558d713332d897843f
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "56854707"
---
# <a name="use-the-delist-portal-to-remove-yourself-from-the-blocked-senders-list"></a>Utiliser le portail Retirer d’une liste pour vous supprimer de la liste des expéditeurs bloqués

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Recevez-vous un message d’erreur lorsque vous essayez d’envoyer un message électronique à un destinataire dont l’adresse de messagerie est Microsoft 365 ? Si vous pensez ne pas recevoir le message d’erreur, vous pouvez utiliser le portail supprimer de la liste pour vous supprimer de la liste des expéditeurs bloqués.

## <a name="what-is-the-blocked-senders-list"></a>Qu’est-ce que la liste des expéditeurs bloqués ?

Microsoft utilise la liste des expéditeurs bloqués pour protéger ses clients contre le courrier indésirable, l'usurpation d'identité et les attaques par hameçonnage. L’adresse IP de votre serveur de messagerie, c’est-à-dire l’adresse que votre serveur de messagerie utilise pour s’identifier sur Internet, a été marquée comme une menace potentielle pour Microsoft 365 pour diverses raisons. Lorsque Microsoft 365 ajoute l’adresse IP à la liste, cela empêche toute communication supplémentaire entre l’adresse IP et l’un de nos clients via nos centres de données.

Vous savez que vous avez été ajouté à la liste si vous recevez une réponse à un courrier électronique incluant une erreur ressemblant à ce qui suit :

> 550 5.7.606-649 Accès refusé, adresse _IP_ d’envoi interdite [ adresse IP ]; Pour demander la suppression de cette liste, visitez <https://sender.office.com/> et suivez les instructions. Pour plus d’informations, [consultez les rapports de non-remise](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online)par courrier électronique Exchange Online .

où  _IP address_ est l'adresse IP de l'ordinateur sur lequel s'exécute le serveur de messagerie.

### <a name="to-use-delist-portal-to-remove-yourself-from-the-blocked-senders-list"></a>Pour utiliser le portail supprimer de la liste pour vous supprimer de la liste des expéditeurs bloqués

1. Dans un navigateur web, accédez à <https://sender.office.com>.

2. Suivez les instructions de la page. Assurez-vous que vous utilisez l'adresse de messagerie à laquelle le message d'erreur a été envoyé et l'adresse IP qui est spécifiée dans le message d'erreur. Vous ne pouvez entrer qu'une adresse de messagerie et une adresse IP par visite.

3. Cliquez sur **Envoyer**.

    Le portail envoie un courrier électronique à l'adresse de messagerie que vous indiquez. L’e-mail ressemblera à ce qui suit : Capture d’écran du courrier électronique reçu lorsque vous envoyez une demande ![ via le portail Delist](../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png)

4. Cliquez sur le lien de confirmation dans le courrier électronique envoyé par le portail de suppression de la liste.

    Vous revenez au portail Supprimer de la liste.

5. Dans le portail Supprimer de la liste, cliquez sur **Supprimer l'adresse IP de la liste**.

    Une fois l’adresse IP supprimée de la liste des expéditeurs bloqués, les messages électroniques provenant de cette adresse IP sont remis aux destinataires qui utilisent Microsoft 365. Assurez-vous donc que les messages électroniques envoyés à partir de cette adresse IP ne seront pas abusifs ou malveillants ; Dans le cas contraire, l’adresse IP risque d’être de nouveau bloquée.

    > [!NOTE]
    > Cela peut prendre jusqu’à 24 heures ou les résultats peuvent varier considérablement avant la suppression des restrictions.

Voir [Créer des listes d’expéditeurs](create-safe-sender-lists-in-office-365.md) sûrs dans EOP et la protection contre le courrier indésirable sortant dans [EOP](outbound-spam-controls.md) pour empêcher le blocage d’une adresse IP.