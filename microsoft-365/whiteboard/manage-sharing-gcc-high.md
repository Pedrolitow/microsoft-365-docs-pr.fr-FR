---
title: Gérer le partage pour le tableau blanc Microsoft dans les environnements GCC High
ms.author: v-jdeweese
author: johnddeweese
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Découvrez comment gérer le partage pour le Tableau blanc Microsoft dans les environnements GCC High.
ms.openlocfilehash: 0cd4dc8e4bf39cfbaab79a0140bac544de9e9015
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66943373"
---
# <a name="manage-sharing-for-microsoft-whiteboard-in-gcc-high-environments"></a>Gérer le partage pour le tableau blanc Microsoft dans les environnements GCC High

>[!NOTE]
> Ces conseils s’appliquent aux environnements US Government Community Cloud (GCC) High.

L’expérience de partage diffère en fonction de l’appareil et du client utilisés. 

## <a name="share-in-teams-meetings"></a>Partager dans des réunions Teams

Lorsque vous partagez un tableau blanc dans une réunion Teams, le tableau blanc crée un lien de partage accessible à toute personne au sein de l’organisation. Il partage ensuite automatiquement le tableau blanc avec tous les utilisateurs in-tenants de la réunion.

>[!NOTE]
> Le partage externe pendant une réunion Teams n’est pas encore disponible, mais sera ajouté dans une version ultérieure.

|Scénario |Stockage et propriété |Paramètres de partage |Expérience de partage |
|---------|---------|---------|---------|
|Démarrer le tableau blanc à partir d’un ordinateur de bureau ou d’un appareil mobile |Stockage : OneDrive Entreprise<br><br>Propriétaire : Utilisateur qui crée le tableau blanc |N’est pas encore disponible. |Utilisateurs in-tenants : peut créer, afficher et collaborer<br><br>Utilisateurs externes : non encore disponible<br><br>Comptes d’appareil partagés : non encore disponibles |
|Démarrer le tableau blanc à partir d’un Surface Hub ou d’un Salles Microsoft Teams |N’est pas encore disponible. |         |         |

## <a name="add-as-a-tab-in-teams-channels-and-chats"></a>Ajouter sous la forme d’un onglet dans les canaux et les conversations Teams

Lorsque vous ajoutez un tableau blanc sous forme d’onglet dans un canal ou une conversation Teams, le tableau blanc crée un lien de partage accessible à tous les membres de l’organisation.

|Scénario  |Stockage et propriété  |Paramètres de partage  |Expérience de partage  |
|---------|---------|---------|---------|
|Ajouter le tableau blanc à un canal ou une conversation à partir d’un ordinateur de bureau ou d’un appareil mobile  |Stockage : OneDrive Entreprise<br><br>Propriétaire : Utilisateur qui crée le tableau blanc  |Non applicable  |Utilisateurs in-tenants : peuvent lancer, afficher et collaborer<br><br>Utilisateurs externes : non pris en charge  |

## <a name="create-and-share-in-whiteboard-native-clients"></a>Créer et partager dans des clients natifs de tableau blanc

Lorsque vous partagez un tableau blanc à partir de clients web, de bureau ou mobiles, vous pouvez choisir des personnes spécifiques. Vous pouvez également créer un lien de partage accessible à tous les membres de l’organisation. 

>[!NOTE]
> Le partage externe pendant une réunion Teams n’est pas encore disponible, mais sera ajouté dans une version ultérieure.

|Scénario  |Stockage et propriété  |Paramètres de partage  |Expérience de partage  |
|---------|---------|---------|---------|
|Créer le tableau blanc à partir d’un ordinateur de bureau ou d’un appareil mobile  |Stockage : OneDrive Entreprise<br><br>Propriétaire : Utilisateur qui crée le tableau blanc  |Non applicable  |Utilisateurs internes : peuvent partager au sein de leur organisation<br><br>Utilisateurs externes : le partage avec des utilisateurs externes n’est pas pris en charge pour l’instant  |
|Créer le tableau blanc à partir d’un Surface Hub  |Stockage : local<br><br>Propriétaire : Aucun  |Non applicable  |Utilisateurs dans le locataire (bientôt disponibles) : l’utilisateur pourra se connecter pour enregistrer et partager le tableau<br><br>Utilisateurs externes : le partage avec des utilisateurs externes n’est pas pris en charge pour l’instant |
|Créer le tableau blanc à partir de Salles Microsoft Teams  |N’est pas encore disponible.         |         |         |

## <a name="see-also"></a>Voir aussi

[Gérer l’accès au Tableau blanc - GCC High](manage-whiteboard-access-gcc-high.md)

[Gérer les données pour le tableau blanc - GCC High](manage-data-gcc-high.md)

[Gérer les clients pour le Tableau blanc - GCC High](manage-clients-gcc-high.md)
