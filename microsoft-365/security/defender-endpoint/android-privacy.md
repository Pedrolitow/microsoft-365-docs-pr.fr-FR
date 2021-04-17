---
title: 'Microsoft Defender ATP pour Android : informations de confidentialité'
description: Contrôles de confidentialité, comment configurer des paramètres de stratégie qui ont une incidence sur la confidentialité et des informations sur les données de diagnostic collectées dans Microsoft Defender ATP pour Android.
keywords: microsoft, defender, atp, android, confidentialité, diagnostic
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
ms.openlocfilehash: 79f8882e21f23e75d85813cde03260ef17adf246
ms.sourcegitcommit: 2655bb0ccd66279c35be2fadbd893c937d084109
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "51876108"
---
#  <a name="microsoft-defender-for-endpoint-on-android---privacy-information"></a>Microsoft Defender pour point de terminaison Android : informations sur la confidentialité

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 


Defender pour le point de terminaison pour Android collecte des informations à partir de vos appareils Android configurés et les stocke dans le même client que celui où vous avez Defender for Endpoint. Les informations sont collectées pour aider à maintenir defender pour point de terminaison pour iOS sécurisé, à jour, performant comme prévu et pour prendre en charge le service.

Pour plus d'informations sur le stockage des données, voir Microsoft Defender pour le stockage et la confidentialité des données de point [de terminaison.](data-storage-privacy.md)

Des informations sont collectées pour aider à maintenir defender pour point de terminaison pour Android sécurisé, à jour, en cours d'application et pour prendre en charge le service.

## <a name="required-data"></a>Données requises 

Les données requises sont constituées de données qui sont nécessaires pour que Defender for Endpoint for Android fonctionne comme prévu. Ces données sont essentielles au fonctionnement du service et peuvent inclure des données relatives à l'utilisateur final, à l'organisation, à l'appareil et aux applications. Voici une liste des types de données collectées :

### <a name="app-information"></a>Informations sur l'application

Informations sur **les** packages d'application Android malveillants (APK) sur l'appareil, y compris

-  Source d'installation
-  Emplacement de stockage (chemin d'accès au fichier) de l'APIK
-  Heure d'installation, taille de l'API et autorisations

### <a name="web-page--network-information"></a>Page Web / Informations réseau

- URL complète du site web uniquement lorsqu'une connexion malveillante ou une page web est détectée.
- Informations de connexion
- Type de protocole (par exemple, HTTP, HTTPS, etc.)


### <a name="device-and-account-information"></a>Informations sur l'appareil et le compte

- Informations sur l'appareil telles que l'& date, la version Android, le modèle OEM, les informations sur l'UC et l'identificateur de l'appareil
- L'identificateur de l'appareil est l'un des éléments suivants :
    - Wi-Fi'adaptateur MAC
    - [ID Android](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID_ID) (tel que généré par Android au moment du premier démarrage de l'appareil)
    - Identificateur global unique (GUID) généré de manière aléatoire

- Informations sur le client, l'appareil et l'utilisateur
    -   ID d'appareil Azure Active Directory (AD) et ID utilisateur Azure : identifie de manière unique l'appareil, utilisateur, respectivement dans Azure Active Directory.

    -   ID client Azure : GUID qui identifie votre organisation dans Azure Active Directory

    -   ID d'organisation Microsoft Defender ATP : identificateur unique associé à l'entreprise à qui appartient l'appareil. Permet à Microsoft d'identifier si les problèmes ont un impact sur un ensemble d'entreprises sélectionné et le nombre d'entreprises qui en sont touchées 

    -   Nom d'utilisateur principal – ID de messagerie de l'utilisateur

### <a name="product-and-service-usage-data"></a>Données d'utilisation des produits et services

Les informations suivantes sont collectées uniquement pour l'application Microsoft Defender for Endpoint installée sur l'appareil. 

-   Informations sur le package d'application, y compris le nom, la version et l'état de la mise à niveau de l'application

-   Actions effectuées dans l'application

-   Informations sur la détection des menaces, telles que le nom de la menace, la catégorie, etc.

-   Journaux de rapport d'incident générés par Android

## <a name="optional-data"></a>Données facultatives

Les données facultatives incluent les données de diagnostic et les données de commentaires. Les données de diagnostic facultatives nous aident à améliorer le produit et nous fournissent des informations complémentaires pour détecter, diagnostiquer et résoudre les problèmes. Les données de diagnostic facultatives incluent :

-   Utilisation de l'application, du processeur et du réseau

-   État de l'appareil du point de vue de l'application, y compris l'état de l'analyse, le minutage de l'analyse, les autorisations d'application accordées et l'état de mise à niveau

-   Fonctionnalités configurées par l'administrateur

-   Informations de base sur les navigateurs sur l'appareil

**Les données de** commentaires sont collectées par le biais de commentaires dans l'application fournis par l'utilisateur

-   L'adresse e-mail de l'utilisateur, s'il choisit de la fournir

-   Type de commentaires (souris, frown, idée) et tous les commentaires envoyés par l'utilisateur
