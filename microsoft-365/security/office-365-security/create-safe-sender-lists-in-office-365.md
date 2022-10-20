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
ms.collection: m365-security
ms.localizationpriority: medium
search.appverid:
- MET150s
ms.assetid: 9721b46d-cbea-4121-be51-542395e6fd21
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les options disponibles et préférées pour autoriser les messages entrants dans Exchange Online Protection (EOP).
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 65520a890be1e7c8e529496b7fb78005139bde9d
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68645184"
---
# <a name="create-safe-sender-lists-in-eop"></a>Créer des listes d’expéditeurs fiables dans EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si vous êtes un client Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou un client Exchange Online Protection autonome (EOP) sans boîtes aux lettres Exchange Online, EOP offre plusieurs façons de s’assurer que les utilisateurs recevront des e-mails d’expéditeurs approuvés. Collectivement, vous pouvez considérer ces options comme des _listes d’expéditeurs fiables_.

Les listes d’expéditeurs fiables disponibles sont décrites dans la liste suivante, de la plus recommandée au moins recommandée :

1. Autorisez les entrées pour les domaines et les adresses e-mail (y compris les expéditeurs usurpés) dans la liste d’autorisations/de blocs du locataire.
2. Règles de flux de messagerie (également appelées règles de transport).
3. Outlook Safe Senders (liste des expéditeurs approuvés qui est stockée dans chaque boîte aux lettres).
4. Liste d’autorisations IP (filtrage de connexion)
5. Listes d’expéditeurs autorisées ou listes de domaines autorisés (stratégies anti-courrier indésirable)

Le reste de cet article contient des détails sur chaque méthode.

> [!IMPORTANT]
> Les messages identifiés comme des programmes malveillants ou un hameçonnage à haut niveau de confiance sont toujours mis en quarantaine, quelle que soit l’option de liste d’expéditeurs fiables que vous utilisez. Pour plus d’informations, consultez [Sécuriser par défaut dans Office 365](secure-by-default.md).
>
> Veillez à surveiller attentivement _les_ exceptions que vous apportez au filtrage du courrier indésirable à l’aide de listes d’expéditeurs fiables.
>
> Envoyez toujours des messages dans vos listes d’expéditeurs sécurisés à Microsoft à des fins d’analyse. Pour obtenir des instructions, consultez [Signaler un bon e-mail à Microsoft](admin-submission.md#report-good-email-to-microsoft). Si les messages ou les sources de messages sont déterminés comme étant bénins, Microsoft peut autoriser automatiquement les messages, et vous n’aurez pas besoin de gérer manuellement l’entrée dans les listes d’expéditeurs fiables.
>
> Au lieu d’autoriser le courrier électronique, vous disposez également de plusieurs options pour bloquer les e-mails provenant de sources spécifiques à l’aide de _listes d’expéditeurs bloquées_. Pour plus d’informations, voir [Créer des listes d’expéditeurs bloqués dans Exchange Online PowerShell](create-block-sender-lists-in-office-365.md).

## <a name="use-allow-entries-in-the-tenant-allowblock-list"></a>Utiliser des entrées d’autorisation dans la liste d’autorisations/de blocs du locataire

L’option numéro un recommandée pour autoriser le courrier provenant d’expéditeurs ou de domaines est la liste d’autorisation/de blocage du locataire. Pour obtenir des instructions, consultez [Autoriser ou bloquer les e-mails à l’aide de la liste d’autorisation/de blocage du locataire](allow-block-email-spoof.md).

Ce n’est que si vous ne pouvez pas utiliser la liste d’autorisation/de blocage du locataire pour une raison quelconque que vous envisagez d’utiliser une autre méthode pour autoriser les expéditeurs.

## <a name="use-mail-flow-rules"></a>Utiliser des règles de flux de messagerie

> [!NOTE]
> Vous ne pouvez pas utiliser les en-têtes de message et les règles de flux de courrier pour désigner un expéditeur interne comme expéditeur sûr. Les procédures de cette section fonctionnent uniquement pour les expéditeurs externes.

Les règles de flux de messagerie dans Exchange Online et les exceptions EOP autonomes utilisent des conditions et des exceptions pour identifier les messages, ainsi que des actions pour spécifier ce qui doit être fait pour ces messages. Pour plus d’informations, consultez la rubrique [Mail flow rules (transport rules) in Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

L’exemple suivant suppose que vous avez besoin d’e-mail de contoso.com pour ignorer le filtrage du courrier indésirable. Pour ce faire, configurez les paramètres suivants :

1. **Condition** : **le domaine de l’expéditeur** \> **est** \> contoso.com.

2. Configurez l’un des paramètres suivants :

   - **Condition de règle de flux** de **messagerie : un en-tête** \> **de message inclut l’un des mots suivants** \> Nom de l’en-tête : `Authentication-Results` \> **Valeur d’en-tête** : `dmarc=pass` ou `dmarc=bestguesspass`.

     Cette condition vérifie l’état d’authentification par e-mail du domaine de messagerie d’envoi pour s’assurer que le domaine d’envoi n’est pas usurpé. Pour plus d’informations sur l’authentification par e-mail, consultez [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) et [DMARC](use-dmarc-to-validate-email.md).

   - **Liste d’adresses IP autorisées** : spécifiez l’adresse IP source ou la plage d’adresses dans la stratégie de filtre de connexion. Pour obtenir des instructions, consultez [Configurer le filtrage de connexion](configure-the-connection-filter-policy.md).

     Utilisez ce paramètre si le domaine d’envoi n’utilise pas l’authentification par e-mail. Soyez aussi restrictif que possible quand il s’agit des adresses IP sources dans la liste d’autorisations IP. Nous vous recommandons une plage d’adresses IP de /24 ou moins (moins c’est mieux). N’utilisez pas de plages d’adresses IP qui appartiennent à des services grand public (par exemple, outlook.com) ou à des infrastructures partagées.

   > [!IMPORTANT]
   >
   > - Ne configurez jamais les règles de flux de courrier avec _uniquement_ le domaine de l’expéditeur comme condition pour ignorer le filtrage du courrier indésirable. Cela augmente _considérablement_ la probabilité que les attaquants puissent usurper le domaine d’envoi (ou emprunter l’identité de l’adresse e-mail complète), ignorer tout filtrage du courrier indésirable et ignorer les vérifications d’authentification de l’expéditeur pour que le message arrive dans la boîte de réception du destinataire.
   >
   > - N’utilisez pas les domaines que vous possédez (également appelés domaines acceptés) ou les domaines populaires (par exemple, microsoft.com) comme conditions dans les règles de flux de messagerie. Cela est considéré comme un risque élevé, car il crée des opportunités pour les attaquants d’envoyer des e-mails qui seraient autrement filtrés.
   >
   > - Si vous autorisez une adresse IP qui se trouve derrière une passerelle NAT (Network Address Translation), vous devez connaître les serveurs impliqués dans le pool NAT afin de connaître l’étendue de votre liste d’autorisations IP. Les adresses IP et les participants NAT peuvent changer. Vous devez vérifier régulièrement vos entrées de liste d’autorisations IP dans le cadre de vos procédures de maintenance standard.

3. **Conditions facultatives** :

   - **L’expéditeur** \> **est interne/externe** \> **En dehors de l’organisation** : cette condition est implicite, mais il est possible de l’utiliser pour tenir compte des serveurs de messagerie locaux qui risquent de ne pas être correctement configurés.
   - **Objet ou corps** \> **objet ou corps inclut l’un de ces mots** \> \<keywords\>: Si vous pouvez restreindre davantage les messages par mots clés ou expressions dans la ligne d’objet ou le corps du message, vous pouvez utiliser ces mots comme condition.

4. **Action** : Configurez ces deux actions dans la règle :

   1. **Modifier les propriétés** \> du message **définir le niveau de confiance du courrier indésirable (SCL)** \> **Ignorer le filtrage du courrier indésirable**.
   2. **Modifier les propriétés** \> du message **définir un en-tête de message** : **définissez l’en-tête** \<CustomHeaderName\> **de message sur la valeur** \<CustomHeaderValue\>.

      Par exemple : `X-ETR: Bypass spam filtering for authenticated sender 'contoso.com'`. Si vous avez plusieurs domaines dans la règle, vous pouvez personnaliser le texte de l’en-tête selon les besoins.

      Lorsqu’un message ignore le filtrage du courrier indésirable en raison d’une règle de flux de courrier, la `SFV:SKN` valeur est horodaté dans l’en-tête **X-Forefront-Antispam-Report** . Si le message provient d’une source figurant dans la liste d’autorisations IP, la valeur `IPV:CAL` est également ajoutée. Ces valeurs peuvent vous aider à résoudre les problèmes.

      :::image type="content" source="../../media/1-AllowList-SkipFilteringFromContoso.png" alt-text="Paramètres de règle de flux de courrier dans le CAE pour contourner le filtrage du courrier indésirable" lightbox="../../media/1-AllowList-SkipFilteringFromContoso.png":::

## <a name="use-outlook-safe-senders"></a>Utiliser des expéditeurs sécurisés Outlook

> [!CAUTION]
> Cette méthode crée un risque élevé que des attaquants envoient correctement des e-mails à la boîte de réception qui autrement seraient filtrés ; toutefois, si un message provenant d’une entrée dans les listes Expéditeurs approuvés ou Domaines sûrs de l’utilisateur est déterminé comme étant un programme malveillant ou un hameçonnage à haut niveau de confiance, le message est filtré.

Au lieu d’un paramètre organisationnel, les utilisateurs ou les administrateurs peuvent ajouter les adresses e-mail de l’expéditeur à la liste des expéditeurs approuvés dans la boîte aux lettres. Pour obtenir des instructions, consultez [Configurer les paramètres de courrier indésirable sur Exchange Online boîtes aux lettres dans Office 365](configure-junk-email-settings-on-exo-mailboxes.md).

Cette méthode n’est pas souhaitable dans la plupart des cas, car les expéditeurs contournent certaines parties de la pile de filtrage. Même si vous faites confiance à l’expéditeur, l’expéditeur peut toujours être compromis et envoyer du contenu malveillant. Vous devez laisser nos filtres vérifier chaque message, puis [signaler les faux positifs/négatifs à Microsoft](report-junk-email-messages-to-microsoft.md) si nous nous sommes trompés. Le contournement de la pile de filtrage interfère également avec le [vidage automatique de zéro heure (ZAP).](zero-hour-auto-purge.md)

Par conception et pour renforcer la sécurité des boîtes aux lettres Exchange Online, seuls les paramètres de courrier indésirable pour les expéditeurs sécurisés, les expéditeurs bloqués et les domaines bloqués sont reconnus. Les paramètres de liste de diffusion sécurisés sont ignorés.

**Remarque** : Dans Exchange Online, les entrées de domaine dans la liste Des expéditeurs approuvés Outlook ou le paramètre TrustedSendersAndDomains ne sont pas reconnues. Utilisez donc uniquement des adresses e-mail.

Lorsque les messages ignorent le filtrage du courrier indésirable en raison de la liste des expéditeurs approuvés d’un utilisateur, le champ **d’en-tête X-Forefront-Antispam-Report** contient la valeur `SFV:SFE`, ce qui indique que le filtrage du courrier indésirable, de l’usurpation d’identité et du hameçonnage a été contourné.

## <a name="use-the-ip-allow-list"></a>Utiliser la liste d’autorisations IP

> [!CAUTION]
> Sans vérification supplémentaire comme les règles de flux de courrier, les e-mails provenant de sources dans la liste d’autorisation IP ignorent le filtrage du courrier indésirable et les vérifications de l’authentification de l’expéditeur (SPF, DKIM, DMARC). Ce résultat crée un risque élevé que les attaquants envoient correctement des e-mails à la boîte de réception qui autrement seraient filtrés ; toutefois, si un message d’une entrée dans la liste d’autorisations IP est déterminé comme étant un programme malveillant ou un hameçonnage à haut niveau de confiance, le message est filtré.

La meilleure option consiste à ajouter le ou les serveurs de messagerie source à la liste d’autorisations IP dans la stratégie de filtre de connexion. Pour plus d’informations, consultez [Configurer le filtrage de connexion dans EOP](configure-the-connection-filter-policy.md).

**Remarques** :

- Il est important de conserver au minimum le nombre d’adresses IP autorisées. Évitez donc d’utiliser des plages d’adresses IP entières dans la mesure du possible.
- N’utilisez pas de plages d’adresses IP qui appartiennent à des services grand public (par exemple, outlook.com) ou à des infrastructures partagées.
- Examinez régulièrement les entrées de la liste d’autorisations IP et supprimez les entrées dont vous n’avez plus besoin.

## <a name="use-allowed-sender-lists-or-allowed-domain-lists"></a>Utiliser des listes d’expéditeurs autorisées ou des listes de domaines autorisées

> [!CAUTION]
>
> Cette méthode crée un risque élevé que des attaquants envoient correctement des e-mails à la boîte de réception qui autrement seraient filtrés ; toutefois, si un message provenant d’une entrée dans les expéditeurs autorisés ou les listes de domaines autorisés est déterminé comme étant un programme malveillant ou un hameçonnage à haut niveau de confiance, le message est filtré.
>
> N’utilisez pas les domaines que vous possédez (également appelés domaines acceptés) ou les domaines populaires (par exemple, microsoft.com) dans les listes de domaines autorisées.

L’option la moins souhaitable consiste à utiliser la liste d’expéditeurs autorisée ou la liste de domaines autorisés dans les stratégies anti-courrier indésirable. Vous devez éviter cette option _si possible_ , car les expéditeurs contournent tous les courriers indésirables, usurpation d’identité, protection contre le hameçonnage (sauf le hameçonnage à haut niveau de confiance) et l’authentification de l’expéditeur (SPF, DKIM, DMARC). Cette méthode est idéale pour les tests temporaires uniquement. Les étapes détaillées sont disponibles dans Configurer les stratégies [anti-courrier indésirable dans la rubrique EOP](configure-your-spam-filter-policies.md) .

La limite maximale pour ces listes est d’environ 1 000 entrées ; bien que, vous ne pourrez entrer que 30 entrées dans le portail. Vous devez utiliser PowerShell pour ajouter plus de 30 entrées.

## <a name="considerations-for-bulk-email"></a>Considérations relatives aux e-mails en bloc

Un message électronique SMTP standard est constitué d’une _enveloppe de message_ et d’un contenu de message. L’enveloppe du message contient les informations nécessaires à la transmission et à la remise du message entre les serveurs SMTP. Le contenu du message comporte les champs d’en-tête de message (collectivement appelés l’_en-tête de message_) et le corps du message. L’enveloppe du message est décrite dans RFC 5321 et l’en-tête de message est décrit dans RFC 5322. Les destinataires ne voient jamais l’enveloppe de message réelle, car elle est générée par le processus de transmission de message et ne fait pas réellement partie du message.

- L’adresse `5321.MailFrom` (également appelée adresse **MAIL FROM** , expéditeur P1 ou expéditeur d’enveloppe) est l’adresse e-mail utilisée dans la transmission SMTP du message. Cette adresse e-mail est généralement enregistrée dans le champ **d’en-tête Chemin d’accès** de retour dans l’en-tête de message (bien qu’il soit possible pour l’expéditeur de désigner une autre adresse **e-mail return-path** ). Si le message ne peut pas être remis, il s’agit du destinataire du rapport de non-remise (également appelé NDR ou message de rebond).
- L’adresse `5322.From` de messagerie (également appelée adresse **De** ou expéditeur P2) est l’adresse e-mail dans le champ d’en-tête **From** et l’adresse e-mail de l’expéditeur qui s’affiche dans les clients de messagerie.

Souvent, les adresses et `5322.From` les `5321.MailFrom` adresses sont les mêmes (communication de personne à personne). Toutefois, lorsque l’e-mail est envoyé pour le compte d’une autre personne, les adresses peuvent être différentes. Cela se produit le plus souvent pour les messages électroniques en bloc.

Par exemple, supposons que Blue Yonder Airlines ait embauché Margie’s Travel pour envoyer des messages électroniques publicitaires. Le message que vous recevez dans votre boîte de réception a les propriétés suivantes :

- L’adresse `5321.MailFrom` est blueyonder.airlines@margiestravel.com.
- L’adresse `5322.From` est blueyonder@news.blueyonderairlines.com, ce que vous verrez dans Outlook.

Les listes d’expéditeurs approuvés et les listes de domaines sécurisés dans les stratégies anti-courrier indésirable dans EOP inspectent uniquement les `5322.From` adresses. Ce comportement est similaire à celui des expéditeurs fiables Outlook qui utilisent l’adresse `5322.From` .

Pour empêcher le filtrage de ce message, vous pouvez effectuer les étapes suivantes :

- Ajoutez blueyonder@news.blueyonderairlines.com (l’adresse `5322.From` ) en tant qu’expéditeur sûr Outlook.
- [Utilisez une règle de flux de messagerie](#use-mail-flow-rules) avec une condition qui recherche les messages de blueyonder@news.blueyonderairlines.com (l’adresse `5322.From` ), blueyonder.airlines@margiestravel.com (l’adresse `5321.MailFrom` ) ou les deux.
