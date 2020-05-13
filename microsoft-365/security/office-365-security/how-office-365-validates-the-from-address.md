---
title: Comment EOP valide l’adresse de pour empêcher le hameçonnage
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
- OWC150
- MET150
ms.assetid: eef8408b-54d3-4d7d-9cf7-ad2af10b2e0e
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent en savoir plus sur les types d’adresses de messagerie qui sont acceptés ou refusés par Exchange Online Protection (EOP) et Outlook.com afin d’empêcher le hameçonnage.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f16bb9b0af1ca5481437ef253c6d36dd519ff9e2
ms.sourcegitcommit: 93c0088d272cd45f1632a1dcaf04159f234abccd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209450"
---
# <a name="how-eop-validates-the-from-address-to-prevent-phishing"></a>Comment EOP valide l’adresse de pour empêcher le hameçonnage

Les attaques par hameçonnage représentent une menace constante pour toute organisation de messagerie. En plus des [adresses de messagerie d’expéditeur usurpées (falsifiées)](anti-spoofing-protection.md), les agresseurs utilisent souvent des valeurs de l’adresse de provenance qui enfreignent les normes Internet. Pour éviter ce type de hameçonnage, Exchange Online Protection (EOP) et Outlook.com requièrent désormais que les messages entrants incluent une adresse d’adresse conforme à la RFC, comme décrit dans cette rubrique. Cette mise en œuvre a été activée en novembre 2017.

**Remarques** :

- Si vous recevez régulièrement du courrier électronique d’organisations qui ont des adresses de provenance incorrectes, comme décrit dans cette rubrique, encouragez ces organisations à mettre à jour leurs serveurs de messagerie afin de se conformer aux normes de sécurité modernes.

- Le champ expéditeur associé (utilisé par envoyer de la part de et des listes de publipostage) n’est pas affecté par ces exigences. Pour plus d’informations, consultez le billet de blog suivant : qu’est- [ce que nous voulons dire lorsque nous faisons référence à l’expéditeur d’un message électronique ?](https://blogs.msdn.microsoft.com/tzink/2017/06/22/what-do-we-mean-when-we-refer-to-the-sender-of-an-email/).

## <a name="an-overview-of-email-message-standards"></a>Vue d’ensemble des standards des messages électroniques

Un message électronique SMTP standard est constitué d’une *enveloppe de message* et d’un contenu de message. L’enveloppe de message contient les informations requises pour la transmission et la remise du message entre les serveurs SMTP. Le contenu du message comporte les champs d’en-tête de message (collectivement appelés l’*en-tête de message*) et le corps du message. L’enveloppe de message est décrite dans la [norme rfc 5321](https://tools.ietf.org/html/rfc5321)et l’en-tête de message est décrit dans la [spécification RFC 5322](https://tools.ietf.org/html/rfc5322). Les destinataires ne voient jamais l’enveloppe de message réelle, car elle est générée par le processus de transmission des messages, et elle ne fait pas partie du message.

- L' `5321.MailFrom` adresse (également appelée adresse **de messagerie de** l’expéditeur, expéditeur P1 ou expéditeur de l’enveloppe) est l’adresse de messagerie utilisée dans la transmission SMTP du message. Cette adresse de messagerie est généralement enregistrée dans le champ d’en-tête de **retour** de l’en-tête du message (bien que l’expéditeur ait la possibilité de désigner une autre adresse de messagerie de **chemin d’accès** ).

- Le `5322.From` (également appelé l’adresse de l’expéditeur ou l’expéditeur P2) est l’adresse de messagerie dans le champ de l’en-tête **de** , et est l’adresse de messagerie de l’expéditeur affichée dans les clients de messagerie. L’adresse de provenance est l’élément de la configuration requise dans cette rubrique.

L’adresse de l’adresse est définie en détail dans plusieurs RFC (par exemple, les sections de la norme RFC 5322 3.2.3, 3,4 et 3.4.1, et la [norme rfc 3696](https://tools.ietf.org/html/rfc3696)). Il existe de nombreuses variantes de l’adressage et ce qui est considéré comme valide ou non valide. Pour simplifier, nous vous recommandons de suivre le format et les définitions suivants :

`From: "Display Name" <EmailAddress>`

- **Nom d’affichage**: expression facultative qui décrit le propriétaire de l’adresse de messagerie.

  - Nous vous recommandons de toujours placer le nom d’affichage entre guillemets doubles ("), comme illustré ci-dessous. Si le nom complet contient une virgule, vous _devez_ placer la chaîne entre guillemets doubles par RFC 5322.
  - Si l’adresse de l’adresse contient un nom d’affichage, la valeur EmailAddress doit être placée entre chevrons (< >) comme illustré.
  - Microsoft recommande vivement d’insérer un espace entre le nom d’affichage et l’adresse de messagerie.

- **EmailAddress**: une adresse de messagerie utilise le format `local-part@domain` suivant :

  - **local-part**: une chaîne qui identifie la boîte aux lettres associée à l’adresse. Cette valeur est unique au sein du domaine. Souvent, le nom d’utilisateur ou le GUID du propriétaire de la boîte aux lettres est utilisé.
  - **domaine**: nom de domaine complet (FQDN) du serveur de messagerie qui héberge la boîte aux lettres identifiée par la partie locale de l’adresse de messagerie.

  Voici quelques considérations supplémentaires pour la valeur EmailAddress :

  - Une seule adresse de messagerie.
  - Nous vous recommandons de ne pas séparer les chevrons avec des espaces.
  - N’incluez pas de texte supplémentaire après l’adresse de messagerie.

## <a name="examples-of-valid-and-invalid-from-addresses"></a>Exemples d’adresses valides et non valides

Les adresses de messagerie suivantes sont valides :

- `From: sender@contoso.com`

- `From: <sender@contoso.com>`

- `From: < sender@contoso.com >`(Non recommandé, car il y a des espaces entre les chevrons et l’adresse de messagerie.)

- `From: "Sender, Example" <sender.example@contoso.com>`

- `From: "Microsoft 365" <sender@contoso.com>`

- `From: Microsoft 365 <sender@contoso.com>`(Non recommandé, car le nom d’affichage n’est pas entouré de guillemets doubles.)

Les adresses de messagerie suivantes ne sont pas valides :

- **Non de l’adresse**: certains messages automatisés n’incluent pas d’adresse de provenance. Dans le passé, lorsque Microsoft 365 ou Outlook.com a reçu un message sans adresse de provenance, le service a ajouté la valeur par défaut suivante de : adresse pour que le message soit remis :

  `From: <>`

  Désormais, les messages dont l’adresse est vide à partir de ne sont plus acceptés.

- `From: Microsoft 365 sender@contoso.com`(Le nom complet est présent, mais l’adresse de messagerie n’est pas entourée de crochets pointus.)

- `From: "Microsoft 365" <sender@contoso.com> (Sent by a process)`(Texte après l’adresse de messagerie.)

- `From: Sender, Example <sender.example@contoso.com>`(Le nom complet contient une virgule, mais n’est pas entouré de guillemets doubles.)

- `From: "Microsoft 365 <sender@contoso.com>"`(La valeur entière est placée de manière incorrecte entre guillemets doubles.)

- `From: "Microsoft 365 <sender@contoso.com>" sender@contoso.com`(Le nom complet est présent, mais l’adresse de messagerie n’est pas entourée de crochets pointus.)

- `From: Microsoft 365<sender@contoso.com>`(Pas d’espace entre le nom d’affichage et le crochet pointu gauche.)

- `From: "Microsoft 365"<sender@contoso.com>`(Aucun espace entre les guillemets doubles de fermeture et le crochet pointu gauche.)

## <a name="suppress-auto-replies-to-your-custom-domain"></a>Supprimer les réponses automatiques à votre domaine personnalisé

Vous ne pouvez pas utiliser la valeur `From: <>` pour supprimer les réponses automatiques. Au lieu de cela, vous devez configurer un enregistrement MX null pour votre domaine personnalisé. Les réponses automatiques (et toutes les réponses) sont naturellement supprimées, car il n’existe aucune adresse publiée à laquelle le serveur de réponse peut envoyer des messages.

- Choisissez un domaine de messagerie qui ne peut pas recevoir de courrier électronique. Par exemple, si votre domaine principal est contoso.com, vous pouvez choisir noreply.contoso.com.

- L’enregistrement MX null de ce domaine se compose d’un seul point.

Par exemple :

```text
noreply.contoso.com IN MX .
```

Pour plus d’informations sur la configuration des enregistrements MX, consultez la rubrique [créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS pour Microsoft 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

Pour plus d’informations sur la publication d’une valeur null MX, voir [RFC 7505](https://tools.ietf.org/html/rfc7505).

## <a name="override-from-address-enforcement"></a>Remplacer l’application de l’adresse

Pour ignorer l’adresse requise pour le courrier électronique entrant, vous pouvez utiliser la liste d’adresses IP autorisées (filtrage des connexions) ou les règles de flux de messagerie (également appelées règles de transport), comme décrit dans [Create Safe sender Lists in Microsoft 365](create-safe-sender-lists-in-office-365.md).

Vous ne pouvez pas remplacer l’adresse requise pour le courrier électronique sortant que vous envoyez à partir de Microsoft 365. De plus, Outlook.com n’autorisera pas les remplacements, même via la prise en charge.

## <a name="other-ways-to-prevent-and-protect-against-cybercrimes-in-microsoft-365"></a>Autres moyens de prévenir et de protéger contre les cybercriminels dans Microsoft 365

Pour plus d’informations sur la façon dont vous pouvez renforcer votre organisation contre le hameçonnage, le courrier indésirable, les violations de données et d’autres menaces, consultez les [10 meilleures façons de sécuriser les plans Microsoft 365 pour les entreprises](../../admin/security-and-compliance/secure-your-business-data.md).
