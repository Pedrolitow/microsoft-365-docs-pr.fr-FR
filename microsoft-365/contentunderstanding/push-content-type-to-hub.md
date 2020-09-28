---
title: Envoi de types de contenu vers un concentrateur
description: Découvrez comment diffuser des types de contenu vers un concentrateur
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: a852207bfd1a2a7643ce8895a533371d194954cf
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48295900"
---
# <a name="push-content-types-to-a-hub"></a>Envoi de types de contenu vers un concentrateur

Pour rendre les types de contenu importants plus cohérents disponibles pour les bibliothèques et les listes SharePoint, vous pouvez les envoyer aux concentrateurs de votre choix. Cela les ajoute automatiquement aux nouvelles listes et bibliothèques créées sur les sites associés au concentrateur, ainsi qu’aux nouveaux sites ajoutés au Hub.

Pour que cette fonctionnalité fonctionne, les types de contenu en cours d’envoi doivent déjà être publiés.

Pour envoyer des types de contenu vers des concentrateurs

1. Dans le centre d’administration SharePoint, développez **services de contenu**, puis cliquez sur Galerie de **types de contenu**.

2. Cliquez sur le type de contenu que vous souhaitez envoyer aux hubs.

3. Cliquez sur **modifier** dans la barre de commandes.
 
4. Cliquez sur **choisir des sites hub**.
 
5. Sélectionnez les sites hub souhaités, puis cliquez sur **OK**.
 
6. Cliquez sur **Enregistrer**.

Lorsque vous transmettez un type de contenu à un concentrateur existant & les sites associés existants pour la première fois, il peut prendre jusqu’à une heure après avoir consulté le Hub ou les sites associés pour que les paramètres soient mis à jour dans le site. Les nouvelles associations au hub ne nécessitent pas cette attente et les paramètres seront reflétés dans quelques minutes. 

Une fois cette configuration effectuée, le type de contenu avec ces paramètres sera disponible dans tout site nouvellement associé avec le Hub dans quelques minutes. Une fois la nouvelle liste ou bibliothèque créée, le type de contenu est ajouté automatiquement dans quelques minutes de création. Un type de contenu push est ajouté à une bibliothèque de documents uniquement s’il est dérivé directement ou indirectement du type de contenu document, et un type de contenu est ajouté à une liste uniquement s’il ne dérive pas directement ou indirectement du type de contenu de document.

## <a name="see-also"></a>Voir aussi



  






