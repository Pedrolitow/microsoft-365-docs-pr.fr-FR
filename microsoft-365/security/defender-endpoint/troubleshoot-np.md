---
title: Résoudre les problèmes liés à la protection du réseau
description: Ressources et exemple de code pour résoudre les problèmes avec la protection réseau dans Microsoft Defender for Endpoint.
keywords: résoudre les problèmes, erreur, corriger, windows defender eg, asr, rules, hips, troubleshoot, audit, exclusion, false positive, broken, blocking, Microsoft Defender for Endpoint
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: fce2366a155dca3f045497abf2a7a9892180710d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60159317"
---
# <a name="troubleshoot-network-protection"></a>Résoudre les problèmes de protection du réseau

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Cet article fournit des informations de dépannage pour la [protection](network-protection.md)du réseau, dans les cas suivants :

- La protection du réseau bloque un site web sécurisé (faux positif)
- La protection du réseau ne parvient pas à bloquer un site web malveillant suspect ou connu (faux négatif)

La résolution de ces problèmes se fait en quatre étapes :

1. Confirmer les conditions préalables
2. Utiliser le mode audit pour tester la règle
3. Ajouter des exclusions pour la règle spécifiée (pour les faux positifs)
4. Envoyer les journaux de support

## <a name="confirm-prerequisites"></a>Confirmer les conditions préalables

La protection réseau ne fonctionne que sur les appareils qui ont les conditions suivantes :

> [!div class="checklist"]
>
> - Les points de terminaison Windows 10 Professionnel ou Enterprise version 1709 ou supérieure.
> - Les points de terminaison utilisent Antivirus Microsoft Defender comme seule application de protection antivirus. [Découvrez ce qui se produit lorsque vous utilisez une solution antivirus non-Microsoft.](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility)
> - [La protection en temps réel](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) est activée.
> - [La protection cloud](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) est activée.
> - Le mode audit n’est pas activé. Utilisez [la stratégie de](enable-network-protection.md#group-policy) groupe pour définir la règle sur **Désactivé** (valeur : **0**).

## <a name="use-audit-mode"></a>Utiliser le mode Audit

Vous pouvez activer la protection réseau en mode audit, puis visiter un site web que nous avons créé pour rétrograder la fonctionnalité. Toutes les connexions de site web sont autorisées par la protection réseau, mais un événement est enregistré pour indiquer toute connexion qui aurait été bloquée si la protection du réseau était activée.

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

## <a name="add-exclusions"></a>Ajouter des exclusions
Les options d’exclusion actuelles sont :

1.  Configuration d’un indicateur d’autoriser personnalisé.
2.  Utilisation d’exclusions IP : `Add-MpPreference -Exclusion IpAddress 192.168.1.1`
3.  Exclusion d’un processus entier. Pour plus d’informations, [voir Antivirus Microsoft Defender exclusions.](configure-exclusions-microsoft-defender-antivirus.md) 


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

3. Joignez le fichier au formulaire d’envoi. Par défaut, les journaux de diagnostic sont enregistrés sur `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab` .

## <a name="resolve-connectivity-issues-with-network-protection-for-e5-customers"></a>Résoudre les problèmes de connectivité avec la protection réseau (pour les clients E5)

En raison de l’environnement dans lequel la protection réseau s’exécute, Microsoft ne peut pas voir les paramètres de proxy de votre système d’exploitation. Dans certains cas, les clients de protection réseau ne peuvent pas accéder au service cloud. Pour résoudre les problèmes de connectivité avec la protection réseau, configurez l’une des clés de Registre suivantes afin que la protection réseau soit au courant de la configuration du proxy :

```powershell
Set-MpPreference -ProxyServer <proxy IP address: Port>
```

---OR---

```powershell
Set-MpPreference -ProxyPacUrl <Proxy PAC url>
```

Vous pouvez configurer la clé de Registre à l’aide de PowerShell, Microsoft Endpoint Manager ou d’une stratégie de groupe. Voici quelques ressources pour vous aider :

- [Working with Registry Keys](/powershell/scripting/samples/working-with-registry-keys)
- [Configurer les paramètres client personnalisés pour Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure-client)
- [Utiliser les paramètres de stratégie de groupe pour gérer les Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-group-policies)

## <a name="see-also"></a>Voir aussi

- [Protection du réseau](network-protection.md)
- [Protection du réseau et protocole d’auto-transport TCP triple](network-protection.md#network-protection-and-the-tcp-three-way-handshake)
- [Évaluer la protection du réseau](evaluate-network-protection.md)
- [Activer la protection réseau](enable-network-protection.md)
- [Corriger les faux positifs/négatifs dans Defender pour le point de terminaison](defender-endpoint-false-positives-negatives.md)
