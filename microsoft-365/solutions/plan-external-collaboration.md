---
title: Planifier une collaboration externe avec des conversations de canal, une collaboration de fichiers et des applications partagées
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
localization_priority: Normal
f1.keywords: NOCSH
recommendations: false
description: Découvrez la différence entre la collaboration invité et les canaux partagés dans Teams et comment choisir celui à utiliser.
ms.openlocfilehash: 09948b49d0c4f3e21d03c1e3994e4dd2d609ed13
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65465781"
---
# <a name="plan-external-collaboration-with-channel-conversations-file-collaboration-and-shared-apps"></a>Planifier une collaboration externe avec des conversations de canal, une collaboration de fichiers et des applications partagées

Microsoft 365 offre plusieurs options pour collaborer avec des personnes extérieures à votre organisation :

- 1:1 et conversation de groupe dans Teams avec des personnes extérieures à votre organisation
- Teams réunions avec des personnes extérieures à votre organisation
- Partage de fichiers ou de dossiers individuels avec des personnes extérieures à votre organisation
- Collaboration au sein d’une équipe, avec des conversations de canal, une collaboration de fichiers et des applications partagées

Cet article aborde la quatrième option, la collaboration de groupe avec les conversations de canal, la collaboration de fichiers et les applications partagées. (Pour une vue d’ensemble de toutes les options, consultez [Vue d’ensemble des options de collaboration externe dans Microsoft 365](/microsoft-365/enterprise/external-guest-access).)

## <a name="terms"></a>Termes

- **Azure AD B2B Collaboration** : fonctionnalité qui permet aux utilisateurs de partager des fichiers, des dossiers, des sites, des groupes et des équipes avec des personnes extérieures à votre organisation. Ces personnes accèdent aux ressources partagées en utilisant des comptes invités dans votre répertoire.
- **Connexion directe Azure AD B2B** : fonctionnalité qui permet aux utilisateurs de partager des ressources dans votre organisation avec des personnes d’autres organisations Azure AD. Ces personnes accèdent aux ressources partagées à l’aide de leur propre compte professionnel ou scolaire. Aucun compte invité n’est créé dans votre organisation.
- **Participant externe** – Personne externe à votre organisation qui participe à une ressource ( par exemple, un canal partagé ) utilisant sa propre identité et non un compte invité dans votre annuaire.
- **Organisation externe** : autre organisation avec laquelle vous partagez des ressources.
- **Invité** : personne externe à votre organisation qui accède aux ressources partagées en se connectant à un compte invité dans votre annuaire.
- **Organisation hôte** : organisation qui héberge une ressource partagée, telle qu’un canal partagé.
- **Canal partagé** : canal Teams qui peut être partagé avec des personnes extérieures à l’équipe. Ces personnes peuvent se trouver au sein de votre organisation ou d’autres organisations Azure AD.
- **Partage de liens** : liens avec des autorisations vers un fichier ou un dossier utilisé pour partager ce fichier ou ce dossier avec d’autres personnes. Les personnes avec lesquelles ils sont partagés peuvent se trouver à l’intérieur ou à l’extérieur de votre organisation.

## <a name="options-for-collaboration-in-a-team"></a>Options de collaboration dans une équipe

Lorsque vous collaborez dans une équipe avec des personnes extérieures à votre organisation, il existe deux options permettant à ces personnes d’accéder aux ressources que vous partagez avec elles.

### <a name="guest-sharing"></a>Partage d’invités

Le partage d’invités utilise Azure AD B2B Collaboration pour permettre le partage et la collaboration avec des personnes extérieures à votre organisation en ajoutant un compte invité dans Azure AD pour chaque personne. Les comptes invités peuvent être utilisés pour les éléments suivants :

- Appartenance des invités aux équipes, aux sites SharePoint et aux groupes Microsoft 365
- Partage de fichiers et de dossiers individuel

Les invités d’une équipe ont des fonctionnalités similaires aux membres réguliers de l’équipe.

### <a name="external-participants-in-shared-channels"></a>Participants externes dans les canaux partagés

Les participants externes accèdent aux ressources partagées de votre organisation à l’aide de leur propre identité Azure AD ou Microsoft 365. Cette option est activée par Azure AD B2B Direct Connect via une relation organisationnelle configurée par les deux organisations. Les comptes invités ne sont pas utilisés dans cette relation.

Le principal avantage des participants externes dans les canaux partagés par rapport au partage d’invités est que les personnes extérieures à votre organisation peuvent collaborer avec vos utilisateurs dans Teams sans avoir à modifier leur contexte utilisateur. Lorsque vous utilisez des comptes invités, les utilisateurs doivent se déconnecter de Teams avec leur compte professionnel ou scolaire et se reconnecter à l’aide du compte invité. Ils peuvent également avoir une copie distincte de Teams en cours d’exécution dans une session de navigateur privé. Ce basculement entre les organisations prend du temps et peut entraîner l’absence de communications importantes lors de la déconnexion d’une organisation donnée.

Avec les canaux partagés, les utilisateurs peuvent rester connectés à leur organisation et accéder aux canaux partagés avec eux à partir d’autres organisations. Les canaux partagés d’autres organisations sont disponibles dans Teams aux côtés des équipes et des canaux de votre organisation. Il n’est pas nécessaire de changer d’organisation.

## <a name="feature-comparison"></a>Comparaison des fonctionnalités

Le tableau suivant décrit les expériences disponibles en fonction du type de compte utilisé.

|Fonctionnalité|Utilisateur (votre organisation)|Invité (Collaboration Azure AD)|Participant externe (Connexion directe Azure AD)|
|:-----|:-----|:------|:-------|
|Accès à l’équipe|v|v|N|
|Accès au canal partagé|v|N|v|
|Autorisations via des liens de partage de fichiers|v|v|N|
|Utiliser des canaux partagés|v|N|v|
|Utiliser des canaux privés|v|v|N|
|Compte dans votre répertoire|v|v|N|
|Révisions accès|v|v|v|

## <a name="planning-considerations"></a>Considérations relatives à la planification

La plupart des organisations utilisent à la fois le partage d’invités et les canaux partagés avec des participants externes.

Le partage d’invités est activé par défaut dans Azure AD et dans Microsoft 365 (Teams, Groupes Microsoft 365 et SharePoint). Cela permet aux utilisateurs d’inviter des invités à des équipes et des sites et de partager des fichiers avec eux sans avoir à demander de l’aide à l’informatique.

Vous devez utiliser le partage d’invités si :

- Vous souhaitez inviter des personnes extérieures à votre organisation à l’équipe plutôt qu’à des canaux individuels
- Vous souhaitez partager des fichiers ou des dossiers dans un canal avec des personnes extérieures à votre organisation qui ne sont pas dans le canal
- Vous souhaitez collaborer avec des personnes extérieures à votre organisation qui n’ont pas de compte professionnel ou scolaire.

Bien que les canaux partagés soient activés par défaut dans Teams, la collaboration externe avec les canaux partagés nécessite qu’un administrateur Azure AD configure l’accès interlocataire entre votre organisation et l’autre organisation avec laquelle vous souhaitez partager. Les autres organisations doivent également configurer l’accès entre locataires à leur extrémité.

Si vous envisagez d’utiliser des canaux partagés avec d’autres organisations, vous pouvez choisir entre un modèle libre-service et un modèle par demande.

- Libre-service : vous pouvez configurer l’accès entre locataires pour autoriser l’accès entrant et sortant à toutes les autres organisations Azure AD. Vous pouvez également bloquer une liste d’organisations avec lesquelles vous ne souhaitez pas que vos utilisateurs partagent, en laissant toutes les autres organisations disponibles. Cela permet à vos utilisateurs d’inviter des personnes extérieures à l’organisation à participer à des canaux partagés sans avoir à contacter votre support technique ou votre service informatique.
- Par demande : vous pouvez configurer l’accès entre locataires pour chaque organisation avec laquelle vous souhaitez autoriser les canaux partagés. Lorsque vous choisissez ce modèle, il est important de disposer d’un processus métier documenté que vos utilisateurs peuvent suivre pour demander l’accès entre locataires avec une autre organisation.

## <a name="compliance-in-shared-channels"></a>Conformité dans les canaux partagés

Les canaux partagés sont intégrés à Microsoft Purview fonctionnalités.

### <a name="communications-compliance"></a>Conformité des communications

Les administrateurs peuvent définir des stratégies pour surveiller le contenu de tous les utilisateurs du canal. Tous les messages contenus dans les canaux, y compris les canaux partagés, sont couverts par les [stratégies de conformité des communications](/microsoft-365/compliance/communication-compliance). Les canaux partagés héritent de la stratégie de l’organisation hôte.

### <a name="conditional-access"></a>Accès conditionnel

Les [stratégies d’accès conditionnel prises](/azure/active-directory/conditional-access/overview) en charge par l’organisation hôte peuvent être appliquées aux utilisateurs de connexion directe B2B. (Les stratégies de l’organisation externe ne sont pas utilisées.) Les types suivants de stratégies d’accès conditionnel sont pris en charge avec les canaux partagés :

- Stratégies étendues à **tous les utilisateurs invités et externes**, ainsi qu’à **l’application cloud Office 365 SharePoint Online**.
- Accordez des contrôles Access qui nécessitent l’authentification multifacteur, un appareil conforme ou un appareil joint à Azure AD hybride.

Les stratégies basées sur IP sont prises en charge au niveau du fichier SharePoint. Ainsi, un participant externe peut accéder au canal partagé à partir d’un emplacement restreint, mais être bloqué lors de la tentative d’ouverture d’un fichier.

Pour plus d’informations sur l’accès conditionnel pour les identités externes, consultez [Authentification et Accès conditionnel pour les identités externes](/azure/active-directory/external-identities/authentication-conditional-access).

### <a name="data-loss-prevention-dlp"></a>Protection contre la perte de données (DLP)

Les administrateurs peuvent appliquer [Microsoft Purview stratégies DLP](/microsoft-365/compliance/dlp-policy-design) à une équipe où tous les canaux, y compris les canaux partagés, héritent de la stratégie. Les canaux partagés héritent de la stratégie de l’organisation hôte.

### <a name="retention-policy"></a>Stratégie de rétention

Les administrateurs peuvent appliquer une [stratégie de rétention](/microsoft-365/compliance/retention) sur une équipe où tous les canaux, y compris les canaux partagés, héritent de la stratégie de rétention. Les canaux partagés héritent de la stratégie de l’équipe parente.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

[Les étiquettes de confidentialité](/microsoft-365/compliance/sensitivity-labels) disponibles dans l’organisation hôte sont les seules étiquettes qui peuvent être appliquées aux documents dans un site de canal partagé. Un fichier chiffré par une étiquette de confidentialité ne peut pas être ouvert par des participants externes. L’étiquetage automatique n’est pas utilisé.

Les canaux partagés et leurs sites SharePoint associés héritent de l’étiquette de l’équipe parente.

### <a name="information-barriers"></a>Obstacles aux informations

Les utilisateurs qui ne sont pas autorisés à communiquer par [stratégies d’obstacle à l’information](/microsoftteams/information-barriers-in-teams) ne peuvent pas faire partie du canal partagé. Les stratégies d’obstacle à l’information ne sont efficaces que pour les utilisateurs de l’organisation hôte. Si les utilisateurs sont des participants externes dans le canal partagé d’une autre organisation, les stratégies de barrière à l’information ne s’appliquent pas.

### <a name="ediscovery"></a>eDiscovery

Les administrateurs peuvent effectuer des recherches pour tous les utilisateurs du canal. Tous les canaux, y compris le canal partagé, sont détectables. Toutes les données de message dans le canal, quelle que soit la personne qui a ajouté les données, sont détectables par l’administrateur de conformité.

### <a name="legal-hold"></a>Conservation légale

Les administrateurs peuvent placer les membres du canal uniquement de l’organisation hôte qui ne font pas partie de l’équipe en attente. Ils peuvent également [mettre toute l’équipe en attente](/MicrosoftTeams/legal-hold). Les administrateurs ne peuvent pas mettre un participant externe en attente.

### <a name="audit-logs"></a>Journaux d'audit

Toutes les actions effectuées pour les [événements d’audit existants](/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log) sont auditées dans des canaux partagés.

## <a name="related-topics"></a>Voir aussi

[Introduction à la collaboration de fichiers dans Microsoft 365](/sharepoint/intro-to-file-collaboration)

[Planifier la collaboration de fichiers dans SharePoint avec Microsoft 365](/sharepoint/deploy-file-collaboration)
