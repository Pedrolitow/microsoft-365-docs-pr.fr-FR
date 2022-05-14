---
title: Configurer des notifications Antivirus Microsoft Defender
description: Découvrez comment configurer et personnaliser des notifications standard et autres Antivirus Microsoft Defender sur les points de terminaison.
keywords: notifications, defender, antivirus, point de terminaison, gestion, administrateur
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
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 6c9dfd603a128de4a94c9cf49faa6ba9ca940d9b
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418179"
---
# <a name="configure-microsoft-defender-antivirus-notifications-that-appear-on-endpoints"></a>Configurer Antivirus Microsoft Defender notifications qui s’affichent sur les points de terminaison

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Dans Windows 10 et Windows 11, les notifications d’application sur la détection et la correction des programmes malveillants sont plus robustes, cohérentes et concises. Antivirus Microsoft Defender notifications apparaissent sur les points de terminaison lorsque les analyses sont terminées et que des menaces sont détectées. Les notifications suivent les analyses planifiées et déclenchées manuellement. Ces notifications apparaissent également dans le **Centre de notification**, et un résumé des analyses et des détections de menaces s’affiche à intervalles réguliers.

Si vous faites partie de l’équipe de sécurité de votre organisation, vous pouvez configurer la façon dont les notifications apparaissent sur les points de terminaison, telles que les notifications qui demandent un redémarrage du système ou qui indiquent qu’une menace a été détectée et corrigée.

## <a name="configure-antivirus-notifications-using-group-policy-or-the-windows-security-app"></a>Configurer des notifications antivirus à l’aide de stratégie de groupe ou de l’application Sécurité Windows

Vous pouvez configurer l’affichage de notifications supplémentaires, telles que des résumés de détection de menaces récents, dans [l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md) et avec stratégie de groupe.

> [!NOTE]
> Dans Windows 10, version 1607, la fonctionnalité a été appelée **notifications améliorées** et a été configurée sous **Windows Paramètres** \> **Mise à jour &** **Windows Defender** de sécurité\>. Dans stratégie de groupe paramètres pour toutes les versions de Windows 10 et Windows 11, la fonctionnalité de notification est appelée **notifications améliorées**.

### <a name="use-group-policy-to-disable-additional-notifications"></a>Utiliser stratégie de groupe pour désactiver des notifications supplémentaires

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

3. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

4. Sélectionnez **Modèles d’administration**.

5. Développez l’arborescence pour **Windows composants** \> **Antivirus Microsoft Defender** >  **Reporting**.

6. Double-cliquez sur **Désactiver les notifications améliorées** et définissez l’option **sur Activé**. Puis sélectionnez **OK**. Cela empêchera l’apparition de notifications supplémentaires.

> [!IMPORTANT]
> La désactivation des notifications supplémentaires ne désactive pas les notifications critiques, telles que les alertes de détection des menaces et de correction.

### <a name="use-the-windows-security-app-to-disable-additional-notifications"></a>Utiliser l’application Sécurité Windows pour désactiver les notifications supplémentaires

1. Ouvrez l’application Sécurité Windows en cliquant sur l’icône du bouclier dans la barre des tâches ou en recherchant **la sécurité** dans le menu Démarrer.

2. Sélectionnez **la vignette Virus & protection contre les menaces** (ou l’icône du bouclier dans la barre de menus de gauche), puis sélectionnez **Virus & paramètres de protection contre les menaces**

3. Faites défiler jusqu’à la section **Notifications** et **sélectionnez Modifier les paramètres de notification**.

4. Faites glisser le commutateur vers **Désactivé** ou **Activé** pour désactiver ou activer des notifications supplémentaires.

> [!IMPORTANT]
> La désactivation des notifications supplémentaires ne désactive pas les notifications critiques, telles que les alertes de détection des menaces et de correction.

## <a name="configure-standard-notifications-on-endpoints-using-group-policy"></a>Configurer des notifications standard sur les points de terminaison à l’aide de stratégie de groupe

Vous pouvez utiliser stratégie de groupe pour :

- Afficher du texte personnalisé supplémentaire sur les points de terminaison lorsque l’utilisateur doit effectuer une action
- Masquer toutes les notifications sur les points de terminaison
- Masquer les notifications de redémarrage sur les points de terminaison

Le masquage des notifications peut être utile dans les situations où vous ne pouvez pas masquer l’intégralité de l’interface Antivirus Microsoft Defender. Pour plus d’informations, consultez [Empêcher les utilisateurs de voir ou d’interagir avec l’interface utilisateur Antivirus Microsoft Defender](prevent-end-user-interaction-microsoft-defender-antivirus.md). Le masquage des notifications se produit uniquement sur les points de terminaison sur lesquels la stratégie a été déployée. Les notifications relatives aux actions qui doivent être effectuées (par exemple, un redémarrage) apparaissent toujours dans le [tableau de bord et les rapports de surveillance Microsoft Endpoint Manager Endpoint Protection](/configmgr/protect/deploy-use/monitor-endpoint-protection). 

Pour ajouter des informations de contact personnalisées aux notifications de point de terminaison, consultez [Personnaliser l’application Sécurité Windows pour votre organisation](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center).

### <a name="use-group-policy-to-hide-notifications"></a>Utiliser stratégie de groupe pour masquer les notifications

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

3. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**, puis sélectionnez **Modèles d’administration**.

4. Développez l’arborescence pour **Windows composants** \> **Antivirus Microsoft Defender** \> **interface client**. 

5. Double-cliquez sur **Supprimer toutes les notifications** et définissez l’option **sur Activé**. 

6. Sélectionnez **OK**. Cela empêchera l’apparition de notifications supplémentaires.

### <a name="use-group-policy-to-hide-reboot-notifications"></a>Utiliser stratégie de groupe pour masquer les notifications de redémarrage

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Cliquez sur **Modèles d’administration**.

4. Développez l’arborescence pour **Windows composants** \> **Antivirus Microsoft Defender** \> **interface client**.

5. Double-cliquez sur **Supprimer les notifications de redémarrage** et définissez l’option **sur Activé**. 

5. Sélectionnez **OK**. Cela empêchera l’apparition de notifications supplémentaires.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)