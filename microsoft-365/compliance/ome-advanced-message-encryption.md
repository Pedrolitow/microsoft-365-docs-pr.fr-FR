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
ms.localizationpriority: medium
ms.date: 04/01/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Le chiffrement de messages avancé aide les organisations à respecter leurs obligations de conformité en permettant aux administrateurs d’en faire encore plus avec les messages protégés.
ms.openlocfilehash: 74d94bdb837531fdbbb819c86f9dbb7dd80272e8
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634336"
---
# <a name="advanced-message-encryption"></a>Chiffrement de messages avancé

Chiffrement avancé de messages Office 365 est inclus dans Microsoft 365 Entreprise [E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (tarifs du personnel pour les associations), Office 365 Entreprise  E5 (tarifs du personnel pour les associations) et Office 365 Éducation A5. Pour utiliser les fonctions avancées de révocation et d’expiration du chiffrement de messages, activez l’option Premium **chiffrement** Office 365 dans votre licence E5.

Si votre organisation dispose d’un abonnement qui n’inclut pas Chiffrement avancé de messages Office 365, vous pouvez l’acheter avec le module Microsoft 365 E5 Conformité SKU Microsoft 365 E3, Microsoft 365 E3  (Prix du personnel pour les associations) ou module Conformité avancée Office 365 SKU pour Microsoft 365 E3, Microsoft 365 E3 (prix du personnel à but non lucratif), Office 365 références (SKU) ou Microsoft 365 E5/A5 Information Protection de référence et de gouvernance pour Microsoft 365 A3/E3.

Le chiffrement de messages avancé aide les clients à respecter les obligations de conformité qui nécessitent des contrôles plus souples sur les destinataires externes et leur accès aux messages électroniques chiffrés. Avec le chiffrement de messages avancé Office 365, vous pouvez contrôler les e-mails sensibles partagés à l’extérieur de l’organisation à l’aide de stratégies automatiques. Vous configurez ces stratégies pour identifier les types d’informations sensibles tels que les données personnelles, les identifiants financiers ou les ID d’état de santé, ou vous pouvez utiliser des mots clés pour améliorer la protection. Une fois que vous avez configuré les stratégies, associez les stratégies à des modèles de courrier personnalisés, puis ajoutez une date d’expiration pour un contrôle supplémentaire des e-mails qui correspondent à la stratégie. En outre, les administrateurs peuvent contrôler davantage les e-mails chiffrés accessibles en externe via un portail web sécurisé en révoquer l’accès au courrier électronique à tout moment.

Vous pouvez uniquement révoquer et définir une date d’expiration pour les messages électroniques envoyés à des destinataires externes.

## <a name="get-started-with-office-365-advanced-message-encryption"></a>Démarrage avec Chiffrement avancé de messages Office 365

Les articles suivants décrivent comment configurer et utiliser le chiffrement de messages avancé.

Votre organisation doit avoir un abonnement qui inclut Chiffrement avancé de messages Office 365. Pour plus d’informations sur les abonnements pris en charge, voir la [description du service de conformité et de stratégie de message](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

Si vous n’avez pas encore Office 365 de chiffrement de messages, voir Configurer les nouvelles fonctionnalités Office 365 chiffrement [de messages](set-up-new-message-encryption-capabilities.md).

Avec le chiffrement de messages avancé, vous n’êtes pas limité à un seul modèle de  branding. Au lieu de cela, vous pouvez créer et utiliser plusieurs modèles de  branding. L’ajout d’une personnalisation vous permet également d’activer le suivi d’une révocation de messages chiffrés. Pour plus d’informations, [voir Ajouter la marque de votre organisation à vos messages chiffrés](add-your-organization-brand-to-encrypted-messages.md). Lorsque vous utilisez la personnalisation, les destinataires externes reçoivent un e-mail de notification contenant un lien vers le portail OME. La règle de flux de messagerie détermine le modèle de  branding utilisé par le courrier électronique de notification et le portail OME. Ainsi, votre contenu sécurisé n’est pas envoyé en dehors de votre organisation.

Vous pouvez uniquement révoquer des messages et appliquer des dates d’expiration aux messages que les utilisateurs reçoivent via le portail. En d’autres termes, un modèle de personnalisation est appliqué au courrier électronique. Pour plus d’informations et un exemple, consultez les instructions de la boîte aux lettres s’assurer que tous les [destinataires externes utilisent le portail OME pour lire les messages chiffrés](manage-office-365-message-encryption.md#ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail).

[Définissez une date d’expiration pour les messages électroniques chiffrés par Chiffrement avancé de messages Office 365](ome-advanced-expiration.md). Contrôler les e-mails sensibles partagés en dehors de l’organisation avec des stratégies automatiques qui améliorent la protection en arrivant à expiration de l’accès via un portail web sécurisé aux messages électroniques chiffrés.

[Révoquer les messages électroniques chiffrés par Chiffrement avancé de messages Office 365](revoke-ome-encrypted-mail.md). Contrôler les e-mails sensibles partagés en dehors de l’organisation et améliorer la protection en révoquer l’accès via un portail web sécurisé aux messages électroniques chiffrés.  
