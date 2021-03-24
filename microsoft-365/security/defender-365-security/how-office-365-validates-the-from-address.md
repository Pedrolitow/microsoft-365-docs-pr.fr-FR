---
title: Comment EOP valide l’adresse De pour empêcher le hameçonnage
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
search.appverid:
- OWC150
- MET150
ms.assetid: eef8408b-54d3-4d7d-9cf7-ad2af10b2e0e
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent en savoir plus sur les types d’adresses de messagerie acceptées ou rejetées par Exchange Online Protection (EOP) et Outlook.com pour empêcher le hameçonnage.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5a02313bf8c36fe0be91340e421c69a8dc5c0842
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51063358"
---
# <a name="how-eop-validates-the-from-address-to-prevent-phishing"></a>Comment EOP valide l’adresse De pour empêcher le hameçonnage

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les attaques par hameçonnage sont une menace constante pour toute organisation de messagerie. Outre l’utilisation d’adresses e-mail d’expéditeur falsifiées [(falsifiées),](anti-spoofing-protection.md)les personnes malveillantes utilisent souvent des valeurs dans l’adresse De qui ne respectent pas les normes Internet. Pour éviter ce type d’hameçonnage, Exchange Online Protection (EOP) et Outlook.com requièrent désormais que les messages entrants incluent une adresse de provenance conforme À la norme RFC, comme décrit dans cet article. Cette application a été activée en novembre 2017.

**Remarques** :

- Si vous recevez régulièrement des messages électroniques provenant d’organisations dont les adresses ont été mal renseignées, comme décrit dans cet article, encouragez ces organisations à mettre à jour leurs serveurs de messagerie pour se conformer aux normes de sécurité modernes.

- Le champ Expéditeur associé (utilisé par les listes d’envoi de la part de et de publipostage) n’est pas affecté par ces exigences. Pour plus d’informations, consultez le billet de blog suivant : Que voulons-nous dire lorsque nous faisons référence à l'« expéditeur » [d’un e-mail ?](/archive/blogs/tzink/what-do-we-mean-when-we-refer-to-the-sender-of-an-email)

## <a name="an-overview-of-email-message-standards"></a>Vue d’ensemble des normes de message électronique

Un message électronique SMTP standard est constitué d’une *enveloppe de message* et d’un contenu de message. L’enveloppe de message contient les informations requises pour transmettre et remettre le message entre des serveurs SMTP. Le contenu du message comporte les champs d’en-tête de message (collectivement appelés l’*en-tête de message*) et le corps du message. L’enveloppe de message est décrite dans [la RFC 5321](https://tools.ietf.org/html/rfc5321)et l’en-tête du message est décrit dans [la RFC 5322](https://tools.ietf.org/html/rfc5322). Les destinataires ne voient jamais l’enveloppe de message réelle, car elle est générée par le processus de transmission du message et ne fait pas réellement partie du message.

- L’adresse (également appelée adresse MAIL FROM, expéditeur P1 ou expéditeur d’enveloppe) est l’adresse de messagerie utilisée dans la `5321.MailFrom` transmission SMTP du message.  Cette adresse de messagerie est généralement enregistrée dans le champ **d’en-tête Return-Path** dans l’en-tête du message (bien qu’il soit possible pour l’expéditeur de désigner une autre adresse de messagerie **Return-Path).**

- L’adresse e-mail (également appelée adresse de provenance ou expéditeur P2) est l’adresse de messagerie dans le champ d’en-tête De et l’adresse de messagerie de l’expéditeur qui s’affiche dans les clients de `5322.From` messagerie.  L’adresse de provenance est au centre des exigences de cet article.

L’adresse De est définie en détail sur plusieurs RFC (par exemple, les sections RFC 5322 3.2.3, 3.4 et 3.4.1 et [RFC 3696](https://tools.ietf.org/html/rfc3696)). Il existe de nombreuses variantes sur l’adressan et ce qui est considéré comme valide ou non valide. Pour des raisons de simplicité, nous vous recommandons le format et les définitions suivants :

`From: "Display Name" <EmailAddress>`

- **Nom complet**: expression facultative qui décrit le propriétaire de l’adresse e-mail.

  - Nous vous recommandons de toujours entourer le nom complet de guillemets doubles (« ) comme illustré. Si le nom complet contient  une virgule, vous devez mettre la chaîne entre guillemets doubles par RFC 5322.
  - Si l’adresse De comprend un nom d’affichage, la valeur EmailAddress doit être entre crochets (< >) comme illustré.
  - Microsoft recommande vivement d’insérer un espace entre le nom complet et l’adresse e-mail.

- **EmailAddress**: une adresse de messagerie utilise le format `local-part@domain` :

  - **partie locale :** chaîne qui identifie la boîte aux lettres associée à l’adresse. Cette valeur est unique dans le domaine. Souvent, le nom d’utilisateur ou le GUID du propriétaire de la boîte aux lettres est utilisé.
  - **domaine**: nom de domaine complet (FQDN) du serveur de messagerie qui héberge la boîte aux lettres identifiée par la partie locale de l’adresse de messagerie.

  Voici quelques considérations supplémentaires pour la valeur EmailAddress :

  - Une seule adresse de messagerie.
  - Nous vous recommandons de ne pas séparer les crochets pointants par des espaces.
  - N’incluez pas de texte supplémentaire après l’adresse e-mail.

## <a name="examples-of-valid-and-invalid-from-addresses"></a>Exemples d’adresses De valides et non valides

Les adresses de messagerie De suivantes sont valides :

- `From: sender@contoso.com`

- `From: <sender@contoso.com>`

- `From: < sender@contoso.com >` (Non recommandé, car il existe des espaces entre les crochets et l’adresse e-mail.)

- `From: "Sender, Example" <sender.example@contoso.com>`

- `From: "Microsoft 365" <sender@contoso.com>`

- `From: Microsoft 365 <sender@contoso.com>` (Non recommandé, car le nom complet n’est pas entouré de guillemets doubles.)

Les adresses de messagerie De suivantes ne sont pas valides :

- **Adresse De non :** certains messages automatisés n’incluent pas d’adresse de provenance. Dans le passé, lorsque Microsoft 365 ou Outlook.com recevait un message sans adresse de provenance, le service ajoutait l’adresse De : par défaut suivante pour rendre le message livrable :

  `From: <>`

  À présent, les messages dont l’adresse de provenance est vide ne sont plus acceptés.

- `From: Microsoft 365 sender@contoso.com` (Le nom complet est présent, mais l’adresse e-mail n’est pas entre crochets.)

- `From: "Microsoft 365" <sender@contoso.com> (Sent by a process)` (Texte après l’adresse e-mail.)

- `From: Sender, Example <sender.example@contoso.com>` (Le nom complet contient une virgule, mais n’est pas entre guillemets doubles.)

- `From: "Microsoft 365 <sender@contoso.com>"` (La valeur entière est incorrectement entourée de guillemets doubles.)

- `From: "Microsoft 365 <sender@contoso.com>" sender@contoso.com` (Le nom complet est présent, mais l’adresse e-mail n’est pas entre crochets.)

- `From: Microsoft 365<sender@contoso.com>` (Aucun espace entre le nom d’affichage et le crochet angle gauche.)

- `From: "Microsoft 365"<sender@contoso.com>` (Aucun espace entre les guillemets fermants et le crochet angle gauche.)

## <a name="suppress-auto-replies-to-your-custom-domain"></a>Supprimer les réponses automatiques à votre domaine personnalisé

Vous ne pouvez pas utiliser la valeur pour `From: <>` supprimer les réponses automatiques. Au lieu de cela, vous devez configurer un enregistrement MX null pour votre domaine personnalisé. Les réponses automatiques (et toutes les réponses) sont supprimées naturellement, car il n’existe aucune adresse publiée à qui le serveur répondant peut envoyer des messages.

- Choisissez un domaine de messagerie qui ne peut pas recevoir de courrier électronique. Par exemple, si votre domaine principal est contoso.com, vous pouvez choisir noreply.contoso.com.

- L’enregistrement MX null pour ce domaine se compose d’un point unique.

Par exemple :

```text
noreply.contoso.com IN MX .
```

Pour plus d’informations sur la configuration des enregistrements MX, voir Créer des enregistrements DNS chez un fournisseur d’hébergement [DNS pour Microsoft 365.](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)

Pour plus d’informations sur la publication d’un MX null, voir [RFC 7505](https://tools.ietf.org/html/rfc7505).

## <a name="override-from-address-enforcement"></a>Remplacer l’application de l’adresse

Pour contourner les exigences d’adresse De pour le courrier entrant, vous pouvez utiliser la liste d’adresses IP (filtrage des connexions) ou les règles de flux de messagerie (également appelées règles de transport) comme décrit dans Créer des listes d’expéditeurs sûrs dans [Microsoft 365.](create-safe-sender-lists-in-office-365.md)

Vous ne pouvez pas remplacer les exigences d’adresse de provenance pour les messages sortants que vous envoyez à partir de Microsoft 365. En outre, Outlook.com n’autorise pas les remplacements de quelque type que ce soit, même par le biais de la prise en charge.

## <a name="other-ways-to-prevent-and-protect-against-cybercrimes-in-microsoft-365"></a>Autres méthodes de prévention et de protection contre les cybercriminels dans Microsoft 365

Pour plus d’informations sur la façon de renforcer votre organisation contre le hameçonnage, le courrier indésirable, les violations de données et d’autres menaces, voir les 10 principales façons de sécuriser les [plans Microsoft 365](../../admin/security-and-compliance/secure-your-business-data.md)pour les entreprises.