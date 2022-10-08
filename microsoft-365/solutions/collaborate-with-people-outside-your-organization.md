---
title: Collaborer avec des personnes extérieures à votre organisation
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- highpri
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
ms.openlocfilehash: 98ebf62386b948b97c888db23ae887635404ca6c
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67987299"
---
# <a name="collaborating-with-people-outside-your-organization"></a>Collaborer avec des personnes extérieures à votre organisation

Les fonctionnalités de partage externe dans Microsoft 365 permettent aux membres de votre organisation de collaborer avec des partenaires, des fournisseurs, des clients et d’autres personnes qui n’ont pas de compte dans votre annuaire. Vous pouvez partager des équipes, des canaux ou des sites entiers avec des personnes extérieures à votre organisation, ou simplement des fichiers individuels.

La collaboration avec des personnes extérieures à votre organisation se compose de ces principaux composants :

- **Activer le partage** : configurez les contrôles de partage sur Azure Active Directory, Teams, Groupes Microsoft 365 et SharePoint pour autoriser le niveau de partage souhaité pour votre organisation.
- **Configurer les relations organisationnelles** : si vous utilisez des canaux partagés, vous devez configurer les paramètres d’accès entre locataires dans Azure Active Directory pour autoriser l’accès direct B2B à la connexion pour chaque organisation avec laquelle vous souhaitez collaborer. (Ces organisations doivent également configurer les relations organisationnelles avec votre locataire.)
- **Activer une sécurité supplémentaire** - Bien que les fonctionnalités de partage de base puissent être configurées pour exiger que des personnes extérieures à votre organisation s’authentifient, Microsoft 365 fournit de nombreuses fonctionnalités supplémentaires de sécurité et de conformité pour vous aider à protéger vos données et à maintenir vos stratégies de gouvernance tout en partageant en externe.

Lisez [Configurer une collaboration sécurisée avec Microsoft 365 et Microsoft Teams](/microsoft-365/solutions/setup-secure-collaboration-with-teams) pour découvrir comment le partage externe est lié aux conseils généraux de collaboration microsoft 365.

## <a name="enable-sharing"></a>Activer le partage

Par défaut, le partage avec des personnes extérieures à votre organisation à l’aide de l’accès invité ou anonyme est activé, mais les canaux partagés doivent être activés en configurant les relations organisationnelles dans Azure AD. La plupart des scénarios de partage d’invités fonctionnent sans configuration supplémentaire. Pour confirmer les paramètres d’un scénario que vous utilisez ou en activer un nouveau, choisissez parmi les options suivantes :

- [Collaborer sur des documents](collaborate-on-documents.md) - Découvrez comment configurer Microsoft 365 pour permettre le partage et la collaboration avec des personnes extérieures à votre organisation (invités et utilisateurs non authentifiés) sur des fichiers et des dossiers.
- [Collaborer dans un site](collaborate-in-site.md) - Découvrez comment configurer Microsoft 365 pour permettre le partage de sites SharePoint avec des invités.
- [Collaborer en équipe](collaborate-as-team.md) - Découvrez comment configurer Microsoft 365 pour activer la collaboration des invités dans Teams.
- [Collaborez avec des participants externes dans un canal](/microsoft-365/solutions/collaborate-teams-direct-connect) pour collaborer avec des personnes extérieures à l’organisation dans un canal partagé.

Pour obtenir un aperçu complet des paramètres de partage d’invités disponibles dans Microsoft 365, consultez la [référence des paramètres de partage d’invités Microsoft 365](microsoft-365-guest-settings.md).

## <a name="enable-additional-security"></a>Activer une sécurité supplémentaire

Une fois que vous avez activé le scénario que vous souhaitez utiliser pour le partage avec des personnes extérieures à votre organisation, envisagez des mesures de protection supplémentaires pour protéger votre contenu contre un partage inapproprié accidentel ou intentionnel.

- [Meilleures pratiques pour le partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md) - Découvrez les meilleures pratiques de partage avec des utilisateurs non authentifiés.
- [Limiter l’exposition accidentelle](share-limit-accidental-exposure.md) - Découvrez comment réduire les risques de partage accidentel de contenu sensible avec des personnes extérieures à votre organisation.
- [Créer un environnement de partage d’invités sécurisé](create-secure-guest-sharing-environment.md) - Découvrez les outils fournis dans Microsoft 365 pour vous assurer que le partage avec des personnes extérieures à votre organisation est effectué de manière sécurisée et conforme à vos exigences de gouvernance.

## <a name="collaborate-with-partner-companies"></a>Collaborer avec des sociétés partenaires

Lorsque vous travaillez sur un grand projet qui implique des invités d’une autre organisation, envisagez des canaux partagés. Étant donné que les canaux partagés n’utilisent pas de comptes invités, les utilisateurs de l’autre organisation peuvent accéder directement au canal partagé sans avoir à se connecter à votre organisation séparément.

Si vous avez une relation de fournisseur en cours dans laquelle les invités changent souvent, vous pouvez utiliser la gestion des droits d’utilisation dans Azure Active Directory pour simplifier la gestion des invités et permettre à l’entreprise partenaire de partager cette responsabilité. Pour plus d’informations, consultez [Créer un extranet B2B avec des invités gérés](b2b-extranet.md) .

## <a name="limit-sharing"></a>Limiter le partage

Si certaines des fonctionnalités de partage de Microsoft 365 sont en conflit avec vos stratégies de gouvernance, consultez [Limiter le partage dans Microsoft 365](microsoft-365-limit-sharing.md) pour en savoir plus sur les options de limitation du partage.

## <a name="related-topics"></a>Voir aussi

[Introduction à la collaboration de fichiers dans Microsoft 365](/sharepoint/intro-to-file-collaboration)

[Planifier la collaboration de fichiers dans SharePoint avec Microsoft 365](/sharepoint/deploy-file-collaboration)
