---
title: Créer des listes d’expéditeurs approuvés
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150s
ms.assetid: 9721b46d-cbea-4121-be51-542395e6fd21
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les options disponibles et préférées pour autoriser les messages entrants dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e5473f8c37b4edcf6c2451cf995b430edbe09533
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065313"
---
# <a name="create-safe-sender-lists-in-eop"></a>Créer des listes d’expéditeurs sûrs dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si vous êtes un client Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou un client Exchange Online Protection autonome (EOP) sans boîtes aux lettres Exchange Online, EOP offre plusieurs façons de s’assurer que les utilisateurs reçoivent des messages électroniques d’expéditeurs fiables. Ces options incluent les règles de flux de messagerie Exchange (également appelées règles de transport), les expéditeurs autorisés Outlook, la liste d’adresses IP autorisées (filtrage des connexions) et les listes d’expéditeurs autorisés ou de domaines autorisés dans les stratégies anti-courrier indésirable. Collectivement, vous pouvez voir ces options comme des _listes d’expéditeurs sûrs._

Les listes d’expéditeurs sûrs disponibles sont décrites dans la liste suivante, de la plus recommandée à la moins recommandée :

1. Règles de flux de messagerie
2. Expéditeurs sécurisés Outlook
3. Liste d’adresses IP permises (filtrage des connexions)
4. Listes d’expéditeurs autorisés ou listes de domaines autorisés (stratégies anti-courrier indésirable)

Les règles de flux de messagerie offrent la plus grande souplesse pour garantir que seuls les messages de droite sont autorisés. Les listes d’expéditeurs autorisés et de domaines autorisés dans les stratégies anti-courrier indésirable ne sont pas aussi sécurisées que la liste d’adresses IP autorisées, car le domaine de messagerie de l’expéditeur est facilement usurpé. Toutefois, la liste d’adresses IP  permises présente également un risque, car les messages électroniques provenant de n’importe quel domaine envoyé à partir de cette adresse IP contournent le filtrage du courrier indésirable.

> [!IMPORTANT]
>
> - Veillez à surveiller attentivement les *exceptions* que vous faites au filtrage du courrier indésirable à l’aide de listes d’expéditeurs sûrs.
>
> - Bien que vous pouvez utiliser des listes d’expéditeurs sûrs pour vous aider avec les faux positifs (message électronique de qualité marqué comme faux), vous devez envisager l’utilisation de listes d’expéditeurs sûrs comme une solution temporaire à éviter si possible. Nous vous déconseillons de gérer les faux positifs à l’aide de listes d’expéditeurs sûrs, car les exceptions au filtrage du courrier indésirable peuvent ouvrir votre organisation à l’usurpation d’identité et à d’autres attaques. Si vous persistez à utiliser des listes d’expéditeurs sûrs pour gérer les faux positifs, vous devez être vigilant et maintenir la rubrique Signaler les messages et les fichiers à [Microsoft.](report-junk-email-messages-to-microsoft.md)
>
> - Pour autoriser un domaine à envoyer des messages électroniques non authentifiés (contournement de la protection contre l’usurpation d’identité) sans contourner les vérifications anti-courrier indésirable et anti-programme malveillant, vous pouvez l’ajouter à la liste des expéditeurs autorisés [AllowedToSpoof](walkthrough-spoof-intelligence-insight.md)
>
> - EOP et Outlook inspectent différentes propriétés de message pour déterminer l’expéditeur du message. Pour plus d’informations, voir la section Considérations pour [les courriers](#considerations-for-bulk-email) électroniques en nombre plus loin dans cet article.

En revanche, vous avez également plusieurs options pour bloquer le courrier provenant de sources spécifiques à l’aide de _listes d’expéditeurs bloqués._ Pour plus d’informations, voir [Créer des listes d’expéditeurs bloqués dans Exchange Online PowerShell](create-block-sender-lists-in-office-365.md).

## <a name="recommended-use-mail-flow-rules"></a>(Recommandé) Utiliser des règles de flux de messagerie

Les règles de flux de messagerie dans Exchange Online et EOP autonome utilisent des conditions et des exceptions pour identifier les messages et des actions pour spécifier ce qui doit être fait pour ces messages. Pour plus d’informations, consultez la rubrique [Mail flow rules (transport rules) in Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

L’exemple suivant suppose que vous avez besoin d’e-contoso.com pour ignorer le filtrage du courrier indésirable. Pour ce faire, configurez les paramètres suivants :

1. **Condition**: **le domaine de** \> **l’expéditeur est** \> contoso.com.

2. Configurez l’un des paramètres suivants :

   - **Condition de règle de flux** de messagerie : un en-tête de **message** inclut l’un de ces mots Nom d’en-tête : \>  \>  `Authentication-Results` \> **valeur d’en-tête**: `dmarc=pass` ou `dmarc=bestguesspass` .

     Cette condition vérifie l’état d’authentification de messagerie du domaine de courrier d’envoi pour s’assurer que le domaine d’envoi n’est pas usurpé. Pour plus d’informations sur l’authentification de messagerie, voir [SPF,](set-up-spf-in-office-365-to-help-prevent-spoofing.md) [DKIM](use-dkim-to-validate-outbound-email.md)et [DMARC.](use-dmarc-to-validate-email.md)

   - **Liste d’adresses IP permises**: spécifiez l’adresse IP source ou la plage d’adresses dans la stratégie de filtrage des connexions.

     Utilisez ce paramètre si le domaine d’envoi n’utilise pas l’authentification de messagerie. Soyez aussi restrictif que possible en ce qui concerne les adresses IP sources dans la liste d’adresses IP permises. Nous vous recommandons d’avoir une plage d’adresses IP inférieure ou inférieure à /24 (moins est préférable). N’utilisez pas de plages d’adresses IP appartenant aux services grand public (par exemple, outlook.com) ou aux infrastructures partagées.

   > [!IMPORTANT]
   >
   > - Ne configurez jamais de règles de flux de *messagerie* avec uniquement le domaine de l’expéditeur comme condition pour ignorer le filtrage du courrier indésirable. Cela augmente  considérablement la probabilité que les personnes malveillantes usurpent le domaine d’envoi (ou usurpent l’identité de l’adresse de messagerie complète), ignorent le filtrage du courrier indésirable et ignorent les vérifications d’authentification des expéditeurs afin que le message arrive dans la boîte de réception du destinataire.
   >
   > - N’utilisez pas les domaines que vous possédez (également appelés domaines acceptés) ou les domaines populaires (par exemple, microsoft.com) comme conditions dans les règles de flux de messagerie. Cette situation est considérée comme un risque élevé, car elle crée des opportunités pour les attaquants d’envoyer des messages électroniques qui seraient autrement filtrés.
   >
   > - Si vous autorisez une adresse IP qui se cache derrière une passerelle NAT (Network Address Translation), vous devez connaître les serveurs impliqués dans le pool NAT afin de connaître l’étendue de votre liste d’adresses IP permises. Les adresses IP et les participants NAT peuvent changer. Vous devez vérifier régulièrement vos entrées de listes d’adresses IP permises dans le cadre de vos procédures de maintenance standard.

3. **Conditions facultatives**:

   - **L’expéditeur** \> **est interne/externe** \> **En dehors de** l’organisation : cette condition est implicite, mais vous pouvez l’utiliser pour prendre en compte les serveurs de messagerie locaux qui ne sont peut-être pas correctement configurés.

   - **L’objet ou le corps** \> **l’objet ou le corps inclut l’un de ces mots** \> : si vous pouvez limiter davantage les messages par mots clés ou expressions dans la ligne d’objet ou le corps du message, vous pouvez utiliser ces \<keywords\> mots comme condition.

4. **Action**: configurez ces deux actions dans la règle :

   a. **Modifier les propriétés du message** \> **définir le niveau de confiance du courrier indésirable (SCL)** \> **Contourner le filtrage du courrier indésirable.**

   b. **Modifier les propriétés du message** \> **définir un en-tête de message**: **définissez l’en-tête de message** sur la \<CustomHeaderName\> **valeur** \<CustomHeaderValue\> .

      Par exemple, `X-ETR: Bypass spam filtering for authenticated sender 'contoso.com'`. Si vous avez plusieurs domaines dans la règle, vous pouvez personnaliser le texte d’en-tête selon le cas.

      Lorsqu’un message ignore le filtrage du courrier indésirable en raison d’une règle de flux de messagerie, la valeur est estampillée dans `SFV:SKN` l’en-tête **X-Forefront-Antispam-Report.** Si le message est issu d’une source qui se trouve sur la liste d’adresses IP permises, la valeur `IPV:CAL` est également ajoutée. Ces valeurs peuvent vous aider à résoudre les problèmes.

![Paramètres de règle de flux de messagerie dans le EAC pour contourner le filtrage du courrier indésirable.](../../media/1-AllowList-SkipFilteringFromContoso.png)

## <a name="use-outlook-safe-senders"></a>Utiliser les expéditeurs sécurisés Outlook

> [!CAUTION]
> Cette méthode crée un risque élevé de remettre correctement des messages électroniques à la boîte de réception qui seraient autrement filtrés . toutefois, les listes Des expéditeurs ou des domaines sûrs de l’utilisateur n’empêchent pas le filtrage des programmes malveillants ou des messages de hameçonnage à haut niveau de confiance.

Au lieu d’un paramètre organisationnel, les utilisateurs ou les administrateurs peuvent ajouter les adresses de messagerie des expéditeurs à la liste des expéditeurs sûrs dans la boîte aux lettres. Pour obtenir des instructions, voir Configurer les paramètres du courrier indésirable sur les boîtes aux lettres [Exchange Online dans Office 365.](configure-junk-email-settings-on-exo-mailboxes.md) Cela n’est pas souhaitable dans la plupart des cas, car les expéditeurs contournent certaines parties de la pile de filtrage. Même si vous faites confiance à l’expéditeur, l’expéditeur peut toujours être compromis et envoyer du contenu malveillant. Il est préférable de laisser nos filtres faire ce qui est nécessaire pour vérifier chaque message, puis signaler le [faux positif/négatif](report-junk-email-messages-to-microsoft.md) à Microsoft si nos filtres se sont mal produits. Le contournement de la pile de filtrage interfère également avec [ZAP](zero-hour-auto-purge.md).

Lorsque les messages ignorent le filtrage du courrier indésirable en raison de la liste des expéditeurs sûrs d’un utilisateur, le champ **d’en-tête X-Forefront-Antispam-Report** contient la valeur, ce qui indique que le filtrage du courrier indésirable, de l’usurpation et du hameçonnage a été `SFV:SFE` contourné.

## <a name="use-the-ip-allow-list"></a>Utiliser la liste d’adresses IP permises

Si vous ne pouvez pas utiliser les règles de flux de messagerie comme décrit précédemment, la meilleure option suivante consiste à ajouter le ou les serveurs de messagerie source à la liste d’adresses IP permises dans la stratégie de filtrage des connexions. Pour plus d’informations, [voir Configurer le filtrage des connexions dans EOP.](configure-the-connection-filter-policy.md)

**Remarques** :

- Il est important que vous maintenez le nombre d’adresses IP autorisées au minimum, donc évitez d’utiliser des plages d’adresses IP entières chaque fois que possible.

- N’utilisez pas de plages d’adresses IP appartenant aux services grand public (par exemple, outlook.com) ou aux infrastructures partagées.

- Examinez régulièrement les entrées de la liste d’adresses IP permises et supprimez les entrées dont vous n’avez plus besoin.

> [!CAUTION]
> Sans vérification supplémentaire comme les règles de flux de messagerie, le courrier électronique provenant de sources dans la liste d’adresses IP permises ignore le filtrage du courrier indésirable et les vérifications d’authentification des expéditeurs (SPF, DKIM, DMARC). Cela crée un risque élevé de remettre correctement des messages électroniques à la boîte de réception qui seraient autrement filtrés ; Toutefois, la liste d’adresses IP permises n’empêche pas le filtrage des programmes malveillants ou des messages de hameçonnage à haut niveau de confiance.

## <a name="use-allowed-sender-lists-or-allowed-domain-lists"></a>Utiliser des listes d’expéditeurs autorisés ou des listes de domaines autorisés

L’option la moins souhaitable consiste à utiliser la liste des expéditeurs autorisés ou la liste des domaines autorisés dans les stratégies anti-courrier indésirable. Vous devez éviter cette option si *possible,* car les expéditeurs contournent la protection contre le courrier indésirable, l’usurpation d’identité et l’authentification des expéditeurs (SPF, DKIM, DMARC). Cette méthode est idéale pour les tests temporaires uniquement. Les étapes détaillées se trouvent dans la rubrique Configurer les stratégies [anti-courrier indésirable dans la rubrique EOP.](configure-your-spam-filter-policies.md)

La limite maximale pour ces listes est d’environ 1 000 entrées ; cependant, vous ne pourrez entrer que 30 entrées dans le portail. Vous devez utiliser PowerShell pour ajouter plus de 30 entrées.

> [!CAUTION]
>
> - Cette méthode crée un risque élevé de remettre correctement des messages électroniques à la boîte de réception qui seraient autrement filtrés . toutefois, les listes des expéditeurs autorisés ou des domaines autorisés n’empêchent pas le filtrage des programmes malveillants ou des messages de hameçonnage à haut niveau de confiance.
>
> - N’utilisez pas les domaines que vous possédez (également appelés domaines acceptés) ou les domaines populaires (par exemple, microsoft.com) dans les listes de domaines autorisés.

## <a name="considerations-for-bulk-email"></a>Considérations sur les messages électroniques en masse

Un message électronique SMTP standard est constitué d’une *enveloppe de message* et d’un contenu de message. L’enveloppe de message contient les informations requises pour transmettre et remettre le message entre des serveurs SMTP. Le contenu du message comporte les champs d’en-tête de message (collectivement appelés l’*en-tête de message*) et le corps du message. L’enveloppe du message est décrite dans la RFC 5321 et l’en-tête du message est décrit dans la RFC 5322. Les destinataires ne voient jamais l’enveloppe de message réelle, car elle est générée par le processus de transmission du message et ne fait pas réellement partie du message.

- L’adresse (également appelée adresse MAIL FROM, expéditeur P1 ou expéditeur d’enveloppe) est l’adresse de messagerie utilisée dans la `5321.MailFrom` transmission SMTP du message.  Cette adresse de messagerie est généralement enregistrée dans le champ **d’en-tête Return-Path** dans l’en-tête du message (bien qu’il soit possible pour l’expéditeur de désigner une autre adresse de messagerie **Return-Path).** Si le message ne peut pas être remis, il s’agit du destinataire de la non-remise (également appelée NDR ou message de non-remise).

- L’adresse e-mail (également appelée adresse de provenance ou expéditeur P2) est l’adresse de messagerie dans le champ d’en-tête De et l’adresse e-mail de l’expéditeur qui s’affiche dans les clients de `5322.From` messagerie.  

Souvent, les adresses et les `5321.MailFrom` `5322.From` adresses sont identiques (communication de personne à personne). Toutefois, lorsque le courrier électronique est envoyé pour le compte d’une autre personne, les adresses peuvent être différentes. Cela se produit le plus souvent pour les messages électroniques en masse.

Par exemple, supposons que Blue Yonder Airlines a embauché Margie’s Travel pour envoyer ses messages électroniques publicitaires. Le message que vous recevez dans votre boîte de réception possède les propriétés suivantes :

- `5321.MailFrom`L’adresse est blueyonder.airlines@margiestravel.com.

- L’adresse est blueyonder@news.blueyonderairlines.com, ce qui est `5322.From` ce que vous verrez dans Outlook.

Les listes d’expéditeurs sûrs et les listes de domaines sûrs dans les stratégies anti-courrier indésirable dans EOP inspectent uniquement les adresses, ce qui est similaire aux expéditeurs sûrs Outlook qui `5322.From` utilisent `5322.From` l’adresse.

Pour empêcher le filtrage de ce message, vous pouvez suivre les étapes suivantes :

- Ajoutez blueyonder@news.blueyonderairlines.com `5322.From` (l’adresse) en tant qu’expéditeur sécurisé Outlook.

- [Utilisez une règle de flux de](#recommended-use-mail-flow-rules) messagerie avec une condition qui recherche des messages à partir de blueyonder@news.blueyonderairlines.com (l’adresse, blueyonder.airlines@margiestravel.com `5322.From` (le ), ou les `5321.MailFrom` deux.

Pour plus d’informations, voir [Créer des listes d’expéditeurs sûrs dans EOP.](create-safe-sender-lists-in-office-365.md)