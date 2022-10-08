---
title: Spécifier des ensembles de définitions supplémentaires pour l’inspection du trafic réseau pour Microsoft Defender Antivirus
description: Spécifiez des ensembles de définitions supplémentaires pour l’inspection du trafic réseau pour Microsoft Defender Antivirus.
keywords: Microsoft Defender Antivirus, logiciel anti-programme malveillant, sécurité, defender, inspection du trafic réseau
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 05/07/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.subservice: mde
ms.topic: article
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 53bf1b15e2d9b76e755c3c8484c0b1f1b7ad5043
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68221739"
---
# <a name="specify-additional-definition-sets-for-network-traffic-inspection"></a>Spécifier des ensembles de définitions supplémentaires pour l’inspection du trafic réseau

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Vous pouvez spécifier des ensembles de définitions supplémentaires pour l’inspection du trafic réseau à l’aide de stratégie de groupe.

## <a name="use-group-policy-to-specify-additional-definition-sets-for-network-traffic-inspection"></a>Utiliser stratégie de groupe pour spécifier des ensembles de définitions supplémentaires pour l’inspection du trafic réseau

1. Sur votre point de terminaison de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Accédez aux **composants** \> Windows Microsoft Defender **système d’inspection du réseau** **antivirus**\>.

3. Sélectionnez **Spécifier des ensembles de définitions supplémentaires pour l’inspection du trafic réseau**. Par défaut, cette stratégie est définie sur **Non configuré.**

4. Pour modifier la stratégie, sélectionnez le lien **modifier le paramètre de stratégie** .

5. Sélectionnez **Activé**, puis dans la section **Options** , **sélectionnez Afficher...**.

6. Ajoutez des entrées à la liste, puis sélectionnez **OK**.

   Chaque entrée doit être répertoriée en tant que paire nom-valeur, où le nom est une représentation sous forme de chaîne d’un GUID d’ensemble de définitions. Par exemple, le GUID du jeu de définitions permettant d’activer l’intelligence de sécurité de test est défini comme suit : `{b54b6ac9-a737-498e-9120-6616ad3bf590}`. La valeur n’étant pas utilisée, nous vous recommandons de la définir sur `0`.

7. Sélectionnez **OK**, puis déployez votre objet stratégie de groupe mis à jour. Consultez [stratégie de groupe console de gestion](/windows/win32/srvnodes/group-policy).

> [!TIP]
> Utilisez-vous des objets stratégie de groupe localement ? Découvrez comment ils se traduisent dans le cloud. [Analysez vos objets de stratégie de groupe locaux à l’aide de l’analytique stratégie de groupe dans Microsoft Endpoint Manager - Préversion](/mem/intune/configuration/group-policy-analytics).

## <a name="related-articles"></a>Articles connexes

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Comment créer et déployer des stratégies anti-programme malveillant : service de protection cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)