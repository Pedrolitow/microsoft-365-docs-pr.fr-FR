---
title: Gérer les règles de suppression de microsoft Defender pour les points de terminaison
description: Vous devrez peut-être empêcher l'apparition d'alertes dans le portail à l'aide de règles de suppression. Découvrez comment gérer vos règles de suppression dans Microsoft Defender pour point de terminaison.
keywords: gérer la suppression, les règles, le nom de la règle, l'étendue, l'action, les alertes, activer, désactiver
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: f1549512a02fe3af71d32c6b33c69cc705de99a8
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "51862126"
---
# <a name="manage-suppression-rules"></a>Gérer des règles de suppression

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


Dans certains scénarios, vous devrez peut-être supprimer l'apparition d'alertes dans le portail. Vous pouvez créer des règles de suppression pour des alertes spécifiques qui sont connues comme étant anodins, telles que des outils ou des processus connus dans votre organisation. Pour plus d'informations sur la suppression des alertes, voir [Supprimer des alertes.](manage-alerts.md)

Vous pouvez afficher la liste de toutes les règles de suppression et les gérer au même endroit. Vous pouvez également activer ou désactiver une règle de suppression d'alerte.


1. Dans le volet de navigation, sélectionnez **Suppression de l'alerte**  >  **paramètres.** La liste des règles de suppression créées par les utilisateurs de votre organisation s'affiche.

2. Sélectionnez une règle en cliquant sur la case à cocher en regard du nom de la règle.

3. Cliquez **sur Activer,** **Modifier la règle** ou Supprimer une **règle.** Lorsque vous modifiez une règle, vous pouvez choisir de publier des alertes qu'elle a déjà supprimées, que ces alertes correspondent ou non aux nouveaux critères. 


## <a name="view-details-of-a-suppression-rule"></a>Afficher les détails d'une règle de suppression

1. Dans le volet de navigation, sélectionnez **Suppression de l'alerte**  >  **paramètres.** La liste des règles de suppression créées par les utilisateurs de votre organisation s'affiche.

2. Cliquez sur un nom de règle. Les détails de la règle s’affichent. Vous verrez les détails de la règle tels que l’état, l’étendue, l’action, le nombre d’alertes correspondantes, créés par et la date de création de la règle. Vous pouvez également afficher les alertes associées et les conditions de règle.

## <a name="related-topics"></a>Voir aussi

- [Gérer des alertes](manage-alerts.md)
