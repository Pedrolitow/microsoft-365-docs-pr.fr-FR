---
title: Masquer l’interface Antivirus Microsoft Defender de données
description: Vous pouvez masquer la vignette de protection contre les virus et les menaces dans Sécurité Windows application.
keywords: Verrouillage de l’interface utilisateur, mode sans en-tête, masquer l’application, masquer les paramètres, masquer l’interface
ms.prod: m365-security
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
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 26a792a753b0855a12cd994256cef93a64a5a159
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469226"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>Empêcher les utilisateurs de voir ou d’interagir avec Antivirus Microsoft Defender’interface utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Vous pouvez utiliser la stratégie de groupe pour empêcher les utilisateurs sur les points de terminaison de voir Antivirus Microsoft Defender interface utilisateur. Vous pouvez également les empêcher de mettre en pause les analyses.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>Masquer l’interface Antivirus Microsoft Defender de données

Dans Windows 10, versions 1703, le masquage de l’interface masquera les notifications Antivirus Microsoft Defender et empêchera l’apparition de la vignette de protection contre les menaces & virus dans l’application Sécurité Windows.

Avec le paramètre **activé :**

:::image type="content" source="../../media/wdav-headless-mode-off-1703.png" alt-text="Le Sécurité Windows sans l’icône de bouclier et les sections de protection contre les virus et menaces" lightbox="../../media/wdav-headless-mode-off-1703.png":::

Avec le paramètre désactivé **ou** non configuré :

:::image type="content" source="../../media/wdav-headless-mode-1703.png" alt-text="Sections Sécurité Windows icône de bouclier et protection contre les menaces" lightbox="../../media/wdav-headless-mode-1703.png":::

> [!NOTE]
> Le masquage de l’interface empêchera Antivirus Microsoft Defender notifications d’apparaître sur le point de terminaison. Les notifications de Microsoft Defender pour point de terminaison s’affichent toujours. Vous pouvez également configurer individuellement [les notifications qui apparaissent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)

Dans les versions antérieures de Windows 10, le paramètre masque l’interface Windows Defender client. Si l’utilisateur tente de l’ouvrir, il reçoit un avertissement signalant que l’administrateur système a un accès restreint à cette application.

:::image type="content" source="../../media/wdav-headless-mode-1607.png" alt-text="Message d’avertissement lorsque le mode sans en-tête est activé Windows 10 versions antérieures à 1703" lightbox="../../media/wdav-headless-mode-1607.png":::

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>Utiliser une stratégie de groupe pour masquer l’interface de Microsoft Defender AV aux utilisateurs

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier**.

2. À **l’aide de l’Éditeur de gestion des stratégies de** groupe, allez **à configuration ordinateur**.

3. Cliquez **sur Modèles d’administration**.

4. Développez l’arborescence **Windows composants > Antivirus Microsoft Defender >'interface client**.

5. Double-cliquez sur le **paramètre Activer le mode d’interface** utilisateur sans en-tête et définissez l’option **sur Activé**. Cliquez sur **OK**.

Voir [Empêcher les utilisateurs de modifier localement les paramètres](configure-local-policy-overrides-microsoft-defender-antivirus.md) de stratégie pour plus d’options pour empêcher les utilisateurs de modifier la protection sur leurs PC.

## <a name="prevent-users-from-pausing-a-scan"></a>Empêcher les utilisateurs de mettre une analyse en pause

Vous pouvez empêcher les utilisateurs de mettre en pause les analyses, ce qui peut être utile pour vous assurer que les analyses programmées ou à la demande ne sont pas interrompues par les utilisateurs.

> [!NOTE]
> Ce paramètre n’est pas pris en charge sur Windows 10.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>Utiliser une stratégie de groupe pour empêcher les utilisateurs de mettre une analyse en pause

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier**.

2. À **l’aide de l’Éditeur de gestion des stratégies de** groupe, allez **à configuration ordinateur**.

3. Cliquez **sur Modèles d’administration**.

4. Développez l’arborescence **Windows composants Antivirus Microsoft Defender** \>  \> **Scan**.

5. Double-cliquez sur le paramètre **Autoriser les utilisateurs à suspendre** l’analyse et définissez l’option **sur Désactivé.** Cliquez sur **OK**.

## <a name="related-articles"></a>Articles connexes

- [Configurer les notifications qui s’affichent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)
- [Configurer l’interaction de l’utilisateur final avec Antivirus Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
