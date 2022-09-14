---
title: Masquer l’interface antivirus Microsoft Defender
description: Vous pouvez masquer la vignette de protection contre les virus et les menaces dans l’application Sécurité Windows.
keywords: Verrouillage de l’interface utilisateur, mode sans tête, masquer l’application, masquer les paramètres, masquer l’interface
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.topic: article
ms.collection: M365-security-compliance
search.appverid: met150
ms.openlocfilehash: 6e507eb344f1dabc485bd89e68e9dcef8213419b
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67693992"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>Empêcher les utilisateurs de voir ou d’interagir avec l’interface utilisateur de l’Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez utiliser stratégie de groupe pour empêcher les utilisateurs sur les points de terminaison de voir l’interface antivirus Microsoft Defender. Vous pouvez également les empêcher de suspendre les analyses.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>Masquer l’interface antivirus Microsoft Defender

Dans Windows 10, les versions 1703, le masquage de l’interface masque les notifications antivirus Microsoft Defender et empêche l’affichage de la vignette Virus & threat protection dans l’application Sécurité Windows.

Avec le paramètre défini sur **Activé** :

:::image type="content" source="../../media/wdav-headless-mode-off-1703.png" alt-text="Le Sécurité Windows sans l’icône de bouclier et les sections de protection contre les virus et les menaces" lightbox="../../media/wdav-headless-mode-off-1703.png":::

Avec le paramètre défini sur **Désactivé** ou non configuré :

:::image type="content" source="../../media/wdav-headless-mode-1703.png" alt-text="La Sécurité Windows avec l’icône de bouclier et les sections de protection contre les menaces" lightbox="../../media/wdav-headless-mode-1703.png":::

> [!NOTE]
> Le masquage de l’interface empêche également l’affichage des notifications antivirus Microsoft Defender sur le point de terminaison. Microsoft Defender pour point de terminaison notifications s’affichent toujours. Vous pouvez également configurer individuellement [les notifications qui apparaissent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)

Dans les versions antérieures de Windows 10, le paramètre masque l’interface client Windows Defender. Si l’utilisateur tente de l’ouvrir, il reçoit un avertissement indiquant que « Votre administrateur système a un accès restreint à cette application ».

:::image type="content" source="../../media/wdav-headless-mode-1607.png" alt-text="Message d’avertissement lorsque le mode sans tête est activé dans Windows 10, versions antérieures à 1703" lightbox="../../media/wdav-headless-mode-1607.png":::

## <a name="use-group-policy-to-hide-the-microsoft-defender-antivirus-interface-from-users"></a>Utiliser stratégie de groupe pour masquer l’interface antivirus Microsoft Defender aux utilisateurs

1. Sur votre machine de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. À l’aide de **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Cliquez sur **Modèles d’administration**.

4. Développez l’arborescence sur **les composants Windows > l’interface client de l’antivirus Microsoft Defender >**.

5. Double-cliquez sur le paramètre **Activer le mode d’interface utilisateur sans tête** et définissez l’option **sur Activé**. Cliquez sur **OK**.

Consultez [Empêcher les utilisateurs de modifier localement les paramètres de](configure-local-policy-overrides-microsoft-defender-antivirus.md) stratégie pour plus d’options sur la prévention de la modification de la protection des utilisateurs sur leurs PC.

## <a name="prevent-users-from-pausing-a-scan"></a>Empêcher les utilisateurs de suspendre une analyse

Vous pouvez empêcher les utilisateurs de suspendre les analyses, ce qui peut être utile pour garantir que les analyses planifiées ou à la demande ne sont pas interrompues par les utilisateurs.

> [!NOTE]
> Ce paramètre n’est pas pris en charge sur Windows 10.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>Utiliser stratégie de groupe pour empêcher les utilisateurs de suspendre une analyse

1. Sur votre machine de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. À l’aide de **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Cliquez sur **Modèles d’administration**.

4. Développez l’arborescence pour accéder aux **composants** \> Windows de **l’analyse antivirus** \> Microsoft Defender.

5. Double-cliquez sur le paramètre **Autoriser les utilisateurs à suspendre l’analyse** et définissez l’option **sur Désactivé**. Cliquez sur **OK**.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-articles"></a>Articles connexes

- [Configurer les notifications qui s’affichent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)
- [Configurer l’interaction de l’utilisateur final avec l’antivirus Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
