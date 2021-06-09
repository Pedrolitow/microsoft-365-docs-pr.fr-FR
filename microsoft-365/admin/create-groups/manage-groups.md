---
title: Gérer un groupe dans le Centre d’administration
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 74a1ef8b-3844-4d08-9980-9f8f7a36000f
description: Apprenez à gérer les Microsoft 365, notamment en ajoutant supprimer des membres du groupe, en éditant l’adresse e-mail, le nom du groupe ou la description, et en personnalisant le fonctionnement du groupe.
ms.openlocfilehash: 3ba3dd36ed3929e956ce6359e678d6b684f64bb9
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50908709"
---
# <a name="manage-a-group-in-the-microsoft-365-admin-center"></a>Gérer un groupe dans le centre d’administration Microsoft 365 de gestion

Après avoir créé [un groupe Microsoft 365 et](create-groups.md) ajouté des membres du groupe, vous pouvez configurer votre groupe. Vous pouvez modifier le nom ou la description du groupe, gérer les propriétaires ou les membres, et spécifier si les expéditeurs externes peuvent envoyer des messages électroniques au groupe et s’il faut envoyer des copies des conversations de groupe aux membres.

Go to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com) .

## <a name="edit-the-group-name-or-description"></a>Modifier le nom ou la description du groupe

1. Dans le Centre d’administration, développez **Groupes,** puis cliquez sur **Groupes.**

2. Sélectionnez le groupe à modifier, puis cliquez sur **Modifier le nom et la description.**

3. Mettez à jour le nom et la description, puis sélectionnez **Enregistrer.**

## <a name="manage-group-owners-and-members"></a>Gérer les propriétaires et les membres du groupe

1. Dans le Centre d’administration, développez **Groupes,** puis cliquez sur **Groupes.**

2. Cliquez sur le nom du groupe que vous souhaitez gérer pour ouvrir le volet des paramètres.

3. Sous **l’onglet** Membres, choisissez si vous souhaitez gérer les propriétaires ou les membres.

4. Choisissez **Ajouter** pour ajouter une personne ou cliquez **sur X** pour supprimer une personne.

5. Cliquez sur **Fermer**.

## <a name="send-copies-of-conversations-to-group-members-inboxes"></a>Envoyer des copies des conversations aux boîtes de réception des membres du groupe
  
Lorsque vous utilisez le Centre d’administration pour créer un groupe, par défaut, les utilisateurs n’obtiennent pas de copies des messages électroniques de groupe et des invitations aux réunions envoyées à leur boîte de réception. Ils doivent aller au groupe pour voir les conversations et les réunions. Vous pouvez modifier ce paramètre dans le Centre d’administration.

Lorsque vous activer ce paramètre, les membres du groupe obtiennent une copie des e-mails de groupe et des invitations aux réunions envoyés à leur boîte Outlook réception. Ces derniers peuvent le lire et supprimer cette copie du courrier sans affecter d'autres personnes. Une copie du courrier est conservée dans la boîte aux lettres du groupe.

Les membres du groupe peuvent refuser de recevoir ces e-mails en choisissant d’arrêter de suivre le groupe dans Outlook.

1. Dans le Centre d’administration, développez **Groupes,** puis cliquez sur **Groupes.**

2. Cliquez sur le nom du groupe que vous souhaitez gérer pour ouvrir le volet des paramètres.

3. Sous **l’onglet Paramètres,** sélectionnez Envoyer des copies des conversations de groupe et des **événements** aux membres du groupe si vous souhaitez que les membres reçoivent des copies des messages de groupe et des éléments de calendrier dans leur propre boîte de réception.

4. Sélectionnez **Enregistrer**.

## <a name="let-people-outside-the-organization-email-the-group"></a>Laisser les personnes extérieures à l’organisation envoyer un e-mail au groupe

Cette option est idéale si vous souhaitez avoir une adresse de messagerie d’entreprise telle que info@contoso.com.
 
1. Dans le Centre d’administration, développez **Groupes,** puis cliquez sur **Groupes.**

2. Cliquez sur le nom du groupe que vous souhaitez gérer pour ouvrir le volet des paramètres.

3. Dans la liste des groupes du Centre d’administration, sélectionnez le nom du groupe à modifier, puis sous l’onglet **Paramètres,** sélectionnez Autoriser les expéditeurs externes à envoyer un e-mail à **ce groupe.**
    
4. Sélectionnez **Enregistrer**.

## <a name="permanently-delete-a-microsoft-365-group"></a>Supprimer définitivement un groupe Microsoft 365 de données

Il peut arriver que vous vouliez purger définitivement un groupe sans attendre l’expiration de la période de suppression temporaire de 30 jours. Pour ce faire, démarrez PowerShell et exécutez la commande suivante pour obtenir l'ID d'objet du groupe.
 
 ```powershell
`Get-AzureADMSDeletedGroup`
```

Prenez note de l’ID d’objet du ou des groupes que vous souhaitez supprimer définitivement.
  
> [!CAUTION]
> La suppression définitive du groupe supprime le groupe et ses données pour toujours. 
  
Pour supprimer définitivement le groupe, exécutez la commande suivante dans PowerShell :

```powershell
`Remove-AzureADMSDeletedDirectoryObject -Id <objectId>`
```

Pour vérifier que le groupe a été supprimé définitivement, réexécutez l'applet de commande  *Get-AzureADMSDeletedGroup*  pour confirmer que le groupe n'apparaît plus dans la liste des groupes supprimés (suppression réversible). Dans certains cas, la suppression définitive du groupe et de toutes ses données peut prendre jusqu'à 24 heures. 
  
## <a name="related-articles"></a>Articles connexes

[Créer un groupe Microsoft 365 de groupe](create-groups.md)

[Gérer l’accès de groupe aux groupes Microsoft 365](https://support.microsoft.com/office/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Choisir le domaine à utiliser lors de la création de Microsoft 365 groupes](../../solutions/choose-domain-to-create-groups.md)

[Autoriser les membres à envoyer en tant que ou de la part d’Microsoft 365 groupe](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md)

[Mettre à niveau les listes de distribution Microsoft 365 groupes](../manage/upgrade-distribution-lists.md)

[Gérer Microsoft 365 groupes avec PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md)