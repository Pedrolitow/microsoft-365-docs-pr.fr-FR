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
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 003d7a74-3e16-4453-ae0c-9dbae51f66d1
description: Les administrateurs peuvent apprendre à afficher et effectuer des recherches dans le journal d’audit de l’administrateur dans Exchange Online Protection (EOP) autonome.
ms.openlocfilehash: 9fe2c742083cde1ca36f6a04cd357a473a10aeac
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48196542"
---
# <a name="view-the-admin-audit-log-in-standalone-eop"></a>Afficher le journal d’audit de l’administrateur dans EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Exchange Online (EOP) autonomes sans boîtes aux lettres Exchange Online, vous pouvez utiliser le centre d’administration Exchange ou le PowerShell autonome EOP pour rechercher et afficher des entrées dans le journal d’audit de l’administrateur.

Le journal d’audit de l’administrateur enregistre des actions spécifiques, basées sur des applets de commande autonomes EOP PowerShell, effectuées par les administrateurs et les utilisateurs disposant de privilèges d’administration. Les entrées du journal d’audit de l’administrateur vous fournissent des informations sur la cmdlet qui a été exécutée, les paramètres utilisés, l’utilisateur qui a exécuté la cmdlet et les objets affectés.

> [!NOTE]
>
> - La journalisation d’audit de l’administrateur est activée par défaut et vous ne pouvez pas la désactiver.
>
> - Le journal d’audit de l’administrateur n’enregistre pas les actions basées sur les cmdlets qui commencent par les verbes **Get**, **Search**ou **test**.
>
> - Les entrées du journal d'audit sont conservées pendant 90 jours. Lorsqu’une entrée est antérieure à 90 jours, elle est supprimée.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le centre d’administration Exchange, consultez la rubrique [Exchange Admin Center in standalone EOP](exchange-admin-center-in-exchange-online-protection-eop.md).

- Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. Plus précisément, vous avez besoin du rôle journaux d’audit ou journaux d’audit en affichage seul, qui sont attribués aux groupes de rôles ComplianceManagement, OrganizationManagement (administrateurs globaux) et SecurityAdministrator par défaut. Pour plus d’informations, consultez la rubrique [autorisations dans EOP autonome](feature-permissions-in-eop.md) et utiliser le centre d’administration Exchange pour [modifier la liste des membres dans les groupes de rôles](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups).

- Pour plus d’informations sur les raccourcis clavier applicables aux procédures de cette rubrique, voir [raccourcis clavier pour le centre d’administration Exchange dans Exchange Online](https://docs.microsoft.com/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Vous rencontrez des difficultés ? Demandez de l’aide dans le Forum [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351) .

## <a name="use-the-eac-to-view-the-admin-audit-log"></a>Utiliser le centre d’administration Exchange pour afficher le journal d’audit de l’administrateur

1. Dans le centre d’administration Exchange, accédez à audit de **gestion de la conformité** \> **Auditing**, puis choisissez **exécuter le rapport du journal d’audit de l’administrateur**.

2. Dans la page **Rechercher les modifications apportées aux groupes de rôles d’administrateur** qui s’ouvre, choisissez une **Date de début** et une date de **fin** (la plage par défaut est les deux dernières semaines), puis choisissez **recherche**. Toutes les modifications de configuration effectuées pendant la période spécifiée sont affichées et peuvent être triées, avec les informations suivantes :

   - **Date**: date et heure de la modification de la configuration. La date et l'heure sont enregistrées au format temps universel coordonné (UTC).

   - **Cmdlet**: nom de la cmdlet qui a été utilisée pour la modification de la configuration.

   - **User**: nom du compte d’utilisateur de l’utilisateur qui a effectué la modification de configuration.

     Jusqu'à 5 000 entrées s'affichent sur plusieurs pages. Si vous devez affiner vos résultats, spécifiez une plage de dates plus courte. Si vous sélectionnez un seul résultat de recherche, l'information supplémentaire suivante s'affiche dans le volet de détails :

   - **Objet modifié**: objet qui a été modifié par la cmdlet.

   - **Parameters (paramètre : valeur)**: paramètres de l’applet de commande qui ont été utilisés et n’importe quelle valeur spécifiée avec le paramètre.

3. Si vous souhaitez imprimer une entrée du journal d'audit spécifique, choisissez le bouton **Imprimer** dans le volet de détails.

## <a name="use-standalone-eop-powershell-to-view-the-admin-audit-log"></a>Utilisation d’EOP PowerShell autonome pour afficher le journal d’audit de l’administrateur

Vous pouvez utiliser la version autonome d’EOP PowerShell pour rechercher des entrées du journal d’audit correspondant aux critères que vous spécifiez. Utilisez la syntaxe suivante :

```PowerShell
Search-AdminAuditLog [-Cmdlets <Cmdlet1,Cmdlet2,...CmdletN>] [-Parameters <Parameter1,Parameter2,...ParameterN>] [-StartDate <UTCDateTime>] [-EndDate <UTCDateTime>] [-UserIds <"User1","User2",..."UserN">] [-ObjectIds <"Object1","Object2",..."ObjectN">] [-IsSuccess <$true | $false>]
```

**Remarques** :

- Vous ne pouvez utiliser le paramètre _Parameters_ qu’avec le paramètre _cmdlets_ .

- Le paramètre _ObjectID_ filtre les résultats par l’objet qui a été modifié par la cmdlet. Une valeur valide dépend de la façon dont l’objet est représenté dans le journal d’audit. Par exemple :

  - Nom
  - Nom unique canonique (par exemple, contoso.com/Users/Akia al-Zuhairi)

  Vous devrez probablement utiliser d’autres paramètres de filtrage sur cette cmdlet pour affiner les résultats et identifier les types d’objets qui vous intéressent.

- Le paramètre _userids_ filtre les résultats par l’utilisateur qui a effectué la modification (qui a exécuté l’applet de commande).

- Pour les paramètres _StartDate_ et _EndDate_ , si vous spécifiez une valeur de date/heure sans fuseau horaire, la valeur est au format UTC (temps universel coordonné). Pour spécifier une valeur date/heure pour ce paramètre, utilisez l’une des options suivantes :

  - Spécifier la valeur de date/heure au format UTC : par exemple, "06/05/2016 14:30:00z".

  - Spécifiez la valeur date/heure sous la forme d’une formule qui convertit la date/l’heure de votre fuseau horaire local en heure UTC : par exemple, `(Get-Date "5/6/2016 9:30 AM").ToUniversalTime()` . Pour plus d’informations, consultez [Get-Date](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date).

- L’applet de commande renvoie un maximum de 1 000 entrées de journal par défaut. Utilisez le paramètre _result_ pour spécifier jusqu’à 250 000 entrées de journal. Vous pouvez utiliser la valeur `Unlimited` pour renvoyer toutes les entrées.

Cet exemple effectue une recherche portant sur toutes les entrées du journal d'audit avec les critères suivants :

- **Date de début**: 4 août 2019
- **Date de fin**: 3 octobre 2019
- **Cmdlets**: Update-RoleGroupMember

```PowerShell
Search-AdminAuditLog -Cmdlets Update-RoleGroupMember -StartDate (Get-Date "08/04/2019").ToUniversalTime() -EndDate (Get-Date "10/03/2019").ToUniversalTime()
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Search-AdminAuditLog](https://docs.microsoft.com/powershell/module/exchange/search-adminauditlog).

### <a name="view-details-of-audit-log-entries"></a>Afficher le détail des entrées du journal d’audit

L’applet de commande **Search-AdminAuditLog** renvoie les champs décrits dans la section [contenu du journal d’audit](#audit-log-contents) , plus loin dans cette rubrique. Parmi les champs renvoyés par l’applet de commande, deux champs, **CmdletParameters** et **ModifiedProperties**, contiennent des informations supplémentaires qui ne sont pas renvoyées par défaut.

Pour afficher le contenu des champs **CmdletParameters** et **ModifiedProperties**, suivez la procédure ci-après.

1. Déterminez les critères sur lesquels doivent porter vos recherches, exécutez la cmdlet **Search-AdminAuditLog** et stockez les résultats dans une variable au moyen de la commande suivante.

    ```PowerShell
    $Results = Search-AdminAuditLog <search criteria>
    ```

2. Chaque entrée du journal d’audit est stockée sous la forme d’un élément de tableau dans la variable `$Results` . Vous pouvez sélectionner un élément de tableau en précisant son index. Les index des éléments de tableau commencent à zéro (0) pour le premier élément du tableau. Par exemple, pour extraire le cinquième élément de tableau dont l'index est 4, utilisez la commande suivante.

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
|`ObjectModified`|Ce champ contient l’objet qui a été modifié par la cmdlet spécifiée dans le `CmdletName` champ.|
|`CmdletName`|Ce champ contient le nom de la cmdlet exécutée par l’utilisateur dans le `Caller` champ.|
|`CmdletParameters`|Ce champ contient les paramètres qui ont été spécifiés lors de l’exécution de la cmdlet dans le `CmdletName` champ. La valeur spécifiée avec le paramètre est également stockée dans ce champ, mais invisible dans la sortie par défaut, le cas échéant.|
|`ModifiedProperties`|Ce champ contient les propriétés qui ont été modifiées sur l’objet dans le `ObjectModified` champ. L’ancienne valeur de la propriété et la nouvelle valeur stockée sont également stockées dans ce champ, mais sont invisibles dans la sortie par défaut.|
|`Caller`|Ce champ contient le compte d’utilisateur de l’utilisateur qui a exécuté la cmdlet dans le `CmdletName` champ.|
|`ExternalAccess`|Ce champ est utilisé en interne par EOP.|
|`Succeeded`|Ce champ indique si la cmdlet dans le `CmdletName` champ a été exécutée avec succès. La valeur est soit `True` ou `False` .|
|`Error`|Ce champ contient le message d’erreur généré si l’exécution de la cmdlet dans le `CmdletName` champ a échoué.|
|`RunDate`|Ce champ contient la date et l’heure d’exécution de la cmdlet dans le `CmdletName` champ. La date et l'heure sont enregistrées au format temps universel coordonné (UTC).|
|`OriginatingServer`|Ce champ indique le serveur sur lequel la cmdlet spécifiée dans le `CmdletName` champ a été exécutée.|
|`ClientIP`|Ce champ est utilisé en interne par EOP.|
|`SessionId`|Ce champ est utilisé en interne par EOP.|
|`AppId`|Ce champ est utilisé en interne par EOP.|
|`ClientAppId`|Ce champ est utilisé en interne par EOP.|
|`Identity`|Ce champ est utilisé en interne par EOP.|
|`IsValid`|Ce champ est utilisé en interne par EOP.|
|`ObjectState`|Ce champ est utilisé en interne par EOP.|
|
