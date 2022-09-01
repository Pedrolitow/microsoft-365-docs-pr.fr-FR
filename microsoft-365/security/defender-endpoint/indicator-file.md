---
title: Créer des indicateurs pour les fichiers
ms.reviewer: ''
description: Créez des indicateurs pour un hachage de fichier qui définissent la détection, la prévention et l’exclusion des entités.
keywords: fichier, hachage, gérer, autorisé, bloqué, bloquer, nettoyer, malveillant, hachage de fichier, adresse IP, URL, domaine
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
ms.date: 08/10/2022
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: ea7283127708d5576e6436fae5f7f077d53182f6
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67521058"
---
# <a name="create-indicators-for-files"></a>Créer des indicateurs pour les fichiers

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour point de terminaison Plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/mdb-overview.md)

> [!TIP]
> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Empêchez la propagation d’une attaque dans votre organisation en interdisant les fichiers potentiellement malveillants ou les programmes malveillants suspectés. Si vous connaissez un fichier exécutable portable (PE) potentiellement malveillant, vous pouvez le bloquer. Cette opération empêche sa lecture, son écriture ou son exécution sur les appareils de votre organisation.

Il existe trois façons de créer des indicateurs pour les fichiers :

- En créant un indicateur via la page paramètres
- En créant un indicateur contextuel à l’aide du bouton Ajouter un indicateur à partir de la page de détails du fichier
- En créant un indicateur via [l’API Indicateur](ti-indicator.md)

## <a name="before-you-begin"></a>Avant de commencer

Il est important de comprendre les prérequis suivants avant de créer des indicateurs pour les fichiers :

- Cette fonctionnalité est disponible si votre organisation utilise **l’antivirus Microsoft Defender (en mode actif)** et que **la protection basée sur le cloud est activée**. Pour plus d’informations, consultez [Gérer la protection basée sur le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).

- La version du client Antimalware doit être 4.18.1901.x ou ultérieure. Voir [les versions mensuelles de la plateforme et du moteur](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)

- Pris en charge sur les appareils avec Windows 10, version 1703 ou ultérieure, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 et Windows Server 2022.
    
   > [!NOTE]
   > Windows Server 2016 et Windows Server 2012 R2 doivent être intégrés à l’aide des instructions fournies dans [les serveurs Windows intégrés](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) pour que cette fonctionnalité fonctionne. Les indicateurs de fichier personnalisés avec les actions Autoriser, Bloquer et Corriger sont désormais également disponibles dans les [fonctionnalités améliorées du moteur anti-programme malveillant pour macOS et Linux](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/enhanced-antimalware-engine-capabilities-for-linux-and-macos/ba-p/3292003).

- Pour commencer à bloquer des fichiers, vous devez [d’abord activer la fonctionnalité « bloquer ou autoriser »](advanced-features.md) dans Paramètres.

Cette fonctionnalité est conçue pour empêcher le téléchargement de logiciels malveillants (ou de fichiers potentiellement malveillants) à partir du web. Il prend actuellement en charge les fichiers exécutables portables (PE), y compris les fichiers .exe et .dll. La couverture sera prolongée au fil du temps.

> [!IMPORTANT]
> Dans Defender pour point de terminaison Plan 1 et Defender entreprise, vous pouvez créer un indicateur pour bloquer ou autoriser un fichier. Dans Defender entreprise, votre indicateur est appliqué dans votre environnement et ne peut pas être étendu à des appareils spécifiques.

## <a name="create-an-indicator-for-files-from-the-settings-page"></a>Créer un indicateur pour les fichiers à partir de la page paramètres

1. Dans le volet de navigation, sélectionnez **Paramètres** \> Points de **terminaison Indicateurs** \> (sous **Règles**).

2. Sélectionnez l’onglet **Hachages de** fichier.

3. Sélectionnez **Ajouter un élément**.

4. Spécifiez les détails suivants :
    - Indicateur : spécifiez les détails de l’entité et définissez l’expiration de l’indicateur.
    - Action : spécifiez l’action à entreprendre et fournissez une description.
    - Étendue : définissez l’étendue du groupe d’appareils (l’étendue n’est pas disponible dans [Defender entreprise](../defender-business/mdb-overview.md)).

5. Passez en revue les détails sous l’onglet Résumé, puis **sélectionnez Enregistrer**.

## <a name="create-a-contextual-indicator-from-the-file-details-page"></a>Créer un indicateur contextuel à partir de la page de détails du fichier

L’une des options lors de [l’exécution d’actions de réponse sur un fichier](respond-file-alerts.md) consiste à ajouter un indicateur pour le fichier. Lorsque vous ajoutez un hachage d’indicateur pour un fichier, vous pouvez choisir de déclencher une alerte et de bloquer le fichier chaque fois qu’un appareil de votre organisation tente de l’exécuter.

Les fichiers automatiquement bloqués par un indicateur ne s’affichent pas dans le centre d’action du fichier, mais les alertes restent visibles dans la file d’attente des alertes.

## <a name="public-preview-alerting-on-file-blocking-actions"></a>Préversion publique : Alertes sur les actions de blocage de fichiers

> [!IMPORTANT]
> Les informations contenues dans cette section (**préversion publique pour le moteur d’investigation et de correction automatisée**) concernent le produit de préversion qui peut être considérablement modifié avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Les actions actuellement prises en charge pour l’ioc de fichier sont autoriser, auditer et bloquer et corriger. Après avoir choisi de bloquer un fichier, vous pouvez choisir si le déclenchement d’une alerte est nécessaire. De cette façon, vous serez en mesure de contrôler le nombre d’alertes à envoyer à vos équipes d’opérations de sécurité et de vous assurer que seules les alertes requises sont déclenchées.

Dans Microsoft 365 Defender, accédez à **Paramètres** > **Les indicateurs de points de terminaison** >  > **ajoutent un nouveau hachage de fichier**.

Choisissez de bloquer et de corriger le fichier.

Choisissez si vous souhaitez générer une alerte sur l’événement de bloc de fichiers et définir les paramètres des alertes :

- Titre de l’alerte
- Gravité de l’alerte
- Catégorie
- Description
- Actions recommandées

:::image type="content" source="images/indicators-generate-alert.png" alt-text="Paramètres d’alerte pour les indicateurs de fichier" lightbox="images/indicators-generate-alert.png":::

> [!IMPORTANT]
>
> - En règle générale, les blocs de fichiers sont appliqués et supprimés en quelques minutes, mais peuvent prendre jusqu’à 30 minutes.
> - S’il existe des stratégies IoC de fichier en conflit avec le même type d’application et la même cible, la stratégie du hachage plus sécurisé est appliquée. Une stratégie IoC de hachage de fichier SHA-256 gagnera une stratégie IoC de hachage de fichier SHA-1, qui gagnera une stratégie IoC de hachage de fichier MD5 si les types de hachage définissent le même fichier. Cela est toujours vrai, quel que soit le groupe d’appareils.
> - Dans tous les autres cas, si des stratégies IoC de fichier en conflit avec la même cible d’application sont appliquées à tous les appareils et au groupe de l’appareil, pour un appareil, la stratégie dans le groupe d’appareils gagne.
> - Si la stratégie de groupe EnableFileHashComputation est désactivée, la précision de blocage de l’IoC de fichier est réduite. Toutefois, l’activation `EnableFileHashComputation` peut avoir un impact sur les performances de l’appareil. Par exemple, la copie de fichiers volumineux à partir d’un partage réseau sur votre appareil local, en particulier via une connexion VPN, peut avoir un effet sur les performances de l’appareil.
>
> Pour plus d’informations sur la stratégie de groupe EnableFileHashComputation, consultez [defender CSP](/windows/client-management/mdm/defender-csp).
>
> Pour plus d’informations sur la configuration de cette fonctionnalité sur Defender pour point de terminaison sur Linux et macOS, consultez [Configurer la fonctionnalité de calcul de hachage de fichier sur Linux](linux-preferences.md#configure-file-hash-computation-feature) et [configurer la fonctionnalité de calcul de hachage de fichier sur macOS](mac-preferences.md#configure-file-hash-computation-feature).

## <a name="public-preview-advanced-hunting-capabilities"></a>Préversion publique : Fonctionnalités de chasse avancées

> [!IMPORTANT]
> Les informations contenues dans cette section (**préversion publique pour le moteur d’investigation et de correction automatisée**) concernent le produit de préversion qui peut être considérablement modifié avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Vous pouvez interroger l’activité d’action de réponse à l’avance. Voici un exemple de requête de chasse avancée :

```console
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
Timestamp > ago(30d)
| where AdditionalFields contains "EUS:Win32/CustomEnterpriseBlock!cl"
```

Pour plus d’informations sur la chasse avancée, consultez [La chasse proactive contre les menaces avec la chasse avancée](advanced-hunting-overview.md).

Voici d’autres noms de threads qui peuvent être utilisés dans l’exemple de requête ci-dessus :

Fichiers :

- EUS:Win32/CustomEnterpriseBlock!cl
- EUS:Win32/CustomEnterpriseNoAlertBlock!cl

Certificats:

- EUS:Win32/CustomCertEnterpriseBlock!cl

L’activité d’action de réponse peut également être visible dans la chronologie de l’appareil.

## <a name="policy-conflict-handling"></a>Gestion des conflits de stratégie

Le conflit de gestion des stratégies Cert et File IoC suit l’ordre ci-dessous :

- Si le fichier n’est pas autorisé par Windows Defender Contrôle d’application et AppLocker appliquent une stratégie/stratégies de mode, **bloquez**
- Sinon, si le fichier est autorisé par l’exclusion de l’Antivirus Microsoft Defender, **autorisez**
- Sinon, si le fichier est bloqué ou averti par un bloc ou avertit l’IoC du fichier, **bloquez/avertissez**
- Sinon, si le fichier est autorisé par une stratégie IoC de fichier d’autorisation, **autorisez**
- Sinon, si le fichier est bloqué par des règles ASR, CFA, AV, SmartScreen, puis **Bloquer**
- Sinon **, autoriser** (passe Windows Defender Application Control & stratégie AppLocker, aucune règle IoC ne s’applique à celle-ci)

>[!NOTE]
> Dans les situations où l’antivirus Microsoft Defender est défini sur **Bloquer**, mais que Defender pour point de terminaison est défini sur **Autoriser**, la stratégie est définie par défaut sur **Autoriser**.

S’il existe des stratégies IoC de fichier en conflit avec le même type d’application et la même cible, la stratégie du hachage plus sécurisé (c’est-à-dire plus long) est appliquée. Par exemple, une stratégie IoC de hachage de fichier SHA-256 gagnera une stratégie IoC de hachage de fichier MD5 si les deux types de hachage définissent le même fichier.

> [!WARNING]
> La gestion des conflits de stratégie pour les fichiers et les certificats diffère de la gestion des conflits de stratégie pour les domaines/URL/adresses IP.

les fonctionnalités d’application vulnérables de bloc de Gestion des vulnérabilités Microsoft Defender utilisent les E/S de fichier pour l’application et suivent l’ordre de gestion des conflits ci-dessus.

### <a name="examples"></a>Exemples

<br>

****

|Composant|Application des composants|Action de l’indicateur de fichier|Résultat|
|---|---|---|---|
|Exclusion du chemin d’accès du fichier de réduction de la surface d’attaque|Autoriser|Bloquer|Bloquer|
|Règle de réduction de la surface d’attaque|Bloquer|Autoriser|Autoriser|
|Windows Defender Application Control|Autoriser|Bloquer|Autoriser|
|Windows Defender Application Control|Bloquer|Autoriser|Bloquer|
|Exclusion de l’antivirus Microsoft Defender|Autoriser|Bloquer|Autoriser|
|

## <a name="see-also"></a>Voir aussi

- [Créer des indicateurs](manage-indicators.md)
- [Créer des indicateurs pour les IP et URL/domaines](indicator-ip-domain.md)
- [Créer des indicateurs basés sur des certificats](indicator-certificates.md)
- [Gérer des indicateurs](indicator-manage.md)
