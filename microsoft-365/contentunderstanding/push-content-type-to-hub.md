---
title: Envoyer (push) des types de contenu à un hub
description: Découvrez comment envoyer (push) des types de contenu à un hub
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: high
ms.openlocfilehash: 6dcd4bae638a9193e1fba2c0719339a5ddedc18d
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61372851"
---
# <a name="push-content-types-to-a-hub"></a>Envoyer (push) des types de contenu à un hub

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GyeV]  

</br>


Pour mettre les types de contenu importants systématiquement à la disposition des bibliothèques et des listes SharePoint, vous pouvez les pousser vers les hubs de votre choix. L’application des types de contenu les ajoute automatiquement à toutes les listes et bibliothèques créées sur les sites associés au hub, ainsi qu’à tous les nouveaux sites ajoutés à ce dernier. Cette fonctionnalité nécessite une licence [SharePoint Syntex](index.md).

Pour que cette fonctionnalité soit opérationnelle, les types de contenu envoyés par commande push doivent être déjà publiés.

Pour envoyer (push) des types de contenu à un hub

1. Dans le Centre d’administration SharePoint, développez **Services de contenu**, puis sélectionnez **Galerie de types de contenus**.
2. Sélectionnez le type de contenu à envoyer (push) à des hubs.
3. Sélectionnez **Modifier** dans la barre de commandes.
4. Sélectionnez sur **Choisir les sites hub**.
5. Sélectionnez les sites concentrateurs de votre choix, puis **OK**.
6. Cliquez sur **Enregistrer**.

Lors du premier envoi (push) d’un type de contenu à un hub existant et à ses sites associés, la mise à jour des paramètres sur le site peut prendre jusqu’à une heure à compter de la visite du hub ou des sites associés. Pour les nouvelles associations au hub, ce temps d’attente ne sera pas nécessaires, et la prise en compte des paramètres ne prendra que quelques minutes.

Une fois les paramètres mis à jour, le type de contenu avec ces paramètres sera disponible dans tout site récemment associé avec le hub dans quelques minutes. L’affichage de la bibliothèque par défaut sera changé en l’un de ces affichages créés automatiquement. Ensuite, le type de contenu est automatiquement ajouté à la nouvelle liste ou bibliothèque quelques minutes après la création de celle-ci. Un type de contenu envoyé (push) est ajouté à une bibliothèque de documents uniquement s’il provient directement ou indirectement du type de contenu Document. D’autre part, un type de contenu est ajouté à une liste uniquement s’il ne provient pas directement ou indirectement du type de contenu Document.

## <a name="see-also"></a>Voir aussi
