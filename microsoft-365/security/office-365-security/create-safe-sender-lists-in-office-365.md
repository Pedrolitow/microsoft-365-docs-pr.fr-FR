---
title: Créer des listes d’expéditeurs approuvés
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150s
ms.assetid: 9721b46d-cbea-4121-be51-542395e6fd21
description: Les administrateurs peuvent en savoir plus sur les options disponibles dans Microsoft 365 et EOP qui permettent aux messages entrants d’ignorer le filtrage du courrier indésirable.
ms.openlocfilehash: ff4f2715ddfe0029aced27ed466a5af8eb95e790
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43637675"
---
# <a name="create-safe-sender-lists"></a>Créer des listes d’expéditeurs approuvés

Si vous êtes un client Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou un client Exchange Online Protection (EOP) autonome sans boîte aux lettres Exchange Online, EOP offre plusieurs moyens de s’assurer que les utilisateurs recevront des messages provenant d’expéditeurs approuvés. Ces options incluent les règles de flux de messagerie Exchange (également appelées règles de transport), les expéditeurs approuvés Outlook, la liste d’adresses IP autorisées (filtrage des connexions) et les listes d’expéditeurs autorisés ou les listes de domaines autorisés dans les stratégies anti-courrier indésirable. Collectivement, ces options peuvent être considérées comme des _listes d’expéditeurs approuvés_.

Les listes d’expéditeurs approuvés disponibles sont décrites dans la liste suivante dans l’ordre, de la plus recommandée au moins recommandé :

1. Règles de flux de messagerie

2. Expéditeurs approuvés Outlook

3. Liste d’adresses IP autorisées (filtrage des connexions)

4. Listes d’expéditeurs autorisés ou listes de domaines autorisés (stratégies anti-courrier indésirable)

Les règles de flux de messagerie offrent une flexibilité maximale pour garantir que seuls les messages corrects sont autorisés. Les listes d’expéditeurs autorisés et de domaines autorisés dans les stratégies de blocage du courrier indésirable ne sont pas aussi sécurisées que la liste d’adresses IP autorisées, car le domaine de messagerie de l’expéditeur est facilement falsifié. Toutefois, la liste d’adresses IP autorisées présente également un risque, car les messages provenant de _n’importe quel_ domaine qui est envoyé à partir de cette adresse IP contourneront le filtrage du courrier indésirable.

> [!IMPORTANT]
> <ul><li>Veillez à contrôler attentivement *les* exceptions de filtrage du courrier indésirable à l’aide des listes des expéditeurs autorisés.</li><li>Bien que vous puissiez utiliser des listes d’expéditeurs approuvés pour vous aider à obtenir des faux positifs (courrier électronique marqué comme courrier indésirable), vous devez envisager d’utiliser des listes d’expéditeurs approuvés comme solution temporaire qui doit être évitée dans la mesure du possible. Nous vous déconseillons de gérer les faux positifs à l’aide de listes d’expéditeurs approuvés, car les exceptions au filtrage du courrier indésirable peuvent ouvrir votre organisation à l’usurpation d’identité et à d’autres attaques. Si vous insistez sur l’utilisation de listes d’expéditeurs approuvés pour gérer les faux positifs, vous devez être vigilant et conserver la rubrique [signaler les messages et les fichiers à Microsoft](report-junk-email-messages-to-microsoft.md) à l’adresse.</li><li>Pour autoriser un domaine à envoyer des courriers électroniques non authentifiés (ignorer la protection contre l’usurpation d’identité) mais ne pas contourner les vérifications anti-courrier indésirable et anti-programme malveillant, vous pouvez l’ajouter à la [liste des expéditeurs approuvés AllowedToSpoof](walkthrough-spoof-intelligence-insight.md)</li><li>EOP et Outlook inspectent les différentes propriétés des messages pour déterminer l’expéditeur du message. Pour plus d’informations, consultez la section [considérations relatives à l’envoi en nombre de messages électroniques](#considerations-for-bulk-email) plus loin dans cette rubrique.</li></ul>

En revanche, vous disposez également de plusieurs options pour bloquer les messages provenant de sources spécifiques en utilisant des _listes d’expéditeurs bloqués_. Pour plus d’informations, voir [Créer des listes d’expéditeurs bloqués dans Office 365](create-block-sender-lists-in-office-365.md).

## <a name="recommended-use-mail-flow-rules"></a>Recommandation Utiliser des règles de flux de messagerie

Règles de flux de messagerie dans Exchange Online et dans un environnement autonome EOP utilisez des conditions et des exceptions pour identifier les messages, ainsi que les actions à effectuer pour ces messages. Pour plus d’informations, consultez la rubrique [Mail flow rules (transport rules) in Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

L’exemple suivant suppose que vous avez besoin d’un courrier électronique de contoso.com pour ignorer le filtrage du courrier indésirable. Pour ce faire, configurez les paramètres suivants :

1. **Condition**: **le domaine de l’expéditeur** \> **est** \> contoso.com.

2. Configurez l’un des paramètres suivants :

   - **Condition de règle de flux de messagerie**: **un en-tête** \> **de message inclut l’un de ces mots** \> **nom** `Authentication-Results` \> d’en-tête : **valeur d’en-tête**: `dmarc=pass` ou. `dmarc=bestguesspass`

     Cette condition vérifie l’état de l’authentification de l’expéditeur du domaine de messagerie d’envoi pour s’assurer que le domaine d’envoi n’est pas usurpé. Pour plus d’informations sur l’authentification de messagerie, voir [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md)et [DMARC](use-dmarc-to-validate-email.md).

   - **Liste d’adresses IP autorisées**: spécifiez l’adresse IP source ou la plage d’adresses dans la stratégie de filtrage des connexions.
  
     Utilisez ce paramètre si le domaine d’envoi n’a pas d’authentification. Être aussi restrictif que possible lorsqu’il s’agit des adresses IP source dans la liste d’adresses IP autorisées. Nous vous recommandons d’utiliser une plage d’adresses IP supérieure ou égale à 24 (moins est préférable). N’utilisez pas de plages d’adresses IP appartenant à des services grand public (par exemple, outlook.com) ou à des infrastructures partagées.

   > [!IMPORTANT]
   > <ul><li>Ne configurez jamais les règles *de flux de messagerie avec le* domaine de l’expéditeur comme condition pour ignorer le filtrage du courrier indésirable. Cela augmentera *considérablement* la probabilité que les attaquants puissent usurper le domaine d’envoi (ou emprunter l’adresse de messagerie complète), ignorer le filtrage du courrier indésirable et ignorer les vérifications d’authentification de l’expéditeur afin que le message arrive dans la boîte de réception du destinataire.</li><li>N’utilisez pas les domaines que vous possédez (également appelés domaines acceptés) ou les domaines populaires (par exemple, microsoft.com) comme conditions dans les règles de flux de messagerie. Cette opération est considérée comme un risque élevé, car elle permet aux attaquants d’envoyer des courriers électroniques qui seraient normalement filtrés.</li><li>Si vous autorisez une adresse IP se trouvant derrière une passerelle NAT (Network Address Translation), vous devez déterminer les serveurs impliqués dans le pool NAT afin de déterminer l’étendue de votre liste d’adresses IP autorisées. Les adresses IP et les participants NAT peuvent modifier. Vous devez vérifier régulièrement vos entrées de liste d’adresses IP autorisées dans le cadre de vos procédures de maintenance standard.</li></ul>

3. **Conditions facultatives**:

   - **L’expéditeur** \> **est interne/externe** \> à **l’extérieur de l’organisation**: cette condition est implicite, mais il est possible de l’utiliser pour prendre en compte les serveurs de messagerie locaux qui ne sont peut-être pas correctement configurés.

   - **L’objet ou** \> le corps **de texte ou le corps de texte comprend l’un des** \> \<Mots-clés\>suivants : Si vous pouvez restreindre davantage les messages en fonction de mots clés ou d’expressions dans la ligne d’objet ou le corps du message, vous pouvez utiliser ces mots comme condition.

4. **Action**: configurez ces deux actions dans la règle :

   a. **Modifier les propriétés** \> du message définir le seuil de probabilité de courrier indésirable **(SCL)** \> **ignorer le filtrage du courrier indésirable**.

   b. **Un en-tête** \> **de message comprend l’un des mots** \> **suivants :** \<CustomHeaderName\> d' \<en\> **-** tête : CustomHeaderValue.

      Par exemple, `X-ETR: Bypass spam filtering for authenticated sender 'contoso.com'`. Si vous avez plusieurs domaines dans la règle, vous pouvez personnaliser le texte d’en-tête en fonction de vos besoins.

      Lorsqu’un message ignore le filtrage du courrier indésirable en raison d’une `SFV:SKN` règle de flux de messagerie, la valeur de la valeur est marquée dans l’en-tête **X-Forefront-antispam-Report** . Si le message provient d’une source située dans la liste d’adresses IP autorisées, la `IPV:CAL` valeur est également ajoutée. Ces valeurs peuvent vous aider à résoudre les problèmes.

![Paramètres de règle de flux de messagerie dans le centre d’administration Exchange pour ignorer le filtrage du courrier indésirable.](../../media/1-AllowList-SkipFilteringFromContoso.png)

## <a name="use-outlook-safe-senders"></a>Utiliser des expéditeurs approuvés Outlook

Au lieu d’un paramètre organisationnel, les utilisateurs ou les administrateurs peuvent ajouter les adresses de messagerie de l’expéditeur à la liste des expéditeurs approuvés dans la boîte aux lettres. Pour obtenir des instructions, consultez la rubrique [configurer les paramètres de courrier indésirable sur les boîtes aux lettres Exchange Online dans Office 365](configure-junk-email-settings-on-exo-mailboxes.md).

Lorsque les messages ignorent le filtrage du courrier indésirable en raison de la liste des expéditeurs approuvés d’un utilisateur, le champ d’en `SFV:SFE`-tête **X-Forefront-antispam-Report** contient la valeur qui indique que le courrier indésirable, l’usurpation et le filtrage du hameçonnage ont été ignorés.

## <a name="use-the-ip-allow-list"></a>Utiliser la liste d’adresses IP autorisées

Si vous ne pouvez pas utiliser les règles de flux de messagerie comme décrit précédemment, la meilleure solution consiste à ajouter le ou les serveurs de messagerie source à la liste d’adresses IP autorisées dans la stratégie de filtrage des connexions. Pour plus d’informations, consultez la rubrique [configurer le filtrage des connexions dans Office 365](configure-the-connection-filter-policy.md).

**Remarques** :

- Il est important de conserver le nombre d’adresses IP autorisées à un minimum, donc d’éviter d’utiliser des plages d’adresses IP entières dès que possible.

- N’utilisez pas de plages d’adresses IP appartenant à des services grand public (par exemple, outlook.com) ou à des infrastructures partagées.

- Examinez régulièrement les entrées de la liste d’adresses IP autorisées et supprimez les entrées dont vous n’avez plus besoin.

> [!CAUTION]
> Sans une vérification supplémentaire comme les règles de flux de messagerie, les messages provenant de sources dans la liste d’adresses IP autorisées ignorent les vérifications de filtrage du courrier indésirable et d’authentification de l’expéditeur (SPF, DKIM, DMARC). Cela crée un risque élevé que des attaquants délivrent des courriers électroniques à la boîte de réception qui seraient normalement filtrés.

## <a name="use-allowed-sender-lists-or-allowed-domain-lists"></a>Utiliser des listes d’expéditeurs autorisés ou des listes de domaines autorisés

L’option la moins intéressante consiste à utiliser la liste des expéditeurs autorisés ou la liste des domaines autorisés dans les stratégies de blocage du courrier indésirable. Vous devez éviter cette option *si possible* , car les expéditeurs contournent tout le courrier indésirable, l’usurpation d’identité et la protection contre le hameçonnage, et l’authentification des expéditeurs (SPF, DKIM, DMARC). Cette méthode est recommandée pour le test temporaire uniquement. La procédure détaillée est décrite dans la rubrique [configurer des stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md) .

La limite maximale de ces listes est d’environ 1000 entrées ; Bien que vous ne puissiez entrer que 30 entrées dans le portail. Vous devez utiliser PowerShell pour ajouter plus de 30 entrées.

> [!CAUTION]
> <ul><li>Cette méthode crée un risque élevé de remise des messages électroniques à la boîte de réception qui seraient normalement filtrés.</li><li>N’utilisez pas les domaines que vous possédez (également appelés domaines acceptés) ou les domaines populaires (par exemple, microsoft.com) dans les listes de domaines autorisés.</li></ul>

## <a name="considerations-for-bulk-email"></a>Considérations relatives au courrier en nombre

Un message électronique SMTP standard est constitué d’une *enveloppe de message* et d’un contenu de message. L’enveloppe de message contient les informations requises pour la transmission et la remise du message entre les serveurs SMTP. Le contenu du message comporte les champs d’en-tête de message (collectivement appelés l’*en-tête de message*) et le corps du message. L’enveloppe de message est décrite dans la norme RFC 5321 et l’en-tête de message est décrit dans la spécification RFC 5322. Les destinataires ne voient jamais l’enveloppe de message réelle, car elle est générée par le processus de transmission des messages, et elle ne fait pas partie du message.

- L' `5321.MailFrom` adresse (également appelée adresse **de messagerie de** l’expéditeur, expéditeur P1 ou expéditeur de l’enveloppe) est l’adresse de messagerie utilisée dans la transmission SMTP du message. Cette adresse de messagerie est généralement enregistrée dans le champ d’en-tête de **retour** de l’en-tête du message (bien que l’expéditeur ait la possibilité de désigner une autre adresse de messagerie de **chemin d’accès** ). Si le message ne peut pas être remis, il s’agit du destinataire de la notification d’échec de remise (également appelée notification de non-remise).

- Le `5322.From` (également appelé l’adresse **de** l’expéditeur ou l’expéditeur P2) est l’adresse de messagerie dans le champ de l’en-tête **de** , et est l’adresse de messagerie de l’expéditeur affichée dans les clients de messagerie.

Fréquemment, les `5321.MailFrom` adresses `5322.From` et sont identiques (communication de personne à personne). Toutefois, lorsqu'un courrier électronique est envoyé à la place d'une autre personne, les adresses sont souvent différentes. Cela se produit généralement avec les messages de courrier indésirable.

Par exemple, supposons que Blue Yonder Airlines a embauché Margie’s Travel pour envoyer sa publicité par courrier électronique. Le message que vous recevez dans votre boîte de réception comporte les propriétés suivantes :

- L' `5321.MailFrom` adresse est blueyonder.Airlines@margiestravel.com.

- L' `5322.From` adresse est blueyonder@news.blueyonderairlines.com, ce que vous verrez dans Outlook.

Listes des expéditeurs approuvés et listes de domaines fiables dans les stratégies de blocage du courrier indésirable dans EOP, inspectez les `5321.MailFrom` adresses et. `5322.From` Les expéditeurs approuvés Outlook utilisent uniquement `5322.From` l’adresse.

Pour empêcher le filtrage de ce message, procédez comme suit :

- Ajoutez blueyonder@news.blueyonderairlines.com (l' `5322.From` adresse) en tant qu’expéditeur approuvé Outlook.

- [Utilisez une règle de flux de messagerie](#recommended-use-mail-flow-rules) avec une condition qui recherche les messages provenant de `5322.From` blueyonder@news.blueyonderairlines.com (l’adresse, `5321.MailFrom`blueyonder.Airlines@margiestravel.com (le) ou les deux.

Pour plus d’informations, consultez la rubrique [créer des listes d’expéditeurs approuvés dans Office 365](create-safe-sender-lists-in-office-365.md).
