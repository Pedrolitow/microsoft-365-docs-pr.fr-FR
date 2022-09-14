---
title: Contrôle d’appareil pour macOS
description: Découvrez comment configurer Microsoft Defender pour point de terminaison sur Mac pour réduire les menaces provenant d’un stockage amovible tel que des périphériques USB.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, appareil, contrôle, usb, amovible, média
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
- m365-security-compliance
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: ffd814f3cbb90a072ce8dbe21aa3f3793cfa9c01
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67687106"
---
# <a name="device-control-for-macos"></a>Contrôle d’appareil pour macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="requirements"></a>Conditions requises

Le contrôle d’appareil pour macOS présente les prérequis suivants :

> [!div class="checklist"]
>
> - Microsoft Defender pour point de terminaison droit (peut être une version d’évaluation)
> - Version minimale du système d’exploitation : macOS 11 ou version ultérieure
> - Version minimale du produit : 101.34.20

## <a name="device-control-policy"></a>Stratégie de contrôle d’appareil

Pour configurer le contrôle d’appareil pour macOS, vous devez créer une stratégie qui décrit les restrictions que vous souhaitez mettre en place au sein de votre organisation.

La stratégie de contrôle d’appareil est incluse dans le profil de configuration utilisé pour configurer tous les autres paramètres de produit. Pour plus d’informations, consultez [La structure du profil de configuration](mac-preferences.md#configuration-profile-structure).

Dans le profil de configuration, la stratégie de contrôle d’appareil est définie dans la section suivante :

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|deviceControl|
|**Type de données**|Dictionnaire (préférence imbriqué)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|

La stratégie de contrôle d’appareil peut être utilisée pour :

- [Personnaliser la cible d’URL pour les notifications déclenchées par le contrôle d’appareil](#customize-url-target-for-notifications-raised-by-device-control)
- [Autoriser ou bloquer des appareils amovibles](#allow-or-block-removable-devices)

### <a name="customize-url-target-for-notifications-raised-by-device-control"></a>Personnaliser la cible d’URL pour les notifications déclenchées par le contrôle d’appareil

Lorsque la stratégie de contrôle d’appareil que vous avez mise en place est appliquée sur un appareil (par exemple, l’accès à un périphérique multimédia amovible est restreint), une notification s’affiche à l’utilisateur.

:::image type="content" source="images/mac-device-control-notification.png" alt-text="Notification de contrôle d’appareil" lightbox="images/mac-device-control-notification.png":::

Lorsque les utilisateurs finaux cliquent sur cette notification, une page web est ouverte dans le navigateur par défaut. Vous pouvez configurer l’URL qui est ouverte lorsque les utilisateurs finaux cliquent sur la notification.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|navigationTarget|
|**Type de données**|Chaîne|
|**Commentaires**|S’il n’est pas défini, le produit utilise une URL par défaut pointant vers une page générique expliquant l’action effectuée par le produit.|
|

### <a name="allow-or-block-removable-devices"></a>Autoriser ou bloquer des appareils amovibles

La section média amovible de la stratégie de contrôle d’appareil est utilisée pour restreindre l’accès aux supports amovibles.

> [!NOTE]
> Les types de supports amovibles suivants sont actuellement pris en charge et peuvent être inclus dans la stratégie : les périphériques de stockage USB.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|removableMediaPolicy|
|**Type de données**|Dictionnaire (préférence imbriqué)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|

Cette section de la stratégie est hiérarchique, ce qui permet une flexibilité maximale et couvre un large éventail de cas d’usage. Au niveau supérieur se trouvent les fournisseurs, identifiés par un ID de fournisseur. Pour chaque fournisseur, il existe des produits, identifiés par un ID de produit. Enfin, pour chaque produit, il existe des numéros de série indiquant des appareils spécifiques.

```text
|-- policy top level
    |-- vendor 1
        |-- product 1
            |-- serial number 1
            ...
            |-- serial number N
        ...
        |-- product N
    ...
    |-- vendor N
```

Pour plus d’informations sur la recherche des identificateurs d’appareil, consultez [Rechercher les identificateurs d’appareil](#look-up-device-identifiers).

La stratégie est évaluée de l’entrée la plus spécifique à la plus générale. Autrement dit, lorsqu’un appareil est branché, le produit tente de trouver la correspondance la plus spécifique dans la stratégie pour chaque périphérique multimédia amovible et d’appliquer les autorisations à ce niveau. S’il n’y a pas de correspondance, la meilleure correspondance suivante est appliquée, jusqu’à l’autorisation spécifiée au niveau supérieur, qui est la valeur par défaut lorsqu’un appareil ne correspond à aucune autre entrée de la stratégie.

#### <a name="policy-enforcement-level"></a>Niveau d’application de la stratégie

Dans la section média amovible, vous pouvez définir le niveau d’application, qui peut prendre l’une des valeurs suivantes :

- `audit` - Sous ce niveau de mise en œuvre, si l’accès à un appareil est restreint, une notification s’affiche à l’utilisateur, mais l’appareil peut toujours être utilisé. Ce niveau d’application peut être utile pour évaluer l’efficacité d’une stratégie.
- `block` - Dans ce niveau d’application, les opérations que l’utilisateur peut effectuer sur l’appareil sont limitées à ce qui est défini dans la stratégie. En outre, une notification est envoyée à l’utilisateur.

> [!NOTE]
> Par défaut, le niveau d’application est défini sur `audit`.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|enforcementLevel|
|**Type de données**|Chaîne|
|**Valeurs possibles**|audit (par défaut) <p> Bloc|
|

#### <a name="default-permission-level"></a>Niveau d’autorisation par défaut

Au niveau supérieur de la section média amovible, vous pouvez configurer le niveau d’autorisation par défaut pour les appareils qui ne correspondent à rien d’autre dans la stratégie.

Ce paramètre peut être défini sur :

- `none` - Aucune opération ne peut être effectuée sur l’appareil
- Combinaison des valeurs suivantes :
  - `read` - Les opérations de lecture sont autorisées sur l’appareil
  - `write` - Les opérations d’écriture sont autorisées sur l’appareil
  - `execute` - Les opérations d’exécution sont autorisées sur l’appareil

> [!NOTE]
> S’il `none` est présent dans le niveau d’autorisation, toutes les autres autorisations (`read`, `write`ou `execute`) sont ignorées.
>
> L’autorisation `execute` fait uniquement référence à l’exécution de fichiers binaires Mach-O. Il n’inclut pas l’exécution de scripts ou d’autres types de charges utiles.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|autorisation|
|**Type de données**|Tableau de chaînes|
|**Valeurs possibles**|none <p> read <p> write <p> Exécuter|
|

#### <a name="restrict-removable-media-by-vendor-product-and-serial-number"></a>Restreindre les supports amovibles par fournisseur, produit et numéro de série

Comme décrit dans [Autoriser ou bloquer les appareils amovibles](#allow-or-block-removable-devices), les supports amovibles tels que les périphériques USB peuvent être identifiés par l’ID du fournisseur, l’ID de produit et le numéro de série.

Au niveau supérieur de la stratégie de média amovible, vous pouvez éventuellement définir des restrictions plus granulaires au niveau du fournisseur.

Le `vendors` dictionnaire contient une ou plusieurs entrées, chaque entrée étant identifiée par l’ID du fournisseur.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|Fournisseurs|
|**Type de données**|Dictionnaire (préférence imbriqué)|
|

Pour chaque fournisseur, vous pouvez spécifier le niveau d’autorisation souhaité pour les appareils de ce fournisseur.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|autorisation|
|**Type de données**|Tableau de chaînes|
|**Valeurs possibles**|Identique au [niveau d’autorisation par défaut](#default-permission-level)|
|

En outre, vous pouvez éventuellement spécifier l’ensemble des produits appartenant à ce fournisseur pour lesquels des autorisations plus granulaires sont définies. Le `products` dictionnaire contient une ou plusieurs entrées, chaque entrée étant identifiée par l’ID de produit.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|Produits|
|**Type de données**|Dictionnaire (préférence imbriqué)|
|

Pour chaque produit, vous pouvez spécifier le niveau d’autorisation souhaité pour ce produit.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|autorisation|
|**Type de données**|Tableau de chaînes|
|**Valeurs possibles**|Identique au [niveau d’autorisation par défaut](#default-permission-level)|
|

En outre, vous pouvez spécifier un ensemble facultatif de numéros de série pour lesquels des autorisations plus précises sont définies.

Le `serialNumbers` dictionnaire contient une ou plusieurs entrées, chaque entrée étant identifiée par le numéro de série.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|serialNumbers|
|**Type de données**|Dictionnaire (préférence imbriqué)|
|

Pour chaque numéro de série, vous pouvez spécifier le niveau d’autorisation souhaité.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|autorisation|
|**Type de données**|Tableau de chaînes|
|**Valeurs possibles**|Identique au [niveau d’autorisation par défaut](#default-permission-level)|
|

#### <a name="example-device-control-policy"></a>Exemple de stratégie de contrôle d’appareil

L’exemple suivant montre comment combiner tous les concepts ci-dessus dans une stratégie de contrôle d’appareil. Dans l’exemple suivant, notez la nature hiérarchique de la stratégie de média amovible.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>navigationTarget</key>
        <string>[custom URL for notifications]</string>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>[enforcement level]</string> <!-- audit / block -->
            <key>permission</key>
            <array>
                <string>[permission]</string> <!-- none / read / write / execute -->
                <!-- other permissions -->
            </array>
            <key>vendors</key>
            <dict>
                <key>[vendor id]</key>
                <dict>
                    <key>permission</key>
                    <array>
                        <string>[permission]</string> <!-- none / read / write / execute -->
                        <!-- other permissions -->
                    </array>
                    <key>products</key>
                    <dict>
                        <key>[product id]</key>
                        <dict>
                            <key>permission</key>
                            <array>
                                <string>[permission]</string> <!-- none / read / write / execute -->
                                <!-- other permissions -->
                            </array>
                            <key>serialNumbers</key>
                            <dict>
                                <key>[serial-number]</key>
                                <array>
                                    <string>[permission]</string> <!-- none / read / write / execute -->
                                    <!-- other permissions -->
                                </array>
                                <!-- other serial numbers -->
                            </dict>
                        </dict>
                        <!-- other products -->
                    </dict>
                </dict>
                <!-- other vendors -->
            </dict>
        </dict>
    </dict>
</dict>
</plist>
```

Nous avons inclus d’autres exemples de stratégies de contrôle d’appareil dans les documents suivants :

- [Exemples de stratégies de contrôle d’appareil pour Intune](mac-device-control-intune.md)
- [Exemples de stratégies de contrôle d’appareil pour JAMF](mac-device-control-jamf.md)

#### <a name="look-up-device-identifiers"></a>Rechercher les identificateurs d’appareil

Pour rechercher l’ID du fournisseur, l’ID de produit et le numéro de série d’un périphérique USB :

1. Connectez-vous à un appareil Mac.
1. Connectez l’appareil USB pour lequel vous souhaitez rechercher les identificateurs.
1. Dans le menu de niveau supérieur de macOS, sélectionnez **À propos de ce Mac**.

   :::image type="content" source="images/mac-device-control-lookup-1.png" alt-text="À propos de cette page Mac" lightbox="images/mac-device-control-lookup-1.png":::

1. Sélectionnez **Rapport système**.

   :::image type="content" source="images/mac-device-control-lookup-2.png" alt-text="Rapport système" lightbox="images/mac-device-control-lookup-2.png":::

1. Dans la colonne de gauche, sélectionnez **USB**.

   :::image type="content" source="images/mac-device-control-lookup-3.png" alt-text="Vue de tous les périphériques USB" lightbox="images/mac-device-control-lookup-3.png":::
    

1. Sous **l’arborescence des périphériques USB**, accédez à l’appareil USB que vous avez branché.

   :::image type="content" source="images/mac-device-control-lookup-4.png" alt-text="Détails d’un périphérique USB" lightbox="images/mac-device-control-lookup-4.png":::

1. L’ID du fournisseur, l’ID de produit et le numéro de série sont affichés. Lors de l’ajout de l’ID de fournisseur et de l’ID de produit à la stratégie de média amovible, vous devez uniquement ajouter la partie après `0x`. Par exemple, dans l’image ci-dessous, l’ID du fournisseur est `1000` et l’ID de produit est `090c`.

#### <a name="discover-usb-devices-in-your-organization"></a>Découvrir les périphériques USB de votre organisation

Vous pouvez afficher les événements de montage, de démontage et de modification de volume provenant d’appareils USB dans Microsoft Defender pour point de terminaison repérage avancé. Ces événements peuvent être utiles pour identifier les activités d’utilisation suspectes ou effectuer des investigations internes.

```bash
DeviceEvents
    | where ActionType == "UsbDriveMounted" or ActionType == "UsbDriveUnmounted" or ActionType == "UsbDriveDriveLetterChanged"
    | where DeviceId == "<device ID>"
```

## <a name="device-control-policy-deployment"></a>Déploiement d’une stratégie de contrôle d’appareil

La stratégie de contrôle d’appareil doit être incluse en regard des autres paramètres de produit, comme décrit dans [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md).

Ce profil peut être déployé à l’aide des instructions répertoriées dans le [déploiement du profil de configuration](mac-preferences.md#configuration-profile-deployment).

## <a name="troubleshooting-tips"></a>Conseils de dépannage

Après avoir poussé le profil de configuration via Intune ou JAMF, vous pouvez vérifier s’il a été correctement récupéré par le produit en exécutant la commande suivante à partir du terminal :

```bash
mdatp device-control removable-media policy list
```

Cette commande imprime en sortie standard la stratégie de contrôle d’appareil que le produit utilise. Dans le cas où cela s’imprime `Policy is empty`, assurez-vous que (a) le profil de configuration a bien été envoyé à votre appareil à partir de la console de gestion, et (b) qu’il s’agit d’une stratégie de contrôle d’appareil valide, comme décrit dans ce document.

Sur un appareil sur lequel la stratégie a été remise avec succès et où un ou plusieurs appareils sont connectés, vous pouvez exécuter la commande suivante pour répertorier tous les appareils et les autorisations effectives qui leur sont appliquées.

```bash
mdatp device-control removable-media devices list
```

Exemple de sortie :

```Output
.Device(s)
|-o Name: Untitled 1, Permission ["read", "execute"]
| |-o Vendor: General "fff0"
| |-o Product: USB Flash Disk "1000"
| |-o Serial number: "04ZSSMHI2O7WBVOA"
| |-o Mount point: "/Volumes/TESTUSB"
```

Dans l’exemple ci-dessus, il n’y a qu’un seul périphérique multimédia amovible connecté et il dispose `read` et `execute` dispose d’autorisations, conformément à la stratégie de contrôle d’appareil qui a été remise à l’appareil.

## <a name="related-topics"></a>Voir aussi

- [Exemples de stratégies de contrôle d’appareil pour Intune](mac-device-control-intune.md)
- [Exemples de stratégies de contrôle d’appareil pour JAMF](mac-device-control-jamf.md)
