---
title: Microsoft Defender pour point de terminaison Mac
ms.reviewer: ''
description: Découvrez comment installer, configurer, mettre à jour et utiliser Microsoft Defender pour Endpoint pour Mac.
keywords: microsoft, defender, atp, mac, installation, déployer, désinstallation, intune, jamf, macos, big sur, magasin, mojave, mde pour mac
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 22d35a42eb7fb7eadbba686c292729772951c05c
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51500688"
---
# <a name="microsoft-defender-for-endpoint-for-mac"></a>Microsoft Defender pour point de terminaison Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique décrit comment installer, configurer, mettre à jour et utiliser Defender pour Endpoint pour Mac.

> [!CAUTION]
> L’exécution d’autres produits de protection de point de terminaison tiers avec Microsoft Defender pour Endpoint pour Mac est susceptible de provoquer des problèmes de performances et des effets secondaires imprévisibles. Si la protection des points de terminaison non-Microsoft est une exigence absolue dans votre environnement, vous pouvez toujours tirer parti en toute sécurité de la fonctionnalité Defender pour point de terminaison pour Mac EDR après avoir configuré la fonctionnalité antivirus pour qu’elle s’exécute en [mode passif.](mac-preferences.md#enable--disable-passive-mode)

## <a name="whats-new-in-the-latest-release"></a>Nouveautés de la dernière version

[Nouveautés dans Microsoft Defender pour point de terminaison](whats-new-in-microsoft-defender-atp.md)

[Nouveautés de Microsoft Defender pour Endpoint pour Mac](mac-whatsnew.md)

> [!TIP]
> Si vous avez des commentaires que vous souhaitez partager, envoyez-le en ouvrant Microsoft Defender pour Endpoint pour Mac sur votre appareil et en naviguant vers l’aide pour envoyer  >  **des commentaires.**

Pour obtenir les dernières fonctionnalités, y compris les fonctionnalités de prévisualisation (telles que la détection et la réponse des points de terminaison pour vos appareils Mac), configurez votre appareil macOS exécutant Microsoft Defender pour endpoint comme un appareil « Insider ».

## <a name="how-to-install-microsoft-defender-for-endpoint-for-mac"></a>Comment installer Microsoft Defender pour endpoint pour Mac

### <a name="prerequisites"></a>Conditions préalables

- Abonnement a Defender for Endpoint et accès au portail Centre de sécurité Microsoft Defender
- Expérience de niveau débutant dans les scripts macOS et BASH
- Privilèges d’administration sur l’appareil (en cas de déploiement manuel)

### <a name="installation-instructions"></a>Instructions d’installation

Vous pouvez utiliser plusieurs méthodes et outils de déploiement pour installer et configurer Defender pour Endpoint pour Mac.

- Outils de gestion tiers :
    - [Déploiement basé sur Microsoft Intune](mac-install-with-intune.md)
    - [Déploiement basé sur JAMF](mac-install-with-jamf.md)
    - [Autres produits MDM](mac-install-with-other-mdm.md)

- Outil en ligne de commande :
    - [Déploiement manuel](mac-install-manually.md)

### <a name="system-requirements"></a>Configuration requise

Les trois plus récentes publication majeures de macOS sont pris en charge.

> [!IMPORTANT]
> Sur macOS 11 (Big Sur), Microsoft Defender for Endpoint nécessite des profils de configuration supplémentaires. Si vous êtes un client existant en cours de mise à niveau à partir de versions antérieures de macOS, veillez à déployer les profils de configuration supplémentaires répertoriés dans les nouveaux profils de configuration pour macOS Et les versions plus récentes de [macOS.](mac-sysext-policies.md)

> [!IMPORTANT]
> La prise en charge de macOS 10.13 (High Sierra) n’est plus prise en charge depuis le 15 février 2021.

- 11 (Big Sur), 10.15 (Domaine), 10.14 (Mojave)
- Espace disque : 1 Go

Les versions bêta de macOS ne sont pas pris en charge.

Après avoir activé le service, vous devrez peut-être configurer votre réseau ou votre pare-feu pour autoriser les connexions sortantes entre celui-ci et vos points de terminaison.

### <a name="licensing-requirements"></a>Critères de licence

Microsoft Defender pour endpoint pour Mac nécessite l’une des offres de licence en volume Microsoft suivantes :

- Microsoft 365 E5 (M365 E5)
- Microsoft 365 E5 Sécurité
- Microsoft 365 A5 (M365 A5)

> [!NOTE]
> Les utilisateurs titulaires d’une licence éligible peuvent utiliser Microsoft Defender pour endpoint sur cinq appareils simultanés au plus.
> Microsoft Defender pour le point de terminaison est également disponible à l’achat auprès d’un fournisseur de solutions Cloud (CSP). Lorsqu’elle est achetée via un programme CSP, elle ne nécessite pas d’offres de licence en volume Microsoft répertoriées.

### <a name="network-connections"></a>Connexions réseau

La feuille de calcul téléchargeable suivante répertorie les services et les URL associées à qui votre réseau doit pouvoir se connecter. Vous devez vous assurer qu’il n’existe aucune règle de pare-feu ou de  filtrage réseau qui refuserait l’accès à ces URL, ou que vous devrez peut-être créer une règle d’autoriser spécifiquement pour eux.



|**Liste de feuilles de calcul de domaines**|**Description**|
|:-----|:-----|
|![Image miniature de la feuille de calcul DES URL de Microsoft Defender pour les points de terminaison](images/mdatp-urls.png)<br/>  | Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation. <br><br>Téléchargez la feuille de calcul [ ici :mdatp-urls.xlsx](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx).

Microsoft Defender pour le point de terminaison peut découvrir un serveur proxy à l’aide des méthodes de découverte suivantes :
- Proxy autoconfig (PAC)
- WPAD (Web Proxy Autodiscovery Protocol)
- Configuration manuelle du proxy statique

Si un proxy ou un pare-feu bloque le trafic anonyme, assurez-vous que le trafic anonyme est autorisé dans les URL répertoriées précédemment.

> [!WARNING]
> Les proxies authentifiés ne sont pas pris en charge. Assurez-vous que seuls pac, WPAD ou un proxy statique est utilisé.
>
> L’inspection et l’interception des proxies SSL ne sont pas non plus pris en charge pour des raisons de sécurité. Configurez une exception pour l’inspection SSL et votre serveur proxy afin de transmettre directement les données de Microsoft Defender pour Endpoint pour Mac aux URL pertinentes sans interception. L’ajout de votre certificat d’interception au magasin global n’autorise pas l’interception.

Pour vérifier qu’une connexion n’est pas bloquée, [https://x.cp.wd.microsoft.com/api/report](https://x.cp.wd.microsoft.com/api/report) ouvrez-la [https://cdn.x.cp.wd.microsoft.com/ping](https://cdn.x.cp.wd.microsoft.com/ping) et dans un navigateur.

Si vous préférez la ligne de commande, vous pouvez également vérifier la connexion en exécutant la commande suivante dans Terminal :

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

La sortie de cette commande doit être similaire à celle-ci :

 `OK https://x.cp.wd.microsoft.com/api/report`

 `OK https://cdn.x.cp.wd.microsoft.com/ping`

> [!CAUTION]
> Nous vous recommandons de conserver la [Protection de l’intégrité](https://support.apple.com/en-us/HT204899) du système (SIP) activée sur les appareils clients. SIP est une fonctionnalité de sécurité macOS intégrée qui empêche toute falsification de bas niveau avec le système d’exploitation et est activée par défaut.

Une fois Que Microsoft Defender pour le point de terminaison est installé, la connectivité peut être validée en exécutant la commande suivante dans Terminal :
```bash
mdatp connectivity test
```

## <a name="how-to-update-microsoft-defender-for-endpoint-for-mac"></a>Comment mettre à jour Microsoft Defender pour endpoint pour Mac

Microsoft publie régulièrement des mises à jour logicielles pour améliorer les performances, la sécurité et fournir de nouvelles fonctionnalités. Pour mettre à jour Microsoft Defender pour Endpoint pour Mac, un programme nommé Microsoft AutoUpdate (MAU) est utilisé. Pour plus d’informations, voir [Déployer les mises à jour de Microsoft Defender pour Endpoint pour Mac.](mac-updates.md)

## <a name="how-to-configure-microsoft-defender-for-endpoint-for-mac"></a>Comment configurer Microsoft Defender pour endpoint pour Mac

Des instructions sur la configuration du produit dans les environnements d’entreprise sont disponibles dans Définir les préférences de [Microsoft Defender pour Endpoint pour Mac.](mac-preferences.md)

## <a name="macos-kernel-and-system-extensions"></a>Noyau macOS et extensions système

En adéquation avec l’évolution de macOS, nous préparons une mise à jour de Microsoft Defender pour Endpoint pour Mac qui tire parti des extensions système au lieu des extensions de noyau. Pour plus d’informations, voir Nouveautés de [Microsoft Defender pour Endpoint pour Mac.](mac-whatsnew.md)

## <a name="resources"></a>Ressources

- Pour plus d’informations sur la journalisation, la désinstallation ou d’autres rubriques, voir [Resources for Microsoft Defender for Endpoint for Mac](mac-resources.md).

- [Confidentialité pour Microsoft Defender pour point de terminaison pour Mac.](mac-privacy.md)