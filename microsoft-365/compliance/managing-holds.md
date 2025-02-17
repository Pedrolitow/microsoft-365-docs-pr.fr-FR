---
title: Gérer les conservations dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 04/27/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment placer des conservations sur les consignataires et leurs sources de données afin de conserver le contenu approprié pour votre cas eDiscovery (Premium).
ms.custom:
- seo-marvel-mar2020
- admindeeplinkMAC
ms.openlocfilehash: b5ea5b5b942bf3facd1858b5a40e3ec4d05ebc72
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67817265"
---
# <a name="manage-holds-in-ediscovery-premium"></a>Gérer les conservations dans eDiscovery (Premium)

Vous pouvez utiliser un cas Microsoft Purview eDiscovery (Premium) pour créer des conservations afin de conserver le contenu susceptible d’être pertinent pour votre cas. À l’aide des fonctionnalités de conservation eDiscovery (Premium), vous pouvez placer des conservations sur les consignats et leurs sources de données. En outre, vous pouvez placer une conservation non-custodiale sur les boîtes aux lettres et les sites OneDrive Entreprise. Vous pouvez également placer une conservation sur la boîte aux lettres de groupe, le site SharePoint et OneDrive Entreprise site pour un groupe Microsoft 365. De même, vous pouvez placer une conservation sur la boîte aux lettres et le site associés à Microsoft Teams. Lorsque vous placez des emplacements de contenu en attente, le contenu est conservé jusqu’à ce que vous libériez le consignateur, que vous supprimiez un emplacement de données spécifique ou que vous supprimiez entièrement la stratégie de conservation.

## <a name="manage-custodian-based-holds"></a>Gérer les conservations basées sur les consignats

Dans certains cas, vous pouvez avoir un ensemble de consignataires que vous avez identifiés et que vous avez décidé de conserver leurs données pendant le cas. Dans eDiscovery (Premium), lorsque ces consignats sont mis en attente, l’utilisateur et ses sources de données sélectionnées sont automatiquement ajoutés à une stratégie de conservation des consignatateurs.

Pour afficher la stratégie de conservation du consignatien :

1. Dans le portail de conformité Microsoft Purview, cliquez sur **eDiscovery > Avancé** pour afficher la liste des cas dans votre organisation.

2. Accédez à l’onglet **Sources** pour ajouter des consignatateurs dans votre cas. Pour savoir comment ajouter et mettre les consignatateurs en attente dans un cas eDiscovery (Premium), consultez [Ajouter des consignatateurs à un cas](add-custodians-to-case.md). Si vous avez déjà ajouté des consignats et les avez mis en attente, passez à l’étape 3.

3. Accédez à l’onglet **Conservations** , puis cliquez sur **CustodianHold\<HoldId>**.

4. Dans la page de menu volant, vous pouvez effectuer des actions telles que l’application d’une requête à votre conservation basée sur le consignat. Pour plus d’informations sur la création d’une requête de conservation et l’utilisation de conditions, consultez [les requêtes de mots clés et les conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md).

## <a name="manage-non-custodial-holds"></a>Gérer les conservations non liées à la garde

Lorsque vous créez une conservation, vous disposez des options suivantes pour étendre le contenu qui se trouve dans les emplacements de contenu spécifiés :

- Vous créez une conservation infinie où tout le contenu est mis en attente. Vous pouvez également créer une conservation basée sur une requête où seul le contenu correspondant à une requête de recherche est mis en attente.
  
- Vous pouvez spécifier une plage de dates pour contenir uniquement le contenu qui a été envoyé, reçu ou créé dans cette plage de dates. Vous pouvez également contenir tout le contenu, quel que soit le moment où il a été envoyé, reçu ou créé.

Pour créer une conservation non gardienne pour un cas eDiscovery (Premium) :

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité</a>, cliquez sur **eDiscovery > Avancé** pour afficher la liste des cas dans votre organisation.
  
2. Cliquez sur **Ouvrir** en regard du cas dans lequel vous souhaitez créer les conservations.
  
3. Dans la page d’accueil du cas, cliquez sur l’onglet **Conservations** .
  
4. Sous l’onglet **Conservations** , cliquez sur **Créer**.
  
5. Dans la page **Nom de votre conservation** , donnez un nom à la conservation. Le nom de la conservation doit être unique dans toute votre organisation.

6. (Facultatif) Dans la zone **Description** , ajoutez une description de la conservation.
  
7. Cliquez sur **Suivant**.
  
8. Choisissez les emplacements de contenu que vous souhaitez mettre en attente. Vous pouvez mettre en attente des boîtes aux lettres, des sites et des dossiers publics.

   1. **E-mail Exchange** : cliquez sur **Choisir des utilisateurs, des groupes ou des équipes,** puis cliquez à nouveau sur **Choisir des utilisateurs, des groupes ou des équipes** pour spécifier les boîtes aux lettres à mettre en attente. Utilisez la zone de recherche pour rechercher des boîtes aux lettres utilisateur et des groupes de distribution (pour placer les boîtes aux lettres des membres du groupe en conservation) à placer en conservation. Vous pouvez également placer une conservation sur la boîte aux lettres associée pour un groupe Microsoft 365 ou une équipe Microsoft. Sélectionnez l’utilisateur, le groupe, la case à cocher d’équipe, cliquez sur **Choisir**, puis cliquez sur **Terminé**.

      > [!NOTE]
      > Lorsque vous cliquez sur **Choisir des utilisateurs, des groupes ou des équipes** pour spécifier les boîtes aux lettres à mettre en attente, le sélecteur de boîte aux lettres affiché est vide. C’est par conception pour améliorer les performances. Pour ajouter des personnes à cette liste, tapez un nom (au moins 3 caractères) dans la zone de recherche.

   1. **Sites SharePoint** - Cliquez sur **Choisir des sites**, puis cliquez à nouveau sur **Choisir les sites** pour spécifier SharePoint et OneDrive Entreprise sites à mettre en attente. Saisissez l’URL de chaque site à placer en conservation. Vous pouvez également ajouter l’URL du site SharePoint pour un groupe Microsoft 365 ou une équipe Microsoft. Cliquez sur **Choisir**, puis sur **Terminé**.

      > [!NOTE]
      > L’URL du compte OneDrive d’un utilisateur inclut son nom d’utilisateur principal (UPN) (par exemple, `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). Dans les rares cas où l’UPN d’une personne est modifié, son URL OneDrive change également pour incorporer le nouvel UPN. Si le compte OneDrive d’un utilisateur fait partie d’une conservation non-custodiale et que son nom d’utilisateur principal est modifié, vous devez mettre à jour la conservation et pointer vers la nouvelle URL OneDrive. Pour plus d’informations, voir [Comment les modifications du nom d’utilisateur principal affectent l’URL OneDrive](/onedrive/upn-changes).

   1. **Dossiers publics Exchange** : déplacez le commutateur bascule vers la position Tout pour mettre tous les dossiers publics de votre organisation Exchange Online en attente. Vous ne pouvez pas choisir des dossiers publics spécifiques à mettre en attente. Laissez le commutateur bascule défini sur **Aucun** si vous ne souhaitez pas mettre une suspension sur les dossiers publics.

9. Lorsque vous avez terminé d’ajouter des emplacements de contenu à la conservation, cliquez sur **Suivant**.
  
10. Pour créer une conservation basée sur une requête avec des conditions, procédez comme suit. Sinon, cliquez simplement sur **Suivant**.

    - Dans la zone sous **Mots clés, tapez** une requête de recherche dans la zone afin que seul le contenu qui répond aux critères de recherche soit mis en attente. Vous pouvez spécifier des mots clés, des propriétés de message ou des propriétés de document, telles que des noms de fichiers. Vous pouvez également utiliser des requêtes plus complexes qui utilisent un opérateur booléen, tel que ET, OUou NON. Si vous laissez la zone de mot clé vide, tout le contenu situé dans les emplacements de contenu spécifiés sera mis en attente.

    - Cliquez sur  **Ajouter** des conditions pour ajouter une ou plusieurs conditions pour affiner la requête de recherche pour la conservation. Chaque condition ajoute une clause à la requête de recherche KQL qui est créée et exécutée lorsque vous créez la conservation. Par exemple, vous pouvez spécifier une plage de dates afin que les e-mails ou les documents de site créés dans la plage de dates soient mis en attente. Une condition est connectée à la requête de mot-clé (spécifiée dans la zone de mot-clé) sur le plan logique par l’opérateur AND. Cela signifie que les éléments doivent satisfaire à la fois à la requête de mot clé et à la condition à mettre en attente.

     Pour plus d’informations sur la création d’une requête de recherche et l’utilisation de conditions, consultez [requêtes de mots clés et conditions de recherche pour la recherche de contenu](/office365/SecurityCompliance/keyword-queries-and-search-conditions).

11. Après avoir configuré une conservation basée sur une requête, cliquez sur **Suivant**.

12. Passez en revue vos paramètres, puis cliquez sur **Créer cette conservation**.

> [!NOTE]
> Lorsque vous créez une conservation basée sur une requête, tout le contenu des emplacements sélectionnés est initialement mis en attente. Après l’exécution du travail du minuteur dans Exchange ou SharePoint, tout contenu qui ne correspond pas à la requête spécifiée est effacé de la conservation. Une fois que le nombre de caractères dans toutes les requêtes sur un emplacement unique dépasse 10 000 caractères, l’emplacement entier est mis en attente. 

> [!NOTE]
> Si l’adresse SMTP de l’utilisateur change après la mise en attente de la boîte aux lettres de l’utilisateur, la boîte aux lettres reste en attente. Pour utiliser la nouvelle adresse SMTP pour placer la conservation, créez une nouvelle conservation.

## <a name="place-a-hold-on-microsoft-teams-and-office-365-groups"></a>Mettre en attente Microsoft Teams et les groupes Office 365

Microsoft Teams repose sur des groupes Office 365. Par conséquent, leur mise en attente dans eDiscovery (Premium) est similaire.

- **Comment faire mapper un Groupes Microsoft 365 supplémentaire ou un site Microsoft Teams à un dépositaire ? Et qu’en est-il de placer une conservation non-custodiale sur Groupes Microsoft 365 et Microsoft Teams ?** Microsoft Teams repose sur Groupes Microsoft 365. Par conséquent, les mettre en attente dans un cas eDiscovery est similaire. Gardez à l’esprit les éléments suivants lorsque vous placez Groupes Microsoft 365 et Microsoft Teams en attente.

  - Pour mettre en attente le contenu situé dans Groupes Microsoft 365 et Microsoft Teams, vous devez spécifier la boîte aux lettres et le site SharePoint associés à un groupe ou une équipe.
  
  - Exécutez l’applet **de commande Get-UnifiedGroup** dans Exchange Online pour afficher les propriétés d’un groupe Microsoft 365 ou d’une équipe Microsoft. Il s’agit d’un bon moyen d’obtenir l’URL du site associé à un groupe Microsoft 365 ou à une équipe Microsoft. Par exemple, la commande suivante affiche les propriétés sélectionnées pour un groupe Microsoft 365 nommé Senior Leadership Team :

    ```console
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Pour exécuter l'applet de commande Get-UnifiedGroup, vous devez avoir le rôle de destinataires en affichage seul dans Exchange Online ou être membre d’un groupe de rôles affecté du rôle de destinataires en affichage seul.

  - Lorsque la boîte aux lettres d’un utilisateur est recherchée, aucun groupe Microsoft 365 ou équipe Microsoft dont l’utilisateur est membre ne sera recherché. De même, lorsque vous placez une conservation microsoft 365 Group ou Microsoft Team, seule la boîte aux lettres de groupe et le site de groupe sont mis en attente ; les boîtes aux lettres et les sites OneDrive Entreprise des membres du groupe ne sont pas mis en attente, sauf si vous les ajoutez explicitement en tant que consignateurs ou placez leurs sources de données en attente. Par conséquent, si vous devez mettre un groupe Microsoft 365 ou une équipe Microsoft en attente pour un consignateur spécifique, envisagez de mapper le site de groupe et la boîte aux lettres de groupe au consignateur (voir Managing Custodians in eDiscovery (Premium)). Si le groupe Microsoft 365 ou l’équipe Microsoft n’est pas attribuable à un seul consignataire, envisagez d’ajouter la source à une conservation non gardienne.
  - Pour obtenir la liste des membres d’un groupe Microsoft 365 ou d’une équipe Microsoft, vous pouvez afficher les propriétés de la page [**Groupes**](https://go.microsoft.com/fwlink/p/?linkid=2052855) **d’accueil** >  dans le Centre d'administration Microsoft 365. Vous pouvez également exécuter la commande suivante dans Exchange Online PowerShell :

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > Pour exécuter l'applet de commande **Get-UnifiedGroupLinks**, vous devez avoir le rôle de destinataires en affichage seul dans Exchange Online ou être membre d’un groupe de rôles affecté du rôle de destinataires en affichage seul.

  - Les conversations de canal qui font partie d’un canal Microsoft Teams sont stockées dans la boîte aux lettres associée à l’équipe. De même, les fichiers partagés par les membres d’une équipe dans un canal sont stockés sur le site SharePoint de l’équipe. Par conséquent, vous devez mettre la boîte aux lettres microsoft team et le site SharePoint en attente pour conserver les conversations et les fichiers dans un canal.
  
  - Vous pouvez également stocker les conversations qui font partie de la liste des conversations dans Microsoft Teams dans la boîte aux lettres des utilisateurs qui participent à la conversation.  Les fichiers qu’un utilisateur partage dans des conversations de conversation sont stockés dans le site OneDrive Entreprise de l’utilisateur qui partage le fichier. Par conséquent, vous devez mettre les boîtes aux lettres des utilisateurs individuels et les sites OneDrive Entreprise en attente pour conserver les conversations et les fichiers dans la liste des conversations.
  
  - Chaque équipe Microsoft ou canal d’équipe contient un Wiki pour la prise de notes et la collaboration. Le contenu wiki est automatiquement enregistré dans un fichier au format .mht. Ce fichier est stocké dans la bibliothèque de documents wiki Teams sur le site SharePoint de l’équipe. Vous pouvez mettre en attente le contenu du Wiki en mettant le site SharePoint de l’équipe en attente.

    > [!NOTE]
    > La possibilité de conserver le contenu Wiki d’une équipe Microsoft ou d’un canal d’équipe (lorsque vous mettez le site SharePoint de l’équipe en attente) a été publiée le 22 juin 2017. Si un site d’équipe est en attente, le contenu wiki sera conservé à compter de cette date. Toutefois, si un site d’équipe est en attente et que le contenu wiki a été supprimé avant le 22 juin 2017, le contenu wiki n’a pas été conservé.
