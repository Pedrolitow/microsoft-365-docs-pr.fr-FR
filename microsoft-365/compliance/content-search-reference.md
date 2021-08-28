---
title: Référence des fonctionnalités pour la recherche du contenu
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Cet article contient des informations de référence sur l’outil eDiscovery de recherche de contenu dans le Centre de conformité Microsoft 365 pour vous aider à en savoir plus sur la recherche de contenu.
ms.openlocfilehash: f6c720973f91ae9a202b232d821c33c7f487b76a
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58574447"
---
# <a name="feature-reference-for-content-search"></a>Référence des fonctionnalités pour la recherche du contenu

Cet article décrit les fonctionnalités de la recherche du contenu.

## <a name="content-search-limits"></a>Limites de la recherche de contenu

Pour une description des limites qui sont appliquées aux recherches de contenu, voir [Limites pour la recherche de contenu](limits-for-content-search.md).

## <a name="building-a-search-query"></a>Exécuter une requête de recherche

Pour plus d’informations sur la création d’une requête de recherche, l’utilisation d’opérateurs de recherche booléens et de conditions de recherche, ainsi que la recherche de types d’informations sensibles et de contenu partagés avec des utilisateurs externes à votre organisation, voir [Requêtes par mots clés et recherche conditions pour la recherche de contenu](keyword-queries-and-search-conditions.md).

Gardez les points suivants à l’esprit lorsque vous utilisez la liste de mots clés pour créer une requête de recherche.

- Vous devez cocher la case **Afficher la liste de mots clés**, puis taper chaque mot-clé dans une ligne distincte pour créer une requête de recherche dans laquelle les mots-clés (ou les phrases de mots-clés) de chaque ligne sont connectés par l’opérateur **ou**. Si vous collez une liste de mots clés dans la zone de mot clé ou appuyez sur la touche **entrée** après avoir tapé un mot clé, ils ne sont pas connectés par l’opérateur **ou**. Voici quelques exemples incorrects et corrects d’ajout d’une liste de mots clés.

    **Incorrect**

    ![La façon incorrecte de mettre en forme une liste de mots clés (en collant la liste dans la zone de mot clé).](../media/fb54e3df-232a-439a-b3d7-27a60ec76a4c.png)

    **Correct**

    ![La façon correcte de mettre en forme une liste de mots clés (en sélectionnant la case à cocher, puis en collant la liste)](../media/5d511a7b-c1f9-499c-bffe-e075bfc9adec.png)

- Vous pouvez également préparer une liste de mots clés ou d’expressions de mots clés dans un fichier Excel ou un fichier texte brut, puis copier et coller votre liste dans la liste de mots clés. Pour ce faire, vous devez activer la case à cocher **afficher la liste de mots clés**. Cliquez ensuite sur la première ligne de la liste de mots clés, puis collez votre liste. Chaque ligne du fichier Excel ou texte est copiée dans une ligne distincte de la liste des mots clés.

- Une fois que vous avez créé une requête à l’aide de la liste de mots clés, nous vous conseillons de vérifier la syntaxe de requête de recherche pour faire en sorte que la requête corresponde à ce que vous souhaitez. Dans la requête de recherche affichée sous **requête**, dans le volet Détails, les mots clés sont séparés par le texte **(c:s)**. Cela indique que les mots clés sont connectés à l’aide d’un opérateur logique similaire à une fonctionnalité à l’opérateur **ou**. De même, si votre requête de recherche inclut des conditions, les mots clés et les conditions sont séparés par le texte **(c:c)**. Cela indique que les mots clés sont connectés aux conditions à l’aide d’un opérateur logique similaire à une fonctionnalité à l’opérateur **ET**. Voici un exemple de requête de recherche (affichée dans le volet Détails) qui résulte de l’utilisation de la liste de mots clés et d’une condition.

    ![Exemple de requête créée lors de l’utilisation de la liste de mots clés et d’une condition.](../media/b463750c-57fa-4602-9fed-0d5a420db3ad.png)

- Lorsque vous effectuez une recherche de contenu, Microsoft 365 vérifie automatiquement la présence de caractères non pris en charge et d’opérateurs booléens qui ne sont pas en majuscules dans votre requête de recherche. En règle générale, les caractères non pris en charge sont masqués et entraînent une erreur ou renvoient des résultats inattendus. Pour plus d’informations sur les caractères non pris en charge qui ont été vérifiés, voir [vérifier la présence d’erreurs dans votre requête de recherche de contenu](check-your-content-search-query-for-errors.md).

- Si vous avez une requête de recherche qui contient des mots clés pour les caractères non anglais (tels que les caractères chinois), vous pouvez cliquer sur l’icône **Requête de langue-pays/région** ![Requête de langue-pays/région dans la recherche de contenu.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) et sélectionnez une valeur de code de culture pays/langue de votre recherche. La langue/région par défaut est neutre. Comment savoir si vous avez besoin de modifier le paramètre de langue d’une recherche de contenu ? Si vous êtes certain que les emplacements de contenu contiennent les caractères non anglais que vous recherchez, mais que la recherche ne renvoie aucun résultat, le paramètre de langue peut être à l’origine du problème.

## <a name="partially-indexed-items"></a>Éléments partiellement indexés

- Les éléments partiellement indexés dans les boîtes aux lettres sont inclus dans les résultats de recherche estimés. Les éléments partiellement indexés de SharePoint et OneDrive ne sont pas inclus dans les résultats de recherche estimés. Si vous souhaitez en savoir plus, consultez [Éléments partiellement indexés dans eDiscovery](partially-indexed-items-in-content-search.md).

## <a name="searching-onedrive-accounts"></a>Recherche de comptes OneDrive

- Pour recueillir la liste des URL des sites OneDrive au sein de votre organisation, voir [créer une liste de tous les emplacements OneDrive au sein de votre organisation](/onedrive/list-onedrive-urls). Ce script dans cet article crée un fichier texte qui contient une liste de tous les sites OneDrive. Pour exécuter ce script, vous devez installer et utiliser SharePoint Online Management Shell. N’oubliez pas d’ajouter l’URL du domaine MySite de votre organisation à chaque site OneDrive dans lequel vous souhaitez effectuer une recherche. Il s’agit du domaine où se trouve tout le contenu de votre OneDrive (par exemple,`https://contoso-my.sharepoint.com`). Voici un exemple d’URL pour le site d’un utilisateur OneDrive : `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft.com`.

    Dans le cas rare où le nom d’utilisateur principal (UPN) d’une personne est modifié, l’URL de son emplacement OneDrive est modifiée pour incorporer le nouveau nom d’utilisateur principal (UPN). Dans ce cas, vous devez modifier une recherche de contenu en ajoutant la nouvelle URL OneDrive de l’utilisateur et en supprimant l’ancienne. Pour plus d’informations, voir [Comment les modifications du nom d’utilisateur principal affectent l’URL OneDrive](/onedrive/upn-changes).

## <a name="searching-microsoft-teams-and-microsoft-365-groups"></a>Recherche dans Microsoft Teams et les Groupes Microsoft 365

Vous pouvez rechercher la boîte aux lettres associée à une équipe Microsoft ou à un groupe Microsoft 365. Étant donné que Microsoft Teams est basé sur les Groupes Microsoft 365, la recherche est similaire. Dans les deux cas, la recherche porte uniquement sur la boîte aux lettres de groupe ou d’équipe. Les boîtes aux lettres des membres du groupe ou de l’équipe ne sont pas recherchées. Pour effectuer une recherche, vous devez les ajouter spécifiquement à la recherche.

Gardez les points suivants à l’esprit lors de la recherche de contenu dans les Groupes Microsoft Teams et Microsoft 365.

- Pour rechercher du contenu se trouvant dans Teams et Groupes Microsoft 365, vous devez spécifier la boîte aux lettres et le site SharePoint qui sont associés à une équipe ou à un groupe.

- Le contenu provenant de canaux privés est stocké dans la boîte aux lettres de chaque utilisateur, et non dans celle de l’équipe. Pour rechercher du contenu dans des canaux privés, voir [Découverte automatique des canaux privés](/microsoftteams/ediscovery-investigation#ediscovery-of-private-channels).

- Lancez le **cmdlet Get-UnifiedGroup** dans Exchange Online pour afficher les propriétés d'une équipe ou d'un groupe Microsoft 365. C'est un bon moyen d'obtenir l'URL du site qui est associé à une équipe ou à un groupe. Par exemple, la commande suivante affiche les propriétés sélectionnées pour un groupe Microsoft 365 nommé Senior Leadership Team :

  ```text
  Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
  DisplayName            : Senior Leadership Team
  Alias                  : seniorleadershipteam
  PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
  SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
  ```

    > [!NOTE]
    > Pour exécuter l'applet de commande **Get-UnifiedGroup**, vous devez avoir le rôle de destinataires en affichage seul dans Exchange Online ou être membre d’un groupe de rôles affecté du rôle de destinataires en affichage seul.

- Lorsque vous effectuez une recherche dans la boîte aux lettres d’un utilisateur, aucun des Groupes Microsoft 365 ou équipe dont l’utilisateur est membre n’est inclus dans la recherche. De même, lorsque vous effectuez une recherche sur une équipe ou un groupe Microsoft 365, seules la boîte aux lettres et le site du groupe que vous spécifiez sont recherchés. Les boîtes aux lettres et les comptes OneDrive entreprises des membres du groupe ne sont pas recherchés, sauf si vous les ajoutez explicitement à la recherche.

- Pour obtenir la liste des membres d'une équipe ou d'un groupe Microsoft 365, vous pouvez consulter les propriétés sur la **page\> Groupes** d'accueil dans le centre d'administration de Microsoft 365. Vous pouvez également exécuter la commande suivante dans Exchange Online PowerShell :

  ```powershell
  Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
  ```

    > [!NOTE]
    > Pour exécuter l'applet de commande **Get-UnifiedGroupLinks**, vous devez avoir le rôle de destinataires en affichage seul dans Exchange Online ou être membre d’un groupe de rôles affecté du rôle de destinataires en affichage seul.

- Les conversations faisant partie d’un canal d’équipe sont stockées dans la boîte aux lettres associée à l’équipe. De même, les fichiers partagés par les membres d’une équipe dans un canal sont stockés sur le site SharePoint de l’équipe. Par conséquent, vous devez ajouter la boîte aux lettres d’équipe et le site SharePoint comme emplacement de contenu pour rechercher des conversations et des fichiers dans un canal.

- De même, les conversations faisant partie de la liste de conversations dans Teams sont stockées dans la boîte aux lettres Exchange Online des utilisateurs qui participent à la conversation. Les fichiers partagés par un utilisateur dans les conversations Chat sont stockés dans le compte OneDrive Entreprise de l’utilisateur qui partage le fichier. Par conséquent, vous devez ajouter les boîtes aux lettres d’utilisateur individuelles et les comptes OneDrive Entreprise comme emplacements de contenu pour rechercher des conversations et des fichiers dans la liste de conversations.

    > [!NOTE]
    > Dans un déploiement Exchange hybride, les utilisateurs disposant d’une boîte aux lettres locale peuvent participer aux conversations qui font partie de la liste de Conversations dans Teams. Dans ce cas, le contenu de ces conversations peut également faire l’objet d’une recherche, car il est enregistré dans une zone de stockage basée sur le Cloud (appelée *boîte aux lettres basée sur le Cloud pour les utilisateurs locaux*) pour les utilisateurs disposant d’une boîte aux lettres locale. Pour plus d'informations, voir [Recherche de données de conversation des équipes pour les utilisateurs sur site](search-cloud-based-mailboxes-for-on-premises-users.md).

- Toutes les équipes ou canaux d’équipe contiennent un site wiki pour la prise de notes et la collaboration. Le contenu wiki est automatiquement enregistré dans un fichier au format .mht. Ce fichier est stocké dans la bibliothèque de documents wiki Teams sur le site SharePoint de l’équipe. Vous pouvez utiliser l’outil recherche de contenu pour effectuer une recherche sur le site wiki en spécifiant le site SharePoint de l’équipe comme emplacement de contenu à rechercher.

    > [!NOTE]
    > La fonctionnalité de recherche d’une équipe ou d’un canal sur le site wiki (lorsque vous effectuez une recherche sur le site SharePoint de l’équipe) a été publiée le 22 juin 2017. Les pages wiki qui ont été enregistrées ou mises à jour à cette date ou après peuvent être recherchées. Les pages wiki enregistrées ou mises à jour avant cette date ne sont pas disponibles pour la recherche.

- Les informations de synthèse pour les réunions et les appels dans un canal Teams sont également stockées dans les boîtes aux lettres des utilisateurs qui composent la réunion ou l’appel. Cela signifie que vous pouvez utiliser la recherche de contenu pour rechercher ces enregistrements de synthèse. Ces informations de résumé sont les suivantes :

  - Date, heure de début, heure de fin et durée d’une réunion ou d’un appel

  - Date et heure quand chaque participant a joint ou quitté la réunion ou de l’appel

  - Appels envoyés à la messagerie vocale

  - Appels manqués ou sans réponse

  - Appels de transfert, représentés par deux appels distincts

  La possibilité d’effectuer une recherche dans les enregistrements de synthèse des réunions et des appels peut prendre jusqu’à 8 heures.

  Dans les résultats de la recherche, les résumés de la réunion sont identifiés en tant que **réunion** dans le **champ type** et les résumés d’appels sont identifiés en tant qu’**appel**. De plus, les conversations qui font partie d’une chaîne de Teams et de conversations 1xN sont identifiées en tant que **messages instantanés** dans le **champ type**.

  ![Les réunions, les appels et les conversations 1xN de Teams sont identifiés dans le champ Type.](../media/O365-ContentSearch-Teams-MessageKind.png)

   Pour plus d’informations, voir [Microsoft Teams lance l’eDiscovery pour les appels et les réunions](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-launches-ediscovery-for-calling-and-meetings/ba-p/210947).

- Le contenu des cartes généré par les applications des canaux Teams, des chats 1:1 et des chats 1xN est stocké dans les boîtes aux lettres et peut être recherché. Une *carte* est un conteneur de l'assurance-chômage pour de petits morceaux de contenu. Les cartes peuvent avoir de multiples propriétés et pièces jointes, et peuvent inclure des boutons qui peuvent déclencher des actions de la carte. Pour plus d'informations, voir [Cartes](/microsoftteams/platform/task-modules-and-cards/what-are-cards) 

  Comme pour le contenu des autres Teams, le lieu de stockage du contenu de la carte est basé sur l'endroit où la carte a été utilisée. Le contenu des cartes utilisées dans un canal Teams est stocké dans la boîte aux lettres du groupe Teams. Le contenu des cartes pour les chats 1:1 et 1xN est stocké dans les boîtes aux lettres des participants au conversation.

  Pour rechercher le contenu d'une carte, vous pouvez utiliser les`kind:microsoftteams` conditions`itemclass:IPM.SkypeTeams.Message` de recherche. Lors de l'examen des résultats de recherche, le contenu de la carte généré par les robots dans un canal Teams a la propriété **Sender/Author** email comme `<appname>@teams.microsoft.com` , où `appname`est le nom de l'application qui a généré le contenu de la carte. Si le contenu de la carte a été généré par un utilisateur, la valeur **d'Expéditeur/Autorisateur** permet d'identifier l'utilisateur.

  Lorsque vous consultez le contenu de la carte dans les résultats de la recherche de contenu, le contenu apparaît comme une pièce jointe au message. La pièce jointe est nommée `appname.html`, où`appname` se trouve le nom de l'application qui a généré le contenu de la carte. Les captures d'écran suivantes montrent comment le contenu des cartes (pour une application nommée Asana) apparaît dans les équipes et dans les résultats d'une recherche.

  **Contenu de la carte dans Teams**

  ![Contenu de la carte dans le message de la chaîne Teams.](../media/CardContentTeams.png)

  **Contenu de la carte dans les résultats de recherche**

  ![Même contenu de carte dans les résultats d'une recherche de contenu](../media/CardContentEdiscoverySearchResults.png)

  > [!NOTE]
  > Pour afficher les images du contenu de la carte dans les résultats de recherche à ce moment (comme les cases cochées dans la capture d'écran précédente), vous devez être connecté à Teams (danshttps://teams.microsoft.com) un onglet différent dans la même session de navigateur que celle que vous utilisez pour voir les résultats de recherche. Dans le cas contraire, des emplacements pour les images sont affichés.

- Vous pouvez utiliser la propriété **type de courrier** ou la condition de recherche **type de message** pour rechercher spécifiquement du contenu dans Teams.

  - Pour utiliser la propriété **Type** dans le cadre de la requête de recherche par mot clé, dans la zone **Mots clés** d'une requête de recherche, tapez`kind:microsoftteams`.

    ![Utilisez kind:microsoftteams dans la zone de mots clés.](../media/O365-ContentSearch-Teams-Keywords.png)

  - Pour utiliser une condition de recherche, ajoutez la condition **type de message** et utilisez la valeur`microsoftteams`.

    ![Utilisez la condition type de message avec la valeur microsoftteams.](../media/O365-ContentSearch-Teams-MessageKindCondition.png)

   Les conditions sont logiquement connectées à la requête de mot clé par l’opérateur **et**. Cela signifie qu’un élément doit correspondre à la requête de mot clé et à la condition de recherche à renvoyer dans les résultats de la recherche. Pour obtenir plus d’informations, reportez-vous à la rubrique «Guide des conditions d’utilisation» dans[Requêtes par mots-clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md#guidelines-for-using-conditions).

## <a name="searching-yammer-groups"></a>Recherche de groupes Yammer

Vous pouvez utiliser la propriété d’e-mail **ItemClass** ou la condition de recherche **Type** pour rechercher spécifiquement les éléments de conversation dans les groupes Yammer.

  - Pour utiliser la propriété **ItemClass** dans le cadre d'une requête de recherche par mot-clé, dans la zone **Mots-clés** d'une requête de recherche, vous pouvez saisir une (ou toutes) des paires property:value suivantes :

     - ItemClass:IPM.Yammer.message
     - ItemClass:IPM.Yammer.poll
     - ItemClass:IPM.Yammer.praise
     - ItemClass:IPM.Yammer.question

    Par exemple, vous pouvez utiliser la requête de recherche suivante pour renvoyer des messages Yammer et des éléments de compliment Yammer :

    ![Utiliser la propriété ItemClass pour rechercher des éléments Yammer.](../media/YammerContentSearch1.png)

  - Vous pouvez également utiliser la condition de **Type** e-mail et sélectionner les **messages Yammer** pour renvoyer les éléments Yammer. Par exemple, la requête de recherche suivante renvoie tous les éléments de conversation Yammer qui contiennent le mot clé « confidentiel ».

    ![Utiliser la carte de condition Type pour rechercher des éléments de conversation Yammer.](../media/YammerContentSearch2.png)

## <a name="searching-inactive-mailboxes"></a>Recherche des boîtes aux lettres inactives

Vous pouvez effectuer une recherche dans les boîtes aux lettres inactives dans une recherche de contenu. Pour obtenir une liste des boîtes aux lettres inactives de votre organisation, exécutez la commande `Get-Mailbox -InactiveMailboxOnly` dans Exchange Online PowerShell. Vous pouvez également accéder à **Gouvernance des informations** \> **Rétention** dans le Centre de sécurité & conformité, puis cliquer sur **Plus**![Ellipses de la barre de navigation.](../media/9723029d-e5cd-4740-b5b1-2806e4f28208.gif) \> **Boîtes aux lettres inactives**.

Voici quelques éléments à prendre en considération lors de la recherche de boîtes aux lettres inactives.

- Si une recherche de contenu existante inclut une boîte aux lettres utilisateur et que cette boîte aux lettres devient ensuite inactive, la recherche de contenu se poursuit dans la boîte aux lettres inactive lorsque vous relancez cette recherche.

- Un utilisateur peut parfois avoir une boîte aux lettres active et une boîte aux lettres inactive portant la même adresse SMTP. Dans ce cas, la recherche porte sur la boîte aux lettres que vous sélectionnez en tant qu’emplacement à des fins de recherche de contenu. En d’autres termes, si vous ajoutez la boîte aux lettres d’un utilisateur à une recherche, vous ne pouvez pas supposer que les boîtes aux lettres actives et inactives sont recherchées. Seules les boîtes aux lettres que vous ajoutez explicitement à la recherche font l’objet d’une recherche.

- Vous pouvez utiliser le centre de sécurité et de conformité PowerShell pour créer une recherche de contenu pour effectuer une recherche dans une boîte aux lettres inactive. Pour ce faire, vous devez préalablement ajouter un point (. ) à l’adresse de messagerie du propriétaire de boîte aux lettres inactive. Par exemple, la commande suivante crée une recherche de contenu qui recherche dans une boîte aux lettres inactive l’adresse de courrier pavelb@contoso.onmicrosoft.com:

   ```powershell
   New-ComplianceSearch -Name InactiveMailboxSearch -ExchangeLocation .pavelb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true
   ```

- Nous vous déconseillons vivement d’utiliser une boîte aux lettres active et une boîte aux lettres inactive portant la même adresse SMTP. Si vous devez réutiliser l’adresse SMTP attribuée à une boîte aux lettres inactive, nous vous recommandons de récupérer la boîte aux lettres inactive ou de restaurer le contenu d’une boîte aux lettres inactive dans une boîte aux lettres active (ou l’archive d’une boîte aux lettres active), puis de supprimer la boîte aux lettres inactive. Pour plus d'informations, consultez l'une des rubriques suivantes :

  - [Récupérer une boîte aux lettres inactive dans Office 365](recover-an-inactive-mailbox.md)

  - [Restaurer une boîte aux lettres inactive dans Office 365](restore-an-inactive-mailbox.md)

  - [Supprimer une boîte aux lettres inactive dans Office 365](delete-an-inactive-mailbox.md)

## <a name="searching-disconnected-or-de-licensed-mailboxes"></a>Recherche de boîtes aux lettres déconnectées ou sans licence

Si la licence Exchange Online (ou la licence Microsoft 365 entière) est supprimée d’un compte d’utilisateur ou dans Azure Active Directory, la boîte aux lettres de l’utilisateur devient une *boîte aux lettres déconnectée*. Cela signifie que la boîte aux lettres n’est plus associée au compte d’utilisateur. Voici ce qui se produit lorsque vous effectuez des recherches dans les boîtes aux lettres déconnectées :

- Si la licence est supprimée d’une boîte aux lettres, il n’est plus possible d’y effectuer des recherches.

- Si une recherche de contenu existante inclut une boîte aux lettres dont laquelle la licence est supprimée, aucun résultat de la boîte aux lettres déconnectée ne sera renvoyé si vous réexécutez la recherche de contenu.

- Si vous utilisez la cmdlet **New-ComplianceSearch** pour créer une recherche de contenu et spécifiez une boîte aux lettres déconnectée comme emplacement de contenu Exchange où effectuer la recherche, la recherche de contenu ne renverra aucun résultat de la boîte aux lettres déconnectée.

Si vous devez conserver les données d’une boîte aux lettres déconnectée pour y effectuer des recherches, vous devez placer la boîte aux lettres en conservation avant de supprimer la licence. Cela conserve les données et permet de continuer à effectuer des recherches dans la boîte aux lettres déconnectée jusqu’à ce que la conservation soit supprimée. Pour plus d’informations sur les conservations, voir [Comment identifier le type de conservation placé sur une boîte aux lettres Exchange Online](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="searching-for-content-in-a-sharepoint-multi-geo-environment"></a>Recherche de contenu dans un environnement SharePoint multigéographique

Si une personne dotée du rôle Gestionnaire eDiscovery doit rechercher du contenu dans SharePoint et OneDrive à travers différentes régions dans un [environnement SharePoint multigéographique](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md), vous devez effectuer les opérations suivantes :

1. Créez un compte d’utilisateur distinct pour chaque position géographique de satellite où le Gestionnaire eDiscovery doit effectuer une recherche. Pour rechercher du contenu dans les sites dans cette position géographique, le Gestionnaire eDiscovery doit se connecter au compte que vous avez créé pour cette position, puis exécuter une recherche de contenu.

2. Créez un filtre d’autorisation de recherche pour chaque position géographique de satellite (et le compte d’utilisateur correspondant) où le Gestionnaire eDiscovery doit effectuer une recherche. Chacun de ces filtres d’autorisations de recherche limite l’étendue de la recherche de contenu à une position géographique spécifique lorsque le Gestionnaire eDiscovery est connecté au compte d’utilisateur associé à cette position.

> [!TIP]
> Vous n’êtes pas obligé d’utiliser cette stratégie lorsque vous utilisez l'outil de recherche dans [Advanced eDiscovery](overview-ediscovery-20.md). En effet, lorsque vous effectuez des recherches dans les sites SharePoint et les comptes OneDrive dans Advanced eDiscovery, elles s’effectuent sur tous les centres de données. Vous devez uniquement utiliser cette stratégie de comptes d’utilisateurs et de filtres d’autorisations propres aux zones de recherche lorsque vous utilisez l’outil de recherche de contenu et que vous exécutez des recherches associées à des [cas eDiscovery](./get-started-core-ediscovery.md).

Prenons l’exemple d’un gestionnaire eDiscovery devant rechercher du contenu SharePoint et OneDrive dans des emplacements satellites positionnés en Amérique du Nord, en Europe et en Asie Pacifique. La première étape consiste à créer trois comptes d’utilisateurs : un pour chaque emplacement. L’étape suivante consiste à créer trois filtres d’autorisations de recherche, un pour chaque emplacement *et* compte d’utilisateur correspondant. Voici quelques exemples des trois filtres d’autorisations de recherche pour ce scénario. Dans chacun de ces exemples, le paramètre **Région** spécifie la position du centre de données SharePoint pour cette zone géographique et le paramètre **Utilisateurs** spécifie le compte d’utilisateur correspondant.

**Amérique du Nord**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-NAM" -Users ediscovery-nam@contoso.com -Region NAM -Action ALL
```

**Europe**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-EUR" -Users ediscovery-eur@contoso.com -Region EUR -Action ALL
```

**Asie-Pacifique**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-APC" -Users ediscovery-apc@contoso.com -Region APC -Action ALL
```

Lorsque vous utilisez des filtres d’autorisation de recherche pour rechercher du contenu dans des environnements multigéographiques, n’oubliez pas les points suivants :

- Le paramètre **Région** dirige les recherches vers la position de satellite spécifiée. La recherche ne retourne aucun résultat lorsqu’un Gestionnaire eDiscovery recherche uniquement des sites SharePoint et OneDrive en dehors de la position spécifiée dans le filtre des autorisations de recherche.

- Le paramètre **Région** ne contrôle pas les recherches dans les boîtes aux lettres Exchange. Lorsque vous effectuez des recherches dans des boîtes aux lettres, elles s’appliquent à tous les centres de données.

Si vous souhaitez en savoir plus sur l’utilisation des filtres d’autorisation de recherche dans un environnement multigéographique, veuillez consulter la section « Recherche et exportation de contenu dans des environnements multigéographiques » de l’article [Configurer les limites de conformité pour les enquêtes eDiscovery](set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).
