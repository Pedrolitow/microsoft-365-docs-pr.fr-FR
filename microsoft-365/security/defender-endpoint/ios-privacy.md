---
title: Informations de confidentialité - Microsoft Defender pour point de terminaison sur iOS
ms.reviewer: ''
description: Décrit les informations de confidentialité pour Microsoft Defender pour point de terminaison sur iOS
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, ios, stratégie, vue d’ensemble
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
- m365-security-compliance
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 64525457c63930876a729888aa5a8d5575894b45
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67522651"
---
# <a name="privacy-information---microsoft-defender-for-endpoint-on-ios"></a>Informations de confidentialité - Microsoft Defender pour point de terminaison sur iOS

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!NOTE]
> Defender pour point de terminaison sur iOS utilise un VPN pour fournir la fonctionnalité De protection web. Il ne s’agit pas d’un VPN normal et d’un VPN local ou auto-bouclage qui ne prend pas le trafic en dehors de l’appareil. **Microsoft ou votre organisation ne voit pas votre activité de navigation.**

Defender pour point de terminaison sur iOS collecte des informations à partir de vos appareils iOS configurés et les stocke dans le même locataire que defender pour point de terminaison. Les informations sont collectées pour vous aider à maintenir Defender pour point de terminaison sur iOS sécurisé, à jour, performant comme prévu et à prendre en charge le service.

Pour plus d’informations sur le stockage des données, consultez [Microsoft Defender pour point de terminaison stockage des données et la confidentialité](data-storage-privacy.md).

Pour plus d’informations sur les questions de confidentialité les plus courantes sur Microsoft Defender pour point de terminaison sur les appareils mobiles Android et iOS, consultez [Microsoft Defender pour point de terminaison et votre confidentialité sur les appareils mobiles Android et iOS](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-and-your-privacy-on-android-and-ios-mobile-devices-4109bc54-8ec5-4433-9c33-d359b75ac22a).

## <a name="required-data"></a>Données requises

Les données requises sont constituées de données nécessaires pour que Defender pour point de terminaison sur iOS fonctionne comme prévu. Ces données sont essentielles au fonctionnement du service et peuvent inclure des données relatives à l’utilisateur final, à l’organisation, à l’appareil et aux applications.

Voici une liste des types de données collectées :

### <a name="web-page-or-network-information"></a>Informations sur la page web ou le réseau

- Nom de domaine et adresse IP du site web uniquement lorsqu’une connexion malveillante ou une page web est détectée.

### <a name="device-and-account-information"></a>Informations sur l’appareil et le compte

- Informations sur l’appareil, telles que la date & l’heure, la version iOS, les informations d’UC et l’identificateur d’appareil, où l’identificateur d’appareil est l’un des éléments suivants :
  - adresse MAC de l’adaptateur Wi-Fi
  - Identificateur global unique (GUID) généré de manière aléatoire
- Informations sur le locataire, l’appareil et l’utilisateur
  - ID d’appareil Azure Active Directory (AD) et ID d’utilisateur Azure : identifie de façon unique l’appareil, utilisateur respectivement dans Azure Active Directory.
  - ID de locataire Azure - GUID qui identifie votre organisation au sein d’Azure Active Directory.
  - Microsoft Defender pour point de terminaison ID d’organisation : identificateur unique associé à l’entreprise à laquelle appartient l’appareil. Permet à Microsoft d’identifier s’il existe des problèmes affectant un ensemble sélectionné d’entreprises et le nombre d’entreprises concernées.
  - Nom d’utilisateur principal : Email ID de l’utilisateur.

### <a name="product-and-service-usage-data"></a>Données d’utilisation des produits et des services

Les informations suivantes sont collectées uniquement pour Microsoft Defender pour point de terminaison application installée sur l’appareil.

- Informations sur le package d’application, notamment le nom, la version et l’état de mise à niveau de l’application.
- Actions effectuées dans l’application.
- Journaux des rapports d’incident générés par iOS.
- Données d’utilisation de la mémoire.

## <a name="optional-data"></a>Données facultatives

Les données facultatives incluent les données de diagnostic et les données de commentaires du client. Les données de diagnostic facultatives nous aident à améliorer le produit et nous fournissent des informations complémentaires pour détecter, diagnostiquer et résoudre les problèmes. Ces données sont uniquement à des fins de diagnostic et ne sont pas requises pour le service lui-même.

Les données de diagnostic facultatives incluent :

- Utilisation de l’application, du processeur et du réseau pour Defender pour point de terminaison.
- Fonctionnalités configurées par l’administrateur pour Defender pour point de terminaison.

Les données de commentaires sont collectées par le biais des commentaires dans l’application fournis par l’utilisateur.

- Adresse e-mail de l’utilisateur, s’il choisit de la fournir.
- Type de commentaires (sourire, froncement de sourcils, idée) et tous les commentaires envoyés par l’utilisateur.

Pour plus d’informations, consultez [Plus sur la confidentialité](https://aka.ms/mdatpiosprivacystatement).
