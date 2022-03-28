---
title: vue Microsoft 365 Lighthouse Windows page 365 (PC cloud)
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez la page Windows 365 (PC cloud).
ms.openlocfilehash: fa910e3de992aa3f3f76090f76a473a96aebc8fb
ms.sourcegitcommit: 9d563faeaa50b59b0b468dbb373d886e5270f58e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2022
ms.locfileid: "64387071"
---
# <a name="windows-365-cloud-pcs-page-overview"></a>vue Windows page 365 (PC cloud)  
  
Windows 365 est un service basé sur le cloud qui permet aux administrateurs Microsoft Endpoint Manager (MEM) de fournir et de gérer des PC Cloud pour leurs utilisateurs qui ont une licence Windows 365. Windows 365 est entièrement intégré à MEM pour la gestion des appareils et à Microsoft 365 Lighthouse pour la gestion par les partenaires des PC Cloud sur tous les clients.

Pour plus d’informations Windows 365, voir [Qu’est-ce Windows 365 ?](/windows-365/overview) Pour obtenir la liste des Windows 365 requises, voir [Requirements for Windows 365](/windows-365/enterprise/requirements).

> [!IMPORTANT]
> Vous devez vous rendre sur [MEM](https://go.microsoft.com/fwlink/p/?linkid=2150463) pour mettre en service des PC Cloud pour chaque client avant de pouvoir les gérer dans Le Monde. Vous ne pouvez pas l’approvisionnement à partir de l’intérieur de l’île.

Une fois que vous avez mis en service les PC Cloud pour votre client, la carte Windows 365 sur la page d’accueil Microsoft 365 fournit une brève alerte sur les PC cloud qui ont besoin d’action, telles que le nombre de PC cloud qui n’ont pas pu être mis en service et les échecs de connexion réseau Azure. Pour obtenir un état détaillé, sélectionnez le bouton sur la carte Windows 365 (ou sélectionnez **Windows 365** dans le volet de navigation de gauche) pour ouvrir la page Windows 365. À partir de cette page, vous pouvez obtenir une vue d’ensemble de l’état des PC Cloud affectés à vos clients, afficher la liste de tous les PC Cloud que vous gérez et les clients qui leur sont affectés, et afficher les connexions réseau Azure entre vos clients clients et Azure Active Directory (Azure AD) et leur état.

## <a name="overview-tab"></a>Onglet Overview

Sous l’onglet Vue d’ensemble, la barre de nombre d’annotations en couleur affiche le nombre total de PC Cloud ou de connexions réseau Azure sur tous les clients qui ont les états suivants : Échec des connexions réseau, Non mise en service, Échec de l’approvisionnement et désapprovisionnement bientôt.

Vous pouvez voir une répartition des statuts de l’ordinateur cloud pour chaque client dans la liste sous la barre d’annotations. Pour voir quels locataires ont des PC Cloud avec un état spécifique, sélectionnez cet état dans la barre d’annotations de nombre pour filtrer la liste. Pour voir les statuts du Cloud PC pour un ou plusieurs clients spécifiques, utilisez  le menu déroulant Clients pour filtrer la liste.

Pour obtenir des informations détaillées sur l’état d’un client particulier, sélectionnez une valeur sous l’une des colonnes d’état de ce client. Selon la colonne dans laquelle se trouve la valeur, l’onglet **Connexions réseau Azure** ou Tous les **PC cloud** s’ouvre et affiche plus d’informations.

L’onglet Vue d’ensemble inclut également les options suivantes :

- **Actualiser :** Sélectionnez pour récupérer les données de PC cloud les plus récentes.
- **Exporter :** Choisissez d’exporter les données cloud PC vers un Excel valeurs séparées par des virgules (.csv).
- **Recherche :** Entrez des mots clés pour localiser rapidement un PC Cloud spécifique dans la liste.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png" alt-text="Capture d’écran de Windows onglet Vue d’ensemble de 365." lightbox="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png":::

## <a name="all-cloud-pcs-tab"></a>Onglet Tous les PC cloud

Sous l’onglet Tous les PC Cloud, la barre d’annotations de nombre en couleur affiche le nombre total de PC Cloud sur tous les clients qui ont les statuts suivants : Mise en service, non mise en service, échec de l’approvisionnement et mise en service prochainement.

Vous pouvez afficher tous les PC cloud et leur état d’approvisionnement dans la liste sous la barre d’annotations. Les informations suivantes sont fournies :

- **Nom du PC cloud :** Nom attribué au PC cloud.
- **Client :** Client dans lequel un PC cloud a été provisioné.
- **Nom de l’appareil :** Nom de l’appareil Intune : identificateur unique pour un PC cloud.
- **Type de PC :** Type de PC cloud en fonction des références standard.
- **État :** État de mise en service du PC cloud.
- **Utilisateur :** Utilisateur pour lequel un PC Cloud a été mis en service ou a tenté d’être mis en service.

Pour voir quels locataires ont des PC Cloud avec un état d’approvisionnement spécifique, sélectionnez cet état dans la barre d’annotations de nombre pour filtrer la liste. Pour voir les **statuts** de mise en service de Cloud PC pour un ou plusieurs clients spécifiques, utilisez le menu déroulant Clients pour filtrer la liste.

Sélectionnez n’importe quel PC cloud dans la liste pour afficher plus de détails. Si vous avez besoin d’agir sur le PC cloud, des options s’offrent à vous pour afficher les stratégies d’approvisionnement des locataires et les détails de l’appareil dans Microsoft Endpoint Manager.

L’onglet Tous les PC cloud inclut également les options suivantes :

- **Actualiser :** Sélectionnez pour récupérer les données de PC cloud les plus récentes.
- **Exporter :** Choisissez d’exporter les données cloud PC vers un Excel valeurs séparées par des virgules (.csv).
- **Recherche :** Entrez des mots clés pour localiser rapidement un PC Cloud spécifique dans la liste.
- **Nouvelle tentative d’approvisionnement :** Sélectionnez 1 à 20 PC cloud dans la liste dont l’état de mise en service a **échoué, puis** sélectionnez cette option pour réessayer d’approvisionnement pour ces PC Cloud.

Pour obtenir la liste complète des états d’approvisionnement des PC cloud et leur description, voir vue d’ensemble de la gestion des appareils pour les PC [cloud](/windows-365/enterprise/device-management-overview#column-details) dans la bibliothèque de documentation Windows 365.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Capture d’écran Windows onglet 365 Tous les PC cloud." lightbox="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png":::

## <a name="azure-network-connections-tab"></a>Onglet Connexions réseau Azure

Sous l’onglet Connexions réseau Azure, la barre d’annotations de nombre de couleurs affiche le nombre total de connexions réseau Azure sur tous les clients qui ont les statuts suivants : Connexions réussies et Connexions échouées.

Dans la liste sous la barre d’annotations de nombre, vous pouvez afficher toutes les connexions réseau Azure et leur état de connexion.

Pour voir les connexions avec un état d’approvisionnement spécifique, sélectionnez cet état dans la barre d’annotations de nombre pour filtrer la liste. Pour voir les statuts de connexion d’un ou de plusieurs clients spécifiques, utilisez le menu déroulant Clients pour filtrer la liste.

Si vous devez prendre des mesures ou résoudre les problèmes d’une connexion dans la liste, sélectionnez Afficher les **détails de connexion dans Microsoft Endpoint Manager**.

L’onglet Connexions réseau Azure inclut également les options suivantes :

- **Actualiser :** Sélectionnez pour récupérer les données de connexion les plus récentes.
- **Exporter :** Sélectionnez cette sélection pour exporter les données de connexion vers Excel fichier de valeurs séparées par des virgules (.csv).
- **Recherche :** Entrez des mots clés pour localiser rapidement une connexion spécifique.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png" alt-text="Capture d’écran de l’onglet Connexions réseau Azure." lightbox="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png":::

## <a name="related-content"></a>Contenu associé

[Qu’est-ce que Windows 365 ?](/windows-365/overview) (article)\
[Windows vue d’ensemble de la gestion des appareils 365 pour les PC cloud](/windows-365/enterprise/device-management-overview) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)