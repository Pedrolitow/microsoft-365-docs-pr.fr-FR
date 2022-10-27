---
title: Centre d'administration Microsoft 365 rapports d’utilisation des boîtes aux lettres
ms.author: kwekua
author: kwekua
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
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: beffbe01-ce2d-4614-9ae5-7898868e2729
description: Découvrez comment obtenir le rapport d’utilisation de la boîte aux lettres pour connaître les niveaux d’activité des utilisateurs disposant d’une boîte aux lettres utilisateur, ainsi que les informations de stockage et de quota pour chacun d’eux.
ms.openlocfilehash: 55b5fba9328b43d107a8c34a40a4a5e55aa8a1aa
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68723932"
---
# <a name="microsoft-365-reports-in-the-admin-center---mailbox-usage"></a>Rapports Microsoft 365 dans le Centre d’administration - Utilisation de la boîte aux lettres

Le **rapport d’utilisation de la boîte aux lettres** fournit des informations sur les utilisateurs disposant d’une boîte aux lettres utilisateur et le niveau d’activité de chacun en fonction de l’envoi, de la lecture, de la création d’un rendez-vous, de l’envoi d’une réunion, de l’acceptation d’une réunion, du refus de réunion et de l’annulation de l’activité de réunion. Il fournit également des informations sur l'espace de stockage utilisé par chaque boîte aux lettres utilisateur et sur le nombre de boîtes aux lettres proches de leurs quotas de stockage. Le rapport d’utilisation des boîtes aux lettres contient également des informations sur les boîtes aux lettres partagées entre les utilisateurs, en fournissant des données de stockage et de quota sur les boîtes aux lettres partagées.
 
## <a name="how-to-get-to-the-mailbox-usage-report"></a>Comment accéder au rapport Utilisation des boîtes aux lettres ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Sélectionnez **Afficher plus** sous **Email’activité**. 
3. Dans la liste déroulante **activité Email**, sélectionnez **Utilisation de la boîte aux lettres** **Exchange**\>.

## <a name="interpret-the-mailbox-usage-report"></a>Interpréter le rapport d’utilisation de la boîte aux lettres

Vous pouvez obtenir une vue de l’utilisation des boîtes aux lettres de votre organisation en examinant les graphiques **Boîte aux lettres**, **Stockage** et **Quota** .

Pour accéder aux informations de boîte aux lettres partagées, remplacez la sélection déroulante en haut à droite des graphiques par **Partagé**.  Si votre locataire n’a pas de boîtes aux lettres partagées, vous ne pourrez pas afficher les informations de boîte aux lettres partagées.

> [!NOTE]
> Actuellement, vous ne pouvez pas exporter les informations du graphique récapitulative pour les boîtes aux lettres partagées. Il s’agit d’un problème connu qui sera corrigé dans une prochaine itération.
  
:::image type="content" alt-text="Rapport d’utilisation des boîtes aux lettres." source="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png" lightbox="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png":::

Le rapport **Utilisation des boîtes aux lettres** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, la table affiche les données pendant jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré). Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures.

### <a name="the-mailbox-chart"></a>Graphique de boîtes aux lettres

Le graphique **Boîtes aux lettres** vous indique le nombre total de boîtes aux lettres d’utilisateur ou partagées dans votre organisation, ainsi que le nombre total de boîtes aux lettres utilisateur actives sur un jour donné de la période de rapport. Une boîte aux lettres utilisateur est considérée comme active si elle a reçu un e-mail d’envoi, de lecture, de création d’un rendez-vous, d’envoi de réunion, d’acceptation de réunion, de refus de réunion et d’annulation d’une activité de réunion.

> [!NOTE]
> Les boîtes aux lettres partagées n’ayant pas d’activité indépendante d’une boîte aux lettres utilisateur, seul un nombre de boîtes aux lettres partagées s’affiche lorsque ce type de boîte aux lettres est sélectionné.

Dans le graphique Boîte aux lettres :
- L’axe Y est le nombre de boîtes aux lettres utilisateur ou partagées. 
- L’axe X est la plage de dates sélectionnée pour ce rapport spécifique.

### <a name="the-storage-chart"></a>Graphique de stockage

Le graphique **Stockage** indique la quantité de stockage utilisée dans votre organisation par type de boîte aux lettres. Le graphique de stockage n’inclut pas les boîtes aux lettres d’archivage. Pour plus d’informations sur l’archivage à extension automatique, consultez [Vue d’ensemble de l’archivage à extension automatique dans Microsoft 365](../../compliance/autoexpanding-archiving.md).

Dans le graphique Stockage :
- L’axe Y est la quantité de stockage utilisée par les boîtes aux lettres utilisateur ou partagées dans votre organisation.
- L’axe X est la plage de dates sélectionnée pour ce rapport spécifique.

### <a name="the-quota-chart"></a>Graphique des quotas

Le graphique **Quota** indique le nombre de boîtes aux lettres utilisateur ou partagées dans chaque catégorie de quota. Il existe quatre catégories de quota : 
- Bon : nombre d’utilisateurs ou de boîtes aux lettres partagées dont le stockage utilisé est inférieur au quota « avertissement de problème ».
- Avertissement : nombre d’utilisateurs ou de boîtes aux lettres partagées dont le stockage utilisé est au-dessus ou au-dessus du quota « avertissement de problème », mais en dessous du quota « interdire l’envoi ».
- Impossible d’envoyer : nombre d’utilisateurs ou de boîtes aux lettres partagées dont le stockage utilisé est supérieur ou égal au quota d’envois interdits, mais en dessous du quota d’envoi/réception interdit.
- Impossible d’envoyer/recevoir : nombre d’utilisateurs ou de boîtes aux lettres partagées dont le stockage utilisé est supérieur ou égal au quota « interdire l’envoi/réception ».

Sur le graphique Quota :
- L’axe Y est le nombre de boîtes aux lettres utilisateur ou partagées dans chaque quota de stockage.
- L’axe X est la catégorie de quota.

Vous pouvez filtrer les graphiques que vous voyez en sélectionnant un élément dans la légende.

## <a name="mailbox-usage-per-mailbox-table"></a>Utilisation de boîte aux lettres par table de boîte aux lettres

Ce tableau présente une répartition de l’utilisation des boîtes aux lettres au niveau de chaque boîte aux lettres. Vous pouvez y ajouter des colonnes. 

|Élément|Description|
|:-----|:-----|
|Type de destinataire |Partagé ou Utilisateur. |
|Nom d'utilisateur |Adresse e-mail de l’utilisateur. |
|Nom d’affichage  |Nom complet de l’utilisateur. |
|Deleted |Boîte aux lettres dont l’état actuel est supprimé, mais qui était active pendant une partie de la période de création de rapports du rapport.|
|Date de suppression |Date à laquelle la boîte aux lettres a été supprimée. |
|Date de création | Date de création de la boîte aux lettres.  |
|Date de la dernière activité | Date de la dernière activité d’envoi ou de lecture d’e-mail dans la boîte aux lettres.   |
|nombre d'éléments|Nombre total d’éléments dans la boîte aux lettres. |
|Stockage utilisé (Mo)|Stockage total utilisé. |
|Nombre d’éléments supprimés|Nombre total d’éléments supprimés dans la boîte aux lettres. |
|Taille de l’élément supprimé (Mo)|Taille totale de tous les éléments supprimés dans la boîte aux lettres. |
|Quota d’avertissement de problème (Mo)|Limite de stockage lorsque le propriétaire de la boîte aux lettres reçoit un avertissement indiquant qu’il est sur le point d’atteindre le quota de stockage.  |
|Interdire le quota d’envoi (Mo)|Limite de stockage lorsque la boîte aux lettres ne peut plus envoyer d’e-mails. |
|Interdire le quota de réception d’envoi (Mo)|Limite de stockage lorsque la boîte aux lettres ne peut plus envoyer ou recevoir des e-mails. |
|Quota d’éléments récupérables (Mo)|Limite de stockage pour les éléments récupérables (supprimés) dans la boîte aux lettres lorsque la boîte aux lettres ne peut plus supprimer les e-mails. |
|Possède un Archive|Indique si une archive en ligne est activée pour la boîte aux lettres. |


Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **Masquer les détails de l’utilisateur dans les rapports** dans les [rapports d’activité dans le Centre d'administration Microsoft 365](activity-reports.md).

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.  <br/> :::image type="content" alt-text="Rapport d’utilisation de la boîte aux lettres : choisissez des colonnes." source="../../media/ea3d0b18-6ac6-41b0-9bb9-4844f040ea75.png":::

Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter** . 
