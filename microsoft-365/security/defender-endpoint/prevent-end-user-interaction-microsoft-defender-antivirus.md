---
title: Masquer l'interface antivirus Microsoft Defender
description: Vous pouvez masquer la vignette de protection contre les virus et les menaces dans l'application Sécurité Windows.
keywords: Verrouillage de l'interface utilisateur, mode sans en-tête, masquer l'application, masquer les paramètres, masquer l'interface
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 6b5ce018db436aee35bfa1899fb42f1dca31efa6
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690639"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>Empêcher les utilisateurs de voir ou d'interagir avec l'interface utilisateur de l'Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez utiliser la stratégie de groupe pour empêcher les utilisateurs sur les points de terminaison de voir l'interface de l'Antivirus Microsoft Defender. Vous pouvez également les empêcher de mettre en pause les analyses.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>Masquer l'interface antivirus Microsoft Defender

Dans Windows 10, versions 1703, le masquage de l'interface masquera les notifications de l'Antivirus Microsoft Defender et empêchera l'apparition de la vignette de protection contre les menaces virus & dans l'application Sécurité Windows.

Avec le paramètre activé **:**

![Capture d'écran de la sécurité Windows sans l'icône de bouclier et la section protection contre les virus et menaces](images/defender/wdav-headless-mode-1703.png)

Avec le paramètre désactivé **ou** non configuré :

![Capture d'écran de sécurité Windows affichant l'icône de bouclier et la section protection contre les virus et menaces](images/defender/wdav-headless-mode-off-1703.png)

>[!NOTE]
>Le masquage de l'interface empêche également les notifications de l'Antivirus Microsoft Defender d'apparaître sur le point de terminaison. Les notifications de Microsoft Defender pour point de terminaison s'affichent toujours. Vous pouvez également configurer individuellement [les notifications qui apparaissent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)

Dans les versions antérieures de Windows 10, le paramètre masque l'interface Windows Defender client. Si l'utilisateur tente de l'ouvrir, il reçoit un avertissement signalant que l'administrateur système a un accès restreint à cette application.

![Message d'avertissement lorsque le mode sans tête est activé dans Windows 10, versions antérieures à 1703](images/defender/wdav-headless-mode-1607.png)

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>Utiliser une stratégie de groupe pour masquer l'interface de Microsoft Defender AV aux utilisateurs

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. À **l'aide de l'Éditeur de gestion des stratégies de** groupe, go to **Computer configuration**.

3. Cliquez **sur Modèles d'administration.**

4. Développez l'arborescence **des composants Windows >'interface > client antivirus Microsoft Defender.**

5. Double-cliquez sur le **paramètre Activer le mode d'interface** utilisateur sans en-tête et définissez l'option sur **Activé.** Cliquez sur **OK**. 

Voir [Empêcher les utilisateurs de modifier localement](configure-local-policy-overrides-microsoft-defender-antivirus.md) les paramètres de stratégie pour plus d'options pour empêcher les utilisateurs de modifier la protection sur leurs PC.

## <a name="prevent-users-from-pausing-a-scan"></a>Empêcher les utilisateurs de mettre une analyse en pause

Vous pouvez empêcher les utilisateurs de mettre en pause les analyses, ce qui peut être utile pour vous assurer que les analyses programmées ou à la demande ne sont pas interrompues par les utilisateurs.

> [!NOTE]
> Ce paramètre n'est pas pris en charge sur Windows 10.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>Utiliser une stratégie de groupe pour empêcher les utilisateurs de mettre une analyse en pause

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. À **l'aide de l'Éditeur de gestion des stratégies de** groupe, go to **Computer configuration**.

3. Cliquez **sur Modèles d'administration.**

4. Développez l'arborescence **des composants Windows**  >  **Analyse antivirus Microsoft Defender.**  >  

5. Double-cliquez sur le **paramètre Autoriser les utilisateurs à suspendre** l'analyse et définissez l'option **sur Désactivé.** Cliquez sur **OK**. 

## <a name="related-articles"></a>Articles connexes

- [Configurer les notifications qui apparaissent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)

- [Configurer l'interaction de l'utilisateur final avec l'Antivirus Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)