---
title: Résoudre les problèmes liés à la protection réseau
description: Ressources et exemple de code pour résoudre les problèmes liés à la protection réseau dans Microsoft Defender pour point de terminaison.
keywords: dépannage, erreur, correctif, windows defender, par exemple, asr, règles, hanches, résolution des problèmes, audit, exclusion, faux positif, cassé, blocage, Microsoft Defender pour point de terminaison
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde
manager: dansimp
ms.subservice: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 6b901bf480bda34318042cefb2f8edc8b1f920fb
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67579906"
---
# <a name="troubleshoot-network-protection"></a>Résoudre les problèmes de protection réseau

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Cet article fournit des informations de dépannage pour la [protection réseau](network-protection.md), dans les cas suivants :

- La protection réseau bloque un site web sécurisé (faux positif)
- La protection réseau ne parvient pas à bloquer un site web malveillant suspect ou connu (faux négatif)

Il existe quatre étapes pour résoudre ces problèmes :

1. Confirmer les prérequis
2. Utiliser le mode audit pour tester la règle
3. Ajouter des exclusions pour la règle spécifiée (pour les faux positifs)
4. Envoyer les journaux d’activité de support

## <a name="confirm-prerequisites"></a>Confirmer les prérequis

La protection réseau fonctionne uniquement sur les appareils avec les conditions suivantes :

> [!div class="checklist"]
>
> - Les points de terminaison exécutent Windows 10 Professionnel ou l’édition Enterprise, version 1709 ou ultérieure.
> - Les points de terminaison utilisent l’Antivirus Microsoft Defender comme seule application de protection antivirus. [Découvrez ce qui se passe lorsque vous utilisez une solution antivirus non Microsoft](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).
> - [La protection en temps réel](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) est activée.
> - [La protection fournie par le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) est activée.
> - Le mode Audit n’est pas activé. Utilisez [stratégie de groupe](enable-network-protection.md#group-policy) pour définir la règle sur **Désactivé** (valeur : **0**).

## <a name="use-audit-mode"></a>Utiliser le mode Audit

Vous pouvez activer la protection réseau en mode audit, puis visiter un site web que nous avons créé pour faire la démonstration de la fonctionnalité. Toutes les connexions au site web sont autorisées par la protection réseau, mais un événement est enregistré pour indiquer toute connexion qui aurait été bloquée si la protection réseau était activée.

1. Définissez la protection réseau sur **le mode Audit**.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

2. Effectuez l’activité de connexion à l’origine d’un problème (par exemple, tentez de visiter le site, ou connectez-vous à l’adresse IP que vous voulez bloquer ou que vous ne voulez pas bloquer).

3. [Passez en revue les journaux des événements de protection réseau](network-protection.md#review-network-protection-events-in-windows-event-viewer) pour voir si la fonctionnalité aurait bloqué la connexion si elle avait été définie sur **Activé**.

   Si la protection réseau ne bloque pas une connexion que vous attendez qu’elle bloque, activez la fonctionnalité.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

## <a name="report-a-false-positive-or-false-negative"></a>Signaler un faux positif ou un faux négatif

Si vous avez testé la fonctionnalité avec le site de démonstration et le mode d’audit, et que la protection réseau fonctionne sur des scénarios préconfigurés, mais qu’elle ne fonctionne pas comme prévu pour une connexion spécifique, utilisez le [formulaire de soumission web Windows Defender Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) pour signaler un faux positif négatif ou faux pour la protection réseau. Avec un abonnement E5, vous pouvez également [fournir un lien vers n’importe quelle alerte associée](alerts-queue.md).

Voir [Adresse des faux positifs/négatifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md).

## <a name="add-exclusions"></a>Ajouter des exclusions

Les options d’exclusion actuelles sont les suivantes :

1. Configuration d’un indicateur d’autorisation personnalisé.
2. Utilisation d’exclusions IP : `Add-MpPreference -ExclusionIpAddress 192.168.1.1`
3. À l’exclusion d’un processus entier. Pour plus d’informations, consultez [les exclusions de l’Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md). 

## <a name="collect-diagnostic-data-for-file-submissions"></a>Collecter des données de diagnostic pour les soumissions de fichiers

Lorsque vous signalez un problème avec la protection réseau, vous êtes invité à collecter et à envoyer des données de diagnostic qui peuvent être utilisées par les équipes de support et d’ingénierie Microsoft pour aider à résoudre les problèmes.

1. Ouvrez une invite de commandes avec élévation de privilèges et accédez au répertoire Windows Defender :

   ```console
   cd c:\program files\windows defender
   ```

2. Exécutez cette commande pour générer les journaux de diagnostic :

   ```console
   mpcmdrun -getfiles
   ```

3. Attachez le fichier au formulaire d’envoi. Par défaut, les journaux de diagnostic sont enregistrés à l’adresse `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

## <a name="resolve-connectivity-issues-with-network-protection-for-e5-customers"></a>Résoudre les problèmes de connectivité avec la protection réseau (pour les clients E5)

En raison de l’environnement dans lequel la protection réseau s’exécute, Microsoft ne peut pas voir les paramètres de proxy de votre système d’exploitation. Dans certains cas, les clients de protection réseau ne peuvent pas atteindre le service cloud. Pour résoudre les problèmes de connectivité liés à la protection réseau, configurez l’une des clés de Registre suivantes afin que la protection réseau prenne conscience de la configuration du proxy :

```powershell
Set-MpPreference -ProxyServer <proxy IP address: Port>
```

---OR---

```powershell
Set-MpPreference -ProxyPacUrl <Proxy PAC url>
```

Vous pouvez configurer la clé de Registre à l’aide de PowerShell, microsoft Endpoint Manager ou stratégie de groupe. Voici quelques ressources pour vous aider :

- [Utilisation des clés de Registre](/powershell/scripting/samples/working-with-registry-keys)
- [Configurer les paramètres client personnalisés pour Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure-client)
- [Utiliser stratégie de groupe paramètres pour gérer Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-group-policies)

## <a name="see-also"></a>Voir aussi

- [Protection du réseau](network-protection.md)
- [Protection réseau et liaison TCP triple](network-protection.md#network-protection-and-the-tcp-three-way-handshake)
- [Évaluer la protection du réseau](evaluate-network-protection.md)
- [Activer la protection réseau](enable-network-protection.md)
- [Résoudre les faux positifs/négatifs dans Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)
