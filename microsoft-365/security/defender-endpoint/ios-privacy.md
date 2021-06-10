---
title: Informations de confidentialité - Microsoft Defender pour point de terminaison sur iOS
ms.reviewer: ''
description: Décrit les informations de confidentialité de Microsoft Defender pour Endpoint sur iOS
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, ios, stratégie, vue d’ensemble
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
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a232bd8d600df37d5b9b01921859556476ced345
ms.sourcegitcommit: 50908a93554290ff1157b58d0a868a33e012513c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52822369"
---
# <a name="privacy-information---microsoft-defender-for-endpoint-on-ios"></a>Informations de confidentialité - Microsoft Defender pour point de terminaison sur iOS

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!NOTE]
> Defender pour le point de terminaison sur iOS utilise un VPN pour fournir la fonctionnalité de protection web. Il ne s’agit pas d’un VPN normal et d’un VPN local ou en boucle autonome qui ne prend pas le trafic en dehors de l’appareil. **Microsoft ou votre organisation ne voit pas votre activité de navigation.**

Defender pour le point de terminaison sur iOS collecte des informations à partir de vos appareils iOS configurés et les stocke dans le même client que celui où vous avez Defender for Endpoint. Les informations sont collectées pour aider à maintenir Defender for Endpoint sur iOS sécurisé, à jour, en cours d’évaluation et pour prendre en charge le service.

Pour plus d’informations sur le stockage des données, voir Microsoft Defender pour le stockage et la confidentialité des données de point [de terminaison.](data-storage-privacy.md)


Pour plus d’informations sur les questions de confidentialité les plus courantes concernant Microsoft Defender pour point de terminaison sur les appareils mobiles Android et iOS, consultez Microsoft Defender pour endpoint et votre confidentialité sur les appareils mobiles Android et [iOS.](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-and-your-privacy-on-android-and-ios-mobile-devices-4109bc54-8ec5-4433-9c33-d359b75ac22a)

## <a name="required-data"></a>Données requises 

Les données requises sont constituées de données nécessaires pour que Defender for Endpoint sur iOS fonctionne comme prévu. Ces données sont essentielles au fonctionnement du service et peuvent inclure des données relatives à l’utilisateur final, à l’organisation, à l’appareil et aux applications. 

Voici une liste des types de données collectées : 

### <a name="web-page-or-network-information"></a>Page Web ou informations réseau 

- Nom de domaine et adresse IP du site web uniquement lorsqu’une connexion malveillante ou une page web est détectée. 

### <a name="device-and-account-information"></a>Informations sur l’appareil et le compte 

- Informations sur l’appareil telles que l'& date, la version d’iOS, les informations sur l’UC et l’identificateur de l’appareil, où l’identificateur d’appareil est l’un des éléments suivants : 

    - Wi-Fi'adaptateur MAC 

    - Identificateur global unique (GUID) généré de manière aléatoire 

- Informations sur le client, l’appareil et l’utilisateur 

    - Azure Active Directory (AD) ID d’appareil et ID utilisateur Azure : identifie de manière unique l’appareil, utilisateur, respectivement dans Azure Active Directory. 

    - ID de client Azure : GUID qui identifie votre organisation au sein Azure Active Directory. 

    - ID d’organisation Microsoft Defender pour point de terminaison : identificateur unique associé à l’entreprise à qui appartient l’appareil. Permet à Microsoft d’identifier s’il existe des problèmes affectant un ensemble sélectionné d’entreprises et le nombre d’entreprises touchés. 

    - Nom d’utilisateur principal : ID de messagerie de l’utilisateur. 

### <a name="product-and-service-usage-data"></a>Données d’utilisation des produits et services 

Les informations suivantes sont collectées uniquement pour l’application Microsoft Defender for Endpoint installée sur l’appareil. 

- Informations sur le package d’application, y compris le nom, la version et l’état de la mise à niveau de l’application. 

- Actions réalisées dans l’application. 

- Journaux de rapport d’incident générés par iOS. 

- Données d’utilisation de la mémoire. 

## <a name="optional-data"></a>Données facultatives 

Les données facultatives incluent les données de diagnostic et les données de commentaires du client. Les données de diagnostic facultatives nous aident à améliorer le produit et nous fournissent des informations complémentaires pour détecter, diagnostiquer et résoudre les problèmes. Ces données sont uniquement à des fins de diagnostic et ne sont pas requises pour le service lui-même. 

Les données de diagnostic facultatives incluent : 

- Utilisation de l’application, du processeur et du réseau pour Defender pour endpoint. 

- Fonctionnalités configurées par l’administrateur de Defender pour le point de terminaison. 

Les données de commentaires sont collectées par le biais de commentaires dans l’application fournis par l’utilisateur. 

- Adresse de messagerie de l’utilisateur, s’il choisit de la fournir.

- Type de commentaires (souris, frown, idée) et tous les commentaires envoyés par l’utilisateur. 

Pour plus d’informations, [voir plus d’informations sur la confidentialité.](https://aka.ms/mdatpiosprivacystatement)


