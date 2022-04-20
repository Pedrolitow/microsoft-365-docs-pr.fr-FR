---
title: Options de conformité pour les groupes Microsoft 365, les Teams et la collaboration SharePoint
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Découvrez les options de conformité pour les groupes Microsoft 365, les Teams et la collaboration SharePoint.
ms.openlocfilehash: afbbc6e507d613e028f65dbc157ec2222414af8c
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939123"
---
# <a name="compliance-options-for-microsoft-365-groups-teams-and-sharepoint-collaboration"></a>Options de conformité pour les groupes Microsoft 365, les Teams et la collaboration SharePoint

Microsoft 365 offre une suite complète d’outils pour maintenir la conformité à mesure que vos utilisateurs collaborent. Passez en revue ces options et réfléchissez à la façon dont elles correspondent à vos besoins métier, à la sensibilité de vos données et à l’étendue des personnes avec lesquelles vos utilisateurs doivent collaborer.

Le tableau suivant fournit une référence rapide pour les contrôles de conformité disponibles dans Microsoft 365. Des informations supplémentaires sont fournies dans les sections suivantes.

|Catégorie|Description|Référence|
|:-------|:----------|:--------|
|Conservation des informations|||
||Conserver le contenu de messagerie et de SharePoint des groupes|[En savoir plus sur les stratégies de rétention dans SharePoint et OneDrive](../compliance/retention-policies-sharepoint.md)|
||Conserver la conversation et les messages|[En savoir plus sur les stratégies de rétention dans Microsoft Teams](../compliance/retention-policies-teams.md)|
|Classification des informations|||
||Classifier des groupes et des équipes|[Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Classifier automatiquement le contenu sensible|[Appliquer automatiquement une étiquette de confidentialité à du contenu](../compliance/apply-sensitivity-label-automatically.md)|
||Chiffrer le contenu sensible|[Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité](../compliance/encryption-sensitivity-labels.md)|
|Protection des informations|||
||Empêcher la perte d’informations sensibles|[En savoir plus sur la protection contre la perte de données Microsoft Purview](../compliance/dlp-learn-about-dlp.md)|
||Protéger les informations sensibles dans la conversation.|[Protection contre la perte de données Microsoft Purview et Microsoft Teams](../compliance/dlp-microsoft-teams.md)|
||Définir les informations sensibles de votre organisation|[Types d’informations sensibles personnalisés](../compliance/sensitive-information-type-learn-about.md)|
|Segmentation des utilisateurs|||
||Restreindre la communication entre les segments d’utilisateur|[Obstacles aux informations](../compliance/information-barriers.md)|
|Résidence de données|||
||Stocker des données dans des emplacements géographiques spécifiques|[Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)|

## <a name="information-retention"></a>Conservation des informations

Des stratégies de rétention sont disponibles pour conserver ou supprimer les éléments utilisés pour la collaboration dans les groupes et les équipes, y compris les fichiers, les messages et le courrier. Les stratégies peuvent être définies pour conserver et supprimer, conserver uniquement ou supprimer uniquement. Les informations couvertes par une stratégie de rétention sont protégées en cas d’expiration ou de suppression du groupe ou de l’équipe.

La configuration d’une stratégie de rétention pour Groupes Microsoft 365 couvre la boîte aux lettres de groupe et le site et les fichiers SharePoint associés.

- [En savoir plus sur les stratégies de rétention dans SharePoint et OneDrive](../compliance/retention-policies-sharepoint.md)

Stratégies de rétention pour Teams conserver les messages de conversation et de canal. Bien que les messages de conversation et de canal soient stockés dans Exchange boîtes aux lettres, ils ne sont pas affectés par Exchange stratégies de rétention. Vous devez définir vos stratégies de rétention à appliquer aux conversations Teams et aux messages de canal Teams. 

Les conversations utilisateur sont conservées indéfiniment même si un compte d’utilisateur est supprimé. Si vous ne souhaitez pas conserver ces données indéfiniment, envisagez d’utiliser une stratégie de rétention pour supprimer les conversations utilisateur après une heure spécifiée ou inclure cette suppression dans votre processus de suppression d’utilisateur.

- [En savoir plus sur les stratégies de rétention dans Microsoft Teams](../compliance/retention-policies-teams.md)

- [Stratégies de rétention dans Microsoft Teams](/microsoftteams/retention-policies)

Une stratégie de rétention unique peut être définie pour s’appliquer à Teams conversation et Teams messages de canal. 

Ressources supplémentaires :

- [Découvrir les stratégies de rétention](../compliance/retention.md)

- [Balises de rétention et stratégies de rétention](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) dans Exchange

## <a name="information-classification"></a>Classification des informations

Vous pouvez utiliser des étiquettes de confidentialité pour régir l’accès invité, la confidentialité des groupes et des équipes, ainsi que l’accès par des appareils non gérés pour les groupes et les équipes. En appliquant l’étiquette, ces paramètres sont automatiquement configurés comme spécifié par les paramètres d’étiquette.

- [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)

Vous pouvez configurer Microsoft 365 pour appliquer automatiquement des étiquettes de confidentialité aux fichiers et e-mails en fonction des critères que vous spécifiez, notamment la détection des types d’informations sensibles ou la mise en correspondance de modèles avec des classifieurs pouvant être formés.

- [Appliquer automatiquement une étiquette de confidentialité à du contenu](../compliance/apply-sensitivity-label-automatically.md)

Vous pouvez utiliser des étiquettes de confidentialité pour chiffrer les fichiers, en autorisant uniquement les personnes disposant d’autorisations à les déchiffrer et à les lire.

- [Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité](../compliance/encryption-sensitivity-labels.md)

- [Configurer une équipe avec l’isolation de sécurité](./secure-teams-security-isolation.md)

Ressources supplémentaires :

- [En savoir plus sur les étiquettes de niveau de confidentialité](../compliance/sensitivity-labels.md)


## <a name="information-protection"></a>Protection des informations

Les stratégies DLP peuvent empêcher le partage accidentel d’informations sensibles entre SharePoint, Exchange et Teams. Vous pouvez créer des stratégies qui spécifient des actions à entreprendre (telles que le blocage de l’accès) en fonction d’un ensemble de règles.

- [En savoir plus sur la prévention des pertes de données](../compliance/dlp-learn-about-dlp.md)

DLP dans Teams peut aider à protéger les informations sensibles dans Teams les messages de conversation et de canal en supprimant les messages qui contiennent des informations sensibles.

- [Protection contre la perte de données et Microsoft Teams](../compliance/dlp-microsoft-teams.md)

Si vous avez des informations sensibles propres à votre organisation, telles que des noms de code de projet, vous pouvez créer vos propres types d’informations sensibles et les appliquer aux stratégies DLP pour protéger le contenu dans les groupes, les équipes et les SharePoint.

- [Types d’informations sensibles personnalisés](../compliance/sensitive-information-type-learn-about.md)

## <a name="user-segmentation"></a>Segmentation des utilisateurs

Avec les obstacles à l’information, vous pouvez segmenter vos données et vos utilisateurs pour limiter la communication et la collaboration indésirables entre les groupes et éviter les conflits d’intérêt au sein de votre organisation. Les obstacles à l’information vous permettent de créer des stratégies pour autoriser ou empêcher la collaboration de fichiers, les conversations, les appels ou les invitations à une réunion entre des groupes de personnes de votre organisation.

- [Obstacles aux informations](../compliance/information-barriers.md)

- [Cloisonnement de l’information dans Microsoft Teams](/microsoftteams/information-barriers-in-teams)

- [Utiliser les obstacles à l’information avec SharePoint](/sharepoint/information-barriers)

## <a name="data-residency"></a>Résidence de données

Avec Microsoft 365 multigéographique, vous pouvez approvisionner et stocker des données au repos dans les emplacements géographiques que vous avez choisis pour répondre aux exigences de résidence des données. Dans un environnement multigéographique, votre locataire Microsoft 365 se compose d’un emplacement central (où votre abonnement Microsoft 365 a été initialement approvisionné) et d’un ou plusieurs emplacements satellites où vous pouvez stocker des données.

- [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)

- [Plan pour Microsoft 365 Multi-Geo](/microsoft-365/enterprise/plan-for-multi-geo)

## <a name="related-topics"></a>Sujets associés

[Recommandations en matière de planification de la gouvernance de collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Sécurité et conformité des Exchange Online](/exchange/security-and-compliance/security-and-compliance)

[Protéger les informations](../compliance/information-protection.md)
