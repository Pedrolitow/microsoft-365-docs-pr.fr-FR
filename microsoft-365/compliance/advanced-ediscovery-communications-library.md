---
title: Gérer les modèles de communications des dépositaires dans la bibliothèque de communications dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Vous pouvez ajouter des modèles de communications de dépositaire (comme un modèle de notification de conservation) dans Advanced eDiscovery afin qu’ils soient utilisés dans n’importe quel cas de votre organisation.
ms.openlocfilehash: 1b5be4a4a923050b43943e81ac64265e16749899
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330829"
---
# <a name="manage-custodian-communications-templates-in-advanced-ediscovery"></a>Gérer les modèles de communications des dépositaires dans Advanced eDiscovery

Lorsque vous ou d’autres utilisateurs créez une notification de conservation ou d’autres types de communications de consignateur, vous deviez créer le document de communication à partir de zéro à l’aide de l’éditeur de communications sous l’onglet **Communications** dans un cas Advanced eDiscovery. Nous avons maintenant publié une nouvelle fonctionnalité qui vous permet de créer des modèles de communication qui peuvent être utilisés pour créer des communications dans n’importe quel cas de votre organisation. Une fois les modèles de communication créés, ils peuvent être utilisés dans un cas. Cela signifie que les parajureurs ou les autres utilisateurs qui créent des communications de dépositaire n’ont pas besoin de partir de zéro pour créer une notification. Au lieu de cela, ils peuvent sélectionner un modèle pour créer la notification qui est envoyée à un dépositaire.

Cet article explique comment créer des modèles de communications à l’échelle de l’organisation et les sélectionner lors de la création d’une notification de dépositaire pour un cas Advanced eDiscovery spécifique.

## <a name="before-you-create-templates-in-the-communications-library"></a>Avant de créer des modèles dans la bibliothèque communications

- Vous devez être administrateur eDiscovery dans votre organisation pour ajouter ou supprimer des modèles dans la bibliothèque de communications dans Advanced eDiscovery. Pour plus d’informations, [voir Attribuer des autorisations eDiscovery dans le Centre de conformité Microsoft 365](assign-ediscovery-permissions.md)  

- Votre organisation peut avoir un maximum de 50 modèles dans la bibliothèque communications.

## <a name="create-a-communications-template"></a>Créer un modèle de communication

1. Dans la Centre de conformité Microsoft 365, [Advanced eDiscovery, puis](https://go.microsoft.com/fwlink/p/?linkid=2173764) cliquez **sur Advanced eDiscovery paramètres**.

   ![Sélectionner Advanced eDiscovery paramètres](..\media\HistoricalVersions1.png)

2. Dans la **page Paramètres**, sélectionnez **l’onglet Bibliothèque de** communications.

3. Dans la page **Bibliothèque de** communications, cliquez sur **Créer**.

4. Suivez la procédure pour créer une communication de dépositaire. Pour obtenir des instructions détaillées, voir [Créer une notification de mise en attente légale](create-hold-notification.md).

   > [!NOTE]
   > Les étapes de création d’un modèle de communication sont les mêmes que le flux de travail pour créer une notification dans un cas. La seule différence est que lorsque vous créez un modèle, vous ne spécifiez pas de responsable de l’émission et vous n’affectez pas de dépositaires. La spécification d’un responsable de l’émission et l’affectation de dépositaires sont réalisées lorsque vous utilisez un modèle de communication pour créer une notification de dépositaire pour un cas.

5. Une fois que vous avez créé un modèle, il s’affiche sur la page Bibliothèque **de** communications.

   ![Modèles affichés dans la bibliothèque communications](..\media\AeDCommunicationsLibrary1.png)

Vous ou d’autres administrateurs eDiscovery pouvez modifier un modèle de communication. Les modifications apportées à un modèle n’affectent ni ne modifient les notifications précédemment créées à l’aide de ce modèle. Ces modifications s’appliquent uniquement aux nouvelles notifications créées à l’aide du modèle mis à jour.

## <a name="use-a-communications-template-to-create-a-custodian-notification"></a>Utiliser un modèle de communication pour créer une notification de dépositaire

Une fois qu’un ou plusieurs modèles de communication ont été créés dans la bibliothèque de communications, ces modèles peuvent être sélectionnés pour créer une notification de dépositaire dans un cas.

Pour sélectionner un modèle :

1. Dans la Centre de conformité Microsoft 365, go to **eDiscovery > Advanced** to display the list of cases in your organization.

2. Sélectionnez un cas, cliquez sur **l’onglet Communications** , puis sur **Nouvelle communication**.

3. Dans la page **Communication** avec le nom, utilisez la liste de listes de sélection du modèle de **communication** pour sélectionner un modèle de communication à utiliser pour créer la notification du dépositaire.

   La liste des modèles de la bibliothèque de communication de votre organisation s’affiche dans la liste liste.

   ![Modèles de la bibliothèque communications affichés dans la liste liste.](..\media\AeDCommunicationsTemplates1.png)
