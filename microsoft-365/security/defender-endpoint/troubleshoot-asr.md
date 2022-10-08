---
title: Résoudre les problèmes liés aux règles de réduction de la surface d’attaque
description: Ressources et exemple de code pour résoudre les problèmes liés aux règles de réduction de la surface d’attaque dans Microsoft Defender pour point de terminaison.
keywords: dépannage, erreur, correctif, windows defender, par exemple, asr, règles, hanches, résolution des problèmes, audit, exclusion, faux positif, cassé, blocage, Microsoft Defender pour point de terminaison
ms.pagetype: security
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.date: 03/27/2019
ms.reviewer: ''
manager: dansimp
ms.custom: asr
ms.subservice: mde
ms.topic: how-to
ms.collection:
- m365-security
- tier3
search.appverid: met150
ms.openlocfilehash: 134cf426c0e1f38819d68a20fe58bc8f0fd89b90
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68219165"
---
# <a name="troubleshoot-attack-surface-reduction-rules"></a>Résoudre les problèmes liés aux règles de réduction de la surface d’attaque

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Lorsque vous utilisez [des règles de réduction de la surface d’attaque](attack-surface-reduction.md) , vous pouvez rencontrer des problèmes, tels que :

- Une règle bloque un fichier, un processus ou effectue une autre action qu’elle ne doit pas (faux positif)
- Une règle ne fonctionne pas comme décrit ou ne bloque pas un fichier ou un processus qu’elle doit (faux négatif)

Il existe quatre étapes pour résoudre ces problèmes :

1. [Confirmer les prérequis](#confirm-prerequisites)
2. [Utiliser le mode audit pour tester la règle](#use-audit-mode-to-test-the-rule)
3. [Ajouter des exclusions pour la règle spécifiée](#add-exclusions-for-a-false-positive) (pour les faux positifs)
4. [Envoyer les journaux d’activité de support](#collect-diagnostic-data-for-file-submissions)

## <a name="confirm-prerequisites"></a>Confirmer les prérequis

Les règles de réduction de la surface d’attaque fonctionnent uniquement sur les appareils avec les conditions suivantes :

- Les points de terminaison s’exécutent Windows 10 Entreprise, version 1709 (également appelée Fall Creators Update).

- Les points de terminaison utilisent Microsoft Defender Antivirus comme seule application de protection antivirus. [L’utilisation d’une autre application antivirus entraîne la désactivation de Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).

- [La protection en temps réel](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) est activée.

- Le mode Audit n’est pas activé. Utilisez stratégie de groupe pour définir la règle sur **Désactivé** (valeur : **0**), comme décrit dans [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md).

Si ces conditions préalables ont toutes été remplies, passez à l’étape suivante pour tester la règle en mode audit.

## <a name="use-audit-mode-to-test-the-rule"></a>Utiliser le mode audit pour tester la règle

Suivez ces instructions dans [Utiliser l’outil de démonstration pour voir comment fonctionnent les règles de réduction de la surface d’attaque](evaluate-attack-surface-reduction.md) pour tester la règle spécifique avec laquelle vous rencontrez des problèmes.

1. Activez le mode audit pour la règle spécifique que vous souhaitez tester. Utilisez stratégie de groupe pour définir la règle en **mode Audit** (valeur : **2**), comme décrit dans Activer les règles de [réduction de la surface d’attaque](enable-attack-surface-reduction.md). Le mode Audit permet à la règle de signaler le fichier ou le processus, mais elle l’autorise toujours à s’exécuter.

2. Effectuez l’activité à l’origine d’un problème (par exemple, ouvrez ou exécutez le fichier ou le processus qui doit être bloqué, mais qui est autorisé).

3. [Passez en revue les journaux des événements de règle de réduction de la surface d’attaque](attack-surface-reduction.md) pour voir si la règle aurait bloqué le fichier ou le processus si la règle avait été définie sur **Activé**.

Si une règle ne bloque pas un fichier ou un processus que vous attendez doit bloquer, vérifiez d’abord si le mode d’audit est activé.

Le mode Audit a peut-être été activé pour tester une autre fonctionnalité, ou par un script PowerShell automatisé, et n’a peut-être pas été désactivé une fois les tests terminés.

Si vous avez testé la règle avec l’outil de démonstration et le mode audit, et que les règles de réduction de la surface d’attaque fonctionnent sur des scénarios préconfigurés, mais que la règle ne fonctionne pas comme prévu, passez à l’une des sections suivantes en fonction de votre situation :

1. Si la règle de réduction de la surface d’attaque bloque quelque chose qu’elle ne doit pas bloquer (également appelée faux positif), vous pouvez [d’abord ajouter une exclusion de règle de réduction de la surface d’attaque](#add-exclusions-for-a-false-positive).

2. Si la règle de réduction de la surface d’attaque ne bloque pas un élément qu’elle doit bloquer (également appelé faux négatif), vous pouvez passer immédiatement à la dernière étape, [en collectant les données de diagnostic et en nous soumettant le problème](#collect-diagnostic-data-for-file-submissions).

## <a name="add-exclusions-for-a-false-positive"></a>Ajouter des exclusions pour un faux positif

Si la règle de réduction de la surface d’attaque bloque quelque chose qu’elle ne doit pas bloquer (également appelée faux positif), vous pouvez ajouter des exclusions pour empêcher les règles de réduction de la surface d’attaque d’évaluer les fichiers ou dossiers exclus.

Pour ajouter une exclusion, consultez [Personnaliser la réduction de la surface d’attaque](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules).

> [!IMPORTANT]
> Vous pouvez spécifier des fichiers et des dossiers individuels à exclure, mais vous ne pouvez pas spécifier de règles individuelles.
> Cela signifie que tous les fichiers ou dossiers exclus seront exclus de toutes les règles ASR.

## <a name="report-a-false-positive-or-false-negative"></a>Signaler un faux positif ou un faux négatif

Utilisez le [formulaire de soumission web Windows Defender Security Intelligence](https://www.microsoft.com/wdsi/support/report-exploit-guard) pour signaler un faux positif négatif ou faux pour la protection réseau. Avec un abonnement Windows E5, vous pouvez également [fournir un lien vers n’importe quelle alerte associée](alerts-queue.md).

## <a name="collect-diagnostic-data-for-file-submissions"></a>Collecter des données de diagnostic pour les soumissions de fichiers

Lorsque vous signalez un problème avec les règles de réduction de la surface d’attaque, vous êtes invité à collecter et à envoyer des données de diagnostic qui peuvent être utilisées par les équipes de support et d’ingénierie Microsoft pour aider à résoudre les problèmes.

1. Ouvrez une invite de commandes avec élévation de privilèges et accédez au répertoire Windows Defender :

   ```console
   cd "c:\program files\windows defender"
   ```

2. Exécutez cette commande pour générer les journaux de diagnostic :

   ```console
   mpcmdrun -getfiles
   ```

3. Par défaut, ils sont enregistrés dans `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`. Attachez le fichier au formulaire d’envoi.

## <a name="related-articles"></a>Articles connexes

- [Règles de réduction de la surface d’attaque](attack-surface-reduction.md)
- [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)
- [Évaluer les règles de réduction de la surface d’attaque](evaluate-attack-surface-reduction.md)
