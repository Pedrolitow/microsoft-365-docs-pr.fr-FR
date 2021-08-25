---
title: vue d Microsoft 365 Lighthouse Windows la page 365 (PC cloud)
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez la page Windows 365 (PC cloud).
ms.openlocfilehash: b71beb0315c15929b20e1afd32a96bfd811a9ea9
ms.sourcegitcommit: f358e321f7e81eff425fe0f0db1be0f3348d2585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2021
ms.locfileid: "58507793"
---
# <a name="windows-365-cloud-pcs-page-overview"></a>vue d Windows la page 365 (Pc cloud)  

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences.](m365-lighthouse-requirements.md) Si votre organisation n’a pas de Microsoft 365 Lighthouse, voir [S’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).
  
Windows 365 est un service basé sur le cloud qui permet aux administrateurs de Microsoft Endpoint Manager (MEM) de provisioner et de gérer des PC Cloud pour leurs utilisateurs qui ont une licence Windows 365. Windows 365 est entièrement intégré à MEM pour la gestion des appareils et à Microsoft 365 Lighthouse pour la gestion par les partenaires des PC cloud sur tous les clients.

Pour plus d’informations Windows 365, voir [Qu’est-ce Windows 365 ?](/windows-365/overview) Pour obtenir la liste des Windows 365 requises, voir [Requirements for Windows 365](/windows-365/requirements).

> [!IMPORTANT]
> Vous devez vous rendre sur [MEM](https://go.microsoft.com/fwlink/p/?linkid=2150463) pour mettre en service des PC Cloud pour chaque client avant de pouvoir les gérer dans Le Monde. Vous ne pouvez pas le faire à partir de l’intérieur de l’île.

Une fois que vous avez mis en service les PC Cloud pour votre client, la carte Windows 365 sur la page d’accueil Microsoft 365 fournit une brève alerte sur les PC cloud qui ont besoin d’action, telles que le nombre de PC Cloud qui n’ont pas pu être mis en service et les échecs de connexion réseau locaux. Pour obtenir un état détaillé, sélectionnez le bouton sur la carte Windows 365 (ou sélectionnez **Windows 365** dans le volet de navigation de gauche) pour ouvrir la page Windows 365. À partir de cette page, vous pouvez obtenir une vue d’ensemble de l’état des PC Cloud affectés à vos clients, afficher la liste de tous les PC Cloud que vous gérez et les clients qui leur sont affectés, et afficher les connexions réseau sur site entre vos clients clients et Azure Active Directory (Azure AD) et leur état.

## <a name="overview-tab"></a>Onglet Overview

Sous l’onglet Vue d’ensemble, la barre de nombre d’annotations colorée affiche le nombre total de PC Cloud ou de connexions réseau sur site sur tous les clients qui ont les états suivants : Connexions réseau défactuées, Non mise en service, échec de l’approvisionnement et mise en service prochainement.

Vous pouvez voir une répartition des statuts de l’ordinateur cloud pour chaque client dans la liste sous la barre d’annotations. Pour voir quels locataires ont des PC Cloud avec un état spécifique, sélectionnez cet état dans la barre d’annotations de nombre pour filtrer la liste. Pour voir les statuts du Cloud PC pour  un ou plusieurs clients spécifiques, utilisez le menu déroulant Clients pour filtrer la liste.

Pour obtenir des informations détaillées sur l’état d’un client particulier, sélectionnez une valeur sous l’une des colonnes d’état de ce client. Selon la colonne dans laquelle se trouve la valeur, l’onglet **Connexions** réseau sur site ou Tous les **PC cloud** s’ouvre et affiche plus d’informations.

L’onglet Vue d’ensemble inclut également les options suivantes :

- **Actualiser :** Sélectionnez pour récupérer les données de PC cloud les plus récentes.
- **Exporter :** Choisissez d’exporter les données cloud PC vers Excel fichier de valeurs séparées par des virgules (.csv).
- **Recherche :** Entrez des mots clés pour localiser rapidement un PC Cloud spécifique dans la liste.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png" alt-text="Capture d’écran de l Windows onglet Vue d’ensemble de 365.":::

## <a name="all-cloud-pcs-tab"></a>Onglet Tous les PC cloud

Sous l’onglet Tous les PC Cloud, la barre d’annotations de nombre en couleur affiche le nombre total de PC Cloud sur tous les clients qui ont les statuts suivants : Mise en service, non mise en service, échec de l’approvisionnement et mise en service prochainement.

Vous pouvez afficher tous les PC cloud et leur état d’approvisionnement dans la liste sous la barre d’annotations. Les informations suivantes sont fournies :

- **Nom du PC cloud :** Nom attribué au PC Cloud.
- **Client :** Client dans lequel un PC cloud a été provisioné.
- **Nom de l’appareil :** Nom de l’appareil Intune : identificateur unique pour un PC cloud.
- **Type de PC :** Type de PC cloud en fonction des références standard.
- **État :** État de mise en service du PC cloud.
- **Utilisateur :** Utilisateur pour lequel un PC Cloud a été mis en service ou a tenté d’être mis en service.

Pour voir quels locataires ont des PC Cloud avec un état d’approvisionnement spécifique, sélectionnez cet état dans la barre d’annotations de nombre pour filtrer la liste. Pour voir les **statuts** de mise en service de Cloud PC pour un ou plusieurs clients spécifiques, utilisez le menu déroulant Clients pour filtrer la liste.

Sélectionnez n’importe quel PC cloud dans la liste pour afficher plus de détails. Si vous devez prendre des mesures sur le PC cloud, il existe des options pour afficher les stratégies d’approvisionnement des locataires et les détails de l’appareil dans Microsoft Endpoint Manager.

L’onglet Tous les PC cloud inclut également les options suivantes :

- **Actualiser :** Sélectionnez pour récupérer les données de PC cloud les plus récentes.
- **Exporter :** Choisissez d’exporter les données cloud PC vers Excel fichier de valeurs séparées par des virgules (.csv).
- **Recherche :** Entrez des mots clés pour localiser rapidement un PC Cloud spécifique dans la liste.
- **Nouvelle tentative de mise en service :** Sélectionnez 1 à 20 PC cloud dans la liste dont l’état de mise en service a **échoué,** puis sélectionnez cette option pour réessayer d’approvisionnement pour ces PC Cloud.

Pour consulter la liste complète des statuts des PC cloud et leur description, consultez la page de présentation de [Cloud PC](/windows-365/device-management-overview#cloud-pc-overview-page) dans la bibliothèque de documentation Windows 365.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Capture d’écran de Windows onglet 365 Tous les PC cloud.":::

## <a name="on-premises-network-connections-tab"></a>Onglet Connexions réseau sur site

Sous l’onglet Connexions réseau sur site, la barre de nombre d’annotations en couleur affiche le nombre total de connexions réseau sur site sur tous les clients qui ont les états suivants : Connexions réussies et Connexions échouées.

Dans la liste sous la barre d’annotations de nombre, vous pouvez afficher toutes les connexions réseau sur site et leur état de connexion.

Pour voir les connexions avec un état d’approvisionnement spécifique, sélectionnez cet état dans la barre d’annotations de nombre pour filtrer la liste. Pour voir les statuts de connexion d’un  ou de plusieurs clients spécifiques, utilisez le menu déroulant Clients pour filtrer la liste.

Si vous devez prendre des mesures ou résoudre les problèmes d’une connexion dans la liste, sélectionnez Afficher les **détails** de connexion dans Microsoft Endpoint Manager .

L’onglet Connexions réseau local inclut également les options suivantes :

- **Actualiser :** Sélectionnez pour récupérer les données de connexion les plus récentes.
- **Exporter :** Sélectionnez cette sélection pour exporter les données de connexion vers Excel fichier de valeurs séparées par des virgules (.csv).
- **Recherche :** Entrez des mots clés pour localiser rapidement une connexion spécifique.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/on-prem-network-connections-tab.png" alt-text="Capture d’écran Windows onglet Connexions réseau 365 sur site.":::

## <a name="related-content"></a>Contenu associé

[Qu’est-Windows 365 ?](/windows-365/overview) (article)\
[Windows vue d’ensemble de](/windows-365/device-management-overview) la gestion des appareils 365 pour les PC cloud (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)