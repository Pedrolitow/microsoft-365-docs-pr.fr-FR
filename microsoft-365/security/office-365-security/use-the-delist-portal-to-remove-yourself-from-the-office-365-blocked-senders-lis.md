---
title: Supprimez-vous de la liste des expéditeurs bloqués et de l’adresse 5.7.511 Erreurs d’accès refusé
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/18/2016
audience: ITPro
ms.topic: troubleshooting
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 0bcecdd4-3343-4cc0-9e58-e19d4de515e8
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous allez apprendre à utiliser le portail Supprimer de la liste pour vous supprimer de la liste Microsoft 365 les expéditeurs bloqués. Il s’agit de la meilleure réponse pour résoudre les erreurs d’accès 5.7.511.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 58ddb2913ce7ecd047b1d5acb360c8f4c9ff5074
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775783"
---
# <a name="use-the-delist-portal-to-remove-yourself-from-the-blocked-senders-list-and-address-57511-access-denied-errors"></a>Utiliser le portail supprimer de la liste pour vous supprimer de la liste des expéditeurs bloqués et adresse 5.7.511 Erreurs d’accès refusé

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Recevez-vous un message d’erreur lorsque vous essayez d’envoyer un message électronique à un destinataire dont l’adresse de messagerie est en Microsoft 365 (par exemple, et l’adresse 5.7.511 Accès refusé) ? Si vous pensez ne pas recevoir le message d’erreur, vous pouvez utiliser le portail Supprimer de la liste pour vous supprimer de la liste des expéditeurs bloqués.

## <a name="what-is-the-blocked-senders-list"></a>Qu’est-ce que la liste des expéditeurs bloqués ?

Microsoft utilise la liste des expéditeurs bloqués pour protéger ses clients contre le courrier indésirable, l'usurpation d'identité et les attaques par hameçonnage. L’adresse IP de votre serveur de messagerie, c’est-à-dire l’adresse que votre serveur de messagerie utilise pour s’identifier sur Internet, a été marquée comme une menace potentielle pour Microsoft 365 pour diverses raisons. Lorsque Microsoft 365 ajoute l’adresse IP à la liste, cela empêche toute communication supplémentaire entre l’adresse IP et l’un de nos clients via nos centres de données.

Vous savez que vous avez été ajouté à la liste si vous recevez une réponse à un courrier électronique incluant une erreur ressemblant à ce qui suit :

> 550 5.7.606-649 Accès refusé, adresse IP d’envoi interdite [_adresse IP_] (ex. 5.7.511 Accès refusé) <https://sender.office.com/> : pour demander la suppression de cette liste, visitez et suivez les instructions. Pour plus d’informations, [consultez les rapports de non-remise par courrier électronique Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

où  _IP address_ est l'adresse IP de l'ordinateur sur lequel s'exécute le serveur de messagerie.

## <a name="verify-senders-before-removing-them-from-the-blocked-senders-list"></a>Vérifier les expéditeurs avant de les supprimer de la liste des expéditeurs bloqués

Il existe de bonnes raisons pour que les expéditeurs se placent sur la liste des expéditeurs bloqués, mais des erreurs peuvent se produire. Regardez cette vidéo pour obtenir une explication équilibrée des expéditeurs bloqués et de la liste.
<p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvD]

## <a name="to-use-delist-portal-to-remove-yourself-from-the-blocked-senders-list-after-errors-like-57511-access-denied"></a>Pour utiliser le portail supprimer de la liste pour vous supprimer de la liste des expéditeurs bloqués (après des erreurs telles que 5.7.511 Accès refusé)

1. Dans un navigateur web, accédez à <https://sender.office.com>.

2. Suivez les instructions de la page. Assurez-vous que vous utilisez l'adresse de messagerie à laquelle le message d'erreur a été envoyé et l'adresse IP qui est spécifiée dans le message d'erreur. Vous ne pouvez entrer qu'une adresse de messagerie et une adresse IP par visite.

3. Cliquez sur **Envoyer**.

    Le portail envoie un courrier électronique à l'adresse de messagerie que vous indiquez. Le courrier électronique devrait ressembler à ce qui suit :

    ![Capture d’écran du courrier électronique reçu lorsque vous envoyez une demande via le portail Delist.](../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png)

4. Cliquez sur le lien de confirmation dans le courrier électronique envoyé par le portail de suppression de la liste.

    Vous revenez au portail Supprimer de la liste.

5. Dans le portail Supprimer de la liste, cliquez sur **Supprimer l'adresse IP de la liste**.

    Une fois l’adresse IP supprimée de la liste des expéditeurs bloqués, les messages électroniques provenant de cette adresse IP sont remis aux destinataires qui utilisent Microsoft 365. Assurez-vous donc que les messages électroniques envoyés à partir de cette adresse IP ne seront ni abusifs ni malveillants . Dans le cas contraire, l’adresse IP risque d’être de nouveau bloquée.

    > [!NOTE]
    > Cela peut prendre jusqu’à 24 heures ou les résultats peuvent varier considérablement avant la suppression des restrictions.

Voir [Créer des listes d’expéditeurs sûrs dans EOP](create-safe-sender-lists-in-office-365.md) et la protection contre le courrier indésirable sortant dans [EOP](outbound-spam-controls.md) pour empêcher le blocage d’une adresse IP.

### <a name="how-do-fix-error-code-57511"></a>Comment corriger le code d’erreur 5.7.511

En cas de problème de remise d’un message électronique que vous avez envoyé, Microsoft 365 ou Office 365 vous envoie un e-mail pour vous en informer. L’e-mail que vous recevez est une notification d’état de remise. La notification la plus courante est la notification d’échec de remise qui vous informe qu’un message n’a pas été remis. Dans certains cas, Microsoft doit effectuer des enquêtes supplémentaires sur le trafic provenant de votre adresse IP, et si vous recevez le code de la rapport de non-réception 5.7.511, vous ne pourrez pas utiliser le portail de liste.

> 550 5.7.511 Accès refusé, expéditeur interdit[xxx.xxx.xxx.xxx]. Pour demander la suppression de cette liste, delist@messaging.microsoft.com. Pour plus d’informations, voir <https://go.microsoft.com/fwlink/?LinkId=526653>.

Dans l’e-mail pour demander la suppression de cette liste, fournissez le code de la NDR complet et l’adresse IP. Microsoft vous contactera dans les 48 heures avec les étapes suivantes.

## <a name="more-information"></a>Plus d’informations

Le formulaire de **Outlook.com, le service** grand public, est [présent ici](https://support.microsoft.com/supportrequestform/8ad563e3-288e-2a61-8122-3ba03d6b8d75). N’oubliez pas de lire d’abord [le FAQ](https://sendersupport.olc.protection.outlook.com/pm/troubleshooting.aspx) pour obtenir _l’itinéraire de soumission_ .
