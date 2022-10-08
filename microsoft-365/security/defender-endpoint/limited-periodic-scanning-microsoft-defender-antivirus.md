---
title: Activer la fonctionnalité d’analyse périodique Microsoft Defender Antivirus limitée
description: L’analyse périodique limitée vous permet d’utiliser Microsoft Defender Antivirus en plus de vos autres fournisseurs AV installés
keywords: lps, limité, périodique, analyse, analyse, compatibilité, tiers, autre av, désactiver
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.collection:
- m365-security
- tier3
search.appverid: met150
ms.openlocfilehash: 5f897e84e5ce174e88565b9cce5712cb66e00819
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68224929"
---
# <a name="use-limited-periodic-scanning-in-microsoft-defender-antivirus"></a>Utilisez une analyse périodique limitée dans Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

L’analyse périodique limitée est un type spécial de détection et de correction des menaces qui peut être activé lorsque vous avez installé un autre produit antivirus sur un appareil Windows 10 ou Windows 11.

Il ne peut être activé que dans certaines situations. Pour plus d’informations sur l’analyse périodique limitée et le fonctionnement de Microsoft Defender Antivirus avec d’autres produits antivirus, consultez [Microsoft Defender compatibilité](microsoft-defender-antivirus-compatibility.md) antivirus.

**Microsoft ne recommande pas d’utiliser cette fonctionnalité dans les environnements d’entreprise. Il s’agit d’une fonctionnalité principalement destinée aux consommateurs.** Cette fonctionnalité utilise uniquement un sous-ensemble limité des fonctionnalités antivirus Microsoft Defender pour détecter les programmes malveillants, et ne sera pas en mesure de détecter la plupart des programmes malveillants et des logiciels potentiellement indésirables. En outre, les fonctionnalités de gestion et de création de rapports seront limitées. Microsoft recommande aux entreprises de choisir leur solution antivirus principale et de l’utiliser exclusivement.

## <a name="how-to-enable-limited-periodic-scanning"></a>Comment activer l’analyse périodique limitée

Par défaut, Microsoft Defender Antivirus s’active sur un Windows 10 ou un appareil Windows 11 s’il n’y a aucun autre produit antivirus installé, ou si l’autre produit est obsolète, a expiré ou ne fonctionne pas correctement.

Si Microsoft Defender Antivirus est activé, les options habituelles s’affichent pour le configurer sur cet appareil :

:::image type="content" source="images/vtp-wdav.png" alt-text="Application Sécurité Windows affichant Microsoft Defender options antivirus, notamment les options d’analyse, les paramètres et les options de mise à jour" lightbox="images/vtp-wdav.png":::

Si un autre produit antivirus est installé et fonctionne correctement, Microsoft Defender Antivirus se désactive. L’application Sécurité Windows modifie la section **Protection contre les menaces & virus** pour afficher l’état du produit AV et fournit un lien vers les options de configuration du produit.

Sous tous les produits AV tiers, un nouveau lien s’affiche en tant **qu’Microsoft Defender options antivirus**. Cliquez sur ce lien pour afficher le bouton bascule qui permet une analyse périodique limitée. Notez que l’option périodique limitée est un bouton bascule pour activer ou désactiver l’analyse périodique. 

Le fait de faire glisser le commutateur sur **Activé** affiche les options d’antivirus Microsoft Defender standard sous le produit AV tiers. L’option d’analyse périodique limitée apparaît en bas de la page.

## <a name="related-articles"></a>Articles connexes

- [Configurer la protection comportementale, heuristique et en temps réel.](configure-protection-features-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)