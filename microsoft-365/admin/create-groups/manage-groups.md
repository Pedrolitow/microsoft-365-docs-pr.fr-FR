---
title: Gérer un groupe dans le centre d’administration
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
description: Découvrez comment gérer Groupes Microsoft 365, notamment l’ajout de membres de groupe supprimés, la modification de l’adresse e-mail, du nom ou de la description du groupe et la personnalisation du fonctionnement du groupe.
ms.openlocfilehash: 89acd3c8b4935b4b57873d9d8b2cf7786a430e78
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68206958"
---
# <a name="manage-a-group-in-the-microsoft-365-admin-center"></a>Gérer un groupe dans le Centre d'administration Microsoft 365

Une fois que vous avez [créé un groupe Microsoft 365](create-groups.md) et ajouté des membres de groupe, vous pouvez configurer votre groupe. Vous pouvez modifier le nom ou la description du groupe, gérer les propriétaires ou les membres, et spécifier si les expéditeurs externes peuvent envoyer un e-mail au groupe et s’il faut envoyer des copies des conversations de groupe aux membres.

Accédez au Centre d'administration Microsoft 365 sur [https://admin.microsoft.com](https://admin.microsoft.com).

## <a name="edit-the-group-name-or-description"></a>Modifier le nom ou la description du groupe

1. Dans le centre d’administration, développez **Groupes**, puis cliquez sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groupes**</a>.

2. Sélectionnez le groupe à modifier, puis cliquez sur Modifier le **nom et la description**.

3. Mettez à jour le nom et la description, puis **sélectionnez Enregistrer**.

## <a name="manage-group-owners-and-members"></a>Gérer les propriétaires et les membres du groupe

1. Dans le centre d’administration, développez **Groupes**, puis cliquez sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groupes**</a>.

2. Cliquez sur le nom du groupe à gérer pour ouvrir le volet paramètres.

3. Sous l’onglet **Membres** , choisissez si vous souhaitez gérer les propriétaires ou les membres.

4. Choisissez **Ajouter** pour ajouter une personne ou cliquez sur **X** pour supprimer quelqu’un.

5. Cliquez sur **Fermer**.

## <a name="send-copies-of-conversations-to-group-members-inboxes"></a>Envoyer des copies de conversations aux boîtes de réception des membres du groupe
  
Lorsque vous utilisez le Centre d’administration pour créer un groupe, par défaut, les utilisateurs ne reçoivent pas de copies des e-mails de groupe envoyés à leurs boîtes de réception, bien que les utilisateurs reçoivent des copies des invitations aux réunions de groupe envoyées à leurs boîtes de réception. Ils devront accéder au groupe pour voir les conversations. Vous pouvez modifier ce paramètre dans le Centre d’administration.

Lorsque vous activez ce paramètre, les membres du groupe reçoivent une copie des e-mails de groupe et des invitations à la réunion envoyés à leur boîte de réception Outlook. Ces derniers peuvent le lire et supprimer cette copie du courrier sans affecter d'autres personnes. Une copie du courrier est conservée dans la boîte aux lettres du groupe.

Les membres du groupe peuvent refuser de recevoir ces e-mails en choisissant d’arrêter de suivre le groupe dans Outlook.

1. Dans le centre d’administration, développez **Groupes**, puis cliquez sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groupes**</a>.

2. Cliquez sur le nom du groupe à gérer pour ouvrir le volet paramètres.

3. Sous l’onglet **Paramètres** , sélectionnez **Envoyer des copies des conversations de groupe et des événements aux membres du groupe** si vous souhaitez que les membres reçoivent des copies des messages de groupe et des éléments de calendrier dans leur propre boîte de réception.

4. Sélectionnez **Enregistrer**.

## <a name="let-people-outside-the-organization-email-the-group"></a>Permettre aux personnes extérieures à l’organisation d’envoyer un e-mail au groupe

Cette option est idéale si vous souhaitez avoir une adresse e-mail d’entreprise telle que info@contoso.com.
 
1. Dans le centre d’administration, développez **Groupes**, puis cliquez sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groupes**</a>.

2. Cliquez sur le nom du groupe à gérer pour ouvrir le volet paramètres.

3. Dans la liste des groupes du centre d’administration, sélectionnez le nom du groupe à modifier, puis sous l’onglet Paramètres, sélectionnez **Autoriser les expéditeurs externes à envoyer un e-mail à ce groupe**.
    
4. Sélectionnez **Enregistrer**.

> [!NOTE]
> Il peut prendre jusqu’à 30 minutes avant que les utilisateurs extérieurs à l’organisation puissent envoyer un e-mail au groupe.

## <a name="permanently-delete-a-microsoft-365-group"></a>Supprimer définitivement un groupe Microsoft 365

Parfois, vous souhaiterez peut-être vider définitivement un groupe sans attendre l’expiration de la période de suppression réversible de 30 jours. Pour ce faire, démarrez PowerShell et exécutez la commande suivante pour obtenir l'ID d'objet du groupe.
 
 ```powershell
Get-AzureADMSDeletedGroup
```

Notez l’ID d’objet du groupe ou des groupes que vous souhaitez supprimer définitivement.
  
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

[Choisissez le domaine à utiliser lors de la création de Groupes Microsoft 365](../../solutions/choose-domain-to-create-groups.md)

[Autoriser les membres à envoyer en tant que ou pour le compte d’un groupe Microsoft 365](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md)

[Mettre à niveau les listes de distribution vers Groupes Microsoft 365](../manage/upgrade-distribution-lists.md)

[Gérer Groupes Microsoft 365 avec PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md)
