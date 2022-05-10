---
title: En savoir plus sur les obstacles aux informations
description: Découvrez les obstacles à l’information dans Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, conformité, obstacles à l’information
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 72a53580222b315f86fd397e391b026937b8035b
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65287175"
---
# <a name="learn-about-information-barriers"></a>En savoir plus sur les obstacles aux informations

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Les services de cloud computing Microsoft incluent des fonctionnalités enrichies de communication et de collaboration. Supposons toutefois que vous souhaitiez restreindre la communication et la collaboration entre deux groupes afin d’éviter qu’un conflit d’intérêts ne se produise dans votre organisation. Ou, peut-être souhaitez-vous restreindre la communication et la collaboration entre certaines personnes au sein de votre organisation afin de protéger les informations internes. Microsoft 365 permet la communication et la collaboration entre les groupes et les organisations. Existe-t-il donc un moyen de restreindre la communication et la collaboration entre des groupes d’utilisateurs spécifiques si nécessaire ? Avec Microsoft Purview Information Barriers (IB), vous pouvez !

Microsoft Teams, SharePoint Online et OneDrive Entreprise prennent en charge les obstacles à l’information. En supposant que votre [abonnement](#required-licenses-and-permissions) inclut des barrières à l’information, un administrateur de conformité ou un administrateur des obstacles à l’information peut définir des stratégies pour autoriser ou empêcher les communications entre des groupes d’utilisateurs dans Microsoft Teams. Les stratégies d’obstacle à l’information peuvent être utilisées pour des situations comme celles-ci :

- L’utilisateur du groupe de commerçants de jour ne doit pas communiquer ni partager de fichiers avec l’équipe marketing
- Le personnel financier travaillant sur des informations confidentielles de l’entreprise ne doit pas communiquer ou partager des fichiers avec certains groupes au sein de son organisation
- Une équipe interne avec du matériel de secret commercial ne doit pas appeler ou discuter en ligne avec des personnes de certains groupes au sein de leur organisation
- Une équipe de recherche doit uniquement appeler ou discuter en ligne avec une équipe de développement de produits
- Un site pour le groupe de commerçants de jour ne doit pas être partagé ou accessible par toute personne en dehors du groupe de commerçants de jour

> [!IMPORTANT]
> Les barrières à l’information ***ne prennent en charge que** les restrictions bidirectionnelle. Les restrictions d’une manière, telles que le marketing, peuvent communiquer et collaborer avec des commerçants de jour, mais les commerçants de jour ne peuvent pas communiquer et collaborer avec le marketing _*_n’est pas pris en charge_**.

Pour tous ces exemples de scénarios (et bien plus encore), des stratégies d’obstacle à l’information peuvent être définies pour empêcher ou autoriser les communications et la collaboration dans Microsoft Teams, SharePoint Online et OneDrive. De telles stratégies peuvent empêcher des personnes d’appeler ou de discuter avec celles qu’elles ne devraient pas, ou permettre aux personnes de communiquer uniquement avec des groupes spécifiques dans Microsoft Teams. Avec les stratégies d’obstacle à l’information en vigueur, chaque fois que les utilisateurs couverts par ces stratégies tentent de communiquer et de collaborer avec d’autres utilisateurs dans Microsoft Teams, SharePoint en ligne ou OneDrive des contrôles sont effectués pour empêcher (ou autoriser) la communication et la collaboration (comme défini par les stratégies d’obstacle à l’information).

Pour en savoir plus sur l’expérience utilisateur avec les obstacles à l’information, consultez :

- [Cloisonnement de l’information dans Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Obstacles à l’information dans SharePoint Online](/sharepoint/information-barriers)
- [Obstacles à l’information dans OneDrive](/onedrive/information-barriers)

> [!IMPORTANT]
> Actuellement, les obstacles à l’information ne s’appliquent pas aux communications par e-mail. En outre, les obstacles à l’information sont indépendants des [limites de conformité](set-up-compliance-boundaries.md).<p> Avant de définir et d’appliquer des stratégies d’obstacle à l’information, assurez-vous que votre organisation n’a pas [de stratégies de carnet d’adresses Exchange](/exchange/address-books/address-book-policies/address-book-policies) en vigueur. (Les obstacles à l’information sont basés sur des stratégies de carnet d’adresses.)

## <a name="what-happens-with-information-barriers"></a>Que se passe-t-il avec les obstacles à l’information ?

Lorsque des stratégies d’obstacle à l’information sont en place, les personnes qui ne doivent pas communiquer ou partager des fichiers avec d’autres utilisateurs spécifiques ne peuvent pas trouver, sélectionner, discuter ou appeler ces utilisateurs. Avec les obstacles à l’information, des contrôles sont en place pour empêcher toute communication et collaboration non autorisées.

Les obstacles à l’information s’appliquent aux Microsoft Teams (conversations et canaux), SharePoint En ligne et OneDrive. Dans Microsoft Teams, les stratégies de cloisonnement de l’information déterminent et bloquent les types suivants de communications non autorisées :

- Recherche d’un utilisateur
- Ajout d’un membre à une équipe
- Démarrage d’une session de conversation avec une personne
- Démarrage d’une conversation de groupe
- Inviter une personne à participer à une réunion
- Partage d’un écran
- Passer un appel
- Partage d’un fichier avec un autre utilisateur
- Accès au fichier via le lien de partage

Si les personnes impliquées sont incluses dans une stratégie de cloisonnement de l’information pour empêcher l’activité, elles ne pourront pas continuer. De plus, il est possible que les personnes incluses dans une stratégie de barrière des informations ne puissent pas communiquer avec d’autres personnes dans Microsoft Teams. Lorsque des personnes concernées par une stratégie de cloisonnement de l’information font partie de la même conversation de groupe ou d’équipe, il est possible qu’elles soient supprimées de ces sessions de conversation et que la communication avec le groupe ne soit pas autorisée.

Pour en savoir plus sur l’expérience utilisateur avec les obstacles à l’information, consultez [les obstacles à l’information dans Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams).

Dans SharePoint Online et OneDrive, les stratégies d’obstacle à l’information déterminent et empêchent les types de collaborations non autorisées suivants :

- Ajout d’un membre à un site
- Accès au site ou au contenu par un utilisateur
- Partage de site ou de contenu avec un autre utilisateur
- Recherche sur un site

Pour en savoir plus sur l’expérience utilisateur avec les obstacles à l’information, consultez [les obstacles à l’information dans SharePoint Online](/sharepoint/information-barriers)

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Avant de commencer à utiliser IB, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) et tous les modules complémentaires. Pour accéder à IB et l’utiliser, votre organisation doit disposer de l’un des abonnements ou modules complémentaires suivants :

- abonnement Microsoft 365 E5/A5 (version payante ou d’évaluation)
- abonnement Office 365 E5/A5/A3/A1 (version payante ou d’évaluation)
- Conformité avancée Office 365 module complémentaire (plus disponible pour les nouveaux abonnements)
- Microsoft 365 E3/A3/A1 + le module complémentaire conformité Microsoft 365 E5/A5
- Microsoft 365 E3/A3/A1 + le module complémentaire de gestion des risques internes Microsoft 365 E5/A5

Pour plus d’informations, consultez [Microsoft 365 conseils sur les licences pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

Pour [définir ou modifier des stratégies d’obstacle aux informations](information-barriers-policies.md), vous devez disposer de l’un des rôles suivants :

- Administrateur général Microsoft 365
- Administrateur général Office 365
- Administrateur de conformité
- Gestion de la conformité IB

(Pour en savoir plus sur les rôles et les autorisations, consultez [Autorisations dans le Office 365 Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).)

Vous devez être familiarisé avec les applets de commande PowerShell pour définir, valider ou modifier des stratégies d’obstacle aux informations. Bien que nous fournissions plusieurs exemples d’applets de commande PowerShell dans [l’article de procédure](information-barriers-policies.md), vous devez connaître d’autres détails, tels que des paramètres, pour votre organisation.

## <a name="next-steps"></a>Étapes suivantes

- [En savoir plus sur les obstacles à l’information dans Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [En savoir plus sur les obstacles à l’information dans SharePoint Online](/sharepoint/information-barriers)
- [En savoir plus sur les obstacles à l’information dans OneDrive](/onedrive/information-barriers)
- [Voir les attributs qui peuvent être utilisés pour les stratégies d’obstacle à l’information](information-barriers-attributes.md)
- [Définir des stratégies pour les obstacles à l’information](information-barriers-policies.md)
- [Modifier (ou supprimer) des stratégies de cloisonnement de l’information](information-barriers-edit-segments-policies.md)
