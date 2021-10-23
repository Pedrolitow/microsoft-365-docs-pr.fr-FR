---
title: Antivirus Microsoft Defender dans Windows
description: Découvrez comment gérer, configurer et utiliser l’Antivirus Microsoft Defender, une protection antivirus et un logiciel anti-programme malveillant intégrés.
keywords: Antivirus Microsoft Defender, windows defender, logiciel anti-programme malveillant, scep, system center endpoint protection, system center configuration manager, virus, programme malveillant, menace, détection, protection, sécurité
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: high
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 201f8c57057b1f8a314bdd42ba53042a4f6d00e3
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60552655"
---
# <a name="microsoft-defender-antivirus-in-windows"></a>Antivirus Microsoft Defender dans Windows

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)
- Antivirus Microsoft Defender

L’Antivirus Microsoft Defender est disponible dans Windows 10 et Windows 11, et dans les versions de Windows Server.

Antivirus Microsoft Defender est un composant majeur de votre protection nouvelle génération dans Microsoft Defender pour point de terminaison. Cette protection regroupe le Machine Learning, l’analyse big data, la recherche approfondie sur la résistance aux menaces et l’infrastructure cloud Microsoft pour protéger les appareils (ou les points de terminaison) de votre organisation. Antivirus Microsoft Defender est intégré à Windows et fonctionne avec Microsoft Defender pour point de terminaison pour fournir une protection sur votre appareil et dans le cloud.

## <a name="compatibility-with-other-antivirus-products"></a>Compatibilité avec d’autres produits antivirus

Si vous utilisez un produit antivirus/anti-programme malveillant non Microsoft sur votre appareil, vous pourrez peut-être exécuter Antivirus Microsoft Defender en mode passif en même temps que la solution antivirus non-Microsoft. Cela dépend du système d’exploitation utilisé et de l’intégration de votre appareil à Defender pour point de terminaison. Pour plus d’informations, consultez [Compatibilité Antivirus Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

## <a name="comparing-active-mode-passive-mode-and-disabled-mode"></a>Comparaison du mode actif, du mode passif et du mode désactivé

Le tableau suivant décrit à quoi s’attendre lorsque Antivirus Microsoft Defender est en mode actif, passif ou désactivé.

<br/><br/>

| Mode | Action exécutée |
|---|---|
| Mode actif | En mode actif, Antivirus Microsoft Defender est utilisé comme application antivirus principale sur l’appareil. Les fichiers sont analysés, les menaces corrigées et les menaces détectées sont répertoriées dans les rapports de sécurité de votre organisation et dans votre application Sécurité Windows. |
| Mode passif | En mode passif, Antivirus Microsoft Defender n’est pas utilisé comme application antivirus principale sur l’appareil. Les fichiers sont analysés et les menaces détectées sont signalées, mais les menaces ne sont pas corrigées par Antivirus Microsoft Defender. <br/><br/> **IMPORTANT** : Microsoft Defender Antivirus peut fonctionner en mode passif uniquement sur les points d'extrémité qui sont intégrés à Microsoft Defender pour point de terminaison. Voir [Configuration requise pour que Microsoft Defender Antivirus fonctionne en mode passif ](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode). |
| Désactivé ou désinstallé | En cas de désinstallation ou de désinstallation, Antivirus Microsoft Defender n’est pas utilisé. Les fichiers ne sont pas analysés et les menaces ne sont pas corrigées. En général, nous vous déconseillons de désactiver ou de désinstaller Antivirus Microsoft Defender. |

Pour plus d’informations, consultez [Compatibilité Antivirus Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

## <a name="check-the-state-of-microsoft-defender-antivirus-on-your-device"></a>Vérifier l’état des Antivirus Microsoft Defender sur votre appareil

Si vous souhaitez vérifier l’état de Antivirus Microsoft Defender sur votre appareil, vous pouvez utiliser l’une des différentes méthodes, telles que l’application Sécurité Windows ou Windows PowerShell.

### <a name="use-the-windows-security-app-to-check-status-of-microsoft-defender-antivirus"></a>Utiliser l’application Sécurité Windows pour vérifier l’état de Antivirus Microsoft Defender

1. Sur votre appareil Windows, sélectionnez le menu Démarrer et commencez à taper `Security`. Ouvrez ensuite l’application Sécurité Windows dans les résultats.

2. Sélectionnez **Protection contre les virus et les menaces**.

3. Sous **Protection contre les virus et menaces paramètres**, choisissez **Gérer les paramètres**.

Le nom de votre solution antivirus/anti-programme malveillant apparaît sur la page des paramètres.

### <a name="use-powershell-to-check-status-of-microsoft-defender-antivirus"></a>Utiliser PowerShell pour vérifier l’état de Antivirus Microsoft Defender

1. Sélectionnez le menu Démarrer, puis commencez à taper `PowerShell`. Ouvrez ensuite Windows PowerShell dans les résultats.

2. Tapez `Get-MpComputerStatus`.

3. Dans la liste des résultats, examinez la ligne **AMRunningMode**.

   - **Normal** signifie que Antivirus Microsoft Defender s’exécute en mode actif.

   - **Le mode passif** signifie Antivirus Microsoft Defender en cours d’exécution, mais n’est pas le produit antivirus/anti-programme malveillant principal sur votre appareil. Le mode passif est uniquement disponible pour les appareils qui sont intégrés à Microsoft Defender pour point de terminaison et qui répondent à certaines exigences. Pour en savoir plus, voir [Configuration requise pour que Microsoft Defender Antivirus fonctionne en mode passif ](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode).

   - **Le mode de blocage EDR** signifie que Antivirus Microsoft Defender est en cours d’exécution et qu’une fonctionnalité de [Microsoft Defender pour point de terminaison appelée EDR en mode bloc](edr-in-block-mode.md) est activée.

   - **Le mode passif** de SxS signifie que Microsoft Defender Antivirus est exécuté aux côtés d'un autre produit antivirus/antimalware et [qu'une analyse périodique limitée est utilisée](limited-periodic-scanning-microsoft-defender-antivirus.md).

> [!TIP]
> Pour en savoir plus sur l’applet de commande PowerShell Get-MpComputerStatus, consultez l’article de référence [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

## <a name="get-your-antivirusantimalware-platform-updates"></a>Obtenir les mises à jour de votre plateforme antivirus/anti-programme malveillant

Il est important de maintenir à jour Antivirus Microsoft Defender ou toute solution antivirus/anti-programme malveillant. Microsoft publie régulièrement des mises à jour pour vous assurer que vos appareils disposent des dernières technologies pour se protéger contre les nouveaux programmes malveillants et techniques d’attaque. Pour plus d’informations, consultez [Gérer les mises à jour Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender sur Windows Server](microsoft-defender-antivirus-on-windows-server.md)
- [Configuration et gestion d’Antivirus Microsoft Defender](configuration-management-reference-microsoft-defender-antivirus.md)
- [Évaluer la protection de l’Antivirus Microsoft Defender](evaluate-microsoft-defender-antivirus.md)
