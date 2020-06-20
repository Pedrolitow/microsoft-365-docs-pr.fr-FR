---
title: Créer une suspension pour litige
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 3/13/2018
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid: MET150
ms.assetid: 39db1659-0b12-4243-a21c-2614512dcb44
description: Découvrez comment placer une boîte aux lettres en conservation pour litige, en conservant tout le contenu de la boîte aux lettres pendant une enquête.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 9c62dfcd9e4cf1e3cc75e029b250c7abe80de6df
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44818043"
---
# <a name="create-a-litigation-hold"></a>Créer une suspension pour litige

Vous pouvez placer une boîte aux lettres en conservation pour litige pour conserver tout le contenu des boîtes aux lettres, y compris les éléments supprimés et les versions d’origine des éléments modifiés. Lorsque vous placez une boîte aux lettres utilisateur en conservation pour litige, le contenu de la boîte aux lettres d’archivage de l’utilisateur (si elle est activée) est également conservé. Lorsque vous créez une suspension, vous pouvez spécifier une durée de conservation (également appelée *conservation basée sur l’heure*) afin que les éléments supprimés et modifiés soient conservés pendant une période spécifiée, puis supprimés définitivement de la boîte aux lettres. Vous pouvez également conserver indéfiniment le contenu (appelé *conservation infinie*) ou jusqu’à ce que la conservation pour litige ne soit supprimée. Si vous spécifiez une période de durée de blocage, elle est calculée à partir de la date de réception d’un message ou de la création d’un élément de boîte aux lettres. 
  
Voici ce qui se passe lorsque vous créez une suspension pour litige.
  
- Les éléments définitivement supprimés par l’utilisateur sont conservés dans le dossier éléments récupérables de la boîte aux lettres de l’utilisateur pendant la durée de la conservation.
    
- Les éléments purgés du dossier éléments récupérables par l’utilisateur sont conservés pendant la durée de la conservation.
    
- Le quota de stockage pour le dossier éléments récupérables est passé de 30 Go à 110 Go.
    
- Les éléments dans les boîtes aux lettres principale et d’archivage de l’utilisateur sont conservés
    
## <a name="assign-an-exchange-online-plan-2-license"></a>Affecter une licence Exchange Online plan 2

- Pour placer une boîte aux lettres Exchange Online en conservation pour litige, une licence Exchange Online plan 2 doit lui être attribuée. Si une licence Exchange Online plan 1 est attribuée à une boîte aux lettres, vous devez lui attribuer une licence d’archivage Exchange Online distincte pour la mettre en attente.
    

## <a name="place-a-mailbox-on-litigation-hold"></a>Placement d’une boîte aux lettres en conservation pour litige

Voici les étapes à suivre pour placer une boîte aux lettres en conservation pour litige à l’aide du centre d’administration Exchange.

1. Accédez à [https://outlook.office.com/ecp](https://outlook.office.com/ecp) et connectez-vous à l’aide de votre compte d’administrateur général.

2. Cliquez sur **destinataires > boîtes aux lettres** dans le volet de navigation de gauche.

3. Sélectionnez la boîte aux lettres que vous souhaitez placer en conservation pour litige, puis cliquez sur **modifier**.

4. Dans la page de propriétés de boîte aux lettres, cliquez sur **Fonctionnalités de boîte aux lettres**.
    
5. Sous **Conservation pour litige : désactivée**, cliquez sur **Activer** pour mettre la boîte aux lettres en conservation pour litige.
    
6. Sur la page **conservation pour litige** , entrez les informations facultatives suivantes : 
    
    - **Durée de la conservation pour litige (jours)** : cette zone permet de créer une conservation basée sur le temps et de spécifier la durée pendant laquelle les éléments de boîte aux lettres sont conservés lorsque la boîte aux lettres est placée en conservation pour litige. La durée est calculée à compter de la date de réception ou de création de l'élément de boîte aux lettres. Lorsque la durée de la conservation expire pour un élément spécifique, cet élément n’est plus conservé. Si vous laissez cette zone vide, les éléments sont conservés indéfiniment ou jusqu’à ce que la conservation soit supprimée. Indiquez la période en nombre de jours.
    
    - **Remarque** : cette zone permet d’informer l’utilisateur que sa boîte aux lettres est en conservation pour litige. La note apparaît sur la page informations sur le compte dans la boîte aux lettres de l’utilisateur si elle utilise Outlook 2010 ou une version ultérieure. Pour accéder à cette page, les utilisateurs peuvent cliquer sur **fichier** dans Outlook.
    
    - **URL** : ce champ permet de diriger l’utilisateur vers un site Web pour plus d’informations sur la conservation pour litige. Cette URL apparaît sur la page informations sur le compte dans la boîte aux lettres de l’utilisateur, si elle utilise Outlook 2010 ou une version ultérieure. Pour accéder à cette page, les utilisateurs peuvent cliquer sur **fichier** dans Outlook..

7. Cliquez sur **Enregistrer** sur la page **conservation pour litige** , puis cliquez sur **Enregistrer** dans la page Propriétés de la boîte aux lettres.

### <a name="create-a-litigation-hold-using-powershell"></a>Création d’une conservation pour litige à l’aide de PowerShell

Vous pouvez également créer une conservation pour litige en exécutant la commande suivante dans [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true
```

La commande précédente conserve les éléments indéfiniment, car la durée de la conservation n’est pas spécifiée. Pour créer une conservation basée sur l’heure, à l’aide de la commande suivante :

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true -LitigationHoldDuration <number of days>
```

Pour plus d’informations, consultez [Set-Mailbox](https://docs.microsoft.com/powershell/module/exchange/set-mailbox).

## <a name="how-does-litigation-hold-work"></a>Comment fonctionne la conservation pour litige ?

Dans le flux de travail d'éléments supprimés normal, un élément de boîte aux lettres est déplacé dans le sous-dossier Suppressions du dossier Éléments récupérables lorsqu'il est définitivement supprimé (MAJ + SUPPR) ou supprimé du dossier Éléments supprimés. Une stratégie de suppression (balise de rétention configurée avec une action de rétention Supprimer) déplace également les éléments dans le sous-dossier Suppressions à l'expiration de la période de rétention. Lorsqu'un utilisateur purge un élément du dossier Éléments récupérables ou lorsque la période de rétention des éléments supprimés expire, l'élément est déplacé dans le sous-dossier Purges et marqué pour suppression définitive. Il sera (purgé) d'Exchange lors du prochain traitement de la boîte aux lettres par l'Assistant Dossier géré.

When a mailbox is placed on Litigation Hold, items in the Purges subfolder are preserved for the hold duration specified by the Litigation Hold. The hold duration is calculated from the original date an item was received or created, and defines how long items in the Purges subfolder are held. When the hold duration expires for an item in the Purges subfolder, the item is marked for permanent deletion and will be purged from Exchange the next time the mailbox is processed by the MFA. If an indefinite hold is placed on a mailbox, items will never be purged from the Purges subfolder.

L'illustration suivante montre les sous-dossiers des dossiers Éléments récupérables et le processus de conservation inaltérable.

![Cycle de vie de conservation pour litige](../media/LitigationHoldLifeCycle.png)

> [!NOTE]
> Si une conservation associée à un cas de découverte électronique est placée dans une boîte aux lettres, les éléments purgés sont déplacés du sous-dossier suppressions vers le sous-dossier DiscoveryHolds et sont conservés jusqu’à ce que la boîte aux lettres soit libérée de la conservation eDiscovery.
  
