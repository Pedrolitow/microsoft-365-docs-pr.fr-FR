---
title: Rapports Microsoft 365 dans le centre d’administration-utilisation des boîtes aux lettres
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: beffbe01-ce2d-4614-9ae5-7898868e2729
description: Découvrez comment obtenir un rapport d’utilisation des boîtes aux lettres pour connaître les activités des utilisateurs à l’aide d’une boîte aux lettres utilisateur.
ms.openlocfilehash: a866a586c9d36be03b39cb1c75be884eae3cb41b
ms.sourcegitcommit: 5c43e89ed94ad9fd1db049446383c65e548189b7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "44321992"
---
# <a name="microsoft-365-reports-in-the-admin-center---mailbox-usage"></a>Rapports Microsoft 365 dans le centre d’administration-utilisation des boîtes aux lettres

Le **rapport d’utilisation des boîtes aux lettres** fournit des informations sur les utilisateurs disposant d’une boîte aux lettres utilisateur et le niveau d’activité de chacun d’eux en fonction des e-mails envoyer, lire, créer un rendez-vous, envoyer une réunion, accepter une réunion, refuser une réunion et annuler une activité de réunion. Il fournit également des informations sur l'espace de stockage utilisé par chaque boîte aux lettres utilisateur et sur le nombre de boîtes aux lettres proches de leurs quotas de stockage. 
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, teams, Team communications ou Skype entreprise pour afficher des rapports. 
 
## <a name="how-to-get-to-the-mailbox-usage-report"></a>Comment accéder au rapport Utilisation des boîtes aux lettres ?

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la liste déroulante **Sélectionner un rapport** , **Exchange** sélectionnez \> **utilisation des boîtes aux lettres**Exchange.
  
## <a name="interpret-the-mailbox-usage-report"></a>Interpréter le rapport Utilisation des boîtes aux lettres

Pour obtenir un aperçu de l' **utilisation des boîtes aux lettres** de votre organisation, consultez les graphiques **Boîte aux lettres**, **Stockage** et **Quota**. 
  
|||
|:-----|:-----|
|1.  <br/> |Le rapport **Utilisation des boîtes aux lettres** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données de 28 jours maximum à compter de la date actuelle (pas la date à laquelle le rapport a été généré).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement les 24 à 48 heures.  <br/> |
|3.  <br/> |Le graphique Boîte aux lettres vous montre le nombre total de boîtes aux lettres utilisateur au sein de votre organisation ainsi que le nombre total de boîtes aux lettres actives pour un jour donné de la période de rapport. Une boîte aux lettres utilisateur est considérée comme étant active si elle avait un message électronique envoyer, lire, créer un rendez-vous, envoyer une réunion, accepter une réunion, refuser une réunion et annuler une activité de réunion.  <br/> |
|4.  <br/> |Le graphique **Stockage** présente l'espace de stockage utilisé au sein de votre organisation. Le graphique de stockage n’inclut pas les boîtes aux lettres d’archivage. Pour plus d’informations sur l’archivage à extension automatique, consultez la rubrique [Overview of Unlimited Archiving in Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/unlimited-archiving).<br/> |
|5.  <br/> | Le graphique **Quota** présente le nombre de boîtes aux lettres utilisateur dans chaque catégorie de quota. Il existe quatre catégories de quota :  <br/>  Satisfaisante - Nombre d'utilisateurs dont l'espace de stockage utilisé est inférieur au quota d'émission d'avertissement.  <br/>  Avertissement - Nombre d'utilisateurs dont l'espace de stockage utilisé est supérieur ou égal au quota d'émission d'avertissement, mais inférieur au quota d'interdiction d'envoi.  <br/>  Envoi impossible - Nombre d'utilisateurs dont l'espace de stockage utilisé est supérieur ou égal au quota d'interdiction d'envoi, mais inférieur au quota d'interdiction d'envoi et de réception.  <br/>  Envoi/réception impossible - Nombre d'utilisateurs dont l'espace de stockage utilisé est supérieur ou égal au quota d'interdiction d'envoi et de réception.  <br/> |
|6.  <br/> | Sur le graphique **Boîte aux lettres**, l'axe Y représente le nombre de boîtes aux lettres utilisateur.  <br/>  Dans le graphique **Stockage**, l'axe Y indique la quantité d'espace de stockage utilisée par les boîtes aux lettres utilisateur au sein de votre organisation.  <br/>  Sur le graphique **Quota**, l'axe Y représente le nombre de boîtes aux lettres utilisateur appartenant à chaque catégorie de quota de stockage.  <br/>  L'axe X sur les graphiques Boîte aux lettres et Stockage indique la plage de dates sélectionnée pour ce rapport particulier.  <br/>  L'axe X sur le graphique Quota indique la catégorie du quota.  <br/> |
|7.  <br/> |Vous pouvez filtrer les graphiques que vous voyez en sélectionnant un élément dans la légende.  <br/> |
|8.  <br/> | Le tableau offre le détail de l'utilisation des boîtes aux lettres au niveau des utilisateurs. Vous pouvez y ajouter des colonnes.  <br/> **Nom d'utilisateur** est l'adresse de courrier de l'utilisateur.  <br/> **Nom d'affichage** est le nom complet de l'utilisateur.  <br/> **Supprimé** se réfère aux boîtes aux lettres dont l'état actuel est Supprimé, mais qui ont été actives durant une partie de la période du rapport.  <br/> **Date de suppression** représente la date à laquelle la boîte aux lettres a été supprimée.  <br/> **Date de création** représente la date à laquelle la boîte aux lettres a été créée.  <br/> **Date de la dernière activité** fait référence à la date à laquelle la boîte aux lettres a enregistré une activité d'envoi ou de lecture de courrier électronique.  <br/> **Nombre d'éléments** fait référence au nombre total d'éléments dans la boîte aux lettres.  <br/> **Stockage utilisé (Mo)** fait référence à la quantité totale d'espace de stockage utilisée.  <br/> **Nombre** d’éléments supprimés fait référence au nombre total d’éléments supprimés dans la boîte aux lettres. <br/> La taille de l' **élément supprimé (Mo)** fait référence à la taille totale de tous les éléments supprimés dans la boîte aux lettres. <br/> **Quota d'émission d'avertissement (Mo)** fait référence à la limite de stockage atteinte lorsque le propriétaire de la boîte aux lettres reçoit un avertissement indiquant qu'il est sur le point d'atteindre le quota de stockage.  <br/> **Quota d'interdiction d'envoi (Mo)** fait référence à la limite de stockage atteinte lorsque la boîte aux lettres ne peut plus envoyer de courriers électroniques.  <br/> **Quota d'interdiction d'envoi/de réception (Mo)** fait référence à la limite de stockage atteinte lorsque la boîte aux lettres ne peut plus envoyer ou recevoir de courriers électroniques.  <br/>  Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **Masquer les détails de l’utilisateur dans les rapports** des [rapports d’activité dans le centre d’administration 365 de Microsoft](activity-reports.md).  <br/> |
|9.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier. csv Excel en sélectionnant le lien **Exporter** .  <br/> |
|||
   

