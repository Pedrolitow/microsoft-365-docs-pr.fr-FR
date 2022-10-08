---
title: Résolution des problèmes d’e-mails envoyés à Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: troubleshooting
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: f4caa4e1-e414-4b21-8822-31c08064c059
ms.collection:
- m365-security
ms.custom:
- seo-marvel-apr2020
description: Cet article fournit des informations de dépannage pour les problèmes liés à l’envoi d’e-mails aux boîtes de réception dans Microsoft 365 & meilleures pratiques pour le publipostage en bloc aux clients Microsoft 365.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 7e9410da7ddf8fc8d125d97601a7bc57db50583a
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68075051"
---
# <a name="troubleshooting-mail-sent-to-microsoft-365"></a>Résolution des problèmes d’e-mails envoyés à Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

Cet article fournit des informations de dépannage pour les expéditeurs qui rencontrent des problèmes lors de la tentative d’envoi de courrier électronique à des boîtes de réception dans Microsoft 365 et les meilleures pratiques pour le publipostage en bloc aux clients.

## <a name="are-you-managing-your-ip-and-domains-sending-reputation"></a>Vous gérez la réputation de l’expéditeur de votre IP et domaine ?

Les technologies de filtrage EOP sont conçues pour fournir une protection anti-courrier indésirable pour Microsoft 365 et d’autres produits Microsoft tels que Exchange Server. Nous utilisons également SPF, DKIM et DMARC ; technologies d’authentification par e-mail qui permettent de résoudre le problème de l’usurpation d’identité et du hameçonnage en vérifiant que le domaine qui envoie l’e-mail est autorisé à le faire. Le filtrage EOP est influencé par de nombreux facteurs liés à l’adresse IP d’envoi, au domaine, à l’authentification, à la précision de la liste, aux taux de plaintes, au contenu, etc. Parmi ces facteurs, l'un des facteurs principaux responsable de la baisse de réputation d'un expéditeur et sa capacité à remettre un e-mail est son taux de plainte de courrier indésirable.

## <a name="are-you-sending-email-from-new-ip-addresses"></a>Vous envoyez des e-mails depuis de nouvelles adresses IP ?

IP addresses not previously used to send email typically don't have any reputation built up in our systems. As a result, emails from new IPs are more likely to experience delivery issues. Once the IP has built a reputation for not sending spam, EOP will typically allow for a better email delivery experience.

New IPs that are added for domains that are authenticated under existing SPF records typically experience the added benefit of inheriting some of the domain's sending reputation. If your domain has a good sending reputation new IPs may experience a faster ramp up time. A new IP can expect to be fully ramped within a couple of weeks or sooner depending on volume, list accuracy, and junk email complaint rates.

## <a name="confirm-that-your-dns-is-set-up-correctly"></a>Confirmer que votre DNS est configuré correctement

Pour savoir comment créer et gérer des enregistrements DNS, y compris l’enregistrement MX requis pour le routage du courrier, vous devez contacter votre fournisseur d’hébergement DNS.

## <a name="ensure-that-you-do-not-advertise-yourself-as-a-non-routable-ip"></a>Vérifier que vous ne vous annoncez pas sous la forme d’une adresse IP non routable

We may not accept email from senders who fail a reverse-DNS lookup. In some cases, legitimate senders advertise themselves incorrectly as a non-internet routable IP when attempting to open a connection to EOP. IP addresses that are reserved for private (non-routable) networking include:

- 192.168.0.0/16 (ou 192.168.0.0 - 192.168.255.255)
- 10.0.0.0/8 (ou 10.0.0.0 - 10.255.255.255)
- 172.16.0.0/11 (ou 172.16.0.0 - 172.31.255.255)

## <a name="you-received-a-non-delivery-report-ndr-when-sending-email-to-a-user-in-office-365"></a>Vous avez reçu une notification d'échec de remise lors de l'envoi de messages électroniques à un utilisateur dans Office 365

Some delivery issues are the result of the sender's IP address being blocked by Microsoft or because the user account is identified as banned sender due to previous spam activity. If you believe that you have received the NDR in error, first follow any instructions in the NDR message to resolve the issue.

Pour plus d’informations sur l’erreur que vous avez reçue, consultez la liste des codes d’erreur dans [Email rapports de non-remise dans Exchange Online](/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

 Par exemple, si vous recevez la DNR suivante, cela indique que l’adresse IP d’envoi a été bloquée par Microsoft :

 `550 5.7.606-649 Access denied, banned sending IP [x.x.x.x]; To request removal from this list please visit https://sender.office.com/ and follow the directions.`

Pour demander la suppression de cette liste, vous pouvez [utiliser le portail de suppression pour vous supprimer de la liste des expéditeurs bloqués](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="my-email-landed-in-the-recipients-junk-email-folder"></a>Mon e-mail est arrivé dans le dossier Courrier indésirable du destinataire Email

Si un message a été incorrectement identifié comme courrier indésirable par EOP, vous pouvez collaborer avec le destinataire pour envoyer ce faux positif à l'équipe d'analyse du courrier indésirable de Microsoft. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="traffic-from-my-ip-address-is-throttled-by-eop"></a>Le trafic provenant de mon adresse IP est limité par EOP

Si vous recevez une notification d’échec de remise d’EOP, cela indique que votre adresse IP est limitée par EOP, par exemple :

 `host xxxx.outlook.com [x.x.x.x]: 451 4.7.550 Access denied, please try again later`

You received the NDR because suspicious activity has been detected from the IP address and it has been temporarily restricted while it is being further evaluated. If the suspicion is cleared through evaluation, this restriction will be lifted shortly.

## <a name="i-cant-receive-email-from-senders-in-microsoft-365"></a>Je ne peux pas recevoir d’e-mail d’expéditeurs dans Microsoft 365

 Afin de recevoir des messages de la part de nos utilisateurs, assurez-vous que votre réseau autorise les connexions provenant des adresses IP utilisées par EOP dans nos centres de données. Pour plus d’informations, consultez [Exchange Online Protection adresses IP](../../enterprise/urls-and-ip-address-ranges.md).

## <a name="best-practices-for-bulk-emailing-to-microsoft-365-users"></a>Meilleures pratiques pour l’envoi de messages électroniques en bloc aux utilisateurs de Microsoft 365

Si vous effectuez souvent des campagnes de messagerie en bloc pour les utilisateurs de Microsoft 365 et que vous souhaitez vous assurer que vos e-mails arrivent en toute sécurité et en temps opportun, suivez les conseils de cette section.

### <a name="ensure-that-the-from-name-reflects-who-is-sending-the-message"></a>Assurez-vous que le nom De reflète qui envoie le message

The Subject should be a brief summary of what the message is about, and the message body should clearly and succinctly indicate what the offering, service, or product is about. For example:

Correct :

> De : marketing@shoppershandbag.com <br> Objet : Catalogue mis à jour pour la saison de Noël!

Incorrect :

> De : someone@outlook.com <br> Objet : Catalogues

Plus vous vous présentez et décrivez ce que vous faites de façon claire, moins vos courriers seront bloqués par la plupart des filtres anti-spam.

### <a name="always-include-an-unsubscribe-option-in-campaign-emails"></a>Toujours inclure une option de désinscription dans les e-mails de campagne

Les e-mails de marketing, notamment les bulletins d’informations, doivent toujours inclure une option permettant de se désinscrire pour ne plus recevoir de futurs e-mails. Par exemple :

 `This email was sent to example@contoso.com by sender@fabrikam.com.`

 `Update Profile/Email Address | Instant removal with SafeUnsubscribe&trade; | Privacy Policy`

Some senders include this option by requiring recipients to send an email to a certain alias with "Unsubscribe" in the subject. This is not preferable to the one-click example above. If you do choose to require recipients to send a mail, ensure that when they click the link, all the required fields are pre-populated.

### <a name="use-the-double-opt-in-option-for-marketing-email-or-newsletter-registration"></a>Utiliser l’option de contrôle de consentement double pour l’enregistrement à des e-mails de marketing ou à des bulletins d’informations

This industry best practice is recommended if your company requires or encourages users to register their contact information in order to access your product or services. Some companies make it a practice to automatically sign up their users for marketing emails or e-newsletters during the registration process, but this is considered a questionable marketing practice in the world of email filtering.

Au cours du processus d'enregistrement, si la case à cocher « Oui, merci de m'envoyer votre bulletin d'informations » ou « Oui, merci de m'envoyer les offres spéciales » est sélectionnée par défaut, les utilisateurs qui ne font pas assez attention risquent de s'inscrire par inadvertance aux e-mails de marketing ou aux bulletins d'informations qu'ils ne souhaitent pas recevoir.

 Microsoft recommande plutôt l’option de double adhésion, ce qui signifie que la case à cocher pour les e-mails marketing ou les bulletins d’informations est désactivée par défaut. En outre, une fois que le formulaire d'inscription a été envoyé, un e-mail de vérification est envoyé à l'utilisateur avec une URL qui leur permet de confirmer leur décision de recevoir des e-mails de marketing.

 Cela permet de garantir que seuls les utilisateurs qui souhaitent recevoir des e-mails de marketing sont inscrits pour les e-mails, en désactivant ensuite l’entreprise émettrice de toute pratique discutable.

### <a name="ensure-that-email-message-content-is-transparent-and-traceable"></a>Vérifier que le contenu des messages électroniques est transparent et qu’il est possible de le suivre

Just as important as the way the emails are sent is the content they contain. When creating email content, use the following best practices to ensure that your emails will not be flagged by email filtering services:

- Lorsque le message de l'e-mail demande aux destinataires d'ajouter l'expéditeur au carnet d'adresses, il doit clairement indiquer qu'une telle action ne constitue pas une garantie de remise.

- Redirects included in the body of the message should be similar and consistent, and not multiple and varied. A redirect in this context is anything that points away from the message, such as links and documents. If you have a lot of advertising or Unsubscribe links or Update the Profile links, they should all point to the same domain. For example:

  Correct (tous les domaines sont identiques) :

  `unsubscribe.bulkmailer.com`

  `profile.bulkmailer.com`

  `options.bulkmailer.com`

  Incorrect (tous les domaines sont différents) :

  `unsubscribe.bulkmailer.com`

  `profile.excite.com`

  `options.yahoo.com`

- Évitez les images et les pièces jointes volumineuses, ou les messages contenant uniquement une image.

- Vos paramètres publics de confidentialité ou P3P doivent signaler clairement la présence des pixels de suivi (bogues ou balises web).

### <a name="remove-incorrect-email-aliases-from-your-databases"></a>Supprimer les alias de messagerie incorrects de vos bases de données

Any email alias in your database that creates a bounce-back is unnecessary and puts your outbound emails at risk for further scrutiny by email filtering services. Ensure that your email database is up-to-date.
