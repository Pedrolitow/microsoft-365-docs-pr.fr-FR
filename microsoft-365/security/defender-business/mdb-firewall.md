---
title: Pare-feu dans Microsoft Defender pour les PME
description: En savoir plus sur Windows Defender Pare-feu dans Microsoft Defender pour les PME, notamment les paramètres de configuration
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 77c2042ace89a133b9be8995ef817c1fe3766a07
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861397"
---
# <a name="firewall-in-microsoft-defender-for-business"></a>Pare-feu dans Microsoft Defender pour les PME

> [!NOTE]
> Microsoft Defender pour les PME est désormais inclus dans [Microsoft 365 Business Premium](../../business-premium/index.md). 

Microsoft Defender pour les PME inclut des fonctionnalités de pare-feu avec [Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). La protection pare-feu permet de sécuriser les appareils avec des règles qui déterminent le trafic réseau autorisé à entrer ou à circuler à partir d’appareils. 

Vous pouvez utiliser la protection pare-feu pour spécifier s’il faut autoriser ou bloquer des connexions sur des appareils à différents emplacements. Par exemple, vos paramètres de pare-feu peuvent autoriser les connexions entrantes sur les appareils connectés au réseau interne de votre entreprise, mais empêcher ces connexions lorsque l’appareil se trouve sur un réseau avec des appareils non approuvés.

**Cet article décrit :**

- [Paramètres de pare-feu par défaut dans Defender pour Entreprises](#default-firewall-settings-in-defender-for-business)
- [Paramètres de pare-feu que vous pouvez configurer dans Defender entreprise](#firewall-settings-you-can-configure-in-defender-for-business)

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

## <a name="default-firewall-settings-in-defender-for-business"></a>Paramètres de pare-feu par défaut dans Defender pour Entreprises

Microsoft Defender pour les PME inclut des stratégies et des paramètres de pare-feu par défaut pour protéger les appareils de votre entreprise dès le premier jour. Dès que les appareils de votre entreprise sont intégrés à Microsoft Defender pour les PME, votre stratégie de pare-feu par défaut fonctionne comme suit :

- Les connexions sortantes à partir d’appareils sont autorisées par défaut, quel que soit l’emplacement.
- Lorsque les appareils sont connectés au réseau de votre entreprise, toutes les connexions entrantes sont bloquées par défaut.
- Lorsque les appareils sont connectés à un réseau public ou privé, toutes les connexions entrantes sont bloquées par défaut.

Dans Microsoft Defender pour les PME, vous pouvez définir des exceptions pour bloquer ou autoriser les connexions entrantes. Vous définissez ces exceptions en créant des règles personnalisées. Consultez [Gérer les règles personnalisées pour les stratégies de pare-feu](mdb-custom-rules-firewall.md).

## <a name="firewall-settings-you-can-configure-in-defender-for-business"></a>Paramètres de pare-feu que vous pouvez configurer dans Defender entreprise

Microsoft Defender pour les PME inclut la protection pare-feu par le biais du pare-feu Windows Defender. Le tableau suivant répertorie les paramètres qui peuvent être configurés pour la protection pare-feu dans Microsoft Defender pour les PME.

| Setting | Description |
|--|--|
| **Réseau de domaine** | Le profil réseau de domaine s’applique au réseau de votre entreprise. Les paramètres de pare-feu de votre réseau de domaine s’appliquent aux connexions entrantes lancées sur d’autres appareils qui se trouvent sur le même réseau. Par défaut, les connexions entrantes sont définies sur **Bloquer tout**.  |
| **Réseau public** | Le profil de réseau public s’applique à un réseau que vous pouvez utiliser dans un emplacement public, tel qu’un café ou un aéroport. Les paramètres de pare-feu pour les réseaux publics s’appliquent aux connexions entrantes lancées sur d’autres appareils qui se trouvent sur le même réseau. Étant donné qu’un réseau public peut inclure des appareils que vous ne connaissez pas ou ne faites pas confiance, les connexions entrantes sont définies sur **Bloquer tout** par défaut.  |
| **Réseau privé** | Le profil de réseau privé s’applique à un réseau dans un emplacement privé, tel que votre domicile. Les paramètres de pare-feu pour les réseaux privés s’appliquent aux connexions entrantes lancées sur d’autres appareils qui se trouvent sur le même réseau. En général, sur un réseau privé, il est supposé que tous les autres appareils sur le même réseau sont des appareils approuvés. Toutefois, par défaut, les connexions entrantes sont définies sur **Bloquer tout**. |
| **Règles personnalisées** | [Les règles personnalisées](mdb-custom-rules-firewall.md) vous permettent de bloquer ou d’autoriser des connexions spécifiques. Par exemple, supposons que vous souhaitez bloquer toutes les connexions entrantes sur les appareils connectés à un réseau privé, à l’exception des connexions via une application spécifique sur un appareil. Dans ce cas, vous devez définir **le réseau privé** pour bloquer toutes les connexions entrantes, puis ajouter une règle personnalisée pour définir l’exception. <br/><br/>Vous pouvez utiliser des règles personnalisées pour définir des exceptions pour des fichiers ou applications spécifiques, une adresse IP ou une plage d’adresses IP. <br/><br/>Selon le type de règle personnalisée que vous créez, voici quelques exemples de valeurs que vous pouvez utiliser : <br/><br/>Chemin du fichier d’application : `C:\Windows\System\Notepad.exe or %WINDIR%\Notepad.exe` <br/><br/>IP : adresse IPv4/IPv6 valide, telle que `192.168.11.0` ou `192.168.1.0/24` <br/><br/>IP : plage d’adresses IPv4/IPv6 valide, au format similaire `192.168.1.0-192.168.1.9` (sans espaces inclus) |

## <a name="next-steps"></a>Prochaines étapes

- [Gérer les paramètres de pare-feu dans Microsoft Defender pour les PME](mdb-custom-rules-firewall.md)
- [En savoir plus sur Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)
- [Afficher et gérer les incidents dans Microsoft Defender pour les PME](mdb-view-manage-incidents.md)
- [Répondre aux menaces et les atténuer dans Microsoft Defender pour les PME](mdb-respond-mitigate-threats.md)
- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)