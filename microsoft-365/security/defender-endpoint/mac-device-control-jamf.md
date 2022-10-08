---
title: Exemples de stratégies de contrôle d’appareil pour JAMF
description: Découvrez comment utiliser des stratégies de contrôle d’appareil à l’aide d’exemples qui peuvent être utilisés avec JAMF.
keywords: microsoft, defender, point de terminaison, Microsoft Defender pour point de terminaison, mac, appareil, contrôle, usb, amovible, média, jamf
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
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 201e7a1be6caa53f8a7ba68c4b7090de21c21e90
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68221541"
---
# <a name="examples-of-device-control-policies-for-jamf"></a>Exemples de stratégies de contrôle d’appareil pour JAMF

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Ce document contient des exemples de stratégies de contrôle d’appareil que vous pouvez personnaliser pour votre propre organisation. Ces exemples s’appliquent si vous utilisez JAMF pour gérer les appareils de votre entreprise.

## <a name="restrict-access-to-all-removable-media"></a>Restreindre l’accès à tous les supports amovibles

L’exemple suivant limite l’accès à tous les supports amovibles. Notez l’autorisation `none` appliquée au niveau supérieur de la stratégie, ce qui signifie que toutes les opérations de fichier seront interdites.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>block</string>
            <key>permission</key>
            <array>
                <string>none</string>
            </array>
        </dict>
    </dict>
</dict>
</plist>
```

## <a name="set-all-removable-media-to-be-read-only"></a>Définir tous les supports amovibles en lecture seule

L’exemple suivant configure tous les supports amovibles en lecture seule. Notez l’autorisation `read` appliquée au niveau supérieur de la stratégie, ce qui signifie que toutes les opérations d’écriture et d’exécution ne seront pas autorisées.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>block</string>
            <key>permission</key>
            <array>
                <string>read</string>
            </array>
        </dict>
    </dict>
</dict>
</plist>
```

## <a name="disallow-program-execution-from-removable-media"></a>Interdire l’exécution du programme à partir d’un média amovible

L’exemple suivant montre comment l’exécution du programme à partir d’un média amovible peut être interdite. Notez les `read` autorisations `write` appliquées au niveau supérieur de la stratégie.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>block</string>
            <key>permission</key>
            <array>
                <string>read</string>
                <string>write</string>
            </array>
        </dict>
    </dict>
</dict>
</plist>
```

## <a name="restrict-all-devices-from-specific-vendors"></a>Restreindre tous les appareils de fournisseurs spécifiques

L’exemple suivant restreint tous les appareils de fournisseurs spécifiques (dans ce cas identifiés par `fff0` et `4525`). Tous les autres appareils seront illimités, car l’autorisation définie au niveau supérieur de la stratégie répertorie toutes les autorisations possibles (lecture, écriture et exécution).

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>block</string>
            <key>permission</key>
            <array>
                <string>read</string>
                <string>write</string>
                <string>execute</string>
            </array>
            <key>vendors</key>
            <dict>
                <key>fff0</key>
                <dict>
                    <key>permission</key>
                    <array>
                        <string>none</string>
                    </array>
                </dict>
                <key>4525</key>
                <dict>
                    <key>permission</key>
                    <array>
                        <string>none</string>
                    </array>
                </dict>
            </dict>
        </dict>
    </dict>
</dict>
</plist>
```

## <a name="restrict-specific-devices-identified-by-vendor-id-product-id-and-serial-number"></a>Restreindre des appareils spécifiques identifiés par l’ID du fournisseur, l’ID de produit et le numéro de série

L’exemple suivant restreint deux appareils spécifiques, identifiés par l’ID `fff0`du fournisseur, l’ID `1000`de produit et les numéros `04ZSSMHI2O7WBVOA` de série et `04ZSSMHI2O7WBVOB`. À tous les autres niveaux de la stratégie, les autorisations incluent toutes les valeurs possibles (lecture, écriture et exécution), ce qui signifie que tous les autres appareils seront illimités.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>block</string>
            <key>permission</key>
            <array>
                <string>read</string>
                <string>write</string>
                <string>execute</string>
            </array>
            <key>vendors</key>
            <dict>
                <key>fff0</key>
                <dict>
                    <key>permission</key>
                    <array>
                        <string>read</string>
                        <string>write</string>
                        <string>execute</string>
                    </array>
                    <key>products</key>
                    <dict>
                        <key>1000</key>
                        <dict>
                            <key>permission</key>
                            <array>
                                <string>read</string>
                                <string>write</string>
                                <string>execute</string>
                            </array>
                            <key>serialNumbers</key>
                            <dict>
                                <key>04ZSSMHI2O7WBVOA</key>
                                <array>
                                  <string>none</string>
                                </array>
                                <key>04ZSSMHI2O7WBVOB</key>
                                <array>
                                  <string>none</string>
                                </array>
                            </dict>
                        </dict>
                    </dict>
                </dict>
            </dict>
        </dict>
    </dict>
</dict>
</plist>
```

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble du contrôle d’appareil pour macOS](mac-device-control-overview.md)
