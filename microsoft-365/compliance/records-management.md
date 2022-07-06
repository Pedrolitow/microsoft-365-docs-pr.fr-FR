---
title: En savoir plus sur la gestion des enregistrements Microsoft Purview
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- admindeeplinkCOMPLIANCE
- seo-marvel-apr2020
- seo-marvel-jun2020
description: Découvrez comment la gestion des enregistrements Microsoft Purview prend en charge les éléments à valeur élevée pour les exigences de conservation des enregistrements métier, légales ou réglementaires.
ms.openlocfilehash: 1a9d37f138647a36fb7440f15fd74851957b542f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642325"
---
# <a name="learn-about-records-management"></a>Découvrez la gestion des enregistrements

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!TIP]
> *Saviez-vous que vous pouvez essayer les versions Premium des neuf solutions Microsoft Purview gratuitement ?* Utilisez la version d’évaluation des solutions Purview de 90 jours pour découvrir comment des fonctionnalités Purview robustes peuvent aider votre organisation à répondre à ses besoins de conformité. Microsoft 365 E3 et Office 365 E3 clients peuvent être démarrés maintenant sur le [Hub d’essais du portail de conformité Microsoft Purview](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). Découvrez plus d’informations sur [les personnes qui peuvent s’inscrire et les conditions d’évaluation](compliance-easy-trials.md).

Les organisations de tous types ont besoin d'une solution de gestion des documents pour gérer les documents réglementaires, juridiques et critiques pour l'entreprise dans l'ensemble de leurs données d'entreprise. La gestion des enregistrements pour Microsoft Purview aide une organisation à gérer ses obligations légales, lui donne la possibilité de démontrer sa conformité aux réglementations et augmente l'efficacité en éliminant régulièrement les éléments qui ne doivent plus être conservés, qui n'ont plus de valeur ou qui ne sont plus nécessaires à l'activité de l'entreprise.

Utilisez les fonctionnalités suivantes pour prendre en charge votre solution de gestion des enregistrements pour les services et applications Microsoft 365 :

- **Étiquetez le contenu en tant qu’enregistrement**. Créez et configurez des étiquettes de rétention pour indiquer que le contenu est un [enregistrement](#records) qui peut ensuite être appliqué par les utilisateurs ou appliqué automatiquement en identifiant les informations sensibles, les mots clés ou les types de contenu.

- **Migrez et gérez vos exigences de rétention à l’aide d’un plan de gestion des fichiers**. L’utilisation d’un [plan de gestion des fichiers](file-plan-manager.md) vous permet de mettre en place un plan de rétention existant dans Microsoft 365 ou d’en créer un nouveau pour les fonctionnalités de gestion améliorées.

- **Configurez les paramètres de rétention et de suppression à l’aide des étiquettes de rétention**. Configurez les [étiquettes de rétention](retention.md#retention-labels) avec des périodes de rétention et des actions basées sur divers facteurs tels que la date de la dernière modification ou création.

- **Démarrer différentes périodes de rétention lorsqu’un événement se produit** avec [rétention basée sur des événements](event-driven-retention.md).

- **Vérifier et valider la destruction** en effectuant une [révision avant destruction](disposition.md#disposition-reviews) et la preuve de la [suppression d’enregistrements](disposition.md#disposition-of-records).

- **Exporter des informations sur tous les éléments supprimés** avec l’[option exporter](disposition.md#filter-and-export-the-views).

- **Définir des autorisations spécifiques** afin que les fonctions de gestionnaire d’enregistrements au sein de votre organisation [disposent du droit d’accès](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

Grâce à ces capacités, vous pouvez intégrer les calendriers de rétention et les exigences de votre organisation dans une solution de gestion des documents qui gère la rétention, la déclaration et l'élimination des enregistrements, afin de prendre en charge le cycle de vie complet de votre contenu.

En plus de la documentation en ligne, vous trouverez peut-être utile de télécharger une [série de diapositives des FAQs](https://aka.ms/MIPC/Blog-RecordsManagementWebinar) à partir d’un webinaire de gestion des enregistrements. L’enregistrement du webinaire réel n’est plus disponible.

## <a name="records"></a>Enregistrements

Lorsque le contenu est déclaré comme enregistrement:

- Des restrictions sont appliquées aux éléments en ce qui concerne les [actions autorisées ou bloquées](#compare-restrictions-for-what-actions-are-allowed-or-blocked).

- Des activités supplémentaires sur l’élément sont enregistrées.

- Vous avez une preuve de destruction lorsque les éléments sont supprimés à la fin de la période de rétention.

Vous utilisez les [étiquettes de rétention](retention.md#retention-labels) pour marquer le contenu comme **enregistrement**, ou **enregistrement réglementaire**. La différence entre ces deux éléments est expliquée dans la section suivante. Vous pouvez soit publier ces étiquettes pour permettre aux utilisateurs et aux administrateurs de les appliquer manuellement au contenu, ou appliquer automatiquement ces étiquettes au contenu que vous voulez marquer comme enregistrement ou enregistrement réglementaire.

En utilisant des étiquettes de rétention pour marquer du contenu en tant qu’enregistrement, vous pouvez implémenter une stratégie unique et cohérente pour la gestion des enregistrements dans votre environnement Microsoft 365.

### <a name="compare-restrictions-for-what-actions-are-allowed-or-blocked"></a>Comparer des restrictions relatives aux actions autorisées ou bloquées

Utilisez le tableau suivant pour identifier les restrictions placées sur du contenu suite à l’application d’une étiquette de rétention standard, ainsi que les étiquettes de rétention qui marquent du contenu en tant qu’enregistrement ou enregistrement réglementaire. 

Une étiquette de rétention standard comporte des paramètres et des actions de rétention mais ne marque pas du contenu comme enregistrement ou enregistrement réglementation.

> [!NOTE]
> Pour couvrir tous les cas de figure, le tableau inclut les colonnes d’un enregistrement verrouillé et déverrouillé, applicable à SharePoint et OneDrive, mais pas à Exchange. La possibilité de verrouiller et de déverrouiller un enregistrement utilise le [contrôle de version](record-versioning.md) qui n’est pas pris en charge pour les éléments Exchange. Par conséquent, pour tous les éléments Exchange marqués en tant qu’enregistrement, le comportement mappe vers l’**Enregistrement – colonne verrouillée**, et l’**Enregistrement – colonne déverrouillée** n’est pas pertinent.


|Action| Étiquette de rétention |Enregistrement – colonne verrouillée| Enregistrement – colonne déverrouillée| Enregistrement réglementaire |
|:-----|:-----|:-----|:-----|:-----|:-----|
|Modifier les contenus|Autorisé | **Bloqué** | Autorisé | **Bloqué**|
|Modifier les propriétés, y compris Renommer|Autorisé |<sup>1</sup> autorisé | Autorisé | **Bloqué**|
|Supprimer|<sup>2</sup> autorisé |**Bloqué** |**Bloqué**| **Bloqué**|
|Copier|Autorisé |Autorisé | Autorisé| Autorisé|
|Déplacer au sein du conteneur <sup>3</sup>|Autorisé |Autorisé | Autorisé| Autorisé|
|Déplacer sur les conteneurs <sup>3</sup>|Autorisé |Autorisé si jamais déverrouillé | **Bloqué** | **Bloqué**|
|Ouvert/lu|Autorisé |Autorisé | Autorisé| Autorisé|
|Modifier l’étiquette|Autorisé |Autorisé – administrateur de conteneur uniquement | **Bloqué**| **Bloqué**
|Supprimer l’étiquette|Autorisé |Autorisé – administrateur de conteneur uniquement | **Bloqué**| **Bloqué**

Notes de bas de page :

<sup>1</sup> Les propriétés de modification d’un enregistrement verrouillé sont autorisées par défaut, mais peuvent être bloquées par un paramètre client dans le [Portail de conformité Microsoft Purview](https://compliance.microsoft.com/) > **Gestion des enregistrements** > **Paramètres de gestion des enregistrements** > **Étiquettes de rétention** > **Autoriser la modification des propriétés d’enregistrement**.

<sup>2</sup> La suppression d’éléments étiquetés dans SharePoint et OneDrive peut être bloquée en tant que paramètre client dans le [Portail de conformité Microsoft Purview](https://compliance.microsoft.com/) > **Gestion des enregistrements** > **Paramètres de gestion des enregistrements** > **Étiquettes de rétention** > **Suppression des éléments**.

Lorsque vous appliquez une étiquette de rétention à un élément de liste qui contient une pièce jointe au document, ce document n’hérite pas des paramètres de rétention et peut être supprimé de l’élément de liste. En comparaison, si cet élément de liste a été déclaré comme un enregistrement avec une étiquette de rétention, la pièce jointe au document hériterait des paramètres de rétention et n’a pas pu être supprimée.

<sup>3</sup> Les conteneurs incluent les bibliothèques de documents SharePoint, les comptes OneDrive et les boîtes aux lettres Exchange.

> [!IMPORTANT]
> La principale différence pour un enregistrement réglementaire est qu’une fois qu’il est appliqué au contenu, personne, pas même un administrateur général, peut supprimer l’étiquette.
>
> Les étiquettes de rétention configurées pour les enregistrements réglementaires ont également les restrictions d’administrateur suivantes :
>
> - La période de rétention ne peut pas être plus courte une fois l’étiquette enregistrée, mais seulement prolongée.
> - Ces étiquettes ne sont pas prises en charge par les stratégies d’attribution automatique d’étiquette, et doivent être appliquées à l’aide des [stratégies d’étiquette de rétention](create-apply-retention-labels.md).
>
> De plus, une étiquette réglementaire ne peut être appliquée à un document extrait dans SharePoint.
>
> En raison de ces restrictions et de l’irréversibilité de ces actions, assurez-vous que vous devez vraiment utiliser les enregistrements réglementaires avant de sélectionner cette option pour les étiquettes de rétention. Pour empêcher la configuration accidentelle, cette option n’est pas disponible par défaut, mais doit d’abord être activée à l’aide de PowerShell. Des instructions sont incluses dans [Déclarer les enregistrements à l’aide d’étiquettes de rétention](declare-records.md).

## <a name="configuration-guidance"></a>Instructions de configuration

Voir [Prise en main de la gestion des enregistrements](get-started-with-records-management.md). Cet article présente des informations sur les abonnements, les autorisations, et des liens vers des instructions de configuration de bout en bout pour des scénarios de gestion des enregistrements.
