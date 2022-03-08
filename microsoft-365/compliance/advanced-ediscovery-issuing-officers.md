---
title: Gérer les responsables de l’émission dans Advanced eDiscovery
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
description: Vous pouvez ajouter des responsables de l’émission à l’échelle de l’organisation dans Advanced eDiscovery afin qu’ils soient ajoutés à n’importe quelle communication de garde dans n’importe quel cas de votre organisation.
ms.openlocfilehash: 21c5a3db9cb0cfefb26bc75537f298c7e8a5c09a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319182"
---
# <a name="manage-issuing-officers-in-advanced-ediscovery"></a>Gérer les responsables de l’émission dans Advanced eDiscovery

Lorsque vous ou d’autres personnes créez une notification de conservation ou tout autre type de communication qui est envoyé à un utilisateur qui est un dépositaire au cas où, vous devez spécifier un responsable de l’émission. La notification est envoyée au dépositaire au nom du responsable de l’émission spécifié. Par exemple, un technicien juridique de votre organisation peut être responsable de la création et de l’envoi de notifications de conservation aux dépositaires dans un cas. Dans ce scénario, l’avocat juridique peut spécifier un avocat dans l’organisation comme responsable de l’émission. Qui peut être spécifié en tant que responsable de l’émission ? Il existe deux types d’utilisateurs qui peuvent être sélectionnés en tant que responsable de l’émission pour la communication d’un dépositaire :

- Tout membre du cas spécifique dont la communication est envoyée au nom de.

- Tout utilisateur ajouté à la liste des responsables de l’émission à l’échelle de l’organisation. Les utilisateurs de cette liste peuvent être ajoutés à n’importe quel cas de votre organisation par un responsable de l’émission.

Cet article explique comment ajouter et supprimer des utilisateurs à la liste des responsables de l’émission à l’échelle de l’organisation.

## <a name="before-you-add-an-issuing-officer"></a>Avant d’ajouter un responsable de l’émission

- Vous devez être administrateur eDiscovery dans votre organisation pour ajouter ou supprimer des responsables de l’émission. Pour plus d’informations, [voir Attribuer des autorisations eDiscovery dans le Centre de conformité Microsoft 365](assign-ediscovery-permissions.md)  

- L’utilisateur ajouté en tant qu’agent d’émission doit avoir une boîte aux lettres active dans Microsoft 365 organisation.

- Votre organisation peut avoir un maximum de 15 responsables de l’émission. Les membres d’un cas qui peuvent être spécifiés comme responsable de l’émission ne sont pas comptabilisés dans cette limite. Cette limite s’applique uniquement au nombre d’utilisateurs qui peuvent être ajoutés à **la page Des** responsables de l’émission dans Advanced eDiscovery.

## <a name="add-an-issuing-officer"></a>Ajouter un responsable de l’émission

1. Dans la Centre de conformité Microsoft 365, [Advanced eDiscovery, puis](https://go.microsoft.com/fwlink/p/?linkid=2173764) cliquez **sur Advanced eDiscovery paramètres**.

   ![Sélectionner Advanced eDiscovery paramètres](..\media\HistoricalVersions1.png)

2. Dans la page **Paramètres**, sélectionnez l’onglet  Responsables de l’émission pour afficher la page Gérer les **responsables de l’émission**.

   ![Page paramètres des responsables de l’émission.](..\media\AeDIssuingOfficers1.png)

3. Cliquez **sur** Ajouter, puis recherchez et ajoutez un ou plusieurs utilisateurs à la liste des responsables de l’émission.

Une fois que vous avez ajouté des utilisateurs comme responsables de l’émission, vous ou d’autres utilisateurs pourrez spécifier ces utilisateurs en tant que responsables de l’émission des communications des dépositaires pour tous les cas de votre organisation. Pour plus d’informations sur la création de communications de dépositaire, voir [Créer une notification de conservation légale](create-hold-notification.md).

## <a name="remove-an-issuing-officer"></a>Supprimer un responsable de l’émission

1. Dans la Centre de conformité Microsoft 365, [Advanced eDiscovery, puis](https://go.microsoft.com/fwlink/p/?linkid=2173764) cliquez **sur Advanced eDiscovery paramètres**.

2. Dans la page **Paramètres**, sélectionnez l’onglet **Responsables de l’émission**.

3. Sélectionnez un ou plusieurs utilisateurs dans la liste des responsables de l’émission, puis cliquez sur **Supprimer**.

Une fois que vous avez supprimé des utilisateurs de la liste des responsables de l’émission, ces utilisateurs ne peuvent plus être spécifiés en tant que responsables de l’émission dans les nouvelles communications de dépositaire, sauf si l’utilisateur est membre du cas spécifique dont la communication est émise. En outre, la suppression d’un responsable de l’émission n’affectera pas les communications qui ont été envoyées avant que l’utilisateur ne soit supprimé de son rôle.
