---
title: Configurer des remplacements locaux pour Microsoft Defender paramètres antivirus
description: Activez ou désactivez les utilisateurs des paramètres modifiés localement dans Microsoft Defender Antivirus.
keywords: remplacement local, stratégie locale, stratégie de groupe, gpo, verrouillage, fusion, listes
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 08/02/2022
ms.reviewer: ''
manager: dansimp
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 5d1857105c8043a38b486f435506a4dca017fee4
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68172222"
---
# <a name="prevent-or-allow-users-to-locally-modify-microsoft-defender-antivirus-policy-settings"></a>Empêcher ou autoriser les utilisateurs à modifier localement Microsoft Defender paramètres de stratégie antivirus


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Par défaut, Microsoft Defender paramètres antivirus déployés via un objet stratégie de groupe aux points de terminaison de votre réseau empêche les utilisateurs de modifier localement les paramètres. Vous pouvez modifier cette configuration dans certains cas. Par exemple, il peut être nécessaire de permettre à certains groupes d’utilisateurs, tels que les chercheurs en sécurité et les enquêteurs sur les menaces, d’avoir un contrôle supplémentaire sur les paramètres individuels sur les points de terminaison qu’ils utilisent.

## <a name="configure-local-overrides-for-microsoft-defender-antivirus-settings"></a>Configurer des remplacements locaux pour Microsoft Defender paramètres antivirus

Le paramètre par défaut de ces stratégies de remplacement local est **Désactivé**.

Si les stratégies sont définies sur **Activé**, les utilisateurs peuvent apporter des modifications aux paramètres associés sur leurs appareils à l’aide de l’application [Sécurité Windows](microsoft-defender-security-center-antivirus.md), des paramètres stratégie de groupe locaux ou des applets de commande PowerShell (le cas échéant).

La [section table des paramètres](#table-of-settings) répertorie les paramètres de stratégie de remplacement et les instructions de configuration.

Pour configurer ces paramètres :

1. Sur votre ordinateur de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

2. Dans l’**Éditeur de gestion des stratégies de groupe** accédez à **Configuration de l’ordinateur** et sélectionnez **Modèles d’administration**.

3. Développez l’arborescence sur **les composants** >  Windows **Microsoft Defender Antivirus**, puis **l’emplacement** spécifié dans la [section Table des paramètres](#table-of-settings) (dans cet article).

4. Double-cliquez sur le **paramètre** de stratégie comme spécifié dans le tableau ci-dessous, puis définissez l’option sur la configuration souhaitée. Sélectionnez **OK**, puis répétez pour tous les autres paramètres.

5. Déployez l’objet stratégie de groupe comme d’habitude.

## <a name="table-of-settings"></a>Table des paramètres

| Emplacement | Setting | Article |
|---|---|---|---|
| CARTES |Configurer le remplacement des paramètres locaux pour la création de rapports à Microsoft MAPS|[Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) |
| Quarantaine|Configurer le remplacement des paramètres locaux pour la suppression d’éléments du dossier Quarantaine|[Configurer la correction pour les analyses](configure-remediation-microsoft-defender-antivirus.md) |
| Protection en temps réel|Configurer le remplacement des paramètres locaux pour surveiller l’activité de fichier et de programme sur votre ordinateur|[Activer et configurer Microsoft Defender protection et surveillance always on antivirus](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Protection en temps réel|Configurer le remplacement des paramètres locaux pour la surveillance de l’activité de fichier entrante et sortante | [Activer et configurer Microsoft Defender protection et surveillance always on antivirus](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Protection en temps réel|Configurer le remplacement des paramètres locaux pour l’analyse de tous les fichiers téléchargés et pièces jointes|[Activer et configurer Microsoft Defender protection et surveillance always on antivirus](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Protection en temps réel|Configurer le remplacement des paramètres locaux pour activer la surveillance du comportement|[Activer et configurer Microsoft Defender protection et surveillance always on antivirus](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Protection en temps réel|Configurer le remplacement de paramètre local pour activer la protection en temps réel|[Activer et configurer Microsoft Defender protection et surveillance always on antivirus](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Assainissement|Configurer le remplacement des paramètres locaux pour l’heure de la journée afin d’exécuter une analyse complète planifiée pour terminer la correction|[Configurer la correction pour les analyses](configure-remediation-microsoft-defender-antivirus.md) |
| Analyser|Configurer le remplacement des paramètres locaux pour le pourcentage maximal d’utilisation du processeur|[Configurer et exécuter des analyses](run-scan-microsoft-defender-antivirus.md) |
| Analyser|Configurer le remplacement des paramètres locaux pour le jour de l’analyse de planification|[Configurer les analyses planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Analyser|Configurer le remplacement des paramètres locaux pour le temps d’analyse rapide planifié|[Configurer les analyses planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Analyser|Configurer le remplacement des paramètres locaux pour l’heure d’analyse planifiée|[Configurer les analyses planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Analyser|Configurer le remplacement de paramètre local pour le type d’analyse à utiliser pour une analyse planifiée|[Configurer les analyses planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |

<a id="merge-lists"></a>

## <a name="configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged"></a>Configurer la façon dont les listes de correction et d’exclusions des menaces définies localement et globalement sont fusionnées

Vous pouvez également configurer la façon dont les listes définies localement sont combinées ou fusionnées avec des listes définies globalement. Ce paramètre s’applique aux [listes d’exclusion](configure-exclusions-microsoft-defender-antivirus.md), aux [listes de correction spécifiées](configure-remediation-microsoft-defender-antivirus.md) et à [la réduction de la surface d’attaque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction).

Par défaut, les listes qui ont été configurées dans la stratégie de groupe locale et l’application Sécurité Windows sont fusionnées avec les listes définies par l’objet stratégie de groupe approprié que vous avez déployé sur votre réseau. En cas de conflits, la liste définie à l’échelle mondiale est prioritaire. Vous pouvez désactiver ce paramètre pour vous assurer que seules les listes définies à l’échelle mondiale (telles que celles de tous les objets de stratégie de groupe déployés) sont utilisées.

### <a name="use-group-policy-to-disable-local-list-merging"></a>Utiliser stratégie de groupe pour désactiver la fusion de listes locales

1. Sur votre ordinateur de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. Dans l’**Éditeur de gestion des stratégies de groupe** accédez à **Configuration de l’ordinateur** et sélectionnez **Modèles d’administration**.

3. Développez l’arborescence sur **les composants** >  Windows **Microsoft Defender Antivirus**.

4. Double-cliquez sur **Configurer le comportement de fusion de l’administrateur local pour les listes** et définissez l’option **sur Désactivé**. Puis sélectionnez **OK**.

### <a name="use-microsoft-endpoint-manager-to-disable-local-list-merging"></a>Utiliser Microsoft Endpoint Manager pour désactiver la fusion de listes locales

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://endpoint.microsoft.com), sélectionnez Antivirus **de sécurité** >  de point de **terminaison**.

2. Choisissez **Créer** une stratégie ou modifiez une stratégie antivirus Microsoft Defender existante.

3. Sous les **paramètres de configuration**, sélectionnez la liste déroulante en regard de **Désactiver la fusion locale Administration**, puis sélectionnez **Désactiver la fusion locale Administration**.

> [!NOTE]
> Si vous désactivez la fusion de liste locale, elle remplace les paramètres d’accès contrôlé aux dossiers. Il remplace également les dossiers protégés ou les applications autorisées définis par l’administrateur local. Pour plus d’informations sur les paramètres d’accès contrôlé aux dossiers, consultez [Autoriser une application bloquée dans Sécurité Windows](https://support.microsoft.com/help/4046851/windows-10-allow-blocked-app-windows-security).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-topics"></a>Voir aussi

- [Microsoft Endpoint Manager](/mem/endpoint-manager-overview)
- [Antivirus Microsoft Defender dans Windows](microsoft-defender-antivirus-in-windows-10.md)
- [Configurer l’interaction de l’utilisateur final avec Microsoft Defender Antivirus](configure-end-user-interaction-microsoft-defender-antivirus.md)
