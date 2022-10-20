---
title: Protéger les paramètres de sécurité macOS avec la protection contre les falsifications
description: Utilisez la protection contre les falsifications pour empêcher les applications malveillantes de modifier les paramètres de sécurité macOS importants.
keywords: macos, protection contre les falsifications, paramètres de sécurité, programmes malveillants
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 115b1159bb425688fe808652ab7e2b61170f3f8e
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68637483"
---
# <a name="protect-macos-security-settings-with-tamper-protection"></a>Protéger les paramètres de sécurité macOS avec la protection contre les falsifications

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-rbac-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]


La protection contre les falsifications dans macOS permet d’empêcher les modifications indésirables apportées aux paramètres de sécurité par des utilisateurs non autorisés. La protection contre les falsifications permet d’empêcher la suppression non autorisée de Microsoft Defender pour point de terminaison sur macOS. Cette fonctionnalité permet également aux fichiers de sécurité, aux processus et aux paramètres de configuration importants d’être falsifiés.

Vous pouvez définir la protection contre les falsifications dans les modes suivants :

|Rubrique|Description|
|---|---|
|Désactivé|La protection contre les falsifications est complètement désactivée (il s’agit du mode par défaut après l’installation)|
|Audit|Les opérations de falsification sont journalisées, mais pas bloquées|
|Bloquer|La protection contre les falsifications est activée, les opérations de falsification sont bloquées|

Lorsque la protection contre les falsifications est définie sur le mode audit ou bloquer, vous pouvez vous attendre aux résultats suivants :

**Mode Audit** :

- Les actions pour désinstaller Defender pour l’agent de point de terminaison sont journalisées (auditées)
- La modification/modification des fichiers Defender pour point de terminaison est enregistrée (auditée)
- La création de nouveaux fichiers sous l’emplacement defender pour point de terminaison est enregistrée (auditée)
- La suppression des fichiers Defender pour point de terminaison est journalisée (auditée)
- Le changement de nom des fichiers Defender pour point de terminaison est enregistré (audité)

**Mode bloc** :

- Les actions de désinstallation de l’agent Defender pour point de terminaison sont bloquées
- La modification/modification des fichiers Defender pour point de terminaison est bloquée
- La création de nouveaux fichiers sous l’emplacement de Defender pour point de terminaison est bloquée
- La suppression des fichiers Defender pour point de terminaison est bloquée
- Le changement de nom des fichiers Defender pour point de terminaison est bloqué
- Les commandes pour arrêter l’agent échouent

Voici un exemple de message système en réponse à une action bloquée :

![Image de l’opération bloquée](images/operation-blocked.png)

Vous pouvez configurer le mode de protection contre les falsifications en fournissant le nom du mode au niveau de l’application.

> [!NOTE]
>
> - La modification du mode s’applique immédiatement.
> - Si vous avez utilisé JAMF pendant la configuration initiale, vous devez également mettre à jour la configuration à l’aide de JAMF.

## <a name="before-you-begin"></a>Avant de commencer

- Versions macOS prises en charge : Monterey (12), Big Sur (11), Catalina (10.15+).
- Version minimale requise pour Defender pour point de terminaison : 101.70.19.

**Paramètres fortement recommandés :**

- Protection de l’intégrité du système (SIP) activée. Pour plus d’informations, consultez [Désactivation et activation de la protection de l’intégrité du système](https://developer.apple.com/documentation/security/disabling_and_enabling_system_integrity_protection).
- Utilisez un outil de gestion des appareils mobiles (GPM) pour configurer Microsoft Defender pour point de terminaison.

## <a name="configure-tamper-protection-on-macos-devices"></a>Configurer la protection contre les falsifications sur les appareils macOS

Il existe plusieurs façons de configurer la protection contre les falsifications :

- [Configuration manuelle](#manual-configuration)
- [JAMF](#jamf)
- [Intune](#intune)

### <a name="before-you-begin"></a>Avant de commencer

Vérifiez que « tamper_protection » est défini sur « désactivé » ou « audit » pour observer le changement d’état.
Assurez-vous également que « release_ring » ne signale pas « Production ».

```bash
mdatp health
```

```console
healthy                                     : true
health_issues                               : []
licensed                                    : true
engine_version                              : "1.1.19300.3"
app_version                                 : "101.70.19"
org_id                                      : "..."
log_level                                   : "info"
machine_guid                                : "..."
release_ring                                : "InsiderFast"
product_expiration                          : Dec 29, 2022 at 09:48:37 PM
cloud_enabled                               : true
cloud_automatic_sample_submission_consent   : "safe"
cloud_diagnostic_enabled                    : false
passive_mode_enabled                        : false
real_time_protection_enabled                : true
real_time_protection_available              : true
real_time_protection_subsystem              : "endpoint_security_extension"
network_events_subsystem                    : "network_filter_extension"
device_control_enforcement_level            : "audit"
tamper_protection                           : "audit"
automatic_definition_update_enabled         : true
definitions_updated                         : Jul 06, 2022 at 01:57:03 PM
definitions_updated_minutes_ago             : 5
definitions_version                         : "1.369.896.0"
definitions_status                          : "up_to_date"
edr_early_preview_enabled                   : "disabled"
edr_device_tags                             : []
edr_group_ids                               : ""
edr_configuration_version                   : "20.199999.main.2022.07.05.02-ac10b0623fd381e28133debe14b39bb2dc5b61af"
edr_machine_id                              : "..."
conflicting_applications                    : []
network_protection_status                   : "stopped"
data_loss_prevention_status                 : "disabled"
full_disk_access_enabled                    : true
```

### <a name="manual-configuration"></a>Configuration manuelle

1. Utilisez la commande suivante :

   ```console
   sudo mdatp config tamper-protection enforcement-level --value block
   ```

   ![Image de la commande de configuration manuelle](images/manual-config-cmd.png)

   > [!NOTE]
   > Si vous utilisez la configuration manuelle pour activer la protection contre les falsifications, vous pouvez également désactiver la protection contre les falsifications manuellement à tout moment. Par exemple, vous pouvez révoquer manuellement l’accès au disque complet de Defender dans préférences système. Vous devez utiliser MDM au lieu d’une configuration manuelle pour empêcher un administrateur local de le faire.

2. Vérifiez le résultat.

  ```bash
  mdatp health
  ```

  ```console
  healthy                                     : true
  health_issues                               : []
  licensed                                    : true
  engine_version                              : "1.1.19300.3"
  app_version                                 : "101.70.19"
  org_id                                      : "..."
  log_level                                   : "info"
  machine_guid                                : "..."
  release_ring                                : "InsiderFast"
  product_expiration                          : Dec 29, 2022 at 09:48:37 PM
  cloud_enabled                               : true
  cloud_automatic_sample_submission_consent   : "safe"
  cloud_diagnostic_enabled                    : false
  passive_mode_enabled                        : false
  real_time_protection_enabled                : true
  real_time_protection_available              : true
  real_time_protection_subsystem              : "endpoint_security_extension"
  network_events_subsystem                    : "network_filter_extension"
  device_control_enforcement_level            : "audit"
  tamper_protection                           : "block"
  automatic_definition_update_enabled         : true
  definitions_updated                         : Jul 06, 2022 at 01:57:03 PM
  definitions_updated_minutes_ago             : 5
  definitions_version                         : "1.369.896.0"
  definitions_status                          : "up_to_date"
  edr_early_preview_enabled                   : "disabled"
  edr_device_tags                             : []
  edr_group_ids                               : ""
  edr_configuration_version                   : "20.199999.main.2022.07.05.02-ac10b0623fd381e28133debe14b39bb2dc5b61af"
  edr_machine_id                              : "..."
  conflicting_applications                    : []
  network_protection_status                   : "stopped"
  data_loss_prevention_status                 : "disabled"
  full_disk_access_enabled                    : true
  ```

Notez que « tamper_protection » est maintenant défini sur « block ».

### <a name="jamf"></a>JAMF

Configurez le mode de protection contre les falsifications dans Microsoft Defender pour point de terminaison [profil de configuration](mac-jamfpro-policies.md), en ajoutant les paramètres suivants :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>tamperProtection</key>
    <dict>
      <key>enforcementLevel</key>
      <string>block</string>
    </dict>
  </dict>
</plist>
```

> [!NOTE]
> Si vous disposez déjà d’un profil de configuration pour Microsoft Defender pour point de terminaison vous devez *y ajouter* des paramètres. Vous n’avez pas besoin de créer un deuxième profil de configuration.

### <a name="intune"></a>Intune

Suivez l’exemple de profil Intune documenté pour configurer la protection contre les falsifications via Intune. Pour plus d’informations, consultez [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md).

Ajoutez la configuration suivante dans votre profil Intune :

> [!NOTE]
> Pour Intune configuration, vous pouvez créer un fichier de configuration de profil pour ajouter la configuration de protection contre les falsifications, ou ajouter ces paramètres à celui existant.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>tamperProtection</key>
                <dict>
                             <key>enforcementLevel</key>
                             <string>block</string>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

Vérifiez l’état de la protection contre les falsifications en exécutant la commande suivante :

`mdatp health --field tamper_protection`

Le résultat affiche « block » si la protection contre les falsifications est activée :

![Image de la protection contre les falsifications en mode bloc](images/tp-block-mode.png)

Vous pouvez également exécuter l’exécution complète `mdatp health` et rechercher le « tamper_protection » dans la sortie

## <a name="verify-tamper-protection-preventive-capabilities"></a>Vérifier les fonctionnalités préventives de protection contre les falsifications

Vous pouvez vérifier que la protection contre les falsifications est activée de différentes manières.

### <a name="verify-block-mode"></a>Vérifier le mode bloc

L’alerte de falsification est déclenchée dans le portail Microsoft 365 Defender

![Image de l’alerte de falsification déclenchée dans le portail Microsoft 365 Defender](images/tampering-sensor-portal.png)

### <a name="verify-block-mode-and-audit-modes"></a>Vérifier le mode bloc et les modes d’audit

- À l’aide de la chasse avancée, vous verrez apparaître des alertes de falsification
- Les événements de falsification se trouvent dans les journaux d’activité des appareils locaux : `sudo grep -F '[{tamperProtection}]' /Library/Logs/Microsoft/mdatp/microsoft_defender_core.log`

![Image du journal de protection contre les falsifications](images/tamper-protection-log.png)

### <a name="diy-scenarios"></a>Scénarios de diy

- Avec la protection contre les falsifications définie sur « block », essayez différentes méthodes pour désinstaller Defender pour point de terminaison. Par exemple, faites glisser la vignette de l’application dans la corbeille ou désinstallez la protection contre les falsifications à l’aide de la ligne de commande.
- Essayez d’arrêter le processus Defender pour point de terminaison (kill).
- Essayez de supprimer, renommer, modifier, déplacer des fichiers Defender pour point de terminaison (semblables à ce qu’un utilisateur malveillant ferait), par exemple :

  - /Applications/Microsoft Defender ATP.app/
  - /Library/LaunchDaemons/com.microsoft.fresno.plist
  - /Library/LaunchDaemons/com.microsoft.fresno.uninstall.plist
  - /Library/LaunchAgents/com.microsoft.wdav.tray.plist
  - /Library/Managed Preferences/com.microsoft.wdav.ext.plist
  - /Library/Managed Preferences/mdatp_managed.json
  - /Library/Managed Preferences/com.microsoft.wdav.atp.plist
  - /Library/Managed Preferences/com.microsoft.wdav.atp.offboarding.plist
  - /usr/local/bin/mdatp

## <a name="turning-off-tamper-protection"></a>Désactivation de la protection contre les falsifications

Vous pouvez désactiver la protection contre les falsifications à l’aide de l’une des méthodes suivantes.

### <a name="manual-configuration"></a>Configuration manuelle

Utilisez la commande suivante :

```console
sudo mdatp config tamper-protection enforcement-level - -value disabled
```

## <a name="jamf"></a>JAMF
Remplacez la `enforcementLevel` valeur par « désactivée » dans votre profil de configuration et envoyez-la à l’ordinateur :

```console
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>tamperProtection</key>
    <dict>
      <key>enforcementLevel</key>
      <string>disabled</string>
    </dict>
  </dict>
</plist>

```

### <a name="intune"></a>Intune
Ajoutez la configuration suivante dans votre profil Intune :

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>tamperProtection</key>
                <dict>
                             <key>enforcementLevel</key>
                             <string>disabled</string>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="troubleshooting-configuration-issues"></a>Résolution des problèmes de configuration

### <a name="issue-tamper-protection-is-reported-as-disabled"></a>Problème : La protection contre les falsifications est signalée comme désactivée

Si l’exécution de la commande `mdatp health` indique que la protection contre les falsifications est désactivée, même si vous l’avez activée et que plus d’une heure s’est écoulée depuis l’intégration, vous pouvez vérifier si vous disposez de la configuration appropriée en exécutant la commande suivante :

```console
$ sudo grep -F '\[{tamperProtection}\]: Feature state:' /Library/Logs/Microsoft/mdatp/microsoft_defender_core.log | tail -n 1


```

Le mode doit être « block » (ou « audit »). Si ce n’est pas le cas, vous n’avez pas défini le mode de protection contre les falsifications par le biais de `mdatp config` la commande ou de Intune.
