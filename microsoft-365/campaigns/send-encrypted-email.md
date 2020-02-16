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
ms.openlocfilehash: 559998326caedaf3352741ad9083940f79b1a614
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42080455"
---
# <a name="encrypt-or-label-your-sensitive-email"></a>Chiffrer ou étiqueter votre courrier électronique sensible

Les données et les informations de votre campagne sont importantes et souvent confidentielles. Protégez ces informations sensibles en utilisant des étiquettes de chiffrement et de confidentialité pour que vous et vos destinataires de courrier traitent les informations dont ils ont besoin.


## <a name="best-practices"></a>Meilleures pratiques

Avant d’envoyer un courrier électronique avec des informations confidentielles ou sensibles, envisagez d’activer :

- **Chiffrement :** Vous pouvez chiffrer votre courrier électronique pour protéger la confidentialité des informations contenues dans le message électronique. Lorsque vous chiffrez un message électronique, il est converti du texte brut lisible en texte Cypher brouillé. Seul le destinataire qui dispose de la clé privée correspondant à la clé publique utilisée pour chiffrer le message peut déchiffrer le message en lecture. Tout destinataire sans clé privée correspondante voit le texte indéchiffrable. Votre administrateur peut définir des règles pour chiffrer automatiquement les messages qui répondent à certains critères. Par exemple, votre administrateur peut créer une règle qui chiffre tous les messages envoyés en dehors de votre organisation ou tous les messages qui mentionnent des mots ou des expressions spécifiques. Toutes les règles de chiffrement seront appliquées automatiquement.
- **Étiquettes de sensibilité :** Votre campagne peut également configurer des étiquettes de confidentialité que vous pouvez appliquer à vos fichiers et à vos courriers électroniques pour les garder en conformité avec les stratégies de protection des informations de votre campagne. Lorsque vous définissez une étiquette, celle-ci est conservée dans votre courrier électronique, même si elle est envoyée, par exemple, en apparaissant comme en-tête de votre message.

![Diagramme d’un message avec des légendes pour les étiquettes et le chiffrement](../media/m365-campaign-email-encrypt.png)


## <a name="set-it-up"></a>Configuration

Si vous souhaitez chiffrer un message qui ne correspond pas à une règle prédéfinie ou que votre administrateur n’a pas défini de règles, vous pouvez appliquer diverses règles de chiffrement avant d’envoyer le message. Pour envoyer un message chiffré à partir d’Outlook 2013 ou 2016, ou Outlook 2016 pour Mac, sélectionnez **Options > autorisations**, puis sélectionnez l’option de protection dont vous avez besoin. Vous pouvez également envoyer un message chiffré en sélectionnant le bouton **protéger** dans Outlook sur le Web. Pour plus d’informations, consultez la rubrique [Envoyer, afficher et répondre à des messages chiffrés dans Outlook pour PC](https://support.office.com/article/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980?ui=en-US&rs=en-US&ad=US).

## <a name="admin-settings"></a>Paramètres d’administration

Vous pouvez en savoir plus sur la configuration du chiffrement du courrier électronique à [l’adresse de chiffrement de courrier électronique dans Office 365](https://docs.microsoft.com/office365/securitycompliance/email-encryption).

### <a name="automatically-encrypt-email-messages"></a>Chiffrer automatiquement les messages électroniques

Les administrateurs peuvent créer des règles de flux de messagerie pour protéger automatiquement les messages électroniques qui sont envoyés et reçus de votre campagne. Configurez des règles pour chiffrer les messages électroniques sortants et supprimez le chiffrement des messages chiffrés provenant de votre organisation ou des réponses aux messages chiffrés envoyés par votre organisation. 

Vous créez des règles de flux de messagerie pour chiffrer les messages électroniques avec les nouvelles fonctionnalités de chiffrement de messages Office 365 (OME). Définir des règles de flux de messagerie pour déclencher le chiffrement des messages avec les nouvelles fonctionnalités de OME à l’aide du centre d’administration Exchange. 

1. Dans un navigateur Web, à l’aide d’un compte professionnel ou scolaire auquel des autorisations d’administrateur général ont été accordées, connectez-vous à Office 365. 
2. Sélectionnez la vignette admin. 
3. Dans le centre d’administration, sélectionnez **centres d’administration > Exchange**. 

Pour plus d’informations, consultez la rubrique [définir des règles de flux de messagerie pour chiffrer les messages électroniques dans Office 365](https://docs.microsoft.com/office365/securitycompliance/define-mail-flow-rules-to-encrypt-email).

### <a name="brand-your-encryption-messages"></a>Personnaliser vos messages de chiffrement

Vous pouvez également appliquer votre personnalisation de campagne pour personnaliser l’apparence et le texte dans les messages électroniques. Pour plus d’informations, reportez-vous à la rubrique [Ajouter la marque de votre organisation à vos messages chiffrés](https://docs.microsoft.com/office365/securitycompliance/email-encryption).

