---
title: 'Microsoft Defender pour point de terminaison Android : informations sur la confidentialité'
description: Contrôles de confidentialité, comment configurer les paramètres de stratégie qui ont une incidence sur la confidentialité et les informations sur les données de diagnostic collectées dans Microsoft Defender pour Endpoint sur Android.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, android, confidentialité, diagnostic
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 7adb3dfe610cb8fa2c2c697956e13769b09315b54d7e1506afc25d0a9520ccd2
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53894646"
---
#  <a name="microsoft-defender-for-endpoint-on-android---privacy-information"></a>Microsoft Defender pour point de terminaison Android : informations sur la confidentialité

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Defender pour le point de terminaison sur Android collecte des informations à partir de vos appareils Android configurés et les stocke dans le même client que celui où vous avez Defender for Endpoint. Les informations sont collectées pour aider à maintenir defender pour point de terminaison pour Android sécurisé, à jour, performant comme prévu et pour prendre en charge le service.

Pour plus d’informations sur le stockage des données, voir Microsoft Defender pour le stockage et la confidentialité des données de point [de terminaison.](data-storage-privacy.md)

Des informations sont collectées pour aider à maintenir defender pour point de terminaison pour Android sécurisé, à jour, en cours d’application et pour prendre en charge le service.

Pour plus d’informations sur les questions de confidentialité les plus courantes concernant Microsoft Defender pour point de terminaison sur les appareils mobiles Android et iOS, consultez Microsoft Defender pour endpoint et votre confidentialité sur les appareils mobiles Android et [iOS.](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-and-your-privacy-on-android-and-ios-mobile-devices-4109bc54-8ec5-4433-9c33-d359b75ac22a)

## <a name="required-data"></a>Données requises

Les données requises sont constituées de données qui sont nécessaires pour que Defender for Endpoint for Android fonctionne comme prévu. Ces données sont essentielles au fonctionnement du service et peuvent inclure des données relatives à l’utilisateur final, à l’organisation, à l’appareil et aux applications. Voici une liste des types de données collectées :

### <a name="app-information"></a>Informations sur l’application

Informations sur **les** packages d’application Android malveillants (APK) sur l’appareil, y compris

- Source d’installation
- Stockage emplacement (chemin d’accès du fichier) de l’APIK
- Heure d’installation, taille de l’API et autorisations

### <a name="web-page--network-information"></a>Page Web / Informations réseau

- URL complète du site web uniquement lorsqu’une connexion malveillante ou une page web est détectée.
- Informations de connexion
- Type de protocole (par exemple, HTTP, HTTPS, etc.)

### <a name="device-and-account-information"></a>Informations sur l’appareil et le compte

- Informations sur l’appareil telles que l'& date, la version Android, le modèle OEM, les informations sur l’UC et l’identificateur de l’appareil.
- L’identificateur de l’appareil est l’un des éléments suivants :
  - Wi-Fi'adaptateur MAC
  - [ID Android](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID_ID) (tel que généré par Android au moment du premier démarrage de l’appareil).
  - Identificateur global unique (GUID) généré de manière aléatoire.

- Informations sur le client, l’appareil et l’utilisateur
  - Azure Active Directory (AD) Device ID et Azure User ID : identifie de manière unique l’appareil, Utilisateur, respectivement dans Azure Active Directory.
  - ID de client Azure : GUID qui identifie votre organisation au sein Azure Active Directory.
  - ID d’organisation Microsoft Defender pour point de terminaison : identificateur unique associé à l’entreprise à qui appartient l’appareil. Permet à Microsoft d’identifier si les problèmes ont un impact sur un ensemble d’entreprises sélectionné et le nombre d’entreprises qui en sont touchées.
  - Nom d’utilisateur principal : ID de messagerie de l’utilisateur

### <a name="product-and-service-usage-data"></a>Données d’utilisation des produits et services

Les informations suivantes sont collectées uniquement pour l’application Microsoft Defender for Endpoint installée sur l’appareil. 

- Informations sur le package d’application, y compris le nom, la version et l’état de la mise à niveau de l’application.
- Actions effectuées dans l’application.
- Informations sur la détection des menaces, telles que le nom de la menace, la catégorie, etc.
- Journaux de rapport d’incident générés par Android.

## <a name="optional-data"></a>Données facultatives

Les données facultatives incluent les données de diagnostic et les données de commentaires. Les données de diagnostic facultatives nous aident à améliorer le produit et nous fournissent des informations complémentaires pour détecter, diagnostiquer et résoudre les problèmes. Les données de diagnostic facultatives incluent :

- Utilisation de l’application, du processeur et du réseau.
- État de l’appareil du point de vue de l’application, y compris l’état de l’analyse, le minutage de l’analyse, les autorisations d’application accordées et l’état de mise à niveau.
- Fonctionnalités configurées par l’administrateur.
- Informations de base sur les navigateurs sur l’appareil.

**Les données de** commentaires sont collectées par le biais de commentaires dans l’application fournis par l’utilisateur

- Adresse de messagerie de l’utilisateur, s’il choisit de la fournir.
- Type de commentaires (souris, frown, idée) et tous les commentaires envoyés par l’utilisateur.
