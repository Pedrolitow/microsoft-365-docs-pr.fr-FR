---
title: Activer la reconnaissance de protocole pour Antivirus Microsoft Defender
description: Activer la reconnaissance de protocole pour Antivirus Microsoft Defender.
keywords: Antivirus Microsoft Defender, anti-programme malveillant, sécurité, defender, reconnaissance de protocole
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 05/07/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: 9baaedad2895c9d5a3b26cab0289f7bb86af17cf
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60193948"
---
# <a name="turn-on-protocol-recognition"></a>Activer la reconnaissance de protocole

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Ce paramètre de stratégie vous permet de configurer la reconnaissance de protocole pour la protection du réseau contre les attaques de vulnérabilités connues. Si vous activez ou ne configurez pas ce paramètre, la reconnaissance de protocole est activée. Si vous désactivez ce paramètre, la reconnaissance de protocole sera désactivée.

## <a name="use-group-policy-to-configure-protocol-recognition"></a>Utiliser une stratégie de groupe pour configurer la reconnaissance de protocole

1. Sur votre point de terminaison de gestion des stratégies de groupe, ouvrez la [console de gestion des stratégies de groupe.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. Go to **Computer Configuration** \> **Administrative Templates** Windows \> **Components** \> **Antivirus Microsoft Defender** Network \> **Inspection System**.

3. Sélectionnez **la reconnaissance de protocole.** Par défaut, cette stratégie est activée. Si la définition **n’est pas configurée,** le retrait de définition est activé.

4. Pour modifier la stratégie, sélectionnez le lien **modifier le paramètre de stratégie.**

5. Sélectionnez **Activé,** puis **OK**.

6. Déployez votre objet de stratégie de groupe mis à jour. Voir [La Console de gestion des stratégies de groupe.](/windows/win32/srvnodes/group-policy)

> [!TIP]
> Utilisez-vous des objets de stratégie de groupe en local ? Découvrez comment ils traduisent dans le cloud. [Analysez vos objets de stratégie](/mem/intune/configuration/group-policy-analytics)de groupe en local à l’aide de l’analyse de stratégie de groupe dans Microsoft Endpoint Manager - Aperçu .

## <a name="related-articles"></a>Articles connexes

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Comment créer et déployer des stratégies de logiciel anti-programme malveillant : service de protection cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)