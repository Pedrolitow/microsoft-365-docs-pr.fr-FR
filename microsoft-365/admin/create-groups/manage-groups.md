---
title: Gérer un groupe dans le centre d’administration
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
description: Apprenez à gérer les groupes Microsoft 365, notamment l’ajout de supprimer des membres du groupe, la modification de l’adresse de messagerie, du nom de groupe ou de la description et la personnalisation du fonctionnement du groupe.
ms.openlocfilehash: 8216b80ba6cd6bffe470f4fe4ace43307afba5f2
ms.sourcegitcommit: 3cdb670f10519f7af4015731e7910954ba9f70dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "48753300"
---
# <a name="manage-a-group-in-the-microsoft-365-admin-center"></a>Gérer un groupe dans le centre d’administration Microsoft 365

Une fois que vous avez [créé un groupe Microsoft 365](create-groups.md) et ajouté des membres du groupe, vous pouvez configurer votre groupe. Vous pouvez modifier le nom ou la description du groupe, gérer les propriétaires ou les membres, et spécifier si les expéditeurs externes peuvent envoyer un message électronique au groupe et s’il faut envoyer des copies des conversations de groupe aux membres.

Accédez au centre d’administration Microsoft 365 à l’adresse [https://admin.microsoft.com](https://admin.microsoft.com) .

## <a name="edit-the-group-name-or-description"></a>Modifier le nom ou la description du groupe

1. Dans le centre d’administration, développez **groupes**, puis cliquez sur **groupes**.

2. Sélectionnez le groupe que vous souhaitez modifier, puis cliquez sur **modifier le nom et la description**.

3. Mettez à jour le nom et la description, puis sélectionnez **Enregistrer**.

## <a name="manage-group-owners-and-members"></a>Gérer les propriétaires et les membres du groupe

1. Dans le centre d’administration, développez **groupes**, puis cliquez sur **groupes**.

2. Cliquez sur le nom du groupe que vous souhaitez gérer pour ouvrir le volet Paramètres.

3. Dans l’onglet **membres** , choisissez si vous souhaitez gérer les propriétaires ou les membres.

4. Sélectionnez **Ajouter** pour ajouter une personne ou cliquez sur **X** pour supprimer une personne.

5. Cliquez sur **Fermer**.

## <a name="send-copies-of-conversations-to-group-members-inboxes"></a>Envoyer des copies des conversations vers les boîtes de réception des membres du groupe
  
Lorsque vous utilisez le centre d’administration pour créer un groupe, par défaut, les utilisateurs n’obtiennent pas de copie des courriers électroniques de groupe et des invitations envoyées à leur boîte de réception. Ils devront accéder au groupe pour afficher les conversations et les réunions. Vous pouvez modifier ce paramètre dans le centre d’administration.

Lorsque vous activez ce paramètre, les membres du groupe reçoivent une copie des messages électroniques de groupe et des invitations envoyées à leur boîte de réception Outlook. Ces derniers peuvent le lire et supprimer cette copie du courrier sans affecter d'autres personnes. Une copie du courrier est conservée dans la boîte aux lettres du groupe.

Les membres du groupe peuvent désactiver la réception de ces messages en choisissant d’arrêter de suivre le groupe dans Outlook.

1. Dans le centre d’administration, développez **groupes**, puis cliquez sur **groupes**.

2. Cliquez sur le nom du groupe que vous souhaitez gérer pour ouvrir le volet Paramètres.

3. Dans l’onglet **paramètres** , sélectionnez **Envoyer des copies des conversations et des événements de groupe aux membres du groupe** si vous voulez que les membres reçoivent des copies des messages de groupe et des éléments de calendrier dans leur propre boîte de réception.

4. Sélectionnez **Enregistrer**.

## <a name="let-people-outside-the-organization-email-the-group"></a>Autoriser les utilisateurs extérieurs à l’organisation à envoyer des courriers électroniques au groupe

Cette option est intéressante si vous souhaitez avoir une adresse de messagerie d’entreprise telle que info@contoso.com.
 
1. Dans le centre d’administration, développez **groupes**, puis cliquez sur **groupes**.

2. Cliquez sur le nom du groupe que vous souhaitez gérer pour ouvrir le volet Paramètres.

3. Dans la liste groupes du centre d’administration, sélectionnez le nom du groupe que vous souhaitez modifier, puis sous l’onglet **paramètres** , sélectionnez **autoriser les expéditeurs externes à envoyer un message électronique à ce groupe**.
    
4. Sélectionnez **Enregistrer**.

## <a name="permanently-delete-a-microsoft-365-group"></a>Supprimer définitivement un groupe Microsoft 365

Il peut arriver que vous souhaitiez purger définitivement un groupe sans attendre que la période de suppression du logiciel de 30 jours expire. Pour ce faire, démarrez PowerShell et exécutez la commande suivante pour obtenir l'ID d'objet du groupe.
 
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

[Créer un groupe Microsoft 365](create-groups.md)

[Gérer l’accès invité aux groupes Microsoft 365](https://support.microsoft.com/office/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Choisir le domaine à utiliser lors de la création de groupes Microsoft 365](../../solutions/choose-domain-to-create-groups.md)

[Autoriser les membres à envoyer en tant que ou envoyer de la part d’un groupe Microsoft 365](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md)

[Mettre à niveau les listes de distribution vers des groupes Microsoft 365](../manage/upgrade-distribution-lists.md)

[Gérer les groupes Microsoft 365 avec PowerShell](https://docs.microsoft.com/microsoft-365/enterprise/manage-microsoft-365-groups-with-powershell)
