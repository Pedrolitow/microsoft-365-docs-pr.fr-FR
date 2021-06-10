---
title: Créer une suspension pour litige
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid: MET150
ms.assetid: 39db1659-0b12-4243-a21c-2614512dcb44
description: Découvrez comment placer une boîte aux lettres en attente pour litige, en conservant tout le contenu de la boîte aux lettres au cours d’un examen.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 81d3bf7bba0aadbcd2d52b5f7707caeea96e26c1
ms.sourcegitcommit: 07dea2aa98daf0c4086f8590375167830027c802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51750058"
---
# <a name="create-a-litigation-hold"></a>Créer une suspension pour litige

Vous pouvez placer une boîte aux lettres en attente pour litige pour conserver tout le contenu de la boîte aux lettres, y compris les éléments supprimés et les versions d’origine des éléments modifiés. Lorsque vous placez une boîte aux lettres utilisateur en attente pour litige, le contenu de la boîte aux lettres d’archivage de l’utilisateur (si elle est activée) est également conservé. Lorsque vous créez une attente, vous pouvez spécifier une durée de la rétention (également appelée « attente basée sur le temps *)* afin que les éléments supprimés et modifiés soient conservés pendant une période spécifiée, puis supprimés définitivement de la boîte aux lettres. Vous pouvez également conserver le contenu indéfiniment (appelé « attente infinie *»* ou jusqu’à ce que la rétention pour litige soit supprimée. Si vous spécifiez une période de attente, elle est calculée à partir de la date de réception d’un message ou de la création d’un élément de boîte aux lettres. 
  
Voici ce qui se produit lorsque vous créez une attente pour litige.
  
- Les éléments supprimés définitivement par l’utilisateur sont conservés dans le dossier Éléments récupérables de la boîte aux lettres de l’utilisateur pendant toute la durée de la rétention.

- Les éléments purgés du dossier Éléments récupérables par l’utilisateur sont conservés pendant toute la durée de la rétention.

- Le quota de stockage pour le dossier Éléments récupérables est augmenté de 30 Go à 110 Go.

- Les éléments des boîtes aux lettres principale et d’archivage de l’utilisateur sont conservés

## <a name="assign-an-exchange-online-plan-2-license"></a>Attribuer une licence Exchange Online Plan 2

Pour placer une boîte Exchange Online boîte aux lettres en attente pour litige, une licence Plan 2 Exchange Online lui est attribuée. Si une boîte aux lettres est Exchange Online licence Plan 1, vous devez lui attribuer une licence Archivage Exchange Online pour la placer en attente.

> [!NOTE]
> Pour Office 365 Éducation organisations, la Office 365 A1 pour litige est prise en charge dans les abonnements Exchange Online Plan 1 avec des fonctionnalités supplémentaires. Pour plus d’informations, voir la section « fonctionnalités Exchange Online » dans la [description Office 365 Éducation service.](/office365/servicedescriptions/office-365-platform-service-description/office-365-education#exchange-online-features)

## <a name="place-a-mailbox-on-litigation-hold"></a>Placement d’une boîte aux lettres en conservation pour litige

Voici les étapes à suivre pour placer une boîte aux lettres en attente pour litige à l’aide Exchange’administration centrale.

1. Go to [https://outlook.office.com/ecp](https://outlook.office.com/ecp) and sign in using your global administrator account.

2. Cliquez **sur Destinataires > boîtes aux lettres** dans le volet de navigation gauche.

3. Sélectionnez la boîte aux lettres que vous souhaitez placer en attente pour litige, puis cliquez sur **Modifier.**

4. Dans la page de propriétés de boîte aux lettres, cliquez sur **Fonctionnalités de boîte aux lettres**.
    
5. Sous **Conservation pour litige : désactivée**, cliquez sur **Activer** pour mettre la boîte aux lettres en conservation pour litige.
    
6. Dans la page **De attente pour** litige, entrez les informations facultatives suivantes : 
    
    - Durée de la mise en attente **pour litige (jours)** : cette zone vous indique la durée de la mise en attente des éléments de boîte aux lettres lorsque la boîte aux lettres est placée en attente pour litige. La durée est calculée à compter de la date de réception ou de création de l'élément de boîte aux lettres. Lorsque la durée de la conservation expire pour un élément spécifique, cet élément n’est plus conservé. Si vous laissez cette zone vide, les éléments sont conservés indéfiniment ou jusqu’à ce que la conservation soit supprimée. Indiquez la période en nombre de jours.
    
    - **Remarque** : cette zone de message informe l’utilisateur que sa boîte aux lettres est en attente pour litige. La note s’affiche dans la page Informations sur le compte de la boîte aux lettres de l’utilisateur s’il utilise Outlook 2010 ou ultérieure. Pour accéder à cette page, les utilisateurs peuvent cliquer **sur Fichier** Outlook.
    
    - **URL** : cette zone vous aide à diriger l’utilisateur vers un site web pour plus d’informations sur la mise en attente pour litige. Cette URL apparaît sur la page Informations sur le compte dans la boîte aux lettres de l’utilisateur s’il utilise Outlook 2010 ou une date ultérieure. Pour accéder à cette page, les utilisateurs peuvent cliquer **sur Fichier** Outlook.

7. Cliquez **sur Enregistrer** sur la page De **attente** pour litige, puis **sur** Enregistrer sur la page des propriétés de la boîte aux lettres.

### <a name="create-a-litigation-hold-using-powershell"></a>Créer une attente pour litige à l’aide de PowerShell

Vous pouvez également créer une attente pour litige en exécutant la commande suivante [dans Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true
```

La commande précédente conserve les éléments indéfiniment, car la durée de la conservation n’est pas spécifiée. Pour créer une attente basée sur le temps, à l’aide de la commande suivante :

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true -LitigationHoldDuration <number of days>
```

Pour plus d’informations, consultez [Set-Mailbox](/powershell/module/exchange/set-mailbox).

## <a name="how-does-litigation-hold-work"></a>Comment fonctionne la conservation pour litige ?

Dans le flux de travail d'éléments supprimés normal, un élément de boîte aux lettres est déplacé dans le sous-dossier Suppressions du dossier Éléments récupérables lorsqu'il est définitivement supprimé (MAJ + SUPPR) ou supprimé du dossier Éléments supprimés. Une stratégie de suppression (balise de rétention configurée avec une action de rétention Supprimer) déplace également les éléments dans le sous-dossier Suppressions à l'expiration de la période de rétention. Lorsqu'un utilisateur purge un élément du dossier Éléments récupérables ou lorsque la période de rétention des éléments supprimés expire, l'élément est déplacé dans le sous-dossier Purges et marqué pour suppression définitive. Il sera (purgé) d'Exchange lors du prochain traitement de la boîte aux lettres par l'Assistant Dossier géré.

Lorsqu'une boîte aux lettres est placée en conservation pour litige, les éléments dans le sous-dossier Purges sont conservés pendant la durée spécifiée par la conservation pour litige. La durée de conservation est calculée à partir de la date de réception ou de création d'un élément, et correspond à la durée pendant laquelle les éléments du sous-dossier Purges sont conservés. Lorsque la durée de conservation d'un élément du sous-dossier expire, l'élément est marqué pour suppression définitive et supprimé d'Exchange lors du prochain traitement de la boîte aux lettres par l'Assistant Dossier géré. Si une boîte aux lettres est placée en conservation indéfinie, les éléments ne sont jamais purgés du sous-dossier Purges.

L'illustration suivante montre les sous-dossiers des dossiers Éléments récupérables et le processus de conservation inaltérable.

![Cycle de vie de la attente pour litige](../media/LitigationHoldLifeCycle.png)

> [!NOTE]
> Si une conservation associée à un cas eDiscovery est placée sur une boîte aux lettres, les éléments purgés sont déplacés du sous-dossier Suppressions vers le sous-dossier DiscoveryHolds et sont conservés jusqu’à ce que la boîte aux lettres soit libérée de la conservation eDiscovery.
