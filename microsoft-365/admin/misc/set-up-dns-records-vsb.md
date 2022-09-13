---
title: Connecter votre domaine à Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- highpri
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
search.appverid:
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Apprenez à vérifier votre domaine et à créer des enregistrements DNS avec Microsoft 365.
ms.custom:
- VSBFY23
- AdminSurgePortfolio
ms.openlocfilehash: c2d2787e8d7f035cbefefe16b4defcdc310e65c7
ms.sourcegitcommit: 37e137535c4f70702afe1a5eeaa899c75ee02cfd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2022
ms.locfileid: "67661868"
---
# <a name="connect-your-domain-to-microsoft-365"></a>Connecter votre domaine à Microsoft 365

> [!NOTE]
> Si vous n’ajoutez pas de domaine, les membres de votre organisation utiliseront le domaine onmicrosoft.com pour leur adresse de messagerie jusqu’à ce que vous le fassiez. Il est important d’ajouter votre domaine avant d’ajouter des utilisateurs, de sorte que vous n’ayez pas à les reconfigurer.

[Consultez la FAQ dédiée aux domaines](../setup/domains-faq.yml) si vous ne trouvez pas ci-dessous ce que vous recherchez .

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

Vous obtiendrez les informations relatives à l’enregistrement MX à partir de l’Assistant Configuration du domaine du centre d’administration.

Sur le site Web de votre fournisseur d’hébergement, créez un nouvel enregistrement MX.
Vérifiez que les champs sont définis par les valeurs suivantes :

- Type d’enregistrement : `MX`
- Priorité : sélectionnez la valeur la plus élevée disponible, généralement `0`.
- Nom de l’hôte : `@`
- Adresse de pointage : copiez la valeur à partir du centre d’administration et collez-la ici.
- TTL : `3600` (ou votre fournisseur par défaut)

Sauvegardez l’enregistrement et supprimez tous les autres enregistrements MX.

## <a name="add-a-cname-record-to-connect-users-to-their-mailboxes"></a>Ajouter un enregistrement CNAME pour connecter des utilisateurs à leurs boîtes aux lettres

Vous obtiendrez les informations relatives aux enregistrements CNAME à partir de l’Assistant Configuration du domaine du centre d’administration.

Sur le site web de votre fournisseur d’hébergement, ajoutez l’enregistrement CNAME suivant. Dans le nouvel enregistrement, vérifiez que chacun des champs sont définis par les valeurs suivantes :

- Type d’enregistrement : `CNAME (Alias)`
- Hôte : collez les valeurs que vous copiez à partir du centre d’administration ici.
- Adresse de pointage : copiez la valeur à partir du centre d’administration et collez-la ici.
- TTL : `3600` (ou votre fournisseur par défaut)

## <a name="add-a-txt-record-to-help-prevent-spam"></a>Ajouter un enregistrement TXT afin d'éviter le courrier indésirable

**Avant de commencer :** Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft 365. Ajoutez plutôt les valeurs Microsoft 365 requises à l’enregistrement actuel sur le site Web de votre fournisseur d’hébergement de manière à n’avoir qu’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs.

Sur le site web de votre fournisseur d’hébergement, modifiez l'enregistrement SPF existant ou créez un enregistrement SPF.
Vérifiez que les champs sont définis par les valeurs suivantes :

- Type d’enregistrement : `TXT (Text)`
- Hôte : `@`
- Valeur TXT :`v=spf1 include:spf.protection.outlook.com -all`
- TTL : `3600` (ou votre fournisseur par défaut)

Enregistrez l'enregistrement.

Validez votre enregistrement SPF en utilisant l'un des [Outils de validation SPF](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain) suivants

SPF est conçu pour lutter contre l’usurpation d’adresse, mais il existe des techniques d’usurpation d’adresse contre lesquelles SPF ne peut rien faire. Pour vous protéger contre ces techniques, une fois que vous avez configuré votre SPF, vous devez également configurer DKIM et DMARC pour Microsoft 365.

Pour commencer, consultez la rubrique [Utilisation du DKIM pour valider les e-mails sortants envoyés à partir de votre domaine dans Microsoft 365](../../security/office-365-security/use-dkim-to-validate-outbound-email.md) et [Utilisation du DMARC pour valider les e-mails dans Microsoft 365](../../security/office-365-security/use-dmarc-to-validate-email.md).

Pour finir, revenez à l’Assistant Configuration du domaine du centre d’administration pour terminer votre installation.
