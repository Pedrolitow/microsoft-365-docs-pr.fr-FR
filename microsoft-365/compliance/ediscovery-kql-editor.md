---
title: Utiliser l’éditeur KQL pour générer des requêtes de recherche
description: Vous pouvez utiliser l’éditeur KQL pour configurer des requêtes de recherche eDiscovery dans Recherche de contenu, eDiscovery (Standard) et eDiscovery (Premium).
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
- ediscovery
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: bfee0098300c6cb00bc456c5329f98f87e468461
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68686578"
---
# <a name="use-the-kql-editor-to-build-search-queries"></a>Utiliser l’éditeur KQL pour générer des requêtes de recherche

La nouvelle expérience de requête KQL (Keyword Query Language) dans la recherche d’outils Microsoft Purview eDiscovery fournit des commentaires et des conseils lorsque vous créez des requêtes de recherche dans Recherche de contenu, Microsoft Purview eDiscovery (Standard) et eDiscovery (Premium). Lorsque vous entrez des requêtes dans l’éditeur, il fournit la saisie automatique des propriétés et conditions pouvant faire l’objet d’une recherche et fournit des listes de valeurs prises en charge pour les propriétés et conditions standard. Par exemple, si vous spécifiez la `kind` propriété email dans votre requête, l’éditeur présente une liste de valeurs prises en charge que vous pouvez sélectionner. L’éditeur KQL affiche également les erreurs de requête potentielles en temps réel que vous pouvez corriger avant d’exécuter la recherche. Mieux encore, vous pouvez coller des requêtes complexes directement dans l’éditeur sans avoir à générer manuellement des requêtes à l’aide des mots clés et des cartes de conditions dans le générateur de conditions standard.
  
Voici les principaux avantages de l’utilisation de l’éditeur KQL :

- Fournit des conseils et vous aide à créer des requêtes de recherche à partir de zéro.
- Vous permet de coller rapidement des requêtes longues et complexes directement dans l’éditeur. Par exemple, si vous recevez une requête complexe d’un avocat opposé, vous pouvez la coller dans l’éditeur KQL au lieu d’avoir à utiliser le générateur de conditions.
- Identifie rapidement les erreurs potentielles et affiche des conseils sur la façon de résoudre les problèmes.

L’éditeur KQL est également disponible lorsque vous créez des conservations basées sur des requêtes dans eDiscovery (Standard) et eDiscovery (Premium).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="displaying-the-kql-editor"></a>Affichage de l’éditeur KQL

Lorsque vous créez ou modifiez une recherche eDiscovery, l’option permettant d’afficher et d’utiliser l’éditeur KQL se trouve dans la page **Conditions** de l’Assistant Recherche ou collections.

### <a name="kql-editor-in-content-search-and-ediscovery-standard"></a>Éditeur KQL dans recherche de contenu et eDiscovery (Standard)

![Éditeur KQL dans recherche de contenu et eDiscovery (Standard)](../media/KQLEditorCore.png)

### <a name="kql-editor-in-ediscovery-premium"></a>Éditeur KQL dans eDiscovery (Premium)

![Éditeur KQL dans eDiscovery (Premium)](../media/KQLEditorAdvanced.png)

## <a name="using-the-kql-editor"></a>Utilisation de l’éditeur KQL

Les sections suivantes montrent des exemples de la façon dont l’éditeur KQL fournit des suggestions et détecte les erreurs potentielles.

### <a name="autocompletion-of-search-properties-and-operators"></a>Autocomplétion des propriétés et des opérateurs de recherche

Lorsque vous commencez à entrer une requête de recherche dans l’éditeur KQL, l’éditeur affiche la saisie automatique suggérée des propriétés de recherche prises en charge (également *appelées restrictions de propriété*) que vous pouvez sélectionner. Vous devez taper au moins deux caractères pour afficher la liste des propriétés prises en charge qui commencent par ces deux caractères. Par exemple, la capture d’écran suivante montre les propriétés de recherche suggérées qui commencent par `Se`.

![L’éditeur KQL suggère des propriétés prises en charge](../media/KQLEditorAutoCompleteProperties.png)

En outre, l’éditeur suggère également de fournir une liste d’opérateurs pris en charge (tels que `:`, `=` et `<>`) lorsque vous tapez un nom de propriété complet. Par exemple, la capture d’écran suivante montre les opérateurs suggérés pour la `Date` propriété .

![L’éditeur KQL suggère des opérateurs](../media/KQLEditorOperatorSuggestions.png)

Pour plus d’informations sur les propriétés et les opérateurs de recherche pris en charge, consultez [Requêtes par mot clé et conditions de recherche pour eDiscovery](keyword-queries-and-search-conditions.md).

### <a name="property-value-suggestions"></a>Suggestions de valeur de propriété

L’éditeur KQL fournit des suggestions pour les valeurs possibles de certaines propriétés. Par exemple, la capture d’écran suivante montre les valeurs suggérées pour la `Kind` propriété .

![L’éditeur KQL suggère des valeurs pour certaines propriétés](../media/KQLEditorValueSuggestions.png)

L’éditeur suggère également une liste d’utilisateurs (au format UPN) lorsque vous tapez des propriétés de destinataire d’e-mail, telles que `From`, `To`et `Recipients` `Participants`.

![L’éditeur KQL suggère des utilisateurs pour les propriétés de l’e-mail du destinataire](../media/KQLEditorRecipientSuggestions.png)

### <a name="detection-of-potential-errors"></a>Détection des erreurs potentielles

L’éditeur KQL détecte les erreurs potentielles dans les requêtes de recherche et fournit un indicateur de la cause de l’erreur pour vous aider à résoudre l’erreur. L’éditeur indique également une erreur potentielle lorsqu’une propriété n’a pas d’opération ou de valeur correspondante. Les erreurs potentielles dans la requête sont mises en surbrillance en rouge, et les explications et les correctifs possibles pour l’erreur sont affichés dans la section de liste déroulante **Erreurs potentielles** . Par exemple, si vous collez la requête suivante dans l’éditeur KQL, quatre erreurs potentielles sont détectées.

![Détection des erreurs de l’éditeur KQL](../media/KQLEditorErrorDetection.png)

Dans ce cas, vous pouvez utiliser les indicateurs d’erreur potentiels pour résoudre les problèmes et corriger la requête.

## <a name="more-information"></a>Plus d’informations

- Vous pouvez basculer entre le générateur de conditions et l’éditeur KQL. Par exemple, si vous utilisez le générateur de conditions pour configurer une requête à l’aide de la zone Mots clés et de plusieurs cartes de condition, vous pouvez afficher la requête obtenue dans l’éditeur KQL. Toutefois, si vous créez une requête complexe (avec des mots clés et des conditions) dans l’éditeur KQL, la requête résultante s’affiche uniquement dans la zone Mots clés lorsque vous l’affichez dans le générateur de conditions.

- Si vous collez une requête complexe dans l’éditeur KQL, l’éditeur détecte les erreurs potentielles et suggère des solutions possibles pour résoudre les erreurs.
