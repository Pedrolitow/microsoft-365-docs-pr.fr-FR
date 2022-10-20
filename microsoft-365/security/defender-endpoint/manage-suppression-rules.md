---
title: Gérer les règles de suppression Microsoft Defender pour point de terminaison
description: Vous devrez peut-être empêcher l’affichage d’alertes dans le portail à l’aide de règles de suppression. Découvrez comment gérer vos règles de suppression dans Microsoft Defender pour point de terminaison.
keywords: gérer la suppression, les règles, le nom de la règle, l’étendue, l’action, les alertes, activer, désactiver
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 6ac4f0dfe292d6b2a9b7d6baf185d001b38a8e2b
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68630334"
---
# <a name="manage-suppression-rules"></a>Gérer des règles de suppression

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Il peut y avoir des scénarios dans lesquels vous devez supprimer l’affichage des alertes dans le portail. Vous pouvez créer des règles de suppression pour des alertes spécifiques qui sont connues pour être inoffensifs, telles que des outils ou des processus connus dans votre organisation. Pour plus d’informations sur la suppression des alertes, consultez [Supprimer les alertes](manage-alerts.md).

Vous pouvez afficher la liste de toutes les règles de suppression et les gérer au même endroit. Vous pouvez également activer ou désactiver une règle de suppression d’alerte.


1. Dans le volet de navigation, sélectionnez **Suppression des alertes** de **règles** \> de **paramètres** \> de points de terminaison.\> La liste des règles de suppression créées par les utilisateurs de votre organisation s’affiche.

2. Sélectionnez une règle en cliquant sur la case à cocher en regard du nom de la règle.

3. Cliquez **sur Activer la règle**, **Modifier la règle** ou Supprimer la  **règle**. Lorsque vous apportez des modifications à une règle, vous pouvez choisir de libérer les alertes qu’elle a déjà supprimées, que ces alertes correspondent ou non aux nouveaux critères. 


## <a name="view-details-of-a-suppression-rule"></a>Afficher les détails d’une règle de suppression

1. Dans le volet de navigation, sélectionnez **Suppression des alertes** de **règles** \> de **paramètres** \> de points de terminaison.\> La liste des règles de suppression créées par les utilisateurs de votre organisation s’affiche.

2. Cliquez sur un nom de règle. Les détails de la règle s’affichent. Vous verrez les détails de la règle, tels que l’état, l’étendue, l’action, le nombre d’alertes correspondantes, créées par et la date de création de la règle. Vous pouvez également afficher les alertes associées et les conditions de règle.

## <a name="related-topics"></a>Voir aussi

- [Gérer des alertes](manage-alerts.md)
