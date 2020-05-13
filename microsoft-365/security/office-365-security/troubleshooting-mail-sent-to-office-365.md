---
title: Dépannage des messages envoyés à Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: troubleshooting
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: f4caa4e1-e414-4b21-8822-31c08064c059
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Cet article fournit des informations sur la résolution des problèmes liés à l’envoi de messages électroniques à des boîtes de réception dans Microsoft 365 & meilleures pratiques pour le publipostage vers les clients Microsoft 365.
ms.openlocfilehash: 0d9c1646aa7491b3da458c7cb0ddeb908873153a
ms.sourcegitcommit: 93c0088d272cd45f1632a1dcaf04159f234abccd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208596"
---
# <a name="troubleshooting-mail-sent-to-microsoft-365"></a>Dépannage des messages envoyés à Microsoft 365

Cet article fournit des informations de dépannage pour les expéditeurs qui rencontrent des problèmes lors de la tentative d’envoi de messages électroniques à des boîtes de réception dans Microsoft 365 et les meilleures pratiques pour le publipostage à des clients.

## <a name="are-you-managing-your-ip-and-domains-sending-reputation"></a>Vous gérez la réputation de l’expéditeur de votre IP et domaine ?

Les technologies de filtrage EOP sont conçues pour assurer une protection contre le courrier indésirable pour Microsoft 365, ainsi que d’autres produits Microsoft tels que Exchange Server. Nous tirons également parti de SPF, DKIM et DMARC ; des technologies d'authentification de messagerie qui aident à résoudre le problème d'usurpation et d'hameçonnage en vérifiant que le domaine qui envoie l'e-mail est autorisé à le faire. Le filtrage EOP est affecté par de nombreux facteurs liés à l'IP d'envoi, le domaine, l'authentification, la précision de la liste, les taux de plaintes, le contenu, etc. Parmi ces facteurs, l'un des facteurs principaux responsable de la baisse de réputation d'un expéditeur et sa capacité à remettre un e-mail est son taux de plainte de courrier indésirable.

## <a name="are-you-sending-email-from-new-ip-addresses"></a>Vous envoyez des e-mails depuis de nouvelles adresses IP ?

Les adresses IP qui n’ont pas été utilisées précédemment pour envoyer des e-mails n’ont généralement pas de réputation créée dans nos systèmes. Par conséquent, les e-mails provenant de nouvelles adresses IP ont plus tendance à rencontrer des problèmes de remise. Une fois que l’adresse IP a créé une réputation de non envoi de courrier indésirable, EOP permet généralement une meilleure expérience de remise des courriers électroniques.

Les nouvelles adresses IP qui sont ajoutées pour des domaines authentifiés sous des enregistrements SPF existants bénéficient généralement de l’avantage d’hériter de la réputation d’envoi du domaine. Si votre domaine a une bonne réputation d’envoi, les nouvelles adresses IP peuvent expérimenter un temps de montée en puissance plus rapide. Une nouvelle adresse IP pourra être entièrement augmentée au bout de quelques semaines ou plus tôt selon le volume, la précision de la liste et les taux de plaintes de courrier indésirable.

## <a name="confirm-that-your-dns-is-set-up-correctly"></a>Confirmer que votre DNS est configuré correctement

Pour savoir comment créer et gérer des enregistrements DNS, y compris l’enregistrement MX requis pour le routage du courrier, vous devez contacter votre fournisseur d’hébergement DNS.

## <a name="ensure-that-you-do-not-advertise-yourself-as-a-non-routable-ip"></a>Vérifier que vous ne vous annoncez pas sous la forme d’une adresse IP non routable

Il se peut que nous n’acceptions pas les e-mails provenant d’expéditeurs dont la recherche DNS inversée a échoué. Dans certains cas, des expéditeurs légitimes s’annoncent de façon incorrecte sous la forme d’une adresse IP routable non Internet lorsqu’ils tentent d’ouvrir une connexion à EOP. Les adresses IP réservées pour le réseau privé (non routable) incluent :

- 192.168.0.0/16 (ou 192.168.0.0 - 192.168.255.255)

- 10.0.0.0/8 (ou 10.0.0.0 - 10.255.255.255)

- 172.16.0.0/11 (ou 172.16.0.0 - 172.31.255.255)

## <a name="you-received-a-non-delivery-report-ndr-when-sending-email-to-a-user-in-office-365"></a>Vous avez reçu une notification d’échec de remise lors de l’envoi d’un message électronique à un utilisateur dans Office 365

Certains problèmes de remise sont dus au blocage de l'adresse IP de l'expéditeur par Microsoft ou à l'identification du compte d'utilisateur comme expéditeur interdit en raison des activité de courrier indésirable précédentes. Si vous pensez que vous avez reçu la notification d'échec de remise par erreur, suivez d'abord toutes les instructions indiquées dans le message de notification d'échec de remise pour résoudre le problème.

Pour plus d’informations sur l’erreur que vous avez reçue, consultez la liste des codes d’erreur dans notifications d’échec de [remise par courrier électronique dans Exchange Online](https://docs.microsoft.com/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

 Par exemple, si vous recevez la notification d’inversion suivante, elle indique que l’adresse IP d’envoi a été bloquée par Microsoft :

 `550 5.7.606-649 Access denied, banned sending IP [x.x.x.x]; To request removal from this list please visit https://sender.office.com/ and follow the directions.`

Pour demander la suppression de cette liste, vous pouvez [utiliser le portail supprimer de la liste pour vous supprimer de la liste des expéditeurs bloqués](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="my-email-landed-in-the-recipients-junk-email-folder"></a>Mon e-mail s’est retrouvé dans le dossier de courrier indésirable du destinataire

Si un message a été incorrectement identifié comme courrier indésirable par EOP, vous pouvez collaborer avec le destinataire pour envoyer ce faux positif à l'équipe d'analyse du courrier indésirable de Microsoft. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="traffic-from-my-ip-address-is-throttled-by-eop"></a>Le trafic provenant de mon adresse IP est limité par EOP

Si vous recevez une notification d'échec de remise d'EOP, cela indique que votre adresse IP est limitée par EOP, par exemple :

 `host xxxx.outlook.com [x.x.x.x]: 451 4.7.550 Access denied, please try again later`

Vous avez reçu une notification d'échec de remise car une activité suspecte a été détectée sur l'adresse IP et a été restreinte temporairement le temps d'effectuer des évaluations supplémentaires. Si la suspicion est désactivée au cours de l'évaluation, cette restriction est bientôt levée.

## <a name="i-cant-receive-email-from-senders-in-microsoft-365"></a>Je ne parviens pas à recevoir des courriers électroniques des expéditeurs dans Microsoft 365

 Afin de recevoir des messages de la part de nos utilisateurs, assurez-vous que votre réseau autorise les connexions provenant des adresses IP utilisées par EOP dans nos centres de données. Pour plus d’informations, consultez la rubrique [Exchange Online Protection IP addresses](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges).

## <a name="best-practices-for-bulk-emailing-to-microsoft-365-users"></a>Meilleures pratiques pour l’envoi en nombre de messages électroniques aux utilisateurs de Microsoft 365

Si vous effectuez souvent des campagnes d’envoi en masse à des utilisateurs de Microsoft 365 et que vous souhaitez vous assurer que vos e-mails arrivent de manière sûre et opportune, suivez les conseils de cette section.

### <a name="ensure-that-the-from-name-reflects-who-is-sending-the-message"></a>Vérifier que le nom de l’expéditeur indique qui envoie le message

L'Objet doit être un bref résumé du contenu du message, et le corps du message doit clairement et brièvement indiquer l'objet de l'offre, du service ou du produit. Par exemple :

Correct :

> De : marketing@shoppershandbag.com <br/> Objet : catalogue mis à jour pour la saison de Noël !

Incorrect :

> De : someone@outlook.com <br/> Objet : Catalogues

Plus vous vous présentez et décrivez ce que vous faites de façon claire, moins vos courriers seront bloqués par la plupart des filtres anti-spam.

### <a name="always-include-an-unsubscribe-option-in-campaign-emails"></a>Toujours inclure une option de désinscription dans les e-mails de campagne

Les e-mails de marketing, notamment les bulletins d'informations, doivent toujours inclure une option permettant de se désinscrire pour ne plus recevoir de futurs e-mails. Par exemple :

 `This email was sent to example@contoso.com by sender@fabrikam.com.`

 `Update Profile/Email Address | Instant removal with SafeUnsubscribe&trade; | Privacy Policy`

Certains expéditeurs incluent cette option en demandant aux destinataires d'envoyer un e-mail à un certain alias avec « Se désabonner » dans l'objet. Cela n'est pas préférable à l'exemple en un seul clic ci-dessus. Si vous choisissez de demander aux destinataires d'envoyer un message, assurez-vous que lorsqu'ils cliquent sur le lien, tous les champs requis sont renseignés au préalable.

### <a name="use-the-double-opt-in-option-for-marketing-email-or-newsletter-registration"></a>Utiliser l’option de contrôle de consentement double pour l’enregistrement à des e-mails de marketing ou à des bulletins d’informations

Cette pratique est recommandée par le secteur si votre entreprise requiert que les utilisateurs enregistrent leurs informations de contact ou les y encourage pour accéder à vos produits ou services. Certaines sociétés ont pris l'habitude d'inscrire automatiquement leurs utilisateurs pour les e-mails de marketing ou les bulletins d'informations électroniques lors du processus d'enregistrement. Néanmoins, cela est considéré comme une pratique marketing discutables dans le monde du filtrage des messages électroniques.

Au cours du processus d'enregistrement, si la case à cocher « Oui, merci de m'envoyer votre bulletin d'informations » ou « Oui, merci de m'envoyer les offres spéciales » est sélectionnée par défaut, les utilisateurs qui ne font pas assez attention risquent de s'inscrire par inadvertance aux e-mails de marketing ou aux bulletins d'informations qu'ils ne souhaitent pas recevoir.

 Nous vous recommandons l'option de contrôle de consentement double à la place, ce qui signifie que la case à cocher pour les e-mails de marketing ou les bulletins d'informations est désactivée par défaut. En outre, une fois que le formulaire d'inscription a été envoyé, un e-mail de vérification est envoyé à l'utilisateur avec une URL qui leur permet de confirmer leur décision de recevoir des e-mails de marketing.

 Cela permet de garantir que seuls les utilisateurs qui souhaitent recevoir des e-mails de marketing sont inscrits pour les e-mails, en désactivant ensuite l'entreprise émettrice de toute pratique discutable.

### <a name="ensure-that-email-message-content-is-transparent-and-traceable"></a>Vérifier que le contenu des messages électroniques est transparent et qu’il est possible de le suivre

La façon dont les e-mails sont envoyés est aussi importante que leur contenu. Lorsque vous créez le contenu d’un e-mail, utilisez les meilleures pratiques suivantes pour vous assurer que vos e-mails ne seront pas signalés par des services de filtrage des messages électroniques :

- Lorsque le message de l'e-mail demande aux destinataires d'ajouter l'expéditeur au carnet d'adresses, il doit clairement indiquer qu'une telle action ne constitue pas une garantie de remise.

- Les redirections incluses dans le corps du message doivent être similaires et cohérentes et non multiples et variées. Une redirection dans ce contexte est tout élément qui pointe en dehors du message, comme des liens et des documents. Si vous avez de très nombreux liens Se désabonner ou Mettre à jour le profil, ils doivent tous pointer vers le même domaine. Par exemple :

  Correct :

  `unsubscribe.bulkmailer.com`

  `profile.bulkmailer.com`

  `options.bulkmailer.com`

  Incorrect :

  `unsubscribe.bulkmailer.com`

  `profile.excite.com`

  `options.yahoo.com`

- Évitez les images et les pièces jointes volumineuses, ou les messages contenant uniquement une image.

- Vos paramètres publics de confidentialité ou P3P doivent signaler clairement la présence des pixels de suivi (bogues ou balises web).

### <a name="remove-incorrect-email-aliases-from-your-databases"></a>Supprimer les alias de messagerie incorrects de vos bases de données

Les alias de messagerie de votre base de données qui créent un renvoi sont inutiles et exposent vos messages électroniques sortants à des risques d’examen approfondi par les services de filtrage de courrier électronique. Assurez-vous que votre base de données de messagerie est à jour.
