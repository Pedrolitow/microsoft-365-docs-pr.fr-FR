---
title: Signaler et résoudre les problèmes de Règles asr de Microsoft Defender pour les points de terminaison
description: Cette rubrique décrit comment signaler et dépanner les règles de résolution des problèmes de Microsoft Defender pour endpoint ASR
keywords: Règles de réduction de la surface d’attaque, asr, hips, système de prévention des intrusions hôtes, règles de protection, anti-attaque, attaque, prévention des infections, microsoft defender pour le point de terminaison
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
audience: ITPro
author: lovina-saldanha
ms.author: v-lsaldanha
ms.reviewer: ''
manager: dansimp
ms.custom: asr
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 6e918c85e50f0e6f675cc623cf7765de6518ab1d
ms.sourcegitcommit: 4740e69326eb7f8302eec7bab5bd516d498e4492
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2021
ms.locfileid: "59401289"
---
# <a name="report-and-troubleshoot-microsoft-defender-for-atp-asr-rules"></a>Signaler et résoudre les problèmes de Microsoft Defender pour les règles DE LAR ATP

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Le centre Microsoft 365 de sécurité est la nouvelle interface de surveillance et de gestion de la sécurité au sein de vos identités, données, appareils, applications et infrastructure Microsoft. Vous pouvez ici consulter facilement l’état de la sécurité de votre organisation, agir pour configurer les appareils, les utilisateurs et les applications ainsi que recevoir des alertes relatives aux activités suspectes. Le Centre de sécurité Microsoft 365 est destiné aux administrateurs de la sécurité et aux équipes d’exploitation de la sécurité pour améliorer la gestion et la protection de leur organisation. Visitez le centre Microsoft 365 sécurité sur <https://security.microsoft.com> .

Dans Microsoft 365 de sécurité, nous vous proposons un coup d’œil complet sur la configuration et les événements actuels des règles asr dans votre patrimoine. Notez que vos appareils doivent être intégrés au service Microsoft Defender for Endpoint pour que ces rapports soient remplis.
Voici une capture d’écran du centre de sécurité Microsoft 365 (sous **Réduction** de la surface d’attaque des appareils \>  \> **de rapports).** Au niveau de l’appareil, **sélectionnez Configuration** dans le volet Règles de réduction de **la surface d’attaque.** L’écran suivant s’affiche, dans lequel vous pouvez sélectionner un appareil spécifique et vérifier sa configuration de règle asr individuelle.

:::image type="content" source="images/asrrulesnew.png" lightbox="images/asrrulesnew.png" alt-text="Écran règles de la asr.":::

## <a name="microsoft-defender-for-endpoint---advanced-hunting"></a>Microsoft Defender pour le point de terminaison - Recherche avancée

L’une des fonctionnalités les plus puissantes de Microsoft Defender pour point de terminaison est le recherche avancée. Si vous ne connaissez pas le hunting avancé, recherchez de manière proactive les menaces [avec le chasse avancée.](advanced-hunting-overview.md)

Le hunting avancé est un outil de recherche de menace basé sur une requête (Kusto Query Language) qui vous permet d’explorer jusqu’à 30 jours des données capturées (brutes) collectées par Defender for Endpoint à partir de vos appareils. Grâce à la recherche avancée, vous pouvez inspecter de manière proactive les événements pour rechercher des indicateurs et des entités intéressants. L’accès flexible aux données permet un recherche sans contraintes pour les menaces connues et potentielles.

Grâce à la recherche avancée, il est possible d’extraire des informations sur les règles de la asr, de créer des rapports et d’obtenir des informations détaillées sur le contexte d’un événement d’audit ou de blocage de règle asr donné.

Les événements de règles ASR peuvent être interrogés à partir de la table DeviceEvents de la section de recherche avancée du Microsoft 365 Defender. Par exemple, une requête simple, telle que celle ci-dessous, peut signaler tous les événements qui ont des règles ASR en tant que source de données, au cours des 30 derniers jours, et les synthétisera par le nombre ActionType, qu’il s’agit dans ce cas du nom de code réel de la règle asr.

:::image type="content" source="images/adv-hunt-querynew.png" alt-text="Requête de recherche avancée.":::

:::image type="content" source="images/adv-hunt-sc-2new.png" lightbox="images/adv-hunt-sc-2new.png" alt-text="écran de recherche avancée.":::

Avec le repérage avancé, vous pouvez mettre en forme les requêtes à votre convenance, afin de voir ce qui se passe, que vous vouliez identifier un pointage sur un ordinateur individuel ou que vous vouliez extraire des informations de l’ensemble de votre environnement.

## <a name="microsoft-defender-for-endpoint-machine-timeline"></a>Chronologie de l’ordinateur Microsoft Defender for Endpoint

Une alternative à la recherche avancée, mais avec une étendue plus étroite, est la chronologie de l’ordinateur Microsoft Defender for Endpoint. Vous pouvez afficher tous les événements collectés d’un appareil, au cours des six derniers mois, dans la Microsoft 365 Defender, en allant dans la liste Ordinateurs, sélectionnez un ordinateur donné, puis cliquez sur l’onglet Chronologie.

Voici une capture d’écran de l’affichage Chronologie de ces événements sur un point de terminaison donné. À partir de cet affichage, vous pouvez filtrer la liste des événements en fonction de n’importe quel groupe d’événements le long du volet droit. Vous pouvez également activer ou désactiver les événements marqués et verbose lors de l’affichage des alertes et du défilement dans la chronologie historique.

:::image type="content" source="images/mic-sec-def-timelinenew.png" lightbox="images/mic-sec-def-timelinenew.png" alt-text="Microsoft 365 Defender chronologie.":::

## <a name="how-to-troubleshoot-asr-rules"></a>Comment résoudre les problèmes de règles de la asr ?

La première et la plus immédiate consiste à vérifier localement, sur un appareil Windows, les règles asr sont activées (et leur configuration) à l’aide des cmdlets PowerShell.

Voici quelques autres sources d’informations que vous Windows, pour résoudre les problèmes d’impact et de fonctionnement des règles asr.

### <a name="querying-which-rules-are-active"></a>Interrogation des règles actives

L’une des façons les plus simples de déterminer si les règles de asr sont déjà activées consiste à utiliser une cmdlet PowerShell, Get-MpPreference.

Voici un exemple :

:::image type="content" source="images/getmpreferencescriptnew.png" lightbox="images/getmpreferencescriptnew.png" alt-text="obtenir un script mppreference.":::

Plusieurs règles de asr sont actives, avec différentes actions configurées.

Pour développer les informations ci-dessus sur les règles de la asr, vous pouvez utiliser les propriétés **AttackSurfaceReductionRules_Ids** et/ou **AttackSurfaceReductionRules_Actions**.

Exemple :

```powershell
Get-MPPreference | Select-Object -ExpandProperty**AttackSurfaceReductionRules_Ids
```

:::image type="content" source="images/getmpref-examplenew.png" alt-text="obtenir un exemple de mpreference.":::

L’exemple ci-dessus montre tous les ID pour les règles de asr qui ont un paramètre différent de 0 (non configuré).

L’étape suivante consiste ensuite à lister les actions réelles (Bloquer ou Auditer) avec qui chaque règle est configurée.

```powershell
Get-MPPreference | Select-Object -ExpandProperty**AttackSurfaceReductionRules_Actions
```

:::image type="content" source="images/getmpref-example2new.png" alt-text="get mppreference example2.":::

### <a name="querying-blocking-and-auditing-events"></a>Interrogation des événements de blocage et d’audit

Les événements de règle asr peuvent être vus dans Windows Defender journal.

Pour y accéder, ouvrez Windows’observateur d’événements et accédez aux journaux des **applications** et des services \> **microsoft** \> **Windows** \> **Windows Defender** \> **opérationnels.**

:::image type="content" source="images/eventviewerscrnew.png" lightbox="images/eventviewerscrnew.png" alt-text="scr de l’observateur d’événements.":::

## <a name="microsoft-defender-malware-protection-logs"></a>Journaux de protection contre les programmes malveillants Microsoft Defender

Vous pouvez également afficher les événements de règle via Antivirus Microsoft Defender’outil en ligne de commande dédié, appelé , qui peut être utilisé pour gérer et configurer, et automatiser les tâches si `*mpcmdrun.exe*` nécessaire.

Vous pouvez trouver cet utilitaire dans *%ProgramFiles%\Windows Defender\MpCmdRun.exe*. Vous devez l’exécuter à partir d’une invite de commandes avec élévation de privilèges (autrement dit, exécuter en tant qu’administrateur).

Pour générer les informations de support, *tapezMpCmdRun.exe -getfiles*. Après un certain temps, plusieurs journaux seront empaquetés dans une archive (MpSupportFiles.cab) et disponibles dans *C:\ProgramData\Microsoft\Windows Defender\Support*.

:::image type="content" source="images/malware-prot-logsnew.png" alt-text="journaux de protection contre les programmes malveillants.":::

Extrayez cette archive et de nombreux fichiers seront disponibles à des fins de dépannage.

Les fichiers les plus pertinents sont les suivants :

- **MPOperationalEvents.txt**: ce fichier contient le même niveau d’informations que celui de l’Observateur d’événements Windows Defender journal opérationnel de l’utilisateur.
- **MPRegistry.txt**: dans ce fichier, vous pouvez analyser toutes les configurations de Windows Defender, à partir du moment où les journaux de support ont été capturés.
- **MPLog.txt**: ce journal contient des informations plus détaillées sur toutes les actions/opérations du Windows Defender.
