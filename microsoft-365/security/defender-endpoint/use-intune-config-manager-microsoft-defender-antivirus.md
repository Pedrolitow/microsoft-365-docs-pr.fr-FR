---
title: Configurer les Antivirus Microsoft Defender à l’aide Microsoft Endpoint Manager
description: Utilisez Microsoft Endpoint Manager et Microsoft Intune pour configurer Antivirus Microsoft Defender et Endpoint Protection
keywords: scep, intune, endpoint protection, configuration
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 12/16/2021
ms.reviewer: phuijbr, oogunrinde
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 1eb126481cc9872c42906e0311d1c771da44c693
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2021
ms.locfileid: "61560194"
---
# <a name="use-microsoft-endpoint-manager-to-configure-and-manage-microsoft-defender-antivirus"></a>Utilisez Microsoft Endpoint Manager pour configurer et gérer les Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Vous pouvez utiliser [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) pour configurer des analyses Antivirus Microsoft Defender’analyse. [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) Configuration [Manager](/mem/configmgr/core/understand/introduction) font désormais partie de Endpoint Manager.

## <a name="configure-microsoft-defender-antivirus-scans-in-endpoint-manager"></a>Configurer des analyses Antivirus Microsoft Defender dans Endpoint Manager

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ), and sign in.

2. Accédez **à Sécurité des points de terminaison.**

3. Under **Manage**, choose **Antivirus**.

4. Sélectionnez votre stratégie Antivirus Microsoft Defender de sécurité.

5. Sous **Gérer**, choisissez **Propriétés**.

6. Près de **Paramètres de configuration**, choisissez **Modifier**.

   > [!IMPORTANT]
   > Les paramètres antivirus AllowOnAccessProtection et AllowIntrusionPreventionSystem sont officiellement supprimés et en tant que tels ne peuvent pas être configurés. 

7. Développez  la section Analyse, puis examinez ou modifiez vos paramètres d’analyse.

8. Choose **Review + save**.

> [!TIP]
> Besoin d’aide ? Voir [Gérer la sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security).

## <a name="related-articles"></a>Articles connexes

- [Articles de référence pour les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
