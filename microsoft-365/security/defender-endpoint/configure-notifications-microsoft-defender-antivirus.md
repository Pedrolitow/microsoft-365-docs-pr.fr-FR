---
title: Configurer les Antivirus Microsoft Defender notifications
description: Découvrez comment configurer et personnaliser les notifications standard et autres Antivirus Microsoft Defender sur les points de terminaison.
keywords: notifications, defender, antivirus, point de terminaison, gestion, administrateur
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.topic: article
ms.author: deniseb
ms.custom: nextgen
ms.date: 06/16/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: c5b651dba1cf6b4e1af2e02e21f18f5663c21d1e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60201407"
---
# <a name="configure-microsoft-defender-antivirus-notifications-that-appear-on-endpoints"></a>Configurer les notifications Antivirus Microsoft Defender qui apparaissent sur les points de terminaison

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Dans Windows 10, les notifications d’application concernant la détection et la correction des programmes malveillants sont plus robustes, cohérentes et concises. Antivirus Microsoft Defender notifications s’affichent sur les points de terminaison lorsque des analyses sont terminées et que des menaces sont détectées. Les notifications suivent les analyses programmées et déclenchées manuellement. Ces notifications apparaissent également dans le Centre de **notifications** et un résumé des analyses et des détections de menaces s’affiche à intervalles réguliers.

Si vous faites partie de l’équipe de sécurité de votre organisation, vous pouvez configurer l’apparition des notifications sur les points de terminaison, telles que les notifications qui invitent à un redémarrage du système ou qui indiquent qu’une menace a été détectée et corrigé.

## <a name="configure-antivirus-notifications-using-group-policy-or-the-windows-security-app"></a>Configurer les notifications antivirus à l’aide de la stratégie de groupe ou de l Sécurité Windows appl

Vous pouvez configurer l’affichage de notifications supplémentaires, telles que des résumés récents de détection des menaces, dans [l’application Sécurité Windows et](microsoft-defender-security-center-antivirus.md) avec la stratégie de groupe.

> [!NOTE]
> Dans Windows 10 version 1607, la fonctionnalité s’appelait **notifications améliorées** et a été configurée sous Windows Paramètres mise à jour &  \> **sécurité** \> **Windows Defender**. Dans les paramètres de stratégie de groupe pour toutes les versions de Windows 10, la fonctionnalité de notification est appelée **notifications améliorées.**

### <a name="use-group-policy-to-disable-additional-notifications"></a>Utiliser une stratégie de groupe pour désactiver des notifications supplémentaires

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Cliquez avec le bouton droit sur l’objet de stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier.**

3. Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

4. Sélectionnez **modèles d’administration.**

5. Développez l’arborescence **Windows composants Antivirus Microsoft Defender** > \>  Reporting**.

6. Double-cliquez **sur Désactiver les notifications améliorées** et définissez l’option sur **Activé.** Puis sélectionnez **OK**. Cela empêche l’apparition de notifications supplémentaires.

> [!IMPORTANT]
> La désactivation de notifications supplémentaires ne désactive pas les notifications critiques, telles que les alertes de détection et de correction des menaces.

### <a name="use-the-windows-security-app-to-disable-additional-notifications"></a>Utiliser l’application Sécurité Windows pour désactiver des notifications supplémentaires

1. Ouvrez l Sécurité Windows application en cliquant sur l’icône de bouclier dans la barre des tâches ou en recherchant sécurité dans le menu **Démarrer.**

2. Sélectionnez **la vignette & protection** antivirus contre les menaces (ou l’icône de bouclier dans la barre de menus de gauche), puis sélectionnez **Paramètres** de protection contre & virus

3. Faites défiler la page **jusqu’à la** section Notifications et sélectionnez **Modifier les paramètres de notification.**

4. Faites glisser le commutateur **sur Désactivé** ou **Activé** pour désactiver ou activer des notifications supplémentaires.

> [!IMPORTANT]
> La désactivation de notifications supplémentaires ne désactive pas les notifications critiques, telles que les alertes de détection et de correction des menaces.

## <a name="configure-standard-notifications-on-endpoints-using-group-policy"></a>Configurer des notifications standard sur les points de terminaison à l’aide de la stratégie de groupe

Vous pouvez utiliser la stratégie de groupe pour :

- Afficher du texte personnalisé supplémentaire sur les points de terminaison lorsque l’utilisateur doit effectuer une action
- Masquer toutes les notifications sur les points de terminaison
- Masquer les notifications de redémarrage sur les points de terminaison

Masquer les notifications peut être utile dans les situations où vous ne pouvez pas masquer l’interface Antivirus Microsoft Defender complète. Pour plus d’informations, voir Empêcher les utilisateurs de voir ou [d’interagir Antivirus Microsoft Defender’interface utilisateur.](prevent-end-user-interaction-microsoft-defender-antivirus.md) Le masquation des notifications se produit uniquement sur les points de terminaison sur lesquels la stratégie a été déployée. Les notifications relatives aux actions qui doivent être prises (telles qu’un redémarrage) apparaissent toujours dans le tableau de bord de Microsoft Endpoint Manager Endpoint Protection et [les rapports.](/configmgr/protect/deploy-use/monitor-endpoint-protection) 

Pour ajouter des informations de contact personnalisées aux notifications de point de terminaison, voir [Personnaliser l’application Sécurité Windows pour votre organisation.](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center)

### <a name="use-group-policy-to-hide-notifications"></a>Utiliser une stratégie de groupe pour masquer les notifications

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Cliquez avec le bouton droit sur l’objet de stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier.**

3. Dans **l’Éditeur de gestion des stratégies de** groupe, sélectionnez **Configuration** ordinateur, puis sélectionnez **Modèles d’administration.**

4. Développez l’arborescence **Windows composants** \>  \> **Antivirus Microsoft Defender’interface client.** 

5. Double-cliquez sur **Supprimer toutes les notifications et** définissez l’option sur **Activé.** 

6. Sélectionnez **OK**. Cela empêche l’apparition de notifications supplémentaires.

### <a name="use-group-policy-to-hide-reboot-notifications"></a>Utiliser une stratégie de groupe pour masquer les notifications de redémarrage

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Cliquez avec le bouton droit sur l’objet de stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

3. Cliquez **sur Modèles d’administration.**

4. Développez l’arborescence **Windows composants** \>  \> **Antivirus Microsoft Defender’interface client.**

5. Double-cliquez **sur Supprimer les notifications** de redémarrage et définir l’option **sur Activé.** 

5. Sélectionnez **OK**. Cela empêche l’apparition de notifications supplémentaires.

