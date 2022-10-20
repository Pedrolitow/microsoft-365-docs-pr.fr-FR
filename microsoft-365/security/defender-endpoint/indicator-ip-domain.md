---
title: Créer des indicateurs pour les IP et URL/domaines
ms.reviewer: ''
description: Créez des indicateurs pour les adresses IP et les URL/domaines qui définissent la détection, la prévention et l’exclusion des entités.
keywords: ip, url, domaine, manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain, IoC precedence, IoC conflict,
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 476058e2d26f14f130a88eca412d34836368987f
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68623033"
---
# <a name="create-indicators-for-ips-and-urlsdomains"></a>Créer des indicateurs pour les IP et URL/domaines

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

## <a name="overview"></a>Vue d’ensemble

En créant des indicateurs pour les adresses IP et les URL ou les domaines, vous pouvez désormais autoriser ou bloquer des adresses IP, des URL ou des domaines en fonction de votre propre renseignement sur les menaces. Vous pouvez également avertir les utilisateurs avec une invite s’ils ouvrent une application à risque. L’invite ne les empêchera pas d’utiliser l’application, mais vous pouvez fournir un message personnalisé et des liens vers une page d’entreprise qui décrit l’utilisation appropriée de l’application. Les utilisateurs peuvent toujours contourner l’avertissement et continuer à utiliser l’application s’ils en ont besoin.

Pour bloquer les adresses IP/URL malveillantes (telles que déterminées par Microsoft), Defender pour point de terminaison peut utiliser :

- Windows Defender SmartScreen pour les navigateurs Microsoft
- Protection réseau pour les navigateurs non-Microsoft ou les appels effectués en dehors d’un navigateur

Les données de renseignement sur les menaces définies pour bloquer les adresses IP/URL malveillantes sont gérées par Microsoft.

Vous pouvez bloquer les adresses IP/URL malveillantes via la page des paramètres ou par les groupes d’ordinateurs, si vous jugez que certains groupes sont plus ou moins à risque que d’autres.

> [!NOTE]
> La notation de routage Inter-Domain sans classe (CIDR) pour les adresses IP n’est pas prise en charge.

## <a name="before-you-begin"></a>Avant de commencer

Il est important de comprendre les prérequis suivants avant de créer des indicateurs pour les adresses IP, les URL ou les domaines :

### <a name="network-protection-requirements"></a>Configuration requise pour la protection réseau

L’autorisation et le bloc d’URL/IP nécessitent que le composant _de Microsoft Defender pour point de terminaison protection réseau_ soit activé en mode bloc. Pour plus d’informations sur la protection réseau et les instructions de configuration, consultez [Activer la protection réseau](enable-network-protection.md).

### <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

- Windows 10, version 1709 ou ultérieure
- Windows 11
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2019
- Windows Server 2022
- Appareils Android et iOS

### <a name="windows-server-2016-and-windows-server-2012-r2-requirements"></a>exigences Windows Server 2016 et Windows Server 2012 R2

Windows Server 2016 et Windows Server 2012 R2 doivent être intégrés à l’aide des instructions fournies dans [les serveurs Windows intégrés](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

### <a name="microsoft-defender-antivirus-version-requirements"></a>Microsoft Defender configuration requise pour la version antivirus

La _version du client Antimalware_ doit être 4.18.1906.x ou ultérieure.

### <a name="custom-network-indicators-requirements"></a>Exigences relatives aux indicateurs réseau personnalisés

Assurez-vous que **les indicateurs réseau personnalisés sont activés** dans les **fonctionnalités avancées** **Microsoft 365 Defender** \> **Paramètres**\>. Pour plus d’informations, consultez [Fonctionnalités avancées](advanced-features.md).

Pour la prise en charge des indicateurs sur iOS, consultez [Microsoft Defender pour point de terminaison sur iOS](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-custom-indicators).

Pour la prise en charge des indicateurs sur Android, consultez [Microsoft Defender pour point de terminaison sur Android](/microsoft-365/security/defender-endpoint/android-configure#configure-custom-indicators).

### <a name="ioc-indicator-list-limitations"></a>Limitations de la liste des indicateurs IoC

Seules les adresses IP externes peuvent être ajoutées à la liste des indicateurs. Les indicateurs ne peuvent pas être créés pour les adresses IP internes. Pour les scénarios de protection web, nous vous recommandons d’utiliser les fonctionnalités intégrées dans Microsoft Edge. Microsoft Edge tire parti de [la protection réseau](network-protection.md) pour inspecter le trafic réseau et autorise les blocs pour TCP, HTTP et HTTPS (TLS).

### <a name="non-microsoft-edge-and-internet-explorer-processes"></a>Processus non Microsoft Edge et Internet Explorer

Pour les processus autres que Microsoft Edge et Internet Explorer, les scénarios de protection web tirent parti de la protection réseau pour l’inspection et l’application :

- L’adresse IP est prise en charge pour les trois protocoles (TCP, HTTP et HTTPS (TLS))
- Seules les adresses IP uniques sont prises en charge (pas de blocs CIDR ou de plages d’adresses IP) dans les indicateurs personnalisés
- Les URL chiffrées (chemin d’accès complet) ne peuvent être bloquées que sur les navigateurs internes (Internet Explorer, Edge)
- Les URL chiffrées (FQDN uniquement) peuvent être bloquées dans des navigateurs tiers (c’est-à-dire autres qu’Internet Explorer, Edge)
- Des blocs de chemin d’URL complets peuvent être appliqués pour les URL non chiffrées
- S’il existe des stratégies d’indicateur d’URL en conflit, le chemin d’accès le plus long est appliqué. Par exemple, la stratégie `https://support.microsoft.com/office` d’indicateur d’URL est prioritaire sur la stratégie `https://support.microsoft.com`d’indicateur d’URL.
Il peut y avoir jusqu’à 2 heures de latence (généralement moins) entre le moment où l’action est effectuée et l’URL et l’adresse IP bloquées.

### <a name="warn-mode-controls"></a>Avertir les contrôles en mode

Lorsque vous utilisez le mode d’avertissement, vous pouvez configurer les contrôles suivants :

- **Capacité de contournement**
  - Bouton Autoriser dans Edge
  - Bouton Autoriser sur toast (navigateurs non-Microsoft)
  - Contourner le paramètre de durée sur l’indicateur
  - Contourner la mise en œuvre dans les navigateurs Microsoft et non-Microsoft

- **URL de redirection**
  - Paramètre d’URL de redirection sur l’indicateur
  - URL de redirection dans Edge
  - URL de redirection sur toast (navigateurs non-Microsoft)

Pour plus d’informations, consultez [Régir les applications découvertes par Microsoft Defender pour point de terminaison](/cloud-app-security/mde-govern).

## <a name="ioc-ip-url-and-domain-policy-conflict-handling-order"></a>Url IP IoC et ordre de gestion des conflits de stratégie de domaine

La gestion des conflits de stratégie suit l’ordre ci-dessous :

- MDCA crée un indicateur non autorisé pour tous les utilisateurs, mais l’URL est autorisée pour un groupe d’appareils spécifique. Le groupe d’appareils spécifique est bloqué l’accès à l’URL.
- Si l’adresse IP, l’URL/le domaine sont autorisés
- Si l’adresse IP, l’URL/le domaine n’est pas autorisé
- Si l’adresse IP, l’URL/le domaine sont autorisés
- Si l’adresse IP, l’URL/le domaine n’est pas autorisé
- Si l’adresse IP, l’URL/le domaine sont autorisés

S’il existe des stratégies IoC de fichier en conflit avec le même type d’application et la même cible, la stratégie de la plus sécurisée sera appliquée.

La gestion des conflits de stratégie pour les domaines/URL/adresses IP diffère de la gestion des conflits de stratégie pour les certificats.

Les fonctionnalités d’application vulnérables de la gestion des menaces et des vulnérabilités utilisent les IOC de fichier pour l’application et suivent l’ordre de gestion des conflits ci-dessus.

## <a name="policy-precedence"></a>Priorité des stratégies

Microsoft Defender pour point de terminaison stratégie est prioritaire sur Microsoft Defender stratégie antivirus. Dans les situations où Defender pour point de terminaison est défini sur **Autoriser**, mais Microsoft Defender Antivirus est défini sur **Bloquer**, la stratégie est définie par défaut sur **Autoriser**.

#### <a name="precedence-for-multiple-active-policies"></a>Priorité pour plusieurs stratégies actives

L’application de plusieurs stratégies de filtrage de contenu web différentes sur le même appareil entraîne l’application d’une stratégie plus restrictive pour chaque catégorie. Prenons l’exemple du scénario suivant :

- **La stratégie 1** bloque les catégories 1 et 2 et audite le reste
- **La stratégie 2** bloque les catégories 3 et 4 et audite le reste

Le résultat est que les catégories 1 à 4 sont toutes bloquées. Ceci est illustré dans l’image suivante.

:::image type="content" source="images/web-content-filtering-policies-mode-precedence.png" alt-text="Diagramme montrant la priorité du mode de blocage de stratégie de filtrage de contenu web sur le mode d’audit.":::

## <a name="create-an-indicator-for-ips-urls-or-domains-from-the-settings-page"></a>Créer un indicateur pour les adresses IP, les URL ou les domaines à partir de la page des paramètres

1. Dans le volet de navigation, sélectionnez **Paramètres** \> Points de **terminaison Indicateurs** \> (sous **Règles**).

2. Sélectionnez l’onglet **Adresses IP ou URL/Domaines** .

3. Sélectionnez **Ajouter un élément**.

4. Spécifiez les détails suivants :
   - Indicateur : spécifiez les détails de l’entité et définissez l’expiration de l’indicateur.
   - Action : spécifiez l’action à entreprendre et fournissez une description.
   - Étendue : définissez l’étendue du groupe d’ordinateurs.

5. Passez en revue les détails sous l’onglet Résumé, puis cliquez sur **Enregistrer**.

## <a name="related-topics"></a>Voir aussi

- [Créer des indicateurs](manage-indicators.md)
- [Créer des indicateurs pour les fichiers](indicator-file.md)
- [Créer des indicateurs basés sur des certificats](indicator-certificates.md)
- [Gérer des indicateurs](indicator-manage.md)
