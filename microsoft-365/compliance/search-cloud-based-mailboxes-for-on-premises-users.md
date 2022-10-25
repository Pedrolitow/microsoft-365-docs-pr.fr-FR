---
title: Recherche de données de conversations Teams pour les utilisateurs locaux
description: Les administrateurs peuvent utiliser les outils eDiscovery dans Microsoft 365 pour rechercher et exporter des données de conversation Teams pour les utilisateurs locaux dans un déploiement exchange hybride.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- tier1
- purview-compliance
- ediscovery
ms.localizationpriority: high
search.appverid:
- MOE150
- MST160
- MET150
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fa1ba34aa94a20c5bcef93e225422411d7af5468
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68686564"
---
# <a name="search-for-teams-chat-data-for-on-premises-users"></a>Recherche de données de conversations Teams pour les utilisateurs locaux

Si votre organisation dispose d’un déploiement Exchange hybride (ou si votre organisation synchronise une organisation Exchange locale avec Microsoft 365) et a activé Microsoft Teams, les utilisateurs locaux peuvent utiliser l’application de conversation Teams pour la messagerie instantanée. Pour un utilisateur dans le cloud, les données de conversation Teams (également appelées *1x1 ou conversations 1x1*) sont enregistrées dans sa boîte aux lettres principale basée sur le cloud. Lorsqu’un utilisateur local utilise l’application de conversation Teams, ses messages de conversation ne peuvent pas être stockés dans sa boîte aux lettres principale qui se situe en local. Pour contourner cette limitation, Microsoft a publié une nouvelle fonctionnalité dans laquelle une zone de stockage basée sur le cloud est crée pour que vous utilisiez les outils eDiscovery pour rechercher et exporter des données de conversation Teams pour les utilisateurs locaux.
  
Voici la configuration requise et les limitations applicables à l’activation du stockage cloud pour les utilisateurs locaux :
  
- Les comptes d’utilisateurs dans votre service d’annuaire local (par exemple, Active Directory) doivent être synchronisés avec Azure Active Directory (service d’annuaire dans Microsoft 365). Cela signifie qu’un compte d’utilisateur de courrier est créé dans Microsoft 365 et est associé à un utilisateur dont la boîte aux lettres principale se trouve dans l’organisation locale.
- Une licence Microsoft Teams doit être attribuée à l’utilisateur dont la boîte aux lettres principale se trouve dans l’organisation locale et au minimum d’une licence Exchange Online (plan 1).
- Si votre organisation ne comporte pas de déploiement Exchange hybride, vous devez synchroniser votre schéma Exchange local avec Azure Active Directory. Sinon, vous risquez de créer des boîtes aux lettres informatiques en double dans Exchange Online pour les utilisateurs disposant d’une boîte aux lettres dans votre organisation Exchange locale.
- Seules les données de conversation Teams associées à un utilisateur local sont stockées dans la zone de stockage basée sur le cloud. Un utilisateur local ne peut en aucune façon accéder à cette zone de stockage.

> [!NOTE]
> Les conversations pa canaux Teams sont toujours stockées dans la boîte aux lettres basée sur le cloud qui est associée à Teams, ce qui signifie que vous pouvez rechercher des conversations dans les canaux. Pour plus d’informations sur la recherche conversations par canaux Teams, consultez[Recherche Microsoft Teams et Groupes Microsoft 365](content-search-reference.md#searching-microsoft-teams-and-microsoft-365-groups).
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="how-it-works"></a>Mode de fonctionnement

Si un utilisateur Microsoft Teams a une boîte aux lettres locale et que son compte d’utilisateur/son identité est synchronisé avec le cloud, Microsoft crée un stockage dans le cloud pour l’associer aux données de conversations Teams 1xN de l’utilisateur local. Les données de conversations Teams pour les utilisateurs locaux sont indexées pour la recherche. Cela vous permet d’utiliser la recherche de contenu (et les recherches associées aux cas Microsoft Purview eDiscovery (Standard) et Microsoft Purview eDiscovery (Premium) pour rechercher, afficher un aperçu et exporter des données de conversation Teams pour les utilisateurs locaux. Vous pouvez également utiliser **\*** les applets de commande ComplianceSearch dans [Security & Compliance PowerShell](/powershell/exchange/scc-powershell) pour rechercher des données de conversation Teams pour les utilisateurs locaux.
  
Le graphique suivant montre comment Teams peut consulter les données de conversation pour les utilisateurs locaux pour pouvoir effectuer des recherches, des aperçus et des exportations.
  
![Stockage sur le cloud pour les utilisateurs locaux de Microsoft Teams.](../media/EHAMShard1.png)
  
En plus de cette fonctionnalité, vous pouvez également utiliser les outils eDiscovery pour rechercher, afficher un aperçu, et exporter du contenu Teams sur le site SharePoint utilisant le cloud et sur la boîte aux lettres Exchange associée à chaque donnée de conversation Microsoft Teams et 1xN Teams dans la boîte aux lettres Exchange Online pour les utilisateurs du cloud.

## <a name="searching-for-teams-chat-content-for-on-premises-users"></a>Recherche du contenu de conversations Teams pour des utilisateurs locaux

Voici comment utiliser la recherche de contenu dans le portail de conformité Microsoft Purview pour rechercher des données de conversation de Teams pour des utilisateurs locaux. Vous pouvez également utiliser l’outil de recherche dans eDiscovery (Standard) pour rechercher des données de conversation pour des utilisateurs locaux.
  
1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Recherche de contenu**.

2. Sous l’onglet **Recherches** , sélectionnez **Nouvelle recherche**, puis nommez la nouvelle recherche.

3. Dans la page **Emplacements** , définissez la bascule sur **Activé** pour les boîtes aux lettres Exchange.

4. Pour rechercher du contenu Teams pour des utilisateurs spécifiques (y compris des utilisateurs locaux), sélectionnez **Choisir un utilisateur, des groupes ou des équipes** et choisissez des utilisateurs spécifiques à inclure dans la recherche. Si vous ne répertoriez pas d’utilisateurs spécifiques, la recherche inclut tous les utilisateurs, y compris les utilisateurs locaux.

5. Vérifiez que la case à cocher **Ajouter du contenu d’application pour les utilisateurs locaux** est cochée. Cela garantit que le stockage de bases cloud pour les utilisateurs locaux sera recherché.

    ![Activez la case à cocher « Ajouter du contenu d’application Office pour les utilisateurs locaux » dans la page de l’Assistant Emplacements.](../media/EHAMShardCheckBox.png)

6. Dans la page **Définir vos conditions de recherche**, créez une requête mot clé et ajoutez des conditions à la requête de recherche si nécessaire. Pour rechercher uniquement les données de conversations Teams, vous pouvez ajouter la requête suivante dans la zone **Mots clés** :

    ```text
    kind:im AND kind:microsoftteams
    ```

6. Envoyez et exécutez la recherche. Les résultats de recherche pour des utilisateurs locaux peuvent être prévisualisés comme tout autre résultat de recherche. Vous pouvez également exporter les résultats de la recherche (y compris les données de conversation des équipes) vers un fichier PST. Pour plus d’informations, voir :

    - [Créer une recherche](content-search.md)
    - [Aperçu des résultats de la recherche](preview-ediscovery-search-results.md)
    - [Exporter les résultats de la recherche](export-search-results.md)

## <a name="using-powershell-to-search-for-teams-chat-data-for-on-premises-users"></a>Utilisation de PowerShell pour la recherche de données de conversations Teams pour les utilisateurs locaux

Vous pouvez utiliser les applets de commande **New-ComplianceSearch** dans [Security & Compliance PowerShell](/powershell/exchange/scc-powershell) pour rechercher des données de conversation Teams pour les utilisateurs locaux. Comme indiqué précédemment, vous n’êtes pas obligé de soumettre une demande de support pour utiliser PowerShell pour rechercher des données de conversation Teams pour les utilisateurs locaux.
  
1. Connectez-vous à [Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Exécutez la commande PowerShell suivante pour créer une recherche de contenu qui recherche des données de conversations Teams pour des utilisateurs locaux.

    ```powershell
    New-ComplianceSearch <name of new search> -ContentMatchQuery <search query> -ExchangeLocation <on-premises user> -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

    Le paramètre *IncludeUserAppContent* est utilisé pour spécifier le stockage cloud pour l’utilisateur ou les utilisateurs spécifiés par le paramètre *ExchangeLocation*. *AllowNotFoundExchangeLocationsEnabled* vous permet d’effectuer une recherche dans le stockage cloud pour les utilisateurs locaux. Lorsque vous utilisez la valeur `$true` pour ce paramètre, la recherche n’essaie pas de valider l’existence de la boîte aux lettres avant son exécution. Celle-ci est nécessaire pour effectuer des recherches dans le stockage cloud des utilisateurs locaux, car ce stockage cloud n’est pas résolu comme une boîte aux lettres cloud normale.

    L’exemple suivant recherche les conversations Teams qui contiennent le mot clé « redstone » dans le stockage basé sur le cloud de Marie Davis, utilisateur local de l’organisation Contoso.
  
    ```powershell
    New-ComplianceSearch "Redstone_Search" -ContentMatchQuery "redstone AND (kind:im AND kind:microsoftteams)" -ExchangeLocation sarad@contoso.com -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

   Une fois que vous avez créé une recherche, veillez à utiliser l’applet de commande **Start-ComplianceSearch** pour lancer la recherche.
  
Pour plus d’informations sur l’utilisation de ces applets de commande, consultez :
  
- [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch)
- [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, vous pouvez rechercher, afficher un aperçu et exporter des données de conversations Teams pour les utilisateurs locaux. Vous pouvez également placer en attente des données de conversations Teams pour un utilisateur local sur un cas Core ou eDiscovery (Premium), et appliquer une stratégie de rétention pour les conversations Teams ou les messages de canal pour les utilisateurs locaux. Pour l’instant, vous ne pouvez pas appliquer une stratégie de rétention pour d’autres emplacements de contenu (tels que les boîtes aux lettres Exchange et les sites SharePoint) pour les utilisateurs locaux.

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

**Dois-je soumettre une demande de support pour rechercher des messages de conversation d’utilisateurs locaux ?**

Non. Cette fonctionnalité est activée par défaut pour toutes les organisations. À un moment, vous deviez contacter le support Microsoft, mais ce n’est plus le cas.
  
 **Les outils eDiscovery peuvent-ils rechercher des anciennes données de conversation Teams d’utilisateurs locaux datant de la période antérieure à l’activation par défaut de cette fonctionnalité pour toutes les organisations ?**
  
Microsoft started storing the Teams chat data for on-premises users on January 31, 2018. So, if the identity of an on-premises Teams user has been synched between you on-premises Active Directory and Azure Active Directory in Microsoft 365 since this date, then their Teams chat data is stored in the cloud and is searchable using eDiscovery tools.

 **Les utilisateurs locaux ont-ils besoin d’une licence pour stocker leurs données de conversations Teams dans le cloud ?**
  
Yes. To store Teams chat data for an on-premises user in a cloud-based storage, the user must be assigned a Microsoft Teams license and an Exchange Online Plan license in Office 365 (or Microsoft 365).

**Où se trouve le stockage cloud pour les utilisateurs locaux ?**
  
Les données de conversation de Teams sont stockées dans le site PDL (Preferred Data Location) d’un utilisateur local. Le PDL est respecté à la fois dans les environnements Mono-Géo et Multi-Géo. Pour en savoir plus, consultez [Microsoft 365 Multigéographie](../enterprise/microsoft-365-multi-geo.md).

**Y a-t-il un risque de perdre les données de conversation Teams si la boîte aux lettres locale de l’utilisateur est déplacée vers le cloud ?**
  
No. When you migrate the primary mailbox of an on-premises user to the cloud, the Teams chat data for that user will be migrated to their new cloud-based primary mailbox.
  
 **Puis-je appliquer une conservation eDiscovery ou des stratégies de rétention à des utilisateurs locaux ?**
  
Oui. Vous pouvez appliquer des conservations eDiscovery ou des stratégies de rétention pour les conversations Teams et les messages de canaux pour les utilisateurs locaux. Toutefois, pour conserver ou conserver le contenu Teams pour les utilisateurs locaux, un utilisateur local doit se voir attribuer une licence Exchange Online Plan 2.
