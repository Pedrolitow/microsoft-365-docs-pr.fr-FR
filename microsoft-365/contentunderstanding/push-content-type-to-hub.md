---
title: Envoyer (push) des types de contenu à un hub
description: Découvrez comment envoyer (push) des types de contenu à un hub.
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: shrganguly
manager: serdars
audience: admin
ms.topic: article
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: admindeeplinkSPO
ms.localizationpriority: high
ms.openlocfilehash: b38cd152f83da1713f03b6b22e37946a5603df41
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662158"
---
# <a name="push-content-types-to-a-hub"></a>Envoyer (push) des types de contenu à un hub

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GyeV]  

</br>


Pour mettre les types de contenu importants systématiquement à la disposition des bibliothèques et des listes SharePoint, vous pouvez les pousser vers les hubs de votre choix. L’application des types de contenu les ajoute automatiquement à toutes les listes et bibliothèques créées sur les sites associés au hub, ainsi qu’à tous les nouveaux sites ajoutés à ce dernier. Cette fonctionnalité nécessite une [licence Microsoft Syntex](syntex-licensing.md).

Pour que cette fonctionnalité soit opérationnelle, les types de contenu envoyés par commande push doivent être déjà publiés.

Pour envoyer (push) des types de contenu à un hub

1. Dans le Centre d’administration SharePoint, développez **services de contenu**, puis sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185074" target="_blank">**Galerie de types de contenu**</a>.
2. Sélectionnez le type de contenu à envoyer (push) à des hubs.
3. Sélectionnez **Modifier** dans la barre de commandes.
4. Sélectionnez sur **Choisir les sites hub**.
5. Sélectionnez les sites concentrateurs de votre choix, puis **OK**.
6. Cliquez sur **Enregistrer**.

When you push a content type to an existing hub & its existing associated sites for the first time, it can take up to an hour from when the hub or associated sites are visited, for the settings to update in the site. Any new associations to the hub won't require this wait and will have the settings reflected in a few minutes.

Une fois les paramètres mis à jour, le type de contenu avec ces paramètres sera disponible dans tout site récemment associé avec le hub dans quelques minutes. L’affichage de la bibliothèque par défaut sera changé en l’un de ces affichages créés automatiquement. S’il existe plusieurs types de contenu placés dans la même bibliothèque, le dernier (en fonction de l’ordre d’action du déplacement de ces types de contenu vers le hub appartenant à cette bibliothèque) est celui qui est défini en tant qu’affichage par défaut. Ensuite, le type de contenu est automatiquement ajouté à la nouvelle liste ou bibliothèque quelques minutes après la création de celle-ci. Un type de contenu envoyé (push) est ajouté à une bibliothèque de documents uniquement s’il provient directement ou indirectement du type de contenu Document. D’autre part, un type de contenu est ajouté à une liste uniquement s’il ne provient pas directement ou indirectement du type de contenu Document.


