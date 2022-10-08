---
title: 'Microsoft Defender pour point de terminaison Android : informations sur la confidentialité'
description: Contrôles de confidentialité, configuration des paramètres de stratégie qui ont un impact sur la confidentialité et les informations sur les données de diagnostic collectées dans Microsoft Defender pour point de terminaison sur Android.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, android, confidentialité, diagnostic
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: a65012792f930c77977537b724cf36d94cc2527b
ms.sourcegitcommit: b9282493c371d59c2e583b9803825096499b5e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68145664"
---
# <a name="microsoft-defender-for-endpoint-on-android---privacy-information"></a>Microsoft Defender pour point de terminaison Android : informations sur la confidentialité

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Defender pour point de terminaison sur Android collecte des informations à partir de vos appareils Android configurés et les stocke dans le même locataire que defender pour point de terminaison. Les informations sont collectées pour vous aider à maintenir Defender pour point de terminaison pour Android sécurisé, à jour, à effectuer les performances attendues et à prendre en charge le service.

Pour plus d’informations sur le stockage des données, consultez [Microsoft Defender pour point de terminaison stockage des données et la confidentialité](data-storage-privacy.md).

Des informations sont collectées pour aider à maintenir Defender pour point de terminaison pour Android sécurisé, à jour, performant comme prévu et à prendre en charge le service.

Pour plus d’informations sur les questions de confidentialité les plus courantes sur Microsoft Defender pour point de terminaison sur les appareils mobiles Android et iOS, consultez [Microsoft Defender pour point de terminaison et votre confidentialité sur les appareils mobiles Android et iOS](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-and-your-privacy-on-android-and-ios-mobile-devices-4109bc54-8ec5-4433-9c33-d359b75ac22a).

## <a name="required-data"></a>Données requises

Les données requises sont constituées de données nécessaires pour que Defender pour point de terminaison pour Android fonctionne comme prévu. Ces données sont essentielles au fonctionnement du service et peuvent inclure des données relatives à l’utilisateur final, à l’organisation, à l’appareil et aux applications. Voici une liste des types de données collectées :

### <a name="app-information"></a>Informations sur l’application

Informations sur les packages d’application Android **malveillants** (APK) sur l’appareil, notamment

- Installer la source
- Emplacement de stockage (chemin d’accès au fichier) de l’APK
- Heure d’installation, taille d’APK et autorisations

Pour les appareils Android Enterprise entièrement gérés : informations sur les packages d’application Android (APK) installés sur l’appareil, notamment

- Nom et nom du package de l’application
- Numéro de version de l’application
- Nom de fournisseur

Pour Android Enterprise avec un profil professionnel - Informations sur les packages d’application Android (APK) installés sur le profil Professionnel de l’appareil, notamment

- Nom et nom du package de l’application
- Numéro de version de l’application
- Nom de fournisseur

*Votre organisation peut également choisir de configurer Defender pour point de terminaison pour envoyer des informations sur toutes les applications installées sur l’appareil. Par défaut, ces informations ne sont pas envoyées à votre organisation.*


### <a name="web-page--network-information"></a>Page Web / Informations réseau

- URL complète du site web uniquement lorsqu’une connexion malveillante ou une page web est détectée et bloquée.
- Informations de connexion
- Type de protocole (tel que HTTP, HTTPS, etc.)

### <a name="device-and-account-information"></a>Informations sur l’appareil et le compte

- Informations sur l’appareil telles que la date & l’heure, la version Android, le modèle OEM, les informations d’UC et l’identificateur d’appareil.
- L’identificateur d’appareil est l’un des éléments suivants :
  - adresse MAC de l’adaptateur Wi-Fi
  - [ID Android](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID_ID) (généré par Android au moment du premier démarrage de l’appareil).
  - Identificateur global unique (GUID) généré de manière aléatoire.

- Informations sur le locataire, l’appareil et l’utilisateur
  - ID d’appareil Azure Active Directory (AD) et ID d’utilisateur Azure : identifie de façon unique l’appareil, l’utilisateur, respectivement dans Azure Active Directory.
  - ID de locataire Azure : GUID qui identifie votre organisation au sein d’Azure Active Directory.
  - Microsoft Defender pour point de terminaison ID d’organisation : identificateur unique associé à l’entreprise à laquelle appartient l’appareil. Permet à Microsoft d’identifier si les problèmes affectent un ensemble sélectionné d’entreprises et le nombre d’entreprises concernées.
  - Nom d’utilisateur principal : ID Email de l’utilisateur

### <a name="product-and-service-usage-data"></a>Données d’utilisation des produits et des services

Les informations suivantes sont collectées uniquement pour Microsoft Defender pour point de terminaison application installée sur l’appareil. 

- Informations sur le package d’application, notamment le nom, la version et l’état de mise à niveau de l’application.
- Actions effectuées dans l’application.
- Informations de détection des menaces, telles que le nom de la menace, la catégorie, etc.
- Journaux des rapports d’incident générés par Android.

## <a name="optional-data"></a>Données facultatives

Les données facultatives incluent les données de diagnostic et les données de commentaires. Les données de diagnostic facultatives nous aident à améliorer le produit et nous fournissent des informations complémentaires pour détecter, diagnostiquer et résoudre les problèmes. Les données de diagnostic facultatives incluent :

- Utilisation de l’application, du processeur et du réseau.
- État de l’appareil du point de vue de l’application, notamment l’état de l’analyse, le minutage de l’analyse, les autorisations d’application accordées et l’état de mise à niveau.
- Fonctionnalités configurées par l’administrateur.
- Informations de base sur les navigateurs sur l’appareil.

**Les données de commentaires** sont collectées via les commentaires dans l’application fournis par l’utilisateur

- Adresse e-mail de l’utilisateur, s’il choisit de la fournir.
- Type de commentaires (sourire, froncement de sourcils, idée) et tous les commentaires envoyés par l’utilisateur.
