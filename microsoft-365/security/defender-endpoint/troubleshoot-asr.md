---
title: Résoudre les problèmes liés aux règles de réduction de la surface d’attaque
description: Ressources et exemple de code pour résoudre les problèmes avec les règles de réduction de la surface d’attaque dans Microsoft Defender for Endpoint.
keywords: résoudre les problèmes, erreur, corriger, windows defender eg, asr, rules, hips, troubleshoot, audit, exclusion, false positive, broken, blocking, Microsoft Defender for Endpoint
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.date: 03/27/2019
ms.reviewer: ''
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: how-to
ms.openlocfilehash: c5c76553ff3f0b32def5fbafbf2c8f010e49eeb2
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52845419"
---
# <a name="troubleshoot-attack-surface-reduction-rules"></a>Résoudre les problèmes de règles de réduction de la surface d’attaque

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 


Lorsque vous utilisez des [règles de réduction de la surface](attack-surface-reduction.md) d’attaque, vous pouvez être face à des problèmes, tels que :

- Une règle bloque un fichier, un processus ou effectue une autre action qu’elle ne devrait pas (faux positif)

- Une règle ne fonctionne pas comme décrit, ou ne bloque pas un fichier ou un processus qu’elle doit (faux négatifs)

La résolution de ces problèmes se fait en quatre étapes :

1. [Confirmer les conditions préalables](#confirm-prerequisites)

2. [Utiliser le mode audit pour tester la règle](#use-audit-mode-to-test-the-rule)

3. [Ajouter des exclusions pour la règle spécifiée](#add-exclusions-for-a-false-positive) (pour les faux positifs)

4. [Envoyer les journaux de support](#collect-diagnostic-data-for-file-submissions)

## <a name="confirm-prerequisites"></a>Confirmer les conditions préalables

Les règles de réduction de la surface d’attaque fonctionnent uniquement sur les appareils qui ont les conditions suivantes :

- Les points de terminaison Windows 10 Entreprise, version 1709 (également appelée Fall Creators Update).

- Les points de terminaison utilisent Antivirus Microsoft Defender comme seule application de protection antivirus. [L’utilisation d’une autre application antivirus entraîne la désactivation](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility)de Microsoft Defender AV.

- [La protection en temps réel](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) est activée.

- Le mode audit n’est pas activé. Utilisez la stratégie de groupe pour définir la règle sur **Désactivé** (valeur : **0**) comme décrit dans Activer les règles de réduction [de la surface d’attaque.](enable-attack-surface-reduction.md)

Si ces conditions préalables ont toutes été remplies, procédez à l’étape suivante pour tester la règle en mode audit.

## <a name="use-audit-mode-to-test-the-rule"></a>Utiliser le mode audit pour tester la règle

Vous pouvez consulter le site web de base de test Windows Defender à [l’adresse demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que les règles de réduction de la surface d’attaque fonctionnent généralement pour les scénarios et processus pré-configurés sur un appareil, ou vous pouvez utiliser le mode audit, qui permet aux règles de signaler uniquement.

Suivez ces instructions dans l’outil de démonstration pour voir comment fonctionnent les règles de réduction de [la surface](evaluate-attack-surface-reduction.md) d’attaque afin de tester la règle spécifique avec qui vous rencontrez des problèmes.

1. Activez le mode audit pour la règle spécifique que vous souhaitez tester. Utilisez la stratégie de groupe pour définir la règle sur **le mode Audit** (valeur : **2**), comme décrit dans activer les règles de réduction [de la surface d’attaque.](enable-attack-surface-reduction.md) Le mode audit permet à la règle de signaler le fichier ou le processus, tout en lui permettant de s’exécuter.

2. Effectuez l’activité à l’origine d’un problème (par exemple, ouvrir ou exécuter le fichier ou le processus qui doit être bloqué mais qui est autorisé).

3. [Consultez les journaux](attack-surface-reduction.md) des événements de règle de réduction de la surface d’attaque pour voir si la règle aurait bloqué le fichier ou le processus si la règle avait été définie sur **Activé.**

Si une règle ne bloque pas un fichier ou un processus que vous attendez qu’il bloque, vérifiez d’abord si le mode audit est activé.

Le mode audit a peut-être été activé pour tester une autre fonctionnalité, ou par un script PowerShell automatisé, et n’a peut-être pas été désactivé une fois les tests terminés.

Si vous avez testé la règle avec l’outil de démonstration et avec le mode audit, et que les règles de réduction de la surface d’attaque fonctionnent sur des scénarios pré-configurés, mais que la règle ne fonctionne pas comme prévu, vous devez passer à l’une des sections suivantes en fonction de votre situation :

1. Si la règle de réduction de la surface d’attaque bloque quelque chose qu’elle ne doit pas bloquer (également appelé faux positif), vous pouvez d’abord ajouter une exclusion de règle de réduction de la [surface d’attaque.](#add-exclusions-for-a-false-positive)

2. Si la règle de réduction de la surface d’attaque ne bloque pas quelque chose qu’elle doit bloquer (également appelé faux négatif), vous pouvez passer immédiatement à la dernière étape, en collectant des données de [diagnostic](#collect-diagnostic-data-for-file-submissions)et en nous envoyant le problème.

## <a name="add-exclusions-for-a-false-positive"></a>Ajouter des exclusions pour un faux positif

Si la règle de réduction de la surface d’attaque bloque quelque chose qu’elle ne doit pas bloquer (également appelé faux positif), vous pouvez ajouter des exclusions pour empêcher les règles de réduction de la surface d’attaque d’évaluer les fichiers ou dossiers exclus.

Pour ajouter une exclusion, voir [Personnaliser la réduction de la surface d’attaque.](customize-attack-surface-reduction.md)

>[!IMPORTANT]
>Vous pouvez spécifier des fichiers et dossiers individuels à exclure, mais vous ne pouvez pas spécifier des règles individuelles.
>Cela signifie que tous les fichiers ou dossiers exclus seront exclus de toutes les règles de la asr.

## <a name="report-a-false-positive-or-false-negative"></a>Signaler un faux positif ou un faux négatif

Utilisez le Windows Defender d’envoi [web Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) pour signaler un faux négatif ou un faux positif pour la protection du réseau. Avec un abonnement Windows E5, vous pouvez également fournir un lien vers [n’importe quelle alerte associée.](alerts-queue.md)

## <a name="collect-diagnostic-data-for-file-submissions"></a>Collecter des données de diagnostic pour les soumissions de fichiers

Lorsque vous signalez un problème avec les règles de réduction de la surface d’attaque, vous êtes invité à collecter et soumettre des données de diagnostic qui peuvent être utilisées par le support microsoft et les équipes d’ingénierie pour vous aider à résoudre les problèmes.

1. Ouvrez une invite de commandes avec élévation de élévation de Windows Defender répertoire :

   ```console
   cd "c:\program files\windows defender"
   ```

2. Exécutez cette commande pour générer les journaux de diagnostic :

   ```console
   mpcmdrun -getfiles
   ```

3. Par défaut, ils sont enregistrés dans `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab` . Joignez le fichier au formulaire d’envoi.

## <a name="related-articles"></a>Articles connexes

- [Règles de réduction de la surface d’attaque](attack-surface-reduction.md)

- [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)

- [Évaluer les règles de réduction de la surface d’attaque](evaluate-attack-surface-reduction.md)
