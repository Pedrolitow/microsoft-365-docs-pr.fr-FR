---
title: Collaborer avec des personnes extérieures à votre organisation
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Découvrez comment configurer des applications Microsoft 365 comme Teams, OneDrive et SharePoint pour la collaboration avec des personnes extérieures à votre organisation.
ms.openlocfilehash: 65511cbafdc1f5a666c11e1bef7fefd6e6852ee3
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63712771"
---
# <a name="collaborating-with-people-outside-your-organization"></a>Collaborer avec des personnes extérieures à votre organisation

Les fonctionnalités de partage externe dans Microsoft 365 permettent aux membres de votre organisation de collaborer avec des partenaires, des fournisseurs, des clients et d’autres personnes qui n’ont pas de compte dans votre annuaire. Vous pouvez partager des équipes, des canaux ou des sites entiers avec des personnes extérieures à votre organisation, ou simplement des fichiers individuels.

La collaboration avec des personnes extérieures à votre organisation comprend les principaux composants ci-après :

- **Activer le** partage : configurez les contrôles de partage entre Azure Active Directory, Teams, Microsoft 365 Groupes et SharePoint pour autoriser le niveau de partage voulu pour votre organisation.
- **Configurer** les relations organisationnelles : si vous utilisez des canaux partagés, vous devez configurer les paramètres d’accès entre clients dans Azure Active Directory pour autoriser l’accès B2B à la connexion directe pour chaque organisation avec qui vous souhaitez collaborer. (Ces organisations doivent également configurer les relations organisationnelles avec votre client.)
-  Activer une sécurité supplémentaire : alors que les fonctionnalités de partage de base peuvent être configurées pour exiger l’authentification des personnes extérieures à votre organisation, Microsoft 365 fournit de nombreuses fonctionnalités de sécurité et de conformité supplémentaires pour vous aider à protéger vos données et à maintenir vos stratégies de gouvernance tout en partageant en externe.

[Lisez Configurer la collaboration sécurisée avec Microsoft 365 et Microsoft Teams](/microsoft-365/solutions/setup-secure-collaboration-with-teams) pour découvrir comment le partage externe est lié à l’ensemble des Microsoft 365 de collaboration.

## <a name="enable-sharing"></a>Activer le partage

Par défaut, le partage avec des personnes extérieures à votre organisation à l’aide de l’accès invité ou de l’accès anonyme est activé, mais les canaux partagés doivent être activés en configurant les relations organisationnelles dans Azure AD. La plupart des scénarios de partage d’invités fonctionnent sans configuration supplémentaire. Pour confirmer les paramètres d’un scénario que vous utilisez ou en activer un nouveau, choisissez l’une des options suivantes :

- [Collaborer sur des documents](collaborate-on-documents.md) : découvrez comment configurer Microsoft 365 pour autoriser le partage et la collaboration avec des personnes extérieures à votre organisation (invités et utilisateurs non authentifiés) sur des fichiers et des dossiers.
- [Collaborer dans un site](collaborate-in-site.md) : découvrez comment configurer des Microsoft 365 pour activer le partage SharePoint sites avec des invités.
- [Collaborer en équipe](collaborate-as-team.md) : découvrez comment configurer des Microsoft 365 pour activer la collaboration d’invités dans Teams.
- [Collaborer avec des participants externes dans un canal pour](/microsoft-365/solutions/collaborate-teams-direct-connect) collaborer avec des personnes extérieures à l’organisation dans un canal partagé.

Pour obtenir un aperçu complet des paramètres de partage d’invités disponibles dans Microsoft 365, voir Microsoft 365 [des paramètres de partage d’invités](microsoft-365-guest-settings.md).

## <a name="enable-additional-security"></a>Activer la sécurité supplémentaire

Une fois que vous avez activé le scénario que vous souhaitez utiliser pour le partage avec des personnes extérieures à votre organisation, envisagez des protections supplémentaires pour protéger votre contenu contre un partage accidentel ou intentionnel.

- [Meilleures pratiques pour le partage](best-practices-anonymous-sharing.md) de fichiers et de dossiers avec des utilisateurs non authentifiés : découvrez les meilleures pratiques de partage avec des utilisateurs non authentifiés.
- [Limiter l’exposition](share-limit-accidental-exposure.md) accidentelle : découvrez comment réduire les risques de partager accidentellement du contenu sensible avec des personnes extérieures à votre organisation.
- [](create-secure-guest-sharing-environment.md) Créez un environnement de partage d’invités sécurisé : découvrez les outils fournis dans Microsoft 365 pour vous assurer que le partage avec des personnes extérieures à votre organisation est effectué de manière sécurisée et répond à vos exigences de gouvernance.

## <a name="collaborate-with-partner-companies"></a>Collaborer avec des entreprises partenaires

Lorsque vous travaillez sur un grand projet qui implique des invités d’une autre organisation, envisagez des canaux partagés. Étant donné que les canaux partagés n’utilisent pas de comptes invités, les utilisateurs de l’autre organisation peuvent accéder directement au canal partagé sans avoir à se connecter séparément à votre organisation.

Si vous avez une relation de fournisseur en cours dans laquelle les invités changent souvent, vous pouvez utiliser la gestion des droits dans Azure Active Directory pour simplifier la gestion des invités et permettre à la société partenaire de partager cette responsabilité. Pour [plus d’informations, voir Créer un extranet B2B](b2b-extranet.md) avec des invités gérés.

## <a name="limit-sharing"></a>Limiter le partage

Si certaines fonctionnalités de partage dans Microsoft 365 entrent en conflit avec vos stratégies de gouvernance, voir Limiter le partage dans [Microsoft 365](microsoft-365-limit-sharing.md) pour en savoir plus sur les options de limitation du partage.

## <a name="related-topics"></a>Sujets associés

[Introduction à la collaboration sur les fichiers dans Microsoft 365](/sharepoint/intro-to-file-collaboration)

[Planifier la collaboration de fichiers SharePoint avec Microsoft 365](/sharepoint/deploy-file-collaboration)
