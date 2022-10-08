---
title: En savoir plus sur les obstacles aux informations
description: Découvrez les obstacles à l’information dans Microsoft Purview. Les obstacles à l’information peuvent aider à éviter les conflits d’intérêts et à protéger les informations internes entre les utilisateurs et les domaines organisationnels.
keywords: Microsoft 365, Microsoft Purview, conformité, obstacles à l’information
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- highpri
- tier2
- purview-compliance
- m365solution-mip
- m365initiative-compliance
- highpri
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2c9bee62d8484c5fe8f096fb432955d2d04c00ed
ms.sourcegitcommit: 6df492719fecc2b213d55465dc1cd60ab4627ed6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68383847"
---
# <a name="learn-about-information-barriers"></a>En savoir plus sur les obstacles aux informations

Microsoft Purview Information Barriers (IB) est une solution de conformité qui vous permet de restreindre la communication bidirectionnelle et la collaboration entre les groupes et les utilisateurs dans Microsoft Teams, SharePoint et OneDrive. Souvent utilisé dans les secteurs hautement réglementés, IB peut aider à éviter les conflits d’intérêts et à protéger les informations internes entre les utilisateurs et les domaines organisationnels.

Lorsque des stratégies d’ib sont en place, les utilisateurs qui ne doivent pas communiquer ou partager des fichiers avec d’autres utilisateurs spécifiques ne peuvent pas trouver, sélectionner, discuter ou appeler ces utilisateurs. Les stratégies IB mettent automatiquement en place des contrôles pour détecter et empêcher toute communication et collaboration non autorisées entre des groupes et des utilisateurs définis. Les stratégies IB sont indépendantes des [limites de conformité](/microsoft-365/compliance/set-up-compliance-boundaries) pour les investigations eDiscovery qui contrôlent les emplacements de contenu utilisateur que les gestionnaires eDiscovery peuvent rechercher.

Les stratégies IB peuvent autoriser ou empêcher la communication et la collaboration entre les groupes et les utilisateurs pour les exemples de scénarios suivants :

- Les utilisateurs du groupe *Day Trader* ne doivent pas communiquer ni partager de fichiers avec l’équipe *marketing*
- Le personnel financier travaillant sur des informations confidentielles de l’entreprise ne doit pas communiquer ou partager des fichiers avec certains groupes au sein de son organisation
- Une équipe interne avec du matériel de secret commercial ne doit pas appeler ou discuter en ligne avec des personnes de certains groupes au sein de leur organisation
- Une équipe de recherche doit uniquement appeler ou discuter en ligne avec une équipe de développement de produits
- Un site SharePoint pour *le groupe Day Trader* ne doit pas être partagé ou accessible par quiconque en dehors du groupe *Day Trader*

> [!IMPORTANT]
> Les obstacles à **l’information prennent uniquement en charge** les restrictions de communication et de collaboration bidirectionnelle. Par exemple, un scénario où le marketing peut communiquer et collaborer avec Day Traders, mais où Day Traders ne peut pas communiquer et collaborer avec marketing **n’est pas pris en charge**.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="information-barriers-and-microsoft-teams"></a>Obstacles à l’information et Microsoft Teams

Dans Microsoft Teams, les stratégies IB déterminent et empêchent les types de communication et de collaboration non autorisés suivants :

- Recherche d’un utilisateur
- Ajout d’un membre à une équipe
- Démarrage d’une session de conversation avec une personne
- Démarrage d’une conversation de groupe
- Inviter une personne à participer à une réunion
- Partage d’un écran
- Passer un appel
- Partage d’un fichier avec un autre utilisateur
- Accès à un fichier via le partage d’un lien

Si les utilisateurs qui effectuent ces activités dans Microsoft Teams sont inclus dans une stratégie IB pour empêcher l’activité, ils ne pourront pas continuer. En outre, toutes les personnes incluses dans une stratégie d’ib peuvent être potentiellement empêchées de communiquer avec d’autres utilisateurs dans Microsoft Teams. Lorsque les personnes affectées par les stratégies d’IB font partie de la même conversation d’équipe ou de groupe, elles peuvent être supprimées de ces sessions de conversation et les communications avec le groupe peuvent ne pas être autorisées.

Pour plus d’informations, consultez [les obstacles à l’information dans Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams).

## <a name="information-barriers-and-sharepoint-and-onedrive"></a>Obstacles à l’information et SharePoint et OneDrive

Dans SharePoint et OneDrive, les stratégies IB détectent et empêchent les types de collaboration non autorisés suivants :

- Ajout d’un membre à un site
- Accès au site ou au contenu par un utilisateur
- Partage de site ou de contenu avec un autre utilisateur
- Recherche sur un site

Pour plus d’informations, consultez [Les obstacles à l’information dans SharePoint](/sharepoint/information-barriers) et [les obstacles à l’information dans OneDrive](/onedrive/information-barriers).

## <a name="information-barriers-and-exchange-online"></a>Obstacles à l’information et Exchange Online

Les stratégies IB ne sont pas disponibles pour restreindre la communication et la collaboration entre les groupes et les utilisateurs dans les messages électroniques. Les stratégies IB sont basées sur [Exchange Online stratégies de carnet d’adresses (APS).](/exchange/address-books/address-book-policies/address-book-policies) Les ABA permettent aux organisations d’affecter virtuellement des utilisateurs à des groupes spécifiques afin de fournir des vues personnalisées du carnet d’adresses global (GAL) de l’organisation. Lorsque des stratégies IB sont créées, les ABA pour les stratégies sont automatiquement créées. À mesure que les stratégies d’ib sont ajoutées dans votre organisation, la structure et le comportement de votre gal changeront pour se conformer aux stratégies IB.

Avant de définir et d’appliquer des stratégies IB, vous devez supprimer toutes les stratégies de carnet d’adresses Exchange existantes dans votre organisation. Les stratégies IB sont basées sur des stratégies de carnet d’adresses et les stratégies ABP existantes ne sont pas compatibles avec les ABA créées par IB. Pour supprimer vos stratégies de carnet d’adresses existantes, consultez [Supprimer une stratégie de carnet d’adresses dans Exchange Online](/exchange/address-books/address-book-policies/remove-an-address-book-policy). Une fois les stratégies IB activées et si vous avez activé le carnet d’adresses hiérarchique, tous les utilisateurs non inclus dans un segment IB voient le [carnet d’adresses hiérarchique](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) dans Exchange Online.

Seuls Exchange Online déploiements sont actuellement pris en charge pour les stratégies IB. Si votre organisation doit définir et contrôler les communications par e-mail, envisagez d’utiliser des [règles de flux de messagerie Exchange](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

- [Démarrer avec le cloisonnement de l’information](information-barriers-policies.md)
- [Gérer les stratégies IB](information-barriers-edit-segments-policies.md)
- [Voir les attributs qui peuvent être utilisés pour les stratégies IB](information-barriers-attributes.md)
