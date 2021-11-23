---
title: Planifier les mises à jour Antivirus Microsoft Defender protection des données
description: Planifier le jour, l’heure et l’intervalle de téléchargement des mises à jour de protection
keywords: mises à jour, bases de référence de sécurité, planifier des mises à jour
ms.prod: m365-security
search.appverid: met150
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 32ca742e4b8a964200f0effac1b6186ed64a911b
ms.sourcegitcommit: 2e05865beeb2051fd9ece212a46179310b946a46
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2021
ms.locfileid: "61148646"
---
# <a name="manage-the-schedule-for-when-protection-updates-should-be-downloaded-and-applied"></a>Gérer le calendrier de téléchargement et d’application des mises à jour de protection

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Antivirus Microsoft Defender vous permet de déterminer quand il doit rechercher et télécharger les mises à jour.

Vous pouvez planifier des mises à jour pour vos points de terminaison en :

- Spécification du jour de la semaine pour vérifier les mises à jour de la protection
- Spécification de l’intervalle de recherche des mises à jour de la protection
- Spécification de l’heure de recherche des mises à jour de la protection

Vous pouvez également aléatoirer les heures où chaque point de terminaison vérifie et télécharge les mises à jour de la protection. Pour plus [d’informations, consultez](scheduled-catch-up-scans-microsoft-defender-antivirus.md) la rubrique Analyses de planification.

## <a name="use-configuration-manager-to-schedule-protection-updates"></a>Utiliser Configuration Manager pour planifier des mises à jour de la protection

1. Sur votre console Microsoft Endpoint Manager, ouvrez la stratégie anti-programme malveillant à modifier (cliquez sur Ressources et conformité dans  le volet de navigation à gauche, puis développez l’arborescence Vue d’ensemble Endpoint Protection **Stratégies** \>  \> **anti-programme** malveillant)

2. Go to the **Security intelligence updates** section.

3. Pour vérifier et télécharger les mises à jour à un moment certain :
      1. Définissez **Check for Endpoint Protection security intelligence updates at a specific interval...** to **0**.
      2. Définissez La vérification Endpoint Protection mises à jour de l’intelligence de sécurité **quotidiennement à...** au moment où les mises à jour doivent être vérifiées.
      3
4. Pour vérifier et télécharger les mises à jour sur un intervalle continu, définissez vérifier les mises à jour de l’intelligence de sécurité Endpoint Protection à un intervalle **spécifique...** au nombre d’heures qui doivent se produire entre les mises à jour.

5. [Déployez la stratégie mise à jour comme d’habitude.](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers)

## <a name="use-group-policy-to-schedule-protection-updates"></a>Utiliser une stratégie de groupe pour planifier des mises à jour de la protection

> [!IMPORTANT]
> Par défaut, Antivirus Microsoft Defender recherche une mise à jour 15 minutes avant l’heure des analyses programmées. L’activation de ces paramètres remplace cette valeur par défaut.

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

3. Cliquez **sur Stratégies** **puis Modèles d’administration.**

4. Développez l’arborescence **Windows composants Antivirus Microsoft Defender** mises à jour Signature Intelligence et \>  \>  configurez les paramètres suivants :

    1. Double-cliquez sur **Spécifier le jour de** la semaine pour vérifier le paramètre des mises à jour de l’intelligence de la sécurité et définir l’option **sur Activé.** Entrez le jour de la semaine pour vérifier les mises à jour. Cliquez sur **OK**.
    2. Double-cliquez sur **spécifier l’intervalle pour vérifier** le paramètre des mises à jour de l’intelligence de la sécurité et définir l’option **sur Activé**. Entrez le nombre d’heures entre les mises à jour. Cliquez sur **OK**.
    3. Double-cliquez sur **le paramètre Spécifier l’heure** à définir pour les mises à jour de l’intelligence de la sécurité et définissez l’option **sur Activé.** Entrez l’heure à quel moment les mises à jour doivent être vérifiées. L’heure est basée sur l’heure locale du point de terminaison. Cliquez sur **OK**.

## <a name="use-powershell-cmdlets-to-schedule-protection-updates"></a>Utiliser les cmdlets PowerShell pour planifier des mises à jour de protection

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter les [cmdlets](/powershell/module/defender/) Antivirus Microsoft Defender et Antivirus Defender.

## <a name="use-windows-management-instruction-wmi-to-schedule-protection-updates"></a>Utiliser Windows Management Instruction (WMI) pour planifier des mises à jour de la protection

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

Pour plus d’informations et les paramètres autorisés, voir les informations suivantes :

- [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="related-articles"></a>Articles connexes

- [Déployer Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Gérer les mises Antivirus Microsoft Defender jour et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Gérer les mises à jour des points de terminaison qui ne sont plus à jour](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
