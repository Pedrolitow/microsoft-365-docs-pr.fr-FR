---
title: Comparaison des versions de chiffrement des messages
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Cet article explique les différences entre les différentes versions du chiffrement des messages.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 44eb59a160af9ecbe171e1c9b63f67e6ac608fe0
ms.sourcegitcommit: cd9df1a681265905eef99c039f7036b2fa6e8b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2022
ms.locfileid: "67276260"
---
# <a name="compare-versions-of-message-encryption"></a>Comparer les versions de chiffrement de messages

> [!IMPORTANT]
> Le 28 février 2021, Microsoft a déprécié la prise en charge d’AD RMS dans Exchange Online. Si vous avez déployé un environnement hybride dans lequel vos boîtes aux lettres Exchange sont en ligne et que vous utilisez irm avec Active Directory RMS en local, vous devez migrer vers Azure. Les organisations déployées dans l’environnement GCC Moderate sont également affectées. Pour plus d’informations, consultez « Vue d’ensemble de la dépréciation d’AD RMS dans Exchange Online ».

Le reste de cet article compare le chiffrement de message hérité Office 365 (OME) à Chiffrement de messages Microsoft Purview et Microsoft Purview Advanced Message Encryption. Chiffrement de messages Microsoft Purview est une fusion et une version plus récente d’OME et de gestion des droits relatifs à l’information (IRM). Les caractéristiques uniques du déploiement dans GCC High sont également décrites. Les deux peuvent coexister dans votre organisation. Pour plus d’informations sur le fonctionnement des nouvelles fonctionnalités, consultez [Office 365 chiffrement des messages (OME).](ome.md)

Cet article fait partie d’une plus grande série d’articles sur le chiffrement des messages. Cet article est destiné aux administrateurs et aux itpros. Si vous recherchez simplement des informations sur l’envoi ou la réception d’un message chiffré, consultez la liste des articles dans [le chiffrement](ome.md) des messages et recherchez l’article qui répond le mieux à vos besoins.

## <a name="overview-of-ad-rms-deprecation-in-exchange-online"></a>Vue d’ensemble de la dépréciation d’AD RMS dans Exchange Online

Exchange Online inclut la fonctionnalité gestion des droits relatifs à l’information (IRM) qui fournit une protection en ligne et hors connexion des e-mails et des pièces jointes. Par défaut, Exchange Online utilise Azure Information Protection. Toutefois, votre organisation a peut-être configuré Exchange Online IRM pour utiliser Active Directory local Rights Management Service (AD RMS). La prise en charge d’AD RMS dans Exchange Online est en cours de mise hors service. Au lieu de cela, Azure Information Protection remplacera entièrement AD RMS.

Pour déterminer si cette dépréciation a un impact sur votre organisation, consultez [Comment migrer AD RMS vers Azure RMS dans Exchange Online](/exchange/troubleshoot/administration/migrate-ad-rms-to-azure). Cet article fournit des recommandations sur les options de migration.

## <a name="side-by-side-comparison-of-message-encryption-features-and-capabilities"></a>Comparaison côte à côte des fonctionnalités et fonctionnalités de chiffrement des messages

|           **Situation**           | **Legacy OME**    | **IRM dans AD RMS**        | **Chiffrement des messages Microsoft Purview** |
|-----------------------------------|-------------------|-------------------|--------------------------|
|*Envoi d’un courrier chiffré*        |Via des règles de flux de messagerie Exchange|Utilisateur final initié à partir du bureau Outlook ou d’Outlook sur le web ; ou via des règles de flux de messagerie Exchange|Utilisateur final initié à partir d’Outlook Desktop, Outlook pour Mac ou Outlook sur le web ; via les règles de flux de messagerie Exchange (également appelées règles de transport) et la protection contre la perte de données (DLP)|
|*Modèle de gestion des droits*       |   S/O      |Option Ne pas transférer et modèles personnalisés|Option Ne pas transférer, option chiffrer uniquement et modèles personnalisés|
|*Type de destinataire*                   |Destinataires internes et externes|Destinataires internes uniquement         |Destinataires internes et externes|
|*Expérience pour le destinataire interne*|Les destinataires reçoivent un message HTML qu’ils téléchargent et ouvrent dans un navigateur web ou une application mobile|Expérience inline native dans les clients Outlook|Expérience inline native pour les destinataires de la même organisation à l’aide de clients Outlook.  Les destinataires peuvent lire le message à partir du portail OME à l’aide de clients autres qu’Outlook (aucun téléchargement ou application requis).|
|*Expérience pour le destinataire externe*|Les destinataires reçoivent un message HTML qu’ils téléchargent et ouvrent dans un navigateur web ou une application mobile|S/O|Expérience inline native pour les destinataires Microsoft 365. Tous les autres destinataires peuvent lire le message à partir du portail OME (aucun téléchargement ou application requis).|
|*Autorisations de pièce jointe*           |Aucune restriction sur les pièces jointes|Les pièces jointes sont protégées|Les pièces jointes sont protégées pour l’option Ne pas transférer et les modèles personnalisés. Les administrateurs peuvent choisir si les pièces jointes de l’option chiffrer uniquement sont protégées ou non.|
|*Prise en charge de BYOK (Apportez votre propre clé)*|Aucun                |Aucun               |BYOK pris en charge          |
||

## <a name="advantages-of-microsoft-purview-message-encryption-over-legacy-ome"></a>Avantages de Chiffrement de messages Microsoft Purview par rapport à l’OME hérité

Les nouvelles fonctionnalités offrent les avantages suivants :

- Possibilité d’utiliser l’option chiffrer uniquement (ce qui permet une collaboration sécurisée), l’option Ne pas transférer et les restrictions personnalisées.
- Les expéditeurs peuvent envoyer des messages chiffrés avec les nouvelles fonctionnalités manuellement à partir d’Outlook Desktop, Outlook pour Mac et Outlook sur le web clients.
- Les destinataires Microsoft 365 peuvent utiliser une expérience inline dans les clients Outlook pris en charge. Les administrateurs peuvent également choisir d’afficher une expérience de marque aux destinataires Microsoft 365.
- Les comptes en dehors de Microsoft 365, tels que les comptes Gmail, Yahoo et Microsoft, sont fédérés avec le portail OME, ce qui offre une meilleure expérience utilisateur pour ces destinataires. Toutes les autres identités utilisent un code de passe unique pour accéder aux messages chiffrés.
- Les administrateurs peuvent personnaliser la personnalisation et créer plusieurs modèles de personnalisation.
- Les administrateurs peuvent révoquer les e-mails chiffrés avec les nouvelles fonctionnalités.
- Les nouvelles fonctionnalités fournissent des rapports d’utilisation détaillés via le Centre de conformité de la sécurité &amp; .

## <a name="microsoft-purview-advanced-message-encryption-capabilities"></a>Fonctionnalités avancées de chiffrement de messages Microsoft Purview

Microsoft Purview Advanced Message Encryption offre des fonctionnalités supplémentaires en plus de Chiffrement de messages Microsoft Purview. Vous devez avoir Chiffrement de messages Microsoft Purview configuré dans votre organisation pour pouvoir utiliser Advanced Message Encryption. En outre, pour utiliser ces fonctionnalités, les destinataires doivent afficher et répondre pour sécuriser le courrier via le portail Chiffrement de messages Microsoft Purview. Les fonctionnalités avancées sont les suivantes :

- Révocation des messages

- Expiration du message

- Plusieurs modèles de personnalisation

Advanced Message Encryption n’est pas pris en charge dans GCC High.

Pour plus d’informations sur l’utilisation d’Advanced Message Encryption, consultez [Microsoft Purview Advanced Message Encryption](ome-advanced-message-encryption.md).

## <a name="unique-characteristics-of-microsoft-purview-message-encryption-in-a-gcc-high-deployment"></a>Caractéristiques uniques de Chiffrement de messages Microsoft Purview dans un déploiement GCC High

Si vous envisagez d’utiliser Chiffrement de messages Microsoft Purview dans un environnement GCC High, il existe des caractéristiques uniques concernant l’expérience du destinataire.

### <a name="encrypted-email-between-gcc-high-and-gcc-high-recipients"></a>E-mail chiffré entre les destinataires GCC High et GCC High

Les expéditeurs peuvent chiffrer manuellement les e-mails dans Outlook pour PC et Mac et Outlook sur le web, ou les organisations peuvent configurer une stratégie pour chiffrer les e-mails à l’aide de règles de flux de messagerie Exchange.

Les destinataires à l’intérieur de GCC High reçoivent la même expérience de lecture en ligne dans Outlook pour PC et Mac et Outlook sur le web que tous les autres utilisateurs.

### <a name="encrypted-email-between-gcc-high-and-non-gcc-high-recipients"></a>E-mail chiffré entre les destinataires GCC High et Non-GCC High

Les expéditeurs à l’intérieur de GCC High peuvent envoyer des e-mails chiffrés en dehors de la limite GCC High et vice versa.

Tous les destinataires en dehors de GCC High, y compris les utilisateurs commerciaux de Microsoft 365, les utilisateurs Outlook.com et d’autres utilisateurs d’autres fournisseurs de messagerie tels que Gmail et Yahoo, reçoivent un wrapper. Ce message wrapper redirige le destinataire vers le portail Chiffrement de messages Microsoft Purview où le destinataire peut lire et répondre au message. Cela est également vrai pour les expéditeurs en dehors de GCC High qui envoient des messages chiffrés OME à GCC High.

## <a name="coexistence-of-legacy-ome-and-microsoft-purview-message-encryption-in-the-same-tenant"></a>Coexistence d’OME et de Chiffrement de messages Microsoft Purview hérités dans le même locataire

Vous pouvez utiliser OME et Chiffrement de messages Microsoft Purview hérités dans le même locataire. En tant qu’administrateur, vous choisissez la version de chiffrement des messages que vous souhaitez utiliser lorsque vous créez vos règles de flux de messagerie.

- Pour spécifier la version héritée d’OME, utilisez l’action de règle de flux de messagerie Exchange **Appliquer la version précédente d’OME**.

- Pour spécifier Chiffrement de messages Microsoft Purview, utilisez l’action de règle de flux de messagerie Exchange **Appliquer Office 365 chiffrement des messages et protection des droits**.

Les utilisateurs peuvent envoyer manuellement des messages chiffrés avec Chiffrement de messages Microsoft Purview à partir d’Outlook Desktop, Outlook pour Mac et Outlook sur le web.

## <a name="migrate-from-legacy-ome-to-microsoft-purview-message-encryption"></a>Migrer d’OME hérité vers Chiffrement de messages Microsoft Purview

Même si les deux versions peuvent coexister, nous vous recommandons vivement de modifier vos anciennes règles de flux de messagerie qui utilisent l’action **de règle Appliquer la version précédente d’OME** pour utiliser Chiffrement de messages Microsoft Purview. Mettez à jour ces règles pour utiliser l’action de règle de flux de messagerie **Appliquer Office 365 chiffrement des messages et protection des droits**, sélectionnez « Chiffrer » dans la liste des modèles RMS. Pour obtenir des instructions, consultez [Définir des règles de flux de courrier pour chiffrer les messages électroniques](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-ome"></a>Prise en main d’OME

En règle générale, Chiffrement de messages Microsoft Purview est automatiquement activé pour votre organisation. Pour plus d’informations sur Chiffrement de messages Microsoft Purview au sein de votre organisation, consultez [Configurer Chiffrement de messages Microsoft Purview](set-up-new-message-encryption-capabilities.md).

La version héritée d’OME est automatiquement activée pour votre organisation si vous avez activé Azure Information Protection. Dans le passé, OME hérité fonctionnait même si Azure Information Protection n’était pas activé. Ce n’est plus le cas.

Pour commencer à utiliser OME hérité, si vous avez activé Azure Information Protection, configurez des règles de flux de messagerie qui utilisent l’action **de règle Appliquer la version précédente d’OME**. Pour obtenir des instructions, consultez [Définir des règles de flux de courrier pour chiffrer les messages électroniques](define-mail-flow-rules-to-encrypt-email.md).
