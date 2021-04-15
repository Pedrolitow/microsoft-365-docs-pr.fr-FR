---
title: Configurer les notifications de l'Antivirus Microsoft Defender
description: Découvrez comment configurer et personnaliser les notifications standard et supplémentaires de l'Antivirus Microsoft Defender sur les points de terminaison.
keywords: notifications, defender, antivirus, point de terminaison, gestion, administrateur
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: a91da48f27450d6f4a6fd2b9607aa979458ccf71
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51765094"
---
# <a name="configure-the-notifications-that-appear-on-endpoints"></a>Configurer les notifications qui apparaissent sur les points de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Dans Windows 10, les notifications d'application concernant la détection et la correction des programmes malveillants sont plus robustes, cohérentes et concises.

Les notifications apparaissent sur les points de terminaison lorsque des analyses déclenchées et programmées manuellement sont terminées et que des menaces sont détectées. Ces notifications apparaissent également dans le Centre de **notifications** et un résumé des analyses et des détections de menaces s'affiche à intervalles réguliers.

Vous pouvez également configurer l'apparition des notifications standard sur les points de terminaison, telles que les notifications de redémarrage ou lorsqu'une menace a été détectée et corrigé.

## <a name="configure-the-additional-notifications-that-appear-on-endpoints"></a>Configurer les notifications supplémentaires qui apparaissent sur les points de terminaison

Vous pouvez configurer l'affichage de notifications supplémentaires, telles que des résumés récents de la détection des menaces, dans l'application Sécurité [Windows](microsoft-defender-security-center-antivirus.md) et avec la stratégie de groupe.

> [!NOTE]
> Dans Windows 10, version 1607, la fonctionnalité était appelée **notifications améliorées** et pouvait être configurée sous La mise à jour des **paramètres Windows**&  >  **sécurité**  >  **Windows Defender**. Dans les paramètres de stratégie de groupe dans toutes les versions de Windows 10, il s'agit des **notifications améliorées.**

> [!IMPORTANT]
> La désactivation de notifications supplémentaires ne désactive pas les notifications critiques, telles que les alertes de détection et de correction des menaces.

**Utilisez l'application sécurité Windows pour désactiver les notifications supplémentaires :**

1. Ouvrez l'application Sécurité Windows en cliquant sur l'icône de bouclier dans la barre des tâches ou en recherchant Defender dans le menu **Démarrer.**

2. Cliquez sur la **vignette & protection** contre les virus contre les menaces (ou sur l'icône de bouclier dans la barre de menus de gauche), puis sur l'étiquette **paramètres** de protection contre & virus :

    ![Capture d'écran de l'étiquette & protection contre les virus dans l'application Sécurité Windows](images/defender/wdav-protection-settings-wdsc.png)

3. Faites défiler la page **jusqu'à la** section Notifications et cliquez **sur Modifier les paramètres de notification.**

4. Faites glisser le commutateur **sur Désactivé** ou **Activé** pour désactiver ou activer des notifications supplémentaires.

**Utilisez la stratégie de groupe pour désactiver les notifications supplémentaires :**

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l'Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

3. Cliquez **sur Modèles d'administration.**

4. Développez l'arborescence **des composants Windows >'antivirus Microsoft Defender > rapports.**

5. Double-cliquez **sur Désactiver les notifications améliorées** et définissez l'option sur **Activé.** Cliquez sur **OK**. Cela empêche l'apparition de notifications supplémentaires.

## <a name="configure-standard-notifications-on-endpoints"></a>Configurer des notifications standard sur les points de terminaison

Vous pouvez utiliser la stratégie de groupe pour :

- Afficher du texte personnalisé supplémentaire sur les points de terminaison lorsque l'utilisateur doit effectuer une action
- Masquer toutes les notifications sur les points de terminaison
- Masquer les notifications de redémarrage sur les points de terminaison

Masquer les notifications peut être utile dans les situations où vous ne pouvez pas masquer l'intégralité de l'interface antivirus Microsoft Defender. Pour [plus d'informations,](prevent-end-user-interaction-microsoft-defender-antivirus.md) voir Empêcher les utilisateurs de voir ou d'interagir avec l'interface utilisateur de l'Antivirus Microsoft Defender. 

> [!NOTE]
> Le masquation des notifications se produit uniquement sur les points de terminaison sur lesquels la stratégie a été déployée. Les notifications liées aux actions qui doivent être prises (par exemple, un redémarrage) apparaissent toujours dans le tableau de bord et les rapports de surveillance de [Microsoft Endpoint Manager Endpoint Protection.](/configmgr/protect/deploy-use/monitor-endpoint-protection) 

Voir [Personnaliser l'application sécurité Windows](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) pour votre organisation pour obtenir des instructions pour ajouter des informations de contact personnalisées aux notifications que les utilisateurs voient sur leurs ordinateurs.

**Utilisez la stratégie de groupe pour masquer les notifications :**

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l'Éditeur de gestion des stratégies de** groupe, cliquez sur **Configuration** ordinateur et cliquez **sur Modèles d'administration.**

3. Développez l'arborescence **des composants Windows >'interface > client antivirus Microsoft Defender.** 

4. Double-cliquez sur **Supprimer toutes les notifications et** définissez l'option sur **Activé.** Cliquez sur **OK**. Cela empêche l'apparition de notifications supplémentaires.

**Utilisez la stratégie de groupe pour masquer les notifications de redémarrage :**

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l'Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

3. Cliquez **sur Modèles d'administration.**

4. Développez l'arborescence **des composants Windows >'interface > client antivirus Microsoft Defender.**

5. Double-cliquez **sur Supprimer les notifications** de redémarrage et définir l'option **sur Activé.** Cliquez sur **OK**. Cela empêche l'apparition de notifications supplémentaires.

## <a name="related-topics"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Configurer l'interaction de l'utilisateur final avec l'Antivirus Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)