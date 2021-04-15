---
title: Définir la façon dont les appareils mobiles sont mis à jour par l'Antivirus Microsoft Defender
description: Gérer la façon dont les appareils mobiles, tels que les ordinateurs portables, doivent être mis à jour avec les mises à jour de la protection antivirus Microsoft Defender.
keywords: mises à jour, protection, planification des mises à jour, batterie, appareil mobile, ordinateur portable, bloc-notes, opt-in, microsoft update, wsus, override
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 826e1456de2aadf4031a91e30925a1e771d44f70
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51765586"
---
# <a name="manage-updates-for-mobile-devices-and-virtual-machines-vms"></a>Gérer les mises à jour pour les périphériques mobiles et les machines virtuelles

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Les appareils mobiles et les ordinateurs VM peuvent nécessiter une configuration plus importante pour s'assurer que les mises à jour n'ont pas d'impact sur les performances.

Deux paramètres sont utiles pour ces appareils :

- Opter pour Microsoft Update sur des ordinateurs mobiles sans connexion WSUS
- Empêcher les mises à jour des informations de sécurité lors de l'exécution sur batterie

Les articles suivants peuvent également être utiles dans les situations suivantes :
- [Configuration des analyses de rattrapage et de planification](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Gérer les mises à jour des points de terminaison qui ne sont pas à jour](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Guide de déploiement de l'Antivirus Microsoft Defender dans un environnement d'infrastructure de bureau virtuel (VDI)](deployment-vdi-microsoft-defender-antivirus.md)

## <a name="opt-in-to-microsoft-update-on-mobile-computers-without-a-wsus-connection"></a>Opter pour Microsoft Update sur des ordinateurs mobiles sans connexion WSUS

Vous pouvez utiliser Microsoft Update pour maintenir à jour les informations de sécurité sur les appareils mobiles exécutant l'Antivirus Microsoft Defender lorsqu'ils ne sont pas connectés au réseau d'entreprise ou n'ont pas de connexion WSUS. 

Cela signifie que les mises à jour de protection peuvent être livrées aux appareils (via Microsoft Update) même si vous avez définie WSUS pour remplacer Microsoft Update.

Vous pouvez choisir Microsoft Update sur l'appareil mobile de l'une des manières suivantes :

- Modifiez le paramètre avec la stratégie de groupe.
- Utilisez un script VBScript pour créer un script, puis exécutez-le sur chaque ordinateur de votre réseau.
- Choisissez manuellement chaque ordinateur de votre réseau via le menu **Paramètres.**

### <a name="use-group-policy-to-opt-in-to-microsoft-update"></a>Utiliser la stratégie de groupe pour opter pour Microsoft Update

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe que vous souhaitez configurer et sélectionnez **Modifier.**

2. Dans **l'Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

3. Sélectionnez **stratégies** **puis modèles d'administration.**

4. Développez l'arborescence **des composants Windows**  >  **Microsoft Defender Antivirus** Signature  >  **Updates**.

5. Définissez **Autoriser les mises à** jour des informations de sécurité de Microsoft Update sur **Activé,** puis sélectionnez **OK.**


### <a name="use-a-vbscript-to-opt-in-to-microsoft-update"></a>Utiliser un VBScript pour opter pour Microsoft Update

1. Utilisez les instructions de l'article MSDN [Opt-In to Microsoft Update](/windows/win32/wua_sdk/opt-in-to-microsoft-update) pour créer le VBScript.

2. Exécutez le script VBScript que vous avez créé sur chaque ordinateur de votre réseau.

### <a name="manually-opt-in-to-microsoft-update"></a>Opter manuellement pour Microsoft Update

1. Ouvrez **Windows Update** dans Update **& paramètres** de sécurité sur l'ordinateur que vous souhaitez utiliser.

2. Sélectionnez **Options avancées.**

3. Cochez la case pour me fournir les mises à jour d'autres produits **Microsoft lorsque je met à jour Windows.**

## <a name="prevent-security-intelligence-updates-when-running-on-battery-power"></a>Empêcher les mises à jour des informations de sécurité lors de l'exécution sur batterie

Vous pouvez configurer l'Antivirus Microsoft Defender pour télécharger uniquement les mises à jour de protection lorsque le PC est connecté à une source d'alimentation câblé. 

### <a name="use-group-policy-to-prevent-security-intelligence-updates-on-battery-power"></a>Utiliser la stratégie de groupe pour empêcher les mises à jour des informations de sécurité sur l'alimentation de la batterie

1.  Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, choisissez l'objet de stratégie de groupe que vous souhaitez configurer et ouvrez-le pour modification.

2.  Dans **l'Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

3.  Sélectionnez **stratégies** **puis modèles d'administration.**

4.  Développez l'arborescence des **composants Windows** Mises à jour des signatures de l'antivirus  >  **Microsoft Defender,** puis définissez Autoriser les mises à jour de l'intelligence de sécurité lorsque vous exécutez l'alimentation sur batterie  >  sur **Désactivé.**  Puis sélectionnez **OK**. 

Cette action empêche le téléchargement des mises à jour de protection lorsque le PC est sur batterie.

## <a name="related-articles"></a>Articles connexes

- [Gérer les mises à jour de l'Antivirus Microsoft Defender et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Mettre à jour et gérer l'Antivirus Microsoft Defender dans Windows 10](deploy-manage-report-microsoft-defender-antivirus.md)