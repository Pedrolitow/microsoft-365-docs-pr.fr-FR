---
title: Créer des indicateurs pour les IP et URL/domaines
ms.reviewer: ''
description: Créez des indicateurs pour les adresses IP et les URL/domaines qui définissent la détection, la prévention et l’exclusion des entités.
keywords: ip, URL, domaine, gérer, autorisé, bloqué, bloquer, nettoyer, malveillant, hachage de fichier, adresse IP, URL, domaine
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 317258174d193c5448353604bae81f42797e01d2
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67690331"
---
# <a name="create-indicators-for-ips-and-urlsdomains"></a>Créer des indicateurs pour les IP et URL/domaines

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Defender pour point de terminaison peut bloquer ce que Microsoft considère comme des adresses IP/URL malveillantes, via Windows Defender SmartScreen pour les navigateurs Microsoft et via la protection réseau pour les navigateurs non Microsoft ou les appels effectués en dehors d’un navigateur.

Le jeu de données de renseignement sur les menaces pour cela a été géré par Microsoft.

En créant des indicateurs pour les adresses IP et les URL ou les domaines, vous pouvez désormais autoriser ou bloquer des adresses IP, des URL ou des domaines en fonction de votre propre renseignement sur les menaces. Vous pouvez également avertir les utilisateurs avec une invite s’ils ouvrent une application à risque. L’invite ne les empêchera pas d’utiliser l’application, mais vous pouvez fournir un message personnalisé et des liens vers une page d’entreprise qui décrit l’utilisation appropriée de l’application. Les utilisateurs peuvent toujours contourner l’avertissement et continuer à utiliser l’application s’ils en ont besoin.

Pour ce faire, vous pouvez utiliser la page paramètres ou les groupes d’ordinateurs si vous jugez que certains groupes sont plus ou moins à risque que d’autres.

> [!NOTE]
> La notation de routage Inter-Domain sans classe (CIDR) pour les adresses IP n’est pas prise en charge.

## <a name="before-you-begin"></a>Avant de commencer

Il est important de comprendre les prérequis suivants avant de créer des indicateurs pour les adresses IP, les URL ou les domaines :

- L’autorisation et le bloc d’URL/IP s’appuient sur la protection réseau du composant Defender pour point de terminaison pour être activée en mode bloc. Pour plus d’informations sur la protection réseau et les instructions de configuration, consultez [Activer la protection réseau](enable-network-protection.md).
- La version du client Antimalware doit être 4.18.1906.x ou ultérieure. 
- Pris en charge sur les machines sur les appareils Windows 10, version 1709 ou ultérieure, Windows 11, Windows Server 2016, Windows Server 2012 R2, Windows Server 2019, Windows Server 2022 et Android et iOS.

    > [!NOTE]
    > Windows Server 2016 et Windows Server 2012 R2 doivent être intégrés à l’aide des instructions fournies dans [les serveurs Windows intégrés](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) pour que cette fonctionnalité fonctionne.

- Assurez-vous que **les indicateurs réseau personnalisés sont activés** dans les **fonctionnalités avancées** **Microsoft 365 Defender** \> **Paramètres**\>. Pour plus d’informations, consultez [Fonctionnalités avancées](advanced-features.md).
- Pour la prise en charge des indicateurs sur iOS, consultez [Microsoft Defender pour point de terminaison sur iOS](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-custom-indicators).
- Pour la prise en charge des indicateurs sur Android, consultez [Microsoft Defender pour point de terminaison sur Android](/microsoft-365/security/defender-endpoint/android-configure#configure-custom-indicators).

> [!IMPORTANT]
> Seules les adresses IP externes peuvent être ajoutées à la liste des indicateurs. Les indicateurs ne peuvent pas être créés pour les adresses IP internes.
> Pour les scénarios de protection web, nous vous recommandons d’utiliser les fonctionnalités intégrées dans Microsoft Edge. Microsoft Edge tire parti de [la protection réseau](network-protection.md) pour inspecter le trafic réseau et autorise les blocs pour TCP, HTTP et HTTPS (TLS).
> S’il existe des stratégies d’indicateur d’URL en conflit, le chemin d’accès le plus long est appliqué. Par exemple, la stratégie `https://support.microsoft.com/office` d’indicateur d’URL est prioritaire sur la stratégie `https://support.microsoft.com`d’indicateur d’URL.

> [!NOTE]
> Pour les processus autres que Microsoft Edge et Internet Explorer, les scénarios de protection web tirent parti de la protection réseau pour l’inspection et l’application :
>
> - L’adresse IP est prise en charge pour les trois protocoles (TCP, HTTP et HTTPS (TLS))
> - Seules les adresses IP uniques sont prises en charge (pas de blocs CIDR ou de plages d’adresses IP) dans les indicateurs personnalisés
> - Les URL chiffrées (chemin d’accès complet) ne peuvent être bloquées que sur les navigateurs internes (Internet Explorer, Edge)
> - Les URL chiffrées (FQDN uniquement) peuvent être bloquées dans des navigateurs tiers (c’est-à-dire autres qu’Internet Explorer, Edge)
> - Des blocs de chemin d’URL complets peuvent être appliqués pour les URL non chiffrées
>
> Il peut y avoir jusqu’à 2 heures de latence (généralement moins) entre le moment où l’action est effectuée et l’URL et l’adresse IP bloquées.

Lorsque vous utilisez le mode d’avertissement, vous pouvez configurer les contrôles suivants :

**Possibilité de contournement** :

- Bouton Autoriser dans Edge
- Bouton Autoriser sur toast (navigateurs non-Microsoft)
- Contourner le paramètre de durée sur l’indicateur
- Contourner la mise en œuvre dans les navigateurs Microsoft et non-Microsoft

**URL de redirection** :

- Paramètre d’URL de redirection sur l’indicateur
- URL de redirection dans Edge
- URL de redirection sur toast (navigateurs non-Microsoft)

Pour plus d’informations, consultez [Régir les applications découvertes par Microsoft Defender pour point de terminaison](/cloud-app-security/mde-govern).

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
