---
title: Types de données et filtres pris en charge en mode guidé pour la chasse dans Microsoft 365 Defender
description: Affinez votre requête en utilisant les différentes fonctionnalités de mode guidé dans la chasse avancée dans Microsoft 365 Defender.
keywords: mode guidé, repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.openlocfilehash: d3b8373743fc742a0d9c4cd83f99101618a3ef6c
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67475585"
---
# <a name="refine-your-query-in-guided-mode"></a>Affiner votre requête en mode guidé 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.
## <a name="use-different-data-types"></a>Utiliser différents types de données

La chasse avancée en mode guidé prend en charge plusieurs types de données que vous pouvez utiliser pour affiner votre requête.

- Nombres<br>
![Capture d’écran des nombres en tant que troisième condition](../../media/guided-hunting/data-numbers.png)

- Chaînes<br>
![Capture d’écran des chaînes en tant que troisième condition](../../media/guided-hunting/data-strings.png)

   Dans la zone de texte libre, tapez la valeur, puis **appuyez sur Entrée** pour l’ajouter. Notez que le délimiteur entre les valeurs est **Entrée**.<br>

   ![Capture d’écran montrant différentes conditions que vous pouvez utiliser](../../media/guided-hunting/data-strings-2.png)

- Boolean<br>
![Capture d’écran des valeurs booléennes en tant que troisième condition](../../media/guided-hunting/boolean.png)


- Datetime<br>
![Capture d’écran des valeurs datetime en tant que troisième condition](../../media/guided-hunting/data-datetime.png)


- Liste fermée : vous n’avez pas besoin de mémoriser la valeur exacte que vous recherchez. Vous pouvez facilement choisir parmi une liste fermée suggérée qui prend en charge la sélection multiple.<br>
![Capture d’écran d’une liste fermée utilisée comme troisième condition](../../media/guided-hunting/data-closed.png)


## <a name="use-subgroups"></a>Utiliser des sous-groupes
Vous pouvez créer des groupes de conditions en cliquant sur **Ajouter un sous-groupe** :

![Capture d’écran mettant en surbrillance le bouton Ajouter un sous-groupe](../../media/guided-hunting/subgroup-1.png)

![Capture d’écran montrant l’utilisation de sous-groupes](../../media/guided-hunting/subgroup-2.png)

## <a name="use-smart-auto-complete-for-search"></a>Utiliser la saisie semi-automatique intelligente pour la recherche
La saisie semi-automatique intelligente pour la recherche d’appareils et de comptes d’utilisateur est prise en charge. Vous n’avez pas besoin de mémoriser l’ID d’appareil, le nom complet de l’appareil ou le nom du compte d’utilisateur. Vous pouvez commencer à taper les premiers caractères de l’appareil ou de l’utilisateur que vous recherchez et une liste suggérée s’affiche à partir de laquelle vous pouvez choisir ce dont vous avez besoin :

![Capture d’écran montrant la prise en charge de la saisie semi-automatique intelligente](../../media/guided-hunting/smart-auto.png)

## <a name="use-eventtype"></a>Utiliser `EventType`
Vous pouvez même rechercher des types d’événements spécifiques comme tous les journaux d’activité ayant échoué, les événements de modification de fichier ou les connexions réseau réussies à l’aide du filtre **EventType** dans n’importe quelle section où il est applicable.

Par exemple, si vous souhaitez ajouter une condition qui recherche des suppressions de valeur de Registre, vous pouvez accéder à la section **Événements du Registre** et sélectionner **EventType**.

![Capture d’écran de différents EventTypes](../../media/guided-hunting/hunt-specific-events-1.png)

La sélection d’EventType sous Événements de Registre vous permet de choisir parmi différents événements de Registre, y compris celui que vous recherchez, **RegistryValueDeleted**.

![Capture d’écran d’EventType RegistryValueDeleted](../../media/guided-hunting/hunt-specific-events-2.png)

>[!NOTE] 
>`EventType` est l’équivalent du schéma de `ActionType` données, dont les utilisateurs du mode avancé peuvent être plus familiers.

## <a name="test-your-query-with-a-smaller-sample-size"></a>Tester votre requête avec une taille d’échantillon plus petite
Si vous travaillez toujours sur votre requête et souhaitez voir rapidement ses performances et certains exemples de résultats, ajustez le nombre d’enregistrements à retourner en sélectionnant un ensemble plus petit dans le menu déroulant **Taille de l’exemple** . 
 
![Capture d’écran du menu déroulant taille de l’exemple](../../media/guided-hunting/smaller-sample.png)

La taille de l’échantillon est définie sur 10 000 résultats par défaut. Il s’agit du nombre maximal d’enregistrements qui peuvent être retournés lors de la chasse. Toutefois, nous vous recommandons vivement de réduire la taille de l’échantillon à 10 ou 100 pour tester rapidement votre requête, car cela consomme moins de ressources pendant que vous travaillez toujours à l’amélioration de la requête.

Ensuite, une fois que vous avez finalisé votre requête et que vous êtes prêt à l’utiliser pour obtenir tous les résultats pertinents pour votre activité de chasse, assurez-vous que la taille de l’échantillon est définie sur 10 000, le maximum.

## <a name="switch-to-advanced-mode-after-building-a-query"></a>Passer en mode avancé après la génération d’une requête
Vous pouvez cliquer sur **Modifier dans KQL** pour afficher la requête KQL générée par vos conditions sélectionnées. La modification dans KQL ouvre un nouvel onglet en mode avancé, avec la requête KQL correspondante :

![Capture d’écran mettant en évidence le bouton Modifier dans KQL](../../media/guided-hunting/switch-to-advanced.png)

![Capture d’écran montrant la même requête de guidée à avancée](../../media/guided-hunting/switch-to-advanced-2.png)

Dans l’exemple ci-dessus, la vue sélectionnée est Tout. Par conséquent, vous pouvez voir que la requête KQL recherche toutes les tables qui ont des propriétés de fichier de nom et SHA256, ainsi que dans toutes les colonnes pertinentes couvrant ces propriétés. 

Si vous remplacez la vue **par e-mails & collaboration**, la requête est réduite à :

![Capture d’écran montrant la même requête, de guidée à avancée, mais avec un domaine limité](../../media/guided-hunting/switch-to-advanced-3.png)

## <a name="see-also"></a>Voir aussi
 - [Quotas de chasse avancés et paramètres d’utilisation](advanced-hunting-limits.md)
 - [Étendre la couverture de chasse avancée avec les paramètres appropriés](advanced-hunting-extend-data.md)