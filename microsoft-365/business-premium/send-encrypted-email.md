---
title: Envoyer un message électronique chiffré
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
ms.date: 9/20/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
ms.assetid: 496e690b-b75d-4ff5-bf34-cc32905d0364
description: Découvrez comment envoyer des e-mails chiffrés à l’aide de Outlook.
ms.openlocfilehash: 9cf39d3147b5ef7a099a06737316ee20e6154775
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946899"
---
# <a name="encrypt-or-label-your-sensitive-email"></a>Chiffrer ou étiqueter votre courrier électronique sensible

Vos données et vos informations de campagne sont importantes et souvent confidentielles. Protégez ces informations sensibles à l’aide d’étiquettes de chiffrement et de confidentialité afin que vous et vos destinataires de courrier traitez les informations avec la sensibilité nécessaire.

## <a name="best-practices"></a>Meilleures pratiques

Avant d’envoyer un e-mail contenant des informations confidentielles ou sensibles, activez :

- **Cryptage:** Vous pouvez chiffrer votre courrier électronique pour protéger la confidentialité des informations contenues dans l’e-mail. Lorsque vous chiffrez un e-mail, il est converti à partir d’un texte brut lisible en texte codé. Seul le destinataire disposant de la clé privée qui correspond à la clé publique utilisée pour chiffrer le message peut déchiffrer le message à lire. Toutefois, tout destinataire sans clé privée correspondante voit du texte indéchiffrable. Votre administrateur peut définir des règles pour chiffrer automatiquement les messages qui répondent à certains critères. Par exemple, votre administrateur peut créer une règle qui chiffre tous les messages envoyés en dehors de votre organisation ou tous les messages qui mentionnent des mots ou des expressions spécifiques. Toutes les règles de chiffrement sont appliquées automatiquement.
- **Étiquettes de confidentialité :** Votre campagne peut également configurer des étiquettes de confidentialité que vous pouvez appliquer à vos fichiers et e-mail pour les maintenir conformes aux stratégies de protection des informations de votre campagne. Lorsque vous définissez une étiquette, l’étiquette persiste avec votre e-mail, même lorsqu’il est envoyé, par exemple en apparaissant sous forme d’en-tête dans votre message.

![Diagramme d’un e-mail avec des légendes pour les étiquettes et le chiffrement.](../media/m365-campaign-email-encrypt.png)

## <a name="set-it-up"></a>Configuration

Si vous souhaitez chiffrer un message qui ne répond pas à une règle prédéfinie ou si votre administrateur n’a pas configuré de règles, vous pouvez appliquer différentes règles de chiffrement avant d’envoyer le message. Pour envoyer un message chiffré à partir de Outlook 2013 ou 2016, ou Outlook 2016 pour Mac, sélectionnez **Options > Autorisations**, puis sélectionnez l’option de protection dont vous avez besoin. Vous pouvez également envoyer un message chiffré en sélectionnant le bouton **Protéger** dans Outlook sur le web. Pour plus d’informations, consultez [Envoyer, afficher et répondre à des messages chiffrés dans Outlook pour PC](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="admin-settings"></a>Paramètres d’administration

Vous pouvez en savoir plus sur la configuration du chiffrement des [e-mails à l’adresse e-mail de chiffrement dans Microsoft 365](../compliance/email-encryption.md).

### <a name="automatically-encrypt-email-messages"></a>Chiffrer automatiquement les messages électroniques

Les administrateurs peuvent créer des règles de flux de courrier pour protéger automatiquement les messages électroniques envoyés et reçus de votre campagne. Configurez des règles pour chiffrer les messages électroniques sortants et supprimer le chiffrement des messages chiffrés provenant de votre organisation ou des réponses aux messages chiffrés envoyés par votre organisation.

Vous créez des règles de flux de courrier pour chiffrer les messages électroniques avec Microsoft Purview Message Encryption. Définissez des règles de flux de messagerie pour déclencher le chiffrement des messages à l’aide du <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange (EAC).</a>

1. Dans un navigateur web, à l’aide d’un compte professionnel ou scolaire qui a reçu des autorisations d’administrateur général, connectez-vous.
2. Choisissez la vignette Administrateur.
3. Dans le Centre d’administration, choisissez **Centres d’administration > Exchange**.

Pour plus d’informations, consultez [Définir des règles de flux de courrier pour chiffrer les messages électroniques](../compliance/define-mail-flow-rules-to-encrypt-email.md).

### <a name="brand-your-encryption-messages"></a>Marquez vos messages de chiffrement

Vous pouvez également appliquer la personnalisation de votre campagne pour personnaliser l’apparence et le texte des messages électroniques. Pour plus [d’informations, consultez Ajouter la marque de votre organisation à vos messages chiffrés](../compliance/email-encryption.md).