---
title: Chiffrement de messages avancé
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.date: 10/16/2019
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Le chiffrement de messages avancé aide les organisations à respecter leurs obligations de conformité en permettant aux administrateurs d’en faire encore plus avec les messages protégés.
ms.openlocfilehash: 8c650c47c1853102e4e2d142040e49724ef707e0
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50923954"
---
# <a name="advanced-message-encryption"></a>Chiffrement de messages avancé

Le chiffrement de messages avancé Office 365 est inclus dans [Microsoft 365 Entreprise E5,](https://www.microsoft.com/microsoft-365/enterprise/home)Office 365 E5, Microsoft 365 E5 (tarifs pour le personnel à but non lucratif), Office 365 Entreprise E5 (prix du personnel à but non lucratif) et Office 365 Éducation A5. Si votre organisation dispose d’un abonnement qui n’inclut pas le chiffrement de messages avancé Office 365, vous pouvez l’acheter avec le module SKU de conformité Microsoft 365 E5 pour Microsoft 365 E3, Microsoft 365 E3 (tarifs pour le personnel à but non lucratif) ou le module complémentaire Office 365 Conformité avancée pour Microsoft 365 E3, Microsoft 365 E3 (tarifs pour le personnel à but non lucratif), les références Office 365 ou le module complémentaire Microsoft 365 E5/A5 Information Protection and Governance SKU pour Microsoft 365 A3/E3.

Le chiffrement de messages avancé aide les clients à respecter les obligations de conformité qui nécessitent des contrôles plus souples sur les destinataires externes et leur accès aux messages électroniques chiffrés. Avec le chiffrement de messages avancé dans Office 365, vous pouvez contrôler les e-mails sensibles partagés à l’extérieur de l’organisation à l’aide de stratégies automatiques. Vous configurez ces stratégies pour identifier les types d’informations sensibles tels que les données personnelles, les identifiants financiers ou les ID d’état de santé, ou vous pouvez utiliser des mots clés pour améliorer la protection. Une fois que vous avez configuré les stratégies, associez les stratégies à des modèles de courrier personnalisés, puis ajoutez une date d’expiration pour un contrôle supplémentaire des e-mails qui correspondent à la stratégie. En outre, les administrateurs peuvent contrôler davantage les e-mails chiffrés accessibles en externe via un portail web sécurisé en révoquer l’accès au courrier électronique à tout moment.

Vous pouvez uniquement révoquer et définir une date d’expiration pour les messages électroniques envoyés à des destinataires externes.

## <a name="get-started-with-office-365-advanced-message-encryption"></a>Mise en place du chiffrement de messages avancé Office 365

Les articles suivants décrivent comment configurer et utiliser le chiffrement de messages avancé.

Votre organisation doit avoir un abonnement qui inclut le chiffrement de messages avancé Office 365. Pour plus d’informations sur les abonnements pris en charge, voir la description du service de stratégie [de message et de conformité.](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)

Si vous n’avez pas encore installé le chiffrement de messages Office 365, voir Configurer les nouvelles fonctionnalités de chiffrement de [messages Office 365.](set-up-new-message-encryption-capabilities.md)

Avec le chiffrement de messages avancé, vous n’êtes pas limité à un seul modèle de branding. Au lieu de cela, vous pouvez créer et utiliser plusieurs modèles de branding. Pour plus d’informations, voir Ajouter la marque de votre [organisation à vos messages chiffrés.](add-your-organization-brand-to-encrypted-messages.md)

[Définissez une date d’expiration pour le courrier électronique chiffré](ome-advanced-expiration.md)par le chiffrement de messages avancé Office 365. Contrôler les e-mails sensibles partagés en dehors de l’organisation avec des stratégies automatiques qui améliorent la protection en arrivant à expiration de l’accès via un portail web sécurisé aux messages électroniques chiffrés.

[Révoquer le courrier électronique chiffré par le chiffrement de messages avancé Office 365.](revoke-ome-encrypted-mail.md) Contrôler les e-mails sensibles partagés en dehors de l’organisation et améliorer la protection en révoquer l’accès via un portail web sécurisé aux messages électroniques chiffrés.  

Avec le chiffrement de messages avancé Office 365, chaque fois que vous appliquez un modèle de personnalisation, Microsoft applique un wrapper au courrier électronique qui correspond à la règle de flux de messagerie à laquelle vous appliquez le modèle. Vous pouvez uniquement révoquer des messages et appliquer des dates d’expiration aux messages que les utilisateurs reçoivent via le portail. En d’autres termes, un modèle de personnalisation est appliqué au courrier électronique. Pour plus d’informations et un exemple, voir les instructions dans Vérifier que tous les destinataires externes utilisent le portail OME pour lire [les messages chiffrés.](manage-office-365-message-encryption.md#ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail)