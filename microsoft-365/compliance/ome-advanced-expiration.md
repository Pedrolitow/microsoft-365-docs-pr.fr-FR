---
title: Définir une date d’expiration pour les e-mails chiffrés par le chiffrement avancé de messages Microsoft Purview
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/8/2019
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Utilisez Microsoft Purview Advanced Message Encryption pour étendre votre sécurité de messagerie en définissant une date d’expiration sur les e-mails via un modèle personnalisé de marque.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 78855ae8906367293b69406ba74246619b5af465
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015559"
---
# <a name="set-an-expiration-date-for-email-encrypted-by-microsoft-purview-advanced-message-encryption"></a>Définir une date d’expiration pour les e-mails chiffrés par le chiffrement avancé de messages Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Advanced Message Encryption est inclus dans [Microsoft 365 Entreprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (tarification du personnel à but non lucratif), Office 365 Entreprise E5 (prix du personnel à but non lucratif) et Office 365 Éducation A5. Microsoft 365 E5 Conformité module complémentaire SKU pour Microsoft 365 E3, Microsoft 365 E3 (Prix du personnel à but non lucratif) ou le module complémentaire de référence SKU Conformité avancée Office 365 pour Microsoft 365 E3, Microsoft 365 E3 (prix du personnel à but non lucratif) ou Office 365 références SKU.

Si votre organisation dispose d’un abonnement qui n’inclut pas Microsoft Purview Advanced Message Encryption, vous pouvez l’acheter avec le module complémentaire de référence SKU Microsoft 365 E5 Conformité pour Microsoft 365 E3, Microsoft 365 E3 (prix du personnel à but non lucratif) ou le Conformité avancée Office 365 module complémentaire SKU pour Microsoft 365 E3, Microsoft 365 E3 (Prix du personnel à but non lucratif) ou Office 365 références SKU.

Vous pouvez utiliser l’expiration des messages sur les e-mails que vos utilisateurs envoient aux destinataires externes qui utilisent le portail OME pour accéder aux e-mails chiffrés. Vous forcez les destinataires à utiliser le portail OME pour afficher et répondre aux e-mails chiffrés envoyés par votre organisation à l’aide d’un modèle personnalisé de marque qui spécifie une date d’expiration dans PowerShell.

En tant qu’administrateur général Office 365, lorsque vous appliquez la marque de votre entreprise pour personnaliser l’apparence des messages électroniques de votre organisation, vous pouvez également spécifier une expiration pour ces messages électroniques. Avec Microsoft Purview Advanced Message Encryption, vous pouvez créer plusieurs modèles pour les e-mails chiffrés provenant de votre organisation. À l’aide d’un modèle, vous pouvez contrôler la durée pendant laquelle les destinataires ont accès au courrier envoyé par vos utilisateurs.

Lorsqu’un utilisateur final reçoit un courrier dont la date d’expiration est définie, il voit la date d’expiration dans l’e-mail du wrapper. Si un utilisateur tente d’ouvrir un courrier expiré, une erreur s’affiche dans le portail OME.

Vous pouvez uniquement définir des dates d’expiration pour les e-mails envoyés à des destinataires externes.

Avec Microsoft Purview Advanced Message Encryption, chaque fois que vous appliquez une personnalisation, le Office 365 applique le wrapper à l’e-mail qui correspond à la règle de flux de messagerie à laquelle vous appliquez le modèle. En outre, vous ne pouvez utiliser l’expiration que si vous utilisez la personnalisation.

## <a name="create-a-custom-branding-template-to-force-mail-expiration-by-using-powershell"></a>Créer un modèle de personnalisation pour forcer l’expiration du courrier à l’aide de PowerShell

1. [Connecter de Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) avec un compte disposant d’autorisations d’administrateur général dans votre organisation.

2. Exécutez l’applet de commande New-OMEConfiguration.

    ```powershell
    New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
    ```

Où :

- `Identity` est le nom du modèle personnalisé.

- `ExternalMailExpiryInDays` identifie le nombre de jours pendant lesquels les destinataires peuvent conserver le courrier avant son expiration. Vous pouvez utiliser n’importe quelle valeur comprise entre 1 et 730 jours.

## <a name="more-information-about-microsoft-purview-advanced-message-encryption"></a>Plus d’informations sur le chiffrement avancé des messages Microsoft Purview

- [Chiffrement avancé des messages](ome-advanced-message-encryption.md)

- [Exemple de scénario : révoquer les e-mails chiffrés avec le chiffrement avancé des messages Microsoft Purview](revoke-ome-encrypted-mail.md)

- [Description de la stratégie de message et du service de conformité](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)
