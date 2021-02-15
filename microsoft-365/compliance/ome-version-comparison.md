---
title: Comparaison des versions du chiffrement de messages (OME)
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.date: 4/30/2019
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Cet article explique les différences entre les différentes versions du chiffrement de messages Office 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 30344a9cbe8629804f5026fc809577923965b7bc
ms.sourcegitcommit: b3bb5bf5efa197ef8b16a33401b0b4f5663d3aa0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2021
ms.locfileid: "50032621"
---
# <a name="compare-versions-of-ome"></a>Comparez les versions de OME

> [!IMPORTANT]
> Le 28 février 2021, Microsoft ne prendra plus en charge AD RMS dans Exchange Online. Si vous avez déployé un environnement hybride dans lequel vos boîtes aux lettres Exchange sont en ligne et que vous utilisez irm avec Active Directory RMS en local, vous devez migrer vers Azure. Les organisations qui ont été déployées dans l’environnement GCC Moderate sont également affectées. Pour plus d’informations, voir « Vue d’ensemble de l’utilisation d’AD RMS dans Exchange Online » dans cet article.

Le reste de cet article compare le chiffrement de messages Office 365 hérité (OME) aux nouvelles fonctionnalités OME et au chiffrement de messages avancé Office 365. Les nouvelles fonctionnalités sont une fusion et une version plus récente d’OME et de la Gestion des droits de l’information (IRM). Les caractéristiques uniques du déploiement dans GCC High sont également décrites. Les deux peuvent coexister dans votre organisation. Pour plus d’informations sur le fonctionnement des nouvelles fonctionnalités, voir Chiffrement de messages [Office 365 (OME).](ome.md)

Cet article fait partie d’une série plus importante d’articles sur le chiffrement de messages Office 365. Cet article est destiné aux administrateurs et aux itpros. Si vous recherchez simplement des informations sur l’envoi ou la réception d’un message chiffré, consultez la liste des articles dans le chiffrement de messages [Office 365 (OME)](ome.md) et recherchez l’article qui répond le mieux à vos besoins.

## <a name="overview-of-ad-rms-deprecation-in-exchange-online"></a>Vue d’ensemble de l’utilisation d’AD RMS dans Exchange Online

Exchange Online inclut la fonctionnalité Gestion des droits de l’information (IRM) qui fournit une protection en ligne et hors connexion des messages électroniques et des pièces jointes. Par défaut, Exchange Online utilise Azure Azure Information Protection. Toutefois, votre organisation a peut-être configuré l’IRM Exchange Online pour utiliser le service AD RMS (Active Directory Rights Management Service) local. La prise en charge d’AD RMS dans Exchange Online est en cours de retrait. Au lieu de cela, Azure Information Protection remplacera entièrement AD RMS.

Avant de commencer, examinez et évaluez l’impact pour votre organisation. Si votre organisation utilise déjà Azure Information Protection pour chiffrer le courrier électronique dans Exchange Online, vous n’avez rien à faire. Si vous chiffrez votre courrier électronique à l’aide de règles de flux de messagerie Exchange, par exemple à l’aide du chiffrement de messages Office 365, vous n’avez pas besoin de modifier votre courrier sécurisé. Dans le cas contraire, vous devrez vous préparer à l’arrêt d’AD RMS en passant à Azure Information Protection.

### <a name="prepare-for-ad-rms-deprecation"></a>Préparer l’annulation d’AD RMS

Si vous avez déjà installé Azure Information Protection mais que vous ne l’utilisez pas, activez le service à l’aide d’Exchange Online PowerShell. Sur votre ordinateur local, à l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous à [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell) dans Windows PowerShell fenêtre.

Pour activer Azure Information Protection, utilisez la cmdlet Set-IrmConfiguration en tapant la commande suivante.

```powershell
Set-IrmConfiguration -AzureRMSLicensingEnabled $true
```

Si votre organisation n’a pas encore installé Azure Information Protection, vous devez migrer d’AD RMS vers Azure Information Protection. Pour obtenir des instructions, [consultez La migration d’AD RMS vers Azure Information Protection.](https://docs.microsoft.com/azure/information-protection/migrate-from-ad-rms-to-azure-rms)

## <a name="side-by-side-comparison-of-features-and-capabilities"></a>Comparaison côte à côte des fonctionnalités et des fonctionnalités

|           **Situation**           | **Legacy OME**    | **IRM dans AD RMS**        | **Nouvelles fonctionnalités OME** |
|-----------------------------------|-------------------|-------------------|--------------------------|
|*Envoi d’un courrier chiffré*        |Via les règles de flux de messagerie Exchange|Utilisateur final initié à partir du bureau Outlook ou d’Outlook sur le Web ; ou via des règles de flux de messagerie Exchange|Utilisateur final initié à partir du bureau Outlook, d’Outlook pour Mac ou d’Outlook sur le Web ; via des règles de flux de messagerie Exchange (également appelées règles de transport) et la protection contre la perte de données (DLP)|
|*Modèle de gestion des droits*       |   S/O      |Option Ne pas forwarder et modèles personnalisés|Option Ne pas forwarder, Encrypt-Only option et modèles personnalisés|
|*Type de destinataire*                   |Destinataires internes et externes|Destinataires internes uniquement         |Destinataires internes et externes|
|*Expérience pour le destinataire interne*|Les destinataires reçoivent un message HTML qu’ils téléchargent et ouvrent dans un navigateur web ou une application mobile|Expérience inline native dans les clients Outlook|Expérience inline native pour les destinataires de la même organisation à l’aide des clients Outlook.  Les destinataires peuvent lire des messages à partir du portail OME à l’aide de clients autres qu’Outlook (aucun téléchargement ou application requis).|
|*Expérience pour un destinataire externe*|Les destinataires reçoivent un message HTML qu’ils téléchargent et ouvrent dans un navigateur web ou une application mobile|S/O|Expérience inline native pour les destinataires Microsoft 365. Tous les autres destinataires peuvent lire le message à partir du portail OME (aucun téléchargement ou application requis).|
|*Autorisations des pièces jointes*           |Aucune restriction sur les pièces jointes|Les pièces jointes sont protégées|Les pièces jointes sont protégées pour l’option Ne pas forwarder et les modèles personnalisés. Les administrateurs peuvent choisir si les pièces jointes de l’option Encrypt-Only sont protégées ou non.|
|*Prise en charge d’Apportez votre propre clé (BYOK)*|Aucun                |Aucun               |BYOK pris en charge          |
||

## <a name="advantages-of-the-new-ome-capabilities-over-legacy-ome"></a>Avantages des nouvelles fonctionnalités OME par rapport à l’OME hérité

Les nouvelles fonctionnalités offrent les avantages suivants :

- Possibilité d’utiliser Encrypt-Only (ce qui permet une collaboration sécurisée), Ne pas avancer et des restrictions personnalisées.
- Les expéditeurs peuvent envoyer des messages chiffrés avec les nouvelles fonctionnalités manuellement à partir des clients Outlook Desktop, Outlook pour Mac et Outlook sur le web.
- Les destinataires Microsoft 365 peuvent utiliser une expérience en ligne dans les clients Outlook pris en charge. Les administrateurs peuvent également choisir d’afficher aux destinataires Microsoft 365 une expérience de marque.
- Les comptes en dehors de Microsoft 365, tels que les comptes Gmail, Yahoo et Microsoft, sont fédérés avec le portail OME, qui offre une meilleure expérience utilisateur à ces destinataires. Toutes les autres identités utilisent un code de passe à usage seul pour accéder aux messages chiffrés.
- Les administrateurs peuvent personnaliser la personnalisation et créer plusieurs modèles de personnalisation.
- Les administrateurs peuvent révoquer les e-mails chiffrés avec les nouvelles fonctionnalités.
- Les nouvelles fonctionnalités fournissent des rapports d’utilisation détaillés via le Centre de &amp; conformité de sécurité.

## <a name="office-365-advanced-message-encryption-capabilities"></a>Fonctionnalités de chiffrement de messages avancée Office 365

Le chiffrement de messages avancé Office 365 offre des fonctionnalités supplémentaires en plus des nouvelles fonctionnalités OME. Les nouvelles fonctionnalités de chiffrement de messages Office 365 doivent être définies dans votre organisation pour pouvoir utiliser les fonctionnalités de chiffrement de messages avancées. En outre, pour utiliser ces fonctionnalités, les destinataires doivent afficher et répondre aux messages sécurisés via le portail OME. Les fonctionnalités avancées sont les suivantes :

- Révocation des messages

- Expiration du message

- Modèles de branding multiples

Le chiffrement de messages avancé Office 365 n’est pas pris en charge dans GCC High.

Pour plus d’informations sur l’utilisation du chiffrement de messages avancé, voir Chiffrement de messages avancé [Office 365.](ome-advanced-message-encryption.md)

## <a name="unique-characteristics-of-office-365-message-encryption-in-a-gcc-high-deployment"></a>Caractéristiques uniques du chiffrement de messages Office 365 dans un déploiement GCC High

Si vous envisagez d’utiliser le chiffrement de messages Office 365 dans un environnement GCC High, il existe certaines caractéristiques uniques concernant l’expérience du destinataire.

### <a name="encrypted-email-between-gcc-high-and-gcc-high-recipients"></a>Messages électroniques chiffrés entre les destinataires GCC High et GCC High

Les expéditeurs peuvent chiffrer manuellement les messages électroniques dans Outlook pour PC et Mac et Outlook sur le web, ou les organisations peuvent configurer une stratégie pour chiffrer les messages électroniques à l’aide de règles de flux de messagerie Exchange.

Les destinataires dans GCC High reçoivent la même expérience de lecture en ligne dans Outlook pour PC et Mac et Outlook sur le web que tous les autres utilisateurs.

### <a name="encrypted-email-between-gcc-high-and-non-gcc-high-recipients"></a>Messages électroniques chiffrés entre les destinataires GCC High et Non GCC High

Les expéditeurs dans GCC High peuvent envoyer des messages chiffrés en dehors de la limite GCC High et vice versa.

Tous les destinataires en dehors de GCC High, y compris les utilisateurs commerciaux de Microsoft 365, les utilisateurs Outlook.com et d’autres utilisateurs d’autres fournisseurs de messagerie tels que Gmail et Yahoo, reçoivent un message de wrapper. Ce message de wrapper redirige le destinataire vers le portail OME où le destinataire peut lire le message et y répondre. Cela est également vrai pour les expéditeurs en dehors de GCC High envoyant des messages chiffrés OME à GCC High.

## <a name="coexistence-of-legacy-ome-and-the-new-capabilities-in-the-same-tenant"></a>Coexistence de l’OME hérité et des nouvelles fonctionnalités dans le même client

Vous pouvez utiliser OME hérité et les nouvelles fonctionnalités dans le même client. En tant qu’administrateur, vous le faites en choisissant la version d’OME que vous souhaitez utiliser lorsque vous créez vos règles de flux de messagerie.

- Pour spécifier la version héritée d’OME, utilisez l’action de règle de flux de messagerie Exchange Appliquer la version précédente **d’OME**.

- Pour spécifier les nouvelles fonctionnalités, utilisez l’action de règle de flux de messagerie Exchange Appliquer le chiffrement de messages **Office 365 et la protection des droits.**

Les utilisateurs peuvent envoyer manuellement des messages chiffrés avec les nouvelles fonctionnalités d’Outlook Desktop, d’Outlook pour Mac et d’Outlook sur le web.

## <a name="migrate-from-legacy-ome-to-the-new-capabilities"></a>Migrer d’OME hérité vers les nouvelles fonctionnalités

Même si les deux versions d’OME peuvent coexister, nous vous recommandons vivement de modifier vos anciennes règles de flux de messagerie qui utilisent l’action de règle Appliquer la version précédente **d’OME** pour utiliser les nouvelles fonctionnalités. Mettez à jour ces règles pour utiliser l’action de règle de flux de messagerie Appliquer le chiffrement de **messages Office 365 et la protection des droits.** Pour obtenir des instructions, voir Définir des règles de flux de messagerie pour chiffrer les [messages électroniques dans Office 365.](define-mail-flow-rules-to-encrypt-email.md)

## <a name="get-started-with-ome"></a>Mise en place d’OME

En règle générale, les nouvelles fonctionnalités OME sont automatiquement activées pour votre organisation. Pour plus d’informations sur les nouvelles fonctionnalités OME au sein de votre organisation, voir Configurer les nouvelles fonctionnalités de chiffrement de [messages Office 365.](set-up-new-message-encryption-capabilities.md)

La version héritée d’OME est automatiquement activée pour votre organisation si vous avez activé Azure Information Protection. Dans le passé, l’OME hérité fonctionnait même si Azure Information Protection n’était pas activé. Ce n’est plus le cas.

Pour commencer à utiliser OME hérité, si vous avez activé Azure Information Protection, configurez des règles de flux de messagerie qui utilisent l’action de règle Appliquer la version précédente **d’OME**. Pour obtenir des instructions, voir [Définir des règles de flux de messagerie pour chiffrer les messages électroniques.](define-mail-flow-rules-to-encrypt-email.md)
