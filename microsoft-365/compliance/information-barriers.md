---
title: En savoir plus sur les barrières relatives aux informations dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
localization_priority: None
description: Utilisez les barrières relatives aux informations pour garantir la conformité de la communication à l’aide de Microsoft teams au sein de votre organisation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 08ec3b01258220a71ac02e5333143fb11b66655f
ms.sourcegitcommit: a0cddd1f888edb940717e434cda2dbe62e5e9475
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49613096"
---
# <a name="learn-about-information-barriers-in-microsoft-365"></a>En savoir plus sur les barrières relatives aux informations dans Microsoft 365

Les services de Cloud Computing Microsoft incluent de puissantes fonctionnalités de communication et de collaboration. Mais supposons que vous souhaitiez restreindre la communication et la collaboration entre deux groupes afin d’éviter un conflit d’intérêts au sein de votre organisation. Ou peut-être souhaitez-vous restreindre la communication et la collaboration entre certaines personnes au sein de votre organisation afin de protéger les informations internes. Microsoft 365 permet la communication et la collaboration entre les groupes et les organisations, de sorte qu’y a-t-il un moyen de restreindre la communication et la collaboration entre des groupes d’utilisateurs spécifiques lorsque cela est nécessaire ? Avec des barrières d’informations, vous pouvez le faire ! 

Les barrières d’informations sont désormais prises en charge dans Microsoft Teams, SharePoint Online et OneDrive entreprise. Si votre [abonnement](#required-licenses-and-permissions) inclut des barrières d’informations, un administrateur de conformité ou un administrateur des barrières de l’information peut définir des stratégies pour autoriser ou empêcher les communications entre les groupes d’utilisateurs dans Microsoft Teams. Les stratégies de barrière des informations peuvent être utilisées pour des situations comme celles-ci :

- L’utilisateur dans le groupe de la journée du commerçant ne doit pas communiquer ou partager des fichiers avec l’équipe marketing
- Le personnel financier travaillant sur les informations confidentielles de l’entreprise ne doit pas communiquer ou partager des fichiers avec certains groupes au sein de son organisation
- Une équipe interne avec des éléments secrets commerciaux ne doit pas appeler ou converser en ligne avec des personnes appartenant à certains groupes au sein de leur organisation
- Une équipe de recherche doit uniquement appeler ou converser en ligne avec une équipe de développement de produit

> [!IMPORTANT]
> Barrières relatives aux informations ***ne prend en charge que** les restrictions de deux façons. Les restrictions d’une seule manière, telles que marketing, peuvent communiquer avec les commerçants, mais les jours où le service marketing ne peut pas communiquer ne _sont pas pris en charge_* *.

Pour tous ces exemples de scénarios (et plus), des stratégies de barrière des informations peuvent être définies pour empêcher ou autoriser les communications dans Microsoft Teams. De telles stratégies peuvent empêcher les personnes d’appeler ou de converser avec celles qu’ils ne doivent pas utiliser, ou d’autoriser les utilisateurs à communiquer uniquement avec des groupes spécifiques dans Microsoft Teams. Avec des stratégies de barrière des informations en vigueur, chaque fois que des utilisateurs couverts par ces stratégies tentent de communiquer avec d’autres personnes dans Microsoft Teams, des vérifications sont effectuées pour empêcher (ou autoriser) la communication (comme défini par les stratégies de barrière des informations). Pour en savoir plus sur l’expérience utilisateur avec des barrières d’informations, consultez la rubrique [barrières relatives aux informations dans Microsoft teams](https://docs.microsoft.com/MicrosoftTeams/information-barriers-in-teams).

> [!IMPORTANT]
> Actuellement, les barrières d’informations ne s’appliquent pas aux communications par courrier électronique. En outre, les barrières de l’information sont indépendantes des [limites de conformité](set-up-compliance-boundaries.md).<p>Avant de définir et d’appliquer des stratégies de barrière des informations, assurez-vous que votre organisation ne dispose pas des [stratégies de carnet d’adresses Exchange](https://docs.microsoft.com/exchange/address-books/address-book-policies/address-book-policies) en vigueur. (Les barrières d’informations sont basées sur les stratégies de carnet d’adresses.) 

## <a name="what-happens-with-information-barriers"></a>Qu’en est-il des barrières de l’information ?

Lorsque des stratégies de barrière des informations sont en place, les personnes qui ne doivent pas communiquer ou partager des fichiers avec d’autres utilisateurs spécifiques ne peuvent pas trouver, sélectionner, converser ou appeler ces utilisateurs. Grâce aux obstacles aux informations, des vérifications sont en place pour empêcher toute communication non autorisée.

Initialement, les barrières relatives aux informations s’appliquent aux conversations et canaux Microsoft teams uniquement. Dans Microsoft Teams, les stratégies de cloisonnement de l’information déterminent et bloquent les types suivants de communications non autorisées :

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

Pour en savoir plus sur l’expérience utilisateur avec des barrières d’informations, consultez la rubrique [barrières relatives aux informations dans Microsoft teams](https://docs.microsoft.com/MicrosoftTeams/information-barriers-in-teams).

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Les barrières de l’information se dérouleront maintenant et sont incluses dans les abonnements, telles que :

- Microsoft 365 E5/a5
- Office 365 E5/a5
- Conformité avancée Office 365
- Conformité Microsoft 365 E5/a5
- Gestion des risques Microsoft 365 Insider

Pour plus d’informations, consultez [la rubrique solutions de conformité](https://products.office.com/business/security-and-compliance/compliance-solutions).

Pour [définir ou modifier des stratégies de barrière des informations](information-barriers-policies.md), vous devez disposer de l’un des rôles suivants :

- Administrateur général Microsoft 365
- Administrateur général Office 365
- Administrateur de conformité
- IB gestion de la conformité (il s’agit d’un nouveau rôle !)

(Pour en savoir plus sur les rôles et les autorisations, consultez [la rubrique autorisations dans le centre de conformité des & de sécurité Office 365](../security/office-365-security/protect-against-threats.md).)

Vous devez être familiarisé avec les applets de commande PowerShell pour définir, valider ou modifier des stratégies de barrière des informations. Bien que nous fournissons plusieurs exemples d’applets de commande PowerShell dans l' [article de procédure](information-barriers-policies.md), vous devez connaître les détails supplémentaires, tels que les paramètres, pour votre organisation.

## <a name="next-steps"></a>Étapes suivantes

- [En savoir plus sur les barrières d’informations dans Microsoft teams](https://docs.microsoft.com/MicrosoftTeams/information-barriers-in-teams)
- [Voir les attributs pouvant être utilisés pour les stratégies de barrière des informations](information-barriers-attributes.md)
- [Définir des stratégies pour les barrières des informations](information-barriers-policies.md)
- [Modifier (ou supprimer) des stratégies de cloisonnement de l’information](information-barriers-edit-segments-policies.md)
- [En savoir plus sur les barrières relatives aux informations dans SharePoint Online](https://docs.microsoft.com/sharepoint/information-barriers)
- [En savoir plus sur les barrières d’informations dans OneDrive entreprise](https://docs.microsoft.com/onedrive/information-barriers)