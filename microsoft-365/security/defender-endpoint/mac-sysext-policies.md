---
title: Nouveaux profils de configuration pour macOS Catalina et les versions plus récentes de macOS
description: Cette rubrique décrit les modifications qui doivent être apportées pour tirer parti des extensions système, qui remplacent les extensions de noyau sur macOS Catalina et les versions plus récentes de macOS.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, noyau, système, extensions, catalina, big sur, monterey, ventura, mde pour mac
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: security
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
ROBOTS: noindex,nofollow
ms.subservice: mde
ms.openlocfilehash: 3ecd935bfbbd6f37d6803409e7ee8336ca25381f
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68770050"
---
# <a name="new-configuration-profiles-for-macos-catalina-and-newer-versions-of-macos"></a>Nouveaux profils de configuration pour macOS Catalina et les versions plus récentes de macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Si vous avez déployé Microsoft Defender pour point de terminaison sur macOS dans un environnement managé (via JAMF, Intune ou une autre solution GPM), vous devez déployer de nouveaux profils de configuration. Si vous n’effectuez pas ces étapes, les utilisateurs reçoivent des invites d’approbation pour exécuter ces nouveaux composants.

## <a name="jamf"></a>JAMF

### <a name="jamf-system-extensions-policy"></a>Stratégie d’extensions système JAMF

Pour approuver les extensions système, créez la charge utile suivante :

1. Dans **Ordinateurs > Profils de configuration** , sélectionnez **Options > Extensions système**.
2. Sélectionnez **Extensions système autorisées** dans la liste déroulante **Types d’extension système** .
3. Utilisez **UBF8T346G9** pour l’ID d’équipe.
4. Ajoutez les identificateurs de bundle suivants à la liste **Extensions système autorisées** :

    - **com.microsoft.wdav.epsext**
    - **com.microsoft.wdav.netext**

    :::image type="content" source="images/mac-approved-system-extensions.png" alt-text=" Page Extensions système approuvées" lightbox="images/mac-approved-system-extensions.png":::

### <a name="privacy-preferences-policy-control"></a>Contrôle de la stratégie des préférences de confidentialité

Ajoutez la charge utile JAMF suivante pour accorder un accès disque complet à l’extension de sécurité de point de terminaison Microsoft Defender pour point de terminaison. Cette stratégie est une condition préalable à l’exécution de l’extension sur votre appareil.

1. Sélectionnez **Options Préférences** \> **de confidentialité Contrôle de stratégie**.
2. Utilisez `com.microsoft.wdav.epsext` comme **identificateur** et `Bundle ID` comme **type d’offre groupée**.
3. Définissez Configuration requise du code sur `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
4. Définissez **Application ou service** sur **SystemPolicyAllFiles** et l’accès sur **Autoriser**.

   :::image type="content" source="images/mac-system-extension-privacy.png" alt-text=" L’élément de menu Contrôle de stratégie de confidentialité" lightbox="images/mac-system-extension-privacy.png":::

### <a name="network-extension-policy"></a>Stratégie d’extension réseau

Dans le cadre des fonctionnalités de détection et de réponse des points de terminaison, Microsoft Defender pour point de terminaison sur macOS inspecte le trafic de socket et signale ces informations au portail Microsoft 365 Defender. La stratégie suivante permet à l’extension réseau d’effectuer cette fonctionnalité.

> [!NOTE]
> JAMF n’a pas de prise en charge intégrée des stratégies de filtrage de contenu, ce qui est une condition préalable à l’activation des extensions réseau qui Microsoft Defender pour point de terminaison sur les installations macOS sur l’appareil. En outre, JAMF modifie parfois le contenu des stratégies déployées.
> Par conséquent, les étapes suivantes fournissent une solution de contournement qui implique la signature du profil de configuration.

1. Enregistrez le contenu suivant sur votre appareil à l’aide `com.microsoft.network-extension.mobileconfig` d’un éditeur de texte :

    ```xml
    <?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1">
        <dict>
            <key>PayloadUUID</key>
            <string>DA2CC794-488B-4AFF-89F7-6686A7E7B8AB</string>
            <key>PayloadType</key>
            <string>Configuration</string>
            <key>PayloadOrganization</key>
            <string>Microsoft Corporation</string>
            <key>PayloadIdentifier</key>
            <string>DA2CC794-488B-4AFF-89F7-6686A7E7B8AB</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft Defender Network Extension</string>
            <key>PayloadDescription</key>
            <string/>
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
                    <string>2BA070D9-2233-4827-AFC1-1F44C8C8E527</string>
                    <key>PayloadType</key>
                    <string>com.apple.webcontent-filter</string>
                    <key>PayloadOrganization</key>
                    <string>Microsoft Corporation</string>
                    <key>PayloadIdentifier</key>
                    <string>CEBF7A71-D9A1-48BD-8CCF-BD9D18EC155A</string>
                    <key>PayloadDisplayName</key>
                    <string>Approved Network Extension</string>
                    <key>PayloadDescription</key>
                    <string/>
                    <key>PayloadVersion</key>
                    <integer>1</integer>
                    <key>PayloadEnabled</key>
                    <true/>
                    <key>FilterType</key>
                    <string>Plugin</string>
                    <key>UserDefinedName</key>
                    <string>Microsoft Defender Network Extension</string>
                    <key>PluginBundleID</key>
                    <string>com.microsoft.wdav</string>
                    <key>FilterSockets</key>
                    <true/>
                    <key>FilterDataProviderBundleIdentifier</key>
                    <string>com.microsoft.wdav.netext</string>
                    <key>FilterDataProviderDesignatedRequirement</key>
                    <string>identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
                </dict>
            </array>
        </dict>
    </plist>
    ```

2. Vérifiez que le fichier ci-dessus a été copié correctement en exécutant l’utilitaire `plutil` dans le terminal :

    ```bash
    $ plutil -lint <PathToFile>/com.microsoft.network-extension.mobileconfig
    ```

    Par exemple, si le fichier a été stocké dans Documents :

    ```bash
    $ plutil -lint ~/Documents/com.microsoft.network-extension.mobileconfig
    ```

    Vérifiez que la commande génère `OK`.

    ```bash
    <PathToFile>/com.microsoft.network-extension.mobileconfig: OK
    ```

3. Suivez les instructions de [cette page](https://www.jamf.com/jamf-nation/articles/649/creating-a-signing-certificate-using-jamf-pro-s-built-in-certificate-authority) pour créer un certificat de signature à l’aide de l’autorité de certification intégrée de JAMF.

4. Une fois le certificat créé et installé sur votre appareil, exécutez la commande suivante à partir du Terminal pour signer le fichier :

    ```bash
    $ security cms -S -N "<CertificateName>" -i <PathToFile>/com.microsoft.network-extension.mobileconfig -o <PathToSignedFile>/com.microsoft.network-extension.signed.mobileconfig
    ```

    Par exemple, si le nom du certificat est **SigningCertificate** et que le fichier signé va être stocké dans Documents :

    ```bash
    $ security cms -S -N "SigningCertificate" -i ~/Documents/com.microsoft.network-extension.mobileconfig -o ~/Documents/com.microsoft.network-extension.signed.mobileconfig
    ```

5. Dans le portail JAMF, accédez à **Profils de configuration** , puis cliquez sur le bouton **Charger** . Sélectionnez `com.microsoft.network-extension.signed.mobileconfig` lorsque vous êtes invité à entrer le fichier.

## <a name="intune"></a>Intune

### <a name="intune-system-extensions-policy"></a>Intune stratégie d’extensions système

Pour approuver les extensions système :

1. Dans Intune, ouvrez **Gérer la** \> **configuration de l’appareil**. Sélectionnez **Gérer les** \> **profils** \> **Créer un profil**.
2. Choisissez un nom pour le profil. Remplacez **Platform=macOS par** **Type de profil=Extensions**. Sélectionnez **Créer**.
3. Dans l’onglet `Basics` , donnez un nom à ce nouveau profil.
4. Dans l’onglet `Configuration settings` , ajoutez les entrées suivantes dans la `Allowed system extensions` section :

   <br>

   ****

   |Identificateur d’offre groupée|Identificateur d’équipe|
   |---|---|
   |com.microsoft.wdav.epsext|UBF8T346G9|
   |com.microsoft.wdav.netext|UBF8T346G9|
   |||

   :::image type="content" source="images/mac-system-extension-intune2.png" alt-text=" Page Profils de configuration système" lightbox="images/mac-system-extension-intune2.png":::

5. Dans l’onglet `Assignments` , affectez ce profil à **Tous les utilisateurs & Tous les appareils**.
6. Passez en revue et créez ce profil de configuration.

### <a name="create-and-deploy-the-custom-configuration-profile"></a>Créer et déployer le profil de configuration personnalisé

Le profil de configuration suivant active l’extension réseau et accorde un accès disque complet à l’extension système Endpoint Security.

Enregistrez le contenu suivant dans un fichier nommé **sysext.xml**:

```xml
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>7E53AC50-B88D-4132-99B6-29F7974EAA3C</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft Corporation</string>
        <key>PayloadIdentifier</key>
        <string>7E53AC50-B88D-4132-99B6-29F7974EAA3C</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender System Extensions</string>
        <key>PayloadDescription</key>
        <string/>
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
                <string>2BA070D9-2233-4827-AFC1-1F44C8C8E527</string>
                <key>PayloadType</key>
                <string>com.apple.webcontent-filter</string>
                <key>PayloadOrganization</key>
                <string>Microsoft Corporation</string>
                <key>PayloadIdentifier</key>
                <string>CEBF7A71-D9A1-48BD-8CCF-BD9D18EC155A</string>
                <key>PayloadDisplayName</key>
                <string>Approved Network Extension</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>FilterType</key>
                <string>Plugin</string>
                <key>UserDefinedName</key>
                <string>Microsoft Defender Network Extension</string>
                <key>PluginBundleID</key>
                <string>com.microsoft.wdav</string>
                <key>FilterSockets</key>
                <true/>
                <key>FilterDataProviderBundleIdentifier</key>
                <string>com.microsoft.wdav.netext</string>
                <key>FilterDataProviderDesignatedRequirement</key>
                <string>identifier &quot;com.microsoft.wdav.netext&quot; and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
            </dict>
            <dict>
                <key>PayloadUUID</key>
                <string>56105E89-C7C8-4A95-AEE6-E11B8BEA0366</string>
                <key>PayloadType</key>
                <string>com.apple.TCC.configuration-profile-policy</string>
                <key>PayloadOrganization</key>
                <string>Microsoft Corporation</string>
                <key>PayloadIdentifier</key>
                <string>56105E89-C7C8-4A95-AEE6-E11B8BEA0366</string>
                <key>PayloadDisplayName</key>
                <string>Privacy Preferences Policy Control</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>Services</key>
                <dict>
                    <key>SystemPolicyAllFiles</key>
                    <array>
                        <dict>
                            <key>Identifier</key>
                            <string>com.microsoft.wdav.epsext</string>
                            <key>CodeRequirement</key>
                            <string>identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
                            <key>IdentifierType</key>
                            <string>bundleID</string>
                            <key>StaticCode</key>
                            <integer>0</integer>
                            <key>Allowed</key>
                            <integer>1</integer>
                        </dict>
                    </array>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

Vérifiez que le fichier ci-dessus a été copié correctement. À partir du terminal, exécutez la commande suivante et vérifiez qu’elle génère `OK`:

```bash
$ plutil -lint sysext.xml
sysext.xml: OK
```

Pour déployer ce profil de configuration personnalisé :

1. Dans Intune, ouvrez **Gérer la** \> **configuration de l’appareil**. Sélectionnez **Gérer les** \> **profils** \> **Créer un profil**.
2. Choisissez un nom pour le profil. Modifiez **Platform=macOS** et **Profile type=Custom**. Sélectionnez **Configurer**.
3. Ouvrez le profil de configuration et chargez **sysext.xml**. Ce fichier a été créé à l’étape précédente.
4. Sélectionnez **OK**.

   :::image type="content" source="images/mac-system-extension-intune.png" alt-text="Extension système dans Intune page" lightbox="images/mac-system-extension-intune.png":::

5. Dans l’onglet `Assignments` , affectez ce profil à **Tous les utilisateurs & Tous les appareils**.
6. Passez en revue et créez ce profil de configuration.
