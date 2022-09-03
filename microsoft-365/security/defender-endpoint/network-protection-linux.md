---
title: Utiliser la protection réseau pour empêcher les connexions Linux à des sites incorrects
description: Protéger votre réseau en empêchant les utilisateurs Linux d’accéder à des adresses réseau malveillantes et suspectes connues
keywords: Protection réseau, exploits Linux, site web malveillant, ip, domaine, domaines, commande et contrôle, SmartScreen, notification toast
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde
manager: dansimp
ms.custom: asr
ms.subservice: mde
ms.topic: overview
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: ee3b78a3cdb03cb652478f68f965c43d022f8633
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67581117"
---
# <a name="network-protection-for-linux"></a>Protection réseau pour Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

## <a name="overview"></a>Vue d’ensemble

Microsoft apporte des fonctionnalités de protection réseau à Linux.

La protection réseau permet de réduire la surface d’attaque de vos appareils à partir d’événements basés sur Internet. Il empêche les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux susceptibles d’héberger :

- hameçonnage
- Exploits
- autres contenus malveillants sur Internet

La protection réseau étend l’étendue de Microsoft Defender [SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview.md) pour bloquer tout le trafic HTTP sortant qui tente de se connecter à des sources de faible réputation. Les blocs sur le trafic HTTP sortant sont basés sur le domaine ou le nom d’hôte.

## <a name="web-content-filtering-for-linux"></a>Filtrage de contenu web pour Linux

Vous pouvez utiliser le filtrage de contenu web pour les tests avec la protection réseau pour Linux. Consultez [le filtrage de contenu Web](web-content-filtering.md).

### <a name="known-issues"></a>Problèmes connus

- La protection réseau est implémentée en tant que tunnel de réseau privé virtuel (VPN). Des options avancées de routage de paquets à l’aide de scripts nftables/iptables personnalisés sont disponibles.
- L’expérience utilisateur Bloquer/Avertir n’est pas disponible
  - Les commentaires des clients sont collectés pour améliorer davantage la conception

> [!NOTE]
> Pour évaluer l’efficacité de Linux Web Threat Protection, nous vous recommandons d’utiliser le navigateur Firefox, qui est la valeur par défaut pour toutes les distributions.

### <a name="prerequisites"></a>Prerequisites

- Licences : Microsoft Defender pour point de terminaison locataire (peut être une version d’évaluation) et des exigences spécifiques à la plateforme trouvées dans [Microsoft Defender pour point de terminaison pour les plateformes non Windows](non-windows.md#licensing-requirements)
- Machines intégrées :
  - **Version Minimale de Linux** : pour obtenir la liste des distributions prises en charge, consultez [Microsoft Defender pour point de terminaison sur Linux](microsoft-defender-endpoint-linux.md).
  - **Microsoft Defender pour point de terminaison version du client Linux** : 101.78.13 -insiderSlow(préversion)

## <a name="instructions"></a>Instructions

Déployer Linux manuellement, voir [Déployer Microsoft Defender pour point de terminaison sur Linux manuellement](linux-install-manually.md)

L’exemple suivant montre la séquence de commandes nécessaire au package mdatp sur ubuntu 20.04 pour le canal insiders-Slow.

```bash
curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/20.04/insiders-slow.list 
sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-insiders-slow.list 
sudo apt-get install gpg 
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add - 
sudo apt-get install apt-transport-https 
sudo apt-get update 
sudo apt install -y mdatp 
```

### <a name="device-onboarding"></a>Intégration d’appareils

Pour intégrer l’appareil, vous devez télécharger le package d’intégration Python pour le serveur Linux à partir de Microsoft 365 Defender -> Settings -> Gestion des appareils -> Onboarding and run :

```bash
sudo python3 MicrosoftDefenderATPOnboardingLinuxServer.py 
```

### <a name="manually-enable-network-protection"></a>Activer manuellement la protection réseau

1. Activez la fonctionnalité « networkProtection », modifiez « /etc/opt/microsoft/mdatp/wdacfg » et **définissez networkProtection** sur **activé**.  
2. Redémarrez le service mdatp en exécutant la commande suivante :

```bash
sudo systemctl restart mdatp 
```
> :::image type="content" source="images/network-protection-linux-mdatp-restart.png" alt-text="Affiche le redémarrage mdatp Linux." lightbox="images/network-protection-linux-mdatp-restart.png":::

### <a name="configure-the-enforcement-level"></a>Configurer le niveau d’application

La protection réseau est désactivée par défaut, mais elle peut être configurée pour s’exécuter dans l’un des modes suivants (également appelés niveaux d’application) :

- **Audit** : utile pour s’assurer qu’il n’affecte pas les applications métier ou avoir une idée de la fréquence à laquelle les blocs se produisent
- **Bloquer** : la protection réseau empêche la connexion à des sites web malveillants
- **Désactivé** : tous les composants associés à la protection réseau sont désactivés

```bash
sudo mdatp config network-protection enforcement-level --value block
```

ou

```bash
sudo mdatp config network-protection enforcement-level --value audit
```

Pour vérifier que la protection réseau a bien démarré, exécutez la commande suivante à partir du terminal ; vérifiez qu’il imprime « démarré » :

```bash
mdatp health --field network_protection_status
```

### <a name="validation"></a>Validation

R. Vérifiez que la protection réseau a un effet sur les sites toujours bloqués :

- [http://www.smartscreentestratings2.net](http://www.smartscreentestratings2.net)
- [https://www.smartscreentestratings2.net](https://www.smartscreentestratings2.net)
- [http://malw-090-0-1.phsh-005-0-1.smartscreentestratings.com/](http://malw-090-0-1.phsh-005-0-1.smartscreentestratings.com/)

B. Inspecter les journaux de diagnostic

```bash
$ sudo mdatp log level set --level debug 
$ sudo tail -f /var/log/microsoft/mdatp/microsoft_defender_np_ext.log 
```

#### <a name="to-exit-the-validation-mode"></a>Pour quitter le mode de validation

Désactivez la protection réseau et redémarrez la connexion réseau :

```bash
$ sudo mdatp config network-protection enforcement-level --value disabled
```

## <a name="advanced-configuration"></a>Configuration avancée

Par défaut, la protection réseau Linux est active sur la passerelle par défaut ; le routage et le tunneling sont configurés en interne.
Pour personnaliser les interfaces réseau, modifiez le paramètre **networkSetupMode** à partir du fichier de configuration **/opt/microsoft/mdatp/conf/**  et redémarrez le service :

```bash
sudo systemctl restart  mdatp 
```

Le fichier de configuration permet également à l’utilisateur de personnaliser :

- paramètre proxy
- Magasins de certificats SSL
- nom de l’appareil de tunneling
- IP
- et bien plus encore

Les valeurs par défaut ont été testées pour toutes les distributions, comme décrit dans [Microsoft Defender pour point de terminaison sur Linux](microsoft-defender-endpoint-linux.md)

### <a name="microsoft-defender-portal"></a>Portail Microsoft Defender

Assurez-vous également que dans **les points de terminaison des paramètres** >  **Microsoft Defender** > ,**les fonctionnalités avancées** >  activées par le bouton bascule **« Indicateurs réseau personnalisés »** sont _activées_.

> [!IMPORTANT]
> Le bouton bascule **« Indicateurs réseau personnalisés » ci-dessus** contrôle l’activation **des indicateurs personnalisés** **pour TOUTES les plateformes prenant en charge la protection réseau, y compris Windows. Rappel : pour que les indicateurs soient appliqués sur Windows, vous devez également activer explicitement la protection réseau.

>:::image type="content" source="images/network-protection-linux-defender-security-center-advanced-features-settings.png" alt-text="MEM - Créer un profil" lightbox="images/network-protection-linux-defender-security-center-advanced-features-settings.png":::

## <a name="how-to-explore-the-features"></a>Comment explorer les fonctionnalités

1. Découvrez comment [protéger votre organisation contre les menaces web](web-threat-protection.md) à l’aide de la protection contre les menaces web.
   - La protection contre les menaces web fait partie de la protection web dans Microsoft Defender pour point de terminaison. Il utilise la protection réseau pour sécuriser vos appareils contre les menaces web.
2. Exécutez le flux [Indicateurs personnalisés de compromission](indicator-ip-domain.md) pour obtenir des blocs sur le type d’indicateur personnalisé.
3. Explorez le [filtrage de contenu web](web-content-filtering.md).
   > [!NOTE]
   > Si vous supprimez une stratégie ou modifiez des groupes d’appareils en même temps, cela peut entraîner un retard dans le déploiement de la stratégie.
   > Conseil pro : vous pouvez déployer une stratégie sans sélectionner de catégorie sur un groupe d’appareils. Cette action crée une stratégie d’audit uniquement pour vous aider à comprendre le comportement de l’utilisateur avant de créer une stratégie de blocage.
4. [Intégrez Microsoft Defender pour point de terminaison à Defender pour Cloud Apps](/defender-cloud-apps/mde-integration) et vos appareils macOS compatibles avec la protection réseau disposeront de fonctionnalités d’application de stratégie de point de terminaison.
   > [!NOTE]
   > La découverte et d’autres fonctionnalités ne sont actuellement pas prises en charge sur ces plateformes.

## <a name="scenarios"></a>Scénarios

Les scénarios suivants sont pris en charge pendant la préversion publique :

### <a name="web-threat-protection"></a>Protection contre les menaces web

La protection contre les menaces web fait partie de la protection web dans Microsoft Defender pour point de terminaison. Il utilise la protection réseau pour sécuriser vos appareils contre les menaces web. En s’intégrant à Microsoft Edge et à des navigateurs tiers populaires comme Chrome et Firefox, la protection contre les menaces web arrête les menaces web sans proxy web. La protection contre les menaces web peut protéger les appareils lorsqu’ils sont en local ou en déplacement. La protection contre les menaces web arrête l’accès aux types de sites suivants :

- sites de hameçonnage
- vecteurs de programmes malveillants
- sites exploit
- sites non approuvés ou à faible réputation
- sites que vous avez bloqués dans votre liste d’indicateurs personnalisés

>:::image type="content" source="images/network-protection-reports-web-protection.png" alt-text="La protection web signale les détections de menaces web." lightbox="images/network-protection-reports-web-protection.png":::

Pour plus d’informations, consultez [Protéger votre organisation contre les menaces web](web-threat-protection.md)

#### <a name="custom-indicators-of-compromise"></a>Indicateurs personnalisés de compromission  

L’indicateur de compromission est une fonctionnalité essentielle dans chaque solution de protection des points de terminaison. Cette fonctionnalité permet à SecOps de définir une liste d’indicateurs pour la détection et le blocage (prévention et réponse).

Créez des indicateurs qui définissent la détection, la prévention et l’exclusion des entités. Vous pouvez définir l’action à entreprendre, ainsi que la durée d’application de l’action et l’étendue du groupe d’appareils auquel l’appliquer.

Les sources actuellement prises en charge sont le moteur de détection cloud de Defender pour point de terminaison, le moteur d’investigation et de correction automatisé et le moteur de prévention des points de terminaison (Antivirus Microsoft Defender).

>:::image type="content" source ="images/network-protection-add-url-domain-indicator.png" alt-text="Affiche l’indicateur d’ajout d’URL ou de domaine par la protection réseau." lightbox="images/network-protection-add-url-domain-indicator.png":::

Pour plus d’informations, consultez : [Créer des indicateurs pour les adresses IP et les URL/domaines](indicator-ip-domain.md).

### <a name="web-content-filtering"></a>Filtrage du contenu web

Le filtrage de contenu web fait partie des fonctionnalités de [protection web](web-protection-overview.md) dans Microsoft Defender pour point de terminaison et Microsoft Defender pour entreprises. Le filtrage de contenu web permet à votre organisation de suivre et de réglementer l’accès aux sites web en fonction de leurs catégories de contenu. La plupart de ces sites Web (même s’ils ne sont pas malveillants) peuvent être problématiques en raison des réglementations de conformité, de l’utilisation de la bande passante ou d’autres problèmes.

Configurez des stratégies entre vos groupes d’appareils pour bloquer certaines catégories. Le blocage d’une catégorie empêche les utilisateurs des groupes d’appareils spécifiés d’accéder aux URL associées à la catégorie. Pour toute catégorie qui n’est pas bloquée, les URL sont automatiquement auditées. Vos utilisateurs peuvent accéder aux URL sans interruption, et vous collectez des statistiques d’accès pour vous aider à créer une décision de stratégie plus personnalisée. Vos utilisateurs verront une notification de blocage si un élément de la page qu’ils consultent effectue des appels à une ressource bloquée.

Le filtrage de contenu web est disponible sur les principaux navigateurs web, avec des blocs exécutés par Windows Defender SmartScreen (Microsoft Edge) et Network Protection (Chrome, Firefox, Brave et Opera). Pour plus d’informations sur la prise en charge des [navigateurs, consultez Prérequis](#prerequisites).

> :::image type="content" source="images/network-protection-wcf-add-policy.png" alt-text="Affiche la stratégie d’ajout de filtrage de contenu web de protection réseau." lightbox="images/network-protection-wcf-add-policy.png":::

Pour plus d’informations sur la création de rapports, consultez [le filtrage de contenu Web](web-content-filtering.md).

### <a name="microsoft-defender-for-cloud-applications"></a>Microsoft Defender pour applications cloud

Microsoft Defender pour applications cloud /Cloud App Catalog identifie les applications que vous souhaitez avertir les utilisateurs finaux lors de l’accès avec Microsoft 365 Defender pour point de terminaison, et les marque comme _surveillées_. Les domaines répertoriés sous les applications surveillées seront synchronisés ultérieurement pour Microsoft 365 Defender pour le point de terminaison :

> :::image type="content" source="images/network-protection-macos-mcas-monitored-apps.png" alt-text="Affiche les applications supervisées par mcas de protection réseau." lightbox="images/network-protection-macos-mcas-monitored-apps.png":::

Dans un délai de 10 à 15 minutes, ces domaines sont répertoriés dans Microsoft 365 Defender pour Endpoint Security Center sous Indicateurs > URL/domaines avec Action=Warn. Dans le contrat SLA d’application (voir les détails à la fin de cet article).

> :::image type="content" source="images/network-protection-macos-mcas-cloud-app-security.png" alt-text="Affiche la sécurité des applications cloud mcas de protection réseau." lightbox="images/network-protection-macos-mcas-cloud-app-security.png":::

## <a name="see-also"></a>Voir aussi

- [Protéger votre réseau](network-protection.md)
- [Activer la protection du réseau](enable-network-protection.md)
- [Protection web](web-protection-overview.md)
- [Créer des indicateurs](manage-indicators.md)
- [Filtrage du contenu web](web-content-filtering.md)
- [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
