---
title: Déployer des mises à jour pour Microsoft Defender pour endpoint sur Mac
description: Contrôler les mises à jour de Microsoft Defender pour Endpoint sur Mac dans les environnements d’entreprise.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, mises à jour, déployer
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 0b9ddf9693a242b3b8c466cfa1616b62c5eb73b9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469292"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-macos"></a>Déployer les mises à jour de Microsoft Defender pour endpoint sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft publie régulièrement des mises à jour logicielles pour améliorer les performances, la sécurité et fournir de nouvelles fonctionnalités.

Pour mettre à jour Microsoft Defender pour endpoint sur macOS, un programme nommé Microsoft AutoUpdate (MAU) est utilisé. Par défaut, MAU recherche automatiquement les mises à jour quotidiennes, mais vous pouvez la modifier de manière hebdomadaire, mensuelle ou manuelle.

:::image type="content" source="images/MDATP-34-MAU.png" alt-text="MAU" lightbox="images/MDATP-34-MAU.png":::

Si vous décidez de déployer des mises à jour à l’aide de vos outils de distribution de logiciels, vous devez configurer MAU pour vérifier manuellement les mises à jour logicielles. Vous pouvez déployer des préférences pour configurer comment et quand MAU recherche les mises à jour pour les Mac dans votre organisation.

## <a name="use-msupdate"></a>Utiliser msupdate

MAU inclut un outil en ligne de commande, appelé *msupdate*, conçu pour les administrateurs informatiques afin qu’ils contrôlent plus précisément le moment où les mises à jour sont appliquées. Vous pouvez trouver des instructions sur l’utilisation de cet outil dans [Update Office pour Mac à l’aide de msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate).

Dans MAU, l’identificateur d’application de Microsoft Defender pour Endpoint sur macOS est *WDAV00*. Pour télécharger et installer les dernières mises à jour de Microsoft Defender pour Endpoint sur macOS, exécutez la commande suivante à partir d’une fenêtre Terminal :

```dos
./msupdate --install --apps wdav00
```

## <a name="set-preferences-for-microsoft-autoupdate"></a>Définir des préférences pour la mise à jour automatique Microsoft

Cette section décrit les préférences les plus courantes qui peuvent être utilisées pour configurer MAU. Ces paramètres peuvent être déployés en tant que profil de configuration via la console de gestion que votre entreprise utilise. Un exemple de profil de configuration est illustré dans les sections suivantes.

### <a name="set-the-channel-name"></a>Définir le nom du canal

Le canal détermine le type et la fréquence des mises à jour proposées via MAU. Les appareils peuvent `Beta` tester de nouvelles fonctionnalités avant d’utiliser `Preview` et `Current`.

Le `Current` canal contient la version la plus stable du produit.

> [!IMPORTANT]
> Avant la mise à jour automatique Microsoft version 4.29, les canaux avaient des noms différents :
>
> - `Beta` a été nommé `InsiderFast` (Insider Fast)
> - `Preview` a été nommé `External` (Insider Slow)
> - `Current` a été nommé `Production`

> [!TIP]
> Pour afficher un aperçu des nouvelles fonctionnalités et fournir des commentaires préliminaires, il est recommandé de configurer certains appareils dans votre entreprise sur `Beta` ou `Preview`.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.autoupdate2`|
|**Clé**|ChannelName|
|**Type de données**|Chaîne|
|**Valeurs possibles**|Bêta <p> Aperçu <p> Current|
|||

> [!WARNING]
> Ce paramètre modifie le canal pour toutes les applications qui sont mises à jour via La mise à jour automatique Microsoft. Pour modifier le canal uniquement pour Microsoft Defender pour le point de terminaison sur macOS, `[channel-name]` exécutez la commande suivante après le remplacement par le canal souhaité :
>
> ```bash
> defaults write com.microsoft.autoupdate2 Applications -dict-add "/Applications/Microsoft Defender.app" " { 'Application ID' = 'WDAV00' ; 'App Domain' = 'com.microsoft.wdav' ; LCID = 1033 ; ChannelName = '[channel-name]' ; }"
> ```

### <a name="set-update-check-frequency"></a>Définir la fréquence de vérification des mises à jour

Modifier la fréquence à la recherche de mises à jour par MAU.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.autoupdate2`|
|**Clé**|UpdateCheckFrequency|
|**Type de données**|Entier|
|**Valeur par défaut**|720 (minutes)|
|**Comment**|Cette valeur est définie en minutes.|
|||

### <a name="change-how-mau-interacts-with-updates"></a>Modifier la façon dont MAU interagit avec les mises à jour

Modifier la façon dont MAU recherche les mises à jour.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.autoupdate2`|
|**Clé**|HowToCheck|
|**Type de données**|Chaîne|
|**Valeurs possibles**|Manual <p> AutomaticCheck <p> AutomaticDownload|
|**Comment**|Notez que AutomaticDownload est téléchargé et installé en mode silencieux si possible.|
|||

### <a name="change-whether-the-check-for-updates-button-is-enabled"></a>Indique si le bouton « Vérifier les mises à jour » est activé.

Indiquez si les utilisateurs locaux pourront cliquer sur l’option « Vérifier les mises à jour » dans l’interface utilisateur Microsoft AutoUpdate.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.autoupdate2`|
|**Clé**|EnableCheckForUpdatesButton|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|True (par défaut) <p> False|
|||

### <a name="disable-insider-checkbox"></a>Désactiver la case à cocher Insider

Définissez la valeur sur True pour que le programme « Rejoindre le programme Office Insider... » case à cocher non disponible/grisée pour les utilisateurs.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.autoupdate2`|
|**Clé**|DisableInsiderCheckbox|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|False (par défaut) <p> Vrai|
|||

### <a name="limit-the-telemetry-that-is-sent-from-mau"></a>Limiter la télémétrie envoyée à partir de MAU

Définissez ce dernier sur False pour envoyer un minimum de données de pulsation, aucune utilisation de l’application et aucun détail sur l’environnement.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.autoupdate2`|
|**Clé**|SendAllTelemetryEnabled|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|True (par défaut) <p> False|
|||

## <a name="example-configuration-profile"></a>Exemple de profil de configuration

Le profil de configuration suivant est utilisé pour :

- Placer l’appareil dans le canal de production
- Télécharger et installer automatiquement les mises à jour
- Activer le bouton « Vérifier les mises à jour » dans l’interface utilisateur
- Autoriser les utilisateurs de l’appareil à s’inscrire aux canaux Insider

> [!WARNING]
> La configuration ci-dessous est un exemple de configuration et ne doit pas être utilisée en production sans une révision appropriée des paramètres et une  adaptation des configurations.

> [!TIP]
> Pour afficher un aperçu des nouvelles fonctionnalités et fournir des commentaires préliminaires, il est recommandé de configurer certains appareils dans votre entreprise sur `Beta` ou `Preview`.

### <a name="jamf"></a>JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>ChannelName</key>
    <string>Production</string>
    <key>HowToCheck</key>
    <string>AutomaticDownload</string>
    <key>EnableCheckForUpdatesButton</key>
    <true/>
    <key>DisableInsiderCheckbox</key>
    <false/>
    <key>SendAllTelemetryEnabled</key>
    <true/>
</dict>
</plist>
```

### <a name="intune"></a>Intune

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>B762FF60-6ACB-4A72-9E72-459D00C936F3</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.autoupdate2</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft AutoUpdate settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft AutoUpdate configuration settings</string>
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
            <string>5A6F350A-CC2C-440B-A074-68E3F34EBAE9</string>
            <key>PayloadType</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadOrganization</key>
            <string>Microsoft</string>
            <key>PayloadIdentifier</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft AutoUpdate configuration settings</string>
            <key>PayloadDescription</key>
            <string/>
            <key>PayloadVersion</key>
            <integer>1</integer>
            <key>PayloadEnabled</key>
            <true/>
            <key>ChannelName</key>
            <string>Production</string>
            <key>HowToCheck</key>
            <string>AutomaticDownload</string>
            <key>EnableCheckForUpdatesButton</key>
            <true/>
            <key>DisableInsiderCheckbox</key>
            <false/>
            <key>SendAllTelemetryEnabled</key>
            <true/>
            </dict>
        </array>
    </dict>
</plist>
```

Pour configurer MAU, vous pouvez déployer ce profil de configuration à partir de l’outil de gestion que votre entreprise utilise :

- À partir de JAMF, téléchargez ce profil de configuration et définissez le domaine de préférence sur *com.microsoft.autoupdate2*.
- À partir d’Intune, téléchargez ce profil de configuration et définissez le nom du profil de configuration personnalisé sur *com.microsoft.autoupdate2*.

## <a name="resources"></a>Ressources

- [Référence msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate)
