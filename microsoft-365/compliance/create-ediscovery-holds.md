---
title: Créer des suspensions eDiscovery dans un cas de découverte électronique principale
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Vous pouvez créer une conservation associée à un cas de découverte électronique de base pour conserver le contenu qui peut être pertinent pour une enquête.
ms.openlocfilehash: 8993a3e88ab7513713086499a316c92fdb7509cb
ms.sourcegitcommit: ff1af42b036bfdf75729db8c78f10cf4642616ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "44477194"
---
# <a name="create-an-ediscovery-hold"></a>Créer une suspension de cas eDiscovery

Vous pouvez utiliser un cas de découverte électronique de base pour créer des suspensions afin de conserver le contenu qui peut être pertinent pour le cas. Vous pouvez placer une suspension sur les boîtes aux lettres Exchange et les comptes OneDrive entreprise des personnes que vous étudiez dans le cas. Vous pouvez également placer une conservation sur les boîtes aux lettres et les sites associés à Microsoft Teams, aux groupes Office 365 et aux groupes Yammer. Lorsque vous placez des emplacements de contenu en conservation, le contenu est conservé jusqu’à ce que vous supprimiez le blocage de l’emplacement du contenu ou jusqu’à ce que vous supprimiez la conservation.

Une fois que vous avez créé une conservation eDiscovery, la conservation peut prendre jusqu’à 24 heures. 

Lorsque vous créez une suspension, vous disposez des options suivantes pour définir l’étendue du contenu qui est conservé dans les emplacements de contenu spécifiés :
  
- Vous créez un blocage infini où tout le contenu est placé en conservation. Vous pouvez également créer une conservation basée sur une requête où seul le contenu qui correspond à une requête de recherche est mis en attente.

- Vous pouvez spécifier une plage de dates pour conserver uniquement le contenu qui a été envoyé, reçu ou créé au sein de cette plage de dates. Vous pouvez également conserver tout le contenu, quel que soit son moment d’envoi, de réception ou de création.

> [!NOTE]
> Vous pouvez avoir un maximum de 10 000 eDiscovery dans tous les cas eDiscovery principaux de votre organisation.
  
## <a name="how-to-create-an-ediscovery-hold"></a>Procédure de création d’une conservation eDiscovery

Pour créer une conservation de découverte électronique qui est associée à un cas de découverte électronique principale, procédez comme suit :
  
1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) et connectez-vous à l’aide des informations d’identification du compte d’utilisateur auquel ont été attribuées les autorisations eDiscovery appropriées.

2. Dans le volet de navigation de gauche du centre de conformité Microsoft 365, cliquez sur **Afficher tout**, puis sur **découverte électronique > Core**.

3. Sur la page de **découverte électronique principale** , sélectionnez le cas dans lequel vous souhaitez créer le blocage, puis cliquez sur **ouvrir le cas**.

4. Sur la page d' **Accueil** de l’incident, cliquez sur l’onglet **suspensions** .
  
5. Sur la page **suspensions** , cliquez sur **créer**.

6. Dans la page **nom de votre Assistant conserver** , donnez un nom et ajoutez une description facultative, puis cliquez sur **suivant**. Le nom de la conservation doit être unique dans toute votre organisation.

7. Sur la page **emplacements de contenu** , sélectionnez les emplacements de contenu que vous souhaitez mettre en attente. Vous pouvez placer les boîtes aux lettres, les sites et les dossiers publics en conservation.

    ![Choisissez les emplacements de contenu à mettre sous conservation](../media/a59e4265-9151-4dbf-913f-6a4ab8db06b4.png)
  
   a. **Emplacements de boîte aux lettres** : cliquez sur **choisir les utilisateurs, les groupes ou les équipes** , puis cliquez à nouveau sur **choisir les utilisateurs, les groupes ou les équipes** pour spécifier les boîtes aux lettres à mettre en attente. Utilisez la zone de recherche pour rechercher des boîtes aux lettres utilisateur et des groupes de distribution (pour mettre en attente les boîtes aux lettres des membres du groupe) à mettre en attente. Vous pouvez également placer une suspension sur la boîte aux lettres associée pour une équipe Microsoft, un groupe Office 365 ou un groupe Yammer. Activez la case à cocher utilisateur, groupe, équipe, cliquez sur **choisir**, puis sur **Terminer**.

   b. **Emplacements de site** : cliquez sur **choisir des sites** , puis cliquez à nouveau sur **choisir les sites** pour spécifier les comptes SharePoint et OneDrive à mettre en attente. Saisissez l’URL de chaque site à placer en conservation. Vous pouvez également ajouter l’URL du site SharePoint pour une équipe Microsoft, un groupe Office 365 ou un groupe Yammer. Cliquez sur **choisir**, puis sur **Terminer**.
  
   c. **Dossiers publics Exchange.** Déplacez le contrôle bascule bascule ![ ](../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png) vers la position **tout** pour mettre en attente tous les dossiers publics de votre organisation Exchange Online. Vous ne pouvez pas choisir des dossiers publics spécifiques à mettre en attente. Laissez le commutateur Toggle défini sur **None** si vous ne souhaitez pas mettre de conservation sur les dossiers publics.

8. Lorsque vous avez terminé d’ajouter des emplacements de contenu au blocage, cliquez sur **suivant**.

9. Pour créer une conservation basée sur une requête avec des conditions, procédez comme suit. Dans le cas contraire, pour conserver tout le contenu des emplacements de contenu spécifiés, cliquez sur **suivant** .

    ![Créer une conservation basée sur une requête avec des conditions](../media/d587b58e-d05c-4ac0-b0fe-09019e4f1063.png)
  
    a. Dans la zone sous **Mots clés**, tapez une requête de recherche afin que seul le contenu correspondant aux critères de recherche soit préservé. Vous pouvez spécifier des mots clés, des propriétés de message électronique ou des propriétés de document, telles que des noms de fichiers. Vous pouvez également utiliser des requêtes plus complexes qui utilisent un opérateur booléen, comme **and**, **or**ou **not**.

    b. Cliquez sur **Ajouter des conditions** pour ajouter une ou plusieurs conditions afin de limiter la requête de recherche pour la suspension. Chaque condition ajoute une clause à la requête de recherche KQL créée et exécutée lors de la création de la suspension. Par exemple, vous pouvez spécifier une plage de dates pour que les documents de courrier ou de site créés dans la plage de dates soient suspendus. Une condition est logiquement liée à la requête par mot clé (spécifiée dans la zone **Mots clés** ) par l’opérateur **et** . Cela signifie que les éléments doivent répondre à la fois à la requête de mot clé et à la condition à conserver.

    Pour plus d’informations sur la création d’une requête de recherche et l’utilisation de conditions, consultez la rubrique [requêtes de mots clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md).

10. Après avoir configuré une conservation basée sur une requête, cliquez sur **suivant**.

11. Vérifiez vos paramètres (et modifiez-les si nécessaire), puis cliquez sur **créer cette suspension**.

## <a name="ediscovery-hold-statistics"></a>statistiques de conservation eDiscovery

Une fois que vous avez créé une conservation de découverte électronique, les informations relatives à la nouvelle conservation s’affichent sur la page de menu volant de la suspension sélectionnée. Ces informations incluent le nombre de boîtes aux lettres et de sites en conservation, ainsi que des statistiques sur le contenu qui a été placé en conservation, telles que le nombre total et la taille des éléments mis en attente et la dernière fois que les statistiques de conservation ont été calculées. Ces statistiques de suspension vous aident à identifier la quantité de contenu liée au cas en cours de conservation.
  
![Statistiques de conservation](../media/575cfe0a-9210-4ae4-8df8-65665d66712e.png)
  
Gardez les points suivants à l’esprit concernant les statistiques de conservation eDiscovery :
  
- Le nombre total d’éléments en attente indique le nombre d’éléments de toutes les sources de contenu qui sont placées en conservation. Si vous avez créé une conservation basée sur une requête, cette statistique indique le nombre d’éléments qui correspondent à la requête.

- Le nombre d’éléments en attente inclut également les éléments non indexés trouvés dans les emplacements de contenu. Si vous créez une conservation basée sur une requête, tous les éléments non indexés des emplacements de contenu sont placés en conservation. Cela inclut les éléments non indexés qui ne correspondent pas aux critères de recherche d’une conservation basée sur une requête et les éléments non indexés qui peuvent se situer en dehors d’une condition de plage de dates. Cette opération est différente de ce qui se passe lorsque vous exécutez une recherche, dans laquelle les éléments non indexés qui ne correspondent pas à la requête de recherche ou qui sont exclus par une condition de plage de dates ne sont pas inclus dans les résultats de la recherche. Pour plus d’informations sur les éléments non indexés, voir [éléments indexés partiellement](partially-indexed-items-in-content-search.md).

- Vous pouvez obtenir les dernières statistiques de conservation en cliquant sur **mettre à jour les statistiques** pour réexécuter une estimation de recherche qui calcule le nombre actuel d’éléments suspendus.

- Il est normal que le nombre d’éléments bloqués augmente au fil du temps, car les utilisateurs dont la boîte aux lettres ou le site est en attente envoient généralement de nouveaux messages électroniques et créent des documents dans SharePoint et OneDrive.

- Si une boîte aux lettres Exchange, un site SharePoint ou un compte OneDrive est déplacé vers une autre région dans un environnement multi-géo, les statistiques de ce site ne sont pas incluses dans les statistiques de conservation. Toutefois, le contenu de ces emplacements reste conservé. En outre, si une boîte aux lettres ou un site est déplacé vers une autre région, l’adresse SMTP ou l’URL affichée dans la conservation n’est pas automatiquement mise à jour. Vous devrez modifier la conservation et mettre à jour l’URL ou l’adresse SMTP de manière à ce que les emplacements de contenu soient à nouveau inclus dans les statistiques de conservation.

## <a name="search-locations-on-ediscovery-hold"></a>Emplacements de recherche pour le blocage eDiscovery

Lorsque vous [recherchez du contenu](search-for-content-in-core-ediscovery.md) dans un cas de découverte électronique de base, vous pouvez configurer rapidement la recherche afin de rechercher uniquement les emplacements de contenu qui ont été placés en conservation associés au cas.

![Emplacements, en attente](../media/d56398aa-0b20-4500-8e26-494eab92a99f.png)

Sélectionnez l’option **emplacements en attente** pour rechercher tous les emplacements de contenu qui ont été placés en conservation. Si le cas contient plusieurs conservations eDiscovery, les emplacements de contenu de toutes les suspensions sont recherchés lorsque vous sélectionnez cette option. En outre, si un emplacement de contenu a été placé sur une conservation basée sur une requête, seuls les éléments qui correspondent à la requête de suspension seront recherchés lors de l’exécution de la recherche. En d’autres termes, seul le contenu qui correspond aux critères de conservation et aux critères de recherche est renvoyé avec les résultats de la recherche. Par exemple, si un utilisateur a été placé sur une conservation de casse basée sur une requête qui conserve les éléments qui ont été envoyés ou créés avant une date spécifique, seuls ces éléments seraient recherchés. Pour ce faire, vous connectez la requête de suspension de la demande de devis et la requête de recherche par un opérateur **and** .

Voici quelques autres éléments à garder à l’esprit lors de la recherche d’emplacements sur une conservation eDiscovery :

- Si un emplacement de contenu fait partie de plusieurs suspensions dans le même cas, les requêtes de conservation sont combinées par des opérateurs **or** lorsque vous effectuez une recherche dans cet emplacement de contenu à l’aide de l’option tout le contenu du cas. De même, si un emplacement de contenu fait partie de deux conservations différentes, où l’une est basée sur une requête et l’autre sur un blocage infini (où tout le contenu est placé en conservation), tout le contenu est effectué par la recherche en raison d’une suspension infinie.

- Si une recherche est configurée pour rechercher des emplacements de recherche, puis modifier une conservation de découverte électronique dans le cas (en ajoutant ou en supprimant un emplacement ou en modifiant une requête de suspension), la configuration de la recherche est mise à jour avec ces modifications. Toutefois, vous devez réexécuter la recherche après la modification de la conservation pour mettre à jour les résultats de la recherche.

- Si plusieurs conservations eDiscovery sont placées à un seul emplacement dans un cas de découverte électronique et que vous choisissez de rechercher des emplacements en conservation, le nombre maximal de mots clés pour cette requête de recherche est de 500. Cela est dû au fait que la recherche combine toutes les conservations basées sur une requête à l’aide de l’opérateur **or** . S’il y a plus de 500 mots clés dans les requêtes de suspension combinées et la requête de recherche, tout le contenu de la boîte aux lettres est recherché, et pas seulement celui qui correspond à la casse basée sur une requête.
    
- Si une conservation de découverte électronique a l’état **activer**, vous pouvez toujours effectuer des recherches dans les emplacements pendant que la conservation est activée.

## <a name="preserve-content-in-microsoft-teams"></a>Conserver du contenu dans Microsoft teams

Les conversations qui font partie d’un canal Microsoft teams sont stockées dans la boîte aux lettres associée à l’équipe Microsoft. De même, les fichiers partagés par les membres d’une équipe dans un canal sont stockés sur le site SharePoint de l’équipe. Par conséquent, vous devez placer la boîte aux lettres d’équipe et le site SharePoint dans la conservation eDiscovery pour conserver les conversations et les fichiers dans un canal.

En guise d’alternative, les conversations qui font partie de la liste des conversations dans Teams (appelée *1:1 conversations* ou *1 : N conversations de groupe*) sont stockées dans les boîtes aux lettres des utilisateurs qui participent à la conversation. Les fichiers que les utilisateurs partagent dans les conversations de conversation sont stockés dans le compte OneDrive de l’utilisateur qui partage le fichier. Par conséquent, vous devez ajouter les boîtes aux lettres d’utilisateur et les comptes OneDrive à une conservation eDiscovery pour conserver les conversations et les fichiers dans la liste des conversations. Il est recommandé de placer une conservation sur les boîtes aux lettres des membres d’une équipe Microsoft en plus de placer la boîte aux lettres d’équipe et la conservation du site.

À partir du 2020 février, nous avons activé la fonctionnalité de conservation du contenu dans les canaux privés. Étant donné que les conversations de canal privé sont stockées dans les boîtes aux lettres des participants à la conversation, le fait de placer une boîte aux lettres utilisateur sur une conservation eDiscovery préserve les conversations de canal privé. De plus, si une boîte aux lettres utilisateur a été placée dans une conservation de découverte électronique antérieure au 2020 février, la suspension s’applique automatiquement aux messages de canal privé stockés dans cette boîte aux lettres. La conservation des fichiers partagés dans les canaux privés est également prise en charge.

Pour plus d’informations sur la conservation du contenu de teams, consultez [la rubrique placer un utilisateur ou une équipe Microsoft teams en conservation légale](https://docs.microsoft.com/MicrosoftTeams/legal-hold).
    
> [!IMPORTANT]
> Dans une organisation en nuage, les utilisateurs qui participent à des conversations faisant partie de la liste des conversations dans teams doivent disposer d’une boîte aux lettres Exchange Online afin de conserver les conversations de conversation lorsque la boîte aux lettres est placée sur une conservation eDiscovery. Cela est dû au fait que les conversations faisant partie de la liste des conversations sont stockées dans les boîtes aux lettres en nuage des participants à la conversation. Si un participant à une conversation ne dispose pas d’une boîte aux lettres Exchange Online, vous ne pourrez pas conserver ces conversations de conversation. Par exemple, dans un déploiement hybride Exchange, les utilisateurs disposant d’une boîte aux lettres locale peuvent être autorisés à participer à des conversations qui font partie de la liste des conversations dans Teams. Toutefois, dans ce cas, le contenu de ces conversations ne peut pas être préservé car ces utilisateurs ne disposent pas de boîtes aux lettres en nuage pouvant être placées en conservation.
  
Chaque canal d’équipe ou d’équipe contient également un wiki pour la prise de notes et la collaboration. Le contenu wiki est automatiquement enregistré dans un fichier au format .mht. Ce fichier est stocké dans la bibliothèque de documents wiki Teams sur le site SharePoint de l’équipe. Vous pouvez conserver le contenu wiki en ajoutant le site SharePoint de l’équipe à une conservation eDiscovery.
    
> [!NOTE]
> La possibilité de conserver le contenu wiki d’une équipe ou d’un canal d’équipe (lorsque vous placez le blocage du site SharePoint de l’équipe) a été publiée le 22 juin 2017. Si un site d’équipe est en conservation, le contenu wiki est conservé à partir de cette date. Toutefois, si un site d’équipe est en conservation et que le contenu wiki a été supprimé avant le 22 juin 2017, le contenu wiki n’a pas été préservé.

### <a name="office-365-groups"></a>Groupes Office 365

Teams est basé sur les groupes Office 365. Par conséquent, le placement de groupes Office 365 sur une conservation eDiscovery est similaire à la mise en attente de contenu de teams.

Gardez les points suivants à l’esprit lorsque vous placez les groupes teams et Office 365 dans une conservation eDiscovery :

- Comme expliqué précédemment, pour placer le contenu situé dans des groupes teams et Office 365 en conservation, vous devez spécifier la boîte aux lettres et le site SharePoint associés à un groupe ou une équipe.

- Exécutez la cmdlet **Get-UnifiedGroup** dans [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) pour afficher les propriétés des groupes teams et Office 365. Il s’agit d’un moyen efficace pour obtenir l’URL du site associé à un groupe Team ou Office 365. Par exemple, la commande suivante affiche les propriétés sélectionnées d’un groupe Office365 nommé Senior Leadership Team :

    ```text
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl

    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Pour exécuter l'applet de commande **Get-UnifiedGroup**, vous devez avoir le rôle de destinataires en affichage seul dans Exchange Online ou être membre d’un groupe de rôles affecté du rôle de destinataires en affichage seul. 
  
- Lors de la recherche dans la boîte aux lettres d’un utilisateur, les équipes ou le groupe Office 365 dont l’utilisateur est membre ne feront pas l’objet d’une recherche. De même, lorsque vous placez une équipe ou un groupe Office 365 sur une conservation eDiscovery, seule la boîte aux lettres de groupe et le site de groupe sont placés en conservation. Les boîtes aux lettres et les sites OneDrive entreprise des membres du groupe ne sont pas mis en attente, sauf si vous les ajoutez explicitement au blocage eDiscovery. Par conséquent, si vous devez placer une équipe ou un groupe Office 365 en conservation pour une raison juridique, envisagez d’ajouter les boîtes aux lettres et les comptes OneDrive des membres de l’équipe ou du groupe sur le même blocage.

- Pour obtenir la liste des membres d’une équipe ou d’un groupe Office 365, vous pouvez afficher les propriétés dans la page **groupes** du centre d’administration Microsoft 365. Vous pouvez également exécuter la commande suivante dans Exchange Online PowerShell : 
    
    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > Pour exécuter l'applet de commande **Get-UnifiedGroupLinks**, vous devez avoir le rôle de destinataires en affichage seul dans Exchange Online ou être membre d’un groupe de rôles affecté du rôle de destinataires en affichage seul.

## <a name="onedrive-accounts"></a>Les comptes OneDrive

Pour collecter une liste des URL pour les sites OneDrive entreprise de votre organisation afin de pouvoir les ajouter à une suspension ou une recherche associée à un cas eDiscovery, consultez la rubrique [créer une liste de tous les emplacements OneDrive de votre organisation](https://docs.microsoft.com/onedrive/list-onedrive-urls). Le script de cet article crée un fichier texte qui contient une liste de tous les sites OneDrive de votre organisation. Pour exécuter ce script, vous devez installer et utiliser SharePoint Online Management Shell. N’oubliez pas d’ajouter l’URL du domaine MySite de votre organisation à chaque site OneDrive dans lequel vous souhaitez effectuer une recherche. Il s’agit du domaine où se trouve tout le contenu de votre OneDrive (par exemple,`https://contoso-my.sharepoint.com`). Voici un exemple d’URL pour le site d’un utilisateur OneDrive : `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft.com`.

> [!IMPORTANT]
> L’URL du compte OneDrive d’un utilisateur inclut son nom d’utilisateur principal (UPN) (par exemple, `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com` ). Dans les rares cas où le nom UPN d’une personne est modifié, son URL OneDrive est également modifiée pour intégrer le nouvel UPN. Si le compte OneDrive d’un utilisateur fait partie d’une conservation eDiscovery, l’ancienne et son UPN sont modifiés, vous devez mettre à jour la conservation et vous devrez mettre à jour la conservation et ajouter la nouvelle URL OneDrive de l’utilisateur et supprimer l’ancienne. Pour plus d’informations, voir [Comment les modifications du nom d’utilisateur principal affectent l’URL OneDrive](https://docs.microsoft.com/onedrive/upn-changes).

## <a name="removing-content-locations-from-an-ediscovery-hold"></a>Suppression des emplacements de contenu d’une conservation eDiscovery

Une fois qu’une boîte aux lettres, un site SharePoint ou un compte OneDrive est supprimé d’une conservation de découverte électronique, une attente de *retard* est appliquée. Cela signifie que la suppression effective de la conservation est retardée de 30 jours afin d’empêcher la suppression définitive des données d’un emplacement de contenu. Les administrateurs peuvent ainsi Rechercher ou récupérer du contenu qui sera purgé après la suppression d’une conservation de découverte électronique. Les détails du fonctionnement de la conservation du retard pour les boîtes aux lettres et les sites sont différents.

- **Boîtes aux lettres :** Un retard de conservation est placé sur une boîte aux lettres la prochaine fois que l’Assistant dossier géré traite la boîte aux lettres et détecte qu’une conservation de découverte électronique a été supprimée. Plus précisément, un délai d’attente est appliqué à une boîte aux lettres lorsque l’Assistant dossier géré définit l’une des propriétés de boîte aux lettres suivantes sur **true**: 

   - **DelayHoldApplied :** Cette propriété s’applique au contenu lié au courrier électronique (généré par des personnes utilisant Outlook et Outlook sur le Web) stocké dans la boîte aux lettres d’un utilisateur.

   - **DelayReleaseHoldApplied :** Cette propriété s’applique au contenu basé sur le Cloud (généré par des applications autres qu’Outlook telles que Microsoft Teams, Microsoft Forms et Microsoft Yammer) stocké dans la boîte aux lettres d’un utilisateur. Les données Cloud générées par une application Microsoft sont généralement stockées dans un dossier masqué de la boîte aux lettres d’un utilisateur.

   Lorsqu’une boîte aux lettres est placée en attente de retard (lorsque l’une des propriétés précédentes est définie sur **true**), la boîte aux lettres est toujours considérée comme suspendue pendant une durée de conservation illimitée, comme si la boîte aux lettres était en conservation pour litige. Au bout de 30 jours, le délai d’attente expire et Microsoft 365 tente automatiquement de supprimer le blocage de délai (en définissant la propriété DelayHoldApplied ou DelayReleaseHoldApplied sur **false**) de sorte que la conservation soit supprimée. Une fois que l’une de ces propriétés est définie sur **false**, les éléments correspondants marqués pour suppression sont purgés lors du prochain traitement de la boîte aux lettres par l’Assistant dossier géré.

   Pour des informations supplémentaires, consultez [Gestion des boîtes aux lettres avec période de grâce](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

- **Sites SharePoint et OneDrive :** Tout contenu SharePoint ou OneDrive conservé dans la bibliothèque de conservation n’est pas supprimé pendant la période de retard de 30 jours après la suppression d’un site d’une conservation eDiscovery. Ceci est semblable à ce qui se produit lorsqu’un site est publié à partir d’une stratégie de rétention. En outre, vous ne pouvez pas supprimer manuellement ce contenu dans la bibliothèque de conservation pendant la période de retard de 30 jours. 

   Pour plus d’informations, consultez [la rubrique libération d’une stratégie de rétention](retention-policies.md#releasing-a-retention-policy).

Une suspension de délai est également appliquée aux emplacements de contenu lorsque vous fermez un cas de découverte électronique de base, car les conservations sont désactivées lors de la fermeture du cas. Pour plus d’informations sur la fermeture d’un cas, voir [Close, Reopen et Delete a Core eDiscovery case](close-reopen-delete-core-ediscovery-cases.md).

## <a name="ediscovery-hold-limits"></a>limites de conservation pour la découverte électronique

Le tableau suivant répertorie les limites pour les cas de découverte électronique et les conservations de casse.
    
  |**Description de la limite**|**Limite**|
  |:-----|:-----|
  |Nombre maximal de cas pour une organisation  <br/> |Sans limite  <br/> |
  |Nombre maximal de conservations eDiscovery pour une organisation  <br/> |10 000  <br/> |
  |Nombre maximal de boîtes aux lettres dans une seule conservation eDiscovery  <br/> |1 000  <br/> |
  |Nombre maximal de sites SharePoint et OneDrive entreprise dans une conservation eDiscovery unique  <br/> |100  <br/> |
  |Nombre maximal de cas affichés sur la page d’accueil eDiscovery et nombre maximal d’éléments affichés dans les onglets conservations, recherches et exporter dans un cas. <sup>0,1</sup> |1 000|
  |||

   > [!NOTE]
   > <sup>1</sup> pour afficher une liste de plus de 1 000 cas, de suspensions, de recherches ou d’exportations, vous pouvez utiliser la cmdlet Office 365 Security & Compliance PowerShell correspondante :<br/> [Get-ComplianceCase](https://docs.microsoft.com/powershell/module/exchange/get-compliancecase) <br/> [Get-CaseHoldPolicy](https://docs.microsoft.com/powershell/module/exchange/get-caseholdpolicy)<br/> [Get-ComplianceSearch](https://docs.microsoft.com/powershell/module/exchange/get-compliancesearch)<br/> [Get-ComplianceSearchAction](https://docs.microsoft.com/powershell/module/exchange/get-compliancesearchaction)
