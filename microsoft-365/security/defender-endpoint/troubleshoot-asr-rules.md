---
title: Signaler et résoudre les problèmes Microsoft Defender pour point de terminaison règles ASR
description: Cette rubrique explique comment signaler et résoudre Microsoft Defender pour point de terminaison règles ASR
keywords: Règles de réduction de la surface d’attaque, asr, hanches, système de prévention des intrusions de l’hôte, règles de protection, anti-exploitation, antiexploitation, exploit, prévention des infections, microsoft defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: lovina-saldanha
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.custom:
- asr
- admindeeplinkDEFENDER
ms.topic: article
ms.subservice: mde
ms.collection:
- m365-security
- tier3
search.appverid: met150
ms.openlocfilehash: 96b7600931d78e6ad1ada5197a79393efb4f1abb
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68229303"
---
# <a name="report-and-troubleshoot-microsoft-defender-for-endpoint-asr-rules"></a>Signaler et résoudre les problèmes Microsoft Defender pour point de terminaison règles ASR

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> est la nouvelle interface pour la surveillance et la gestion de la sécurité sur vos identités, données, appareils, applications et infrastructure Microsoft. Vous pouvez ici consulter facilement l’état de la sécurité de votre organisation, agir pour configurer les appareils, les utilisateurs et les applications ainsi que recevoir des alertes relatives aux activités suspectes. Le portail Microsoft 365 Defender est destiné aux administrateurs de sécurité et aux équipes chargées des opérations de sécurité afin de mieux gérer et protéger leur organisation. Visitez le portail Microsoft 365 Defender.<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>

Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a>, nous vous proposons un aperçu complet de la configuration et des événements actuels des règles ASR dans votre patrimoine. Notez que vos appareils doivent être intégrés au service Microsoft Defender pour point de terminaison pour que ces rapports soient remplis.
Voici une capture d’écran du portail Microsoft 365 Defender (sous **Rapports** \> sur la **réduction de la surface d’attaque** **des appareils**\>). Au niveau de l’appareil, sélectionnez **Configuration** dans le volet **Règles de réduction de la surface d’attaque** . L’écran suivant s’affiche, où vous pouvez sélectionner un appareil spécifique et vérifier sa configuration de règle ASR individuelle.

:::image type="content" source="images/asrrulesnew.png" alt-text="Page règles ASR" lightbox="images/asrrulesnew.png":::

## <a name="microsoft-defender-for-endpoint---advanced-hunting"></a>Microsoft Defender pour point de terminaison - Repérage avancé

L’une des fonctionnalités les plus puissantes de Microsoft Defender pour point de terminaison est la chasse avancée. Si vous n’êtes pas familiarisé avec la chasse avancée, reportez-vous [à la chasse proactive pour les menaces avec la chasse avancée](advanced-hunting-overview.md).

La chasse avancée est un outil de chasse aux menaces basé sur une requête (Langage de requête Kusto) qui vous permet d’explorer jusqu’à 30 jours de données capturées (brutes) collectées par Defender pour point de terminaison à partir de vos appareils. Grâce à la chasse avancée, vous pouvez inspecter de manière proactive les événements pour localiser des indicateurs et des entités intéressants. L’accès flexible aux données permet de rechercher sans contrainte les menaces connues et potentielles.

Grâce à la chasse avancée, il est possible d’extraire des informations sur les règles ASR, de créer des rapports et d’obtenir des informations détaillées sur le contexte d’un audit de règle ASR donné ou d’un événement de bloc.

Les événements de règles ASR peuvent être interrogés à partir de la table DeviceEvents dans la section de chasse avancée de l’Microsoft 365 Defender. Par exemple, une requête simple telle que celle ci-dessous peut signaler tous les événements qui ont des règles ASR en tant que source de données, au cours des 30 derniers jours, et les résumera par le nombre d’ActionTypes, que dans ce cas, il s’agit du nom de code réel de la règle ASR.

:::image type="content" source="images/adv-hunt-querynew.png" alt-text="Requête de chasse avancée" lightbox="images/adv-hunt-querynew.png":::

:::image type="content" source="images/adv-hunt-sc-2new.png" alt-text="Page Repérage avancé" lightbox="images/adv-hunt-sc-2new.png":::

Avec la chasse avancée, vous pouvez mettre en forme les requêtes à votre goût, afin que vous puissiez voir ce qui se passe, que vous souhaitiez identifier quelque chose sur un ordinateur individuel ou que vous souhaitiez extraire des insights de l’ensemble de votre environnement.

## <a name="microsoft-defender-for-endpoint-machine-timeline"></a>Microsoft Defender pour point de terminaison chronologie de l’ordinateur

Une alternative à la chasse avancée, mais avec une portée plus étroite, est la chronologie Microsoft Defender pour point de terminaison machine. Vous pouvez afficher tous les événements collectés d’un appareil, au cours des six derniers mois, dans le Microsoft 365 Defender, en accédant à la liste Machines, en sélectionnant un ordinateur donné, puis en cliquant sur l’onglet Chronologie.

Vous trouverez ci-dessous une capture d’écran de la vue Chronologie de ces événements sur un point de terminaison donné. Dans cette vue, vous pouvez filtrer la liste des événements en fonction de l’un des groupes d’événements le long du volet droit. Vous pouvez également activer ou désactiver les événements marqués d’indicateurs et détaillés lors de l’affichage des alertes et du défilement dans la chronologie historique.

:::image type="content" source="images/mic-sec-def-timelinenew.png" alt-text="Chronologie Microsoft 365 Defender" lightbox="images/mic-sec-def-timelinenew.png":::

## <a name="how-to-troubleshoot-asr-rules"></a>Comment résoudre les problèmes liés aux règles ASR ?

La première et la plus immédiate consiste à vérifier localement, sur un appareil Windows, quelles règles ASR sont activées (et leur configuration) consiste à utiliser les applets de commande PowerShell.

Voici quelques autres sources d’informations que Windows propose pour résoudre les problèmes d’impact et d’exploitation des règles ASR.

### <a name="querying-which-rules-are-active"></a>Interrogation des règles actives

L’une des méthodes les plus simples pour déterminer si les règles ASR sont déjà activées consiste à utiliser une applet de commande PowerShell, Get-MpPreference.

Voici un exemple :

:::image type="content" source="images/getmpreferencescriptnew.png" alt-text="Script get mppreference" lightbox="images/getmpreferencescriptnew.png":::

Plusieurs règles ASR sont actives, avec différentes actions configurées.

Pour développer les informations ci-dessus sur les règles ASR, vous pouvez utiliser les propriétés **AttackSurfaceReductionRules_Ids** et/ou **AttackSurfaceReductionRules_Actions**.

Exemple :

```powershell
Get-MPPreference | Select-Object -ExpandProperty**AttackSurfaceReductionRules_Ids
```

:::image type="content" source="images/getmpref-examplenew.png" alt-text="L’exemple get mpreference" lightbox="images/getmpref-examplenew.png":::

Ce qui précède montre tous les ID des règles ASR qui ont un paramètre différent de 0 (non configuré).

L’étape suivante consiste ensuite à répertorier les actions réelles (Bloquer ou Audit) avec lesquelles chaque règle est configurée.

```powershell
Get-MPPreference | Select-Object -ExpandProperty**AttackSurfaceReductionRules_Actions
```

:::image type="content" source="images/getmpref-example2new.png" alt-text="Get mppreference example2" lightbox="images/getmpref-example2new.png":::

### <a name="querying-blocking-and-auditing-events"></a>Interrogation des événements de blocage et d’audit

Les événements de règle ASR peuvent être affichés dans le journal Windows Defender.

Pour y accéder, ouvrez Windows observateur d'événements et accédez aux **journaux Des applications et des** \> services **Microsoft** \> **Windows** \> **Windows Defender** \> **Opérationnel**.

:::image type="content" source="images/eventviewerscrnew.png" alt-text="Page observateur d'événements" lightbox="images/eventviewerscrnew.png":::

## <a name="microsoft-defender-antimalware-protection-logs"></a>journaux de protection anti-programme malveillant Microsoft Defender

Vous pouvez également afficher les événements de règle via l’outil en ligne de commande dédié à l’antivirus Microsoft Defender, appelé `*mpcmdrun.exe*`, qui peut être utilisé pour gérer et configurer, et automatiser les tâches si nécessaire.

Vous trouverez cet utilitaire dans *%ProgramFiles%\Windows Defender\MpCmdRun.exe*. Vous devez l’exécuter à partir d’une invite de commandes avec élévation de privilèges (autrement dit, exécuter en tant que Administration).

Pour générer les informations de support, tapez *MpCmdRun.exe -getfiles*. Après un certain temps, plusieurs journaux d’activité sont empaquetés dans une archive (MpSupportFiles.cab) et mis à disposition dans *C:\ProgramData\Microsoft\Windows Defender\Support*.

:::image type="content" source="images/malware-prot-logsnew.png" alt-text="Journaux de protection contre les programmes malveillants" lightbox="images/malware-prot-logsnew.png":::

Extrayez cette archive et vous disposerez de nombreux fichiers disponibles à des fins de résolution des problèmes.

Les fichiers les plus pertinents sont les suivants :

- **MPOperationalEvents.txt**: ce fichier contient le même niveau d’informations que celui trouvé dans observateur d'événements pour le journal des opérations de Windows Defender.
- **MPRegistry.txt**: dans ce fichier, vous pouvez analyser toutes les configurations Windows Defender actuelles, à partir du moment où les journaux de support ont été capturés.
- **MPLog.txt**: ce journal contient des informations plus détaillées sur toutes les actions/opérations du Windows Defender.
