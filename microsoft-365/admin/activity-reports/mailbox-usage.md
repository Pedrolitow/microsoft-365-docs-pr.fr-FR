---
title: Centre d'administration Microsoft 365'utilisation des boîtes aux lettres
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
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
description: Découvrez comment obtenir le rapport d’utilisation des boîtes aux lettres pour connaître les activités des utilisateurs  ayant une boîte aux lettres utilisateur.
ms.openlocfilehash: 6a28b6aed8721872a31af57d4c00cd82a89c06bc
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400893"
---
# <a name="microsoft-365-reports-in-the-admin-center---mailbox-usage"></a>Microsoft 365 dans le Centre d’administration - Utilisation des boîtes aux lettres

Le  rapport d’utilisation de la boîte aux lettres fournit des informations sur les utilisateurs ayant une boîte aux lettres utilisateur et le niveau d’activité de chacun d’entre eux en fonction de l’envoi, de la lecture, de la création d’un rendez-vous, de l’envoi d’une réunion, de l’acceptation d’une réunion, du refus de la réunion et de l’annulation de l’activité de réunion. Il fournit également des informations sur l'espace de stockage utilisé par chaque boîte aux lettres utilisateur et sur le nombre de boîtes aux lettres proches de leurs quotas de stockage. 
 
## <a name="how-to-get-to-the-mailbox-usage-report"></a>Comment accéder au rapport Utilisation des boîtes aux lettres ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Sélectionnez **Afficher plus sous** **Activité de messagerie**. 
3. Dans la liste de **listes** de listes de l’activité de messagerie, sélectionnez **Exchange’utilisation de** \> **la boîte aux lettres**.

## <a name="interpret-the-mailbox-usage-report"></a>Interpréter le rapport Utilisation des boîtes aux lettres

Pour obtenir un aperçu de l' **utilisation des boîtes aux lettres** de votre organisation, consultez les graphiques **Boîte aux lettres**, **Stockage** et **Quota**.
  
:::image type="content" alt-text="Rapport d’utilisation de boîte aux lettres." source="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png" lightbox="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png":::

|Item|Description|
|:-----|:-----|
|1.  |Le rapport **Utilisation des boîtes aux lettres** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date du jour (et non la date à laquelle le rapport a été généré). |
|2.  |Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures. |
|3.  |Le graphique Boîte aux lettres vous montre le nombre total de boîtes aux lettres utilisateur au sein de votre organisation ainsi que le nombre total de boîtes aux lettres actives pour un jour donné de la période de rapport. Une boîte aux lettres utilisateur est considérée comme active si elle a reçu un message électronique pour envoyer, lire, créer un rendez-vous, envoyer une réunion, accepter une réunion, refuser une réunion et annuler une activité de réunion. |
|4.  |Le graphique **Stockage** présente l'espace de stockage utilisé au sein de votre organisation. Stockage graphique n’inclut pas les boîtes aux lettres d’archivage. Pour plus d’informations sur l’archivage à extension automatique, voir Vue d’ensemble de l’archivage à [extension automatique dans Microsoft 365](../../compliance/autoexpanding-archiving.md). |
|5.  | Le graphique **Quota** présente le nombre de boîtes aux lettres utilisateur dans chaque catégorie de quota. Il existe quatre catégories de quota :  <br/>  Satisfaisante - Nombre d'utilisateurs dont l'espace de stockage utilisé est inférieur au quota d'émission d'avertissement.  <br/>  Avertissement - Nombre d'utilisateurs dont l'espace de stockage utilisé est supérieur ou égal au quota d'émission d'avertissement, mais inférieur au quota d'interdiction d'envoi.  <br/>  Envoi impossible - Nombre d'utilisateurs dont l'espace de stockage utilisé est supérieur ou égal au quota d'interdiction d'envoi, mais inférieur au quota d'interdiction d'envoi et de réception.  <br/>  Envoi/réception impossible - Nombre d'utilisateurs dont l'espace de stockage utilisé est supérieur ou égal au quota d'interdiction d'envoi et de réception. |
|6.  | Sur le graphique **Boîte aux lettres**, l'axe Y représente le nombre de boîtes aux lettres utilisateur.  <br/>  Dans le graphique **Stockage**, l'axe Y indique la quantité d'espace de stockage utilisée par les boîtes aux lettres utilisateur au sein de votre organisation.  <br/>  Sur le graphique **Quota**, l'axe Y représente le nombre de boîtes aux lettres utilisateur appartenant à chaque catégorie de quota de stockage.  <br/>  L'axe X sur les graphiques Boîte aux lettres et Stockage indique la plage de dates sélectionnée pour ce rapport particulier.  <br/>  L'axe X sur le graphique Quota indique la catégorie du quota. |
|7.  |Vous pouvez filtrer les graphiques que vous voyez en sélectionnant un élément dans la légende. |
|8.  | Le tableau offre le détail de l'utilisation des boîtes aux lettres au niveau des utilisateurs. Vous pouvez y ajouter des colonnes.  <br/> **Nom d'utilisateur** est l'adresse de courrier de l'utilisateur.  <br/> **Nom d'affichage** est le nom complet de l'utilisateur.  <br/> **Supprimé** se réfère aux boîtes aux lettres dont l'état actuel est Supprimé, mais qui ont été actives durant une partie de la période du rapport.  <br/> **Date de suppression** représente la date à laquelle la boîte aux lettres a été supprimée.  <br/> **Date de création** représente la date à laquelle la boîte aux lettres a été créée.  <br/> **Date de la dernière activité** fait référence à la date à laquelle la boîte aux lettres a enregistré une activité d'envoi ou de lecture de courrier électronique.  <br/> **Nombre d'éléments** fait référence au nombre total d'éléments dans la boîte aux lettres.  <br/> **Stockage utilisé (Mo)** fait référence à la quantité totale d'espace de stockage utilisée.  <br/> **Le nombre d’éléments** supprimés fait référence au nombre total d’éléments supprimés dans la boîte aux lettres. <br/> **La taille des éléments supprimés (Mo)** fait référence à la taille totale de tous les éléments supprimés dans la boîte aux lettres. <br/> **Quota d'émission d'avertissement (Mo)** fait référence à la limite de stockage atteinte lorsque le propriétaire de la boîte aux lettres reçoit un avertissement indiquant qu'il est sur le point d'atteindre le quota de stockage.  <br/> **Quota d'interdiction d'envoi (Mo)** fait référence à la limite de stockage atteinte lorsque la boîte aux lettres ne peut plus envoyer de courriers électroniques.  <br/> **Quota d'interdiction d'envoi/de réception (Mo)** fait référence à la limite de stockage atteinte lorsque la boîte aux lettres ne peut plus envoyer ou recevoir de courriers électroniques.  <br/> **Le quota d’éléments récupérables (Mo)** fait référence à la limite de stockage pour les éléments récupérables (supprimés) dans la boîte aux lettres lorsque la boîte aux lettres ne peut plus supprimer de messages électroniques.  <br/> **Indique si archive** en ligne est activée pour la boîte aux lettres.  <br/>  Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la **section Masquer les détails de l’utilisateur** dans la section Rapports d’activité du [Centre d'administration Microsoft 365](activity-reports.md). |
|9.  |**Sélectionnez Sélectionner des colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> :::image type="content" alt-text="Rapport d’utilisation de boîte aux lettres : choisir les colonnes." source="../../media/ea3d0b18-6ac6-41b0-9bb9-4844f040ea75.png":::|
|10. |Vous pouvez également exporter les données du rapport dans un Excel .csv, en sélectionnant le lien **Exporter**. |
|||
