---
title: Recherche de boîtes aux lettres sur le cloud des utilisateurs locaux
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
localization_priority: Priority
search.appverid:
- MOE150
- MST160
- MET150
ms.assetid: 3f7dde1a-a8ea-4366-86da-8ee6777f357c
description: Utilisez l’outil recherche de contenu dans le centre de conformité et de sécurité pour rechercher et exporter des données de conversation MicrosoftTeams (appelées conversations 1xN) pour les utilisateurs locaux dans un déploiement hybride Exchange.
ms.openlocfilehash: ab523c0d2d334d3d2366711e241b3bafa2e0002f
ms.sourcegitcommit: 40ec697e27b6c9a78f2b679c6f5a8875dacde943
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "44352117"
---
# <a name="searching-cloud-based-mailboxes-for-on-premises-users"></a>Recherche de boîtes aux lettres sur le cloud des utilisateurs locaux

Si votre organisation dispose d'un déploiement hybride d'Exchange (ou si votre organisation synchronise une organisation Exchange sur site avec Office 365) et a activé Microsoft Teams, les utilisateurs peuvent utiliser l'application de conversation Teams pour la messagerie instantanée. Pour un utilisateur dans le cloud, les données de conversation Teams (également appelées *conversations 1xN*) sont enregistrées dans leur boîte aux lettres principale basée sur le cloud. Lorsqu’un utilisateur local utilise l’application de conversation Teams, sa boîte aux lettres principale est localisée en local. Pour contourner cette limitation, Microsoft a publié une nouvelle fonctionnalité dans laquelle une zone de stockage basée sur le cloud (appelée boîte aux lettres basée sur le cloud pour les utilisateurs locaux) est créée pour stocker les données de conversation Teams pour les utilisateurs locaux. Cela vous permet d’utiliser l’outil recherche de contenu dans le centre de sécurité et de conformité pour rechercher et exporter des données de conversation pour les utilisateurs locaux. 
  
Voici la configuration requise et les limitations applicables à la configuration de boîtes aux lettres cloud pour les utilisateurs locaux :
  
- Les comptes d’utilisateurs dans votre service d’annuaire local (par exemple, Active Directory) doivent être synchronisés avec Azure Active Directory (service d’annuaire dans Microsoft 365). Cela signifie qu’un compte d’utilisateur de courrier est créé dans Microsoft 365 et est associé à un utilisateur dont la boîte aux lettres principale se trouve dans l’organisation locale.

- Une licence Microsoft Teams doit être attribuée à l’utilisateur dont la boîte aux lettres principale se trouve dans l’organisation locale et au minimum d’une licence Exchange Online (plan 1).

- La boîte aux lettres basée sur le cloud pour les utilisateurs locaux est utilisée uniquement les données de conversation Tems de stockage. Un utilisateur local ne peut pas se connecter à la boîte aux lettres basée sur le cloud ou à un accès de quelque manière que ce soit. Il ne peut pas être utilisé pour envoyer ou recevoir des e-mails. 

- Vous devez envoyer une demande de Support Microsoft pour permettre à votre organisation de rechercher des équipes dans les boîtes aux lettres dans le cloud pour les utilisateurs locaux. Consultez [Classement d’une demande auprès du Support Microsoft pour activer cette fonctionnalité](#filing-a-request-with-microsoft-support-to-enable-this-feature) dans cet article. 

> [!NOTE]
> Les conversations pa canaux Teams sont toujours stockées dans la boîte aux lettres basée sur le cloud qui est associée à Teams. Cela signifie que vous pouvez utiliser la recherche de contenu pour rechercher des conversations de canal sans avoir à classer une demande de support. Pour plus d’informations sur la recherche conversations par canaux Teams, consultez[Recherche Microsoft Teams et Groupes Microsoft 365](content-search.md#searching-microsoft-teams-and-microsoft-365-groups).
  
## <a name="how-it-works"></a>Mode de fonctionnement

Si un utilisateur de Microsoft Teams a une boîte aux lettres locale et que son compte d’utilisateur/son identité est synchronisé avec le cloud, Microsoft crée une boîte aux lettres basée sur le cloud pour stocker les données de conversation de 1xN Teams. Une fois les données de conversation Teams stockées dans la boîte aux lettres basée sur le cloud, celles-ci sont indexées pour la recherche. Cela vous permet d’utiliser la recherche de contenu (et les recherches associées à des cas eDiscovery) pour rechercher, afficher un aperçu et exporter des données de conversation pour les utilisateurs locaux. Vous pouvez également utiliser les applets de commande**\*ComplianceSearch**dans le centre de conformité et de sécurité PowerShell pour rechercher des données de conversation Teams pour les utilisateurs locaux. 
  
Le graphique suivant montre comment Teams peut consulter les données de conversation pour les utilisateurs locaux pour pouvoir effectuer des recherches, des aperçus et des exportations.
  
![Stockage sur le cloud pour les utilisateurs locaux de Microsoft Teams](../media/EHAMShard1.png)
  
En plus de cette nouvelle fonctionnalité, vous pouvez encore utiliser la recherche de contenu pour rechercher, afficher un aperçu et exporter du contenu d’équipes sur le site SharePoint dans le cloud et sur la boîte aux lettres Exchange associée à chaque Microsoft Teams et 1xN Teams discutent des données dans la boîte aux lettres Exchange Online pour utilisateurs dans le cloud.

## <a name="filing-a-request-with-microsoft-support-to-enable-this-feature"></a>Classement d’une demande auprès du Support Microsoft pour activer cette fonctionnalité

Vous devez effectuer une demande auprès du Support Microsoft pour autoriser votre organisation à utiliser l’interface utilisateur graphique dans le centre de conformité et sécurité pour rechercher des équipes dans les boîtes aux lettres en ligne des utilisateurs locaux. Cette fonctionnalité est disponible dans le centre de conformité et sécurité PowerShell. Vous n’êtes pas obligé de soumettre une demande de support pour utiliser PowerShell pour rechercher des données de conversation Teams pour les utilisateurs locaux.
  
Fournissez les informations suivantes lorsque vous envoyez la demande au Support Microsoft :
  
- Nom de domaine par défaut de votre organisation.

- Le nom du locataire et l’ID de client de votre organisation. Celles-ci sont disponibles dans le portail Azure Active Directory (sous **Gérer** \> **Propriétés**). Consultez [Rechercher votre ID de client Microsoft 365](https://docs.microsoft.com/onedrive/find-your-office-365-tenant-id).

- Le titre ou la description de l’objet de la demande de support : « Activer la recherche de contenu d’application pour les utilisateurs locaux ». Cette opération permet d’acheminer la demande vers l’équipe d’ingénierie d’eDiscovery qui implémente la demande.

Une fois la modification d’ingénierie effectuée, le Support Microsoft vous enverra une estimation de la date de déploiement. Le processus de déploiement prend généralement deux à trois semaines après l’envoi de la demande de support.
  
### <a name="what-happens-after-this-feature-is-enabled"></a>Que se passe-t-il si cette fonctionnalité est activée ?

Une fois cette fonctionnalité déployée dans votre organisation, les modifications suivantes sont apportées dans la recherche de contenu et dans les recherches associées à un cas de découverte électronique dans le centre de sécurité et conformité :
  
- La case à cocher **Ajouter du contenu d’application Office pour les utilisateurs locaux** est ajoutée aux **Emplacements** dans la recherche de contenu.

    ![La case à cocher « Ajouter du contenu d’application Office pour les utilisateurs locaux » est ajoutée à l’interface de recherche de contenu.](../media/599e751e-17bd-408d-a18c-127538de6e85.png)
  
- Les utilisateurs locaux sont affichés dans le sélecteur d’emplacements de contenu que vous utilisez pour sélectionner les boîtes aux lettres d’utilisateur à rechercher.

## <a name="searching-for-teams-chat-content-in-cloud-based-mailboxes-for-on-premises-users"></a>Recherche du contenu de conversation Teams dans les boîtes aux lettres sur le cloud des utilisateurs locaux

Une fois la fonctionnalité activée, vous pouvez utiliser la recherche de contenu dans le centre de conformité et sécurité pour rechercher des données de conversation Teams dans les boîtes aux lettres basées sur le cloud pour les utilisateurs locaux.
  
1. Dans le Centre de sécurité et conformité, accédez à **Rechercher** \> **Recherche de contenu**

2. Sur la page de**recherche**, cliquez sur ![Ajouter une icône](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif) **Nouvelle recherche**.

    Comme indiqué précédemment, la case à cocher **Ajouter du contenu d’application Office pour les utilisateurs locaux** s’affiche sous **Emplacements**. Elle est sélectionnée par défaut.

3. Créez la requête de mot clé et ajoutez des conditions à la requête de recherche, le cas échéant. Pour rechercher uniquement les données de conversations Teams, vous pouvez ajouter la requête suivante dans la zone **Mots clés** :

    ```text
    kind:im
    ```

4. À ce stade, vous pouvez choisir l’une des options suivantes sous **Emplacements**:

    - **Tous les emplacements :** sélectionnez cette option pour effectuer une recherche dans les boîtes aux lettres de tous les utilisateurs de votre organisation. Lorsque la case est cochée, toutes les boîtes aux lettres basées sur le cloud pour les utilisateurs locaux sont également recherchées.

    - **Emplacements spécifiques :** sélectionnez cette option, puis cliquez sur **Modifier** \> Choisir un utilisateur, groupes ou équipes pour rechercher des boîtes aux lettres spécifiques. Comme indiqué précédemment, le sélecteur d’emplacements vous permet de rechercher des utilisateurs locaux.

5. Enregistrez et exécutez la recherche. Les résultats de recherche des boîtes aux lettres dans le cloud des utilisateurs locaux peuvent être prévisualisés comme tout autre résultat de recherche. Vous pouvez également exporter les résultats de la recherche (y compris les données de conversation des équipes) vers un fichier PST. Pour plus d’informations, voir : 

    - [Créer une recherche](content-search.md#create-a-search)

    - [Aperçu des résultats de la recherche](content-search.md#preview-search-results)

    - [Exporter les résultats de la recherche de contenu](export-search-results.md)

## <a name="using-powershell-to-search-for-teams-chat-data-in-cloud-based-mailboxes-for-on-premises-users"></a>Utiliser PowerShell pour rechercher des données de conversation Teams dans les boîtes aux lettres sur le cloud des utilisateurs locaux

Vous pouvez utiliser les applets de commande **New-ComplianceSearch** et **ComplianceSearch** dans le centre de sécurité et conformité PowerShell pour effectuer une recherche dans la boîte aux lettres basée sur le Cloud pour les utilisateurs locaux. Comme indiqué précédemment, vous n’êtes pas obligé de soumettre une demande de support pour utiliser PowerShell pour rechercher des données de conversation Teams pour les utilisateurs locaux. 
  
1. [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. Exécutez la commande PowerShell suivante pour créer une recherche de contenu qui recherche dans les boîtes aux lettres basées sur le cloud des utilisateurs locaux.

    ```powershell
    New-ComplianceSearch <name of new search> -ContentMatchQuery <search query> -ExchangeLocation <on-premises user> -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

    Le paramètre *IncludeUserAppContent* est utilisé pour spécifier la boîte aux lettres basée sur le cloud pour l’utilisateur ou les utilisateurs spécifiés par le paramètre *ExchangeLocation*. La *AllowNotFoundExchangeLocationsEnabled* autorise les boîtes aux lettres basées sur le cloud pour les utilisateurs locaux. Lorsque vous utilisez la valeur `$true` pour ce paramètre, la recherche n’essaie pas de valider l’existence de la boîte aux lettres avant son exécution. Celle-ci est nécessaire pour effectuer des recherches dans les boîtes aux lettres basées sur le cloud pour les utilisateurs locaux, car ces types de boîtes aux lettres ne sont pas résolus comme des boîtes aux lettres normales.

    L’exemple suivant recherche les conversations Teams (messages instantanés) qui contiennent le mot clé « redstone » dans la boîte aux lettres basée sur le cloud de Marie Davis, utilisateur local de l’organisation Contoso.
  
    ```powershell
    New-ComplianceSearch "Redstone_Search" -ContentMatchQuery "redstone AND kind:im" -ExchangeLocation sarad@contoso.com -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

   Une fois que vous avez créé une recherche, veillez à utiliser l’applet de commande **Start-ComplianceSearch** pour lancer la recherche. 
  
Pour plus d’informations sur l’utilisation de ces applets de commande, consultez :
  
- [New-ComplianceSearch](https://docs.microsoft.com/powershell/module/exchange/new-compliancesearch)

- [Set-ComplianceSearch](https://docs.microsoft.com/powershell/module/exchange/set-compliancesearch)

- [Start-ComplianceSearch](https://docs.microsoft.com/powershell/module/exchange/start-compliancesearch)

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, vous pouvez rechercher, afficher un aperçu et exporter du contenu dans les boîtes aux lettres dans le cloud pour les utilisateurs locaux. Vous pouvez également placer une boîte aux lettres basée sur le cloud pour un utilisateur local sur une conservation associée à un cas de découverte électronique, et appliquer une stratégie de rétention pour les conversations ou les messages de canal aux boîtes aux lettres dans le cloud pour les utilisateurs locaux. Pour l’instant, vous ne pouvez pas appliquer une stratégie de rétention pour d’autres emplacements de contenu (tels que les boîtes aux lettres Exchange et les sites SharePoint) aux boîtes aux lettres basées sur le cloud pour les utilisateurs locaux.

## <a name="frequently-asked-questions"></a>Foire aux questions

 **Où se trouvent les boîtes aux lettres sur le cloud des utilisateurs locaux ?**
  
Les boîtes aux lettres basées sur le cloud sont créées et stockées dans le même centre de données que votre organisation.
  
 **Y a-t-il d’autres programmes requis que l’envoi d’une demande de support ?**
  
 Comme indiqué précédemment, les identités des utilisateurs disposant de boîtes aux lettres local doivent être synchronisées avec votre organisation cloud de sorte qu’un compte d’utilisateur de courrier correspondant soit créé pour chaque compte d’utilisateur local dans Office 365. Votre organisation doit également disposer d’un abonnement Office 365 Enterprise, tel qu’un abonnement Office 365 Entreprise E1, E3 ou E5.
  
 **Y a-t-il un risque de perdre les données de conversation Teams si la boîte aux lettres locale de l’utilisateur est déplacée vers le cloud ?**
  
Non. Lorsque vous migrez la boîte aux lettres principale d’un utilisateur local vers le cloud, les informations de conversation associées à cet utilisateur sont déplacées vers leur nouvelle boîte aux lettres principale basée sur le cloud.
  
 **Puis-je appliquer une conservation eDiscovery ou des stratégies de rétention à des utilisateurs locaux ?**
  
Oui. Vous pouvez appliquer des conservations eDiscovery ou des stratégies de rétention pour les conversations Teams et les messages de canaux vers les boîtes aux lettres dans le cloud pour les utilisateurs locaux.
  
 **Possibilité de rechercher du contenu Rechercher des conversations plus anciennes Teams pour les utilisateurs locaux avant que mon organisation ait soumis la demande d’activation de cette fonctionnalité ?**
  
Microsoft a commencé à stocker les informations de conversation Teams pour les utilisateurs locaux le 31 janvier 2018. Par conséquent, si l’identité d’un utilisateur Teams locale a été synchronisée entre Active Directory et Azure Active Directory depuis cette date, ses données de conversation Teams sont stockées dans une boîte aux lettres basée sur le cloud et peut faire l’objet d’une recherche à l’aide de la recherche de contenu. Microsoft travaille également au stockage des données de conversation Teams antérieures au 31 janvier 2018 dans les boîtes aux lettres basées sur le cloud pour les utilisateurs locaux. Des informations supplémentaires sont disponibles prochainement.

 **Les utilisateurs locaux ont besoin d’une licence pour stocker les données de conversation Teams dans une boîte aux lettres dans le cloud ?**
  
Oui. Pour stocker les informations de conversation Teams pour un utilisateur local dans une boîte aux lettres dans le cloud, l’utilisateur doit avoir une licence Microsoft Teams et une licence Exchange Online plan dans Office 365 (ou Microsoft 365).
