---
title: Définir une date d’expiration pour les e-mails chiffrés par le chiffrement avancé de messages Office 365
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
description: Utilisez Chiffrement avancé de messages Office 365 pour étendre la sécurité de votre messagerie en fixant une date d’expiration sur les e-mails via un modèle personnalisé.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f936ffa62f31e47f51fc1bcb2765195b0ea809af
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50927784"
---
# <a name="set-an-expiration-date-for-email-encrypted-by-office-365-advanced-message-encryption"></a>Définir une date d’expiration pour les e-mails chiffrés par le chiffrement avancé de messages Office 365

Chiffrement avancé de messages Office 365 est inclus dans [Microsoft 365 Entreprise E5,](https://www.microsoft.com/microsoft-365/enterprise/home)Office 365 E5, Microsoft 365 E5 (tarifs du personnel pour les associations), Office 365 Entreprise E5 (prix du personnel pour les associations) et Office 365 Éducation A5. Si votre organisation dispose d’un abonnement qui n’inclut pas de Chiffrement avancé de messages Office 365, vous pouvez l’acheter avec le module Microsoft 365 E5 Conformité SKU pour Microsoft 365 E3, Microsoft 365 E3 (prix du personnel à but non lucratif) ou le module Conformité avancée Office 365 SKU pour les SKU Microsoft 365 E3, Microsoft 365 E3 (prix du personnel à but non lucratif) ou Office 365 SKU.

Vous pouvez utiliser l’expiration des messages sur les e-mails que vos utilisateurs envoient à des destinataires externes qui utilisent le portail OME pour accéder aux e-mails chiffrés. Vous forcez les destinataires à utiliser le portail OME pour afficher et répondre aux messages électroniques chiffrés envoyés par votre organisation à l’aide d’un modèle personnalisé personnalisé qui spécifie une date d’expiration dans Windows PowerShell.

En tant qu’administrateur Office 365 général, lorsque vous appliquez la marque de votre entreprise pour personnaliser l’apparence des messages électroniques de votre organisation, vous pouvez également spécifier une expiration pour ces messages électroniques. Avec Chiffrement avancé de messages Office 365, vous pouvez créer plusieurs modèles pour les e-mails chiffrés provenant de votre organisation. À l’aide d’un modèle, vous pouvez contrôler la durée pendant combien de temps les destinataires ont accès aux messages envoyés par vos utilisateurs.

Lorsqu’un utilisateur final reçoit un message dont la date d’expiration est définie, il voit la date d’expiration dans le message électronique de wrapper. Si un utilisateur tente d’ouvrir un message expiré, une erreur s’affiche dans le portail OME.

Vous ne pouvez définir des dates d’expiration que pour les messages électroniques envoyés à des destinataires externes.

Avec Chiffrement avancé de messages Office 365, chaque fois que vous appliquez une personnalisation, le Office 365 applique le wrapper au courrier électronique qui correspond à la règle de flux de messagerie à laquelle vous appliquez le modèle. En outre, vous ne pouvez utiliser l’expiration que si vous utilisez une personnalisation.

## <a name="create-a-custom-branding-template-to-force-mail-expiration-by-using-powershell"></a>Créer un modèle de personnalisation pour forcer l’expiration du courrier à l’aide de PowerShell

1. [Connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) avec un compte qui dispose d’autorisations d’administrateur général dans votre organisation.

2. Exécutez lNew-OMEConfiguration cmdlet.

    ```powershell
    New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
    ```

Où :

- `Identity` est le nom du modèle personnalisé.

- `ExternalMailExpiryInDays` identifie le nombre de jours pendant les jours pendantaux pendantaux pendant les destinataires pour conserver le courrier avant son expiration. Vous pouvez utiliser n’importe quelle valeur entre 1 et 730 jours.

## <a name="more-information-about-office-365-advanced-message-encryption"></a>Plus d’informations sur Chiffrement avancé de messages Office 365

- [Chiffrement de messages avancé Office 365](ome-advanced-message-encryption.md)

- [Révoquer les e-mails chiffrés par le chiffrement de messages Office 365](revoke-ome-encrypted-mail.md)

- [Description du service de conformité et de stratégie de message](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)