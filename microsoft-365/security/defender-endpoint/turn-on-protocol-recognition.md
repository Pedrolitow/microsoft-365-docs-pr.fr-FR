---
title: Activer la reconnaissance de protocole pour Antivirus Microsoft Defender
description: Activer la reconnaissance de protocole pour Antivirus Microsoft Defender.
keywords: Antivirus Microsoft Defender logiciel anti-programme malveillant, sécurité, defender, reconnaissance de protocole
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 02/21/2022
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: 221eff4af6bf8e77f29db84694bf3a683107fc8c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325173"
---
# <a name="turn-on-protocol-recognition"></a>Activer la reconnaissance de protocole

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ce paramètre de stratégie vous permet de configurer la reconnaissance de protocole pour la protection du réseau contre les attaques de vulnérabilités connues. Si vous activez ou ne configurez pas ce paramètre, la reconnaissance de protocole est activée. Si vous désactivez ce paramètre, la reconnaissance de protocole sera désactivée.

[!IMPORTANT]
Ce paramètre est désormais supprimé. 

## <a name="use-group-policy-to-configure-protocol-recognition"></a>Utiliser une stratégie de groupe pour configurer la reconnaissance de protocole

1. Sur votre point de terminaison de gestion des stratégies de groupe, ouvrez la [console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Go to **Computer Configuration** \> **Administrative Templates** \> **Windows Components** \> **Antivirus Microsoft Defender** \> **Network Inspection System**.

3. Sélectionnez **la reconnaissance de protocole**. Par défaut, cette stratégie est activée. S’il **n’est pas configuré**, le retrait de définition est activé.

4. Pour modifier la stratégie, sélectionnez le lien **modifier le paramètre de stratégie** .

5. **Sélectionnez Activé**, puis **OK**.

6. Déployez votre objet de stratégie de groupe mis à jour. Voir [Console de gestion des stratégies de groupe](/windows/win32/srvnodes/group-policy).

> [!TIP]
> Utilisez-vous des objets de stratégie de groupe en local ? Découvrez comment ils traduisent dans le cloud. [Analysez vos objets de stratégie](/mem/intune/configuration/group-policy-analytics) de groupe en local à l’aide de l’analyse de stratégie de groupe dans Microsoft Endpoint Manager - Aperçu.

## <a name="related-articles"></a>Articles connexes

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Comment créer et déployer des stratégies de logiciel anti-programme malveillant : service de protection cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)
