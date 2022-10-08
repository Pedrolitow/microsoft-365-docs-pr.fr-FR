---
title: Utiliser la protection réseau pour empêcher les connexions macOS à des sites incorrects
description: Protéger votre réseau en empêchant les utilisateurs macOS d’accéder à des adresses réseau malveillantes et suspectes connues
keywords: Protection réseau, exploits MacOS, site web malveillant, ip, domaine, domaines, commande et contrôle, SmartScreen, notification toast
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
- m365-security
- tier2
ms.date: ''
search.appverid: met150
ms.openlocfilehash: 3617ae81204d6c2e244d58868fad6fe7d315f29e
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68229083"
---
# <a name="network-protection-for-macos"></a>Protection réseau pour macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Microsoft 365 Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Microsoft 365 Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

## <a name="overview"></a>Vue d’ensemble

Microsoft apporte la fonctionnalité de protection réseau à macOS (min. macOS 11).

La protection microsoft network permet de réduire la surface d’attaque de vos appareils à partir d’événements basés sur Internet. Il empêche les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux susceptibles d’héberger :

- hameçonnage
- Exploits
- autres contenus malveillants sur Internet

La protection réseau étend l’étendue de Microsoft 365 Defender [SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview.md) pour bloquer tout le trafic HTTP sortant qui tente de se connecter à des sources de faible réputation. Les blocs sur le trafic HTTP sortant sont basés sur le domaine ou le nom d’hôte.

## <a name="new-and-updated-capabilities"></a>Fonctionnalités nouvelles et mises à jour

- Vous pouvez exécuter votre VPN d’entreprise en tandem ou « côte à côte » avec la protection réseau. Actuellement, aucun conflit VPN n’est identifié. Si vous rencontrez des conflits, vous pouvez fournir des commentaires via le canal de commentaires répertorié en bas de cette page.
  - Le filtrage de contenu web est pris en charge avec la protection réseau pour macOS.  
  - Si la protection réseau est configurée et active sur l’appareil, les stratégies de filtrage de contenu web (WCF) créées dans le portail MDEP sont respectées dans les navigateurs, notamment Chromium Microsoft Edge pour macOS. Le filtrage de contenu web dans Microsoft Edge sur Mac nécessite actuellement une protection réseau ; D’autres fonctionnalités E5, telles que Microsoft Defender pour les applications cloud ou les indicateurs personnalisés, nécessitent actuellement une protection réseau.

### <a name="known-issues"></a>Problèmes connus

- L’expérience utilisateur Bloquer/Avertir n’est pas personnalisable et peut nécessiter d’autres changements d’apparence
  - Les commentaires des clients sont collectés pour améliorer davantage la conception

### <a name="important-notes"></a>Remarques importantes

- Nous vous déconseillons de contrôler la protection réseau à partir des préférences système à l’aide du bouton Déconnecter. Utilisez plutôt l’outil en ligne de commande mdatp ou JAMF/Intune pour contrôler la protection réseau pour macOS.
- Pour évaluer l’efficacité de la protection contre les menaces web macOS, nous vous recommandons de l’essayer dans des navigateurs autres que Microsoft Edge pour macOS (par exemple, Safari). Microsoft Edge pour macOS dispose d’une protection intégrée contre les menaces web qui est activée, que la fonctionnalité de protection réseau Mac que vous évaluez soit activée ou non.

> [!NOTE]
>
> Microsoft Edge pour macOS ne prend actuellement pas en charge le filtrage de contenu web, les indicateurs personnalisés ou d’autres fonctionnalités d’entreprise. Toutefois, la protection réseau fournit cette protection à Microsoft Edge pour macOS également si la protection réseau est activée.

## <a name="prerequisites"></a>Configuration requise

- Licences : Microsoft 365 Defender pour le locataire de point de terminaison (peut être une version d’évaluation)
- Machines intégrées :
  - Version minimale de macOS : 11
  - Version du produit 101.78.13 ou ultérieure
  - Votre appareil doit se trouver dans le canal de mise à jour Microsoft AutoUpdate InsiderSlow (préversion) ou InsiderFast (bêta). Vous pouvez vérifier le canal de mise à jour à l’aide de la commande suivante :

```bash
mdatp health --field release_ring 
```

Si votre appareil n’est pas déjà dans le canal de mise à jour InsiderSlow (préversion), exécutez la commande suivante à partir du terminal. La mise à jour du canal prend effet la prochaine fois que le produit démarre (lors de l’installation de la prochaine mise à jour du produit ou du redémarrage de l’appareil).

```bash
defaults write com.microsoft.autoupdate2 ChannelName -string InsiderSlow
```

Sinon, si vous êtes dans un environnement managé (JAMF ou Intune), vous pouvez configurer le groupe d’appareils à distance. Pour plus d’informations, consultez [Définir les préférences pour Microsoft 365 Defender pour point de terminaison sur macOS](mac-preferences.md).

## <a name="deployment-instructions"></a>Instructions de déploiement

### <a name="microsoft-365-defender-for-endpoint"></a>Microsoft 365 Defender pour point de terminaison

Une fois que vous avez configuré votre appareil pour qu’il soit dans le canal de mise à jour InsiderSlow (préversion), installez la version la plus récente du produit via Microsoft AutoUpdate. Pour ouvrir Microsoft AutoUpdate, exécutez la commande suivante à partir du terminal :

```bash
open /Library/Application\ Support/Microsoft/MAU2.0/Microsoft\ AutoUpdate.app
```

Configurez le produit avec les informations de votre organisation en suivant les instructions de notre documentation publique.  

La protection réseau est désactivée par défaut, mais elle peut être configurée pour s’exécuter dans l’un des modes suivants (également appelés niveaux d’application) :

- **Audit** : utile pour s’assurer qu’il n’affecte pas les applications métier ou avoir une idée de la fréquence à laquelle les blocs se produisent
- **Bloquer** : la protection réseau empêche la connexion à des sites web malveillants
- **Désactivé** : tous les composants associés à la protection réseau sont désactivés

Vous pouvez déployer cette fonctionnalité de l’une des manières suivantes : manuellement, via JAMF ou Intune. Les sections suivantes décrivent chacune de ces méthodes en détail.

#### <a name="manual-deployment"></a>Déploiement manuel

Pour configurer le niveau d’application, exécutez la commande suivante à partir du terminal :

```bash
mdatp config network-protection enforcement-level --value [enforcement-level]
```

Par exemple, pour configurer la protection réseau de manière à ce qu’elle s’exécute en mode bloquant, exécutez la commande suivante :

```bash
mdatp config network-protection enforcement-level --value block
```

Pour vérifier que la protection réseau a bien démarré, exécutez la commande suivante à partir du terminal et vérifiez qu’elle imprime « démarré » :

```bash
mdatp health --field network_protection_status
```

#### <a name="jamf-deployment"></a>Déploiement JAMF

Un déploiement JAMF réussi nécessite un profil de configuration pour définir le niveau de mise en œuvre de la protection réseau.  
Après avoir créé ce profil de configuration, affectez-le aux appareils sur lesquels vous souhaitez activer la protection réseau.

##### <a name="configure-the-enforcement-level"></a>Configurer le niveau d’application

Remarque : Si vous avez déjà configuré Microsoft 365 Defender pour point de terminaison sur Mac à l’aide des instructions répertoriées ici, mettez à jour le fichier plist que vous avez précédemment déployé avec le contenu répertorié ci-dessous et redéployez-le à partir de JAMF.

1. Dans **Profils de configuration**  **des ordinateurs** > , sélectionnez  **Options** > **Applications & Paramètres personnalisés**
2. Sélectionner **Charger un fichier** (fichier PLIST)
3. Définir le domaine de préférence sur _com.microsoft.wdav_
4. Charger le fichier plist suivant

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd"> 
<plist version="1.0"> 
<dict> 
    <key>networkProtection</key> 
    <dict> 
        <key>enforcementLevel</key> 
        <string>block</string> 
    </dict> 
</dict> 
</plist> 
```

#### <a name="intune-deployment"></a>déploiement Intune

Un déploiement Intune réussi nécessite un profil de configuration pour définir le niveau de mise en œuvre de la protection réseau.  
Après avoir créé ce profil de configuration, affectez-le aux appareils sur lesquels vous souhaitez activer la protection réseau.

##### <a name="configure-the-enforcement-level-using-intune"></a>Configurer le niveau d’application à l’aide de Intune

> [!NOTE]
> Si vous avez déjà configuré Microsoft Defender pour point de terminaison sur Mac en suivant les instructions indiquées ici, mettez à jour le fichier plist que vous avez précédemment déployé avec le contenu répertorié ci-dessous et redéployez-le à partir de Intune.

1.  **Ouvrez Gérer** > **la configuration de l’appareil**. Sélectionnez **Gérer les** > **profils** > **Créer un profil**.
2. Spécifiez un nom pour le profil. Remplacez **Platform=macOS** par **Type de profil=Personnalisé**. Sélectionnez **Configurer**.
3. Enregistrez la charge utile suivante en tant que _com.microsoft.wdav.xml_

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
        <string>Microsoft Defender ATP settings</string> 
        <key>PayloadDescription</key> 
        <string>Microsoft Defender ATP configuration settings</string> 
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
                <string>Microsoft Defender ATP configuration settings</string> 
                <key>PayloadDescription</key> 
                <string/> 
                <key>PayloadVersion</key> 
                <integer>1</integer> 
                <key>PayloadEnabled</key> 
                <true/> 
                <key>networkProtection</key> 
                <dict> 
                    <key>enforcementLevel</key> 
                    <string>block</string> 
                </dict> 
            </dict> 
        </array> 
    </dict> 
</plist>
```

4. Vérifiez que le fichier ci-dessus a été copié correctement. À partir du terminal, exécutez la commande suivante et vérifiez qu’elle génère ok :

```bash
plutil -lint com.microsoft.wdav.xml
```

5. Entrez _com.microsoft.wdav_ comme nom de profil de configuration personnalisé.
6. Ouvrez le profil de configuration et chargez le fichier com.microsoft.wdav.xml. (Ce fichier a été créé à l’étape 3.)
7. Sélectionner **OK**
8. Sélectionnez **Gérer** > **les affectations**. Sous l’onglet **Inclure** , sélectionnez les appareils pour lesquels vous souhaitez activer la protection réseau.

## <a name="how-to-explore-the-features"></a>Comment explorer les fonctionnalités

1. Découvrez comment [protéger votre organisation contre les menaces web](web-threat-protection.md) à l’aide de la protection contre les menaces web.
   - La protection contre les menaces web fait partie de la protection web dans Microsoft Defender pour point de terminaison. Il utilise la protection réseau pour sécuriser vos appareils contre les menaces web.
2. Exécutez le flux [Indicateurs personnalisés de compromission](indicator-ip-domain.md) pour obtenir des blocs sur le type d’indicateur personnalisé.
3. Explorez le [filtrage de contenu web](web-content-filtering.md).
   > [!NOTE]
   > Si vous supprimez une stratégie ou modifiez des groupes d’appareils en même temps, cela peut entraîner un retard dans le déploiement de la stratégie.
   > Conseil pro : vous pouvez déployer une stratégie sans sélectionner de catégorie sur un groupe d’appareils. Cette action crée une stratégie d’audit uniquement pour vous aider à comprendre le comportement de l’utilisateur avant de créer une stratégie de blocage.
   >
   > La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.  

4. [Intégrez Microsoft Defender pour point de terminaison à Defender pour Cloud Apps](/defender-cloud-apps/mde-integration) et vos appareils macOS compatibles avec la protection réseau disposeront de fonctionnalités d’application de stratégie de point de terminaison.
   > [!NOTE]
   > La découverte et d’autres fonctionnalités ne sont actuellement pas prises en charge sur ces plateformes.

## <a name="scenarios"></a>Scénarios

Les scénarios suivants sont pris en charge pendant la préversion publique :

### <a name="web-threat-protection"></a>Protection contre les menaces web

La protection contre les menaces web fait partie de la protection web dans Microsoft 365 Defender pour point de terminaison. Il utilise la protection réseau pour sécuriser vos appareils contre les menaces web. En s’intégrant à Microsoft Edge pour macOS et à des navigateurs tiers populaires comme Chrome et Firefox, la protection contre les menaces web arrête les menaces web sans proxy web. La protection contre les menaces web peut protéger les appareils lorsqu’ils sont en local ou en déplacement. La protection contre les menaces web arrête l’accès aux types de sites suivants :

- sites de hameçonnage
- vecteurs de programmes malveillants
- sites exploit
- sites non approuvés ou à faible réputation
- sites que vous avez bloqués dans votre liste d’indicateurs personnalisés

:::image type="content" source="images/network-protection-reports-web-protection.png" alt-text="La protection web signale les détections de menaces web." lightbox="images/network-protection-reports-web-protection.png":::

Pour plus d’informations, consultez [Protéger votre organisation contre les menaces web](web-threat-protection.md)

### <a name="custom-indicators-of-compromise"></a>Indicateurs personnalisés de compromission  

L’indicateur de compromission est une fonctionnalité essentielle dans chaque solution de protection des points de terminaison. Cette fonctionnalité permet à SecOps de définir une liste d’indicateurs pour la détection et le blocage (prévention et réponse).

Créez des indicateurs qui définissent la détection, la prévention et l’exclusion des entités. Vous pouvez définir l’action à entreprendre, ainsi que la durée d’application de l’action et l’étendue du groupe d’appareils auquel l’appliquer.

Les sources actuellement prises en charge sont le moteur de détection cloud de Defender pour point de terminaison, le moteur d’investigation et de correction automatisé et le moteur de prévention des points de terminaison (Microsoft Defender Antivirus).

:::image type="content" source="images/network-protection-add-url-domain-indicator.png" alt-text="Affiche l’indicateur d’ajout d’URL ou de domaine de la protection réseau." lightbox="images/network-protection-add-url-domain-indicator.png":::

Pour plus d’informations, consultez : [Créer des indicateurs pour les adresses IP et les URL/domaines](indicator-ip-domain.md).

### <a name="web-content-filtering"></a>Filtrage du contenu web

Le filtrage de contenu web fait partie des fonctionnalités de [protection web](web-protection-overview.md) dans Microsoft Defender pour point de terminaison et Microsoft Defender pour entreprises. Le filtrage de contenu web permet à votre organisation de suivre et de réglementer l’accès aux sites web en fonction de leurs catégories de contenu. La plupart de ces sites Web (même s’ils ne sont pas malveillants) peuvent être problématiques en raison des réglementations de conformité, de l’utilisation de la bande passante ou d’autres problèmes.

Configurez des stratégies entre vos groupes d’appareils pour bloquer certaines catégories. Le blocage d’une catégorie empêche les utilisateurs des groupes d’appareils spécifiés d’accéder aux URL associées à la catégorie. Pour toute catégorie qui n’est pas bloquée, les URL sont automatiquement auditées. Vos utilisateurs peuvent accéder aux URL sans interruption, et vous collectez des statistiques d’accès pour vous aider à créer une décision de stratégie plus personnalisée. Vos utilisateurs verront une notification de blocage si un élément de la page qu’ils consultent effectue des appels à une ressource bloquée.

Le filtrage de contenu web est disponible sur les principaux navigateurs web, avec des blocs exécutés par la protection réseau (Safari, Chrome, Firefox, Brave et Opera). Pour plus d’informations sur la prise en charge des [navigateurs, consultez Prérequis](#prerequisites).

:::image type="content" source="images/network-protection-wcf-add-policy.png" alt-text="Affiche la stratégie d’ajout de filtrage de contenu web de protection réseau." lightbox="images/network-protection-wcf-add-policy.png":::

Pour plus d’informations sur la création de rapports, consultez [le filtrage de contenu Web](web-content-filtering.md).

### <a name="microsoft-defender-for-cloud-applications"></a>Microsoft Defender pour les applications cloud

Le Microsoft Defender pour les applications cloud /cloud app catalog identifie les applications que vous souhaitez avertir les utilisateurs finaux lors de l’accès avec Microsoft 365 Defender pour point de terminaison, et les marque comme _surveillées_. Les domaines répertoriés sous les applications surveillées seront synchronisés ultérieurement pour Microsoft 365 Defender pour le point de terminaison :

:::image type="content" source="images/network-protection-macos-mcas-monitored-apps.png" alt-text="Affiche les applications surveillées par la protection réseau.":::

Dans un délai de 10 à 15 minutes, ces domaines sont répertoriés dans Microsoft 365 Defender pour Endpoint Security Center sous Indicateurs > URL/domaines avec Action=Warn. Dans le contrat SLA d’application (voir les détails à la fin de cet article), les utilisateurs finaux recevront des messages d’avertissement lors de la tentative d’accès à ces domaines :

:::image type="content" source="images/network-protection-macos-indicators-urls-domains-warn.png" alt-text="Affiche les indicateurs de protection réseau pour l’avertissement d’URL ou de domaines.":::

Lorsque l’utilisateur final tente d’accéder aux domaines surveillés, il est averti par Microsoft 365 Defender pour point de terminaison.

- L’utilisateur bénéficie d’une expérience de bloc simple accompagnée du message toast suivant, qui sera affiché par le système d’exploitation, y compris le nom de l’application bloquée (par exemple, Blogger.com)

  :::image type="content" source="images/network-protection-macos-content-blocked.png" alt-text="Affiche la notification toast bloquée du contenu de protection réseau de l’utilisateur final.":::

Si l’utilisateur final rencontre un _blocage_, l’utilisateur aura deux résolutions possibles :

#### <a name="user-bypass"></a>Contournement de l’utilisateur

- **Pour une expérience de message toast** : appuyez sur le bouton Débloquer. En rechargeant la page web, l’utilisateur peut continuer et utiliser l’application cloud. (Cette action s’applique aux 24 prochaines heures, après quoi l’utilisateur devra débloquer à nouveau)

#### <a name="user-education"></a>Éducation des utilisateurs

- **Pour une expérience de message toast** : appuyez sur le message toast lui-même. L’utilisateur final est redirigé vers une URL de redirection personnalisée définie globalement dans Microsoft Defender pour les applications cloud (plus d’informations en bas de cette page)

> [!NOTE]
> Suivi des contournements par application** : vous pouvez suivre le nombre d’utilisateurs qui ont contourné l’avertissement dans la page _Application_ dans Microsoft Defender for Cloud Applications.

  :::image type="content" source="images/network-protection-macos-mcas-cloud-app-security.png" alt-text="Affiche la vue d’ensemble de la sécurité des applications cloud de protection réseau.":::

## <a name="appendix"></a>Annexe

### <a name="end-user-education-center-sharepoint-site-template"></a>Modèle de site SharePoint du centre d’éducation des utilisateurs finaux

Pour de nombreuses organisations, il est important de prendre les contrôles cloud fournis par Microsoft Defender pour les applications cloud, et non seulement de définir des limitations sur les utilisateurs finaux en cas de besoin, mais aussi de les former et de les entraîner sur :

- l’incident spécifique
- pourquoi cela s’est produit
- ce qui est la pensée derrière cette décision
- comment les sites de blocage peuvent être atténués

Face à un comportement inattendu, la confusion des utilisateurs peut être réduite en leur fournissant autant d’informations que possible, non seulement pour expliquer ce qui s’est passé, mais aussi pour les sensibiliser à être plus conscients la prochaine fois qu’ils choisissent une application cloud pour terminer leur travail. Par exemple, ces informations peuvent inclure :

- Stratégies et recommandations en matière de sécurité et de conformité de l’organisation pour l’utilisation d’Internet et du cloud
- Applications cloud approuvées/recommandées pour une utilisation
- Applications cloud restreintes/bloquées à utiliser

Pour cette page, nous vous recommandons d’utiliser un site SharePoint de base.  

### <a name="important-things-to-know"></a>Choses importantes à savoir

1. La propagation et la mise à jour des domaines d’application dans les appareils de point de terminaison peuvent prendre jusqu’à deux heures (généralement moins) après avoir été marqués comme _surveillés_.  
2. Par défaut, une action est effectuée pour toutes les applications et domaines qui ont été marqués comme surveillés dans Microsoft Defender pour le portail des applications cloud pour tous les points de terminaison intégrés de l’organisation.  
3. Les URL complètes ne sont actuellement pas prises en charge et ne sont pas envoyées de Microsoft Defender pour les applications cloud à Microsoft 365 Defender pour point de terminaison, si des URL complètes sont répertoriées sous Microsoft Defender  pour les applications cloud surveillées, par conséquent, l’utilisateur n’est pas averti lors d’une tentative d’accès (par exemple, google.com/drive n’est pas pris en charge, tandis que drive.google.com est pris en charge).  

Aucune notification de l’utilisateur final sur des navigateurs tiers ? Vérifier les paramètres de votre message toast

## <a name="see-also"></a>Voir aussi

- [Microsoft 365 Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
- [Microsoft 365 Defender pour l’intégration de point de terminaison à Microsoft Microsoft 365 Defender pour les applications cloud](/defender-cloud-apps/mde-integration)
- [Découvrir les fonctionnalités innovantes de Microsoft Edge](https://www.microsoft.com/edge/features)
- [Protéger votre réseau](network-protection.md)
- [Activer la protection du réseau](enable-network-protection.md)
- [Protection web](web-protection-overview.md)
- [Créer des indicateurs](manage-indicators.md)
- [Filtrage du contenu web](web-content-filtering.md)
