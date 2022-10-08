---
title: Centre d'administration Microsoft 365 rapports d’utilisation de boîte aux lettres
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: beffbe01-ce2d-4614-9ae5-7898868e2729
description: Découvrez comment obtenir le rapport d’utilisation de la boîte aux lettres pour connaître les niveaux d’activité des utilisateurs disposant d’une boîte aux lettres utilisateur, ainsi que les informations de stockage et de quota pour chacun d’entre elles.
ms.openlocfilehash: 882a6ec5fb889a145cc9c9ec939948725a10f57f
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68192770"
---
# <a name="microsoft-365-reports-in-the-admin-center---mailbox-usage"></a>Rapports Microsoft 365 dans le centre d’administration - Utilisation de la boîte aux lettres

Le **rapport d’utilisation de la boîte aux lettres** fournit des informations sur les utilisateurs disposant d’une boîte aux lettres utilisateur et le niveau d’activité de chacun en fonction de l’envoi, de la lecture, de la création d’un rendez-vous, de l’envoi d’une réunion, de l’acceptation de la réunion, du refus de la réunion et de l’annulation de l’activité de réunion. Il fournit également des informations sur l'espace de stockage utilisé par chaque boîte aux lettres utilisateur et sur le nombre de boîtes aux lettres proches de leurs quotas de stockage. Le rapport d’utilisation des boîtes aux lettres contient également des informations sur les boîtes aux lettres partagées entre les utilisateurs, fournissant des données de stockage et de quota sur les boîtes aux lettres partagées.
 
## <a name="how-to-get-to-the-mailbox-usage-report"></a>Comment accéder au rapport Utilisation des boîtes aux lettres ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Sélectionnez **Afficher plus** sous **Email activité**. 
3. Dans la liste **déroulante Email activité**, sélectionnez Utilisation de la **boîte aux lettres** **Exchange**\>.

## <a name="interpret-the-mailbox-usage-report"></a>Interpréter le rapport d’utilisation de la boîte aux lettres

Vous pouvez obtenir une vue de l’utilisation de la boîte aux lettres de votre organisation en consultant les graphiques **boîte aux lettres**, **Stockage** et **Quota** .

Pour accéder aux informations de boîte aux lettres partagées, remplacez la sélection déroulante en haut à droite des graphiques par **Shared**.  Si votre locataire n’a pas de boîtes aux lettres partagées, vous ne pourrez pas afficher les informations de boîte aux lettres partagées.

> [!NOTE]
> Actuellement, vous ne pourrez pas exporter les informations du graphique récapitulatif pour les boîtes aux lettres partagées. Il s’agit d’un problème connu qui sera corrigé dans une itération ultérieure.
  
:::image type="content" alt-text="Rapport d’utilisation de la boîte aux lettres." source="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png" lightbox="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png":::

Le rapport **Utilisation des boîtes aux lettres** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré). Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures.

### <a name="the-mailbox-chart"></a>Graphique de boîte aux lettres

Le graphique **des boîtes aux lettres** affiche le nombre total de boîtes aux lettres utilisateur ou partagées dans votre organisation, ainsi que le nombre total de boîtes aux lettres utilisateur actives un jour donné de la période de création de rapports. Une boîte aux lettres utilisateur est considérée comme active si elle avait un e-mail d’envoi, de lecture, de création de rendez-vous, d’envoi de réunion, d’acceptation de réunion, de refus de réunion et d’annulation de l’activité de réunion.

> [!NOTE]
> Les boîtes aux lettres partagées n’ayant pas d’activité indépendante d’une boîte aux lettres utilisateur, seul un nombre de boîtes aux lettres partagées s’affiche lorsque ce type de boîte aux lettres est sélectionné.

Dans le graphique des boîtes aux lettres :
- L’axe Y correspond au nombre de boîtes aux lettres utilisateur ou partagées. 
- L’axe X est la plage de dates sélectionnée pour ce rapport spécifique.

### <a name="the-storage-chart"></a>Graphique de stockage

Le graphique **Stockage** affiche la quantité de stockage utilisée dans votre organisation par type de boîte aux lettres. Le graphique de stockage n’inclut pas les boîtes aux lettres d’archivage. Pour plus d’informations sur le développement automatique de l’archivage, consultez [Vue d’ensemble de l’archivage à extension automatique dans Microsoft 365](../../compliance/autoexpanding-archiving.md).

Dans le graphique stockage :
- L’axe Y correspond à la quantité de stockage utilisée par les boîtes aux lettres utilisateur ou partagées dans votre organisation.
- L’axe X est la plage de dates sélectionnée pour ce rapport spécifique.

### <a name="the-quota-chart"></a>Graphique des quotas

Le graphique **quota** affiche le nombre de boîtes aux lettres utilisateur ou partagées dans chaque catégorie de quota. Il existe quatre catégories de quota : 
- Bon : le nombre d’utilisateurs ou de boîtes aux lettres partagées dont le stockage utilisé est inférieur au quota d'« avertissement de problème ».
- Avertissement : nombre d’utilisateurs ou de boîtes aux lettres partagées dont le stockage utilisé est égal ou supérieur au quota « avertissement de problème », mais en dessous du quota « interdire l’envoi ».
- Impossible d’envoyer : nombre d’utilisateurs ou de boîtes aux lettres partagées dont le stockage utilisé est égal ou supérieur au quota d’envoi interdit, mais inférieur au quota d’envoi/réception interdit.
- Impossible d’envoyer/recevoir : nombre d’utilisateurs ou de boîtes aux lettres partagées dont le stockage utilisé est égal ou supérieur au quota « interdire l’envoi/réception ».

Dans le graphique des quotas :
- L’axe Y correspond au nombre de boîtes aux lettres utilisateur ou partagées dans chaque quota de stockage.
- L’axe X est la catégorie de quota.

Vous pouvez filtrer les graphiques que vous voyez en sélectionnant un élément dans la légende.

## <a name="mailbox-usage-per-mailbox-table"></a>Utilisation de la boîte aux lettres par table de boîtes aux lettres

Ce tableau affiche une répartition de l’utilisation de la boîte aux lettres au niveau de chaque boîte aux lettres. Vous pouvez y ajouter des colonnes. 

|Élément|Description|
|:-----|:-----|
|Type de destinataire |Partagé ou utilisateur. |
|Nom d'utilisateur |Adresse e-mail de l’utilisateur. |
|Nom d’affichage  |Nom complet de l’utilisateur. |
|Deleted |Boîte aux lettres dont l’état actuel est supprimé, mais qui était actif pendant une partie de la période de rapport du rapport.|
|Date de suppression |Date de suppression de la boîte aux lettres. |
|Date de création | Date de création de la boîte aux lettres.  |
|Date de la dernière activité | Date de la dernière activité d’envoi ou de lecture de la boîte aux lettres.   |
|nombre d'éléments|Nombre total d’éléments dans la boîte aux lettres. |
|Stockage utilisé (Mo)|Stockage total utilisé. |
|Nombre d’éléments supprimés|Nombre total d’éléments supprimés dans la boîte aux lettres. |
|Taille de l’élément supprimé (Mo)|Taille totale de tous les éléments supprimés dans la boîte aux lettres. |
|Émission d’un quota d’avertissement (Mo)|Limite de stockage lorsque le propriétaire de la boîte aux lettres reçoit un avertissement indiquant qu’il est sur le point d’atteindre le quota de stockage.  |
|Interdire le quota d’envoi (Mo)|Limite de stockage lorsque la boîte aux lettres ne peut plus envoyer d’e-mails. |
|Interdire le quota de réception d’envoi (Mo)|Limite de stockage lorsque la boîte aux lettres ne peut plus envoyer ou recevoir des e-mails. |
|Quota d’éléments récupérables (Mo)|Limite de stockage pour les éléments récupérables (supprimés) dans la boîte aux lettres lorsque la boîte aux lettres ne peut plus supprimer les e-mails. |
|Possède un Archive|Indique si une archive en ligne est activée pour la boîte aux lettres. |


Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **Masquer les détails de l’utilisateur dans la** section [Rapports d’activité du Centre d'administration Microsoft 365](activity-reports.md).

**Sélectionnez Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.  <br/> :::image type="content" alt-text="Rapport d’utilisation de la boîte aux lettres : choisissez des colonnes." source="../../media/ea3d0b18-6ac6-41b0-9bb9-4844f040ea75.png":::

Vous pouvez également exporter les données du rapport dans un fichier Excel .csv, en sélectionnant le lien **Exporter** . 
