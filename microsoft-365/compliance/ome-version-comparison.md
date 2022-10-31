---
title: Comparaison des versions de chiffrement de message
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
- tier1
- purview-compliance
search.appverid:
- MET150
description: Cet article explique les différences entre les différentes versions du chiffrement des messages.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d77d61ce5c27dad476a67a4360eae463196385b4
ms.sourcegitcommit: 21548843708d80bc861f03ffae41457252492bb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68793255"
---
# <a name="compare-versions-of-message-encryption"></a>Comparer les versions de chiffrement de messages

> [!IMPORTANT]
> Le 28 février 2021, Microsoft a déprécié la prise en charge d’AD RMS dans Exchange Online. Si vous avez déployé un environnement hybride où vos boîtes aux lettres Exchange sont en ligne et que vous utilisez IRM avec Active Directory RMS localement, vous devez migrer vers Azure. Les organisations qui ont déployé dans l’environnement GCC Moderate sont également affectées. Pour plus d’informations, consultez « Vue d’ensemble de la dépréciation d’AD RMS dans Exchange Online ».

Le reste de cet article compare Office 365 Message Encryption (OME) hérité à Chiffrement de messages Microsoft Purview et Microsoft Purview Advanced Message Encryption. Chiffrement de messages Microsoft Purview est une fusion et une version plus récente d’OME et de gestion des droits relatifs à l’information (IRM). Les caractéristiques uniques du déploiement dans GCC High sont également décrites. Les deux peuvent coexister dans votre organisation. Pour plus d’informations sur le fonctionnement des nouvelles fonctionnalités, consultez [Office 365 Chiffrement des messages (OME).](ome.md)

Cet article fait partie d’une série plus large d’articles sur le chiffrement des messages. Cet article est destiné aux administrateurs et à ITPros. Si vous recherchez simplement des informations sur l’envoi ou la réception d’un message chiffré, consultez la liste des articles dans [Chiffrement](ome.md) des messages et recherchez l’article qui répond le mieux à vos besoins.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="overview-of-ad-rms-deprecation-in-exchange-online"></a>Vue d’ensemble de la dépréciation d’AD RMS dans Exchange Online

Exchange Online inclut la fonctionnalité gestion des droits relatifs à l’information (IRM) qui fournit une protection en ligne et hors connexion des messages électroniques et des pièces jointes. Par défaut, Exchange Online utilise azure Information Protection. Toutefois, votre organisation a peut-être configuré Exchange Online IRM pour utiliser Active Directory local Rights Management Service (AD RMS). La prise en charge d’AD RMS dans Exchange Online est en cours de mise hors service. Au lieu de cela, Azure Information Protection remplacera entièrement AD RMS.

Pour évaluer si cette dépréciation a un impact sur votre organisation, consultez [Comment migrer AD RMS vers Azure RMS dans Exchange Online](/exchange/troubleshoot/administration/migrate-ad-rms-to-azure). Cet article fournit des recommandations sur les options de migration.

## <a name="side-by-side-comparison-of-message-encryption-features-and-capabilities"></a>Comparaison côte à côte des fonctionnalités et fonctionnalités de chiffrement des messages

|           **Situation**           | **Legacy OME**    | **IRM dans AD RMS**        | **Chiffrement des messages Microsoft Purview** |
|-----------------------------------|-------------------|-------------------|--------------------------|
|*Envoi d’un courrier chiffré*        |Via les règles de flux de messagerie Exchange|Lancé par l’utilisateur final à partir du bureau Outlook ou d’Outlook sur le web ; ou via des règles de flux de messagerie Exchange|Lancé par l’utilisateur final à partir du bureau Outlook, d’Outlook pour Mac ou d’Outlook sur le web; par le biais de règles de flux de messagerie Exchange (également appelées règles de transport) et de protection contre la perte de données (DLP)|
|*Modèle Rights Management*       |   S/O      |Option Ne pas transférer et modèles personnalisés|Option Ne pas transférer, option de chiffrement uniquement et modèles personnalisés|
|*Type de destinataire*                   |Destinataires internes et externes|Destinataires internes uniquement         |Destinataires internes et externes|
|*Expérience pour le destinataire interne*|Les destinataires reçoivent un message HTML, qu’ils téléchargent et ouvrent dans un navigateur web ou une application mobile|Expérience intégrée native dans les clients Outlook|Expérience inline native pour les destinataires de la même organisation à l’aide de clients Outlook.  Les destinataires peuvent lire les messages à partir du portail OME à l’aide de clients autres qu’Outlook (aucun téléchargement ni application requis).|
|*Expérience pour le destinataire externe*|Les destinataires reçoivent un message HTML, qu’ils téléchargent et ouvrent dans un navigateur web ou une application mobile|S/O|Expérience inline native pour les destinataires Microsoft 365. Tous les autres destinataires peuvent lire les messages à partir du portail OME (aucun téléchargement ni application requis).|
|*Autorisations de pièce jointe*           |Aucune restriction sur les pièces jointes|Les pièces jointes sont protégées|Les pièces jointes sont protégées pour l’option Ne pas transférer et les modèles personnalisés. Les administrateurs peuvent choisir si les pièces jointes de l’option chiffrement uniquement sont protégées ou non.|
|*Prise en charge byOK (Bring Your Own Key)*|Aucun                |Aucun               |BYOK pris en charge          |

## <a name="advantages-of-microsoft-purview-message-encryption-over-legacy-ome"></a>Avantages de Chiffrement de messages Microsoft Purview par rapport à OME hérité

Les nouvelles fonctionnalités offrent les avantages suivants :

- Possibilité d’utiliser l’option de chiffrement uniquement (qui permet une collaboration sécurisée), l’option Ne pas transférer et les restrictions personnalisées.
- Les expéditeurs peuvent envoyer manuellement des messages chiffrés avec les nouvelles fonctionnalités à partir d’Outlook Desktop, Outlook pour Mac et Outlook sur le web clients.
- Les destinataires Microsoft 365 peuvent utiliser une expérience inline dans les clients Outlook pris en charge. Les administrateurs peuvent également choisir de montrer aux destinataires Microsoft 365 une expérience personnalisée.
- Les comptes en dehors de Microsoft 365, tels que les comptes Gmail, Yahoo et Microsoft, sont fédérés avec le portail OME, qui offre une meilleure expérience utilisateur à ces destinataires. Toutes les autres identités utilisent un code de passe à usage unique pour accéder aux messages chiffrés.
- Les administrateurs peuvent personnaliser la personnalisation et créer plusieurs modèles de personnalisation.
- Les administrateurs peuvent révoquer les e-mails chiffrés avec les nouvelles fonctionnalités.
- Les nouvelles fonctionnalités fournissent des rapports d’utilisation détaillés via le Centre de conformité de la sécurité &amp; .

## <a name="microsoft-purview-advanced-message-encryption-capabilities"></a>Fonctionnalités avancées de chiffrement des messages Microsoft Purview

Microsoft Purview Advanced Message Encryption offre des fonctionnalités supplémentaires en plus de Chiffrement de messages Microsoft Purview. Vous devez disposer de Chiffrement de messages Microsoft Purview configurés dans votre organisation pour pouvoir utiliser Advanced Message Encryption. En outre, pour pouvoir utiliser ces fonctionnalités, les destinataires doivent afficher les messages sécurisés et y répondre via le portail Chiffrement de messages Microsoft Purview. Les fonctionnalités avancées sont les suivantes :

- Révocation de messages

- Expiration du message

- Plusieurs modèles de personnalisation

Advanced Message Encryption n’est pas pris en charge dans GCC High.

Pour plus d’informations sur l’utilisation d’Advanced Message Encryption, consultez [Microsoft Purview Advanced Message Encryption](ome-advanced-message-encryption.md).

## <a name="unique-characteristics-of-microsoft-purview-message-encryption-in-a-gcc-high-deployment"></a>Caractéristiques uniques des Chiffrement de messages Microsoft Purview dans un déploiement GCC High

Si vous envisagez d’utiliser Chiffrement de messages Microsoft Purview dans un environnement GCC High, il existe des caractéristiques uniques concernant l’expérience du destinataire.

### <a name="encrypted-email-between-gcc-high-and-gcc-high-recipients"></a>E-mail chiffré entre gcc High et les destinataires GCC High

Les expéditeurs peuvent chiffrer manuellement les e-mails dans Outlook pour PC et Mac et Outlook sur le web, ou les organisations peuvent configurer une stratégie pour chiffrer les e-mails à l’aide des règles de flux de messagerie Exchange.

Les destinataires dans GCC High bénéficient de la même expérience de lecture inline dans Outlook pour PC et Mac et Outlook sur le web que tous les autres utilisateurs.

### <a name="encrypted-email-between-gcc-high-and-non-gcc-high-recipients"></a>E-mail chiffré entre les destinataires GCC High et non-GCC High

Les expéditeurs à l’intérieur de GCC High peuvent envoyer des e-mails chiffrés en dehors de la limite supérieure du GCC et vice versa.

Tous les destinataires en dehors de GCC High, y compris les utilisateurs commerciaux de Microsoft 365, les utilisateurs Outlook.com et les autres utilisateurs d’autres fournisseurs de messagerie tels que Gmail et Yahoo, reçoivent un message wrapper. Ce message wrapper redirige le destinataire vers le portail Chiffrement de messages Microsoft Purview, où il peut lire le message et y répondre. Cela est également vrai pour les expéditeurs en dehors de GCC High qui envoient des messages chiffrés OME à GCC High.

## <a name="coexistence-of-legacy-ome-and-microsoft-purview-message-encryption-in-the-same-tenant"></a>Coexistence d’OME et de Chiffrement de messages Microsoft Purview hérités dans le même locataire

Vous pouvez utiliser OME hérité et Chiffrement de messages Microsoft Purview dans le même locataire. En tant qu’administrateur, vous choisissez la version de chiffrement des messages que vous souhaitez utiliser lorsque vous créez vos règles de flux de courrier.

- Pour spécifier la version héritée d’OME, utilisez l’action de règle de flux de messagerie Exchange **Appliquer la version précédente d’OME**.

- Pour spécifier Chiffrement de messages Microsoft Purview, utilisez l’action de règle de flux de messagerie Exchange **Appliquer Office 365 chiffrement des messages et protection des droits**.

Les utilisateurs peuvent envoyer manuellement des messages chiffrés avec des Chiffrement de messages Microsoft Purview à partir d’Outlook Desktop, Outlook pour Mac et Outlook sur le web.

## <a name="migrate-from-legacy-ome-to-microsoft-purview-message-encryption"></a>Migrer d’OME hérité vers Chiffrement de messages Microsoft Purview

Même si les deux versions peuvent coexister, nous vous recommandons vivement de modifier vos anciennes règles de flux de courrier qui utilisent l’action **de règle Appliquer la version précédente d’OME** pour utiliser Chiffrement de messages Microsoft Purview. Mettez à jour ces règles pour utiliser l’action de règle de flux de messagerie **Appliquer Office 365 chiffrement des messages et la protection des droits**, sélectionnez « Chiffrer » dans la liste des modèles RMS. Pour obtenir des instructions, consultez [Définir des règles de flux de messagerie pour chiffrer les messages électroniques](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-ome"></a>Bien démarrer avec OME

En règle générale, Chiffrement de messages Microsoft Purview est automatiquement activé pour votre organisation. Pour plus d’informations sur Chiffrement de messages Microsoft Purview au sein de votre organisation, consultez [Configurer Chiffrement de messages Microsoft Purview](set-up-new-message-encryption-capabilities.md).

La version héritée d’OME est automatiquement activée pour votre organisation si vous avez activé Azure Information Protection. Dans le passé, OME hérité fonctionnait même si Azure Information Protection n’était pas activé. Ce n’est plus le cas.

Pour commencer à utiliser OME hérité, si vous avez activé Azure Information Protection, configurez des règles de flux de courrier qui utilisent l’action **de règle Appliquer la version précédente d’OME**. Pour obtenir des instructions, consultez [Définir des règles de flux de messagerie pour chiffrer les messages électroniques](define-mail-flow-rules-to-encrypt-email.md).
