---
title: Créer des listes d’expéditeurs approuvés dans Office 365
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 4/29/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150s
ms.assetid: 9721b46d-cbea-4121-be51-542395e6fd21
description: Si vous souhaitez être sûr de recevoir des messages d’un expéditeur particulier, étant donné que vous les approuvez et leurs messages, vous pouvez ajuster votre liste verte dans une stratégie de filtrage du courrier indésirable.
ms.openlocfilehash: 4ac97192327cd9ced853ce63537375931f3f0ec3
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41599531"
---
# <a name="create-safe-sender-lists-in-office-365"></a>Créer des listes d’expéditeurs approuvés dans Office 365

Si vous souhaitez vous assurer que les utilisateurs reçoivent des courriers électroniques provenant d’expéditeurs ou d’expéditeurs spécifiques, car vous les approuvez et leurs messages, vous pouvez choisir parmi plusieurs méthodes. Ces options incluent les règles de flux de messagerie Exchange (également appelées règles de transport), les expéditeurs approuvés Outlook, les listes d’adresses IP autorisées, les listes des expéditeurs de courrier indésirable/de domaine.

> [!IMPORTANT]
> Bien que les listes d’adresses autorisées de l’organisation puissent être utilisées pour résoudre les faux positifs, elle doit être considérée comme une solution temporaire et éviter, dans la mesure du possible. La gestion des faux positifs à l’aide de listes d’autorisation n’est pas recommandée car elle peut accidentellement ouvrir votre organisation à des usurpateurs d’identité, des emprunts d’identité et d’autres attaques. Si vous souhaitez utiliser une liste verte à cette fin, vous devez être vigilant et conserver l’article pour l’envoi de messages indésirables, [non indésirables et de hameçonnage à Microsoft pour analyse](https://docs.microsoft.com/office365/SecurityCompliance/submit-spam-non-spam-and-phishing-scam-messages-to-microsoft-for-analysis), à l’adresse.

La méthode recommandée pour configurer une liste d’expéditeurs approuvés est d’utiliser des règles de flux de messagerie, car cela offre la plus grande flexibilité pour garantir que seuls les messages corrects sont autorisés. Les listes d’adresses de *messagerie des stratégies de blocage du courrier indésirable* et de *domaine* ne sont pas aussi sécurisées que les *listes basées sur les adresses IP* , car les domaines peuvent facilement être falsifiés. Cependant, les listes d’adresses IP autorisées de stratégie de blocage du courrier indésirable présentent également des risques car ils autorisent les domaines envoyés via cette adresse IP à contourner le filtrage du courrier indésirable. Faites attention et surveillez *toutes les* exceptions effectuées, avec précaution.

> [!IMPORTANT]
> Vous [trouverez ici](create-block-sender-lists-in-office-365.md)des informations sur la création d’une **liste d’expéditeurs bloqués** .

## <a name="options-from-most-to-least-recommended"></a>Options du plus ou moins recommandé

Vous devez toujours limiter vos listes d’autorisation, car elles contournent de nombreuses mesures de sécurité. Vous devez revérifier toutes les listes d’autorisation dans le cadre de votre maintenance standard, afin de connaître les personnes autorisées à contourner. Il est recommandé d’utiliser des règles de flux de messagerie restrictives lorsque cela est possible.

- Règles de flux de messagerie Exchange
- Expéditeurs approuvés Outlook
- Stratégie anti-courrier indésirable : listes d’adresses IP autorisées
- Stratégie anti-courrier indésirable : listes vertes de l’expéditeur/du domaine

## <a name="using-exchange-mail-flow-rules-to-allow-specific-senders-recommended"></a>Utilisation de règles de flux de messagerie Exchange pour autoriser des expéditeurs spécifiques (recommandé)

Pour vous assurer que seuls les messages légitimes sont autorisés dans votre organisation, la condition doit être l’une des suivantes :

- Utilisez l’état d’authentification de l’expéditeur du domaine d’envoi. Pour ce faire, vérifiez l’en-tête Authentication-Results afin de vous assurer qu’il contient « dMarc = passe » ou « dMarc = bestguesspass ». Cela garantit que le domaine d’envoi a été authentifié et qu’il n’est pas usurpé. Cliquez pour plus d’informations sur [SPF](https://docs.microsoft.com/office365/SecurityCompliance/set-up-spf-in-office-365-to-help-prevent-spoofing), [DKIM](https://docs.microsoft.com/office365/SecurityCompliance/use-dkim-to-validate-outbound-email)et l’authentification de messagerie [DMARC](https://docs.microsoft.com/office365/SecurityCompliance/use-dmarc-to-validate-email) .

- Si le domaine d’envoi n’a pas d’authentification, utilisez le domaine d’envoi *plus* une adresse IP d’envoi (ou une plage d’adresses IP). Assurez-vous que vous êtes *aussi restrictif que possible*, l’objectif étant que vous effectuez cette opération aussi efficacement que possible. Une plage d’adresses IP supérieure à/24 n’est *pas* recommandée. Évitez d’ajouter des plages d’adresses IP qui appartiennent à des services grand public ou à des infrastructures partagées.

> [!IMPORTANT]
> Si vous autorisez une adresse IP NATted, vous devez déterminer les ordinateurs impliqués dans ce pool NAT afin de déterminer l’étendue de votre autorisation. N’oubliez pas que les adresses IP peuvent varier, et les participants NAT peuvent également l’être. Vous devez revérifier toutes les listes d’autorisation, y compris le protocole IP autorisé dans le cadre de votre maintenance standard.

- Ajoutez *éventuellement*une condition dont le message provient de l’extérieur de l’organisation (Ceci est implicite, mais il convient de l’ajouter en tant que condition pour prendre en compte les serveurs locaux qui ne sont peut-être pas correctement configurés).

- Si vous le *souhaitez, si*vous pouvez identifier des mots clés ou des expressions uniques dans l’objet ou le corps du message, utilisez ces informations comme condition supplémentaire pour limiter davantage les messages électroniques autorisés par la règle de flux de messagerie.

L’action sur la règle doit respecter ce modèle :

1. Définissez le seuil de probabilité de courrier indésirable sur-1 (ignorer le filtrage du courrier indésirable).

2. Ajoutez un en-tête X pour indiquer l’action de la règle. Dans l’exemple ci-dessous, vous pouvez ajouter un `X-ETR: Bypass spam filtering for authenticated sender 'contoso.com'`en-tête simple. Si cette règle comporte plusieurs domaines, vous pouvez modifier le texte d’en-tête en fonction de vos besoins. **Lorsqu’un message ignore le filtrage en raison d’une règle de flux de messagerie, il HORODATE SFV : SKN dans l’en-tête X-Forefront-antispam-Report** (**s’il se trouve sur une liste d’adresses IP autorisées, il marque également IPV : CAL**). Cela vous aidera à résoudre les problèmes.

![Interface utilisateur graphique permettant de contourner le filtrage du courrier indésirable.](../media/1-AllowList-SkipFilteringFromContoso.png)

> [!CAUTION]
> Ne configurez pas les règles de flux de messagerie avec *le domaine de l’expéditeur* comme condition d’ignorer le filtrage du courrier indésirable. Cette méthode augmente considérablement le risque que les spammeurs usurpent le domaine d’envoi (ou empruntent l’identité de l’adresse de messagerie complète) ignorez le filtrage du courrier indésirable, les vérifications d’authentification de l’expéditeur et le message arrivera dans la boîte de réception d’une personne.

![Comment définir la valeur SCL sur moins un.](../media/2-AllowList-SetsSCLMinus1.png)

N’ajoutez pas de domaines que vous possédez ou des domaines populaires ( `microsoft.com`par exemple,) à la règle de flux de messagerie en tant que condition. Ceci est considéré comme un risque élevé, car il permet aux acteurs incorrects de vous envoyer des messages qui seraient autrement filtrés.

Pour plus d’informations, consultez [la rubrique utiliser des règles de flux de messagerie pour définir la valeur SCL dans messages](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md).

## <a name="use-outlook-safe-senders-end-user-managed"></a>Utiliser des expéditeurs approuvés Outlook (géré par l’utilisateur final)

Au lieu d’autoriser une adresse, un domaine ou une adresse IP de manière globale, les utilisateurs finaux peuvent également autoriser l’envoi d’adresses via des expéditeurs approuvés Outlook. Les étapes à suivre pour configurer cette configuration diffèrent entre [Outlook sur le Web](https://support.office.com/article/48c9f6f7-2309-4f95-9a4d-de987e880e46) et le [client Outlook](https://support.office.com/article/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089). **Lorsque les messages sont autorisés en raison des expéditeurs approuvés, vous verrez SFV : SFE dans le X-Forefront-antispam-Report,** ce qui indique que le filtrage du courrier indésirable/de l’usurpation/hameçonnage est contourné.

## <a name="use-anti-spam-policy-ip-allow-lists"></a>Utiliser la stratégie de blocage du courrier indésirable listes d’adresses IP autorisées

Lorsqu’il n’est pas possible d’utiliser des règles de flux de messagerie pour autoriser globalement un expéditeur spécifique lors de la validation de l’authentification de l’expéditeur, ou en liant un domaine et l’adresse IP ensemble, la meilleure option consiste à ajouter l’expéditeur à la *liste d’adresses IP autorisées de la stratégie anti-courrier indésirable*. Vous trouverez les étapes détaillées dans la [configuration de la stratégie de filtrage des connexions](configure-the-connection-filter-policy.md). Il est important de conserver un minimum d’adresses IP autorisées afin d’éviter d’utiliser des plages d’adresses IP entières. En outre, vous ne devez pas ajouter de plages d’adresses IP qui appartiennent à des services grand public ou à des infrastructures partagées, *et vous devez également vérifier* régulièrement la liste des adresses IP autorisées et supprimer celles qui ne sont plus nécessaires.

> [!CAUTION]
> La configuration des stratégies de blocage du courrier indésirable en fonction de l’adresse IP de l’expéditeur uniquement entraîne le blocage du filtrage du courrier indésirable pour tous les messages provenant de cette adresse IP dans la règle d’autorisation. Cela crée un risque élevé que des acteurs défectueux vous envoient des messages qui seraient autrement filtrés. Cette méthode ignore également le filtrage du courrier indésirable, les vérifications d’authentification de l’expéditeur et le message dans la boîte de réception d’un utilisateur, ce qui augmente les risques.

## <a name="use-anti-spam-policy-senderdomain-allow-lists"></a>Utilisation de la stratégie de blocage du courrier indésirable listes des expéditeurs/domaines autorisés

L’option la moins intéressante consiste à autoriser l’expéditeur/domaine. Cette option doit être évitée si cela est *possible* car elle contourne totalement le courrier indésirable/frauduleux/frauduleux et n’évalue pas l’authentification de l’expéditeur. Cette méthode augmente le risque de recevoir des messages à partir d’acteurs incorrects et est recommandé temporairement et uniquement lors des tests. Les étapes détaillées sont disponibles dans la documentation [configurer vos stratégies de filtrage du courrier indésirable](https://docs.microsoft.com/office365/securitycompliance/configure-your-spam-filter-policies) .

La limite maximale de ces listes est d’environ 1000 entrées ; Bien que vous ne puissiez entrer que 30 entrées dans le portail. Vous devez utiliser PowerShell pour ajouter plus de 30 entrées.

> [!IMPORTANT]
> • La configuration des stratégies de blocage du courrier indésirable pour autoriser le domaine de l' *expéditeur/autoriser* a pour effet que les messages ignorent le filtrage du courrier indésirable pour un des messages provenant d’expéditeurs figurant dans la liste verte, ou b) tous les expéditeurs d’un domaine autorisé. Cette méthode augmente considérablement le risque que les spammeurs usurpent le domaine d’envoi (ou empruntent l’identité de l’adresse de messagerie complète), ce qui ignore le filtrage du courrier indésirable, les vérifications d’authentification de l’expéditeur et envoie le message directement dans la boîte de réception d’une personne. <br/><br/>• N’ajoutez pas de domaines propriétaires ou courants (par exemple `microsoft.com`,) à la règle de flux de messagerie en tant que condition. Cette méthode est considérée comme un risque élevé, car elle permet aux acteurs incorrects de vous envoyer des messages qui seraient autrement filtrés, ce qui augmente le risque. <br/><br/>• Informations sur la création d’une **liste d’expéditeurs bloqués** [.](create-block-sender-lists-in-office-365.md)
