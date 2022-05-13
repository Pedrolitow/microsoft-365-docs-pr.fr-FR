---
title: Chiffrement avancé des messages
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 05/12/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Advanced Message Encryption aide les organisations à respecter leurs obligations de conformité en permettant aux administrateurs d’en faire encore plus avec les messages protégés.
ms.openlocfilehash: 077a17921c456ddff30e7490611dd4e78aaa5232
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393283"
---
# <a name="advanced-message-encryption"></a>Chiffrement avancé des messages

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview chiffrement avancé des messages est inclus dans [Microsoft 365 Entreprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (tarification du personnel à but non lucratif), Office 365 Entreprise E5 (personnel à but non lucratif) tarification) et Office 365 Éducation A5. Si votre organisation dispose d’un abonnement qui n’inclut pas Microsoft Purview chiffrement avancé des messages, vous pouvez l’acheter avec le module complémentaire de référence SKU Microsoft 365 E5 Conformité pour Microsoft 365 E3, Microsoft 365 E3 (prix du personnel à but non lucratif) ou le Conformité avancée Office 365 module complémentaire SKU pour les Microsoft 365 E3, les Microsoft 365 E3 (tarification du personnel à but non lucratif), les références SKU Office 365 ou les Information Protection Microsoft 365 E5/A5  et module complémentaire de référence SKU de gouvernance pour Microsoft 365 A3/E3.

Advanced Message Encryption aide les clients à respecter les obligations de conformité qui nécessitent des contrôles plus flexibles sur les destinataires externes et leur accès aux e-mails chiffrés. Avec Advanced Message Encryption dans Office 365, vous pouvez contrôler les e-mails sensibles partagés en dehors de l’organisation avec des stratégies automatiques et suivre ces activités via les journaux d’accès au portail de messages chiffrés. Vous configurez ces stratégies pour identifier les types d’informations sensibles tels que les ID piI, financiers ou d’intégrité, ou vous pouvez utiliser des mots clés pour améliorer la protection. Une fois que vous avez configuré les stratégies, vous associez des stratégies à des modèles de messagerie personnalisés de marque, puis ajoutez une date d’expiration pour un contrôle supplémentaire des e-mails qui correspondent à la stratégie. En outre, les administrateurs peuvent contrôler davantage les e-mails chiffrés accessibles en externe via un portail web sécurisé en révoquer l’accès à la messagerie à tout moment.

Vous pouvez uniquement révoquer et définir une date d’expiration pour les e-mails envoyés aux destinataires externes.

## <a name="get-started-with-microsoft-purview-advanced-message-encryption"></a>Démarrage avec Microsoft Purview chiffrement de message avancé

Les articles suivants décrivent comment configurer et utiliser Advanced Message Encryption.

Votre organisation doit disposer d’un abonnement qui inclut Microsoft Purview Chiffrement avancé des messages. Pour plus d’informations sur les abonnements pris en charge, consultez la description de la stratégie [de message et du service de conformité](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

Si vous n’avez pas encore configuré Office 365 chiffrement des messages, consultez [Configurer de nouvelles fonctionnalités de chiffrement des messages Office 365](set-up-new-message-encryption-capabilities.md).

Avec Advanced Message Encryption, vous n’êtes pas limité à un seul modèle de personnalisation. Au lieu de cela, vous pouvez créer et utiliser plusieurs modèles de personnalisation. L’ajout d’une personnalisation vous permet également d’activer le suivi d’une révocation de messages chiffrés. Pour plus [d’informations, consultez Ajouter la marque de votre organisation à vos messages chiffrés](add-your-organization-brand-to-encrypted-messages.md). Lorsque vous utilisez la personnalisation, les destinataires externes reçoivent un e-mail de notification qui contient un lien vers le portail OME. La règle de flux de messagerie détermine le modèle de personnalisation utilisé par l’e-mail de notification et le portail OME. De cette façon, votre contenu sécurisé n’est pas envoyé en dehors de votre organisation.

Vous pouvez uniquement révoquer des messages et appliquer des dates d’expiration aux messages que les utilisateurs reçoivent via le portail. En d’autres termes, un e-mail avec un modèle de personnalisation personnalisé est appliqué. Pour plus d’informations et pour obtenir un exemple, consultez les conseils dans [Vérifier que tous les destinataires externes utilisent le portail OME pour lire des messages chiffrés](manage-office-365-message-encryption.md#ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail).

[Définissez une date d’expiration pour les e-mails chiffrés par Microsoft Purview Advanced Message Encryption](ome-advanced-expiration.md). Contrôlez les e-mails sensibles partagés en dehors de l’organisation avec des stratégies automatiques qui améliorent la protection en expirant l’accès via un portail web sécurisé aux e-mails chiffrés.

[Révoquez les e-mails chiffrés par Microsoft Purview chiffrement avancé des messages](revoke-ome-encrypted-mail.md). Contrôlez les e-mails sensibles partagés en dehors de l’organisation et améliorez la protection en révoquez l’accès via un portail web sécurisé aux e-mails chiffrés.

[Journal d’activité du portail de messages chiffré par Microsoft Purview Chiffrement avancé des messages](ome-message-access-logs.md). Surveillez les e-mails sensibles partagés en dehors de l’organisation dans le portail de messages chiffrés.
