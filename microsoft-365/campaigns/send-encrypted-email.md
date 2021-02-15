---
title: Envoyer un message électronique chiffré
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 9/20/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
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
search.appverid:
- BCS160
- MET150
ms.assetid: 496e690b-b75d-4ff5-bf34-cc32905d0364
description: Découvrez comment envoyer des messages chiffrés à l’aide d’Outlook.
ms.openlocfilehash: d17abccd645b4dfdf933906dc90175be51f95c9a
ms.sourcegitcommit: 1b30ac6e05906c8a014b1fed33fc71e1821f6ad2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2021
ms.locfileid: "50044215"
---
# <a name="encrypt-or-label-your-sensitive-email"></a>Chiffrer ou étiqueter votre courrier électronique sensible

Vos données et informations de campagne sont importantes et souvent confidentielles. Protégez ces informations sensibles à l’aide d’étiquettes de chiffrement et de sensibilité afin que vos destinataires et vous-même traitiez les informations avec le niveau de sensibilité dont ils ont besoin.

## <a name="best-practices"></a>Bonnes pratiques

Avant d’envoyer des messages électroniques avec des informations confidentielles ou sensibles, envisagez d’allumer :

- **Chiffrement :** Vous pouvez chiffrer votre courrier électronique pour protéger la confidentialité des informations dans le courrier électronique. Lorsque vous chiffrez un message électronique, il est converti du texte simple lisible en texte chiffré. Seul le destinataire qui possède la clé privée qui correspond à la clé publique utilisée pour chiffrer le message peut déchiffrer le message en lecture. Toutefois, tout destinataire sans la clé privée correspondante voit un texte indéchiffrable. Votre administrateur peut définir des règles pour chiffrer automatiquement les messages qui répondent à certains critères. Par exemple, votre administrateur peut créer une règle qui chiffre tous les messages envoyés à l’extérieur de votre organisation ou tous les messages mentionnant des mots ou des expressions spécifiques. Toutes les règles de chiffrement seront appliquées automatiquement.
- **Étiquettes de sensibilité :** Votre campagne peut également configurer des étiquettes de confidentialité que vous pouvez appliquer à vos fichiers et courriers électroniques pour les maintenir conformes aux stratégies de protection des informations de votre campagne. Lorsque vous définissez une étiquette, l’étiquette est persistante avec votre courrier électronique, même lorsqu’il est envoyé( par exemple, en apparaissant en tant qu’en-tête dans votre message.

![Diagramme d’un e-mail avec des callouts pour les étiquettes et le chiffrement](../media/m365-campaign-email-encrypt.png)

## <a name="set-it-up"></a>Configuration

Si vous souhaitez chiffrer un message qui ne répond pas à une règle prédéfinie ou si votre administrateur n’a pas défini de règles, vous pouvez appliquer différentes règles de chiffrement avant d’envoyer le message. Pour envoyer un message chiffré à partir d’Outlook 2013 ou 2016 ou d’Outlook 2016 pour Mac, sélectionnez **Options > Autorisations,** puis sélectionnez l’option de protection dont vous avez besoin. Vous pouvez également envoyer un message  chiffré en sélectionnant le bouton Protéger dans Outlook sur le web. Pour plus d’informations, voir Envoyer, afficher et répondre à des messages chiffrés [dans Outlook pour PC.](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)

## <a name="admin-settings"></a>Paramètres d’administration

Vous pouvez en savoir plus sur la configuration du chiffrement du courrier électronique à l’adresse de chiffrement de [courrier électronique dans Microsoft 365.](https://docs.microsoft.com/microsoft-365/compliance/email-encryption)

### <a name="automatically-encrypt-email-messages"></a>Chiffrer automatiquement les messages électroniques

Les administrateurs peuvent créer des règles de flux de messagerie pour protéger automatiquement les messages électroniques envoyés et reçus à partir de votre campagne. Configurer des règles pour chiffrer les messages électroniques sortants et supprimer le chiffrement des messages chiffrés provenant de l’intérieur de votre organisation ou des réponses aux messages chiffrés envoyés à partir de votre organisation.

Vous créez des règles de flux de messagerie pour chiffrer les messages électroniques avec les nouvelles fonctionnalités de chiffrement de messages Office 365 (OME). Définir des règles de flux de messagerie pour déclencher le chiffrement des messages avec les nouvelles fonctionnalités OME à l’aide du Centre d’administration Exchange (EAC). 

1. Dans un navigateur web, à l’aide d’un compte scolaire ou scolaire qui a reçu des autorisations d’administrateur général, connectez-vous.
2. Sélectionnez la vignette Administrateur.
3. Dans le Centre d’administration, choisissez **Centres d’administration > Exchange.**

Pour plus d’informations, voir [Définir des règles de flux de messagerie pour chiffrer les messages électroniques.](https://docs.microsoft.com/microsoft-365/compliance/define-mail-flow-rules-to-encrypt-email)

### <a name="brand-your-encryption-messages"></a>Brand your encryption messages

Vous pouvez également appliquer la personnalisation de votre campagne pour personnaliser l’apparence et le texte des messages électroniques. Pour plus d’informations, voir Ajouter la marque de votre organisation [à vos messages chiffrés.](https://docs.microsoft.com/microsoft-365/compliance/email-encryption)
