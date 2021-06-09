---
title: Créer des indicateurs pour les IP et URL/domaines
ms.reviewer: ''
description: Créez des indicateurs pour les adresses IPS et les URL/domaines qui définissent la détection, la prévention et l’exclusion des entités.
keywords: ip, url, domaine, gérer, autorisé, bloqué, bloquer, nettoyer, malveillant, hachage de fichier, adresse IP, url, domaine
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: e7dc11fe709a6d04b6309706df90f0ebbc177e25
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52841065"
---
# <a name="create-indicators-for-ips-and-urlsdomains"></a>Créer des indicateurs pour les IP et URL/domaines 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> [!TIP]
> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/en-us/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)


Defender pour le point de terminaison peut bloquer ce que Microsoft considère comme des ADRESSES/URL malveillantes, via Windows Defender SmartScreen pour navigateurs Microsoft et via la Protection du réseau pour les navigateurs non-Microsoft ou les appels effectués en dehors d’un navigateur.

Le jeu de données d’intelligence contre les menaces a été géré par Microsoft.

En créant des indicateurs pour les adresses IP, les URL ou les domaines, vous pouvez désormais autoriser ou bloquer des adresses IP, des URL ou des domaines en fonction de vos propres renseignements sur les menaces. Pour ce faire, vous pouvez utiliser la page des paramètres ou des groupes d’ordinateurs si vous estez d’après certains groupes plus ou moins à risque que d’autres.

> [!NOTE]
> La notation CIDR (Classless Inter-Domain Routing) pour les adresses IP n’est pas prise en charge. 

### <a name="before-you-begin"></a>Avant de commencer
Il est important de comprendre les conditions préalables suivantes avant de créer des indicateurs pour IPS, URL ou domaines :
- Url/IP allow and block relies on the Defender for Endpoint component Network Protection to be enabled in block mode. Pour plus d’informations sur la protection du réseau et les instructions de configuration, voir [Activer la protection réseau.](enable-network-protection.md)
- La version du client anti-programme malveillant doit être 4.18.1906.x ou version ultérieure. 
- Pris en charge sur les ordinateurs Windows 10 version 1709 ou ultérieure. 
- **Assurez-vous que les indicateurs réseau personnalisés** sont activés dans Centre de sécurité Microsoft Defender > Paramètres > **fonctionnalités avancées.** Pour plus d’informations, voir [Fonctionnalités avancées.](advanced-features.md)
- Pour la prise en charge des indicateurs sur iOS, voir [Configurer des indicateurs personnalisés.](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-custom-indicators)


> [!IMPORTANT]
> Seules les IP externes peuvent être ajoutées à la liste d’indicateurs. Les indicateurs ne peuvent pas être créés pour les IP internes.
> Pour les scénarios de protection web, nous vous recommandons d’utiliser les fonctionnalités intégrées dans Microsoft Edge. Microsoft Edge utilise la [Protection](network-protection.md) du réseau pour inspecter le trafic réseau et autorise les blocs pour TCP, HTTP et HTTPS (TLS). S’il existe des stratégies d’indicateur d’URL en conflit, le chemin d’accès le plus long est appliqué. Par exemple, la stratégie d’indicateur d’URL `https:\\support.microsoft.com/en-us/office` est prioritaire sur la stratégie d’indicateur d’URL. `https:\\support.microsoft.com`

> [!NOTE]
> Pour tous les autres processus, les scénarios de protection web tirent parti de la Protection du réseau pour l’inspection et l’application : 
> - L’adresse IP est prise en charge pour les trois protocoles
> - Seules les adresses IP individuelles sont pris en charge (pas de blocs CIDR ou de plages IP)
> - Les URL chiffrées (chemin d’accès complet) ne peuvent être bloquées que sur les navigateurs de première partie (Internet Explorer, Edge)
> - Les URL chiffrées (FQDN uniquement) peuvent être bloquées en dehors des navigateurs de première partie (Internet Explorer, Edge)
> - Les blocs de chemin d’accès d’URL complète peuvent être appliqués au niveau du domaine et à toutes les URL non chiffrées
 
> [!NOTE]
> Il peut y avoir jusqu’à 2 heures de latence (généralement moins) entre le moment où l’action est prise et l’URL et l’ADRESSE IP bloquées. 

### <a name="create-an-indicator-for-ips-urls-or-domains-from-the-settings-page"></a>Créer un indicateur pour les adresses IP, les URL ou les domaines à partir de la page des paramètres

1. Dans le volet de navigation, sélectionnez **Paramètres**  >  **indicateurs.**  

2. Sélectionnez **l’onglet Adresses IP ou URL/Domaines.**

3. Sélectionnez **Ajouter un élément.**

4. Spécifiez les détails suivants :
   - Indicateur : spécifiez les détails de l’entité et définissez l’expiration de l’indicateur.
   - Action : spécifiez l’action à prendre et fournissez une description.
   - Étendue : définir l’étendue du groupe d’ordinateurs.

5. Consultez les détails de l’onglet Résumé, puis cliquez sur **Enregistrer.**

## <a name="related-topics"></a>Voir aussi
- [Créer des indicateurs](manage-indicators.md)
- [Créer des indicateurs pour les fichiers](indicator-file.md)
- [Créer des indicateurs basés sur des certificats](indicator-certificates.md)
- [Gérer des indicateurs](indicator-manage.md)
