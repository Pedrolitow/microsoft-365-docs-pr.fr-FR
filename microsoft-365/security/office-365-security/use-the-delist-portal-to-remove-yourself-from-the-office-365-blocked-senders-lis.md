---
title: Supprimez-vous de la liste des expéditeurs bloqués et adressez les erreurs 5.7.511 Accès refusé
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
description: Dans cet article, vous allez apprendre à utiliser le portail de suppression pour vous supprimer de la liste des expéditeurs bloqués Microsoft 365. Il s’agit de la meilleure réponse pour résoudre les erreurs d’accès refusé 5.7.511.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 43637f8eb72d078223236f78b45034218e34bcbc
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971129"
---
# <a name="use-the-delist-portal-to-remove-yourself-from-the-blocked-senders-list-and-address-57511-access-denied-errors"></a>Utilisez le portail de liste pour vous supprimer de la liste des expéditeurs bloqués et résoudre les erreurs d’accès refusé 5.7.511

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Recevez-vous un message d’erreur lorsque vous essayez d’envoyer un e-mail à un destinataire dont l’adresse e-mail se trouve dans Microsoft 365 (par exemple, l’adresse 5.7.511 Accès refusé) ? Si vous pensez ne pas recevoir le message d’erreur, vous pouvez utiliser le portail de suppression pour vous supprimer de la liste des expéditeurs bloqués.

## <a name="what-is-the-blocked-senders-list"></a>Qu’est-ce que la liste des expéditeurs bloqués ?

Microsoft utilise la liste des expéditeurs bloqués pour protéger ses clients contre le courrier indésirable, l'usurpation d'identité et les attaques par hameçonnage. L’adresse IP de votre serveur de messagerie, c’est-à-dire l’adresse que votre serveur de messagerie utilise pour s’identifier sur Internet, a été marquée comme une menace potentielle pour Microsoft 365 pour l’une des diverses raisons. Lorsque Microsoft 365 ajoute l’adresse IP à la liste, elle empêche toute communication supplémentaire entre l’adresse IP et l’un de nos clients via nos centres de données.

Vous savez que vous avez été ajouté à la liste si vous recevez une réponse à un courrier électronique incluant une erreur ressemblant à ce qui suit :

> 550 5.7.606-649 Accès refusé, interdiction d’envoyer l’adresse _IP [adresse IP_] (par exemple. 5.7.511 Accès refusé) : pour demander la suppression de cette liste, visitez <https://sender.office.com/> et suivez les instructions. Pour plus d’informations, consultez [les rapports de non-remise par e-mail dans Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

où  _IP address_ est l'adresse IP de l'ordinateur sur lequel s'exécute le serveur de messagerie.

## <a name="verify-senders-before-removing-them-from-the-blocked-senders-list"></a>Vérifier les expéditeurs avant de les supprimer de la liste des expéditeurs bloqués

Il existe de bonnes raisons pour que les expéditeurs se retrouvent dans la liste des expéditeurs bloqués, mais des erreurs peuvent se produire. Regardez cette vidéo pour obtenir une explication équilibrée des expéditeurs bloqués et de la suppression de la liste.
<p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvD]

## <a name="to-use-delist-portal-to-remove-yourself-from-the-blocked-senders-list-after-errors-like-57511-access-denied"></a>Pour utiliser le portail de suppression de liste pour vous supprimer de la liste des expéditeurs bloqués (après des erreurs telles que 5.7.511 Accès refusé)

1. Dans un navigateur web, accédez à <https://sender.office.com>.

2. Suivez les instructions de la page. Assurez-vous que vous utilisez l'adresse de messagerie à laquelle le message d'erreur a été envoyé et l'adresse IP qui est spécifiée dans le message d'erreur. Vous ne pouvez entrer qu'une adresse de messagerie et une adresse IP par visite.

3. Cliquez sur **Envoyer**.

    Le portail envoie un courrier électronique à l'adresse de messagerie que vous indiquez. Le courrier électronique devrait ressembler à ce qui suit :

    :::image type="content" source="../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png" alt-text="L’e-mail reçu lorsque vous envoyez une demande via le portail de suppression de liste" lightbox="../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png":::

4. Cliquez sur le lien de confirmation dans le courrier électronique envoyé par le portail de suppression de la liste.

    Vous revenez au portail Supprimer de la liste.

5. Dans le portail Supprimer de la liste, cliquez sur **Supprimer l'adresse IP de la liste**.

    Une fois l’adresse IP supprimée de la liste des expéditeurs bloqués, les messages électroniques de cette adresse IP sont remis aux destinataires qui utilisent Microsoft 365. Par conséquent, assurez-vous que vous êtes sûr que les e-mails envoyés à partir de cette adresse IP ne seront pas abusifs ou malveillants ; Sinon, l’adresse IP peut être à nouveau bloquée.

    > [!NOTE]
    > Il peut prendre jusqu’à 24 heures ou les résultats peuvent varier considérablement avant que les restrictions soient supprimées.

Consultez [Créer des listes d’expéditeurs sécurisés dans EOP](create-safe-sender-lists-in-office-365.md) et protection [contre le courrier indésirable sortant dans EOP](outbound-spam-controls.md) pour empêcher le blocage d’une adresse IP.

### <a name="how-do-fix-error-code-57511"></a>Comment corriger le code d’erreur 5.7.511

En cas de problème de remise d’un message électronique que vous avez envoyé, Microsoft 365 ou Office 365 vous envoie un e-mail pour vous en informer. L’e-mail que vous recevez est une notification d’état de remise. La notification la plus courante est la notification d’échec de remise qui vous informe qu’un message n’a pas été remis. Dans certaines situations, Microsoft doit effectuer des investigations supplémentaires sur le trafic provenant de votre adresse IP et, si vous recevez le code NDR 5.7.511, vous **ne pourrez pas** utiliser le portail de suppression de liste.

> 550 5.7.511 Accès refusé, expéditeur interdit[xxx.xxx.xxx.xxx]. Pour demander la suppression de cette liste, transférez ce message à delist@messaging.microsoft.com. Pour plus d’informations, accédez à <https://go.microsoft.com/fwlink/?LinkId=526653>.

Dans l’e-mail pour demander la suppression de cette liste, fournissez le code NDR complet et l’adresse IP. Microsoft vous contactera dans les 48 heures suivant les étapes suivantes.

## <a name="more-information"></a>Plus d’informations

Formulaire de suppression pour **Outlook.com, le service consommateur** est disponible [ici](https://support.microsoft.com/supportrequestform/8ad563e3-288e-2a61-8122-3ba03d6b8d75). Veillez à lire d’abord le [FAQ](https://sendersupport.olc.protection.outlook.com/pm/troubleshooting.aspx) pour obtenir _la direction de la soumission_ .
