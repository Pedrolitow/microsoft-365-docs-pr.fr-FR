---
title: 'Stratégies Teams recommandées : Microsoft 365 pour les | Documents Microsoft'
description: Décrit les stratégies pour les recommandations de Microsoft sur la façon de sécuriser la communication teams et l’accès aux fichiers.
author: MicrosoftHeidi
manager: serdars
ms.prod: m365-security
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
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 7724ef76d905cdbaf48f3122d0df7ef28d0b8385
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49931625"
---
# <a name="policy-recommendations-for-securing-teams-chats-groups-and-files"></a>Recommandations de stratégie pour la sécurisation des conversations, des groupes et des fichiers Teams

Cet article explique comment implémenter les stratégies recommandées d’identité et d’accès aux appareils pour protéger les conversations, les groupes et le contenu Microsoft Teams tels que les fichiers et les calendriers. Ces instructions s’appuient sur [les](identity-access-policies.md)stratégies d’accès aux appareils et aux identités communes, avec des informations supplémentaires propres à Teams. Étant donné que Teams s’intègre à nos autres produits, consultez également les recommandations de stratégie pour la sécurisation des sites et des fichiers [SharePoint,](sharepoint-file-access-policies.md) ainsi que les recommandations de stratégie [pour la sécurisation de la messagerie électronique.](secure-email-recommended-policies.md)

Ces recommandations sont basées sur trois niveaux différents de sécurité et de protection pour Teams qui peuvent être appliqués en fonction de la granularité de vos besoins : base de référence, sensible et hautement réglementé. Vous pouvez en savoir plus sur ces niveaux de sécurité et les stratégies recommandées référencés par ces recommandations dans les configurations d’identité et d’accès [aux appareils.](microsoft-365-policies-configurations.md)

Des recommandations supplémentaires spécifiques au déploiement de Teams sont incluses dans cet article pour couvrir des circonstances d’authentification spécifiques, y compris pour les utilisateurs externes à votre organisation. Vous devrez suivre ces instructions pour une expérience de sécurité complète.

## <a name="getting-started-with-teams-before-other-dependent-services"></a>Mise en place de Teams avant d’autres services dépendants

Vous n’avez pas besoin d’activer les services dépendants pour commencer à travailler avec Microsoft Teams. Tous ces éléments « fonctionnent simplement ». Toutefois, vous devez être prêt à gérer les choses suivantes :

- Groupes Microsoft 365
- Sites d’équipe SharePoint
- OneDrive Entreprise
- Les boîtes aux lettres Exchange
- Flux de vidéos et plans du Planificateur (si ces services sont activés)

## <a name="updating-common-policies-to-include-teams"></a>Mise à jour des stratégies courantes pour inclure Teams

Pour protéger la conversation, les groupes et le contenu dans Teams, le diagramme suivant illustre les stratégies à mettre à jour à partir des stratégies communes d’accès aux appareils et aux identités. Pour chaque stratégie à mettre à jour, assurez-vous que Teams et les services dépendants sont inclus dans l’affectation des applications cloud.

[![Résumé des mises à jour de stratégie pour la protection de l’accès à Teams et à ses services dépendants](../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png)

[Voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png)

Voici les services dépendants à inclure dans l’attribution des applications cloud pour Teams :

- Microsoft Teams
- SharePoint et OneDrive Entreprise
- Exchange Online
- Skype Entreprise Online
- Microsoft Stream (enregistrements de réunions)
- Planificateur Microsoft (tâches du planificateur et données de plan)

Ce tableau répertorie les stratégies qui doivent être réexaminées et des liens vers chaque stratégie dans les stratégies communes d’accès aux identités et aux [appareils,](identity-access-policies.md)dont la stratégie la plus large est définie pour toutes les applications Office.

|Niveau de protection|Stratégies|Informations supplémentaires sur l’implémentation de Teams|
|---|---|---|
|**Baseline**|[Exiger une mfmf lorsque le risque de se connecte *est moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Assurez-vous que Teams et les services dépendants sont inclus dans la liste des applications. Teams a également des règles d’accès invité et d’accès externe à prendre en compte. Vous en apprendrez plus à ce sujet plus loin dans cet article.|
||[Bloquer les clients ne prenant pas en charge l’authentification moderne](identity-access-policies.md#block-clients-that-dont-support-modern-authentication)|Inclure Teams et les services dépendants dans l’affectation des applications cloud.|
||[Les utilisateurs à risque élevé doivent modifier leur mot de passe](identity-access-policies.md#high-risk-users-must-change-password)|Oblige les utilisateurs de Teams à modifier leur mot de passe lors de la signature si une activité à risque élevé est détectée pour leur compte. Assurez-vous que Teams et les services dépendants sont inclus dans la liste des applications.|
||[Appliquer des stratégies de protection des données APP](identity-access-policies.md#apply-app-data-protection-policies)|Assurez-vous que Teams et les services dépendants sont inclus dans la liste des applications. Mettez à jour la stratégie pour chaque plateforme (iOS, Android, Windows).|
||[Définir des stratégies de conformité des appareils](identity-access-policies.md#define-device-compliance-policies)|Inclure Teams et les services dépendants dans cette stratégie.|
||[Exiger des PC conformes](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Inclure Teams et les services dépendants dans cette stratégie.|
|**Sensible**|[Exiger l’mf lorsque le risque de se connecte *est faible,* *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Teams a également des règles d’accès invité et d’accès externe à prendre en compte. Vous en apprendrez plus à ce sujet plus loin dans cet article. Inclure Teams et les services dépendants dans cette stratégie.|
||[Exiger des PC et *des appareils* mobiles conformes](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Inclure Teams et les services dépendants dans cette stratégie.|
|**Hautement réglementé**|[*Toujours exiger* l’mf d’fa](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Quelle que soit l’identité de l’utilisateur, l’ation MFA sera utilisée par votre organisation. Inclure Teams et les services dépendants dans cette stratégie. |
|

## <a name="teams-dependent-services-architecture"></a>Architecture des services dépendants de Teams

À titre de référence, le diagramme suivant illustre les services sur qui Teams s’appuie. Pour plus d’informations et des illustrations supplémentaires, voir Microsoft Teams et les services de productivité associés dans [Microsoft 365 pour les architectes it.](../../solutions/productivity-illustrations.md)

[![Diagramme montrant les dépendances de Teams sur SharePoint, OneDrive Entreprise et Exchange](../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png)

[Voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png)

## <a name="guest-and-external-access-for-teams"></a>Accès invité et externe pour Teams

Microsoft Teams définit les définitions suivantes :

- **L’accès** invité utilise un compte Azure AD B2B pour un invité ou un utilisateur externe qui peut être ajouté en tant que membre d’une équipe et qui dispose de tous les accès autorisés aux communications et aux ressources de l’équipe.

- **L’accès** externe est pour un utilisateur externe qui n’a pas de compte Azure AD B2B. L’accès externe peut inclure des invitations et la participation à des appels, des conversations et des réunions, mais n’inclut pas l’appartenance à une équipe et l’accès aux ressources de l’équipe.

Les stratégies d’accès conditionnel s’appliquent uniquement à l’accès invité dans Teams, car il existe un compte Azure AD B2B correspondant.

<!--
In Azure AD, guest and external users are the same. The user type for both of these is Guest. Guest users are B2B users. Microsoft Teams differentiates between guest users and external users in the app. While it's important to understand how each of these are treated in Teams, both types of users are B2B users in Azure AD and the recommended policies for B2B users apply to both.

-->

Pour obtenir les stratégies recommandées pour autoriser l’accès aux utilisateurs invités et externes avec un compte Azure AD B2B, voir Stratégies d’accès aux comptes B2B externes et [invités.](identity-access-policies-guest-access.md)

### <a name="guest-access-in-teams"></a>Accès invité dans Microsoft Teams

Outre les stratégies pour les utilisateurs internes à votre entreprise ou organisation, les administrateurs peuvent activer l’accès invité pour autoriser, utilisateur par utilisateur, les personnes externes à votre entreprise ou organisation à accéder aux ressources Teams et à interagir avec des personnes internes pour des choses telles que des conversations de groupe, des conversations et des réunions.

Pour plus d’informations sur l’accès invité et sur la façon de l’implémenter, voir [l’accès invité Teams.](https://docs.microsoft.com/microsoftteams/guest-access)

### <a name="external-access-in-teams"></a>Accès externe dans Teams

L’accès externe est parfois confondu avec l’accès invité. Il est donc important de savoir que ces deux mécanismes d’accès non internes sont en réalité très différents.

L’accès externe permet aux utilisateurs de Teams d’un domaine externe entier de rechercher, d’appeler, de discuter et de configurer des réunions avec vos utilisateurs dans Teams. Les administrateurs Teams configurent l’accès externe au niveau de l’organisation. Pour plus d’informations, voir [Gérer l’accès externe dans Microsoft Teams.](https://docs.microsoft.com/microsoftteams/manage-external-access)

Les utilisateurs d’accès externe ont moins d’accès et de fonctionnalités qu’une personne qui a été ajoutée via l’accès invité. Par exemple, les utilisateurs d’accès externe peuvent discuter avec vos utilisateurs internes avec Teams, mais ne peuvent pas accéder aux canaux d’équipe, aux fichiers ou à d’autres ressources.

L’accès externe n’utilise pas les comptes d’utilisateur Azure AD B2B et, par conséquent, n’utilise pas de stratégies d’accès conditionnel.

## <a name="teams-policies"></a>Stratégies Teams

En dehors des stratégies courantes répertoriées ci-dessus, il existe des stratégies propres à Teams qui peuvent et doivent être configurées pour gérer différentes fonctionnalités Teams.

### <a name="teams-and-channels-policies"></a>Stratégies de teams et de canaux

Teams et les canaux sont deux éléments couramment utilisés dans Microsoft Teams, et il existe des stratégies que vous pouvez mettre en place pour contrôler ce que les utilisateurs peuvent et ne peuvent pas faire lors de l’utilisation des équipes et des canaux. Bien que vous pouvez créer une équipe globale, si votre organisation compte au moins 5 000 utilisateurs, il est probable qu’il soit utile d’avoir des équipes et des canaux plus petits à des fins spécifiques, en ligne avec les besoins de votre organisation.

Il est recommandé de modifier la stratégie par défaut ou de créer des stratégies personnalisées. Pour en savoir plus sur la gestion de vos stratégies, voir ce lien : Gérer les stratégies d’équipe dans [Microsoft Teams.](https://docs.microsoft.com/microsoftteams/teams-policies)

### <a name="messaging-policies"></a>Stratégies de messagerie

La messagerie, ou conversation, peut également être gérée par le biais de la stratégie globale par défaut ou par le biais de stratégies personnalisées, ce qui peut aider vos utilisateurs à communiquer les uns avec les autres d’une manière appropriée pour votre organisation. Ces informations peuvent être examinées dans [La gestion des stratégies de messagerie dans Teams.](https://docs.microsoft.com/microsoftteams/messaging-policies-in-teams)

### <a name="meeting-policies"></a>Stratégies de réunion

Aucune discussion sur Teams ne serait terminée sans la planification et l’implémentation de stratégies autour des réunions Teams. Les réunions sont un composant essentiel de Teams, ce qui permet aux utilisateurs de se rencontrer et de les présenter à de nombreux utilisateurs en même temps, ainsi que de partager du contenu pertinent pour la réunion. Il est essentiel de définir les stratégies pour votre organisation en matière de réunions.

Pour plus d’informations, [consultez Gérer](https://docs.microsoft.com/microsoftteams/meeting-policies-in-teams) les stratégies de réunion dans Teams.

### <a name="app-permission-policies"></a>Stratégies d’autorisation d’application

Teams vous permet également d’utiliser des applications à différents endroits, tels que des canaux ou des conversations personnelles. Il est essentiel d’avoir des stratégies concernant les applications qui peuvent être ajoutées et utilisées, et où, pour maintenir un environnement riche en contenu qui est également sécurisé.

Pour en savoir plus sur les stratégies d’autorisation d’application, consultez [Gérer les stratégies d’autorisation d’application dans Microsoft Teams.](https://docs.microsoft.com/microsoftteams/teams-app-permission-policies)

## <a name="next-steps"></a>Étapes suivantes

![Étape 4 : Stratégies pour les applications cloud Microsoft 365](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

Configurer des stratégies d’accès conditionnel pour :

- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
