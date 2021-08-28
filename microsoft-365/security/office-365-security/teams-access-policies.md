---
title: 'Stratégies de Teams recommandées : Microsoft 365 pour les | Documents Microsoft'
description: Décrit les stratégies pour les recommandations de Microsoft sur la façon de sécuriser Teams communication et l’accès aux fichiers.
author: MicrosoftHeidi
manager: serdars
ms.prod: m365-security
ms.topic: article
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
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: b135c6dd691607dd128bfd83e0d2b484bb3a97ae
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58568059"
---
# <a name="policy-recommendations-for-securing-teams-chats-groups-and-files"></a>Recommandations de stratégie pour la sécurisation des Teams conversations, des groupes et des fichiers

Cet article explique comment implémenter les stratégies recommandées d’identité et d’accès aux appareils pour protéger Microsoft Teams conversations, groupes et contenus tels que des fichiers et des calendriers. Ces instructions s’appuient sur [les](identity-access-policies.md)stratégies d’accès aux appareils et aux identités courantes, avec des informations supplémentaires Teams spécifiques. Comme Teams s’intègre à nos autres produits, voir également [recommandations](sharepoint-file-access-policies.md) en matière de stratégie pour la sécurisation des sites et des fichiers SharePoint et recommandations de stratégie pour la [sécurisation de la messagerie électronique.](secure-email-recommended-policies.md)

Ces recommandations sont basées sur trois niveaux différents de sécurité et de protection pour les Teams qui peuvent être appliqués en fonction de la granularité de vos besoins : base de référence, sensible et hautement réglementé. Vous pouvez en savoir plus sur ces niveaux de sécurité et les stratégies recommandées référencés par ces recommandations dans les configurations d’identité et d’accès [aux appareils.](microsoft-365-policies-configurations.md)

D’autres recommandations spécifiques au déploiement Teams sont incluses dans cet article pour couvrir des circonstances d’authentification spécifiques, y compris pour les utilisateurs externes à votre organisation. Vous devrez suivre ces instructions pour une expérience de sécurité complète.

## <a name="getting-started-with-teams-before-other-dependent-services"></a>Mise en place de la Teams avant les autres services dépendants

Vous n’avez pas besoin d’activer les services dépendants pour commencer à Microsoft Teams. Ces services fonctionneront tous « simplement ». Toutefois, vous devez être prêt à gérer les éléments suivants liés au service :

- Groupes Microsoft 365
- Sites d’équipe SharePoint
- OneDrive Entreprise
- Les boîtes aux lettres Exchange
- Flux de vidéos et plans du Planificateur (si ces services sont activés)

## <a name="updating-common-policies-to-include-teams"></a>Mise à jour des stratégies courantes pour inclure Teams

Pour protéger la conversation, les groupes et le contenu dans Teams, le diagramme suivant illustre les stratégies à mettre à jour à partir des stratégies communes d’accès aux appareils et aux identités. Pour chaque stratégie à mettre à jour, assurez-vous Teams services dépendants sont inclus dans l’affectation des applications cloud.

[![Résumé des mises à jour de stratégie pour la protection de l’accès Teams et de ses services dépendants.](../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png)

Ces services sont les services dépendants à inclure dans l’affectation des applications cloud pour Teams :

- Microsoft Teams
- SharePoint et OneDrive Entreprise
- Exchange Online
- Skype Entreprise Online
- Microsoft Stream (enregistrements de réunions)
- Planificateur Microsoft (tâches du planificateur et données de plan)

Ce tableau répertorie les stratégies qui doivent [](identity-access-policies.md)être réexaminées et les liens vers chaque stratégie dans les stratégies d’accès aux identités et appareils communes, qui ont la stratégie plus large définie pour toutes les applications Office.

|Niveau de protection|Politiques|Informations supplémentaires sur l’implémentation Teams’application|
|---|---|---|
|**Baseline**|[Exiger une mfmf lorsque le risque de se connecte *est moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Assurez-vous Teams services dépendants sont inclus dans la liste des applications. Teams des règles d’accès invité et d’accès externe à prendre en compte, vous en apprendrez plus sur ces règles plus loin dans cet article.|
||[Bloquer les clients ne prenant pas en charge l’authentification moderne](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Inclure Teams services dépendants dans l’affectation des applications cloud.|
||[Les utilisateurs à risque élevé doivent modifier leur mot de passe](identity-access-policies.md#high-risk-users-must-change-password)|Force Teams utilisateurs à modifier leur mot de passe lors de la signature si une activité à risque élevé est détectée pour leur compte. Assurez-vous Teams services dépendants sont inclus dans la liste des applications.|
||[Appliquer des stratégies de protection des données APP](identity-access-policies.md#apply-app-data-protection-policies)|Assurez-vous Teams services dépendants sont inclus dans la liste des applications. Mettez à jour la stratégie pour chaque plateforme (iOS, Android, Windows).|
||[Définir des stratégies de conformité des appareils](identity-access-policies.md#define-device-compliance-policies)|Incluez Teams services dépendants dans cette stratégie.|
||[Exiger des PC conformes](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Incluez Teams services dépendants dans cette stratégie.|
|**Sensible**|[Exiger l’mf lorsque le risque de se connecte *est faible,* *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Teams des règles d’accès invité et d’accès externe à prendre en compte, vous en apprendrez plus sur ces règles plus loin dans cet article. Incluez Teams services dépendants dans cette stratégie.|
||[Exiger des PC et *des appareils* mobiles conformes](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Incluez Teams services dépendants dans cette stratégie.|
|**Hautement réglementé**|[*Toujours exiger* l’mf d’fa](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Quelle que soit l’identité de l’utilisateur, l’ation MFA sera utilisée par votre organisation. Incluez Teams services dépendants dans cette stratégie. |
|

## <a name="teams-dependent-services-architecture"></a>Teams’architecture des services dépendants

À titre de référence, le diagramme suivant illustre les services sur Teams’aide. Pour plus d’informations et d’illustrations, voir Microsoft Teams services de productivité associés [dans Microsoft 365 pour les architectes it.](../../solutions/productivity-illustrations.md)

[![Diagramme montrant Teams dépendances sur SharePoint, OneDrive Entreprise et Exchange.](../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png)

[Voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png)

## <a name="guest-and-external-access-for-teams"></a>Accès invité et externe pour les Teams

Microsoft Teams définit les types d’accès suivants :

- **L’accès** invité utilise un compte Azure AD B2B pour un invité ou un utilisateur externe qui peut être ajouté en tant que membre d’une équipe et qui dispose de tous les accès autorisés aux communications et aux ressources de l’équipe.

- **L’accès** externe est pour un utilisateur externe qui n’a pas de compte Azure AD B2B. L’accès externe peut inclure des invitations et la participation à des appels, des conversations et des réunions, mais n’inclut pas l’appartenance à une équipe et l’accès aux ressources de l’équipe.

Les stratégies d’accès conditionnel s’appliquent uniquement à l’accès invité dans Teams car il existe un compte Azure AD B2B correspondant.

<!--
In Azure AD, guest and external users are the same. The user type for both of these is Guest. Guest users are B2B users. Microsoft Teams differentiates between guest users and external users in the app. While it's important to understand how each of these are treated in Teams, both types of users are B2B users in Azure AD and the recommended policies for B2B users apply to both.

-->

Pour obtenir les stratégies recommandées pour autoriser l’accès aux utilisateurs invités et externes avec un compte Azure AD B2B, voir Stratégies d’accès aux comptes B2B externes et [invités.](identity-access-policies-guest-access.md)

### <a name="guest-access-in-teams"></a>Accès invité dans Microsoft Teams

Outre les stratégies pour les utilisateurs internes à votre entreprise ou organisation, les administrateurs peuvent activer l’accès invité pour autoriser, par utilisateur, les personnes externes à votre entreprise ou organisation à accéder aux ressources Teams et à interagir avec des personnes internes pour des choses telles que des conversations de groupe, des conversations et des réunions.

Pour plus d’informations sur l’accès invité et comment l’implémenter, [voir Teams’accès invité.](/microsoftteams/guest-access)

### <a name="external-access-in-teams"></a>Accès externe dans Teams

L’accès externe est parfois confondu avec l’accès invité. Il est donc important de savoir que ces deux mécanismes d’accès non internes sont des types d’accès différents.

L’accès externe permet aux Teams d’un domaine externe entier de rechercher, d’appeler, de discuter et de configurer des réunions avec vos utilisateurs dans Teams. Teams configurer l’accès externe au niveau de l’organisation. Pour plus d’informations, [voir Gérer l’accès externe dans Microsoft Teams](/microsoftteams/manage-external-access).

Les utilisateurs d’accès externe ont moins d’accès et de fonctionnalités qu’une personne qui a été ajoutée via l’accès invité. Par exemple, les utilisateurs d’accès externe peuvent discuter avec vos utilisateurs internes avec Teams mais ne peuvent pas accéder aux canaux d’équipe, aux fichiers ou à d’autres ressources.

L’accès externe n’utilise pas les comptes d’utilisateur Azure AD B2B et n’utilise donc pas de stratégies d’accès conditionnel.

## <a name="teams-policies"></a>Teams stratégies

En dehors des stratégies courantes répertoriées ci-dessus, il existe des stratégies spécifiques Teams qui peuvent et doivent être configurées pour gérer diverses fonctionnalités Teams de gestion.

### <a name="teams-and-channels-policies"></a>Teams et stratégies de canaux

Teams et les canaux sont deux éléments couramment utilisés dans Microsoft Teams, et il existe des stratégies que vous pouvez mettre en place pour contrôler ce que les utilisateurs peuvent et ne peuvent pas faire lors de l’utilisation d’équipes et de canaux. Bien que vous pouvez créer une équipe globale, si votre organisation compte au moins 5 000 utilisateurs, il est probable qu’il soit utile d’avoir des équipes et des canaux plus petits à des fins spécifiques, en ligne avec les besoins de votre organisation.

Il est recommandé de modifier la stratégie par défaut ou de créer des stratégies personnalisées, et vous pouvez en savoir plus sur la gestion de vos stratégies sur ce lien : Gérer les stratégies d’équipe [dans Microsoft Teams](/microsoftteams/teams-policies).

### <a name="messaging-policies"></a>Stratégies de messagerie

La messagerie ou la conversation peut également être gérée par le biais de la stratégie globale par défaut ou par le biais de stratégies personnalisées, ce qui peut aider vos utilisateurs à communiquer les uns avec les autres d’une manière appropriée pour votre organisation. Ces informations peuvent être examinées dans [managing messaging policies in Teams](/microsoftteams/messaging-policies-in-teams).

### <a name="meeting-policies"></a>Stratégies de réunion

Aucune discussion sur les Teams être terminée sans la planification et l’implémentation de stratégies autour Teams réunions. Les réunions sont un composant essentiel de Teams, ce qui permet aux utilisateurs de se rencontrer et de les présenter à de nombreux utilisateurs à la fois, et de partager du contenu pertinent pour la réunion. Il est essentiel de définir les stratégies pour votre organisation en matière de réunions.

Pour plus d’informations, [examinez Gérer les stratégies de réunion dans Teams](/microsoftteams/meeting-policies-in-teams).

### <a name="app-permission-policies"></a>Stratégies d’autorisation d’application

Teams vous permet également d’utiliser des applications à différents endroits, tels que des canaux ou des conversations personnelles. Il est essentiel d’avoir des stratégies concernant les applications qui peuvent être ajoutées et utilisées, et où, pour maintenir un environnement riche en contenu également sécurisé.

Pour en savoir plus sur les stratégies d’autorisation d’application, consultez Gérer les stratégies [d’autorisation d’application Microsoft Teams](/microsoftteams/teams-app-permission-policies).

## <a name="next-steps"></a>Prochaines étapes

![Étape 4 : Stratégies pour Microsoft 365 applications cloud.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

Configurer des stratégies d’accès conditionnel pour :

- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)