---
title: Pare-feu dans Microsoft Defender pour Entreprises (aperçu)
description: En savoir plus sur Windows Defender pare-feu dans Microsoft Defender entreprise (prévisualisation), y compris les paramètres de configuration
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 12/08/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 9cad75ebdc9ff66958e208e5b74f5ad4470b44a7
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2021
ms.locfileid: "61423454"
---
# <a name="firewall-in-microsoft-defender-for-business-preview"></a>Pare-feu dans Microsoft Defender pour Entreprises (aperçu)

> [!IMPORTANT]
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. Cet article inclut des liens vers du contenu en ligne qui peut décrire certaines fonctionnalités qui ne sont pas incluses dans Microsoft Defender pour Entreprises (prévisualisation).

Microsoft Defender pour Entreprise (prévisualisation) inclut des fonctionnalités de pare-feu avec [Windows Defender pare-feu](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). La protection pare-feu permet de sécuriser les appareils avec des règles qui déterminent le trafic réseau autorisé à entrer ou à circuler à partir d’appareils. 

Vous pouvez utiliser la protection pare-feu pour spécifier s’il faut autoriser ou bloquer les connexions sur des appareils à différents emplacements. Par exemple, vos paramètres de pare-feu peuvent autoriser les connexions entrantes sur les appareils connectés au réseau interne de votre entreprise, mais empêcher ces connexions lorsque l’appareil se trouve sur un réseau avec des appareils non utilisés.

**Cet article décrit**:

- [Paramètres de pare-feu par défaut dans Defender for Business (aperçu)](#default-firewall-settings-in-defender-for-business)
- [Paramètres de pare-feu que vous pouvez configurer dans Defender for Business (aperçu)](#firewall-settings-you-can-configure-in-defender-for-business)

## <a name="default-firewall-settings-in-defender-for-business"></a>Paramètres de pare-feu par défaut dans Defender pour les entreprises

Microsoft Defender pour Entreprise (prévisualisation) inclut des stratégies et des paramètres de pare-feu par défaut pour protéger les appareils de votre entreprise dès le premier jour. Dès que les appareils de votre entreprise sont intégrés à Microsoft Defender pour Entreprises (prévisualisation), votre stratégie de pare-feu par défaut fonctionne comme suit :

- Les connexions sortantes à partir d’appareils sont autorisées par défaut, quel que soit l’emplacement.
- Lorsque des appareils sont connectés au réseau de votre entreprise, toutes les connexions entrantes sont autorisées par défaut.
- Lorsque des appareils sont connectés à un réseau public ou privé, toutes les connexions entrantes sont bloquées par défaut.

Dans Microsoft Defender entreprise (prévisualisation), vous pouvez définir des exceptions pour bloquer ou autoriser les connexions entrantes. Vous définissez ces exceptions en créant des règles personnalisées. Voir [Gérer les règles personnalisées pour les stratégies de pare-feu.](mdb-custom-rules-firewall.md)

## <a name="firewall-settings-you-can-configure-in-defender-for-business"></a>Paramètres de pare-feu que vous pouvez configurer dans Defender for Business

Microsoft Defender pour Entreprise (prévisualisation) inclut une protection pare-feu par Windows Defender pare-feu. Le tableau suivant répertorie les paramètres qui peuvent être configurés pour la protection du pare-feu dans Microsoft Defender pour Entreprises (prévisualisation). <br/><br/>

| Setting | Description |
|--|--|
| **Réseau de domaine** | Le profil réseau de domaine s’applique au réseau de votre entreprise. Les paramètres de pare-feu de votre réseau de domaine s’appliquent aux connexions entrantes qui sont lancées sur d’autres appareils qui se connectent au même réseau. Par défaut, les connexions entrantes sont définies **sur Autoriser tout**.  |
| **Réseau public** | Le profil de réseau public s’applique à un réseau que vous pouvez utiliser dans un emplacement public, tel qu’un café ou un aéroport. Les paramètres de pare-feu pour les réseaux publics s’appliquent aux connexions entrantes qui sont lancées sur d’autres appareils qui se connectent au même réseau. Étant donné qu’un réseau public peut inclure des appareils que vous ne connaissez pas ou ne faites pas confiance, les connexions entrantes sont définies sur Bloquer **tout** par défaut.  |
| **Réseau privé** | Le profil de réseau privé s’applique à un réseau dans un emplacement privé, tel que votre domicile. Les paramètres de pare-feu pour les réseaux privés s’appliquent aux connexions entrantes qui sont lancées sur d’autres appareils qui se connectent au même réseau. En règle générale, sur un réseau privé, il est supposé que tous les autres appareils sur le même réseau sont des appareils de confiance. Toutefois, par défaut, les connexions entrantes sont définies sur **Bloquer tout.** |
| **Règles personnalisées** | [Les règles personnalisées](mdb-custom-rules-firewall.md) vous permettent de bloquer ou d’autoriser des connexions spécifiques. Par exemple, supposons que vous vouliez bloquer toutes les connexions entrantes sur les appareils connectés à un réseau privé, à l’exception des connexions via une application spécifique sur un appareil. Dans ce cas, vous définissez **le** réseau privé pour bloquer toutes les connexions entrantes, puis vous ajoutez une règle personnalisée pour définir l’exception. <br/><br/>Vous pouvez utiliser des règles personnalisées pour définir des exceptions pour des fichiers ou des applications spécifiques, une adresse IP ou une plage d’adresses IP. <br/><br/>Selon le type de règle personnalisée que vous créez, voici quelques exemples de valeurs que vous pouvez utiliser : <br/><br/>Chemin d’accès au fichier d’application : `C:\Windows\System\Notepad.exe or %WINDIR%\Notepad.exe` <br/><br/>IP : une adresse IPv4/IPv6 valide, telle que `192.168.1.0` ou `192.168.1.0/24` <br/><br/>IP : plage d’adresses IPv4/IPv6 valide, formatée `192.168.1.0-192.168.1.9` comme (sans espace inclus) |

## <a name="next-steps"></a>Prochaines étapes

- [Gérer les paramètres de pare-feu dans Microsoft Defender entreprise (aperçu)](mdb-custom-rules-firewall.md)

- [En savoir plus sur Windows Defender pare-feu](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise (prévisualisation)](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)