---
title: Comment EOP valide l’adresse From pour empêcher le hameçonnage
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- OWC150
- MET150
ms.assetid: eef8408b-54d3-4d7d-9cf7-ad2af10b2e0e
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent en savoir plus sur les types d’adresses e-mail acceptées ou rejetées par Exchange Online Protection (EOP) et Outlook.com pour empêcher le hameçonnage.
ms.custom: seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: a4687ca9d9135a8feef66f4caabfcb7a3a2313b4
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67598404"
---
# <a name="how-eop-validates-the-from-address-to-prevent-phishing"></a>Comment EOP valide l’adresse From pour empêcher le hameçonnage

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les attaques par hameçonnage constituent une menace constante pour toute organisation de messagerie. En plus [d’utiliser des adresses e-mail d’expéditeur usurpées (falsifiées), les attaquants](anti-spoofing-protection.md) utilisent souvent des valeurs dans l’adresse From qui violent les normes Internet. Pour éviter ce type de hameçonnage, Exchange Online Protection (EOP) et Outlook.com maintenant exiger que les messages entrants incluent une adresse From conforme À RFC, comme décrit dans cet article. Cette mise en œuvre a été activée en novembre 2017.

**Remarques** :

- Si vous recevez régulièrement des e-mails d’organisations mal formées à partir d’adresses, comme décrit dans cet article, encouragez ces organisations à mettre à jour leurs serveurs de messagerie pour qu’ils se conforment aux normes de sécurité modernes.

- Le champ Expéditeur associé (utilisé par Send on Behalf et les listes de diffusion) n’est pas affecté par ces exigences. Pour plus d’informations, consultez le billet de blog suivant : [Que signifie le terme « expéditeur » d’un e-mail ?](/archive/blogs/tzink/what-do-we-mean-when-we-refer-to-the-sender-of-an-email)

## <a name="an-overview-of-email-message-standards"></a>Vue d’ensemble des normes relatives aux messages électroniques

Un message électronique SMTP standard est constitué d’une *enveloppe de message* et d’un contenu de message. L’enveloppe du message contient les informations nécessaires à la transmission et à la remise du message entre les serveurs SMTP. Le contenu du message comporte les champs d’en-tête de message (collectivement appelés l’*en-tête de message*) et le corps du message. L’enveloppe du message est décrite dans [RFC 5321](https://tools.ietf.org/html/rfc5321) et l’en-tête de message est décrit dans [RFC 5322](https://tools.ietf.org/html/rfc5322). Les destinataires ne voient jamais l’enveloppe de message réelle, car elle est générée par le processus de transmission de message et ne fait pas réellement partie du message.

- L’adresse `5321.MailFrom` (également appelée adresse **MAIL FROM** , expéditeur P1 ou expéditeur d’enveloppe) est l’adresse e-mail utilisée dans la transmission SMTP du message. Cette adresse e-mail est généralement enregistrée dans le champ **d’en-tête Chemin d’accès** de retour dans l’en-tête de message (bien qu’il soit possible pour l’expéditeur de désigner une autre adresse **e-mail return-path** ).

- L’adresse `5322.From` de messagerie (également appelée adresse De ou expéditeur P2) est l’adresse e-mail dans le champ d’en-tête **From** et l’adresse e-mail de l’expéditeur qui s’affiche dans les clients de messagerie. L’adresse From est l’objet des exigences décrites dans cet article.

L’adresse From est définie en détail sur plusieurs RFC (par exemple, les sections RFC 5322 3.2.3, 3.4 et 3.4.1 et [RFC 3696](https://tools.ietf.org/html/rfc3696)). Il existe de nombreuses variantes sur l’adressage et ce qui est considéré comme valide ou non valide. Pour simplifier, nous vous recommandons le format et les définitions suivants :

`From: "Display Name" <EmailAddress>`

- **Nom d’affichage** : expression facultative qui décrit le propriétaire de l’adresse e-mail.

  - Nous vous recommandons de toujours placer le nom complet entre guillemets doubles (« ) comme indiqué. Si le nom d’affichage contient une virgule, vous _devez_ placer la chaîne entre guillemets doubles par RFC 5322.
  - Si l’adresse From inclut un nom d’affichage, la valeur EmailAddress doit être placée entre crochets (< >) comme indiqué.
  - Microsoft recommande vivement d’insérer un espace entre le nom d’affichage et l’adresse e-mail.

- **EmailAddress** : une adresse e-mail utilise le format `local-part@domain`:

  - **local-part** : chaîne qui identifie la boîte aux lettres associée à l’adresse. Cette valeur est unique dans le domaine. Souvent, le nom d’utilisateur ou le GUID du propriétaire de la boîte aux lettres est utilisé.
  - **domaine** : nom de domaine complet (FQDN) du serveur de messagerie qui héberge la boîte aux lettres identifiée par la partie locale de l’adresse e-mail.

  Voici quelques considérations supplémentaires pour la valeur EmailAddress :

  - Une seule adresse e-mail.
  - Nous vous recommandons de ne pas séparer les crochets avec des espaces.
  - N’incluez pas de texte supplémentaire après l’adresse e-mail.

## <a name="examples-of-valid-and-invalid-from-addresses"></a>Exemples d’adresses De valides et non valides

Les adresses de messagerie De suivantes sont valides :

- `From: sender@contoso.com`

- `From: <sender@contoso.com>`

- `From: < sender@contoso.com >` (Non recommandé, car il existe des espaces entre les crochets et l’adresse e-mail.)

- `From: "Sender, Example" <sender.example@contoso.com>`

- `From: "Microsoft 365" <sender@contoso.com>`

- `From: Microsoft 365 <sender@contoso.com>` (Non recommandé, car le nom d’affichage n’est pas placé entre guillemets doubles.)

Les adresses de courrier suivantes ne sont pas valides :

- **Non à partir de l’adresse** : certains messages automatisés n’incluent pas d’adresse From. Par le passé, lorsque Microsoft 365 ou Outlook.com recevait un message sans adresse From, le service ajoutait l’adresse par défaut Suivante à partir de : pour rendre le message livrable :

  `From: <>`

  À présent, les messages avec une adresse From vide ne sont plus acceptés.

- `From: Microsoft 365 sender@contoso.com` (Le nom complet est présent, mais l’adresse e-mail n’est pas placée entre crochets.)

- `From: "Microsoft 365" <sender@contoso.com> (Sent by a process)` (Texte après l’adresse e-mail.)

- `From: Sender, Example <sender.example@contoso.com>` (Le nom d’affichage contient une virgule, mais n’est pas placé entre guillemets doubles.)

- `From: "Microsoft 365 <sender@contoso.com>"` (La valeur entière est incorrectement placée entre guillemets doubles.)

- `From: "Microsoft 365 <sender@contoso.com>" sender@contoso.com` (Le nom complet est présent, mais l’adresse e-mail n’est pas placée entre crochets.)

- `From: Microsoft 365<sender@contoso.com>` (Aucun espace entre le nom d’affichage et le crochet gauche.)

- `From: "Microsoft 365"<sender@contoso.com>` (Aucun espace entre le guillemet double fermant et le crochet gauche.)

## <a name="suppress-auto-replies-to-your-custom-domain"></a>Supprimer les réponses automatiques à votre domaine personnalisé

Vous ne pouvez pas utiliser la valeur `From: <>` pour supprimer les réponses automatiques. Au lieu de cela, vous devez configurer un enregistrement MX null pour votre domaine personnalisé. Les réponses automatiques (et toutes les réponses) sont naturellement supprimées, car il n’existe aucune adresse publiée à laquelle le serveur qui répond peut envoyer des messages.

- Choisissez un domaine de messagerie qui ne peut pas recevoir d’e-mail. Par exemple, si votre domaine principal est contoso.com, vous pouvez choisir noreply.contoso.com.

- L’enregistrement MX null pour ce domaine se compose d’une seule période.

Par exemple :

```text
noreply.contoso.com IN MX .
```

Pour plus d’informations sur la configuration des enregistrements MX, consultez [Créer des enregistrements DNS auprès de n’importe quel fournisseur d’hébergement DNS pour Microsoft 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

Pour plus d’informations sur la publication d’un MX null, consultez [RFC 7505](https://tools.ietf.org/html/rfc7505).

## <a name="override-from-address-enforcement"></a>Remplacement de l’application de l’adresse

Pour contourner les exigences de l’adresse From pour les e-mails entrants, vous pouvez utiliser la liste d’autorisations IP (filtrage de connexion) ou les règles de flux de courrier (également appelées règles de transport), comme décrit dans [Créer des listes d’expéditeurs fiables dans Microsoft 365](create-safe-sender-lists-in-office-365.md).

Vous ne pouvez pas remplacer les exigences de l’adresse De pour les e-mails sortants que vous envoyez à partir de Microsoft 365. En outre, Outlook.com n’autorise pas les remplacements de quelque nature que ce soit, même par le biais de la prise en charge.

## <a name="other-ways-to-prevent-and-protect-against-cybercrimes-in-microsoft-365"></a>Autres moyens de prévenir et de protéger contre les cybercriminalités dans Microsoft 365

Pour plus d’informations sur la façon dont vous pouvez renforcer votre organisation contre le hameçonnage, le courrier indésirable, les violations de données et d’autres menaces, consultez [les meilleures pratiques pour sécuriser Microsoft 365 pour les plans d’entreprise](../../admin/security-and-compliance/secure-your-business-data.md).
