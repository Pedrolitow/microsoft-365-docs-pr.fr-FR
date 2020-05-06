---
title: Définir une date d’expiration pour les e-mails chiffrés par le chiffrement avancé de messages Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/8/2019
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Avec les fonctionnalités de chiffrement de messages avancé Office 365 sur Office 365 message Encryption (OME), vous pouvez étendre votre sécurité de messagerie en définissant une date d’expiration pour les e-mails via un modèle personnalisé.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f555e707cb377033c3bf643785e18b9203be0560
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44036057"
---
# <a name="set-an-expiration-date-for-email-encrypted-by-office-365-advanced-message-encryption"></a>Définir une date d’expiration pour les e-mails chiffrés par le chiffrement avancé de messages Office 365

Le chiffrement de messages avancé Office 365 est inclus dans [microsoft 365 entreprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (tarification du personnel pour les personnes travaillant), Office 365 entreprise E5 (tarification du personnel pour les personnes à but lucratif) et Office 365 éducation a5. Si votre organisation dispose d’un abonnement qui n’inclut pas le chiffrement de messages avancé Office 365, vous pouvez l’acheter avec le complément Microsoft 365 E5 Compliance SKU pour Microsoft 365 E3, Microsoft 365 E3 (tarification du personnel pour les salariés) ou le complément Office 365 Advanced Compliance SKU pour Microsoft 365 E3, Microsoft 365 E3 (tarification du personnel pour les salariés) ou Office 365 SKU.

Vous pouvez utiliser l’expiration des messages envoyés par vos utilisateurs à des destinataires externes qui utilisent le portail OME pour accéder à des e-mails chiffrés. Vous obligez les destinataires à utiliser le portail OME pour afficher et répondre à des messages électroniques chiffrés envoyés par votre organisation à l’aide d’un modèle personnalisé qui spécifie une date d’expiration dans Windows PowerShell.

En tant qu’administrateur général d’Office 365, lorsque vous appliquez la marque de votre entreprise pour personnaliser l’apparence des messages électroniques de votre organisation, vous pouvez également spécifier une expiration pour ces messages électroniques. Avec le chiffrement de messages avancé Office 365, vous pouvez créer plusieurs modèles pour les messages électroniques chiffrés provenant de votre organisation. À l’aide d’un modèle, vous pouvez contrôler la durée pendant laquelle les destinataires ont accès aux messages envoyés par vos utilisateurs.

Lorsqu’un utilisateur final reçoit un message dont la date d’expiration est définie, l’utilisateur voit la date d’expiration dans le message du wrapper. Si un utilisateur tente d’ouvrir un message expiré, une erreur s’affiche dans le portail OME.

Vous pouvez uniquement définir des dates d’expiration pour les messages électroniques adressés à des destinataires externes.

Avec le chiffrement de messages avancé Office 365, chaque fois que vous appliquez une personnalisation personnalisée, Office 365 applique le wrapper aux messages électroniques qui correspondent à la règle de flux de messagerie à laquelle vous appliquez le modèle. De plus, vous ne pouvez utiliser l’expiration que si vous utilisez une personnalisation personnalisée.

## <a name="create-a-custom-branding-template-to-force-mail-expiration-by-using-powershell"></a>Créer un modèle de personnalisation pour forcer l’expiration du courrier à l’aide de PowerShell

1. [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) avec un compte disposant d’autorisations d’administrateur globales au sein de votre organisation.

2. Exécutez la cmdlet New-OMEConfiguration.

     ```powershell
     New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
     ```

Où :

- `Identity`est le nom du modèle personnalisé.

- `ExternalMailExpiryInDays`identifie le nombre de jours pendant lesquels les destinataires peuvent conserver leur courrier avant d’expirer. Vous pouvez utiliser n’importe quelle valeur comprise entre 1 et 730 jours.

## <a name="more-information-about-office-365-advanced-message-encryption"></a>Plus d’informations sur le chiffrement de messages avancé Office 365

- [Chiffrement de messages avancé Office 365](ome-advanced-message-encryption.md)

- [Révoquer les e-mails chiffrés par le chiffrement de messages Office 365](revoke-ome-encrypted-mail.md)

- [Description du service de conformité et de stratégie de message](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)
