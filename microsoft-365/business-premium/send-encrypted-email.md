---
title: Envoyer un message électronique chiffré
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-security
ms.subservice: other
ms.date: 09/15/2022
ms.localizationpriority: high
ms.collection:
- M365-Campaigns
- m365solution-smb
- highpri
- tier1
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
description: Découvrez comment envoyer des messages électroniques chiffrés à l’aide d’Outlook.
ms.openlocfilehash: 481f40321a56ba398c25601a1c5da1a91daae67b
ms.sourcegitcommit: 0283c436f3ba61a708b52b57a1955f5ea74376a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68097245"
---
# <a name="encrypt-or-label-your-sensitive-email-in-microsoft-365"></a>Chiffrer ou étiqueter votre e-mail sensible dans Microsoft 365

Your data and information is important, and often, confidential. The objective here is to help protect this sensitive information by ensuring everyone is using sensitivity labels so that email recipients treat the information with the utmost sensitivity.

## <a name="best-practices"></a>Meilleures pratiques

Avant d’envoyer des messages électroniques contenant des informations confidentielles ou sensibles, les utilisateurs doivent envisager d’activer les fonctionnalités suivantes :

- **Cryptage :** vous pouvez chiffrer votre courrier électronique pour protéger la confidentialité des informations contenues dans les message électroniques. Lorsque vous chiffrez un message électronique, il est converti à partir d’un texte brut lisible en texte chiffré brouillé. Seul le destinataire disposant de la clé privée qui correspond à la clé publique utilisée pour chiffrer le message peut déchiffrer le message à lire. Toutefois, tout destinataire ne disposant pas de la clé privée correspondante voit un texte indéchiffrable. Votre administrateur peut définir des règles pour chiffrer automatiquement les messages qui répondent à certains critères. Par exemple, votre administrateur peut créer une règle qui chiffre tous les messages envoyés en dehors de votre organisation ou tous les messages qui mentionnent des mots ou des expressions spécifiques. Toutes les règles de chiffrement sont appliquées automatiquement.

- **Étiquettes de confidentialité :** si votre organisation en a besoin, vous pouvez configurer des étiquettes de confidentialité que vous appliquez à vos fichiers et messages électroniques afin de les rendre conformes aux stratégies de protection des informations de votre organisation. Lorsque vous définissez une étiquette, l’étiquette persiste avec votre message électronique, même lorsqu’il est envoyé &mdash; par exemple, en apparaissant sous la forme d’un en-tête à votre message.

![Diagramme d’un message électronique avec des légendes pour les étiquettes et le chiffrement.](../media/m365-campaign-email-encrypt.png)

## <a name="set-it-up"></a>Configuration

Si vous souhaitez chiffrer un message qui ne répond pas à une règle prédéfinie ou si votre administrateur n’a pas configuré de règles, vous pouvez appliquer différentes règles de chiffrement avant d’envoyer le message. Pour envoyer un message chiffré à partir d’Outlook 2013 ou 2016, ou Outlook 2016 pour Mac, sélectionnez **Options > Autorisations**, puis sélectionnez l’option de protection dont vous avez besoin. Vous pouvez également envoyer un message chiffré en sélectionnant le bouton **Protéger** dans Outlook sur le web. Pour plus d’informations, consultez [Envoyer, afficher et répondre à des messages chiffrés dans Outlook pour PC](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="admin-settings"></a>Paramètres d’administration

Vous pouvez en savoir plus sur la configuration du chiffrement des messages électroniques à l’adresse [Chiffrement des messages électroniques dans Microsoft 365](../compliance/email-encryption.md).

### <a name="automatically-encrypt-email-messages"></a>Chiffrer automatiquement les messages électroniques

Les administrateurs peuvent créer des règles de flux de courrier pour protéger automatiquement les messages électroniques envoyés et reçus d’une campagne ou d’une entreprise. Configurez des règles pour chiffrer les messages électroniques sortants et supprimer le chiffrement des messages chiffrés provenant de votre organisation ou des réponses aux messages chiffrés par votre organisation.

Vous créez des règles de flux de courrier pour chiffrer les messages électroniques avec Chiffrement des messages Microsoft Purview. Définissez des règles de flux de courrier pour déclencher le chiffrement des messages à l’aide du <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange (EAC)</a>.

1. Dans un navigateur web, à l’aide d’un compte professionnel ou scolaire qui a reçu des autorisations d’administrateur général, connectez-vous.
2. Sélectionnez la mosaïque Administrateur.
3. Dans le centre d’administration, choisissez **Centres d’administration > Exchange**.

Pour en savoir plus, consultez la rubrique [Définir le flux de courrier pour chiffrer des messages électroniques](../compliance/define-mail-flow-rules-to-encrypt-email.md).

### <a name="brand-your-encryption-messages"></a>Marquez vos messages de chiffrement

Vous pouvez également appliquer la personnalisation pour personnaliser l’apparence et le texte des messages électroniques. Pour plus d’informations, consultez la rubrique [Ajouter la marque de votre organisation à vos messages chiffrés](../compliance/email-encryption.md).

## <a name="next-mission"></a>Prochaine mission

Si vous avez atteint ce stade, vous avez terminé une autre mission, alors félicitations ! Nous n’avons pas le temps de nous reposer sur nos lauriers. Nous allons donc nous atteler à la configuration d’un environnement sûr et sécurisé dans lequel l’équipe peut [collaborer en toute sécurité](m365bp-collaborate-share-securely.md).