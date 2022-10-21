---
title: Vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: katmartin
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
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, découvrez la page Windows 365 (PC cloud).
ms.openlocfilehash: 027fcd4fc20ea662d3fae19fba811483e6946705
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68661784"
---
# <a name="overview-of-the-windows-365-cloud-pcs-page-in-microsoft-365-lighthouse"></a>Vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse  
  
Windows 365 est un service cloud qui permet aux administrateurs Microsoft Endpoint Manager (MEM) de provisionner et de gérer des PC cloud pour leurs utilisateurs disposant d’une licence Windows 365. Windows 365 est entièrement intégré à MEM pour la gestion des appareils, ainsi qu’à Microsoft 365 Lighthouse pour la gestion partenaire des PC cloud sur tous leurs locataires clients.

Pour plus d’informations sur Windows 365, consultez [Qu’est-ce que Windows 365 ?](/windows-365/overview) Pour obtenir la liste des exigences Windows 365, consultez [Configuration requise pour Windows 365](/windows-365/enterprise/requirements).

> [!IMPORTANT]
> Vous devez accéder à [MEM](https://go.microsoft.com/fwlink/p/?linkid=2150463) pour provisionner des PC cloud pour chaque locataire client avant de pouvoir les gérer dans Lighthouse. Vous ne pouvez pas provisionner à partir de Lighthouse.

Une fois que vous avez provisionné des PC cloud pour votre client, la carte Windows 365 sur la page d’accueil de Microsoft 365 fournit une brève alerte sur les PC cloud nécessitant une action, par exemple le nombre de PC cloud qui n’ont pas pu être approvisionnés et les échecs de connexion réseau Azure. Pour obtenir un état détaillé, sélectionnez le bouton sur la carte Windows 365 (ou sélectionnez **Appareils** >  **Windows 365** dans le volet de navigation gauche) pour ouvrir la page Windows 365. À partir de cette page, vous pouvez obtenir une vue d’ensemble de l’état des PC cloud attribués à vos locataires clients, afficher une liste de tous les PC cloud que vous gérez et des locataires auxquels ils sont affectés, et afficher les connexions réseau Azure entre vos locataires clients et Azure Active Directory (Azure AD) et leur état.

## <a name="overview-tab"></a>Onglet Overview

Sous l’onglet Vue d’ensemble, la barre d’annotation de nombre de couleurs affiche le nombre total de PC cloud ou de connexions réseau Azure sur tous vos locataires clients qui ont les états suivants : Échec des connexions réseau, Non provisionné, Échec de l’approvisionnement et Déprovisionnement bientôt.

Vous pouvez voir une répartition des états des PC cloud pour chaque locataire client dans la liste sous la barre de nombre d’annotations. Pour voir quels locataires ont des PC cloud avec un état spécifique, sélectionnez cet état dans la barre count-annotation pour filtrer la liste. Pour afficher les états des PC cloud pour un ou plusieurs locataires clients spécifiques, utilisez le menu déroulant **Locataires** pour filtrer la liste.

Pour obtenir des informations détaillées sur l’état d’un locataire client particulier, sélectionnez une valeur sous l’une des colonnes d’état de ce locataire. Selon la colonne dans laquelle se trouve la valeur, l’onglet **Connexions réseau Azure** ou **Tous les PC cloud** s’ouvre et affiche plus d’informations.

L’onglet Vue d’ensemble inclut également les options suivantes :

- **Actualiser:** Sélectionnez cette option pour récupérer les données de PC cloud les plus actuelles.
- **Exportation:** Sélectionnez cette option pour exporter les données du PC cloud vers un fichier de valeurs séparées par des virgules (.csv) Excel.
- **Rechercher:** Entrez des mots clés pour localiser rapidement un PC cloud spécifique dans la liste.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png" alt-text="Capture d’écran de l’onglet Vue d’ensemble Windows 365." lightbox="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png":::

## <a name="all-cloud-pcs-tab"></a>Onglet Tous les PC cloud

Sous l’onglet Tous les PC cloud, la barre d’annotation de nombre de couleurs affiche le nombre total de PC cloud sur tous les locataires de vos clients qui ont les états suivants : Provisionné, Non provisionné, Échec de l’approvisionnement et Déprovisionnement bientôt.

Vous pouvez afficher tous les PC cloud et leur état d’approvisionnement dans la liste sous la barre count-annotation. Les informations suivantes sont fournies :

- **Nom du PC cloud :** Nom attribué au PC cloud.
- **Utilisateur:** Utilisateur pour lequel un PC cloud a été approvisionné ou a tenté de l’être.
- **Nom de l’appareil :** Intune nom de l’appareil, identificateur unique d’un PC cloud.
- **Locataire:** Locataire client dans lequel un PC cloud a été approvisionné.
- **Statut:** État d’approvisionnement du PC cloud.
- **Type de licence :** Entreprise ou Entreprise.
- **Spécifications:** Configuration matérielle du PC cloud.

Pour voir quels locataires ont des PC cloud avec un état d’approvisionnement spécifique, sélectionnez cet état dans la barre count-annotation pour filtrer la liste. Pour afficher les états d’approvisionnement de PC cloud pour un ou plusieurs locataires clients spécifiques, utilisez le menu déroulant **Locataires** pour filtrer la liste.

Sélectionnez n’importe quel PC cloud dans la liste pour afficher plus de détails et exécuter des actions de gestion telles que :
- **Redémarrer:** Sélectionnez cette option pour redémarrer l’appareil. 
- **Reprovisionner :** Sélectionnez cette option pour réinitialiser l’appareil. Vous pouvez également afficher la stratégie d’approvisionnement dans le lien Microsoft Endpoint Manager.
- **Renommer:** Sélectionnez cette option pour renommer l’appareil affecté à un utilisateur.
- **Modifier le type de compte :** Sélectionnez le type de compte pour l’utilisateur : Utilisateur standard (recommandé) ou Administrateur local.

L’onglet Tous les PC cloud inclut également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter les données du PC cloud vers un fichier de valeurs séparées par des virgules (.csv) Excel.
- **Actualiser:** Sélectionnez cette option pour récupérer les données de PC cloud les plus actuelles.
- **Rechercher:** Entrez des mots clés pour localiser rapidement un PC cloud spécifique dans la liste.

Pour voir la liste complète des états d’approvisionnement des PC cloud et leur signification, consultez [Vue d’ensemble de la gestion des appareils pour les PC cloud](/windows-365/enterprise/device-management-overview#column-details) dans la bibliothèque de documentation Windows 365.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Capture d’écran de l’onglet Windows 365 Tous les PC cloud." lightbox="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png":::

## <a name="azure-network-connections-tab"></a>Onglet Connexions réseau Azure

Sous l’onglet Connexions réseau Azure, la barre d’annotation de nombre de couleurs affiche le nombre total de connexions réseau Azure entre tous vos locataires clients qui ont Windows 365 Entreprise PC cloud et qui peuvent avoir les états suivants : Connexions réussies et Connexions en échec.

Dans la liste sous la barre count-annotation, vous pouvez afficher toutes les connexions réseau Azure et leur état de connexion.

Pour afficher les connexions avec un état d’approvisionnement spécifique, sélectionnez cet état dans la barre count-annotation pour filtrer la liste. Pour afficher les états de connexion d’un ou de plusieurs locataires clients spécifiques, utilisez le menu déroulant **Locataires** pour filtrer la liste.

Si vous devez prendre des mesures ou résoudre les problèmes d’une connexion dans la liste, sélectionnez **Afficher les détails de connexion dans Microsoft Endpoint Manager**.

L’onglet Connexions réseau Azure inclut également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter les données de connexion vers un fichier de valeurs séparées par des virgules (.csv) Excel.
- **Actualiser:** Sélectionnez cette option pour récupérer les données de connexion les plus actuelles.
- **Rechercher:** Entrez des mots clés pour localiser rapidement une connexion spécifique.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png" alt-text="Capture d’écran de l’onglet Connexions réseau Azure." lightbox="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png":::

## <a name="related-content"></a>Contenu associé

[Qu’est-ce que Windows 365 ?](/windows-365/overview) (article)\
[vue d’ensemble de la gestion des appareils Windows 365 pour les PC cloud](/windows-365/enterprise/device-management-overview) (article)\
[FAQ Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (article)