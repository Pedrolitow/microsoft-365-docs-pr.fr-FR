---
title: Spécifier des ensembles de définitions supplémentaires pour l’inspection du trafic réseau Antivirus Microsoft Defender
description: Spécifiez des ensembles de définitions supplémentaires pour l’inspection du trafic Antivirus Microsoft Defender.
keywords: Antivirus Microsoft Defender, anti-programme malveillant, sécurité, defender, inspection du trafic réseau
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.date: 05/07/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.openlocfilehash: 82568df0a6ad2225fd31b4c0fa4a654710f1e98b
ms.sourcegitcommit: de5fce90de22ba588e75e1a1d2e87e03b9e25ec7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2021
ms.locfileid: "52300194"
---
# <a name="specify-additional-definition-sets-for-network-traffic-inspection"></a>Spécifier des ensembles de définitions supplémentaires pour l’inspection du trafic réseau

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez spécifier des ensembles de définitions supplémentaires pour l’inspection du trafic réseau à l’aide de la stratégie de groupe.

## <a name="use-group-policy-to-specify-additional-definition-sets-for-network-traffic-inspection"></a>Utiliser une stratégie de groupe pour spécifier des ensembles de définitions supplémentaires pour l’inspection du trafic réseau

1. Sur votre point de terminaison de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. Go to **Windows Components**  >  **Antivirus Microsoft Defender**  >  **Network Inspection System**. 

3. Sélectionnez **Spécifier des jeux de définitions supplémentaires pour l’inspection du trafic réseau.** Par défaut, cette stratégie est définie sur **Non configuré.** 

4. Pour modifier la stratégie, sélectionnez le lien **modifier le paramètre de stratégie.**

5. Sélectionnez **Activé,** puis, dans la section **Options,** **sélectionnez Afficher...**.

6. Ajoutez des entrées à la liste, puis sélectionnez **OK**. 

   Chaque entrée doit être répertoriée en tant que paire nom-valeur, où le nom est une représentation sous la chaîne d’un GUID de jeu de définitions. Par exemple, le GUID de définition défini pour activer l’intelligence de sécurité de test est défini comme : `{b54b6ac9-a737-498e-9120-6616ad3bf590}` . La valeur n’est pas utilisée, donc nous vous recommandons de la définir sur `0` . 

7. Sélectionnez **OK,** puis déployez votre objet de stratégie de groupe mis à jour. Voir [La Console de gestion des stratégies de groupe.](/windows/win32/srvnodes/group-policy)

> [!TIP]
> Utilisez-vous des objets de stratégie de groupe en local ? Découvrez comment ils traduisent dans le cloud. [Analysez vos objets de stratégie](/mem/intune/configuration/group-policy-analytics)de groupe en local à l’aide de l’analyse de stratégie de groupe dans Microsoft Endpoint Manager - Aperçu . 
  
## <a name="related-articles"></a>Articles connexes

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
 
- [Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md)

- [Comment créer et déployer des stratégies de logiciel anti-programme malveillant : service de protection cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)