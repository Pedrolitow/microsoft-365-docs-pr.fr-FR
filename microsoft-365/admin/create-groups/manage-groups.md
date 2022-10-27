---
title: Gérer un groupe dans le Centre d’administration
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 74a1ef8b-3844-4d08-9980-9f8f7a36000f
description: Découvrez comment gérer les Groupes Microsoft 365, notamment l’ajout de membres de groupe de suppression, la modification de l’adresse e-mail, du nom du groupe ou de la description et la personnalisation du fonctionnement du groupe.
ms.openlocfilehash: 2f8536854f2787c0489b06691f6fca602178c39a
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68728662"
---
# <a name="manage-a-group-in-the-microsoft-365-admin-center"></a>Gérer un groupe dans le Centre d'administration Microsoft 365

Après avoir [créé un groupe Microsoft 365](create-groups.md) et ajouté des membres du groupe, vous pouvez configurer votre groupe. Vous pouvez modifier le nom ou la description du groupe, gérer les propriétaires ou les membres, et spécifier si les expéditeurs externes peuvent envoyer un e-mail au groupe et s’il faut envoyer des copies des conversations de groupe aux membres.

Accédez au Centre d'administration Microsoft 365 sur [https://admin.microsoft.com](https://admin.microsoft.com).

## <a name="edit-the-group-name-or-description"></a>Modifier le nom ou la description du groupe

1. Dans le Centre d’administration, développez **Groupes**, puis cliquez sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groupes**</a>.

2. Sélectionnez le groupe que vous souhaitez modifier, puis cliquez sur **Modifier le nom et la description**.

3. Mettez à jour le nom et la description, puis sélectionnez **Enregistrer**.

## <a name="manage-group-owners-and-members"></a>Gérer les propriétaires et les membres du groupe

1. Dans le Centre d’administration, développez **Groupes**, puis cliquez sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groupes**</a>.

2. Cliquez sur le nom du groupe que vous souhaitez gérer pour ouvrir le volet Paramètres.

3. Sous l’onglet **Membres** , choisissez si vous souhaitez gérer les propriétaires ou les membres.

4. Choisissez **Ajouter** pour ajouter une personne ou cliquez sur **X** pour supprimer une personne.

5. Cliquez sur **Fermer**.

## <a name="send-copies-of-conversations-to-group-members-inboxes"></a>Envoyer des copies des conversations aux boîtes de réception des membres du groupe
  
Lorsque vous utilisez le Centre d’administration pour créer un groupe, par défaut, les utilisateurs n’obtiennent pas de copies des e-mails de groupe envoyés à leur boîte de réception, bien que les utilisateurs obtiennent des copies des invitations aux réunions de groupe envoyées à leur boîte de réception. Ils devront se rendre au groupe pour voir les conversations. Vous pouvez modifier ce paramètre dans le centre d’administration.

Lorsque vous activez ce paramètre, les membres du groupe reçoivent une copie des e-mails de groupe et des invitations à la réunion envoyés à leur boîte de réception Outlook. Ces derniers peuvent le lire et supprimer cette copie du courrier sans affecter d'autres personnes. Une copie du courrier est conservée dans la boîte aux lettres du groupe.

Les membres du groupe peuvent refuser de recevoir ces e-mails en choisissant d’arrêter de suivre le groupe dans Outlook.

1. Dans le Centre d’administration, développez **Groupes**, puis cliquez sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groupes**</a>.

2. Cliquez sur le nom du groupe que vous souhaitez gérer pour ouvrir le volet Paramètres.

3. Sous l’onglet **Paramètres** , sélectionnez **Envoyer des copies des conversations et des événements de groupe aux membres du groupe** si vous souhaitez que les membres reçoivent des copies des messages de groupe et des éléments de calendrier dans leur propre boîte de réception.

4. Sélectionnez **Enregistrer**.

## <a name="let-people-outside-the-organization-email-the-group"></a>Autoriser les personnes extérieures à l’organisation à envoyer un e-mail au groupe

Cette option est idéale si vous souhaitez avoir une adresse e-mail d’entreprise telle que info@contoso.com.
 
1. Dans le Centre d’administration, développez **Groupes**, puis cliquez sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groupes**</a>.

2. Cliquez sur le nom du groupe que vous souhaitez gérer pour ouvrir le volet Paramètres.

3. Dans la liste groupes du centre d’administration, sélectionnez le nom du groupe que vous souhaitez modifier, puis, sous l’onglet **Paramètres** , sélectionnez **Autoriser les expéditeurs externes à envoyer un e-mail à ce groupe**.
    
4. Sélectionnez **Enregistrer**.

> [!NOTE]
> Jusqu’à 30 minutes peuvent être nécessaires avant que les utilisateurs extérieurs à l’organisation puissent envoyer un e-mail au groupe.

## <a name="permanently-delete-a-microsoft-365-group"></a>Supprimer définitivement un groupe Microsoft 365

Il peut arriver que vous souhaitiez vider définitivement un groupe sans attendre l’expiration de la période de suppression réversible de 30 jours. Pour ce faire, démarrez PowerShell et exécutez la commande suivante pour obtenir l'ID d'objet du groupe.
 
 ```powershell
Get-AzureADMSDeletedGroup
```

Notez l’ID d’objet du ou des groupes que vous souhaitez supprimer définitivement.
  
> [!CAUTION]
> La suppression définitive du groupe supprime le groupe et ses données pour toujours. 
  
Pour supprimer définitivement le groupe, exécutez la commande suivante dans PowerShell :

```powershell
Remove-AzureADMSDeletedDirectoryObject -Id <objectId>
```

To confirm that the group has been successfully purged, run the  *Get-AzureADMSDeletedGroup*  cmdlet again to confirm that the group no longer appears on the list of soft-deleted groups. In some cases it may take as long as 24 hours for the group and all of its data to be permanently deleted. 
  
## <a name="related-articles"></a>Articles connexes

[Créer un groupe Microsoft 365 ](create-groups.md)

[Gérer l’accès invité à Groupes Microsoft 365](https://support.microsoft.com/office/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Choisissez le domaine à utiliser lors de la création d’Groupes Microsoft 365](../../solutions/choose-domain-to-create-groups.md)

[Autoriser les membres à envoyer en tant que ou à envoyer au nom d’un groupe Microsoft 365](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md)

[Mettre à niveau les listes de distribution vers Groupes Microsoft 365](../manage/upgrade-distribution-lists.md)

[Gérer les Groupes Microsoft 365 avec PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md)
