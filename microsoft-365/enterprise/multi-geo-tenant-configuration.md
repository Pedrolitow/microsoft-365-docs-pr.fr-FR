---
title: Configuration de client multigéographique dans Microsoft 365
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection:
- SPO_Content
- Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: Dans cet article, découvrez l’ajout d’emplacements satellites et la configuration de votre client pour Microsoft 365 Multi-Geo.
ms.openlocfilehash: a656dc718dfaac14d87ea0ae5e1fa792d41a0648
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68804683"
---
# <a name="microsoft-365-multi-geo-_tenant_-configuration"></a>Configuration du _client_ multigéographique Microsoft 365

Avant de configurer votre _locataire_ pour Microsoft 365 Multi-Geo, assurez-vous d’avoir lu [Plan for Microsoft 365 Multi-Geo](plan-for-multi-geo.md).

Pour suivre les étapes décrites dans cet article, vous avez besoin d’une liste des emplacements _Geography_ que vous souhaitez activer en tant qu’emplacements _géographiques satellites_ , ainsi que des utilisateurs de test que vous souhaitez approvisionner pour ces emplacements.

Toutes les charges de travail multigéographiques ne nécessitent pas une configuration pilotée par le client.

## <a name="configuring-exchange-online-for-multi-geo"></a>Configuration de Exchange Online pour multigéographique

Aucune configuration pilotée par le client n’est requise pour préparer Exchange Online dans un _locataire multigéographique_. Un client peut utiliser toutes les zones géographiques avec Exchange Online dès que la multigéographique a été activée dans Exchange Online pour son _locataire_.

## <a name="configuring-microsoft-teams-for-multi-geo"></a>Configuration de Microsoft Teams pour multigéographique

Aucune configuration pilotée par le client n’est requise pour préparer Microsoft Teams dans un locataire multigéographique. Un client peut utiliser toutes les zones géographiques avec Microsoft Teams dès que la multigéographique a été activée dans Microsoft Teams pour son _locataire_.

## <a name="configuring-sharepoint-online-and-onedrive-for-business-for-multi-geo"></a>Configuration de SharePoint Online et OneDrive Entreprise pour multigéographique

Si vous souhaitez stocker des données dans une zone géographique particulière, celle-ci doit être configurée pour SharePoint Online et OneDrive à l’avance.

Une fois que multigéographique a été activé pour votre _locataire_ dans SharePoint Online et OneDrive Entreprise, l’onglet **Emplacements géographiques** devient disponible dans les centres d’administration OneDrive Entreprise et SharePoint Online. Si vous ne voyez pas l’onglet **Emplacements géographiques** , votre _locataire_ n’a pas encore fini d’être activé pour multigéographique.

Pour ajouter chaque emplacement géographique satellite pour SharePoint et OneDrive où vous souhaitez stocker des données :

1. Ouvrez le Centre d’administration SharePoint. et accédez à **Emplacements géographiques**.
1. Sélectionnez **Ajouter un emplacement**.
1. Sélectionnez l’emplacement que vous souhaitez ajouter, puis sélectionnez **Suivant**.
1. Tapez le domaine que vous souhaitez utiliser avec l’emplacement géographique, puis sélectionnez **Ajouter**.
1. Sélectionnez **Fermer**.

L’approvisionnement peut prendre de quelques heures à 72 heures, en fonction de la taille de votre _locataire_. Une fois l’approvisionnement d’un emplacement _géographique satellite_ terminé, vous recevrez une confirmation par e-mail. Lorsque le nouvel emplacement _Geography_ apparaît en bleu sur la carte sous l’onglet Emplacements géographiques dans le Centre d’administration OneDrive et SharePoint, vous pouvez continuer à définir l’emplacement de données préféré des utilisateurs sur cet emplacement _Géographique_ .

> [!IMPORTANT]
> Votre nouvel emplacement _géographique satellite_ sera configuré avec les paramètres par défaut. Cela vous permet de configurer cet emplacement _géographique satellite_ en fonction de vos besoins de conformité locaux.
