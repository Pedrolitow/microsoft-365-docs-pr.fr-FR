---
title: Résoudre les problèmes liés à la protection du réseau
description: Ressources et exemple de code pour résoudre les problèmes avec la protection réseau dans Microsoft Defender for Endpoint.
keywords: résoudre les problèmes, erreur, corriger, windows defender eg, asr, rules, hips, troubleshoot, audit, exclusion, false positive, broken, blocking, microsoft defender for endpoint, microsoft defender advanced threat protection
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
author: dansimp
ms.author: dansimp
ms.date: 01/26/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 165c17bc820403ebfbbe5cdfe3ca856e8416c593
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51066041"
---
# <a name="troubleshoot-network-protection"></a>Résoudre les problèmes de protection du réseau

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 


Lorsque vous utilisez [la protection réseau,](network-protection.md) vous pouvez rencontrer des problèmes, tels que :

- La protection du réseau bloque un site web sécurisé (faux positif)
- La protection du réseau ne parvient pas à bloquer un site web malveillant suspect ou connu (faux négatif)

La résolution de ces problèmes se fait en quatre étapes :

1. Confirmer les conditions préalables
2. Utiliser le mode audit pour tester la règle
3. Ajouter des exclusions pour la règle spécifiée (pour les faux positifs)
4. Envoyer les journaux de support

## <a name="confirm-prerequisites"></a>Confirmer les conditions préalables

La protection réseau ne fonctionne que sur les appareils qui ont les conditions suivantes :

>[!div class="checklist"]
> - Les points de terminaison exécutent Windows 10 Professionnel ou Entreprise, version 1709 ou supérieure.
> - Les points de terminaison utilisent l’Antivirus Microsoft Defender comme seule application de protection antivirus. [Découvrez ce qui se produit lorsque vous utilisez une solution antivirus non-Microsoft.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility)
> - [La protection en temps réel](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) est activée.
> - [La protection cloud](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) est activée.
> - Le mode audit n’est pas activé. Utilisez [la stratégie de](enable-network-protection.md#group-policy) groupe pour définir la règle sur **Désactivé** (valeur : **0**).

## <a name="use-audit-mode"></a>Utiliser le mode audit

Vous pouvez activer la protection réseau en mode audit, puis visiter un site web que nous avons créé pour faire une démonstration de la fonctionnalité. Toutes les connexions de site web sont autorisées par la protection réseau, mais un événement est enregistré pour indiquer toute connexion qui aurait été bloquée si la protection du réseau était activée.

1. Définissez la protection réseau sur **le mode Audit.**

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

2. Effectuez l’activité de connexion à l’origine d’un problème (par exemple, essayez de visiter le site ou de vous connecter à l’adresse IP que vous bloquez ou ne voulez pas bloquer).

3. [Consultez les journaux des événements](network-protection.md#review-network-protection-events-in-windows-event-viewer) de protection réseau pour voir si la fonctionnalité aurait bloqué la connexion si elle avait été définie **sur Activé.**
   
   Si la protection réseau ne bloque pas une connexion que vous attendez qu’elle bloque, activez la fonctionnalité.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

## <a name="report-a-false-positive-or-false-negative"></a>Signaler un faux positif ou un faux négatif

Si vous avez testé la fonctionnalité avec le site de démonstration et le mode audit, et que la protection du réseau fonctionne sur des scénarios pré-configurés, mais ne fonctionne pas comme prévu pour une connexion spécifique, utilisez le formulaire d’envoi [web Windows Defender Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) pour signaler un faux négatif ou un faux positif pour la protection du réseau. Avec un abonnement E5, vous pouvez également fournir un [lien vers n’importe quelle alerte associée.](alerts-queue.md)

Voir [Adresse faux positifs/négatifs dans Microsoft Defender pour le point de terminaison.](defender-endpoint-false-positives-negatives.md)

## <a name="exclude-website-from-network-protection-scope"></a>Exclure le site web de l’étendue de protection réseau

Pour autoriser le site web bloqué (faux positif), ajoutez son URL à la [liste des sites de confiance.](https://blogs.msdn.microsoft.com/asiatech/2014/08/19/how-to-add-web-sites-to-trusted-sites-via-gpo-from-dc-installed-ie10-or-higher-ie-version/) Les ressources Web de cette liste contournent la vérification de la protection réseau.

## <a name="collect-diagnostic-data-for-file-submissions"></a>Collecter des données de diagnostic pour les soumissions de fichiers

Lorsque vous signalez un problème avec la protection du réseau, vous êtes invité à collecter et à envoyer des données de diagnostic qui peuvent être utilisées par le support microsoft et les équipes d’ingénierie pour vous aider à résoudre les problèmes.

1. Ouvrez une invite de commandes avec élévation de élévation de Windows Defender répertoire :

   ```console
   cd c:\program files\windows defender
   ```

2. Exécutez cette commande pour générer les journaux de diagnostic :

   ```console
   mpcmdrun -getfiles
   ```

3. Par défaut, ils sont enregistrés dans C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab. Joignez le fichier au formulaire d’envoi.

## <a name="related-topics"></a>Voir aussi

- [Protection du réseau](network-protection.md)
- [Évaluer la protection du réseau](evaluate-network-protection.md)
- [Activer la protection du réseau](enable-network-protection.md)
- [Corriger les faux positifs/négatifs dans Defender pour le point de terminaison](defender-endpoint-false-positives-negatives.md)
