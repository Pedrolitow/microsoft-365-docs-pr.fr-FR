---
title: Intégrer Office 365 Advanced Threat Protection avec Microsoft Defender Advanced Threat Protection
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.date: 04/13/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 414fa693-d7b7-4a1d-a387-ebc3b6a52889
ms.collection:
- M365-security-compliance
description: Intégrer Office 365 Advanced Threat Protection avec Microsoft Defender Advanced Threat Protection pour consulter des informations plus détaillées sur la gestion des menaces.
ms.openlocfilehash: e416d70baf7498b0163d5bd8aa8e923585a5e5a4
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43633808"
---
# <a name="integrate-office-365-advanced-threat-protection-with-microsoft-defender-advanced-threat-protection"></a>Intégrer Office 365 Advanced Threat Protection avec Microsoft Defender Advanced Threat Protection

Si vous êtes membre de l’équipe de sécurité de votre organisation, vous pouvez intégrer [Office 365 Advanced Threat Protection](office-365-atp.md) et les fonctionnalités d’enquête et de réponse associées avec [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection). Cela peut vous aider à comprendre rapidement si les ordinateurs des utilisateurs sont exposés lorsque vous étudiez les menaces dans Office 365. Par exemple, une fois l’intégration activée, vous pouvez voir la liste des ordinateurs utilisés par les destinataires d’un message électronique détecté, ainsi que le nombre d’alertes récentes de la protection avancée contre les menaces de Microsoft Defender.
  
L’image suivante montre l’onglet **appareils** qui apparaît lorsque l’intégration de Microsoft Defender ATP est activée :
  
![Lorsque l’ATP Microsoft Defender est activé, vous pouvez voir une liste des périphériques avec des alertes.](../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG)
  
Dans cet exemple, vous pouvez voir que les destinataires du message électronique ont quatre appareils et que l’un d’entre eux comporte une alerte. Si vous cliquez sur le lien d’un appareil, celui-ci s’ouvre dans le centre de sécurité Microsoft Defender.
  
## <a name="requirements"></a>Configuration requise

- Votre organisation doit disposer d’Office 365 ATP plan 2 (ou Office 365 E5) et de Microsoft Defender ATP.
    
- Vous devez être un administrateur général ou disposer d’un rôle d’administrateur de sécurité (tel que administrateur de sécurité) affecté dans le [Centre de sécurité &amp; ](https://protection.office.com)et de conformité. (Voir [Permissions in &amp; the Security Compliance Center](permissions-in-the-security-and-compliance-center.md))
    
- Vous devez avoir accès à l' [Explorateur (ou aux détections en temps réel)](threat-explorer.md) dans le centre de sécurité & conformité et au centre de sécurité Microsoft Defender.
    
## <a name="to-integrate-office-365-atp-with-microsoft-defender-atp"></a>Pour intégrer la protection avancée contre les menaces Office 365 à Microsoft Defender ATP

L’intégration de la fonctionnalité ATP Office 365 à Microsoft Defender ATP est configurée à l’aide du centre de sécurité & de la sécurité et du centre de sécurité Microsoft Defender.
  
1. En tant qu’administrateur général ou administrateur de la sécurité, [https://protection.office.com](https://protection.office.com) accédez à et connectez-vous avec votre compte professionnel ou scolaire.
    
2. Choisissez **Threat management** \> **Explorateur**de gestion des menaces.<br>![Explorateur dans le menu gestion des menaces](../../media/ThreatMgmt-Explorer-nav.png)<br>
    
3. Dans le coin supérieur droit de l’écran, sélectionnez **paramètres WDATP**.
    
4. Dans la boîte de dialogue connexion Microsoft Defender ATP, activez **connexion à Windows ATP**.<br>![Connexion ATP Microsoft Defender](../../media/Explorer-WDATPConnection-dialog.png)<br>
    
5. Activez la connexion dans le centre de sécurité Microsoft Defender ([https://securitycenter.windows.com](https://securitycenter.windows.com)).

## <a name="related-topics"></a>Voir aussi

[Fonctionnalités d’enquête et de réponse aux menaces dans Office 365](office-365-ti.md)
  
[Protection avancée contre les menaces dans Office 365](office-365-atp.md)
  

