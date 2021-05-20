---
title: Configurer Antivirus Microsoft Defender notifications
description: Découvrez comment configurer et personnaliser les notifications standard et Antivirus Microsoft Defender sur les points de terminaison.
keywords: notifications, défenseur, antivirus, point final, gestion, admin
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 05/17/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.openlocfilehash: f885b6d7991e4175cd14be5bbe9e0a7c96b1580f
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572344"
---
# <a name="configure-the-notifications-that-appear-on-endpoints"></a>Configurer les notifications qui apparaissent sur les points de terminaison

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

En Windows 10, les notifications d’application sur la détection et l’assainissement des logiciels malveillants sont plus robustes, cohérentes et concises.

Les notifications apparaissent sur les points de terminaison lorsque les analyses déclenchées manuellement et planifiées sont terminées et que les menaces sont détectées. Ces notifications apparaissent également dans le Centre **de notification,** et un résumé des analyses et des détections de menaces apparaissent à intervalles réguliers.

Vous pouvez également configurer la façon dont les notifications standard s’apparaissent sur les paramètres, tels que les notifications de redémarrage ou lorsqu’une menace a été détectée et assainie.

## <a name="configure-the-additional-notifications-that-appear-on-endpoints"></a>Configurer les notifications supplémentaires qui apparaissent sur les points de terminaison

Vous pouvez configurer l’affichage de notifications supplémentaires, telles que des résumés récents de détection de menaces, [dans l’application Sécurité Windows et](microsoft-defender-security-center-antivirus.md) avec la stratégie de groupe.

> [!NOTE]
> Dans Windows 10, version 1607 la fonctionnalité a été appelée **notifications améliorées** et pourrait être **configuré sous Windows Paramètres** mise à jour &  >  **sécurité**  >  **Windows Defender**. Dans les paramètres de stratégie de groupe dans toutes les versions Windows 10, il est appelé **notifications améliorées**.

> [!IMPORTANT]
> La désactivation de notifications supplémentaires ne désactivera pas les notifications critiques, telles que les alertes de détection et d’assainissement des menaces.

**Utilisez l Sécurité Windows apprable pour désactiver les notifications supplémentaires :**

1. Ouvrez l Sécurité Windows application en cliquant sur l’icône bouclier dans la barre des tâches ou en recherchant le menu de démarrage pour **la sécurité**.

2. Sélectionnez **la vignette de protection contre & virus** (ou l’icône du bouclier sur la barre de menu gauche) et sélectionnez ensuite les paramètres de protection contre les menaces & virus ou les paramètres de protection contre les **menaces**

3. Faites défiler vers la section **Notifications** et cliquez sur **Paramètres de notification de modification**.

4. Faites glisser le commutateur vers **Off** ou **On** pour désactiver ou activer des notifications supplémentaires.

**Utilisez la stratégie de groupe pour désactiver des notifications supplémentaires :**

1. Sur votre ordinateur de gestion de stratégie de groupe, ouvrez [la console de gestion de stratégie de](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))groupe, cliquez à droite sur l’objet de stratégie de groupe que vous souhaitez configurer et cliquez sur **Modifier**.

2. Dans le **groupe Policy Management Editor aller** à la configuration de **l’ordinateur**.

3. Cliquez **sur Modèles administratifs**.

4. Étendre l’arbre **aux Windows composants > Antivirus Microsoft Defender > Reporting**.

5. Double-cliquez Désactiver **les notifications améliorées et** définir l’option **activée**. Cliquez sur **OK**. Cela empêchera l’apparition de notifications supplémentaires.

## <a name="configure-standard-notifications-on-endpoints"></a>Configurer les notifications standard sur les points de terminaison

Vous pouvez utiliser la stratégie de groupe pour :

- Affichez du texte supplémentaire personnalisé sur les points de terminaison lorsque l’utilisateur a besoin d’effectuer une action
- Masquer toutes les notifications sur les points de terminaison
- Masquer les notifications de redémarrage sur les points de terminaison

Masquer les notifications peut être utile dans les situations où vous ne pouvez pas masquer l’ensemble Antivirus Microsoft Defender interface. Voir [Empêcher les utilisateurs de voir ou d’interagir avec l’interface Antivirus Microsoft Defender utilisation pour](prevent-end-user-interaction-microsoft-defender-antivirus.md) plus d’informations. 

> [!NOTE]
> La dissimulation des notifications ne se produira que sur les points de terminaison auxquels la stratégie a été déployée. Les notifications relatives aux mesures à prendre (comme un redémarrage) apparaîtront toujours sur le [tableau de bord et les rapports Microsoft Endpoint Manager Endpoint Protection surveillance des données.](/configmgr/protect/deploy-use/monitor-endpoint-protection) 

Consultez [personnaliser l’application Sécurité Windows pour votre organisation pour obtenir](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) des instructions pour ajouter des coordonnées personnalisées aux notifications que les utilisateurs voient sur leurs machines.

**Utilisez la stratégie de groupe pour masquer les notifications :**

1. Sur votre ordinateur de gestion de stratégie de groupe, ouvrez [la console de gestion de stratégie de](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))groupe, cliquez à droite sur l’objet de stratégie de groupe que vous souhaitez configurer et cliquez sur **Modifier**.

2. Dans le **groupe Policy Management Editor aller** à la configuration de **l’ordinateur** et **cliquez sur modèles administratifs**.

3. Élargissez l’arbre **Windows composants > Antivirus Microsoft Defender > interface client.** 

4. Double-cliquez supprimer **toutes les notifications et** définir l’option activé **.** Cliquez sur **OK**. Cela empêchera l’apparition de notifications supplémentaires.

**Utilisez la stratégie de groupe pour masquer les notifications de redémarrage :**

1. Sur votre ordinateur de gestion de stratégie de groupe, ouvrez [la console de gestion de stratégie de](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))groupe, cliquez à droite sur l’objet de stratégie de groupe que vous souhaitez configurer et cliquez sur **Modifier**.

2. Dans le **groupe Policy Management Editor aller** à la configuration de **l’ordinateur**.

3. Cliquez **sur Modèles administratifs**.

4. Élargissez l’arbre **Windows composants > Antivirus Microsoft Defender > interface client.**

5. Double-click **supprime les notifications de redémarrage et** définir l’option **activée**. Cliquez sur **OK**. Cela empêchera l’apparition de notifications supplémentaires.

## <a name="related-topics"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Configurer l’interaction utilisateur final avec Antivirus Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
