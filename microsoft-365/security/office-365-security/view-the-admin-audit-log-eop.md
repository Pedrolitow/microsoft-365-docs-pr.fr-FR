---
title: Afficher le journal d’audit de l’administrateur dans EOP autonome
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
ms.assetid: 003d7a74-3e16-4453-ae0c-9dbae51f66d1
description: Les administrateurs peuvent découvrir comment afficher et effectuer des recherches dans le journal d’audit de l’administrateur dans Exchange Online Protection (EOP) autonome.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ab6bf0a2739a88a075b636b990539b24006f3e63
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50286476"
---
# <a name="view-the-admin-audit-log-in-standalone-eop"></a>Afficher le journal d’audit de l’administrateur dans EOP autonome

**S’applique à**
- [Exchange Online Protection autonome](exchange-online-protection-overview.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, vous pouvez utiliser le Centre d’administration Exchange (CAE) ou EOP PowerShell autonome pour rechercher et afficher des entrées dans le journal d’audit de l’administrateur.

Le journal d’audit de l’administrateur enregistre des actions spécifiques, basées sur des cmdlets EOP PowerShell autonomes, réalisées par les administrateurs et les utilisateurs qui se sont vus attribuer des privilèges d’administration. Les entrées du journal d’audit de l’administrateur vous fournissent des informations sur la cmdlet qui a été exécuté, les paramètres utilisés, l’utilisateur qui a exécuté la cmdlet et les objets affectés.

> [!NOTE]
>
> - La journalisation d’audit de l’administrateur est activée par défaut et vous ne pouvez pas la désactiver.
>
> - Le journal d’audit de l’administrateur n’enregistre pas les actions basées sur les cmdlets qui commencent par les verbes **Obtenir,** Rechercher **ou** **Tester**.
>
> - Les entrées du journal d'audit sont conservées pendant 90 jours. Lorsqu’une entrée est plus ancienne que 90 jours, elle est supprimée

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Centre d’administration Exchange, consultez le [Centre d’administration Exchange dans EOP autonome.](exchange-admin-center-in-exchange-online-protection-eop.md)

- Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous être attribuées dans Exchange Online Protection avant de pouvoir suivre les procédures de cet article. Plus précisément, vous avez besoin du rôle Journaux  d’audit ou Journaux d’audit en affichage seul, qui sont affectés par défaut aux groupes de **rôles** Gestion de l’organisation, Gestion de la conformité et Administrateur de la sécurité.   Pour plus d’informations, voir Autorisations dans [EOP](feature-permissions-in-eop.md) autonome et utiliser le CAE pour modifier la liste des membres des [groupes de rôles.](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups)

- Pour plus d’informations sur les raccourcis clavier qui peuvent s’appliquer aux procédures de cet article, voir raccourcis clavier pour le Centre d’administration [Exchange dans Exchange Online.](https://docs.microsoft.com/Exchange/accessibility/keyboard-shortcuts-in-admin-center)

> [!TIP]
> Vous rencontrez des difficultés ? Demandez de l’aide dans le Forum [Exchange Online Protection](https://social.technet.microsoft.com/Forums/forefront/home?forum=FOPE) .

## <a name="use-the-eac-to-view-the-admin-audit-log"></a>Utiliser le EAC pour afficher le journal d’audit de l’administrateur

1. Dans le EAC, sélectionnez Audit de **la** gestion de la conformité, puis exécutez le rapport du journal \>  **d’audit de l’administrateur.**

2. Dans **la** page Rechercher les modifications apportées aux groupes de rôles d’administrateur qui s’ouvre, choisissez une **date** de début et une **date** de fin (la plage par défaut est les deux dernières semaines), puis choisissez **Rechercher.** Toutes les modifications de configuration effectuées pendant la période spécifiée sont affichées et peuvent être triées, avec les informations suivantes :

   - **Date**: date et heure de la modification de configuration. La date et l'heure sont enregistrées au format temps universel coordonné (UTC).

   - **Cmdlet**: nom de la cmdlet utilisée pour modifier la configuration.

   - **User**: nom du compte d’utilisateur de l’utilisateur qui a effectué la modification de configuration.

     Jusqu'à 5 000 entrées s'affichent sur plusieurs pages. Si vous devez affiner vos résultats, spécifiez une plage de dates plus courte. Si vous sélectionnez un seul résultat de recherche, l'information supplémentaire suivante s'affiche dans le volet de détails :

   - **Objet modifié**: objet modifié par l’cmdlet.

   - **Parameters (Parameter:Value)**: paramètres de cmdlet utilisés et toute valeur spécifiée avec le paramètre.

3. Si vous souhaitez imprimer une entrée du journal d'audit spécifique, choisissez le bouton **Imprimer** dans le volet de détails.

## <a name="use-standalone-eop-powershell-to-view-the-admin-audit-log"></a>Utiliser EOP PowerShell autonome pour afficher le journal d’audit de l’administrateur

Vous pouvez utiliser EOP PowerShell autonome pour rechercher des entrées du journal d’audit qui répondent aux critères que vous spécifiez. Utilisez la syntaxe suivante :

```PowerShell
Search-AdminAuditLog [-Cmdlets <Cmdlet1,Cmdlet2,...CmdletN>] [-Parameters <Parameter1,Parameter2,...ParameterN>] [-StartDate <UTCDateTime>] [-EndDate <UTCDateTime>] [-UserIds <"User1","User2",..."UserN">] [-ObjectIds <"Object1","Object2",..."ObjectN">] [-IsSuccess <$true | $false>]
```

**Remarques** :

- Vous pouvez uniquement utiliser _le paramètre Parameters_ avec le _paramètre Cmdlets._

- Le _paramètre ObjectIds_ filtre les résultats en fonction de l’objet modifié par la cmdlet. Une valeur valide dépend de la façon dont l’objet est représenté dans le journal d’audit. Par exemple :

  - Nom
  - Nom canonique (par exemple, contoso.com/Users/Akia Al-Zuhairi)

  Vous devrez probablement utiliser d’autres paramètres de filtrage sur cette cmdlet pour affiner les résultats et identifier les types d’objets qui vous intéressent.

- Le _paramètre UserIds_ filtre les résultats selon l’utilisateur qui a effectué la modification (qui a effectué la cmdlet).

- Pour les _paramètres StartDate_ et _EndDate,_ si vous spécifiez une valeur de date/heure sans fuseau horaire, la valeur est au temps universel coordonné (UTC). Pour spécifier une valeur date/heure pour ce paramètre, utilisez l’une des options suivantes :

  - Spécifier la valeur de date/heure au format UTC : par exemple, "06/05/2016 14:30:00z".

  - Spécifiez la valeur de date/heure en tant que formule qui convertit la date/l’heure dans votre fuseau horaire local en UTC : Par exemple, `(Get-Date "5/6/2016 9:30 AM").ToUniversalTime()` . Pour plus d’informations, consultez [Get-Date](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date).

- La cmdlet renvoie un maximum de 1 000 entrées de journal par défaut. Utilisez le _paramètre ResultSize_ pour spécifier jusqu’à 250 000 entrées de journal. Vous pouvez également utiliser la valeur `Unlimited` pour renvoyer toutes les entrées.

Cet exemple effectue une recherche portant sur toutes les entrées du journal d'audit avec les critères suivants :

- **Date de** début : 4 août 2019
- **Date de** fin : 3 octobre 2019
- **Cmdlets**: Update-RoleGroupMember

```PowerShell
Search-AdminAuditLog -Cmdlets Update-RoleGroupMember -StartDate (Get-Date "08/04/2019").ToUniversalTime() -EndDate (Get-Date "10/03/2019").ToUniversalTime()
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Search-AdminAuditLog](https://docs.microsoft.com/powershell/module/exchange/search-adminauditlog).

### <a name="view-details-of-audit-log-entries"></a>Afficher le détail des entrées du journal d’audit

La cmdlet **Search-AdminAuditLog** renvoie les champs décrits dans la section Contenu du journal [d’audit](#audit-log-contents) plus loin dans cet article. Des champs renvoyés par la cmdlet, deux champs, **CmdletParameters** et **ModifiedProperties,** contiennent des informations supplémentaires qui ne sont pas renvoyées par défaut.

Pour afficher le contenu des champs **CmdletParameters** et **ModifiedProperties**, suivez la procédure ci-après.

1. Déterminez les critères sur lesquels doivent porter vos recherches, exécutez la cmdlet **Search-AdminAuditLog** et stockez les résultats dans une variable au moyen de la commande suivante.

    ```PowerShell
    $Results = Search-AdminAuditLog <search criteria>
    ```

2. Chaque entrée du journal d’audit est stockée en tant qu’élément de tableau dans la `$Results` variable. Vous pouvez sélectionner un élément de tableau en précisant son index. Les index des éléments de tableau commencent à zéro (0) pour le premier élément du tableau. Par exemple, pour extraire le cinquième élément de tableau dont l'index est 4, utilisez la commande suivante.

    ```PowerShell
    $Results[4]
    ```

3. La commande précédente renvoie l'entrée du journal stockée dans l'élément de tableau 4. Pour afficher le contenu des champs **CmdletParameters** et **ModifiedProperties** pour cette entrée du journal, utilisez les commandes suivantes.

    ```PowerShell
    $Results[4].CmdletParameters
    $Results[4].ModifiedProperties
    ```

4. Pour afficher le contenu des champs **CmdletParameters** ou **ModifiedParameters** dans une autre entrée du journal, modifiez l'index de l'élément de tableau.

## <a name="audit-log-contents"></a>Contenu des journaux d'audit

Chaque entrée du journal d’audit contient les informations décrites dans le tableau suivant. Le journal d’audit contient une ou plusieurs entrées de journal d’audit.

****

|Champ|Description|
|---|---|
|`RunspaceId`|Ce champ est utilisé en interne par EOP.|
|`ObjectModified`|Ce champ contient l’objet modifié par la cmdlet spécifiée dans le `CmdletName` champ.|
|`CmdletName`|Ce champ contient le nom de la cmdlet qui a été exécuté par l’utilisateur dans le `Caller` champ.|
|`CmdletParameters`|Ce champ contient les paramètres qui ont été spécifiés lors de l’exécutement de la cmdlet `CmdletName` dans le champ. La valeur spécifiée avec le paramètre est également stockée dans ce champ, mais invisible dans la sortie par défaut, le cas échéant.|
|`ModifiedProperties`|Ce champ contient les propriétés qui ont été modifiées sur l’objet dans le `ObjectModified` champ. L’ancienne valeur de la propriété et la nouvelle valeur stockée sont également stockées dans ce champ, mais sont invisibles dans la sortie par défaut.|
|`Caller`|Ce champ contient le compte d’utilisateur de l’utilisateur qui a dirigé la cmdlet dans le `CmdletName` champ.|
|`ExternalAccess`|Ce champ est utilisé en interne par EOP.|
|`Succeeded`|Ce champ spécifie si l’cmdlet du champ a `CmdletName` été correctement réussie. La valeur est l’une `True` ou l’autre. `False`|
|`Error`|Ce champ contient le message d’erreur généré si la cmdlet dans le `CmdletName` champ n’a pas pu se terminer correctement.|
|`RunDate`|Ce champ contient la date et l’heure d’exécuter la cmdlet dans `CmdletName` le champ. La date et l'heure sont enregistrées au format temps universel coordonné (UTC).|
|`OriginatingServer`|Ce champ indique le serveur sur lequel la cmdlet spécifiée dans `CmdletName` le champ a été exécuté.|
|`ClientIP`|Ce champ est utilisé en interne par EOP.|
|`SessionId`|Ce champ est utilisé en interne par EOP.|
|`AppId`|Ce champ est utilisé en interne par EOP.|
|`ClientAppId`|Ce champ est utilisé en interne par EOP.|
|`Identity`|Ce champ est utilisé en interne par EOP.|
|`IsValid`|Ce champ est utilisé en interne par EOP.|
|`ObjectState`|Ce champ est utilisé en interne par EOP.|
|
