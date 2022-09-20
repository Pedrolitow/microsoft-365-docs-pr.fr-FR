---
title: Gérer les modèles de communication des consignatateurs dans la bibliothèque communications dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
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
description: Vous pouvez ajouter des modèles de communication de consignation (tels qu’un modèle de notification de conservation) dans eDiscovery (Premium) afin qu’ils puissent être utilisés dans tous les cas de votre organisation.
ms.openlocfilehash: ecc5dcf7d50ad8136e61fa9da86290cf343f4593
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67824925"
---
# <a name="manage-custodian-communications-templates-in-ediscovery-premium"></a>Gérer les modèles de communication des consignatateurs dans eDiscovery (Premium)

Lorsque vous ou d’autres utilisateurs créez une notification d’attente ou d’autres types de communications de consignation, vous deviez créer le document de communication à partir de zéro à l’aide de l’éditeur de communications sous l’onglet **Communications** dans un cas eDiscovery (Premium). À présent, nous avons publié une nouvelle fonctionnalité qui vous permet de créer des modèles de communication qui peuvent être utilisés pour créer des communications dans tous les cas de votre organisation. Une fois les modèles de communication créés, ils sont disponibles pour être utilisés dans un cas. Cela signifie que les parajuristes ou d’autres utilisateurs qui créent des communications de consignat ne doivent pas commencer de zéro pour générer une notification. Au lieu de cela, ils peuvent sélectionner un modèle pour générer la notification envoyée à un consignateur.

Cet article explique comment créer des modèles de communication à l’échelle de l’organisation et les sélectionner lors de la création d’une notification de consignation pour un cas eDiscovery (Premium) spécifique.

## <a name="before-you-create-templates-in-the-communications-library"></a>Avant de créer des modèles dans la bibliothèque communications

- Vous devez être administrateur eDiscovery dans votre organisation pour ajouter ou supprimer des modèles dans la bibliothèque Communications dans eDiscovery (Premium). Pour plus d’informations, consultez [Affecter des autorisations eDiscovery dans le portail de conformité Microsoft Purview](assign-ediscovery-permissions.md)  

- Votre organisation peut avoir un maximum de 50 modèles dans la bibliothèque communications.

## <a name="create-a-communications-template"></a>Créer un modèle de communication

1. Dans le portail de conformité, accédez à [eDiscovery (Premium),](https://go.microsoft.com/fwlink/p/?linkid=2173764) puis cliquez sur les **paramètres eDiscovery (Premium**).

   ![Sélectionner les paramètres eDiscovery (Premium)](..\media\HistoricalVersions1.png)

2. Dans la page **Paramètres** , sélectionnez l’onglet **Bibliothèque de communications** .

3. Dans la page **Bibliothèque de communications** , cliquez sur **Créer**.

4. Suivez la procédure pour créer une communication de consignation. Pour obtenir des instructions pas à pas, consultez [Créer une notification de conservation légale](create-hold-notification.md).

   > [!NOTE]
   > Les étapes de création d’un modèle de communication sont les mêmes que le flux de travail pour créer une notification dans un cas. La seule différence est que lorsque vous créez un modèle, vous ne spécifiez pas d’agent d’émission et vous n’affectez pas de consignatateurs. La spécification d’un agent émetteur et l’affectation de consignats sont effectuées lorsque vous utilisez un modèle de communication pour créer une notification de consignation pour un cas.

5. Une fois que vous avez créé un modèle, il s’affiche sur la page **bibliothèque de communications** .

   ![Modèles affichés dans la bibliothèque communications](..\media\AeDCommunicationsLibrary1.png)

Vous ou d’autres administrateurs eDiscovery pouvez modifier un modèle de communication. Les modifications apportées à un modèle n’affectent ni ne modifient les notifications qui ont été créées précédemment à l’aide de ce modèle. Ces modifications s’appliquent uniquement aux nouvelles notifications créées à l’aide du modèle mis à jour.

## <a name="use-a-communications-template-to-create-a-custodian-notification"></a>Utiliser un modèle de communication pour créer une notification de consignat

Une fois qu’un ou plusieurs modèles de communication ont été créés dans la bibliothèque communications, ces modèles peuvent être sélectionnés pour créer une notification de consignat dans un cas.

Pour sélectionner un modèle :

1. Dans le portail de conformité, accédez à **eDiscovery > Avancé** pour afficher la liste des cas dans votre organisation.

2. Sélectionnez un cas, cliquez sur l’onglet **Communications** , puis sur **Nouvelle communication**.

3. Dans la page **De communication du nom** , utilisez la liste déroulante **Sélectionner un modèle de communication** pour sélectionner un modèle de communication à utiliser pour créer la notification de consignat.

   La liste des modèles de la bibliothèque communication de votre organisation s’affiche dans la liste déroulante.

   ![Modèles de la bibliothèque Communications affichés dans la liste déroulante.](..\media\AeDCommunicationsTemplates1.png)
