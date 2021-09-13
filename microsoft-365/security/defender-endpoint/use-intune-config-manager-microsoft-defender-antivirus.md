---
title: Configurer les Antivirus Microsoft Defender l’Microsoft Endpoint Manager
description: Utilisez Microsoft Endpoint Manager et Microsoft Intune pour configurer Antivirus Microsoft Defender et Endpoint Protection
keywords: scep, intune, endpoint protection, configuration
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 05/24/2021
ms.reviewer: phuijbr, oogunrinde
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.openlocfilehash: 68aad34932f63d1df183b562d87b0d539dab916b
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204635"
---
# <a name="use-microsoft-endpoint-manager-to-configure-and-manage-microsoft-defender-antivirus"></a>Utilisez Microsoft Endpoint Manager pour configurer et gérer les Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez utiliser [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) pour configurer des analyses Antivirus Microsoft Defender’analyse. [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) configuration [Manager](/mem/configmgr/core/understand/introduction) font désormais partie de Endpoint Manager.  

## <a name="configure-microsoft-defender-antivirus-scans-in-endpoint-manager"></a>Configurer des analyses Antivirus Microsoft Defender dans Endpoint Manager

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ), and sign in.

2. Accédez **à Sécurité des points de terminaison.**

3. Under **Manage**, choose **Antivirus**.

4. Sélectionnez votre stratégie Antivirus Microsoft Defender de sécurité. 

5. Sous **Gérer**, choisissez **Propriétés**.

6. Près de **Paramètres de configuration**, choisissez **Modifier**.

7. Développez  la section Analyse, puis examinez ou modifiez vos paramètres d’analyse.

8. Choose **Review + save**


> [!TIP]
> Besoin d’aide ? Voir [Gérer la sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security).


## <a name="related-articles"></a>Articles connexes

- [Articles de référence pour les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)