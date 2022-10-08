---
title: Activer la mise hors service des définitions pour Microsoft Defender Antivirus
description: Activez la mise hors service des définitions pour Microsoft Defender Antivirus.
keywords: Microsoft Defender antivirus, logiciel anti-programme malveillant, sécurité, défenseur, mise hors service des définitions
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 06/10/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.subservice: mde
ms.topic: article
ms.collection:
- m365-security
- tier3
search.appverid: met150
ms.openlocfilehash: 0507707d946ea14be53a12c7e45fc8f9b317e749
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68222713"
---
# <a name="turn-on-definition-retirement"></a>Activer la mise hors service des définitions

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Vous pouvez configurer la mise hors service des définitions à l’aide de stratégie de groupe. La mise hors service des définitions vérifie si un ordinateur dispose des mises à jour de sécurité nécessaires pour le protéger contre une vulnérabilité particulière. Si le système n’est pas vulnérable à l’exploit détecté par une définition, cette définition est « retirée ». Si toutes les informations de sécurité d’un protocole donné sont supprimées, ce protocole n’est plus analysé. L’activation de cette fonctionnalité permet d’améliorer les performances. Sur un ordinateur à jour avec toutes les dernières mises à jour de sécurité, la protection réseau n’aura aucun impact sur les performances du réseau.

## <a name="use-group-policy-to-configure-definition-retirement"></a>Utiliser stratégie de groupe pour configurer la mise hors service des définitions

1. Sur votre point de terminaison de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Accédez aux modèles **d’administration** de **configuration** \> de l’ordinateur **composants** \> \> Windows Microsoft Defender **système d’inspection réseau** **antivirus**\>.

3. Sélectionnez **Activer la mise hors service des définitions**. Par défaut, cette stratégie est activée. Si la définition **n’est pas configurée**, la mise hors service des définitions est activée.

4. Pour modifier la stratégie, sélectionnez le lien **modifier le paramètre de stratégie** .

5. Sélectionnez **Activé**, puis **sélectionnez OK**.

6. Déployez votre objet stratégie de groupe mis à jour. Consultez [stratégie de groupe console de gestion](/windows/win32/srvnodes/group-policy).

> [!TIP]
> Utilisez-vous des objets stratégie de groupe localement ? Découvrez comment ils se traduisent dans le cloud. [Analysez vos objets de stratégie de groupe locaux à l’aide de l’analytique stratégie de groupe dans Microsoft Endpoint Manager - Préversion](/mem/intune/configuration/group-policy-analytics).
