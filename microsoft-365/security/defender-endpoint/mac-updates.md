---
title: Déployer des mises à jour pour Microsoft Defender pour point de terminaison sur Mac
description: Contrôler les mises à jour des Microsoft Defender pour point de terminaison sur Mac dans les environnements d’entreprise.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, updates, deploy, catalina, big sur, monterey, ventura, mde pour mac
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 49eaa79e737b9f29202d3cb8e77ff67df55685fe
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68768564"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-macos"></a>Déployer des mises à jour pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft publie régulièrement des mises à jour logicielles pour améliorer les performances, la sécurité et fournir de nouvelles fonctionnalités.

Pour mettre à jour Microsoft Defender pour point de terminaison sur macOS, un programme nommé Microsoft AutoUpdate (MAU) est utilisé. Par défaut, MAU recherche automatiquement les mises à jour quotidiennes, mais vous pouvez la modifier chaque semaine, mensuellement ou manuellement.

:::image type="content" source="images/MDATP-34-MAU.png" alt-text="Mau" lightbox="images/MDATP-34-MAU.png":::

Si vous décidez de déployer des mises à jour à l’aide de vos outils de distribution de logiciels, vous devez configurer MAU pour rechercher manuellement les mises à jour logicielles. Vous pouvez déployer des préférences pour configurer comment et quand MAU recherche les mises à jour pour les Mac de votre organisation.

## <a name="use-msupdate"></a>Utiliser msupdate

MAU inclut un outil en ligne de commande, appelé *msupdate*, conçu pour les administrateurs informatiques afin qu’ils aient un contrôle plus précis sur le moment où les mises à jour sont appliquées. Vous trouverez des instructions sur l’utilisation de cet outil dans [Mettre à jour Office pour Mac à l’aide de msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate).

Dans MAU, l’identificateur d’application pour Microsoft Defender pour point de terminaison sur macOS est *WDAV00*. Pour télécharger et installer les dernières mises à jour pour Microsoft Defender pour point de terminaison sur macOS, exécutez la commande suivante à partir d’une fenêtre de terminal :

```dos
cd /Library/Application\ Support/Microsoft/MAU2.0/Microsoft\ AutoUpdate.app/Contents/MacOS
./msupdate --install --apps wdav00
```

## <a name="set-preferences-for-microsoft-autoupdate"></a>Définir les préférences pour Microsoft AutoUpdate

Cette section décrit les préférences les plus courantes qui peuvent être utilisées pour configurer MAU. Ces paramètres peuvent être déployés en tant que profil de configuration via la console de gestion utilisée par votre entreprise. Un exemple de profil de configuration est présenté dans les sections suivantes.

### <a name="set-the-channel-name"></a>Définir le nom du canal

Le canal détermine le type et la fréquence des mises à jour proposées via MAU. Les appareils dans `Beta` peuvent essayer de nouvelles fonctionnalités avant les appareils dans `Preview` et `Current`.

Le `Current` canal contient la version la plus stable du produit.

> [!IMPORTANT]
> Avant Microsoft AutoUpdate version 4.29, les canaux avaient des noms différents :
>
> - `Beta` a été nommé `InsiderFast` (Insider Fast)
> - `Preview` a été nommé `External` (Insider Slow)
> - `Current` a été nommé `Production`

> [!TIP]
> Pour afficher un aperçu des nouvelles fonctionnalités et fournir des commentaires précoces, il est recommandé de configurer certains appareils de votre entreprise sur `Beta` ou `Preview`.

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
> Ce paramètre modifie le canal de toutes les applications mises à jour via Microsoft AutoUpdate. Pour modifier le canal uniquement pour Microsoft Defender pour point de terminaison sur macOS, exécutez la commande suivante après avoir `[channel-name]` remplacé par le canal souhaité :
>
> ```bash
> defaults write com.microsoft.autoupdate2 Applications -dict-add "/Applications/Microsoft Defender.app" " { 'Application ID' = 'WDAV00' ; 'App Domain' = 'com.microsoft.wdav' ; LCID = 1033 ; ChannelName = '[channel-name]' ; }"
> ```

### <a name="set-update-check-frequency"></a>Définir la fréquence de vérification des mises à jour

Modifier la fréquence à laquelle MAU recherche des mises à jour.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.autoupdate2`|
|**Clé**|UpdateCheckFrequency|
|**Type de données**|Entier|
|**Valeur par défaut**|720 (minutes)|
|**Commentaire**|Cette valeur est définie en minutes.|
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
|**Commentaire**|Notez que AutomaticDownload effectue un téléchargement et s’installe en mode silencieux si possible.|
|||

### <a name="change-whether-the-check-for-updates-button-is-enabled"></a>Modifier si le bouton « Rechercher Mises à jour » est activé

Indiquez si les utilisateurs locaux pourront cliquer sur l’option « Rechercher Mises à jour » dans l’interface utilisateur de Microsoft AutoUpdate.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.autoupdate2`|
|**Clé**|EnableCheckForUpdatesButton|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|True (par défaut) <p> Faux|
|||

### <a name="disable-insider-checkbox"></a>Désactiver la case à cocher Insider

Définissez la valeur true pour définir « Rejoindre le programme Office Insider... » case à cocher non disponible / grisée pour les utilisateurs.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.autoupdate2`|
|**Clé**|DisableInsiderCheckbox|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|False (valeur par défaut) <p> Vrai|
|||

### <a name="limit-the-telemetry-that-is-sent-from-mau"></a>Limiter les données de télémétrie envoyées à partir de MAU

Définissez sur false pour envoyer un minimum de données de pulsation, aucune utilisation de l’application et aucun détail de l’environnement.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.autoupdate2`|
|**Clé**|SendAllTelemetryEnabled|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|True (par défaut) <p> Faux|
|||

## <a name="example-configuration-profile"></a>Exemple de profil de configuration

Le profil de configuration suivant est utilisé pour :

- Placer l’appareil dans le canal de production
- Télécharger et installer automatiquement les mises à jour
- Activer le bouton « Rechercher les mises à jour » dans l’interface utilisateur
- Autoriser les utilisateurs sur l’appareil à s’inscrire dans les canaux Insider

> [!WARNING]
> La configuration ci-dessous est un exemple de configuration et ne doit pas être utilisée en production sans examen approprié des paramètres et adaptation des configurations.

> [!TIP]
> Pour afficher un aperçu des nouvelles fonctionnalités et fournir des commentaires précoces, il est recommandé de configurer certains appareils de votre entreprise sur `Beta` ou `Preview`.

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

- À partir de JAMF, chargez ce profil de configuration et définissez le domaine de préférence *sur com.microsoft.autoupdate2*.
- À partir Intune, chargez ce profil de configuration et définissez le nom du profil de configuration personnalisé *sur com.microsoft.autoupdate2*.

## <a name="resources"></a>Ressources

- [Informations de référence sur msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate)
