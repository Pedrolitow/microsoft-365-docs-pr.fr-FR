---
title: Découvrir les enregistrements
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
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Découvrir les enregistrements pour vous aider à implémenter une solution de gestion des enregistrements dans Microsoft 365.
ms.openlocfilehash: e64e91aeef307d05f23c47987a84baaf386324df
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46685440"
---
# <a name="learn-about-records"></a>Découvrir les enregistrements

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

La gestion des enregistrements dans Microsoft 365 permet à votre organisation de respecter les stratégies d’entreprise et les obligations légales ou réglementaires, tout en réduisant les risques et la responsabilité juridique.

Lorsque le contenu est marqué comme un enregistrement :

- Des restrictions sont appliquées aux éléments en ce qui concerne les [actions autorisées ou bloquées](#compare-restrictions-for-what-actions-are-allowed-or-blocked).

- Des activités supplémentaires sur l’élément sont enregistrées.

- Vous avez une preuve de destruction lorsque les éléments sont supprimés à la fin de la période de rétention.

Vous utilisez les [étiquettes de rétention](retention.md#retention-labels) pour marquer du contenu sous la forme d’un enregistrement. Vous pouvez soit publier ces étiquettes pour permettre aux utilisateurs et aux administrateurs de les appliquer manuellement au contenu, soit appliquer automatiquement ces étiquettes au contenu que vous voulez marquer comme enregistrement.

En utilisant des étiquettes de rétention pour marquer du contenu en tant qu’enregistrement, vous pouvez implémenter une stratégie de gestion des enregistrements unique et cohérente dans votre environnement Microsoft 365.

## <a name="compare-restrictions-for-what-actions-are-allowed-or-blocked"></a>Comparer des restrictions relatives aux actions autorisées ou bloquées

Utilisez le tableau suivant pour identifier les restrictions placées sur du contenu suite à l’application d’une étiquette de rétention standard, ainsi que les étiquettes de rétention qui marquent du contenu en tant qu’enregistrement. 

Une étiquette de rétention standard a la configuration de conservation des données sans marquer le contenu comme enregistrement.

>[!NOTE] 
> Pour couvrir tous les cas de figure, le tableau inclut les colonnes d’un enregistrement verrouillé et déverrouillé, applicable à SharePoint et OneDrive, mais pas à Exchange. La possibilité de verrouiller et de déverrouiller un enregistrement utilise le [contrôle de version](record-versioning.md) qui n’est pas pris en charge pour les éléments Exchange. Par conséquent, pour tous les éléments Exchange marqués en tant qu’enregistrement, le comportement mappe vers l’**Enregistrement – colonne verrouillée**, et l’**Enregistrement – colonne déverrouillée** n’est pas pertinent.


|Action| Étiquette de rétention |Enregistrement – colonne verrouillée| Enregistrement – colonne déverrouillée|
|:-----|:-----|:-----|:-----|:-----|
|Modifier les contenus|Autorisé | **Bloqué** | Autorisé|
|Modifier les propriétés, y compris Renommer|Autorisé |Autorisé | Autorisé|
|Supprimer|<sup>1</sup> autorisé |**Bloqué** | **Bloqué**|
|Copier|Autorisé |Autorisé | Autorisé|
|Se déplacer au sein du conteneur <sup>2</sup>|Autorisé |Autorisé | Autorisé|
|Se déplacer dans les conteneurs <sup>2</sup>|Autorisé |Autorisé si jamais déverrouillé | Autorisé|
|Ouvert/lu|Autorisé |Autorisé | Autorisé|
|Modifier l’étiquette|Autorisé |Autorisé – administrateur de conteneur uniquement | Autorisé – administrateur de conteneur uniquement|
|Supprimer l’étiquette|Autorisé |Autorisé – administrateur de conteneur uniquement | Autorisé – administrateur de conteneur uniquement|

Notes de bas de page :

<sup>1</sup> Prise en charge par OneDrive et Exchange en conservant une copie dans un emplacement sécurisé, mais bloqué par SharePoint.

Message qu’un utilisateur voit s’il essaie de supprimer un document étiqueté dans SharePoint :

![Message indiquant que l’élément n’a pas été supprimé dans SharePoint](../media/d0020726-1593-4a96-b07c-89b275e75c49.png)


<sup>2</sup> Les conteneurs incluent les bibliothèques de documents SharePoint et les boîtes aux lettres Exchange.

## <a name="next-steps"></a>Étapes suivantes

Si vous n’avez pas encore d’étiquettes de rétention à utiliser pour la gestion des enregistrements, consultez [Prise en main des stratégies et des étiquettes de rétention](get-started-with-retention.md).

Pour marquer du contenu en tant qu’enregistrement, consultez [Déclarer des enregistrements à l’aide d’étiquettes de rétention](declare-records.md).
