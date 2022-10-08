---
title: Vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: katmartin
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez la page Windows 365 (PC cloud).
ms.openlocfilehash: ddc3897f2ab4c6632724fffeb4409ebfa9869894
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68201900"
---
# <a name="overview-of-the-windows-365-cloud-pcs-page-in-microsoft-365-lighthouse"></a>Vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse  
  
Windows 365 est un service cloud qui permet aux administrateurs Microsoft Endpoint Manager (MEM) de provisionner et de gérer des PC cloud pour leurs utilisateurs disposant d’une licence Windows 365. Windows 365 est entièrement intégré à MEM pour la gestion des appareils et à Microsoft 365 Lighthouse pour la gestion des partenaires des PC cloud sur tous leurs locataires clients.

Pour plus d’informations sur Windows 365, voir [Qu’est-ce que Windows 365 ?](/windows-365/overview) Pour obtenir la liste des exigences de Windows 365, consultez [La configuration requise pour Windows 365](/windows-365/enterprise/requirements).

> [!IMPORTANT]
> Vous devez accéder à [MEM](https://go.microsoft.com/fwlink/p/?linkid=2150463) pour provisionner des PC cloud pour chaque locataire client avant de pouvoir les gérer dans Lighthouse. Vous ne pouvez pas approvisionner à partir de Lighthouse.

Une fois que vous avez approvisionné des PC cloud pour votre locataire client, la carte Windows 365 sur la page d’accueil de Microsoft 365 fournit une brève alerte sur les PC cloud qui ont besoin d’être actionnés, comme le nombre de PC cloud qui n’ont pas pu être approvisionnés et les échecs de connexion réseau Azure. Pour obtenir un état détaillé, sélectionnez le bouton de la carte Windows 365 (ou sélectionnez **Appareils** >  **Windows 365** dans le volet de navigation gauche) pour ouvrir la page Windows 365. À partir de cette page, vous pouvez obtenir une vue d’ensemble de l’état des PC cloud affectés à vos locataires clients, afficher la liste de tous les PC cloud que vous gérez et les locataires auxquels ils sont affectés, et afficher les connexions réseau Azure entre vos locataires clients et Azure Active Directory (Azure AD) et leur état.

## <a name="overview-tab"></a>Onglet Overview

Sous l’onglet Vue d’ensemble, la barre d’annotation de nombre de couleurs affiche le nombre total de PC cloud ou de connexions réseau Azure sur tous vos locataires clients qui ont les états suivants : Connexions réseau ayant échoué, Non approvisionné, Échec de l’approvisionnement et Déprovisionnement bientôt.

Vous pouvez voir une répartition des états des PC cloud pour chaque locataire client dans la liste sous la barre d’annotation de nombre. Pour voir quels locataires ont des PC cloud avec un état spécifique, sélectionnez cet état dans la barre count-annotation pour filtrer la liste. Pour afficher les états des PC cloud pour un ou plusieurs locataires clients spécifiques, utilisez le menu déroulant **Locataires** pour filtrer la liste.

Pour obtenir des informations d’état détaillées pour un client particulier, sélectionnez une valeur sous l’une des colonnes d’état de ce locataire. Selon la colonne dans laquelle se trouve la valeur, l’onglet **Connexions réseau Azure** ou **Tous les PC cloud** s’ouvre et affiche plus d’informations.

L’onglet Vue d’ensemble comprend également les options suivantes :

- **Actualiser:** Sélectionnez cette option pour récupérer les données de PC cloud les plus actuelles.
- **Exportation:** Sélectionnez cette option pour exporter des données de PC cloud vers un fichier de valeurs séparées par des virgules Excel (.csv).
- **Rechercher:** Entrez des mots clés pour localiser rapidement un PC cloud spécifique dans la liste.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png" alt-text="Capture d’écran de l’onglet Vue d’ensemble Windows 365." lightbox="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png":::

## <a name="all-cloud-pcs-tab"></a>Onglet Tous les PC cloud

Sous l’onglet Tous les PC cloud, la barre d’annotation de nombre de couleurs affiche le nombre total d’ordinateurs cloud sur tous vos locataires clients ayant les états suivants : Provisionné, Non approvisionné, Échec de l’approvisionnement et Déprovisionnement bientôt.

Vous pouvez afficher tous les PC cloud et leur état d’approvisionnement dans la liste sous la barre count-annotation. Les informations suivantes sont fournies :

- **Nom du PC cloud :** Nom affecté au PC cloud.
- **Utilisateur:** Utilisateur pour lequel un PC cloud a été approvisionné ou a tenté d’être approvisionné.
- **Nom de l’appareil :** Intune nom de l’appareil , un identificateur unique pour un PC cloud.
- **Locataire:** Client dans lequel un PC cloud a été approvisionné.
- **Statut:** État d’approvisionnement du PC cloud.
- **Type de licence :** Entreprise ou Entreprise.
- **Spécifications:** Configuration matérielle du PC cloud.

Pour voir quels locataires ont des PC cloud avec un état d’approvisionnement spécifique, sélectionnez cet état dans la barre count-annotation pour filtrer la liste. Pour afficher les états d’approvisionnement de PC cloud pour un ou plusieurs locataires clients spécifiques, utilisez le menu déroulant **Locataires** pour filtrer la liste.

Sélectionnez n’importe quel PC cloud dans la liste pour afficher plus de détails et exécuter des actions de gestion telles que :
- **Redémarrer:** Sélectionnez cette option pour redémarrer l’appareil. 
- **Reprovisionnement :** Sélectionnez cette option pour réinitialiser l’appareil. Vous pouvez également afficher la stratégie d’approvisionnement dans le lien Microsoft Endpoint Manager.
- **Renommer:** Sélectionnez cette option pour renommer l’appareil affecté à un utilisateur.
- **Modifier le type de compte :** Sélectionnez le type de compte pour l’utilisateur : Utilisateur standard (recommandé) ou Administrateur local.

L’onglet Tous les PC cloud inclut également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter des données de PC cloud vers un fichier de valeurs séparées par des virgules Excel (.csv).
- **Actualiser:** Sélectionnez cette option pour récupérer les données de PC cloud les plus actuelles.
- **Rechercher:** Entrez des mots clés pour localiser rapidement un PC cloud spécifique dans la liste.

Pour obtenir la liste complète des états d’approvisionnement de PC cloud et ce qu’ils signifient, consultez la [vue d’ensemble de la gestion des appareils pour les PC cloud](/windows-365/enterprise/device-management-overview#column-details) dans la bibliothèque de documentation Windows 365.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Capture d’écran de l’onglet Windows 365 Tous les PC cloud." lightbox="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png":::

## <a name="azure-network-connections-tab"></a>Onglet Connexions réseau Azure

Sous l’onglet Connexions réseau Azure, la barre d’annotations de nombre de couleurs affiche le nombre total de connexions réseau Azure sur tous vos locataires clients qui ont Windows 365 Entreprise PC cloud et peuvent avoir les états suivants : Connexions réussies et connexions ayant échoué.

Dans la liste sous la barre count-annotation, vous pouvez afficher toutes les connexions réseau Azure et leur état de connexion.

Pour afficher les connexions avec un état d’approvisionnement spécifique, sélectionnez cet état dans la barre d’annotation de nombre pour filtrer la liste. Pour afficher les états de connexion d’un ou de plusieurs locataires clients spécifiques, utilisez le menu déroulant **Locataires** pour filtrer la liste.

Si vous devez prendre des mesures ou résoudre les problèmes d’une connexion dans la liste, sélectionnez **Afficher les détails de la connexion dans Microsoft Endpoint Manager**.

L’onglet Connexions réseau Azure inclut également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter les données de connexion vers un fichier de valeurs séparées par des virgules Excel (.csv).
- **Actualiser:** Sélectionnez cette option pour récupérer les données de connexion les plus actuelles.
- **Rechercher:** Entrez des mots clés pour localiser rapidement une connexion spécifique.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png" alt-text="Capture d’écran de l’onglet Connexions réseau Azure." lightbox="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png":::

## <a name="related-content"></a>Contenu associé

[Qu’est-ce que Windows 365 ?](/windows-365/overview) (article)\
[Windows 365 vue d’ensemble de la gestion des appareils pour les PC cloud](/windows-365/enterprise/device-management-overview) (article)\
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)