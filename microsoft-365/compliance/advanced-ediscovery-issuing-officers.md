---
title: Gérer les agents émetteurs dans eDiscovery (Premium)
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
description: Vous pouvez ajouter des agents d’émission à l’échelle de l’organisation dans eDiscovery (Premium) afin qu’ils puissent être ajoutés à n’importe quelle communication de garde dans tous les cas de votre organisation.
ms.openlocfilehash: 63c1eb86037d6b94eee1fc0628e0d6fe3ad0a094
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67824793"
---
# <a name="manage-issuing-officers-in-ediscovery-premium"></a>Gérer les agents émetteurs dans eDiscovery (Premium)

Lorsque vous ou d’autres personnes créez une notification de suspension ou tout autre type de communication envoyé à un utilisateur qui est un gardien au cas où, vous devez spécifier un agent émetteur. La notification est envoyée au consignat pour le compte de l’agent émetteur spécifié. Par exemple, un parajuriste de votre organisation peut être responsable de la création et de l’envoi de notifications de conservation aux consignatateurs dans un cas. Dans ce scénario, le parajuriste peut spécifier un avocat dans l’organisation en tant qu’agent d’émission. Qui peut être spécifié en tant qu’agent d’émission? Il existe deux types d’utilisateurs qui peuvent être sélectionnés en tant qu’agent d’émission pour une communication de consignation :

- Tout membre du cas spécifique dont la communication est envoyée au nom de.

- Tout utilisateur ajouté à une liste d’agents d’émission à l’échelle de l’organisation. Les utilisateurs de cette liste peuvent être ajoutés à n’importe quel cas de votre organisation par un agent d’émission.

Cet article explique comment ajouter et supprimer des utilisateurs à la liste des agents d’émission à l’échelle de l’organisation.

## <a name="before-you-add-an-issuing-officer"></a>Avant d’ajouter un agent d’émission

- Vous devez être administrateur eDiscovery dans votre organisation pour ajouter ou supprimer des agents émetteurs. Pour plus d’informations, consultez [Affecter des autorisations eDiscovery dans le portail de conformité Microsoft Purview](assign-ediscovery-permissions.md)  

- L’utilisateur ajouté en tant qu’agent d’émission doit disposer d’une boîte aux lettres active dans votre organisation Microsoft 365.

- Votre organisation peut avoir un maximum de 15 agents émetteurs. Les membres d’un cas qui peuvent être spécifiés en tant qu’agent d’émission ne sont pas comptabilisés dans cette limite. Cette limite s’applique uniquement au nombre d’utilisateurs qui peuvent être ajoutés à la page **Agents d’émission** dans eDiscovery (Premium).

## <a name="add-an-issuing-officer"></a>Ajouter un agent d’émission

1. Dans le portail de conformité, accédez à [eDiscovery (Premium),](https://go.microsoft.com/fwlink/p/?linkid=2173764) puis cliquez sur les **paramètres eDiscovery (Premium**).

   ![Sélectionner les paramètres eDiscovery (Premium)](..\media\HistoricalVersions1.png)

2. Dans la page **Paramètres** , sélectionnez l’onglet **Agents d’émission** pour afficher la page **Gérer les agents émetteurs** .

   ![Page des paramètres des agents d’émission.](..\media\AeDIssuingOfficers1.png)

3. Cliquez sur **Ajouter** , puis recherchez et ajoutez un ou plusieurs utilisateurs à la liste des agents émetteurs.

Une fois que vous avez ajouté des utilisateurs en tant qu’agents d’émission, vous ou d’autres utilisateurs pourrez spécifier ces utilisateurs en tant qu’agent d’émission pour les communications de consignation, quel que soit le cas dans votre organisation. Pour plus d’informations sur la création de communications des consignats, consultez [Créer un avis de conservation légale](create-hold-notification.md).

## <a name="remove-an-issuing-officer"></a>Supprimer un agent d’émission

1. Dans le portail de conformité, accédez à [eDiscovery (Premium),](https://go.microsoft.com/fwlink/p/?linkid=2173764) puis cliquez sur les **paramètres eDiscovery (Premium**).

2. Dans la page **Paramètres** , sélectionnez l’onglet **Agents d’émission** .

3. Sélectionnez un ou plusieurs utilisateurs dans la liste des agents d’émission, puis cliquez sur **Supprimer**.

Une fois que vous avez supprimé des utilisateurs de la liste des agents d’émission, ces utilisateurs ne peuvent plus être spécifiés en tant qu’agent émetteur dans les nouvelles communications de consignation, sauf si l’utilisateur est membre du cas spécifique à partir duquel la communication est émise. En outre, la suppression d’un agent d’émission n’affecte pas les communications envoyées avant la suppression de l’utilisateur en tant qu’agent d’émission.
