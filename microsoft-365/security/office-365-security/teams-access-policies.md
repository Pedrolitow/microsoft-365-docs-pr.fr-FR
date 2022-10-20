---
title: Stratégies Teams recommandées - Microsoft 365 pour les | d’entreprise Microsoft Docs
description: Décrit les stratégies pour les recommandations Microsoft sur la façon de sécuriser la communication teams et l’accès aux fichiers.
author: MicrosoftHeidi
manager: serdars
ms.service: microsoft-365-security
ms.topic: conceptual
audience: Admin
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
- m365-security
- m365solution-identitydevice
- m365solution-scenario
- zerotrust-solution
- highpri
ms.subservice: mdo
search.appverid: met150
ms.openlocfilehash: 828ee351feaeabceea7a2540669e99524f8663c7
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68632467"
---
# <a name="policy-recommendations-for-securing-teams-chats-groups-and-files"></a>Recommandations de stratégie pour la sécurisation des conversations, des groupes et des fichiers Teams

Cet article explique comment implémenter les stratégies d’identité et d’accès aux appareils Confiance nulle recommandées pour protéger les conversations, les groupes et le contenu Microsoft Teams, tels que les fichiers et les calendriers. Cette aide s’appuie sur les stratégies [d’accès aux identités et aux appareils courantes](identity-access-policies.md), avec des informations supplémentaires spécifiques à Teams. Étant donné que Teams s’intègre à nos autres produits, consultez également [les recommandations de stratégie pour la sécurisation des sites et fichiers SharePoint](sharepoint-file-access-policies.md) , ainsi que les recommandations de stratégie [pour la sécurisation des e-mails](secure-email-recommended-policies.md).

Ces recommandations sont basées sur trois niveaux de sécurité et de protection différents pour Teams qui peuvent être appliqués en fonction de la granularité de vos besoins : point de départ, entreprise et sécurité spécialisée. Vous pouvez en savoir plus sur ces niveaux de sécurité et les stratégies recommandées référencées par ces recommandations dans les [configurations d’identité et d’accès aux appareils](microsoft-365-policies-configurations.md).

D’autres recommandations spécifiques au déploiement teams sont incluses dans cet article pour couvrir des circonstances d’authentification spécifiques, notamment pour les utilisateurs extérieurs à votre organisation. Vous devez suivre ces conseils pour une expérience de sécurité complète.

## <a name="getting-started-with-teams-before-other-dependent-services"></a>Bien démarrer avec Teams avant d’autres services dépendants

Vous n’avez pas besoin d’activer les services dépendants pour commencer à utiliser Microsoft Teams. Ces services fonctionneront tous simplement. Toutefois, vous devez être prêt à gérer les éléments liés au service suivants :

- Groupes Microsoft 365
- Sites d’équipe SharePoint
- OneDrive Entreprise
- Les boîtes aux lettres Exchange
- Diffuser en continu des vidéos et des plans du Planificateur (si ces services sont activés)

## <a name="updating-common-policies-to-include-teams"></a>Mise à jour des stratégies courantes pour inclure Teams

Pour protéger les conversations, les groupes et le contenu dans Teams, le diagramme suivant illustre les stratégies à mettre à jour à partir des stratégies d’accès aux identités et aux appareils courantes. Pour chaque stratégie à mettre à jour, assurez-vous que Teams et les services dépendants sont inclus dans l’attribution d’applications cloud.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png" alt-text="Résumé des mises à jour de stratégie pour la protection de l’accès à Teams et à ses services dépendants" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png":::

Ces services sont les services dépendants à inclure dans l’attribution d’applications cloud pour Teams :

- Microsoft Teams
- SharePoint et OneDrive Entreprise
- Exchange Online
- Skype Entreprise Online
- Microsoft Stream (enregistrements de réunion)
- Planificateur Microsoft (tâches du Planificateur et données de plan)

Ce tableau répertorie les stratégies qui doivent être réexaminées et fournit des liens vers chaque stratégie dans les [stratégies d’accès aux identités et aux appareils communes](identity-access-policies.md), qui ont la stratégie plus large définie pour toutes les applications Office.

|Niveau de protection|Politiques|Informations supplémentaires sur l’implémentation de Teams|
|---|---|---|
|**Point de départ**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Assurez-vous que Teams et les services dépendants sont inclus dans la liste des applications. Teams a également des règles d’accès invité et d’accès externe à prendre en compte. Vous en apprendrez plus sur ces règles plus loin dans cet article.|
||[Bloquer les clients ne prenant pas en charge l’authentification moderne](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Incluez Teams et les services dépendants dans l’attribution d’applications cloud.|
||[Les utilisateurs à risque élevé doivent modifier leur mot de passe](identity-access-policies.md#high-risk-users-must-change-password)|Force les utilisateurs Teams à modifier leur mot de passe lors de la connexion si une activité à haut risque est détectée pour leur compte. Assurez-vous que Teams et les services dépendants sont inclus dans la liste des applications.|
||[Appliquer des stratégies de protection des données APP](identity-access-policies.md#apply-app-data-protection-policies)|Assurez-vous que Teams et les services dépendants sont inclus dans la liste des applications. Mettez à jour la stratégie pour chaque plateforme (iOS, Android, Windows).|
|**Enterprise**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *faible*, *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Teams a également des règles d’accès invité et d’accès externe à prendre en compte. Vous en apprendrez plus sur ces règles plus loin dans cet article. Incluez Teams et les services dépendants dans cette stratégie.|
||[Définir des stratégies de conformité des appareils](identity-access-policies.md#define-device-compliance-policies)|Incluez Teams et les services dépendants dans cette stratégie.|
||[Exiger des PC *et* des appareils mobiles conformes](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Incluez Teams et les services dépendants dans cette stratégie.|
|**Sécurité spécialisée**|[*Toujours* exiger l’authentification multifacteur](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Quelle que soit l’identité de l’utilisateur, l’authentification multifacteur est utilisée par votre organisation. Incluez Teams et les services dépendants dans cette stratégie. |

## <a name="teams-dependent-services-architecture"></a>Architecture des services dépendants teams

Pour référence, le diagramme suivant illustre les services sur lesquels Teams s’appuie. Pour plus d’informations et d’illustrations, consultez [Microsoft Teams et les services de productivité associés dans Microsoft 365 pour les architectes informatiques](../../solutions/productivity-illustrations.md).

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png" alt-text="Diagramme montrant les dépendances Teams sur SharePoint, OneDrive Entreprise et Exchange" lightbox="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png":::

## <a name="guest-and-external-access-for-teams"></a>Accès invité et externe pour Teams

Microsoft Teams définit les types d’accès suivants :

- **L’accès invité** utilise un compte Azure AD B2B pour un utilisateur invité ou externe qui peut être ajouté en tant que membre d’une équipe et dispose de toutes les autorisations d’accès à la communication et aux ressources de l’équipe.

- **L’accès externe** est destiné à un utilisateur externe qui n’a pas de compte Azure AD B2B. L’accès externe peut inclure des invitations et la participation à des appels, des conversations et des réunions, mais n’inclut pas l’appartenance à l’équipe et l’accès aux ressources de l’équipe.

Les stratégies d’accès conditionnel s’appliquent uniquement à l’accès invité dans Teams, car il existe un compte Azure AD B2B correspondant.

<!--
In Azure AD, guest and external users are the same. The user type for both of these is Guest. Guest users are B2B users. Microsoft Teams differentiates between guest users and external users in the app. While it's important to understand how each of these are treated in Teams, both types of users are B2B users in Azure AD and the recommended policies for B2B users apply to both.

-->

Pour connaître les stratégies recommandées pour autoriser l’accès pour les utilisateurs invités et externes disposant d’un compte Azure AD B2B, consultez [Stratégies pour autoriser l’accès au compte B2B invité et externe](identity-access-policies-guest-access.md).

### <a name="guest-access-in-teams"></a>Accès invité dans Microsoft Teams

Outre les stratégies pour les utilisateurs internes à votre entreprise ou organisation, les administrateurs peuvent autoriser l’accès invité à autoriser, utilisateur par utilisateur, les personnes externes à votre entreprise ou organisation à accéder aux ressources Teams et à interagir avec des personnes internes pour des éléments tels que les conversations de groupe, les conversations et les réunions.

Pour plus d’informations sur l’accès invité et la façon de l’implémenter, consultez  [l’accès invité Teams](/microsoftteams/guest-access).

### <a name="external-access-in-teams"></a>Accès externe dans Teams

L’accès externe étant parfois confondu avec l’accès invité, il est important d’être clair que ces deux mécanismes d’accès non internes sont des types d’accès différents.

L’accès externe est un moyen pour les utilisateurs Teams d’un domaine externe entier de rechercher, d’appeler, de discuter et de configurer des réunions avec vos utilisateurs dans Teams. Les administrateurs Teams configurent l’accès externe au niveau de l’organisation. Pour plus d’informations, consultez [Gérer l’accès externe dans Microsoft Teams](/microsoftteams/manage-external-access).

Les utilisateurs d’accès externe ont moins d’accès et de fonctionnalités qu’une personne qui a été ajoutée via l’accès invité. Par exemple, les utilisateurs d’accès externe peuvent discuter avec vos utilisateurs internes avec Teams, mais ils ne peuvent pas accéder aux canaux d’équipe, aux fichiers ou à d’autres ressources.

L’accès externe n’utilise pas de comptes d’utilisateur Azure AD B2B et n’utilise donc pas de stratégies d’accès conditionnel.

## <a name="teams-policies"></a>Stratégies Teams

En dehors des stratégies courantes répertoriées ci-dessus, il existe des stratégies spécifiques à Teams qui peuvent et doivent être configurées pour gérer différentes fonctionnalités Teams.

### <a name="teams-and-channels-policies"></a>Stratégies Teams et canaux

Teams et les canaux sont deux éléments couramment utilisés dans Microsoft Teams, et il existe des stratégies que vous pouvez mettre en place pour contrôler ce que les utilisateurs peuvent et ne peuvent pas faire lors de l’utilisation d’équipes et de canaux. Bien que vous puissiez créer une équipe globale, si votre organisation compte 5 000 utilisateurs ou moins, il est probable que vous trouviez utile d’avoir des équipes et des canaux plus petits à des fins spécifiques, conformément aux besoins de votre organisation.

Il est recommandé de modifier la stratégie par défaut ou de créer des stratégies personnalisées. Pour en savoir plus sur la gestion de vos stratégies, consultez ce lien : [Gérer les stratégies Teams dans Microsoft Teams](/microsoftteams/teams-policies).

### <a name="messaging-policies"></a>Stratégies de messagerie

La messagerie, ou conversation, peut également être gérée par le biais de la stratégie globale par défaut ou par le biais de stratégies personnalisées, ce qui peut aider vos utilisateurs à communiquer entre eux d’une manière adaptée à votre organisation. Ces informations peuvent être examinées lors de la [gestion des stratégies de messagerie dans Teams](/microsoftteams/messaging-policies-in-teams).

### <a name="meeting-policies"></a>Stratégies de réunion

Aucune discussion sur Teams ne serait complète sans la planification et l’implémentation de stratégies autour des réunions Teams. Les réunions sont un composant essentiel de Teams, qui permet aux utilisateurs de se rencontrer et de présenter officiellement à de nombreux utilisateurs à la fois, et de partager du contenu pertinent pour la réunion. Il est essentiel de définir les stratégies appropriées pour votre organisation autour des réunions.

Pour plus d’informations, consultez [Gérer les stratégies de réunion dans Teams](/microsoftteams/meeting-policies-in-teams).

### <a name="app-permission-policies"></a>Stratégies d’autorisation d’application

Teams vous permet également d’utiliser des applications à différents endroits, tels que des canaux ou des conversations personnelles. Il est essentiel d’avoir des stratégies concernant les applications qui peuvent être ajoutées et utilisées, et où, pour maintenir un environnement riche en contenu qui soit également sécurisé.

Pour plus d’informations sur les stratégies [d’autorisation d’application, consultez Gérer les stratégies d’autorisation d’application dans Microsoft Teams](/microsoftteams/teams-app-permission-policies).

## <a name="next-steps"></a>Prochaines étapes

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Étape 4 : Stratégies pour les applications cloud Microsoft 365" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Configurer des stratégies d’accès conditionnel pour :

- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
