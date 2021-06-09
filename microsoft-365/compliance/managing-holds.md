---
title: Gérer les Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment placer des conservations sur les dépositaires et leurs sources de données pour conserver le contenu pertinent pour Advanced eDiscovery cas.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 70390a933de788a6b1190e42b5087b85a175b9a2
ms.sourcegitcommit: 6e5c00f84b5201422aed094f2697016407df8fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51570588"
---
# <a name="manage-holds-in-advanced-ediscovery"></a>Gérer les Advanced eDiscovery

Vous pouvez utiliser un cas Advanced eDiscovery pour créer des conservations afin de conserver le contenu qui peut être pertinent pour votre cas. Grâce aux fonctionnalités Advanced eDiscovery de conservation, vous pouvez placer des conservations sur les dépositaires et leurs sources de données. En outre, vous pouvez placer des boîtes aux lettres et des sites OneDrive Entreprise en attente non verrouillés. Vous pouvez également placer en attente la boîte aux lettres de groupe, SharePoint site et le site OneDrive Entreprise pour un groupe Microsoft 365 groupe. De même, vous pouvez placer en attente la boîte aux lettres et le site associés à Microsoft Teams. Lorsque vous placez des emplacements de contenu en conservation, le contenu est mis en attente jusqu’à ce que vous ôtiez le dépositaire, que vous supprimiez un emplacement de données spécifique ou que vous supprimiez entièrement la stratégie de conservation.

## <a name="manage-custodian-based-holds"></a>Gérer les conservations basées sur les dépositaires

Dans certains cas, vous pouvez avoir un ensemble de dépositaires que vous avez identifiés et que vous avez décidé de conserver leurs données pendant le cas. Dans Advanced eDiscovery, lorsque ces dépositaires sont placés en conservation, l’utilisateur et les sources de données sélectionnées sont automatiquement ajoutés à une stratégie de conservation des dépositaires.

Pour afficher la stratégie de conservation des dépositaires :

1. Dans le centre Microsoft 365 conformité, cliquez sur **eDiscovery > Advanced** pour afficher la liste des cas dans votre organisation.

2. Go to the **Sources** tab to add custodians within your case. Pour savoir comment ajouter et placer des dépositaires en conservation dans un Advanced eDiscovery, voir Ajouter des [dépositaires à un cas.](add-custodians-to-case.md) Si vous avez déjà ajouté des dépositaires et les avez placés en conservation, allez à l’étape 3.

3. Go to the **Holds** tab and click **CustodianHold \<HoldId>**.

4. Dans la page volante, vous pouvez voir les statistiques de la stratégie de hold. Vous pouvez également effectuer des actions telles que l’application d’une requête à votre conservation basée sur les dépositaires. Pour plus d’informations sur la création d’une requête de mise en attente et l’utilisation de conditions, voir Requêtes par mot clé et conditions de recherche [pour la recherche de contenu.](keyword-queries-and-search-conditions.md)

## <a name="manage-non-custodial-holds"></a>Gérer les placements non privatives

Lorsque vous créez une attente, vous avez les options suivantes pour l’étendue du contenu qui est placé dans les emplacements de contenu spécifiés :

- Vous créez une mise en attente infinie dans laquelle tout le contenu est mis en attente. Vous pouvez également créer une mise en attente basée sur une requête dans laquelle seul le contenu qui correspond à une requête de recherche est mis en attente.
  
- Vous pouvez spécifier une plage de dates pour contenir uniquement le contenu qui a été envoyé, reçu ou créé dans cette plage de dates. Vous pouvez également conserver tout le contenu, quel que soit le moment où il a été envoyé, reçu ou créé.

Pour créer une mise en attente non privative pour Advanced eDiscovery cas :

1. Dans le centre Microsoft 365 conformité, cliquez sur **eDiscovery > Advanced** pour afficher la liste des cas dans votre organisation.
  
2. Cliquez **sur Ouvrir** en face du cas où vous souhaitez créer les conserves.
  
3. Dans la page d’accueil du cas, cliquez sur **l’onglet Contient.**
  
4. Sous **l’onglet Contient,** cliquez sur **Créer.**
  
5. Dans la page **Nom de votre** attente, donnez un nom à la attente. Le nom de la conservation doit être unique dans toute votre organisation.
 
6. (Facultatif) Dans la **zone Description,** ajoutez une description de la attente.
  
7. Cliquez sur **Suivant**.
  
8. Choisissez les emplacements de contenu que vous souhaitez placer en attente. Vous pouvez placer des boîtes aux lettres, des sites et des dossiers publics en attente.

   1. **Exchange-** Cliquez sur Choisir les utilisateurs, les groupes ou les **équipes,** puis cliquez à nouveau sur Choisir des **utilisateurs,** des groupes ou des équipes pour spécifier les boîtes aux lettres à placer en attente. Utilisez la zone de recherche pour rechercher des boîtes aux lettres utilisateur et des groupes de distribution (pour placer les boîtes aux lettres des membres du groupe en conservation) à placer en conservation. Vous pouvez également placer en attente la boîte aux lettres associée d’un groupe Microsoft 365 ou d’une équipe Microsoft. Sélectionnez la case à cocher Utilisateur, Groupe, Équipe, Cliquez sur **Choisir,** puis cliquez sur **Terminé**.
 
      > [!NOTE]
      > Lorsque vous cliquez sur Choisir des **utilisateurs,** des groupes ou des équipes pour spécifier les boîtes aux lettres à placer en attente, le soche de boîte aux lettres qui s’affiche est vide. Il s’agit d’une conception pour améliorer les performances. Pour ajouter des personnes à cette liste, tapez un nom (un minimum de 3 caractères) dans la zone de recherche.

   1. **SharePoint sites** : cliquez sur Choisir des **sites,** puis cliquez à nouveau sur Choisir des **sites** pour spécifier SharePoint sites OneDrive Entreprise sites à placer en attente. Saisissez l’URL de chaque site à placer en conservation. Vous pouvez également ajouter l’URL du site SharePoint pour un groupe Microsoft 365 ou une équipe Microsoft. Cliquez **sur Choisir,** puis sur **Terminé.**

      > [!NOTE]
      > L’URL du compte d’OneDrive utilisateur inclut son nom d’utilisateur principal (UPN) (par exemple, `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com` ). Dans les rares cas où l’UPN d’une personne est modifié, son URL OneDrive change également pour incorporer le nouveau nom d’upn. Si le compte OneDrive d’un utilisateur fait partie d’une mise en attente non privative et que son UPN est modifié, vous devez mettre à jour la mise en attente et pointer vers la nouvelle URL de OneDrive. Pour plus d’informations, voir [Comment les modifications du nom d’utilisateur principal affectent l’URL OneDrive](/onedrive/upn-changes).

   1. **Exchange publics** : déplacez le bouton bascule vers la position Tout pour placer tous les dossiers publics de votre organisation Exchange Online en attente. Notez que vous ne pouvez pas choisir des dossiers publics spécifiques à mettre en attente. Laissez le bouton bascule sur **Aucun** si vous ne souhaitez pas placer de mise en attente sur les dossiers publics.

9. Lorsque vous avez terminé d’ajouter des emplacements de contenu à la attente, cliquez sur **Suivant**.
  
10. Pour créer une attente basée sur une requête avec des conditions, complétez les conditions suivantes. Dans le cas contraire, cliquez simplement sur **Suivant**.
    
    - Dans la zone sous **Mots clés,** tapez une requête de recherche dans la zone afin que seul le contenu qui répond aux critères de recherche soit mis en attente. Vous pouvez spécifier des mots clés, des propriétés de message ou des propriétés de document, telles que des noms de fichiers. Vous pouvez également utiliser des requêtes plus complexes qui utilisent un opérateur booléen, comme AND, OR ou NOT. Si vous laissez la zone de mot clé vide, tout le contenu situé dans les emplacements de contenu spécifiés est mis en attente.

    - Cliquez  **sur Ajouter** des conditions pour ajouter une ou plusieurs conditions afin de restreindre la requête de recherche pour la attente. Chaque condition ajoute une clause à la requête de recherche KQL qui est créée et qui s’exécute lorsque vous créez la requête de recherche KQL. Par exemple, vous pouvez spécifier une plage de dates afin que les documents électroniques ou de site créés dans la plage de dates soient mis en attente. Une condition est connectée à la requête de mot-clé (spécifiée dans la zone de mot-clé) sur le plan logique par l’opérateur AND. Cela signifie que les éléments doivent satisfaire la requête de mot clé et la condition à placer en attente.

     Pour plus d’informations sur la création d’une requête de recherche et l’utilisation de conditions, voir Requêtes par mot clé et conditions de recherche [pour la recherche de contenu.](/office365/SecurityCompliance/keyword-queries-and-search-conditions)

11. Après avoir configuré une attente basée sur une requête, cliquez sur **Suivant.**

12. Examinez vos paramètres, puis cliquez sur **Créer cette mise en attente.**

## <a name="view-hold-statistics"></a>Afficher les statistiques de la attente

Après un certain temps, les informations sur la nouvelle attente s’affichent dans le volet d’informations sous l’onglet **Attentes** pour la nouvelle attente sélectionnée. Ces informations incluent le nombre de boîtes aux lettres et de sites en attente, ainsi que les statistiques sur le contenu placé en attente, telles que le nombre total et la taille des éléments placés en attente et la dernière fois que les statistiques de mise en attente ont été calculées. Ces statistiques de la découverte électronique vous aident à identifier la quantité de contenu liée au cas eDiscovery.

Gardez les points suivants à l’esprit concernant les statistiques de la attente :

- Le nombre total d’éléments en attente indique le nombre d’éléments de toutes les sources de contenu placés en attente. Si vous avez créé une attente basée sur une requête, cette statistique indique le nombre d’éléments qui correspondent à la requête.
  
- Le nombre d’éléments en attente inclut également les éléments nonndex trouvés dans les emplacements de contenu. Notez que si vous créez une mise en attente basée sur une requête, tous les éléments nonndex dans les emplacements de contenu sont placés en attente. Cela inclut les éléments nonndex qui ne correspondent pas aux critères de recherche d’une attente basée sur une requête et les éléments nonndex qui peuvent se trouver en dehors d’une condition de plage de dates. Cela est différent de ce qui se produit lorsque vous exécutez une recherche de contenu, dans laquelle les éléments nonndex qui ne correspondent pas à la requête de recherche ou qui sont exclus par une condition de plage de dates ne sont pas inclus dans les résultats de la recherche. Pour plus d’informations sur les éléments non indexés, voir Éléments partiellement [indexés](partially-indexed-items-in-content-search.md)dans la recherche de contenu dans Office 365 . 

- Vous pouvez obtenir les dernières statistiques de mise en attente en cliquant sur Mettre à jour les statistiques pour ré-exécuter une estimation de la recherche qui calcule le nombre actuel d’éléments en attente.

- Si nécessaire, cliquez sur Actualiser dans la barre d’outils pour mettre à jour les statistiques de mise en attente dans le volet d’informations.

- Il est normal que le nombre d’éléments en attente augmente au fil du temps, car les utilisateurs dont la boîte aux lettres ou le site est en attente envoient ou reçoivent généralement de nouveaux messages électroniques et créent des documents SharePoint et OneDrive Entreprise.

- Si un site SharePoint ou un compte OneDrive est déplacé vers une autre région dans un environnement multigéogé, les statistiques de ce site ne seront pas incluses dans les statistiques de la recherche. Toutefois, le contenu du site sera toujours en attente. En outre, si un site est déplacé vers une autre région, l’URL affichée dans la mise en attente ne sera pas mise à jour. Vous devez modifier la mise en attente et mettre à jour l’URL.

## <a name="place-a-hold-on-microsoft-teams-and-office-365-groups"></a>Placer en attente les groupes Microsoft Teams et Office 365 de groupe

Microsoft Teams sont créés sur Office 365 groupes. Par conséquent, leur mise en attente Advanced eDiscovery est très similaire.

- **Comment puis-je ma cartographier un Microsoft 365 groupes ou un site Microsoft Teams à un dépositaire ? Et qu’en est-il du placement d’une mise en attente non Microsoft 365 groupes et Microsoft Teams ?** Microsoft Teams sont créés sur Microsoft 365 groupes. Par conséquent, les placer en attente dans un cas eDiscovery est très similaire. Gardez les points suivants à l’esprit lorsque vous Microsoft 365 groupes et Microsoft Teams en attente.
  - Pour placer le contenu situé dans les groupes Microsoft 365 et Microsoft Teams en attente, vous devez spécifier la boîte aux lettres et le site SharePoint associés à un groupe ou à une équipe.
  
  - Exécutez la cmdlet **Get-UnifiedGroup** dans Exchange Online pour afficher les propriétés d’Microsoft 365 groupe ou Microsoft Team. Il s’agit d’un bon moyen d’obtenir l’URL du site associé à un groupe Microsoft 365 ou Microsoft Team. Par exemple, la commande suivante affiche les propriétés sélectionnées d’un groupe Microsoft 365 nommé Senior Leadership Team :


    ```console
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Pour exécuter l'applet de commande Get-UnifiedGroup, vous devez avoir le rôle de destinataires en affichage seul dans Exchange Online ou être membre d’un groupe de rôles affecté du rôle de destinataires en affichage seul.

 - Lorsque la recherche est sur la boîte aux lettres d’un utilisateur, aucun groupe Microsoft 365 ou Microsoft Team dont l’utilisateur est membre n’est pas recherché. De même, lorsque vous placez une Microsoft 365 groupe ou microsoft Team, seules la boîte aux lettres de groupe et le site de groupe sont placés en attente . Les boîtes aux lettres et OneDrive Entreprise sites de membres du groupe ne sont pas placés en conservation, sauf si vous les ajoutez explicitement en tant que dépositaires ou que vous placez leurs sources de données en conservation. Par conséquent, si vous avez besoin de placer un groupe Microsoft 365 ou Microsoft Team en conservation pour un dépositaire spécifique, envisagez de ma mappage du site de groupe et de la boîte aux lettres de groupe au dépositaire (voir Gestion des dépositaires dans Advanced eDiscovery). Si le groupe Microsoft 365 ou l’équipe Microsoft n’est pas attribué à un seul dépositaire, envisagez d’ajouter la source à une conservation non-privative. 
 
 - Pour obtenir la liste des membres d’un groupe Microsoft 365 ou d’une équipe Microsoft, vous pouvez afficher les propriétés sur la page Groupes d’accueil > dans le Centre d’administration Microsoft 365. Vous pouvez également exécuter la commande suivante dans Exchange Online PowerShell :

   ```powershell
   Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
   ```

    > [!NOTE]
    > Pour exécuter l'applet de commande **Get-UnifiedGroupLinks**, vous devez avoir le rôle de destinataires en affichage seul dans Exchange Online ou être membre d’un groupe de rôles affecté du rôle de destinataires en affichage seul.

- Les conversations de canal qui font partie d’un canal Microsoft Teams sont stockées dans la boîte aux lettres associée à l’équipe. De même, les fichiers partagés par les membres d’une équipe dans un canal sont stockés sur le site SharePoint de l’équipe. Par conséquent, vous devez placer la boîte aux lettres de l’équipe Microsoft et le site SharePoint en attente pour conserver les conversations et les fichiers dans un canal.
  
- En outre, les conversations qui font partie de la liste de conversation dans Microsoft Teams sont stockées dans la boîte aux lettres de l’utilisateur qui participe à la conversation.  Les fichiers qu’un utilisateur partage dans les conversations de conversation sont stockés dans le site OneDrive Entreprise de l’utilisateur qui partage le fichier. Par conséquent, vous devez placer les boîtes aux lettres des utilisateurs individuels et les sites OneDrive Entreprise en attente pour conserver les conversations et les fichiers dans la liste de conversation. 
  
- Chaque équipe Microsoft ou canal d’équipe contient un Wiki pour la prise de notes et la collaboration. Le contenu wiki est automatiquement enregistré dans un fichier au format .mht. Ce fichier est stocké dans la bibliothèque de documents wiki Teams sur le site SharePoint de l’équipe. Vous pouvez mettre en attente le contenu du Wiki en mettant le site SharePoint de l’équipe en attente.

  > [!NOTE]
  > La possibilité de conserver le contenu Wiki pour une équipe Microsoft ou un canal d’équipe (lorsque vous placez le site SharePoint de l’équipe en attente) a été publiée le 22 juin 2017. Si un site d’équipe est en attente, le contenu wiki est conservé à partir de cette date. Toutefois, si un site d’équipe est en attente et que le contenu wiki a été supprimé avant le 22 juin 2017, le contenu wiki n’a pas été conservé.
