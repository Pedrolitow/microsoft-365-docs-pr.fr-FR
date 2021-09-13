---
title: Configurer des substitutions locales pour les paramètres de l’Antivirus Microsoft Defender
description: Activez ou désactivez les utilisateurs pour qu’ils ne modifient pas localement les paramètres dans l’Antivirus Microsoft Defender.
keywords: remplacement local, stratégie locale, stratégie de groupe, gpo, verrouillage, fusion, listes
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 02/13/2020
ms.reviewer: ''
manager: dansimp
ms.openlocfilehash: d70d35bc1e2baa795e024da79ea613087bf511d4
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59179371"
---
# <a name="prevent-or-allow-users-to-locally-modify-microsoft-defender-antivirus-policy-settings"></a>Empêcher ou autoriser les utilisateurs à modifier localement les paramètres Antivirus Microsoft Defender stratégie


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Par défaut, Antivirus Microsoft Defender paramètres déployés via un objet de stratégie de groupe sur les points de terminaison de votre réseau empêcheront les utilisateurs de modifier localement les paramètres. Vous pouvez le modifier dans certains cas.

Par exemple, il peut être nécessaire d’autoriser certains groupes d’utilisateurs (tels que les chercheurs en sécurité et les enquêteurs des menaces) à contrôler davantage les paramètres individuels sur les points de terminaison qu’ils utilisent.

## <a name="configure-local-overrides-for-microsoft-defender-antivirus-settings"></a>Configurer des substitutions locales pour Antivirus Microsoft Defender paramètres

Le paramètre par défaut de ces stratégies **est Désactivé.**

S’ils sont activés, les utilisateurs sur les points de terminaison peuvent apporter des modifications au paramètre associé avec l’application [Sécurité Windows,](microsoft-defender-security-center-antivirus.md) les paramètres de stratégie de groupe locaux et les cmdlets PowerShell (le cas échéant).

Le tableau suivant répertorie chacun des paramètres de stratégie de remplacement et les instructions de configuration pour la fonctionnalité ou le paramètre associé.

Pour configurer ces paramètres :

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, cliquez sur **Configuration** ordinateur et cliquez **sur Modèles d’administration.**

3. Développez  **l’arborescence Windows composants > Antivirus Microsoft Defender** puis l’emplacement spécifié dans le tableau ci-dessous.

4. Double-cliquez sur le paramètre **de** stratégie comme indiqué dans le tableau ci-dessous et définissez l’option sur la configuration souhaitée. Cliquez **sur OK,** puis répétez l’une des autres configurations.

5. Déployez l’objet de stratégie de groupe comme d’habitude.

Emplacement|Setting|Article
---|---|---|---
MAPS|Configurer le remplacement de paramètre local pour la création de rapports à Microsoft MAPS|[Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md)
Quarantaine|Configurer le remplacement de paramètre local pour la suppression des éléments du dossier de mise en quarantaine|[Configurer la correction pour les analyses](configure-remediation-microsoft-defender-antivirus.md)
Protection en temps réel|Configurer le remplacement des paramètres locaux pour surveiller l’activité des fichiers et des programmes sur votre ordinateur|[Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md)
Protection en temps réel|Configurer le remplacement de paramètre local pour la surveillance de l’activité des fichiers entrants et sortants|[Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md)
Protection en temps réel|Configurer le remplacement de paramètre local pour l’analyse de tous les fichiers et pièces jointes téléchargés|[Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md)
Protection en temps réel|Configurer le remplacement de paramètre local pour activer l’analyse du comportement|[Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md)
Protection en temps réel|Configurer le remplacement de paramètre local pour activer la protection en temps réel|[Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md)
Correction|Configurer le remplacement de paramètre local pour l’heure de la journée afin d’exécuter une analyse complète programmée pour terminer la correction|[Configurer la correction pour les analyses](configure-remediation-microsoft-defender-antivirus.md)
Analyser|Configurer le remplacement de paramètre local pour le pourcentage maximal d’utilisation du processeur|[Configurer et exécuter des analyses](run-scan-microsoft-defender-antivirus.md)
Analyser|Configurer le remplacement de paramètre local pour le jour de l’analyse de planification|[Configurer des analyses programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
Analyser|Configurer le remplacement de paramètre local pour le temps d’analyse rapide programmé|[Configurer des analyses programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
Analyser|Configurer le remplacement de paramètre local pour l’heure d’analyse programmée|[Configurer des analyses programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
Analyser|Configurer le remplacement de paramètre local pour le type d’analyse à utiliser pour une analyse programmée|[Configurer des analyses programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)

<a id="merge-lists"></a>

## <a name="configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged"></a>Configurer la façon dont les listes de correction et d’exclusions des menaces définies localement et globalement sont fusionnées

Vous pouvez également configurer la façon dont les listes définies localement sont combinées ou fusionnées avec des listes définies globalement. Ce paramètre s’applique aux [listes d’exclusions,](configure-exclusions-microsoft-defender-antivirus.md) [aux listes de](configure-remediation-microsoft-defender-antivirus.md)correction spécifiées et à la réduction de la surface [d’attaque.](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction)

Par défaut, les listes qui ont été configurées dans la stratégie de groupe locale et l’application Sécurité Windows sont fusionnées avec les listes définies par l’objet de stratégie de groupe approprié que vous avez déployé sur votre réseau. En cas de conflit, la liste définie globalement est prioritaire.

Vous pouvez désactiver ce paramètre pour vous assurer que seules les listes définies globalement (telles que celles des G GPO déployés) sont utilisées.

### <a name="use-group-policy-to-disable-local-list-merging"></a>Utiliser la stratégie de groupe pour désactiver la fusion de listes locales

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, cliquez sur **Configuration** ordinateur et cliquez **sur Modèles d’administration.**

3. Développez l’arborescence **Windows composants > Antivirus Microsoft Defender**.

4. Double-cliquez **sur Configurer le comportement de fusion de l’administrateur local** pour les listes et définissez l’option sur **Désactivé.** Cliquez sur **OK**.

> [!NOTE]
> Si vous désactivez la fusion de listes locales, elle remplacera les paramètres d’accès contrôlé aux dossiers. Elle remplace également les dossiers protégés ou les applications autorisées définies par l’administrateur local. Pour plus d’informations sur les paramètres d’accès contrôlé aux dossiers, voir Autoriser une application [bloquée dans Sécurité Windows](https://support.microsoft.com/help/4046851/windows-10-allow-blocked-app-windows-security).

## <a name="related-topics"></a>Rubriques connexes

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Configurer l’interaction de l’utilisateur final avec Antivirus Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
