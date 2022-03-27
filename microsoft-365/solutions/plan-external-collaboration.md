---
title: Planifier la collaboration externe
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
description: Planifiez les options de collaboration externe à utiliser dans Microsoft 365.
ms.openlocfilehash: 56999f3acda0da4f801f3a7ec171c73fe05943a3
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716058"
---
# <a name="plan-external-collaboration"></a>Planifier la collaboration externe

Microsoft 365 offre plusieurs options pour collaborer avec des personnes extérieures à votre organisation :

- 1:1 et conversation de groupe dans Teams avec des personnes extérieures à votre organisation
- Teams réunions avec des personnes extérieures à votre organisation
- Partage de fichiers ou de dossiers individuels avec des personnes extérieures à votre organisation
- Collaboration en équipe, avec conversations de canal, collaboration sur des fichiers et applications partagées

Cet article couvre la quatrième option, la collaboration de groupe avec les conversations de canal, la collaboration sur les fichiers et les applications partagées. 

## <a name="terms"></a>Conditions générales

- **Azure AD collaboration B2B** : fonctionnalité qui permet aux utilisateurs de partager des fichiers, des dossiers, des sites, des groupes et des équipes avec des personnes extérieures à votre organisation. Ces personnes accèdent aux ressources partagées à l’aide de comptes invités dans votre annuaire.
- **Azure AD connexion directe B2B** : fonctionnalité qui permet aux utilisateurs de partager des ressources dans votre organisation avec des personnes d’autres Azure AD organisations. Ces personnes accèdent aux ressources partagées à l’aide de leur propre compte scolaire ou scolaire. Aucun compte invité n’est créé dans votre organisation.
- **Participant externe** ( une personne extérieure à votre organisation qui participe à une ressource, telle qu’un canal partagé), à l’aide de sa propre identité et non d’un compte invité dans votre annuaire.
- **Organisation externe** : autre organisation avec qui vous partagez des ressources.
- **Invité** : personne extérieure à votre organisation qui accède aux ressources partagées en se signant à un compte invité dans votre annuaire.
- **Organisation hôte** : l’organisation qui héberge une ressource partagée, telle qu’un canal partagé.
- **Canal partagé** : canal Teams qui peut être partagé avec des personnes extérieures à l’équipe. Ces personnes peuvent se trouver au sein de votre organisation ou d’autres Azure AD organisations.
- **Partage de liens** : liens avec des autorisations sur un fichier ou un dossier qui sont utilisés pour partager ce fichier ou ce dossier avec d’autres personnes. Les personnes avec qui le partage est partagé peuvent se trouver à l’intérieur ou à l’extérieur de votre organisation.

## <a name="options-for-collaboration-in-a-team"></a>Options de collaboration dans une équipe

Lorsque vous collaborez en équipe avec des personnes extérieures à votre organisation, deux options s’offrent à vous pour accéder aux ressources que vous partagez avec eux.

**Partage d’invités**

Le partage d’invités Azure AD la collaboration B2B pour permettre le partage et la collaboration avec des personnes extérieures à votre organisation en ajoutant un compte d’invité Azure AD pour chaque personne. Les comptes invités peuvent être utilisés pour les raisons suivantes :

- Appartenance à des équipes, SharePoint sites et groupes Microsoft 365 invités
- Partage de fichiers et de dossiers individuel

Les invités d’une équipe ont des fonctionnalités similaires aux membres réguliers de l’équipe.

**Participants externes dans les canaux partagés**

Les participants externes accèdent aux ressources partagées dans votre organisation à l’aide de Azure AD ou Microsoft 365 identité. Cela est activé par une connexion Azure AD B2B directe via une relation organisationnelle configurée par les deux organisations. Les comptes invités ne sont pas utilisés dans cette relation.

Le principal avantage des participants externes dans les canaux partagés par rapport au partage d’invités est que les personnes extérieures à votre organisation peuvent collaborer avec vos utilisateurs dans Teams sans avoir à modifier leur contexte utilisateur. Lorsque vous utilisez des comptes invités, les utilisateurs doivent se Teams avec leur compte scolaire ou scolaire et se connectent à nouveau à l’aide du compte invité. Ils peuvent également avoir une copie distincte des Teams en cours d’exécution dans une session de navigateur privé. Ce basculement entre les organisations prend du temps et peut entraîner l’insignation des communications importantes par les utilisateurs lorsqu’ils sont en communication avec une organisation donnée.

Avec les canaux partagés, les utilisateurs peuvent rester en ligne avec leur organisation et accéder aux canaux partagés avec eux à partir d’autres organisations. Les canaux partagés d’autres organisations sont disponibles Teams aux côtés des équipes et des canaux de votre organisation. Il n’est pas nécessaire de changer d’organisation.

## <a name="feature-comparison"></a>Comparaison des fonctionnalités

Le tableau suivant décrit les expériences disponibles en fonction du type de compte utilisé.

|Fonctionnalité|Utilisateur (votre organisation)|Invité (Azure AD collaboration)|Participant externe (Azure AD connexion directe)|
|:-----|:-----|:------|:-------|
|Accès à l’équipe|v|v|N|
|Accès au canal partagé|v|N|v|
|Autorisations par le biais de liens de partage de fichiers|v|v|N|
|Utiliser des canaux partagés|v|N|v|
|Utiliser des canaux privés|v|v|N|
|Compte dans votre annuaire|v|v|N|
|Révisions accès|v|v|v|
            
## <a name="planning-considerations"></a>Considérations sur la planification

La plupart des organisations utilisent à la fois le partage d’invités et les canaux partagés avec des participants externes. 

Le partage d’invités est activé par défaut dans Azure AD et dans Microsoft 365 (Teams, Microsoft 365 groupes et SharePoint). Cela permet aux utilisateurs d’inviter des invités à des équipes et des sites, et de partager des fichiers avec eux sans avoir à demander de l’aide de la part de l’informatique.

Vous devez utiliser le partage d’invités si :
- Vous souhaitez inviter des personnes extérieures à votre organisation à l’équipe plutôt qu’à des canaux individuels
- Vous souhaitez partager des fichiers ou des dossiers dans un canal avec des personnes extérieures à votre organisation qui ne sont pas dans le canal
- Vous souhaitez collaborer avec des personnes extérieures à votre organisation qui n’ont pas de compte scolaire ou scolaire.

Bien que les canaux partagés sont allumés par défaut dans Teams, la collaboration externe avec les canaux partagés nécessite qu’un administrateur Azure AD configurer l’accès entre les locataires entre votre organisation et l’autre organisation avec laquelle vous souhaitez partager. Les autres organisations doivent également configurer l’accès entre locataires à leur fin.

Si vous envisagez d’utiliser des canaux partagés avec d’autres organisations, vous pouvez choisir entre un modèle en libre-service et un modèle par demande.

- Libre-service : vous pouvez configurer l’accès entre clients pour autoriser l’accès entrant et sortant à toutes les autres Azure AD organisation. Vous pouvez également bloquer une liste d’organisations avec qui vous ne souhaitez pas que vos utilisateurs partagent, en laissant toutes les autres organisations disponibles. Cela permet à vos utilisateurs d’inviter des personnes extérieures à l’organisation à participer à des canaux partagés sans avoir à contacter votre service d’aide ou votre service informatique.
- Sur demande : vous pouvez configurer l’accès entre clients pour chaque organisation avec laquelle vous souhaitez autoriser les canaux partagés. Lorsque vous choisissez ce modèle, il est important d’avoir un processus d’entreprise documenté que vos utilisateurs peuvent suivre pour demander un accès entre clients avec une autre organisation.

## <a name="compliance-in-shared-channels"></a>Conformité dans les canaux partagés

Les canaux partagés sont intégrés aux fonctionnalités Microsoft 365 conformité.

##### <a name="communications-compliance"></a>Conformité des communications

Les administrateurs peuvent définir des stratégies pour surveiller le contenu de tous les utilisateurs du canal. Tous les messages contenus dans les canaux, y compris le canal partagé, sont couverts par les [stratégies de conformité des communications](/microsoft-365/compliance/communication-compliance). Les canaux partagés héritent de la stratégie de l’organisation hôte.

##### <a name="conditional-access"></a>Accès conditionnel

Les stratégies d’accès [conditionnel](/azure/active-directory/conditional-access/overview) de l’organisation hôte sont appliquées aux participants externes, y compris aux utilisateurs de connexion directe B2B. Les stratégies de l’organisation externe ne sont pas utilisées. Les types de stratégies d’accès conditionnel suivants sont pris en charge avec les canaux partagés :

- Stratégies étendues à tous les utilisateurs invités, participants externes, SharePoint applications cloud online
- Accorder des contrôles d’accès qui nécessitent une mf, un appareil conforme ou un appareil Azure AD joint. 

Les stratégies IP sont pris en charge au niveau SharePoint fichier. Ainsi, un participant externe peut accéder au canal partagé à partir d’un emplacement restreint, mais être bloqué lors de la tentative d’ouverture d’un fichier.

##### <a name="data-loss-prevention-dlp"></a>Protection contre la perte de données (DLP)

Les administrateurs peuvent appliquer [des stratégies DLP](/microsoft-365/compliance/dlp-policy-design) à une équipe où tous les canaux, y compris les canaux partagés, héritent de la stratégie. Les canaux partagés héritent de la stratégie de l’organisation hôte.

##### <a name="retention-policy"></a>Stratégie de rétention

Les administrateurs peuvent appliquer une stratégie [de rétention](/microsoft-365/compliance/retention) à une équipe où tous les canaux, y compris les canaux partagés, héritent de la stratégie de rétention. Les canaux partagés héritent de la stratégie de l’équipe parente.

##### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

[Les étiquettes de niveau de](/microsoft-365/compliance/sensitivity-labels) sensibilité disponibles dans l’organisation hôte sont les seules étiquettes qui peuvent être appliquées aux documents dans un site de canal partagé. Un fichier chiffré par une étiquette de sensibilité ne peut pas être ouvert par des participants externes. L’étiquetage automatique n’est pas utilisé.

Les canaux partagés et leurs sites SharePoint héritent de l’étiquette de l’équipe parente.

##### <a name="information-barriers"></a>Obstacles aux informations

Les utilisateurs qui ne sont pas autorisés à communiquer par stratégie de [obstacle à l’information](/microsoftteams/information-barriers-in-teams) ne peuvent pas faire partie du canal partagé. Les stratégies de obstacle à l’information ne sont efficaces que pour les utilisateurs de l’organisation hôte. Si les utilisateurs sont des participants externes au canal partagé d’une autre organisation, les stratégies de obstacle aux informations ne s’appliquent pas.

##### <a name="ediscovery"></a>eDiscovery

Les administrateurs peuvent effectuer des recherches pour tous les utilisateurs du canal. Tous les canaux, y compris le canal partagé, sont découvrables. Toutes les données de message dans le canal, quelle que soit la personne qui a ajouté les données, sont découvrables par l’administrateur de conformité.

##### <a name="legal-hold"></a>Conservation légale

Les administrateurs peuvent placer en attente des membres de canal uniquement de l’organisation hôte qui ne font pas partie de l’équipe. Ils peuvent également [placer l’ensemble de l’équipe en attente](/MicrosoftTeams/legal-hold). Les administrateurs ne peuvent pas placer un participant externe en attente.

##### <a name="audit-logs"></a>Journaux d'audit

Toutes les actions effectuées pour les [événements d’audit](/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log) existants sont auditées dans des canaux partagés.


## <a name="related-topics"></a>Sujets associés

[Introduction à la collaboration sur les fichiers dans Microsoft 365](/sharepoint/intro-to-file-collaboration)

[Planifier la collaboration de fichiers SharePoint avec Microsoft 365](/sharepoint/deploy-file-collaboration)
