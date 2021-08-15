---
title: Chiffrement des messages
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.date: 02/07/2020
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.assetid: f87cb016-7876-4317-ae3c-9169b311ff8a
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment envoyer et recevoir des messages électroniques chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation.
ms.openlocfilehash: 779d23222dd3308ed6464f195cc63ee11da0fc35cf32986c15cc4f7008ac0a97
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53895282"
---
# <a name="message-encryption"></a>Chiffrement des messages

Les messageries électroniques sont souvent utilisées pour échanger des informations sensibles. Par exemple : rapports et états financiers, contrats juridiques, informations confidentielles sur des produits, comptes rendus et prévisions de ventes, données médicales relatives à des patients ou informations sur les clients et le personnel. Il s'en suit que les boîtes aux lettres deviennent vite des référentiels contenant de gros volumes d'informations potentiellement sensibles. C'est pourquoi, toute fuite d'informations peut constituer une véritable menace pour votre organisation.

Avec chiffrement de messages Office 365, votre organisation peur envoyer et recevoir des messages chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. Chiffrement de messages Office 365 fonctionne avec Outlook.com, Yahoo !, Gmail et d’autres services de messagerie. Le chiffrement des messages électroniques permet de s’assurer que seuls les destinataires prévus peuvent afficher le contenu des messages.

## <a name="how-office-365-message-encryption-works"></a>Fonctionnement de chiffrement de messages Office 365

Le reste de cet article s’applique aux nouvelles fonctionnalités OME.

chiffrement de messages Office 365 est un service en ligne qui repose sur Microsoft Azure Rights Management (Azure RMS) qui fait partie d’Azure Information Protection. Ce service inclut des stratégies de chiffrement, d’identité et d’autorisation pour sécuriser votre courrier électronique. Vous pouvez chiffrer des messages à l’aide de modèles de gestion des droits, de [l’option](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails)Ne pas forwarder et de l’option [Chiffrer uniquement.](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)

Les utilisateurs peuvent ensuite chiffrer des messages électroniques et diverses pièces jointes à l’aide de ces options. Pour obtenir la liste complète des types de pièces jointes pris en charge, voir « Types de fichiers couverts par les stratégies IRM lorsqu’ils sont joints à des messages » dans [l’introduction](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM)à LA GESTION des messages électroniques.

En tant qu’administrateur, vous pouvez également définir des règles de flux de messagerie pour appliquer cette protection. Par exemple, vous pouvez créer une règle qui requiert le chiffrement de tous les messages adressés à un destinataire spécifique, ou qui contient des mots spécifiques dans la ligne d’objet, et spécifier que les destinataires ne peuvent pas copier ou imprimer le contenu du message.

Contrairement à la version précédente d’OME, les nouvelles fonctionnalités offrent une expérience d’expéditeur unifiée, que vous envoyiez des messages à l’intérieur de votre organisation ou à des destinataires en dehors de Microsoft 365. En outre, les destinataires qui reçoivent un message électronique protégé envoyé à un compte Microsoft 365 dans Outlook 2016 ou Outlook sur le web n’ont aucune autre action à prendre pour afficher le message. Il fonctionne en toute transparence. Les destinataires qui utilisent d’autres clients de messagerie et fournisseurs de services de messagerie ont également une expérience améliorée. Pour plus d’informations, voir En savoir plus sur les messages protégés [dans Office 365](https://support.office.com/article/Learn-about-protected-messages-in-Office-365-2baf3ac7-12db-40a4-8af7-1852204b4b67) et comment ouvrir un message [protégé](https://support.office.com/article/How-do-I-open-a-protected-message-1157a286-8ecc-4b1e-ac43-2a608fbf3098).

Pour obtenir la liste détaillée des différences entre la version précédente d’OME et les nouvelles fonctionnalités OME, voir Comparer les [versions d’OME.](ome-version-comparison.md)

Lorsqu’une personne envoie un message électronique qui correspond à une règle de flux de messagerie de chiffrement, le message est chiffré avant d’être envoyé. Tous les utilisateurs finaux Microsoft 365 qui utilisent des clients Outlook pour lire le courrier reçoivent des expériences de lecture natives de première classe pour les messages chiffrés et protégés par des droits, même s’ils ne font pas partie de la même organisation que l’expéditeur. Les clients Outlook pris en charge incluent Outlook bureau, Outlook Mac, Outlook mobile sur iOS et Android et Outlook sur le web (anciennement Outlook Web App).

Les destinataires de messages chiffrés qui reçoivent des messages chiffrés ou protégés par des droits envoyés à leurs comptes Outlook.com, Gmail et Yahoo reçoivent un courrier électronique de wrapper qui les dirige vers le portail OME où ils peuvent facilement s’authentifier à l’aide d’informations d’identification Microsoft, Gmail ou Yahoo.

Les utilisateurs finaux qui lisent des messages chiffrés ou protégés par des droits sur des clients autres que Outlook utilisent également le portail OME pour afficher les messages chiffrés et protégés par des droits qu’ils reçoivent.

Si l’expéditeur du courrier protégé est en Cloud de la communauté du secteur public Élevé et que le destinataire se trouve en dehors de Cloud de la communauté du secteur public High, y compris les utilisateurs commerciaux, les utilisateurs Outlook.com et les utilisateurs d’autres fournisseurs de messagerie tels que Gmail, le destinataire reçoit un wrapper. Le message de wrapper dirige le destinataire vers le portail OME où le destinataire peut lire le message et y répondre. Dans le cas contraire, si l’expéditeur et le destinataire sont tous les deux dans l’environnement Cloud de la communauté du secteur public High, même s’ils ne font pas partie de la même organisation, les destinataires qui utilisent des clients Outlook pour lire le courrier reçoivent des expériences de lecture natives de première classe pour les messages chiffrés et protégés par des droits. Pour plus d’informations sur les différentes expériences Cloud de la communauté du secteur public high, voir [Comparer les versions d’OME.](ome-version-comparison.md)

Pour plus d’informations sur les limites de taille des messages et des pièces jointes que vous pouvez chiffrer à l’aide d’OME, voir [Exchange Online limites.](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits)

## <a name="how-office-365-advanced-message-encryption-works-on-top-of-ome"></a>Fonctionnement Chiffrement avancé de messages Office 365 OME

Chiffrement avancé de messages Office 365 vous permet de créer plusieurs modèles de personnalisation afin d’affiner le contrôle sur le courrier des destinataires et de créer des expériences de personnalisation personnalisées pour prendre en charge une structure organisationnelle variée.

Le chiffrement de messages avancé Microsoft 365 vous permet de respecter les obligations de conformité qui nécessitent un contrôle plus souple sur l’accès des destinataires externes aux messages électroniques chiffrés. Avec le chiffrement de messages avancé dans Office 365, en tant qu’administrateur, vous pouvez contrôler les e-mails sensibles partagés en dehors de l’organisation avec des stratégies automatiques qui détectent les types d’informations sensibles (par exemple, les données personnelles, les ID financiers ou d’état de santé) ou les mots clés pour améliorer la protection en arrivant à expiration de l’accès via un portail web sécurisé aux messages électroniques chiffrés. En tant qu’administrateur, vous pouvez contrôler davantage les e-mails chiffrés accessibles via un portail web Microsoft 365 en révoquer l’accès à un e-mail à tout moment.

La révocation et l’expiration des messages fonctionnent uniquement pour les e-mails que vos utilisateurs envoient à des destinataires extérieurs à votre organisation. En outre, les destinataires doivent accéder à l’e-mail via le portail web. Pour vous assurer que le destinataire utilise le portail pour recevoir des messages électroniques, vous devez configurer un modèle de personnalisation qui applique le wrapper. Ensuite, vous appliquez le modèle de branding dans une règle de flux de messagerie. Pour plus d’informations sur le chiffrement de messages avancé, [voir Chiffrement avancé de messages Office 365](ome-advanced-message-encryption.md).

## <a name="defining-rules-for-office-365-message-encryption"></a>Définir les règles pour le chiffrement de messages Office 365

L’une des façons d’activer les nouvelles fonctionnalités pour chiffrement de messages Office 365 consiste à Exchange Online et Exchange Online Protection administrateurs de définir des règles de flux de messagerie. Ces règles déterminent dans quelles conditions les messages électroniques doivent être chiffrés. Lorsqu’une action de chiffrement est définie pour une règle, tous les messages qui correspondent aux conditions de règle sont chiffrés avant d’être envoyés.

Les règles de flux de messagerie sont flexibles, ce qui vous permet de combiner des conditions afin de répondre à des exigences de sécurité spécifiques dans une seule règle. Par exemple, vous pouvez créer une règle pour chiffrer tous les messages qui contiennent les mots-clés spécifiés et adressés à des destinataires externes. Les nouvelles fonctionnalités pour chiffrement de messages Office 365 chiffrent également les réponses des destinataires d’e-mails chiffrés.

Pour plus d’informations sur la création de règles de flux de messagerie pour tirer parti des nouvelles fonctionnalités OME, voir Définir des règles [pour chiffrement de messages Office 365](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-the-new-ome-capabilities"></a>Mise en place des nouvelles fonctionnalités OME

Si vous êtes prêt à commencer à utiliser les nouvelles fonctionnalités OME au sein de votre organisation, voir Configurer de nouvelles fonctionnalités [chiffrement de messages Office 365 de gestion.](set-up-new-message-encryption-capabilities.md)

## <a name="sending-viewing-and-replying-to-encrypted-email-messages"></a>Envoyer, consulter et répondre à des messages électroniques chiffrés

Avec chiffrement de messages Office 365, les utilisateurs peuvent envoyer des messages chiffrés Outlook et Outlook sur le web. En outre, les administrateurs peuvent configurer des règles de flux de messagerie dans Microsoft 365 pour chiffrer automatiquement les messages électroniques en fonction de la correspondance de mots clés ou d’autres conditions.

Les destinataires de messages chiffrés qui sont dans des organisations pourront lire ces messages en toute transparence dans n’importe quelle Outlook de version, y compris Outlook pour PC, Outlook pour Mac, Outlook sur le web, Outlook pour iOS et Outlook pour Android. Les utilisateurs qui reçoivent des messages chiffrés sur d’autres clients de messagerie peuvent afficher les messages dans le portail OME.

Pour obtenir des instructions détaillées sur l’envoi et l’affichage des messages chiffrés, consultez ces articles.

|Lisez cet article...|Si vous...|
|:-----|:-----|
|[En savoir plus sur les messages protégés dans Office 365](https://support.office.com/article/2baf3ac7-12db-40a4-8af7-1852204b4b67.aspx)|Un utilisateur final qui souhaite en savoir plus sur le fonctionnement des messages chiffrés et les options disponibles.|
|[Comment ouvrir un message protégé ?](https://support.office.com/article/1157a286-8ecc-4b1e-ac43-2a608fbf3098.aspx)|Un utilisateur final qui souhaite lire un message protégé qui vous a été envoyé. Cet article inclut des informations sur la lecture de messages dans plusieurs versions de Outlook et à partir de différents comptes de messagerie, y compris les comptes en dehors de Microsoft 365 tels que gmail et Yahoo! comptes.|
|[Envoyer, afficher et répondre à des messages chiffrés dans Outlook](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)|Utilisateur final qui souhaite envoyer, afficher ou répondre à un message chiffré à partir d Outlook. Même si vous n’êtes pas membre d’une organisation, vous recevez toujours une notification de messages chiffrés qui vous sont envoyés dans Outlook. Utilisez cet article pour obtenir des instructions sur la façon d’afficher et de répondre aux messages chiffrés envoyés Office 365.|
|[Envoyer un message signé numériquement ou chiffré](https://support.microsoft.com/office/send-a-digitally-signed-or-encrypted-message-a18ecf7f-a7ac-4edd-b02e-687b05eff547)|Utilisateur final qui souhaite envoyer, afficher ou répondre à des messages chiffrés à l’aide Outlook pour Mac. Cet article traite également de l’utilisation de méthodes de chiffrement autres que OME, telles que S/MIME.|
|[Afficher les messages chiffrés sur votre appareil Android](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb)|Un utilisateur final qui a reçu un message chiffré avec chiffrement de messages Office 365 sur votre appareil Android, vous pouvez utiliser l’application gratuite Visionneuse OME pour afficher le message et envoyer une réponse chiffrée. Cet article explique comment.|
|[Afficher les messages chiffrés sur iPhone ou iPad](https://support.microsoft.com/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|Un utilisateur final qui a reçu un message chiffré avec chiffrement de messages Office 365 sur votre iPhone ou iPad, vous pouvez utiliser l’application visionneuse OME gratuite pour afficher le message et envoyer une réponse chiffrée. Cet article explique comment.|
||