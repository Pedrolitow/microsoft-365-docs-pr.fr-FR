---
title: Gestion des Enregistrements dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
description: La gestion des enregistrements dans Microsoft 365 vous permet d’appliquer des planifications de rétention dans un plan de gestion de fichiers afin de gérer la rétention, la déclaration d’enregistrements et la destruction de ceux-ci.
ms.openlocfilehash: 466b346501f9ee4e02a4a254ebeb2dfdf6e23eca
ms.sourcegitcommit: aebcdbef52e42f37492a7f780b8b9b2bc0998d5c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2021
ms.locfileid: "59775599"
---
# <a name="learn-about-records-management-in-microsoft-365"></a>Découvrez la gestion des enregistrements dans Microsoft 365

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Tous les types d’organisation nécessitent une solution de gestion des enregistrements pour gérer des enregistrements réglementaires, légaux, et hautement professionnels dans les données d’entreprise. La gestion des enregistrements dans Microsoft 365 permet à une organisation de gérer ses obligations légales, démontrer la conformité aux réglementations, et améliore l’efficacité avec une disposition régulière des éléments dont la rétention n’est plus nécessaire, qui n’ont plus de valeur, ou ne sont plus nécessaires pour des objectifs professionnels.

Les fonctionnalités suivantes permettent la prise en charge votre solution de gestion des enregistrements dans Microsoft 365 :

- **Étiqueter du contenu comme enregistrement** Créez et configurez des étiquettes de rétention pour indiquer que le contenu est un [enregistrement](#records) qui peut ensuite être appliqué par les utilisateurs ou appliqué automatiquement en identifiant les informations sensibles, les mots clés ou les types de contenu.

- **Migrer et gérer vos exigences de conservation avec le plan de classement**. L’utilisation d’un [plan de gestion des fichiers ](file-plan-manager.md)vous permet de mettre en place un plan de rétention existante à Microsoft 365 ou d’en créer une nouvelle pour les fonctionnalités de gestion améliorées.

- **Configurer les paramètres de rétention et de suppression avec les étiquettes de rétention**. Configurez les [étiquettes de rétention](retention.md#retention-labels) avec les périodes de rétention et les actions basées sur divers facteurs tels que la date de la dernière modification ou création.

- **Démarrer différentes périodes de rétention lorsqu’un événement se produit** avec [rétention basée sur des événements](event-driven-retention.md).

- **Vérifier et valider la destruction** en effectuant une [révision avant destruction](disposition.md#disposition-reviews) et la preuve de la [suppression d’enregistrements](disposition.md#disposition-of-records).

- **Exporter des informations sur tous les éléments supprimés** avec l’[option exporter](disposition.md#filter-and-export-the-views).

- **Définir des autorisations spécifiques** afin que les fonctions de gestionnaire d’enregistrements au sein de votre organisation [disposent du droit d’accès](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

Grâce à ces capacités, vous pouvez intégrer les calendriers de rétention et les exigences de votre organisation dans une solution de gestion des documents qui gère la rétention, la déclaration et l'élimination des enregistrements, afin de prendre en charge le cycle de vie complet de votre contenu.

En plus de la documentation en ligne, nous vous conseillons d’écouter l’[enregistrement du webinaire](https://aka.ms/MIPC/Video-RecordsManagementWebinar) sur la gestion des enregistrements et de télécharger la [documentation associée à cette présentation, ainsi que les FAQ](https://aka.ms/MIPC/Blog-RecordsManagementWebinar).

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
|Modifier les propriétés, y compris Renommer|Autorisé |Autorisé | Autorisé| **Bloqué**|
|Supprimer|<sup>1</sup> autorisé |**Bloqué** |**Bloqué**| **Bloqué**|
|Copier|Autorisé |Autorisé | Autorisé| Autorisé|
|Se déplacer au sein du conteneur <sup>2</sup>|Autorisé |Autorisé | Autorisé| Autorisé|
|Se déplacer dans les conteneurs <sup>2</sup>|Autorisé |Autorisé si jamais déverrouillé | **Bloqué** | **Bloqué**|
|Ouvert/lu|Autorisé |Autorisé | Autorisé| Autorisé|
|Modifier l’étiquette|Autorisé |Autorisé – administrateur de conteneur uniquement | Autorisé – administrateur de conteneur uniquement| **Bloqué**
|Supprimer l’étiquette|Autorisé |Autorisé – administrateur de conteneur uniquement | Autorisé – administrateur de conteneur uniquement| **Bloqué**

Notes de bas de page :

<sup>1</sup> Prise en charge par OneDrive et Exchange en conservant une copie dans un emplacement sécurisé, mais bloqué par SharePoint.

Lorsque vous appliquez une étiquette de rétention à un élément de liste qui contient une pièce jointe au document, ce document n’hérite pas des paramètres de rétention et peut être supprimé de l’élément de liste. En comparaison, si cet élément de liste a été déclaré comme un enregistrement avec une étiquette de rétention, la pièce jointe au document hériterait des paramètres de rétention et n’a pas pu être supprimée.

<sup>2</sup> Les conteneurs incluent les bibliothèques de documents SharePoint, les comptes OneDrive et les boîtes aux lettres Exchange.

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

Veuillez consulter la page [Prise en main de la gestion des enregistrements](get-started-with-records-management.md). Cet article présente des informations sur les abonnements, les autorisations, et des liens vers des instructions de configuration de bout en bout pour des scénarios de gestion des enregistrements.