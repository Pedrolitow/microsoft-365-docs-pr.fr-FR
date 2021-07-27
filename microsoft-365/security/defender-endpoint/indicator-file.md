---
title: Créer des indicateurs pour les fichiers
ms.reviewer: ''
description: Créez des indicateurs pour un hachage de fichier qui définissent la détection, la prévention et l’exclusion des entités.
keywords: fichier, hachage, gérer, autorisé, bloqué, bloquer, nettoyer, malveillant, hachage de fichier, adresse IP, url, domaine
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
ms.openlocfilehash: 535a729a56c5841eb6591ec34ac934c0446fefbd
ms.sourcegitcommit: bef7bd019531317d083c1125f7d339750c450b2f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2021
ms.locfileid: "53587701"
---
# <a name="create-indicators-for-files"></a>Créer des indicateurs pour les fichiers

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Empêcher toute propagation supplémentaire d’une attaque dans votre organisation en interdit les fichiers potentiellement malveillants ou les programmes malveillants suspects. Si vous connaissez un fichier exécutable portable (PE) potentiellement malveillant, vous pouvez le bloquer. Cette opération l’empêche d’être lue, écrite ou exécutée sur les appareils de votre organisation.

Il existe trois façons de créer des indicateurs pour les fichiers :

- En créant un indicateur via la page paramètres
- En créant un indicateur contextuel à l’aide du bouton Ajouter un indicateur à partir de la page de détails du fichier
- En créant un indicateur via [l’API d’indicateur](ti-indicator.md)

## <a name="before-you-begin"></a>Avant de commencer

Il est important de comprendre les conditions préalables suivantes avant de créer des indicateurs pour les fichiers :

- Cette fonctionnalité est disponible si votre organisation utilise **Antivirus Microsoft Defender (en mode actif)** et si la protection basée sur **le cloud est activée.** Pour plus d’informations, [voir Gérer la protection basée sur le cloud.](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus)

- La version du client anti-programme malveillant doit être 4.18.1901.x ou version ultérieure. Voir [les versions mensuelles de la plateforme et du moteur](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)

- Pris en charge sur les appareils Windows 10, version 1703 ou ultérieure, Windows Server 2016 et 2019.

- Pour commencer à bloquer les fichiers, vous devez d’abord [activer](advanced-features.md) la fonctionnalité « bloquer ou autoriser » dans Paramètres.

Cette fonctionnalité est conçue pour empêcher le téléchargement de programmes malveillants (ou de fichiers potentiellement malveillants) à partir du web. Il prend actuellement en charge les fichiers exécutables portables(PE), notamment les fichiers .exe et .dll portables. La couverture sera étendue au fil du temps.

## <a name="create-an-indicator-for-files-from-the-settings-page"></a>Créer un indicateur pour les fichiers à partir de la page paramètres

1. Dans le volet de navigation, sélectionnez  **Paramètres** \> **indicateurs de points** de \> **terminaison** (sous **Règles).**

2. Sélectionnez **l’onglet Hchéths fichier.**  

3. Sélectionnez **Ajouter un indicateur**.

4. Spécifiez les détails suivants :
    - Indicateur : spécifiez les détails de l’entité et définissez l’expiration de l’indicateur.
    - Action : spécifiez l’action à prendre et fournissez une description.
    - Étendue : définir l’étendue du groupe d’appareils.

5. Examinez les détails dans l’onglet Résumé, puis sélectionnez **Enregistrer.**

## <a name="create-a-contextual-indicator-from-the-file-details-page"></a>Créer un indicateur contextuel à partir de la page de détails du fichier

L’une des options lorsque vous prenez des mesures de réponse sur un [fichier consiste](respond-file-alerts.md)à ajouter un indicateur pour le   fichier. Lorsque vous ajoutez un hachage d’indicateur pour un fichier, vous pouvez choisir de lancer une alerte et de bloquer le fichier chaque fois qu’un appareil de votre organisation tente de l’exécuter.

Les fichiers automatiquement bloqués par un indicateur ne s’afficheront pas dans le centre de l’action du fichier, mais les alertes resteront visibles dans la file d’attente des alertes.

> [!IMPORTANT]
>
>- En règle générale, les blocs de fichiers sont appliqués et supprimés en quelques minutes, mais peuvent prendre plus de 30 minutes.
>
>- S’il existe des stratégies IoC de fichier en conflit avec le même type d’application et la même cible, la stratégie de hachage le plus sécurisé est appliquée. Une stratégie IoC de hachage de fichier SHA-256 l’emporte sur une stratégie IoC de hachage de fichier SHA-1, qui l’emporte sur une stratégie IoC de hachage de fichier MD5 si les types de hachage définissent le même fichier. Cela est toujours vrai quel que soit le groupe d’appareils.
>  Dans tous les autres cas, si des stratégies IoC de fichier en conflit avec la même cible d’application sont appliquées à tous les appareils et au groupe de l’appareil, pour un appareil, la stratégie dans le groupe d’appareils l’emporte.
>
> - Si la stratégie de groupe EnableFileHashComputation est désactivée, la précision de blocage du fichier IoC est réduite. Toutefois, `EnableFileHashComputation` l’activation peut avoir un impact sur les performances de l’appareil. Par exemple, la copie de fichiers de grande taille à partir d’un partage réseau sur votre appareil local, en particulier sur une connexion VPN, peut avoir un impact sur les performances de l’appareil.
>
>   Pour plus d’informations sur la stratégie de groupe EnableFileHashComputation, voir [CSP Defender](/windows/client-management/mdm/defender-csp)

## <a name="policy-conflict-handling"></a>Gestion des conflits de stratégie

Le conflit de gestion des stratégies Cert et IoC de fichier suit l’ordre ci-dessous :

- Si le fichier n’est pas autorisé par Windows Defender application Control et AppLocker appliquent des stratégies/stratégies de mode, **bloquez**
- Sinon, si le fichier est autorisé par l’exclusion Antivirus Microsoft Defender, **autorisez**
- Sinon, si le fichier est bloqué ou averti par un blocage ou un avertissement de fichier IoC, **puis Bloquer/Avertir**
- Sinon, si le fichier est autorisé par une stratégie IoC de fichier autorisé, **autorisez**
- Sinon si le fichier est bloqué par les règles de la asr, cfa, av, SmartScreen, puis **bloquer**
- Else **Allow** (passe Windows Defender Application Control & AppLocker, aucune règle IoC ne s’applique à elle)

S’il existe des stratégies IoC de fichier en conflit avec le même type d’application et la même cible, la stratégie de hachage le plus sécurisé (c’est-à-dire plus long) est appliquée. Par exemple, une stratégie IoC de hachage de fichier SHA-256 l’emporte sur une stratégie IoC de hachage de fichier MD5 si les deux types de hachage définissent le même fichier.

Les fonctionnalités gestion des vulnérabilités d’application vulnérables aux menaces et aux menaces utilisent les IOC de fichier pour l’application et suivent l’ordre de gestion des conflits ci-dessus.

### <a name="examples"></a>Exemples

|Composant|Application des composants|Action de l’indicateur de fichier|Résultat
|---|---|---|---|
|Exclusion du chemin d’accès au fichier de réduction de la surface d’attaque|Autoriser|Bloquer|Bloquer
|Règle de réduction de la surface d’attaque|Bloquer|Autoriser|Autoriser
|Windows Defender Application Control|Autoriser|Bloquer|Autoriser
|Windows Defender Application Control|Bloquer|Autoriser|Bloquer
|Antivirus Microsoft Defender exclusion|Autoriser|Bloquer|Autoriser

## <a name="see-also"></a>Voir aussi

- [Créer des indicateurs](manage-indicators.md)
- [Créer des indicateurs pour les IP et URL/domaines](indicator-ip-domain.md)
- [Créer des indicateurs basés sur des certificats](indicator-certificates.md)
- [Gérer des indicateurs](indicator-manage.md)
