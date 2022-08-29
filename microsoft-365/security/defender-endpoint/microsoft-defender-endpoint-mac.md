---
title: Microsoft Defender pour point de terminaison sur Mac
ms.reviewer: ''
description: Découvrez comment installer, configurer, mettre à jour et utiliser Microsoft Defender pour point de terminaison sur Mac.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, deploy, uninstallation, intune, jamf, macos, monterey, big sur, catalina, mojave, mde pour mac
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 97f7477c1216bfa25e25f6fc3086cf62a8b4b5a3
ms.sourcegitcommit: d09eb780dc41a01796eb8137fbe9267231af6746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2022
ms.locfileid: "67384080"
---
# <a name="microsoft-defender-for-endpoint-on-mac"></a>Microsoft Defender pour point de terminaison sur Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cette rubrique explique comment installer, configurer, mettre à jour et utiliser Defender pour point de terminaison sur Mac.

> [!CAUTION]
> L’exécution d’autres produits de protection de point de terminaison tiers avec Microsoft Defender pour point de terminaison sur Mac est susceptible d’entraîner des problèmes de performances et des effets secondaires imprévisibles. Si la protection des points de terminaison non Microsoft est une exigence absolue dans votre environnement, vous pouvez toujours tirer parti en toute sécurité de la fonctionnalité Defender pour point de terminaison sur Mac EDR après avoir configuré la fonctionnalité antivirus pour qu’elle s’exécute en [mode passif](mac-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="whats-new-in-the-latest-release"></a>Nouveautés de la dernière version

[Nouveautés dans Microsoft Defender pour point de terminaison](whats-new-in-microsoft-defender-endpoint.md)

[Nouveautés de Microsoft Defender pour point de terminaison sur Mac](mac-whatsnew.md)

> [!TIP]
> Si vous souhaitez partager des commentaires, envoyez-le en ouvrant Microsoft Defender pour point de terminaison sur Mac sur votre appareil et en accédant à **l’aide** \> envoyer **des commentaires**.

Pour obtenir les fonctionnalités les plus récentes, notamment les fonctionnalités d’aperçu (telles que la détection de point de terminaison et la réponse pour vos appareils Mac), configurez votre appareil macOS en cours d’exécution Microsoft Defender pour point de terminaison être un appareil « Insider ».

## <a name="how-to-install-microsoft-defender-for-endpoint-on-mac"></a>Comment installer Microsoft Defender pour point de terminaison sur Mac

### <a name="prerequisites"></a>Conditions préalables

- Un abonnement Defender pour point de terminaison et un accès au portail Microsoft 365 Defender
- Expérience de niveau débutant dans les scripts macOS et BASH
- Privilèges d’administration sur l’appareil (en cas de déploiement manuel)

### <a name="installation-instructions"></a>Instructions d’installation

Vous pouvez utiliser plusieurs méthodes et outils de déploiement pour installer et configurer Defender pour point de terminaison sur Mac.

- Outils de gestion tiers :
    - [Déploiement basé sur Microsoft Intune](mac-install-with-intune.md)
    - [Déploiement basé sur JAMF](mac-install-with-jamf.md)
    - [Autres produits GPM](mac-install-with-other-mdm.md)

- Outil en ligne de commande :
    - [Déploiement manuel](mac-install-manually.md)

### <a name="system-requirements"></a>Configuration requise

Les trois versions majeures les plus récentes de macOS sont prises en charge.

> [!IMPORTANT]
> Sur macOS 11 (Big Sur) et versions ultérieures, Microsoft Defender pour point de terminaison nécessite des profils de configuration supplémentaires. Si vous êtes un client existant qui effectue une mise à niveau à partir de versions antérieures de macOS, veillez à déployer les profils de configuration supplémentaires répertoriés sur [les nouveaux profils de configuration pour macOS Catalina et les versions plus récentes de macOS](mac-sysext-policies.md).

- 12 (Monterey), 11 (Big Sur), 10.15 (Catalina)
- Espace disque : 1 Go

Les versions bêta de macOS ne sont pas prises en charge.

La prise en charge des appareils macOS avec des processeurs À puce M1 est officiellement prise en charge depuis la version 101.40.84 de l’agent.

Une fois que vous avez activé le service, vous devrez peut-être configurer votre réseau ou votre pare-feu pour autoriser les connexions sortantes entre celui-ci et vos points de terminaison.

### <a name="licensing-requirements"></a>Conditions d'octroi de licence

Microsoft Defender pour point de terminaison sur Mac nécessite l’une des offres de licence en volume Microsoft suivantes :

- Microsoft 365 E5 (M365 E5)
- Microsoft 365 E5 Sécurité
- Microsoft 365 A5 (M365 A5)
- Windows 10 Entreprise E5
- Microsoft 365 Business Premium
- Windows 11 Entreprise E5
- Microsoft Defender pour point de terminaison

> [!NOTE]
> Les utilisateurs sous licence éligibles peuvent utiliser Microsoft Defender pour point de terminaison sur jusqu’à cinq appareils simultanés.
> Microsoft Defender pour point de terminaison est également disponible à l’achat auprès d’un fournisseur de solutions cloud (CSP). Lorsqu’elle est achetée via un fournisseur de solutions Cloud, elle ne nécessite pas d’offres de licence en volume Microsoft répertoriées.

### <a name="configuring-exclusions"></a>Configuration des exclusions

Lorsque vous ajoutez des exclusions, tenez compte des [erreurs d’exclusion courantes pour l’antivirus Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus).

### <a name="network-connections"></a>Connexions réseau

La feuille de calcul téléchargeable suivante répertorie les services et leurs URL associées auxquelles votre réseau doit pouvoir se connecter. Vous devez vous assurer qu’il n’existe aucune règle de pare-feu ou de filtrage réseau qui refuserait l’accès à ces URL, ou vous devrez peut-être créer une règle *d’autorisation* spécifiquement pour elles.


|Feuille de calcul de la liste des domaines| Description|
|---|---|
|liste d’URL Microsoft Defender pour point de terminaison pour les clients commerciaux| Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation des clients commerciaux. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender pour point de terminaison liste d’URL pour Gov/GCC/DoD | Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation pour les clients Gov/GCC/DoD. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Microsoft Defender pour point de terminaison pouvez découvrir un serveur proxy à l’aide des méthodes de découverte suivantes :

- Configuration automatique du proxy (PAC)
- Protocole WPAD (Web Proxy Auto-Discovery Protocol)
- Configuration manuelle du proxy statique

Si un proxy ou un pare-feu bloque le trafic anonyme, assurez-vous que le trafic anonyme est autorisé dans les URL précédemment répertoriées.

> [!WARNING]
> Les proxys authentifiés ne sont pas pris en charge. Vérifiez que seuls pac, WPAD ou proxy statique sont utilisés.
>
> Les proxys d’inspection et d’interception SSL ne sont pas non plus pris en charge pour des raisons de sécurité. Configurez une exception pour l’inspection SSL et votre serveur proxy pour passer directement les données de Microsoft Defender pour point de terminaison sur macOS aux URL pertinentes sans interception. L’ajout de votre certificat d’interception au magasin global n’autorise pas l’interception.

Pour tester qu’une connexion n’est pas bloquée, ouvrez <https://x.cp.wd.microsoft.com/api/report> et <https://cdn.x.cp.wd.microsoft.com/ping> dans un navigateur.

Si vous préférez la ligne de commande, vous pouvez également vérifier la connexion en exécutant la commande suivante dans Terminal :

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

La sortie de cette commande doit être similaire à ce qui suit :

 `OK https://x.cp.wd.microsoft.com/api/report`

 `OK https://cdn.x.cp.wd.microsoft.com/ping`

> [!CAUTION]
> Nous vous recommandons de conserver [la protection d’intégrité système](https://support.apple.com/HT204899) (SIP) activée sur les appareils clients. SIP est une fonctionnalité de sécurité macOS intégrée qui empêche la falsification de bas niveau avec le système d’exploitation et est activée par défaut.

Une fois Microsoft Defender pour point de terminaison installé, la connectivité peut être validée en exécutant la commande suivante dans Terminal :

```bash
mdatp connectivity test
```

## <a name="how-to-update-microsoft-defender-for-endpoint-on-mac"></a>Guide pratique pour mettre à jour Microsoft Defender pour point de terminaison sur Mac

Microsoft publie régulièrement des mises à jour logicielles pour améliorer les performances, la sécurité et fournir de nouvelles fonctionnalités. Pour mettre à jour Microsoft Defender pour point de terminaison sur Mac, un programme nommé Microsoft AutoUpdate (MAU) est utilisé. Pour plus d’informations, consultez [Déployer des mises à jour pour Microsoft Defender pour point de terminaison sur Mac](mac-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-mac"></a>Comment configurer Microsoft Defender pour point de terminaison sur Mac

Des conseils sur la configuration du produit dans les environnements d’entreprise sont [disponibles dans Définir les préférences pour Microsoft Defender pour point de terminaison sur Mac](mac-preferences.md).

## <a name="macos-kernel-and-system-extensions"></a>Extensions système et noyau macOS

À compter de macOS 11 (Big Sur), Microsoft Defender pour point de terminaison a été entièrement migré de l’extension de noyau vers les extensions système. L’extension de noyau est toujours utilisée sur macOS 10.15 (Catalina).

## <a name="resources"></a>Ressources

- Pour plus d’informations sur la journalisation, la désinstallation ou d’autres rubriques, consultez [Ressources pour Microsoft Defender pour point de terminaison sur Mac](mac-resources.md).
- [Confidentialité des Microsoft Defender pour point de terminaison sur Mac](mac-privacy.md).
- [Activer la protection réseau pour macOS](network-protection-macos.md)
