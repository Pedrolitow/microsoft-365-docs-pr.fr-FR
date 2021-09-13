---
title: Configurer les fonctionnalités de la réduction de la surface d’attaque
description: Utilisez Microsoft Intune, Microsoft Endpoint Configuration Manager, les cmdlets PowerShell et la stratégie de groupe pour configurer la réduction de la surface d’attaque.
keywords: asr, réduction de la surface d’attaque, windows defender, microsoft defender, antivirus, av
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: jweston-1
ms.author: v-jweston
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.date: 08/11/2021
ms.openlocfilehash: 79129d25c730f7948269c4291e53e3fc953af329
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59177708"
---
# <a name="configure-attack-surface-reduction-capabilities"></a>Configurer les fonctionnalités de la réduction de la surface d’attaque

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Defender pour le point de terminaison inclut plusieurs fonctionnalités de réduction de la surface d’attaque. Pour plus d’informations, voir [Vue d’ensemble des fonctionnalités de réduction de la surface d’attaque.](overview-attack-surface-reduction.md) Pour configurer la réduction de la surface d’attaque dans votre environnement, suivez les étapes suivantes :

1. [Activer l’isolation matérielle pour Microsoft Edge](/windows/security/threat-protection/microsoft-defender-application-guard/install-md-app-guard).

2. Activer le contrôle d’application.

   1. Passer en revue les stratégies de base Windows. Voir les [exemples de stratégies de base.](/windows/security/threat-protection/windows-defender-application-control/example-wdac-base-policies)
   2. Consultez le [Windows Defender de conception du contrôle d’application.](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-design-guide)
   3. Reportez-vous [au déploiement Windows Defender de contrôle d’application (WDAC).](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide)

3. [Activer l’accès contrôlé aux dossiers.](enable-controlled-folders.md)

4. [Activer la protection du réseau.](enable-network-protection.md)

5. [Activer Exploit Protection](enable-exploit-protection.md).

6. [Configurer les règles de réduction de la surface d’attaque.](enable-attack-surface-reduction.md)

7. Configurer votre pare-feu réseau.

   1. Obtenez une vue d’ensemble [Windows Defender pare-feu avec une sécurité avancée.](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)
   2. Utilisez le guide [de Windows Defender pare-feu](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-design-guide) pour décider de la façon dont vous souhaitez concevoir vos stratégies de pare-feu.
   3. Utilisez le [guide Windows Defender pare-feu](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-deployment-guide) pour configurer le pare-feu de votre organisation avec une sécurité avancée.

> [!TIP]
> Dans la plupart des cas, lorsque vous configurez des fonctionnalités de réduction de la surface d’attaque, vous pouvez choisir parmi plusieurs méthodes :

> - Microsoft Endpoint Manager (qui inclut désormais Microsoft Intune et Microsoft Endpoint Configuration Manager)
> - Stratégie de groupe
> - Cmdlets PowerShell
