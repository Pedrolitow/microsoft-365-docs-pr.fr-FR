---
title: En savoir plus sur les obstacles aux informations Microsoft 365
description: Utilisez les obstacles à l’information pour assurer la conformité des communications à l Microsoft Teams au sein de votre organisation.
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
ms.openlocfilehash: 5baff70cb3318b05092e940e8160029bc2be69af
ms.sourcegitcommit: 7791c519bd8b68fc23433e13e1ecbdbeaddbebfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60725614"
---
# <a name="learn-about-information-barriers-in-microsoft-365"></a>En savoir plus sur les obstacles aux informations Microsoft 365

Les services de cloud computing Microsoft incluent des fonctionnalités enrichies de communication et de collaboration. Toutefois, supposons que vous vouliez restreindre la communication et la collaboration entre deux groupes pour éviter qu’un conflit d’intérêts ne se produise dans votre organisation. Ou, peut-être souhaitez-vous restreindre la communication et la collaboration entre certaines personnes au sein de votre organisation afin de protéger les informations internes. Microsoft 365 la communication et la collaboration entre les groupes et les organisations, existe-t-il un moyen de restreindre la communication et la collaboration entre des groupes d’utilisateurs spécifiques si nécessaire ? Avec les obstacles à l’information, vous pouvez !

Microsoft Teams, SharePoint Online et OneDrive Entreprise les obstacles aux informations. En [supposant](#required-licenses-and-permissions) que votre abonnement inclut des obstacles à l’information, un administrateur de conformité ou un administrateur des obstacles à l’information peut définir des stratégies pour autoriser ou empêcher les communications entre des groupes d’utilisateurs dans Microsoft Teams. Les stratégies de obstacle à l’information peuvent être utilisées dans des situations comme celles-ci :

- L’utilisateur du jour ne doit pas communiquer ou partager des fichiers avec l’équipe marketing
- Le personnel financier travaillant sur des informations confidentielles sur l’entreprise ne doit pas communiquer ou partager des fichiers avec certains groupes au sein de leur organisation
- Une équipe interne avec du matériel de secret commercial ne doit pas appeler ou discuter en ligne avec des personnes de certains groupes au sein de leur organisation
- Une équipe de recherche doit uniquement appeler ou discuter en ligne avec une équipe de développement de produits
- Un site pour le groupe d’informations d’une journée ne doit pas être partagé ou accessible par quiconque en dehors du groupe de veille du jour

> [!IMPORTANT]
> Obstacles à l’information ***prend uniquement en charge** les restrictions _ à double sens. Les restrictions à sens seul, telles que le marketing, peuvent communiquer et collaborer avec les courtiers du jour, mais les courtiers ne peuvent pas communiquer et collaborer avec marketing __*_ n’est pas pris en charge **.

Pour tous ces exemples de scénarios (et bien plus encore), des stratégies d’obstacle à l’information peuvent être définies pour empêcher ou autoriser les communications et la collaboration dans Microsoft Teams, SharePoint Online et OneDrive. De telles stratégies peuvent empêcher les personnes d’appeler ou de discuter avec celles qu’elles ne devraient pas, ou permettre aux utilisateurs de communiquer uniquement avec des groupes spécifiques Microsoft Teams. Avec les stratégies de obstacle à l’information en vigueur, chaque fois que les utilisateurs couverts par ces stratégies tentent de communiquer et de collaborer avec d’autres personnes dans Microsoft Teams, des vérifications SharePoint Online ou OneDrive sont réalisées pour empêcher (ou autoriser) la communication et la collaboration (telles que définies par les stratégies d’obstacle à l’information).

Pour en savoir plus sur l’expérience utilisateur avec les obstacles aux informations, voir :

- [Cloisonnement de l’information dans Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Obstacles aux informations dans SharePoint Online](/sharepoint/information-barriers)
- [Obstacles aux informations dans OneDrive](/onedrive/information-barriers)

> [!IMPORTANT]
> Actuellement, les obstacles à l’information ne s’appliquent pas aux communications par courrier électronique. En outre, les obstacles aux informations sont indépendants des [limites de conformité.](set-up-compliance-boundaries.md)<p> Avant de définir et d’appliquer des stratégies d’obstacle à l’information, assurez-vous que votre organisation Exchange stratégies de [carnet d’adresses en](/exchange/address-books/address-book-policies/address-book-policies) vigueur. (Les obstacles aux informations sont basés sur des stratégies de carnet d’adresses.)

## <a name="what-happens-with-information-barriers"></a>Que se passe-t-il avec les obstacles à l’information ?

Lorsque des stratégies de obstacle à l’information sont en place, les personnes qui ne doivent pas communiquer ou partager des fichiers avec d’autres utilisateurs spécifiques ne pourront pas trouver, sélectionner, discuter ou appeler ces utilisateurs. Avec les obstacles à l’information, des vérifications sont en place pour empêcher la communication et la collaboration non autorisées. 

Les obstacles à l’information s’appliquent Microsoft Teams (conversations et canaux), SharePoint Online et OneDrive. Dans Microsoft Teams, les stratégies de cloisonnement de l’information déterminent et bloquent les types suivants de communications non autorisées :

- Recherche d’un utilisateur
- Ajout d’un membre à une équipe
- Démarrage d’une session de conversation avec une personne
- Démarrage d’une conversation de groupe
- Inviter une personne à participer à une réunion
- Partage d’un écran
- Passer un appel
- Partage d’un fichier avec un autre utilisateur
- Accès au fichier via un lien de partage

Si les personnes impliquées sont incluses dans une stratégie de cloisonnement de l’information pour empêcher l’activité, elles ne pourront pas continuer. De plus, il est possible que les personnes incluses dans une stratégie de barrière des informations ne puissent pas communiquer avec d’autres personnes dans Microsoft Teams. Lorsque des personnes concernées par une stratégie de cloisonnement de l’information font partie de la même conversation de groupe ou d’équipe, il est possible qu’elles soient supprimées de ces sessions de conversation et que la communication avec le groupe ne soit pas autorisée.

Pour en savoir plus sur l’expérience utilisateur avec les obstacles à l’information, consultez les [obstacles aux](/MicrosoftTeams/information-barriers-in-teams)informations Microsoft Teams .

Dans SharePoint online et OneDrive, les stratégies d’obstacle à l’information déterminent et empêchent les types de collaborations non autorisées suivants :

- Ajout d’un membre à un site
- Accès au site ou au contenu par un utilisateur
- Partage de site ou de contenu avec un autre utilisateur
- Recherche sur un site

Pour en savoir plus sur l’expérience utilisateur avec les obstacles à [l’information,](/sharepoint/information-barriers) consultez la SharePoint Online

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Les obstacles à l’information sont en cours de déploiement et sont inclus dans les abonnements, tels que :

- Microsoft 365 E5/A5/A3/A1
- Office 365 E5/A5/A3/A1
- Conformité avancée Office 365
- Microsoft 365 Conformité E5/A5
- Microsoft 365 : gestion des risques internes

Pour plus d’informations, [voir Microsoft 365 licences pour la sécurité et & conformité.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)

Pour [définir ou modifier des stratégies de obstacle aux](information-barriers-policies.md)informations, vous devez avoir l’un des rôles suivants :

- Administrateur général Microsoft 365
- Administrateur général Office 365
- Administrateur de conformité
- Gestion de la conformité IB

(Pour en savoir plus sur les rôles et les [autorisations,](../security/office-365-security/permissions-in-the-security-and-compliance-center.md)voir Autorisations dans le Centre Office 365 sécurité et conformité &.)

Vous devez être familiarisé avec les cmdlets PowerShell pour définir, valider ou modifier des stratégies d’obstacle aux informations. Bien que nous fournissions plusieurs exemples d’cmdlets PowerShell dans [l’article](information-barriers-policies.md), vous devez connaître d’autres détails, tels que les paramètres, pour votre organisation.

## <a name="next-steps"></a>Prochaines étapes

- [En savoir plus sur les obstacles aux informations dans Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [En savoir plus sur les obstacles aux informations dans SharePoint Online](/sharepoint/information-barriers)
- [En savoir plus sur les obstacles aux informations dans OneDrive](/onedrive/information-barriers)
- [Voir les attributs qui peuvent être utilisés pour les stratégies de obstacle à l’information](information-barriers-attributes.md)
- [Définir des stratégies pour les obstacles à l’information](information-barriers-policies.md)
- [Modifier (ou supprimer) des stratégies de cloisonnement de l’information](information-barriers-edit-segments-policies.md)
