---
title: Limites des stratégies de rétention et stratégies d’étiquettes de rétention
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
hideEdit: true
description: Comprendre le nombre maximal de stratégies et d’éléments par stratégie pour les stratégies de rétention et les stratégies d’étiquette de rétention
ms.openlocfilehash: 52318fb2f8ae81022734bb1f620b220830214ad7
ms.sourcegitcommit: f6fff04431d632db02e7bdbf12f691091a30efad
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2021
ms.locfileid: "60432648"
---
# <a name="limits-for-retention-policies-and-retention-label-policies"></a>Limites des stratégies de rétention et stratégies d’étiquettes de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Lorsque vous utilisez les [stratégies de rétention et stratégies d’étiquette de rétention](retention.md#retention-policies-and-retention-labels) pour conserver ou supprimer automatiquement des données pour votre organisation, vous devez prendre connaissance de certains nombres maximum.

## <a name="maximum-number-of-retention-labels-per-tenant"></a>Nombre maximal d’étiquettes de rétention par client

Un maximum de 1 000 étiquettes de rétention sont supportés par client.

## <a name="maximum-number-of-policies-per-tenant"></a>Nombre maximal de stratégies par client

Un client unique peut avoir un maximum de 10 000 stratégies (n’importe quelle configuration). Ce nombre maximal inclut les différentes stratégies de rétention et d’autres stratégies de conformité, telles que les stratégies de protection contre la perte de données, les obstacles à l’information, les conservations eDiscovery et les étiquettes de confidentialité.

Dans cette limite de 10 000 stratégies, il existe également des limites sur le nombre maximal de stratégies de rétention par charge de travail :

- Exchange (n’importe quelle configuration) : 1 800
- SharePoint ou OneDrive : (tous les sites sont inclus automatiquement) : 13
- SharePoint ou OneDrive (emplacements spécifiques inclus ou exclus) : 2 600

Bien que les stratégies de rétention pour Microsoft Teams et Yammer utilisent des boîtes aux lettres pour stocker des données à des fins de rétention, le nombre maximal de stratégies pour Exchange Online exclut les stratégies de rétention pour Teams et Yammer.

## <a name="maximums-for-adaptive-policy-scopes"></a>Maximums pour les étendues de stratégie adaptative

Il n’existe aucune limite au nombre d’étendues de stratégie adaptative [que](retention.md#adaptive-or-static-policy-scopes-for-retention) vous pouvez ajouter à une stratégie de rétention, mais il existe certaines limites maximales pour la requête qui définit chaque étendue adaptative :

- Longueur de chaîne pour les valeurs d’attribut ou de propriété : 200
- Nombre d’attributs ou de propriétés sans groupe ou au sein d’un groupe : 10
- Nombre de groupes de sécurité : 10
- Nombre de caractères dans une requête avancée : 10 000

Le regroupement d’attributs ou de propriétés au sein d’un groupe n’est pas pris en charge. Cela signifie que le nombre maximal de propriétés ou d’attributs pris en charge dans une seule étendue adaptative est de 100.

## <a name="maximum-number-of-items-per-policy"></a>Nombre maximal d’éléments par stratégie

> [!IMPORTANT]
> Applicable uniquement si vous utilisez des [étendues de stratégie statiques plutôt que des étendues de stratégie adaptatives.](retention.md#adaptive-or-static-policy-scopes-for-retention)

Si vous utilisez des étendues statiques et la configuration optionnelle pour inclure ou exclure des utilisateurs spécifiques, des groupes Microsoft 365 spécifiques ou des sites spécifiques, il y a certaines limites par stratégie à connaître. 

Nombre maximal d’éléments par stratégie pour la rétention :

- Les boîtes aux lettres Exchange : 1 000
- Groupes Microsoft 365 : 1 000
- Messages du canal Teams : 1 000
- Conversations Teams : 1 000
- Messages communautaires Yammer : 1 000
- Messages utilisateur de Yammer : 1 000
- Sites SharePoint : 100
- Comptes OneDrive : 100

Skype Entreprise doit être étendu à des utilisateurs spécifiques et le nombre maximal pris en charge par stratégie est de 1 000.

Ces limitations s'appliquent à chaque police, donc si vous devez utiliser des inclusions ou des exclusions spécifiques qui entraînent un dépassement de ces chiffres, vous pouvez créer des politiques de rétention supplémentaires qui ont les mêmes paramètres de rétention. Voir la section suivante pour quelques[exemples de scénarios et de solutions](#examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers) qui utilisent plusieurs politiques de rétention pour cette raison.

Les stratégies de rétention multiples entraînent des frais administratifs plus élevés. Il faut donc toujours se demander si vous avez vraiment besoin d'inclusions et d'exclusions. Envisagez d’utiliser des étendues adaptatives plutôt que de créer et de gérer plusieurs stratégies avec des inclut et des exclusions.

### <a name="examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers"></a>Exemples d’utilisation de plusieurs stratégies pour éviter le dépassement des nombres maximum

Les exemples suivants concernent des étendues statiques et fournissent quelques solutions de conception lorsque vous ne pouvez pas spécifier uniquement l'emplacement d'une politique de conservation et que vous devez prendre en compte le nombre maximum d'éléments documentés dans la section précédente.

Exemple d'échange :

- **Exigence** : Dans une organisation qui compte plus de 40 000 boîtes aux lettres, la plupart des utilisateurs doivent conserver leur courrier électronique pendant 7 ans, mais un sous-ensemble d'utilisateurs identifiés (425) ne doivent conserver leur courrier électronique que pendant 5 ans.

- **Solution** : Créer une politique de conservation pour le courrier électronique d'échange avec une période de conservation de 7 ans et exclure le sous-ensemble des utilisateurs. Ensuite, créez une deuxième politique de conservation pour le courrier électronique d 'echange avec une période de conservation de 5 ans et incluez le sous-ensemble des utilisateurs. 
    
    Dans les deux cas, le nombre de boîtes aux lettres incluses et exclues est inférieur au nombre maximal de boîtes aux lettres spécifiées pour une seule politique, et le sous-ensemble d'utilisateurs doit être explicitement exclu de la première politique parce qu'elle a une [période de rétention plus longue](retention.md#the-principles-of-retention-or-what-takes-precedence) que la deuxième politique. Si le sous-ensemble d'utilisateurs avait besoin d'une politique de rétention plus longue, vous n'auriez pas besoin de les exclure de la première stratégie.
     
    Avec cette solution, si une nouvelle personne rejoint l'organisation, sa boîte aux lettres est automatiquement incluse dans la première politique pendant 7 ans et il n'y a aucun impact sur le nombre maximum de personnes prises en charge. Cependant, les nouveaux utilisateurs qui ont besoin de la période de conservation de 5 ans s'ajoutent aux numéros d'inclusion et d'exclusion, et cette limite serait atteinte à 1 000.

Exemple de SharePoint :

- **Exigence**: Une organisation possède plusieurs milliers de sites SharePoint, mais seuls 2 000 sites nécessitent une période de conservation de 10 ans, et 8 000 sites nécessitent une période de conservation de 4 ans.

- **Solution**:Créer 20 politiques de conservation pour SharePoint avec une période de conservation de 10 ans qui inclut 100 sites spécifiques, et créer 80 politiques de conservation pour SharePoint avec une période de conservation de 4 ans qui inclut 100 sites spécifiques.
    
    Comme il n'est pas nécessaire de conserver tous les sites SharePoint, vous devez créer des politiques de conservation qui spécifient les sites spécifiques. Comme une stratégie de conservation ne prend pas en charge plus de 100 sites spécifiques, vous devez créer plusieurs stratégies pour les deux périodes de conservation. Ces stratégies de rétention ont le nombre maximum de sites inclus, de sorte que le prochain nouveau site à conserver nécessiterait une nouvelle stratégie de rétention, quelle que soit la période de rétention.

## <a name="maximum-number-of-items-for-disposition"></a>Nombre maximal d’éléments pour la destruction

Pour la [destruction de contenu](disposition.md), il existe des limites à prendre en compte :

- 1 000 000 éléments en attente de destruction par phase pour chaque étiquette de rétention

- Preuve de la destruction pendant un délai maximal de 7 ans après destruction de l’élément, avec une limite de 1 000 000 éléments par étiquette de rétention pour cette période. 
    
Si vous avez besoin d’une preuve de destruction supérieure à cette limite de 1 000 000 pour des éléments entrant comme enregistrements, contactez le [Support Microsoft](../business-video/get-help-support.md).
