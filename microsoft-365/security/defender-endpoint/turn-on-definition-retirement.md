---
title: Activer le retrait de définition pour Antivirus Microsoft Defender
description: Activez le retrait de définition pour Antivirus Microsoft Defender.
keywords: Antivirus Microsoft Defender logiciel anti-programme malveillant, sécurité, defender, retrait de définition
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 06/10/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: 07248f2945e817dc7bdca6240d1de30830abd1e4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60207738"
---
# <a name="turn-on-definition-retirement"></a>Activer le retrait des définitions

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez configurer le retrait des définitions à l’aide de la stratégie de groupe. La définition du retrait vérifie si un ordinateur dispose des mises à jour de sécurité requises pour le protéger contre une vulnérabilité particulière. Si le système n’est pas vulnérable à l’exploit détecté par une définition, cette définition est « retirée ». Si toutes les informations de sécurité pour un protocole donné sont retirées, ce protocole n’est plus utilisé. L’activation de cette fonctionnalité permet d’améliorer les performances. Sur un ordinateur à jour avec toutes les dernières mises à jour de sécurité, la protection du réseau n’aura aucun impact sur les performances du réseau.

## <a name="use-group-policy-to-configure-definition-retirement"></a>Utiliser une stratégie de groupe pour configurer le retrait des définitions

1. Sur votre point de terminaison de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. Go to **Computer Configuration** \> **Administrative Templates** Windows \> **Components** \> **Antivirus Microsoft Defender** Network \> **Inspection System**.

3. Sélectionnez **Activer le retrait de définition.** Par défaut, cette stratégie est activée. Si la définition **n’est pas configurée,** le retrait de définition est activé.

4. Pour modifier la stratégie, sélectionnez le lien **modifier le paramètre de stratégie.**

5. Sélectionnez **Activé,** puis **OK.**

6. Déployez votre objet de stratégie de groupe mis à jour. Voir [La Console de gestion des stratégies de groupe.](/windows/win32/srvnodes/group-policy)

> [!TIP]
> Utilisez-vous des objets de stratégie de groupe en local ? Découvrez comment ils traduisent dans le cloud. [Analysez vos objets de stratégie](/mem/intune/configuration/group-policy-analytics)de groupe en local à l’aide de l’analyse de stratégie de groupe dans Microsoft Endpoint Manager - Aperçu .
