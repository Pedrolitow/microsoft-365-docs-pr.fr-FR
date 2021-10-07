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
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Cet article explique les différences entre les différentes versions de chiffrement de messages Office 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 508a129cd472c8843e2af4a012560b17a44c49aa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60194344"
---
# <a name="compare-versions-of-ome"></a>Comparez les versions de OME

> [!IMPORTANT]
> Le 28 février 2021, Microsoft a supprimé la prise en charge d’AD RMS dans Exchange Online. Si vous avez déployé un environnement hybride dans lequel vos boîtes aux lettres Exchange sont en ligne et que vous utilisez irm avec Active Directory RMS en local, vous devez migrer vers Azure. Les organisations qui ont été déployées dans l Cloud de la communauté du secteur public environnement modéré sont également affectées. Voir « Vue d’ensemble de l’Exchange Online AD RMS » dans cet article pour plus d’informations.

Le reste de cet article compare les chiffrement de messages Office 365 héritées (OME) aux nouvelles fonctionnalités et fonctionnalités OME Chiffrement avancé de messages Office 365. Les nouvelles fonctionnalités sont une fusion et une version plus récente d’OME et de la Gestion des droits de l’information (IRM). Les caractéristiques uniques du déploiement dans Cloud de la communauté du secteur public Élevé sont également décrites. Les deux peuvent coexister dans votre organisation. Pour plus d’informations sur le fonctionnement des nouvelles fonctionnalités, [voir chiffrement de messages Office 365 (OME).](ome.md)

Cet article fait partie d’une série plus importante d’articles sur chiffrement de messages Office 365. Cet article est destiné aux administrateurs et aux itpros. Si vous recherchez simplement des informations sur l’envoi ou la réception d’un message chiffré, consultez la liste des articles dans [chiffrement de messages Office 365 (OME)](ome.md) et recherchez l’article qui répond le mieux à vos besoins.

## <a name="overview-of-ad-rms-deprecation-in-exchange-online"></a>Vue d’ensemble de l’utilisation d’AD RMS dans Exchange Online

Exchange Online inclut la fonctionnalité Gestion des droits de l’information (IRM) qui fournit une protection en ligne et hors connexion des messages électroniques et des pièces jointes. Par défaut, Exchange Online utilise Azure Information Protection. Toutefois, votre organisation a peut-être configuré Exchange Online IRM pour utiliser le service AD RMS (Active Directory Rights Management Service) local. La prise en charge d’AD RMS Exchange Online est en cours de retrait. Au lieu de cela, Azure Information Protection remplacera entièrement AD RMS.

Pour évaluer si cette désintégrement a un impact sur votre organisation, voir Comment migrer [AD RMS vers Azure RMS dans Exchange Online](/exchange/troubleshoot/administration/migrate-ad-rms-to-azure). Cet article fournit des recommandations sur les options de migration.

## <a name="side-by-side-comparison-of-ome-features-and-capabilities"></a>Comparaison côte à côte des fonctionnalités et fonctionnalités OME

|           **Situation**           | **Legacy OME**    | **IRM dans AD RMS**        | **Nouvelles fonctionnalités OME** |
|-----------------------------------|-------------------|-------------------|--------------------------|
|*Envoi d’un courrier chiffré*        |Par le Exchange règles de flux de messagerie|l’utilisateur final initié à partir Outlook bureau ou Outlook sur le Web ; ou par le biais Exchange règles de flux de messagerie|Utilisateur final initié à partir Outlook bureau, Outlook pour Mac ou Outlook sur le Web ; via Exchange règles de flux de messagerie (également appelées règles de transport) et la protection contre la perte de données (DLP)|
|*Modèle de gestion des droits*       |   S/O      |Option Ne pas forwarder et modèles personnalisés|Option Ne pas forwarder, option chiffrer uniquement et modèles personnalisés|
|*Type de destinataire*                   |Destinataires internes et externes|Destinataires internes uniquement         |Destinataires internes et externes|
|*Expérience pour le destinataire interne*|Les destinataires reçoivent un message HTML qu’ils téléchargent et ouvrent dans un navigateur web ou une application mobile|Expérience inline native dans Outlook clients|Expérience inline native pour les destinataires de la même organisation utilisant Outlook clients.  Les destinataires peuvent lire les messages à partir du portail OME à l’aide de clients autres que Outlook (aucun téléchargement ni aucune application n’est requis).|
|*Expérience pour un destinataire externe*|Les destinataires reçoivent un message HTML qu’ils téléchargent et ouvrent dans un navigateur web ou une application mobile|S/O|Expérience inline native pour Microsoft 365 destinataires. Tous les autres destinataires peuvent lire le message à partir du portail OME (aucun téléchargement ou application requis).|
|*Autorisations des pièces jointes*           |Aucune restriction sur les pièces jointes|Les pièces jointes sont protégées|Les pièces jointes sont protégées pour l’option Ne pas forwarder et les modèles personnalisés. Les administrateurs peuvent choisir si les pièces jointes de l’option de chiffrement uniquement sont protégées ou non.|
|*Prise en charge d’Apportez votre propre clé (BYOK)*|Aucun                |Aucun               |BYOK pris en charge          |
||

## <a name="advantages-of-the-new-ome-capabilities-over-legacy-ome"></a>Avantages des nouvelles fonctionnalités OME par rapport à l’OME hérité

Les nouvelles fonctionnalités offrent les avantages suivants :

- Possibilité d’utiliser l’option de chiffrement uniquement (qui permet une collaboration sécurisée), l’option Ne pas forwarder et les restrictions personnalisées.
- Les expéditeurs peuvent envoyer des messages chiffrés avec les nouvelles fonctionnalités manuellement à partir de Outlook bureau, Outlook pour Mac et Outlook sur le web clients.
- Microsoft 365 les destinataires peuvent utiliser une expérience en ligne dans les clients Outlook pris en charge. Les administrateurs peuvent également choisir d’Microsoft 365 aux destinataires une expérience de marque.
- Les comptes en dehors de Microsoft 365, tels que les comptes Gmail, Yahoo et Microsoft, sont fédérés avec le portail OME, qui offre une meilleure expérience utilisateur à ces destinataires. Toutes les autres identités utilisent un code de passe à usage seul pour accéder aux messages chiffrés.
- Les administrateurs peuvent personnaliser la personnalisation et créer plusieurs modèles de personnalisation.
- Les administrateurs peuvent révoquer les e-mails chiffrés avec les nouvelles fonctionnalités.
- Les nouvelles fonctionnalités fournissent des rapports d’utilisation détaillés via le Centre de &amp; conformité de sécurité.

## <a name="office-365-advanced-message-encryption-capabilities"></a>Chiffrement avancé de messages Office 365 fonctionnalités

Chiffrement avancé de messages Office 365 offre des fonctionnalités supplémentaires en plus des nouvelles fonctionnalités OME. Les nouvelles fonctionnalités de chiffrement de messages Office 365 de votre organisation doivent être définies pour pouvoir utiliser les fonctionnalités de chiffrement de messages avancées. En outre, pour utiliser ces fonctionnalités, les destinataires doivent afficher et répondre aux messages sécurisés via le portail OME. Les fonctionnalités avancées sont les suivantes :

- Révocation des messages

- Expiration du message

- Modèles de branding multiples

Chiffrement avancé de messages Office 365 n’est pas pris en charge dans Cloud de la communauté du secteur public High.

Pour plus d’informations sur l’utilisation du chiffrement de messages avancé, [voir Chiffrement avancé de messages Office 365](ome-advanced-message-encryption.md).

## <a name="unique-characteristics-of-office-365-message-encryption-in-a-gcc-high-deployment"></a>Caractéristiques uniques des chiffrement de messages Office 365 dans un déploiement Cloud de la communauté du secteur public déploiement élevé

Si vous prévoyez d’utiliser chiffrement de messages Office 365 dans un environnement Cloud de la communauté du secteur public élevé, il existe certaines caractéristiques uniques concernant l’expérience du destinataire.

### <a name="encrypted-email-between-gcc-high-and-gcc-high-recipients"></a>Messages électroniques chiffrés entre Cloud de la communauté du secteur public destinataires élevés Cloud de la communauté du secteur public élevés

Les expéditeurs peuvent chiffrer manuellement les messages électroniques dans Outlook pour PC et Mac et Outlook sur le web, ou les organisations peuvent configurer une stratégie pour chiffrer les messages électroniques à l’aide de Exchange règles de flux de messagerie.

Les destinataires dans Cloud de la communauté du secteur public High bénéficient de la même expérience de lecture en ligne dans Outlook pour PC et Mac et Outlook sur le web que tous les autres utilisateurs.

### <a name="encrypted-email-between-gcc-high-and-non-gcc-high-recipients"></a>Messages électroniques chiffrés entre Cloud de la communauté du secteur public destinataires élevés et non Cloud de la communauté du secteur public élevés

Les expéditeurs à l Cloud de la communauté du secteur public élevé peuvent envoyer des messages chiffrés en dehors de la limite Cloud de la communauté du secteur public limite élevée et inversement.

Tous les destinataires en dehors de Cloud de la communauté du secteur public Élevé, y compris les utilisateurs Microsoft 365 commerciaux, les utilisateurs Outlook.com et les autres utilisateurs d’autres fournisseurs de messagerie tels que Gmail et Yahoo, reçoivent un wrapper. Ce message de wrapper redirige le destinataire vers le portail OME où le destinataire peut lire le message et y répondre. Cela est également vrai pour les expéditeurs en dehors Cloud de la communauté du secteur public’envoi élevé de messages chiffrés OME Cloud de la communauté du secteur public Élevé.

## <a name="coexistence-of-legacy-ome-and-the-new-capabilities-in-the-same-tenant"></a>Coexistence de l’OME hérité et des nouvelles fonctionnalités dans le même client

Vous pouvez utiliser OME hérité et les nouvelles fonctionnalités dans le même client. En tant qu’administrateur, vous le faites en choisissant la version d’OME que vous souhaitez utiliser lorsque vous créez vos règles de flux de messagerie.

- Pour spécifier la version héritée d’OME, utilisez l’action Exchange règle de flux de messagerie Appliquer la version précédente **d’OME**.

- Pour spécifier les nouvelles fonctionnalités, utilisez l’action Exchange règle de flux de messagerie **s’appliquer chiffrement de messages Office 365 protection des droits.**

Les utilisateurs peuvent envoyer manuellement des messages chiffrés avec les nouvelles fonctionnalités à partir de Outlook Bureau, Outlook pour Mac et Outlook sur le web.

## <a name="migrate-from-legacy-ome-to-the-new-capabilities"></a>Migrer d’OME hérité vers les nouvelles fonctionnalités

Même si les deux versions d’OME peuvent coexister, nous vous recommandons vivement de modifier vos anciennes règles de flux de messagerie qui utilisent l’action de règle Appliquer la version précédente **d’OME** pour utiliser les nouvelles fonctionnalités. Mettez à jour ces règles pour utiliser l’action de règle de flux de messagerie **Appliquer chiffrement de messages Office 365 protection des droits**. Pour obtenir des instructions, voir Définir des règles de flux de messagerie [pour chiffrer](define-mail-flow-rules-to-encrypt-email.md)les messages électroniques Office 365 .

## <a name="get-started-with-ome"></a>Mise en place d’OME

En règle générale, les nouvelles fonctionnalités OME sont automatiquement activées pour votre organisation. Pour plus d’informations sur les nouvelles fonctionnalités OME au sein de votre organisation, voir [Configurer de chiffrement de messages Office 365 nouvelles fonctionnalités.](set-up-new-message-encryption-capabilities.md)

La version héritée d’OME est automatiquement activée pour votre organisation si vous avez activé Azure Information Protection. Dans le passé, l’OME hérité fonctionnait même si Azure Information Protection n’était pas activé. Ce n’est plus le cas.

Pour commencer à utiliser OME hérité, si vous avez activé Azure Information Protection, configurez des règles de flux de messagerie qui utilisent l’action de règle Appliquer la version précédente **d’OME**. Pour obtenir des instructions, voir [Définir des règles de flux de messagerie pour chiffrer les messages électroniques.](define-mail-flow-rules-to-encrypt-email.md)
