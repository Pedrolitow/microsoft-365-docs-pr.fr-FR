---
title: Options de conformité pour Microsoft 365 groupes, Teams et la collaboration SharePoint de conformité
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
description: Découvrez les options de conformité pour Microsoft 365 groupes, Teams et SharePoint collaboration.
ms.openlocfilehash: a9a94f0c1886ac5b60292f5f4d4b9b9d6d84380c
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52241675"
---
# <a name="compliance-options-for-microsoft-365-groups-teams-and-sharepoint-collaboration"></a>Options de conformité pour Microsoft 365 groupes, Teams et la collaboration SharePoint de conformité

Microsoft 365 offre une suite complète d’outils pour maintenir la conformité à mesure que vos utilisateurs collaborent. Examinez ces options et réfléchissez à la façon dont elles s’miquent aux besoins de votre entreprise, à la sensibilité de vos données et à l’étendue des personnes avec qui vos utilisateurs doivent collaborer.

Le tableau suivant fournit une référence rapide pour les contrôles de conformité disponibles dans Microsoft 365. Des informations supplémentaires sont fournies dans les sections suivantes.

|Catégorie|Description|Référence|
|:-------|:----------|:--------|
|Rétention des informations|||
||Conserver les messages et le contenu SharePoint groupes|[En savoir plus sur les stratégies de rétention dans SharePoint et OneDrive](../compliance/retention-policies-sharepoint.md)|
||Conserver la conversation et les messages|[En savoir plus sur les stratégies de rétention dans Microsoft Teams](../compliance/retention-policies-teams.md)|
|Classification des informations|||
||Classifier les groupes et les équipes|[Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Classifier automatiquement le contenu sensible|[Appliquer automatiquement une étiquette de confidentialité à du contenu](../compliance/apply-sensitivity-label-automatically.md)|
||Chiffrer le contenu sensible|[Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité](../compliance/encryption-sensitivity-labels.md)|
|Protection des informations|||
||Empêcher la perte d’informations sensibles|[En savoir plus sur la protection contre la perte de données](../compliance/dlp-learn-about-dlp.md)|
||Protéger les informations sensibles dans la conversation.|[Prévention des pertes de données et Microsoft Teams](../compliance/dlp-microsoft-teams.md)|
||Définir les informations sensibles de votre organisation|[Types d’informations sensibles personnalisés](../compliance/sensitive-information-type-learn-about.md)|
|Segmentation des utilisateurs|||
||Restreindre la communication entre les segments d’utilisateurs|[Obstacles aux informations](../compliance/information-barriers.md)|
|Résidence de données|||
||Stocker des données dans des emplacements géographiques spécifiques|[Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)|

## <a name="information-retention"></a>Rétention des informations

Les stratégies de rétention sont disponibles pour conserver ou supprimer des éléments utilisés pour la collaboration dans des groupes et des équipes, y compris des fichiers, des messages et du courrier. Les stratégies peuvent être définies pour conserver et supprimer, conserver uniquement ou supprimer uniquement. Les informations couvertes par une stratégie de rétention sont protégées en cas d’expiration ou de suppression du groupe ou de l’équipe.

La configuration d’une stratégie de rétention pour Microsoft 365 groupes couvre la boîte aux lettres de groupe et le site et les fichiers SharePoint associés.

- [En savoir plus sur les stratégies de rétention dans SharePoint et OneDrive](../compliance/retention-policies-sharepoint.md)

Les stratégies de rétention Teams conserver les messages de conversation et de canal. Bien que les messages de conversation et de canal soient stockés dans Exchange boîtes aux lettres, ils ne sont pas affectés Exchange stratégies de rétention. Vous devez définir vos stratégies de rétention pour qu’Teams conversations et Teams messages du canal de rétention. 

Les conversations utilisateur sont conservées indéfiniment, même si un compte d’utilisateur est supprimé. Si vous ne souhaitez pas conserver ces données indéfiniment, envisagez d’utiliser une stratégie de rétention pour supprimer les conversations utilisateur après une période spécifiée ou incluez cette suppression dans votre processus de suppression d’utilisateur.

- [En savoir plus sur les stratégies de rétention dans Microsoft Teams](../compliance/retention-policies-teams.md)

- [Stratégies de rétention dans Microsoft Teams](/microsoftteams/retention-policies)

Une stratégie de rétention unique peut être définie pour s’appliquer Teams conversation et Teams messages de canal. 

Ressources supplémentaires :

- [Découvrir les stratégies de rétention](../compliance/retention.md)

- [Balises et stratégies de](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) rétention dans Exchange

## <a name="information-classification"></a>Classification des informations

Vous pouvez utiliser des étiquettes de confidentialité pour régir l’accès invité, la confidentialité des groupes et des équipes, et l’accès par des appareils nonmanagés pour les groupes et les équipes. En appliquant l’étiquette, ces paramètres sont automatiquement configurés comme spécifié par les paramètres d’étiquette.

- [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)

Vous pouvez configurer des Microsoft 365 pour appliquer automatiquement des étiquettes de sensibilité aux fichiers et aux e-mails en fonction des critères que vous spécifiez, y compris la détection de types d’informations sensibles ou la correspondance de modèles avec des classifieurs entraidables.

- [Appliquer automatiquement une étiquette de confidentialité à du contenu](../compliance/apply-sensitivity-label-automatically.md)

Vous pouvez utiliser des étiquettes de niveau de sensibilité pour chiffrer des fichiers, ce qui permet uniquement aux personnes autorisées de les déchiffrer et de les lire.

- [Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité](../compliance/encryption-sensitivity-labels.md)

- [Configurer une équipe avec l’isolation de sécurité](./secure-teams-security-isolation.md)

Ressources supplémentaires :

- [En savoir plus sur les étiquettes de niveau de confidentialité](../compliance/sensitivity-labels.md)


## <a name="information-protection"></a>Protection des informations

Les stratégies DLP peuvent empêcher le partage accidentel d’informations sensibles entre SharePoint, Exchange et Teams. Vous pouvez créer des stratégies qui spécifient les actions à prendre (par exemple, le blocage d’accès) en fonction d’un ensemble de règles.

- [En savoir plus sur la protection contre la perte de données](../compliance/dlp-learn-about-dlp.md)

La protection contre la Teams peut aider à protéger les informations sensibles dans Teams messages de conversation et de canal en supprimant les messages qui contiennent des informations sensibles.

- [Prévention des pertes de données et Microsoft Teams](../compliance/dlp-microsoft-teams.md)

Si vous avez des informations sensibles propres à votre organisation, telles que des noms de code de projet, vous pouvez créer vos propres types d’informations sensibles et les appliquer aux stratégies DLP pour protéger le contenu dans les groupes, les équipes et SharePoint.

- [Types d’informations sensibles personnalisés](../compliance/sensitive-information-type-learn-about.md)

## <a name="user-segmentation"></a>Segmentation des utilisateurs

Avec les obstacles à l’information, vous pouvez segmenter vos données et vos utilisateurs afin de restreindre la communication et la collaboration indésirables entre les groupes et d’éviter les conflits d’intérêt dans votre organisation. Les obstacles à l’information vous permettent de créer des stratégies pour autoriser ou empêcher la collaboration sur des fichiers, des conversations, des appels ou des invitations à des réunions entre des groupes de personnes de votre organisation.

- [Obstacles aux informations](../compliance/information-barriers.md)

- [Cloisonnement de l’information dans Microsoft Teams](/microsoftteams/information-barriers-in-teams)

- [Utiliser les obstacles aux informations avec SharePoint](/sharepoint/information-barriers)

## <a name="data-residency"></a>Résidence de données

Avec Microsoft 365 multigéogé, vous pouvez mettre en service et stocker des données au repos dans les emplacements géographiques que vous avez choisis pour répondre aux exigences de résidence des données. Dans un environnement Multi-Géo, votre client Microsoft 365 se compose d’un emplacement central (où votre abonnement Microsoft 365 a été initialement provisioné) et d’un ou plusieurs emplacements satellites où vous pouvez stocker des données.

- [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)

- [Plan pour Microsoft 365 Multi-Geo](/microsoft-365/enterprise/plan-for-multi-geo)

## <a name="related-topics"></a>Voir aussi

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Sécurité et conformité pour les Exchange Online](/exchange/security-and-compliance/security-and-compliance)

[Protéger les informations](../compliance/information-protection.md)
