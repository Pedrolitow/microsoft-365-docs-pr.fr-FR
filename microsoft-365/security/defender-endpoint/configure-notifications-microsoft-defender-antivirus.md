---
title: Configurer les Antivirus Microsoft Defender notifications
description: Découvrez comment configurer et personnaliser des notifications standard et Antivirus Microsoft Defender supplémentaires sur les points de terminaison.
keywords: notifications, defender, antivirus, point de terminaison, gestion, administrateur
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.topic: article
ms.author: deniseb
ms.custom: nextgen
ms.date: 05/17/2021
ms.reviewer: ''
manager: dansimp
ms.openlocfilehash: 1e9f733b20b62af7e73a923932057920ff1dc155
ms.sourcegitcommit: be929f79751c0c52dfa6bd98a854432a0c63faf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2021
ms.locfileid: "52926237"
---
# <a name="configure-the-notifications-that-appear-on-endpoints"></a>Configurer les notifications qui s’affichent sur les points de terminaison

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Dans Windows 10, les notifications d’application concernant la détection et la correction des programmes malveillants sont plus robustes, cohérentes et concises.

Les notifications apparaissent sur les points de terminaison lorsque des analyses déclenchées et programmées manuellement sont terminées et que des menaces sont détectées. Ces notifications apparaissent également dans le Centre de **notifications** et un résumé des analyses et des détections de menaces s’affiche à intervalles réguliers.

Vous pouvez également configurer l’apparition des notifications standard sur les points de terminaison, telles que les notifications de redémarrage ou lorsqu’une menace a été détectée et corrigé.

## <a name="configure-the-additional-notifications-that-appear-on-endpoints"></a>Configurer les notifications supplémentaires qui apparaissent sur les points de terminaison

Vous pouvez configurer l’affichage de notifications supplémentaires, telles que des résumés récents de détection des menaces, dans [l’application Sécurité Windows et](microsoft-defender-security-center-antivirus.md) avec la stratégie de groupe.

> [!NOTE]
> Dans Windows 10 version 1607, la fonctionnalité était appelée **notifications améliorées** et pouvait être configurée sous Windows Paramètres mise à jour &   >  **sécurité**  >  **Windows Defender**. Dans les paramètres de stratégie de groupe dans toutes les versions Windows 10, il s’agit des **notifications améliorées.**

> [!IMPORTANT]
> La désactivation de notifications supplémentaires ne désactive pas les notifications critiques, telles que les alertes de détection et de correction des menaces.

**Utilisez l’Sécurité Windows pour désactiver des notifications supplémentaires :**

1. Ouvrez l Sécurité Windows application en cliquant sur l’icône de bouclier dans la barre des tâches ou en recherchant sécurité dans le menu **Démarrer.**

2. Sélectionnez **la vignette & protection** antivirus contre les menaces (ou l’icône de bouclier dans la barre de menus de gauche), puis sélectionnez **Paramètres** de protection contre & virus

3. Faites défiler la page **jusqu’à la** section Notifications et cliquez **sur Modifier les paramètres de notification.**

4. Faites glisser le commutateur **sur Désactivé** ou **Activé** pour désactiver ou activer des notifications supplémentaires.

**Utilisez la stratégie de groupe pour désactiver les notifications supplémentaires :**

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

3. Cliquez **sur Modèles d’administration.**

4. Développez l’arborescence **pour Windows composants > Antivirus Microsoft Defender > rapports.**

5. Double-cliquez **sur Désactiver les notifications améliorées** et définissez l’option sur **Activé.** Cliquez sur **OK**. Cela empêche l’apparition de notifications supplémentaires.

## <a name="configure-standard-notifications-on-endpoints"></a>Configurer des notifications standard sur les points de terminaison

Vous pouvez utiliser la stratégie de groupe pour :

- Afficher du texte personnalisé supplémentaire sur les points de terminaison lorsque l’utilisateur doit effectuer une action
- Masquer toutes les notifications sur les points de terminaison
- Masquer les notifications de redémarrage sur les points de terminaison

Masquer les notifications peut être utile dans les situations où vous ne pouvez pas masquer l’interface Antivirus Microsoft Defender complète. Pour plus d’informations, voir Empêcher les utilisateurs de voir ou [d’interagir Antivirus Microsoft Defender’interface utilisateur.](prevent-end-user-interaction-microsoft-defender-antivirus.md) 

> [!NOTE]
> Le masquation des notifications se produit uniquement sur les points de terminaison sur lesquels la stratégie a été déployée. Les notifications liées aux actions qui doivent être prises (par exemple, un redémarrage) apparaissent toujours dans le tableau de bord de Microsoft Endpoint Manager Endpoint Protection de surveillance [et les rapports.](/configmgr/protect/deploy-use/monitor-endpoint-protection) 

Pour obtenir des instructions sur l’ajout [d’informations](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) de contact personnalisées aux notifications que les utilisateurs voient sur leurs ordinateurs, voir Personnaliser l’application Sécurité Windows pour votre organisation.

**Utilisez la stratégie de groupe pour masquer les notifications :**

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, cliquez sur **Configuration** ordinateur et cliquez **sur Modèles d’administration.**

3. Développez l’arborescence **Windows composants > Antivirus Microsoft Defender >'interface client.** 

4. Double-cliquez sur **Supprimer toutes les notifications et** définissez l’option sur **Activé.** Cliquez sur **OK**. Cela empêche l’apparition de notifications supplémentaires.

**Utilisez la stratégie de groupe pour masquer les notifications de redémarrage :**

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

3. Cliquez **sur Modèles d’administration.**

4. Développez l’arborescence **Windows composants > Antivirus Microsoft Defender >'interface client.**

5. Double-cliquez **sur Supprimer les notifications** de redémarrage et définir l’option **sur Activé.** Cliquez sur **OK**. Cela empêche l’apparition de notifications supplémentaires.

## <a name="related-topics"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Configurer l’interaction de l’utilisateur final avec Antivirus Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
