---
title: Utiliser l’éditeur KQL pour générer des requêtes de recherche
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Vous pouvez utiliser l’éditeur KQL pour configurer des requêtes de recherche eDiscovery dans la recherche de contenu, core eDiscovery et Advanced eDiscovery.
ms.openlocfilehash: 571612cc2032b6241923cb6bba2a730a5d821c8a
ms.sourcegitcommit: 88c3b9758214936d283bad0321b826fb40a2e7e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2021
ms.locfileid: "60088216"
---
# <a name="use-the-kql-editor-to-build-search-queries-preview"></a>Utiliser l’éditeur KQL pour créer des requêtes de recherche (aperçu)

La nouvelle expérience de requête KQL dans la recherche d’outils eDiscovery Microsoft 365 fournit des commentaires et des conseils lorsque vous créez des requêtes de recherche dans la recherche de contenu, la découverte électronique principale et Advanced eDiscovery. Lorsque vous tapez des requêtes dans l’éditeur, il fournit lacompletion automatique pour les propriétés et conditions utilisables dans une recherche prise en charge et fournit des listes de valeurs pris en charge pour les propriétés et conditions standard. Par exemple, si vous spécifiez la propriété de messagerie dans votre requête, l’éditeur présente une liste de valeurs que `kind` vous pouvez sélectionner. L’éditeur KQL affiche également les erreurs de requête potentielles en temps réel que vous pouvez corriger avant d’exécuter la recherche. Mieux encore, vous pouvez coller des requêtes complexes directement dans l’éditeur sans avoir à créer manuellement des requêtes à l’aide des mots clés et des cartes de conditions dans le générateur de conditions standard.
  
Voici les principaux avantages de l’utilisation de l’éditeur KQL :

- Fournit des conseils et vous aide à créer des requêtes de recherche à partir de zéro.

- Permet de coller rapidement des requêtes longues et complexes directement dans l’éditeur. Par exemple, si vous recevez une requête complexe du conseiller de l’opposition, vous pouvez la coller dans l’éditeur KQL au lieu d’utiliser le générateur de conditions.

- Identifie rapidement les erreurs potentielles et affiche des conseils sur la façon de résoudre les problèmes.

L’éditeur KQL est également disponible lorsque vous créez des holds basés sur des requêtes dans core eDiscovery et Advanced eDiscovery.

## <a name="displaying-the-kql-editor"></a>Affichage de l’éditeur KQL

Lorsque vous créez ou modifiez une recherche de découverte électronique, l’option d’affichage et d’utilisation de l’éditeur KQL se trouve sur la page **Conditions** de l’Assistant Recherche ou Collections.

### <a name="kql-editor-in-content-search-and-core-ediscovery"></a>Éditeur KQL dans la recherche de contenu et la découverte électronique principale

![Éditeur KQL dans la recherche de contenu et la découverte électronique principale](../media/KQLEditorCore.png)

### <a name="kql-editor-in-advanced-ediscovery"></a>Éditeur KQL dans Advanced eDiscovery

![Éditeur KQL dans Advanced eDiscovery](../media/KQLEditorAdvanced.png)

## <a name="using-the-kql-editor"></a>Utilisation de l’éditeur KQL

Les sections suivantes montrent des exemples de la façon dont l’éditeur KQL fournit des suggestions et détecte les erreurs potentielles.

### <a name="autocompletion-of-search-properties-and-operators"></a>Autocompletion des propriétés et des opérateurs de recherche

Lorsque vous commencez à taper une requête de recherche dans l’éditeur KQL, l’éditeur affiche une suggestion decompletion automatique des propriétés de recherche prise en charge (également *appelées restrictions* de propriété) que vous pouvez sélectionner. Vous devez taper au moins deux caractères pour afficher la liste des propriétés prise en charge qui commencent par ces deux caractères. Par exemple, la capture d’écran suivante montre les propriétés de recherche suggérées qui commencent par `Se` .

![L’éditeur KQL suggère des propriétés pris en charge](../media/KQLEditorAutoCompleteProperties.png)

En outre, l’éditeur suggère également une liste d’opérateurs pris en charge (tels que , et ) lorsque vous tapez un `:` `=` nom de propriété `<>` complet. Par exemple, la capture d’écran suivante montre les opérateurs suggérés pour la `Date` propriété.

![L’éditeur KQL suggère des opérateurs](../media/KQLEditorOperatorSuggestions.png)

Pour plus d’informations sur les opérateurs et les propriétés de recherche pris en charge, voir Requêtes par mot clé et conditions de recherche [pour eDiscovery.](keyword-queries-and-search-conditions.md)

### <a name="property-value-suggestions"></a>Suggestions de valeur de propriété

L’éditeur KQL fournit des suggestions pour les valeurs possibles de certaines propriétés. Par exemple, la capture d’écran suivante montre les valeurs suggérées pour la `Kind` propriété.

![L’éditeur KQL suggère des valeurs pour certaines propriétés](../media/KQLEditorValueSuggestions.png)

L’éditeur suggère également une liste d’utilisateurs (au format UPN) lorsque vous tapez des propriétés de destinataire de courrier électronique, telles `From` `To` que , et `Recipients` `Participants` .

![L’éditeur KQL suggère des utilisateurs pour les propriétés de messagerie du destinataire](../media/KQLEditorRecipientSuggestions.png)

### <a name="detection-of-potential-errors"></a>Détection d’erreurs potentielles

L’éditeur KQL détecte les erreurs potentielles dans les requêtes de recherche et fournit une indication de ce qui provoque l’erreur pour vous aider à résoudre l’erreur. L’éditeur indique également une erreur potentielle lorsqu’une propriété n’a pas d’opération ou de valeur correspondante. Les erreurs potentielles dans la requête sont mises en surbrilllette en texte  rouge, et les explications et les correctifs possibles pour l’erreur sont affichés dans la section de la section « Erreurs potentielles ». Par exemple, si vous avez passé la requête suivante dans l’éditeur KQL, quatre erreurs potentielles seraient détectées.

![Détection des erreurs d’éditeur KQL](../media/KQLEditorErrorDetection.png)

Dans ce cas, vous pouvez utiliser les conseils d’erreur potentiels pour résoudre les problèmes et résoudre la requête.

## <a name="more-information"></a>Plus d’informations

- Vous pouvez faire bascule entre le générateur de condition et l’éditeur KQL. Par exemple, si vous utilisez le générateur de condition pour configurer une requête à l’aide de la zone Mots clés et de plusieurs cartes de condition, vous pouvez afficher la requête résultante dans l’éditeur KQL. Toutefois, si vous créez une requête complexe (avec des mots clés et des conditions) dans l’éditeur KQL, la requête qui en résulte s’affiche uniquement dans la zone Mots clés lorsque vous l’affichez dans le générateur de conditions.

- Si vous collez une requête complexe dans l’éditeur KQL, l’éditeur détecte les erreurs potentielles et suggère des solutions possibles pour résoudre les erreurs.
