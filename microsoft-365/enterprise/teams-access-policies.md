---
title: Stratégies de teams recommandées-Microsoft 365 pour les entreprises | Microsoft docs
description: Décrit les stratégies pour les recommandations de Microsoft relatives à la sécurisation des communications et de l’accès aux fichiers des équipes.
author: MicrosoftHeidi
manager: serdars
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: heidip
ms.date: 09/30/2020
ms.reviewer: anmorgan
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.openlocfilehash: b9a9044a063c01724710679682e1edbe458dec0f
ms.sourcegitcommit: 04c4252457d9b976d31f53e0ba404e8f5b80d527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "48327133"
---
# <a name="policy-recommendations-for-securing-teams-chats-groups-and-files"></a>Recommandations de stratégie pour la sécurisation des conversations, des groupes et des fichiers teams

Cet article explique comment implémenter les stratégies d’identité et d’accès aux appareils recommandées pour protéger les conversations, les groupes et le contenu de Microsoft Teams, tels que les fichiers et les calendriers. Ce guide s’appuie sur les [stratégies courantes d’identité et d’accès aux appareils](identity-access-policies.md), avec des informations supplémentaires spécifiques à Teams. Étant donné que teams s’intègre à nos autres produits, reportez-vous à la rubrique [stratégies recommandées pour sécuriser les sites et les fichiers SharePoint](sharepoint-file-access-policies.md) , ainsi que [les recommandations en matière de sécurisation](secure-email-recommended-policies.md)

Ces recommandations sont basées sur trois niveaux différents de sécurité et de protection pour les équipes qui peuvent être appliquées en fonction de la granularité de vos besoins : planification, sensible et hautement réglementé. Vous pouvez en savoir plus sur ces niveaux de sécurité et les stratégies recommandées référencées par ces recommandations dans les [configurations d’identité et d’accès aux appareils](microsoft-365-policies-configurations.md).

D’autres recommandations spécifiques au déploiement de teams sont incluses dans cet article pour aborder des cas d’authentification spécifiques, y compris pour les utilisateurs extérieurs à votre organisation. Vous devrez suivre ces instructions pour une expérience de sécurité complète.

## <a name="getting-started-with-teams-before-other-dependent-services"></a>Prise en main de teams avant les autres services dépendants

Vous n’avez pas besoin d’activer les services dépendants pour commencer à utiliser Microsoft Teams. Cela fonctionnera tout simplement. Toutefois, vous devez être prêt à gérer les éléments suivants :

- Groupes Microsoft 365
- Sites d’équipe SharePoint
- OneDrive Entreprise
- Les boîtes aux lettres Exchange
- Diffuser des vidéos et des plans du planificateur (si ces services sont activés)

## <a name="updating-common-policies-to-include-teams"></a>Mise à jour de stratégies communes pour inclure teams

Pour protéger la conversation, les groupes et le contenu dans Teams, le diagramme suivant illustre les stratégies à mettre à jour à partir des stratégies courantes d’identité et d’accès aux appareils. Pour chaque stratégie à mettre à jour, assurez-vous que les services teams et dépendants sont inclus dans l’affectation d’applications Cloud.

[![Résumé des mises à jour de stratégie pour protéger l’accès à teams et à ses services dépendants](../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png)

[Afficher une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png)

Il s’agit des services dépendants à inclure dans l’affectation d’applications Cloud pour teams :

- Microsoft Teams
- SharePoint et OneDrive Entreprise
- Exchange Online
- Skype Entreprise Online
- Microsoft Stream (enregistrements de réunions)
- Planificateur Microsoft (tâches du planificateur et données de plan)

Ce tableau répertorie les stratégies qui doivent être revisitées, ainsi que les liens vers chaque stratégie dans les [stratégies d’identité et d’accès aux appareils communes](identity-access-policies.md), dont la stratégie plus large est définie pour toutes les applications Office.

|Niveau de protection|Stratégies|Informations supplémentaires pour l’implémentation de teams|
|:---------------|:-------|:----------------|
|**Baseline**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Assurez-vous que les équipes et les services dépendants sont inclus dans la liste des applications. Les équipes disposent également d’un accès invité et de règles d’accès externe à prendre en compte pour en savoir plus à ce sujet plus loin dans cet article.|
|        |[Bloquer les clients ne prenant pas en charge l’authentification moderne](identity-access-policies.md#block-clients-that-dont-support-modern-authentication)|Incluez les équipes et les services dépendants dans l’affectation d’applications Cloud.|
|        |[Les utilisateurs à risque élevé doivent modifier leur mot de passe](identity-access-policies.md#high-risk-users-must-change-password)|Force les utilisateurs de teams à modifier leur mot de passe lors de la connexion si une activité à haut risque est détectée pour leur compte. Assurez-vous que les équipes et les services dépendants sont inclus dans la liste des applications.|
|        |[Appliquer des stratégies de protection des données d’application](identity-access-policies.md#apply-app-data-protection-policies)|Assurez-vous que les équipes et les services dépendants sont inclus dans la liste des applications. Mettez à jour la stratégie pour chaque plateforme (iOS, Android, Windows).|
|        |[Définir les stratégies de conformité des appareils](identity-access-policies.md#define-device-compliance-policies)|Incluez les équipes et les services dépendants dans cette stratégie.|
|        |[Exiger des PC conformes](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Incluez les équipes et les services dépendants dans cette stratégie.|
|**Sensible**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *faible*, *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Les équipes disposent également d’un accès invité et de règles d’accès externe à prendre en compte pour en savoir plus à ce sujet plus loin dans cet article. Incluez les équipes et les services dépendants dans cette stratégie.|
|         |[Exiger des PC conformes *et des* appareils mobiles](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Incluez les équipes et les services dépendants dans cette stratégie.|
|**Hautement réglementé**|[*Toujours* exiger l’authentification multifacteur](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Quelle que soit l’identité de l’utilisateur, l’authentification multifacteur sera utilisée par votre organisation. Incluez les équipes et les services dépendants dans cette stratégie. |
| | |

## <a name="teams-dependent-services-architecture"></a>Architecture des services dépendants de teams

Pour référence, le diagramme suivant illustre la façon dont les équipes des services s’appuient sur. Pour plus d’informations et des illustrations supplémentaires, consultez [la rubrique Microsoft teams et les services de productivité associés dans microsoft 365 pour les architectes informatiques](../solutions/productivity-illustrations.md).

[![Diagramme illustrant les dépendances de teams sur SharePoint, OneDrive entreprise et Exchange](../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png)

[Afficher une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png)

## <a name="guest-and-external-access-for-teams"></a>Accès invité et externe pour teams

Microsoft teams définit les éléments suivants :

- L' **accès invité** utilise un compte Azure ad B2B pour un invité ou un utilisateur externe qui peut être ajouté en tant que membre d’une équipe et qui dispose de tous les autorisations d’accès à la communication et aux ressources de l’équipe.

- **L’accès externe** est destiné à un utilisateur externe qui n’a pas de compte Azure ad B2B. L’accès externe peut inclure des invitations et la participation à des appels, des conversations et des réunions, mais n’inclut pas l’appartenance aux ressources de l’équipe et l’accès aux ressources de l’équipe.

Les stratégies d’accès conditionnel ne s’appliquent qu’à l’accès invité dans Teams, car il existe un compte Azure AD B2B correspondant.

<!--
In Azure AD, guest and external users are the same. The user type for both of these is Guest. Guest users are B2B users. Microsoft Teams differentiates between guest users and external users in the app. While it's important to understand how each of these are treated in Teams, both types of users are B2B users in Azure AD and the recommended policies for B2B users apply to both. 

--> 

Pour les stratégies recommandées permettant d’autoriser l’accès pour les utilisateurs invités et externes avec un compte Azure AD B2B, consultez la rubrique [stratégies permettant d’autoriser l’accès des comptes de B2B et d’invité](identity-access-policies-guest-access.md).

### <a name="guest-access-in-teams"></a>Accès invité dans Microsoft Teams

En plus des stratégies pour les utilisateurs internes à votre entreprise ou organisation, les administrateurs peuvent autoriser l’accès invité à autoriser, de manière individuelle, les personnes externes à votre entreprise ou organisation à accéder aux ressources de teams et à interagir avec les utilisateurs internes pour des tâches telles que les conversations de groupe, les conversations et les réunions. 

Pour plus d’informations sur l’accès invité et sur son implémentation, consultez la rubrique  [teams Guest Access](https://docs.microsoft.com/microsoftteams/guest-access).

### <a name="external-access-in-teams"></a>Accès externe dans teams

L’accès externe est parfois confondu avec l’accès invité, c’est pourquoi il est important de préciser que ces deux mécanismes d’accès non internes sont vraiment différents. 

L’accès externe est un moyen pour les utilisateurs de teams d’un domaine externe entier de rechercher, d’appeler, de discuter et de configurer des réunions avec vos utilisateurs dans Teams. Les administrateurs de teams configurent l’accès externe au niveau de l’organisation. Pour plus d’informations, consultez la rubrique [gérer l’accès externe dans Microsoft teams](https://docs.microsoft.com/microsoftteams/manage-external-access).

Accès externe les utilisateurs ont moins d’accès et de fonctionnalité qu’un individu qui a été ajouté via l’accès invité. Par exemple, les utilisateurs d’accès externe peuvent discuter avec vos utilisateurs internes avec teams mais ne peuvent pas accéder à des canaux d’équipe, des fichiers ou d’autres ressources.

L’accès externe n’utilise pas de comptes d’utilisateur inter-B2B Azure AD et, par conséquent, n’utilise pas de stratégies d’accès conditionnel. 

## <a name="teams-policies"></a>Stratégies teams

En dehors des stratégies courantes répertoriées ci-dessus, il existe des stratégies spécifiques à teams qui peuvent et doivent être configurées pour gérer les différentes fonctionnalités de teams.

### <a name="teams-and-channels-policies"></a>Stratégies teams et canaux

Teams and Channels sont deux éléments couramment utilisés dans Microsoft Teams, et il existe des stratégies que vous pouvez mettre en place pour contrôler ce que les utilisateurs peuvent et ne peuvent pas faire lors de l’utilisation de teams et de canaux. Bien que vous puissiez créer une équipe globale, si votre organisation dispose de 5000 utilisateurs ou moins, vous pouvez trouver utile d’avoir des équipes et des canaux plus petits à des fins spécifiques, en fonction des besoins de votre organisation.

Il est recommandé de modifier la stratégie par défaut ou de créer des stratégies personnalisées, et vous pouvez en savoir plus sur la gestion des stratégies à ce lien : [gérer les stratégies de teams dans Microsoft teams](https://docs.microsoft.com/microsoftteams/teams-policies).

### <a name="messaging-policies"></a>Stratégies de messagerie

La messagerie, ou conversation, peut également être gérée par le biais de la stratégie globale par défaut, ou par le biais de stratégies personnalisées, ce qui peut aider vos utilisateurs à communiquer les uns avec les autres d’une manière adaptée à votre organisation. Ces informations peuvent être consultées lors [de la gestion des stratégies de messagerie dans teams](https://docs.microsoft.com/microsoftteams/messaging-policies-in-teams).

### <a name="meeting-policies"></a>Stratégies de réunion

Aucune discussion sur les équipes ne serait terminée sans planifier et implémenter des stratégies autour des réunions Teams. Les réunions sont un élément essentiel de teams, qui permet aux utilisateurs de se rencontrer et de présenter officiellement un grand nombre d’utilisateurs en même temps, ainsi que de partager du contenu pertinent à la réunion. La définition des stratégies appropriées pour votre organisation pour les réunions est essentielle.

Pour plus d’informations, consultez la [partie gérer les stratégies de réunion dans teams](https://docs.microsoft.com/microsoftteams/meeting-policies-in-teams) .

### <a name="app-permission-policies"></a>Stratégies d’autorisation de l’application

Teams vous permet également d’utiliser des applications dans différents emplacements, comme des canaux ou des conversations personnelles. Les stratégies qui permettent d’ajouter et d’utiliser des applications, et où, sont essentielles pour la maintenance d’un environnement riche en contenu qui est également sécurisé.

Pour plus d’informations sur les stratégies d’autorisation des applications, consultez la rubrique [gérer les stratégies d’autorisation de l’application dans Microsoft teams](https://docs.microsoft.com/microsoftteams/teams-app-permission-policies).

## <a name="next-steps"></a>Étapes suivantes

![Étape 4 : stratégies pour les applications Cloud Microsoft 365](../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

Configurez les stratégies d’accès conditionnel pour :

- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](secure-email-recommended-policies.md)

