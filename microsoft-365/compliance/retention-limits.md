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
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
hideEdit: true
description: Comprendre le nombre maximal de stratégies et d’éléments par stratégie pour les stratégies de rétention et les stratégies d’étiquette de rétention
ms.openlocfilehash: 007ca6eec50b243e1b820938ffa67553d7882c7b
ms.sourcegitcommit: 794f9767aaebe13ab1aead830b214ea674289d19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52107656"
---
# <a name="limits-for-retention-policies-and-retention-label-policies"></a>Limites des stratégies de rétention et stratégies d’étiquettes de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Lorsque vous utilisez les [stratégies de rétention et stratégies d’étiquette de rétention](retention.md#retention-policies-and-retention-labels) pour conserver ou supprimer automatiquement des données pour votre organisation, vous devez prendre connaissance de certains nombres maximum.

## <a name="maximum-number-of-policies-per-tenant"></a>Nombre maximal de stratégies par client

Un client unique peut avoir un maximum de 10 000 stratégies (n’importe quelle configuration). Ce nombre maximal inclut les différentes stratégies de rétention et d’autres stratégies de conformité, telles que les stratégies DLP.

Nombre maximal de stratégies de rétention par charge de travail :

- Exchange Online (n’importe quelle configuration) : 1 800
- SharePoint ou OneDrive : (tous les sites sont inclus automatiquement) : 13
- SharePoint ou OneDrive (emplacements spécifiques inclus ou exclus) : 2 600

## <a name="maximum-number-of-items-per-policy"></a>Nombre maximal d’éléments par stratégie

Si vous utilisez la configuration optionnelle pour étendre vos paramètres de rétention à des utilisateurs spécifiques, des groupes Microsoft 365 spécifiques ou des sites spécifiques, il faut tenir compte de certaines limites par politique : 

Nombre maximal d’éléments par stratégie pour la rétention :

  - 1 000 boîtes aux lettres (boîtes aux lettres des utilisateurs ou boîtes aux lettres de groupe)
  - 1 000 groupes Microsoft 365
  - 1 000 utilisateurs pour conversations privées Teams
  - 100 sites (OneDrive et SharePoint)

Ces limitations s'appliquent à chaque police, donc si vous devez utiliser des inclusions ou des exclusions spécifiques qui entraînent un dépassement de ces chiffres, vous pouvez créer des politiques de rétention supplémentaires qui ont les mêmes paramètres de rétention. Voir la section suivante pour quelques[exemples de scénarios et de solutions](#examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers) qui utilisent plusieurs politiques de rétention pour cette raison.

Les politiques de rétention multiples entraînent des frais administratifs plus élevés. Il faut donc toujours se demander si vous avez vraiment besoin d'inclusions et d'exclusions. Rappelez-vous que la configuration par défaut qui s'applique à l'ensemble du site n'a pas de limites, et que ce choix de configuration peut être une meilleure solution que la création et la maintenance de plusieurs politiques.

> [!TIP]
> Si vous devez créer et maintenir plusieurs politiques de rétention pour ce scénario, pensez à utiliser [PowerShell](retention.md#powershell-cmdlets-for-retention-policies-and-retention-labels) pour une configuration plus efficace.

### <a name="examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers"></a>Exemples d’utilisation de plusieurs stratégies pour éviter le dépassement des nombres maximum

Les exemples suivants fournissent quelques solutions de conception pour les cas où vous ne pouvez pas spécifier uniquement l'emplacement d'une politique de conservation, et doivent tenir compte des limites documentées dans la section précédente.

Exemple d'échange :

- **Exigence** : Dans une organisation qui compte plus de 40 000 boîtes aux lettres, la plupart des utilisateurs doivent conserver leur courrier électronique pendant 7 ans, mais un sous-ensemble d'utilisateurs identifiés (425) ne doivent conserver leur courrier électronique que pendant 5 ans.

- **Solution** : Créer une politique de conservation pour le courrier électronique d'échange avec une période de conservation de 7 ans et exclure le sous-ensemble des utilisateurs. Ensuite, créez une deuxième politique de conservation pour le courrier électronique d 'echange avec une période de conservation de 5 ans et incluez le sous-ensemble des utilisateurs. 
    
    Dans les deux cas, le nombre de boîtes aux lettres incluses et exclues est inférieur au nombre maximum de boîtes aux lettres spécifiées pour une seule politique, et le sous-ensemble d'utilisateurs doit être explicitement exclu de la première politique parce qu'il a une[ période de conservation plus longue](retention.md#the-principles-of-retention-or-what-takes-precedence)que la deuxième stratégie. Si le sous-ensemble d'utilisateurs nécessitait une politique de conservation plus longue, vous n'auriez pas besoin de les exclure de la première stratégie.
     
    Avec cette solution, si une nouvelle personne rejoint l'organisation, sa boîte aux lettres est automatiquement incluse dans la première politique pendant 7 ans et il n'y a aucun impact sur le nombre maximum de personnes prises en charge. Cependant, les nouveaux utilisateurs qui ont besoin de la période de conservation de 5 ans s'ajoutent aux numéros d'inclusion et d'exclusion, et cette limite serait atteinte à 1 000.

Exemple de SharePoint :

- **Exigence**: Une organisation possède plusieurs milliers de sites SharePoint, mais seuls 2 000 sites nécessitent une période de conservation de 10 ans, et 8 000 sites nécessitent une période de conservation de 4 ans.

- **Solution**:Créer 20 politiques de conservation pour SharePoint avec une période de conservation de 10 ans qui inclut 100 sites spécifiques, et créer 80 politiques de conservation pour SharePoint avec une période de conservation de 4 ans qui inclut 100 sites spécifiques.
    
    Comme il n'est pas nécessaire de conserver tous les sites SharePoint, vous devez créer des politiques de conservation qui spécifient les sites spécifiques. Comme une stratégie de conservation ne prend pas en charge plus de 100 sites spécifiques, vous devez créer plusieurs stratégies pour les deux périodes de conservation. Ces stratégies de rétention ont le nombre maximum de sites inclus, de sorte que le prochain nouveau site à conserver nécessiterait une nouvelle stratégie de rétention, quelle que soit la période de rétention.