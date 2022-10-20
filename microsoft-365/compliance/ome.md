---
title: Chiffrement de messages Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 02/07/2020
search.appverid:
- MET150
ms.collection:
- tier1
- purview-compliance
ms.assetid: f87cb016-7876-4317-ae3c-9169b311ff8a
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment envoyer et recevoir des messages électroniques chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation.
ms.openlocfilehash: 7d08c865735c3ae8f9e6396940b03af4625aad0e
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68644832"
---
# <a name="message-encryption"></a>Chiffrement des messages

People often use email to exchange sensitive information, such as financial data, legal contracts, confidential product information, sales reports and projections, patient health information, or customer and employee information. As a result, mailboxes can become repositories for large amounts of potentially sensitive information and information leakage can become a serious threat to your organization.

Avec chiffrement de messages Office 365, votre organisation peur envoyer et recevoir des messages chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. Chiffrement de messages Office 365 fonctionne avec Outlook.com, Yahoo !, Gmail et d’autres services de messagerie. Le chiffrement de messages vous permet de vous assurer que seuls les destinataires prévus peuvent afficher le contenu des courriers.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="how-message-encryption-works"></a>Fonctionnement du chiffrement des messages

Le reste de cet article s’applique au Chiffrement de messages Microsoft Purview.

Chiffrement de messages Microsoft Purview est un service en ligne basé sur Microsoft Azure Rights Management (Azure RMS) qui fait partie d’Azure Information Protection. Ce service inclut des stratégies de chiffrement, d’identité et d’autorisation pour sécuriser votre courrier électronique. Vous pouvez chiffrer les messages à l’aide de modèles de gestion des droits, de [l’option Ne pas transférer](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails) et de l’option [chiffrer uniquement](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

Les utilisateurs peuvent ensuite chiffrer les messages électroniques et diverses pièces jointes à l’aide de ces options. Pour obtenir la liste complète des types de pièces jointes pris en charge, consultez [« Types de fichiers couverts par les stratégies IRM lorsqu’ils sont attachés aux messages » dans Introduction à IRM pour les messages électroniques](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM).

En tant qu’administrateur, vous pouvez également définir des règles de flux de messagerie pour appliquer cette protection. Par exemple, vous pouvez créer une règle qui nécessite le chiffrement de tous les messages adressés à un destinataire spécifique, ou qui contient des mots spécifiques dans la ligne d’objet, et spécifier également que les destinataires ne peuvent pas copier ou imprimer le contenu du message.

Contrairement à la version précédente d’OME, les nouvelles fonctionnalités offrent une expérience d’expéditeur unifiée, que vous envoyiez du courrier au sein de votre organisation ou à des destinataires en dehors de Microsoft 365. En outre, les destinataires qui reçoivent un message électronique protégé envoyé à un compte Microsoft 365 dans Outlook 2016 ou Outlook sur le web, n’ont pas à prendre d’autres mesures pour afficher le message. Il fonctionne en toute transparence. Les destinataires qui utilisent d’autres clients de messagerie et fournisseurs de services de messagerie bénéficient également d’une expérience améliorée. Pour plus d’informations, consultez [En savoir plus sur les messages protégés dans Office 365](https://support.office.com/article/Learn-about-protected-messages-in-Office-365-2baf3ac7-12db-40a4-8af7-1852204b4b67) et [Comment faire ouvrir un message protégé](https://support.office.com/article/How-do-I-open-a-protected-message-1157a286-8ecc-4b1e-ac43-2a608fbf3098).

Pour obtenir une liste détaillée des différences entre la version précédente d’OME et Chiffrement de messages Microsoft Purview, consultez [Comparer les versions du chiffrement des messages](ome-version-comparison.md).

Lorsqu’une personne envoie un e-mail qui correspond à une règle de flux de messagerie de chiffrement, le message est chiffré avant d’être envoyé. Tous les utilisateurs finaux de Microsoft 365 qui utilisent des clients Outlook pour lire le courrier reçoivent des expériences de lecture natives et de première classe pour les messages chiffrés et protégés par des droits, même s’ils ne font pas dans la même organisation que l’expéditeur. Les clients Outlook pris en charge incluent Outlook Desktop, Outlook Mac, Outlook Mobile sur iOS et Android, et Outlook sur le web (anciennement Outlook Web App).

Les destinataires de messages chiffrés qui reçoivent des messages chiffrés ou protégés par des droits envoyés à leurs comptes Gmail et Yahoo reçoivent un wrapper qui les dirige vers le portail OME où ils peuvent facilement s’authentifier à l’aide d’un compte Microsoft, de Gmail ou d’informations d’identification Yahoo.

Les utilisateurs finaux qui lisent des messages chiffrés ou protégés par des droits sur des clients autres qu’Outlook utilisent également le portail de messages chiffrés pour afficher les messages chiffrés et protégés par des droits qu’ils reçoivent.

Si l’expéditeur du courrier protégé se trouve dans GCC High et que le destinataire se trouve en dehors de GCC High, y compris les utilisateurs commerciaux, les utilisateurs Outlook.com et les utilisateurs d’autres fournisseurs de messagerie tels que Gmail, le destinataire reçoit un wrapper. Le courrier wrapper dirige le destinataire vers le portail de messages chiffrés où le destinataire est en mesure de lire et de répondre au message. Sinon, si l’expéditeur et le destinataire sont tous les deux dans l’environnement GCC High, même s’ils ne font pas partie de la même organisation, les destinataires qui utilisent des clients Outlook pour lire le courrier reçoivent des expériences de lecture natives de première classe pour les messages chiffrés et protégés par des droits. Pour plus d’informations sur les différentes expériences dans GCC High, consultez [Comparer les versions d’OME](ome-version-comparison.md).

Pour plus d’informations sur les limites de taille des messages et pièces jointes que vous pouvez chiffrer à l’aide d’OME, consultez [Exchange Online Limites](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).

## <a name="how-microsoft-purview-advanced-message-encryption-works-on-top-of-microsoft-purview-message-encryption"></a>Fonctionnement de Microsoft Purview Advanced Message Encryption par-dessus Chiffrement de messages Microsoft Purview

Microsoft Purview Advanced Message Encryption vous permet de créer plusieurs modèles de personnalisation afin de pouvoir affiner le contrôle sur les messages des destinataires et créer des expériences de personnalisation personnalisées pour prendre en charge une structure organisationnelle diversifiée.

Advanced Message Encryption dans Microsoft 365 vous aide à respecter les obligations de conformité qui nécessitent un contrôle plus flexible sur l’accès du destinataire externe aux e-mails chiffrés. Avec Advanced Message Encryption, en tant qu’administrateur, vous pouvez contrôler les e-mails sensibles partagés en dehors de l’organisation avec des stratégies automatiques qui détectent les types d’informations sensibles (par exemple, les ID d’informations sensibles, les ID financiers ou d’intégrité) ou les mots clés pour améliorer la protection en expirant l’accès via un portail web sécurisé aux e-mails chiffrés. En tant qu’administrateur, vous pouvez contrôler davantage les e-mails chiffrés accessibles via un portail web en révoquer l’accès à un e-mail à tout moment.

La révocation et l’expiration des messages fonctionnent uniquement pour les e-mails que vos utilisateurs envoient aux destinataires extérieurs à votre organisation. En outre, les destinataires doivent accéder à l’e-mail via le portail web. Pour vous assurer que le destinataire utilise le portail pour recevoir des e-mails, vous configurez un modèle de personnalisation personnalisé qui applique le wrapper. Ensuite, vous appliquez le modèle de personnalisation dans une règle de flux de messagerie. Pour plus d’informations sur Advanced Message Encryption, consultez [Advanced Message Encryption](ome-advanced-message-encryption.md).

## <a name="defining-rules-for-microsoft-purview-message-encryption"></a>Définition de règles pour Chiffrement de messages Microsoft Purview

Une façon d’activer Chiffrement de messages Microsoft Purview consiste à Exchange Online et à Exchange Online Protection administrateurs à définir des règles de flux de messagerie. Ces règles déterminent dans quelles conditions les messages électroniques doivent être chiffrés. Lorsqu’une action de chiffrement est définie pour une règle, tous les messages qui correspondent aux conditions de règle sont chiffrés avant leur envoi.

Les règles de flux de messagerie sont flexibles, ce qui vous permet de combiner des conditions afin de répondre à des exigences de sécurité spécifiques dans une seule règle. Par exemple, vous pouvez créer une règle pour chiffrer tous les messages qui contiennent les mots-clés spécifiés et adressés à des destinataires externes. Chiffrement de messages Microsoft Purview chiffre également les réponses des destinataires d’e-mails chiffrés.

Pour plus d’informations sur la création de règles de flux de messagerie pour tirer parti de Chiffrement de messages Microsoft Purview, consultez [Définir des règles de flux de messagerie pour chiffrer les messages électroniques](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-the-microsoft-purview-message-encryption"></a>Prise en main de la Chiffrement de messages Microsoft Purview

Si vous êtes prêt à commencer à utiliser Chiffrement de messages Microsoft Purview au sein de votre organisation, consultez [Configurer Chiffrement de messages Microsoft Purview](set-up-new-message-encryption-capabilities.md).

## <a name="sending-viewing-and-replying-to-encrypted-email-messages"></a>Envoyer, consulter et répondre à des messages électroniques chiffrés

Avec Chiffrement de messages Microsoft Purview, les utilisateurs peuvent envoyer des e-mails chiffrés à partir d’Outlook et de Outlook sur le web. En outre, les administrateurs peuvent configurer des règles de flux de messagerie dans Microsoft 365 pour chiffrer automatiquement les e-mails en fonction de la correspondance de mots clés ou d’autres conditions.

Les destinataires de messages chiffrés qui se trouvent dans des organisations pourront lire ces messages en toute transparence dans n’importe quelle version d’Outlook, y compris Outlook pour PC, Outlook pour Mac, Outlook sur le web, Outlook pour iOS et Outlook pour Android. Les utilisateurs qui reçoivent des messages chiffrés sur d’autres clients de messagerie peuvent afficher les messages dans le portail de messages chiffrés.

Pour obtenir des conseils détaillés sur l’envoi et l’affichage de messages chiffrés, consultez ces articles.

|Lisez cet article...|Si vous êtes...|
|:-----|:-----|
|[En savoir plus sur les messages protégés dans Office 365](https://support.office.com/article/2baf3ac7-12db-40a4-8af7-1852204b4b67.aspx)|Utilisateur final qui souhaite en savoir plus sur le fonctionnement des messages chiffrés et les options disponibles.|
|[Comment faire ouvrir un message protégé ?](https://support.office.com/article/1157a286-8ecc-4b1e-ac43-2a608fbf3098.aspx)|Utilisateur final qui souhaite lire un message protégé qui vous a été envoyé. Cet article contient des informations sur la lecture de messages dans plusieurs versions d’Outlook et à partir de différents comptes de messagerie, y compris les comptes en dehors de Microsoft 365 tels que gmail et Yahoo! Comptes.|
|[Envoyer, afficher et répondre à des messages chiffrés dans Outlook](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)|Utilisateur final qui souhaite envoyer, afficher ou répondre à un message chiffré à partir d’Outlook. Même si vous n’êtes pas membre d’une organisation, vous recevez toujours une notification des messages chiffrés qui vous sont envoyés dans Outlook. Utilisez cet article pour obtenir des instructions sur la façon d’afficher et de répondre aux messages chiffrés envoyés à partir de Office 365.|
|[Envoyer un message signé numériquement ou chiffré](https://support.microsoft.com/office/send-a-digitally-signed-or-encrypted-message-a18ecf7f-a7ac-4edd-b02e-687b05eff547)|Utilisateur final qui souhaite envoyer, afficher ou répondre à des messages chiffrés à l’aide de Outlook pour Mac. Cet article traite également de l’utilisation de méthodes de chiffrement autres que OME, telles que S/MIME.|
|[Afficher les messages chiffrés sur votre appareil Android](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb)|Un utilisateur final qui a reçu un message chiffré avec Office 365 Chiffrement de message sur votre appareil Android, vous pouvez utiliser l’application OME Viewer gratuite pour afficher le message et envoyer une réponse chiffrée. Cet article explique comment procéder.|
|[Afficher les messages chiffrés sur votre iPhone ou iPad](https://support.microsoft.com/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|Un utilisateur final qui a reçu un message chiffré avec Office 365 Chiffrement des messages sur votre iPhone ou iPad, vous pouvez utiliser l’application OME Viewer gratuite pour afficher le message et envoyer une réponse chiffrée. Cet article explique comment procéder.|
||
