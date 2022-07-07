---
title: Centre d'administration Microsoft 365 rapports d’utilisation de boîte aux lettres
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
description: Découvrez comment obtenir le rapport d’utilisation de la boîte aux lettres pour connaître les niveaux d’activité des utilisateurs disposant d’une boîte aux lettres utilisateur, ainsi que les informations de stockage et de quota pour chacun d’entre elles.
ms.openlocfilehash: c30cb6e9cc593aba14902d81904f3e765faa4231
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2022
ms.locfileid: "66663039"
---
# <a name="microsoft-365-reports-in-the-admin-center---mailbox-usage"></a>Rapports Microsoft 365 dans le centre d’administration - Utilisation de la boîte aux lettres

Le **rapport d’utilisation de la boîte aux lettres** fournit des informations sur les utilisateurs disposant d’une boîte aux lettres utilisateur et le niveau d’activité de chacun en fonction de l’envoi, de la lecture, de la création d’un rendez-vous, de l’envoi d’une réunion, de l’acceptation de la réunion, du refus de la réunion et de l’annulation de l’activité de réunion. Il fournit également des informations sur l'espace de stockage utilisé par chaque boîte aux lettres utilisateur et sur le nombre de boîtes aux lettres proches de leurs quotas de stockage. 
 
## <a name="how-to-get-to-the-mailbox-usage-report"></a>Comment accéder au rapport Utilisation des boîtes aux lettres ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Sélectionnez **Afficher plus** sous **Activité e-mail**. 
3. Dans la liste **déroulante Activité de messagerie**, sélectionnez **Utilisation de la boîte aux lettres** **Exchange**\>.

## <a name="interpret-the-mailbox-usage-report"></a>Interpréter le rapport Utilisation des boîtes aux lettres

Pour obtenir un aperçu de l' **utilisation des boîtes aux lettres** de votre organisation, consultez les graphiques **Boîte aux lettres**, **Stockage** et **Quota**.
  
:::image type="content" alt-text="Rapport d’utilisation de la boîte aux lettres." source="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png" lightbox="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png":::

Le rapport **Utilisation des boîtes aux lettres** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré). Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures.

Le graphique **boîte aux lettres** affiche le nombre total de boîtes aux lettres utilisateur dans votre organisation et le nombre total d’utilisateurs actifs un jour donné de la période de rapport. Une boîte aux lettres utilisateur est considérée comme active si elle avait un e-mail d’envoi, de lecture, de création de rendez-vous, d’envoi de réunion, d’acceptation de réunion, de refus de réunion et d’annulation de l’activité de réunion.

Le graphique **Stockage** présente l'espace de stockage utilisé au sein de votre organisation. Le graphique de stockage n’inclut pas les boîtes aux lettres d’archivage. Pour plus d’informations sur le développement automatique de l’archivage, consultez [Vue d’ensemble de l’archivage à extension automatique dans Microsoft 365](../../compliance/autoexpanding-archiving.md).

Le graphique **Quota** présente le nombre de boîtes aux lettres utilisateur dans chaque catégorie de quota. Il existe quatre catégories de quota : 
- Bon : le nombre d’utilisateurs dont le stockage est utilisé est inférieur au quota d'« avertissement de problème ».
- Avertissement : le nombre d’utilisateurs dont le stockage utilisé est égal ou supérieur au quota d'« avertissement de problème », mais en dessous du quota « interdire l’envoi ».
- Impossible d’envoyer : nombre d’utilisateurs dont le stockage utilisé est égal ou supérieur au quota d’envoi interdit, mais inférieur au quota d’envoi/réception d’interdiction.
- Impossible d’envoyer/recevoir : nombre d’utilisateurs dont le stockage utilisé est égal ou supérieur au quota « interdire l’envoi/réception ».

Sur le graphique Boîte aux lettres, l'axe Y représente le nombre de boîtes aux lettres utilisateur. 

Dans le graphique Stockage, l'axe Y indique la quantité d'espace de stockage utilisée par les boîtes aux lettres utilisateur au sein de votre organisation.

L'axe X sur les graphiques Boîte aux lettres et Stockage indique la plage de dates sélectionnée pour ce rapport particulier.

Sur le graphique Quota, l'axe Y représente le nombre de boîtes aux lettres utilisateur appartenant à chaque catégorie de quota de stockage. Et l’axe X est la catégorie de quota.

Vous pouvez filtrer les graphiques que vous voyez en sélectionnant un élément dans la légende.

Le tableau offre le détail de l'utilisation des boîtes aux lettres au niveau des utilisateurs. Vous pouvez y ajouter des colonnes. 

|Item|Description|
|:-----|:-----|
|Nom d’utilisateur |Adresse e-mail de l’utilisateur. |
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


Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **Masquer les détails de l’utilisateur dans la section Rapports** dans le Centre d'administration Microsoft 365](activity-reports.md.

**Sélectionnez Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.  <br/> :::image type="content" alt-text="Rapport d’utilisation de la boîte aux lettres : choisissez des colonnes." source="../../media/ea3d0b18-6ac6-41b0-9bb9-4844f040ea75.png":::

Vous pouvez également exporter les données du rapport dans un fichier Excel .csv, en sélectionnant le lien **Exporter** . 