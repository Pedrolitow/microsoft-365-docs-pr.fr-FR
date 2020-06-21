---
title: Nouvelle application Microsoft Edge
description: ''
keywords: navigateur, bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 0602d7c6afef6190578268c78994b43ac60d0d2f
ms.sourcegitcommit: 3119b2246001ba06af8264508785352dfb894166
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44820678"
---
# <a name="new-microsoft-edge-app"></a>Nouvelle application Microsoft Edge

Le nouveau [navigateur Microsoft Edge](https://www.microsoft.com/edge) offre des performances de qualité internationale en matière de confidentialité, de productivité et de valeur ajoutée pendant que vous parcourez. Microsoft Managed Desktop offre une préversion publique du déploiement du nouveau navigateur Edge dans votre environnement.

## <a name="initial-deployment"></a>Déploiement initial

Pour migrer vos appareils de bureau gérés Microsoft vers le nouveau navigateur Microsoft Edge, défichierz un ticket de support informatique via le portail de bureau géré Microsoft. Nous allons déployer le canal stable Edge dans le groupe de test lorsque vous fichier, puis le déployer dans chaque groupe de déploiement suivant toutes les 24 heures. Pour suspendre le déploiement, fichier autre ticket demandant les opérations à conserver.

## <a name="updates-to-microsoft-edge"></a>Mises à jour de Microsoft Edge

Microsoft Managed Desktop déploie le [canal stable](https://docs.microsoft.com/deployedge/microsoft-edge-channels#stable-channel) de Microsoft Edge qui est mis à jour automatiquement toutes les six semaines. Les mises à jour sur le canal stable sont déployées [progressivement](https://docs.microsoft.com/deployedge/microsoft-edge-update-progressive-rollout) par le groupe de produits Microsoft Edge afin de garantir une meilleure expérience aux clients. Le canal Microsoft Edge bêta n’est pas disponible actuellement.

Pour vous assurer que les mises à jour Microsoft Edge sont correctes, ne modifiez pas les [stratégies de mise à jour](https://docs.microsoft.com/deployedge/microsoft-edge-update-policies)Microsoft Edge.

## <a name="settings-managed-by-microsoft-managed-desktop"></a>Paramètres gérés par le bureau géré Microsoft

Microsoft Managed Desktop a créé un ensemble de stratégies par défaut pour Microsoft Edge afin de sécuriser le navigateur. Les paramètres du navigateur par défaut sont les suivants :

### <a name="microsoft-edge-extensions"></a>Extensions Microsoft Edge

La sécurité Baseline de Microsoft Edge sur les périphériques de bureau gérés Microsoft définit deux stratégies pour désactiver toutes les extensions chrome et sécuriser les utilisateurs finaux. Pour activer et déployer des extensions dans votre environnement, voir paramètres que vous gérez. 

#### <a name="extension-installation-blocklist"></a>Blocage de l’installation des extensions
**Valeur par défaut :** Tous les

Microsoft Managed Desktop définit cette stratégie pour empêcher les extensions chrome d’être installées sur les points de terminaison gérés. Il existe des risksassociated connus avec le modèle d’extension chrome, notamment la protection contre la perte de données, la confidentialité et d’autres risques qui peuvent compromettre les appareils. 

#### <a name="allow-user-level-native-messaging-hosts-installed-without-admin-permissions"></a>Autoriser les hôtes de messagerie natifs au niveau utilisateur (installés sans autorisations d’administrateur)

**Valeur par défaut :** Activation

Si vous désactivez cette stratégie, Microsoft Edge utilisera uniquement les hôtes de messagerie natif installés au niveau du système. Les hôtes de messagerie natifs font partie des extensions chrome qui permettent au navigateur d’interagir avec d’autres parties du point de terminaison de l’utilisateur, créant ainsi de nombreux problèmes de sécurité.  

### <a name="secure-sockets-layer-ssl"></a>SSL (Secure Sockets Layer)

#### <a name="minimum-ssl-version"></a>Version SSL minimale

**Valeur par défaut :** Minimum TLS 1,2 pris en charge

Si vous souhaitez utiliser le chiffrement TLS 1,1 moins sécurisé, vous pouvez demander ceci.

#### <a name="allows-users-to-proceed-from-the-ssl-warning-page"></a>Permet aux utilisateurs de continuer à partir de la page d’avertissement SSL

**Valeur par défaut :** Activation

Il n’est pas recommandé d’activer ce paramètre, car il permet aux utilisateurs de visiter des sites avec des erreurs SSL.

### <a name="microsoft-defender-smart-screen"></a>Écran intelligent Microsoft Defender

#### <a name="configure-microsoft-defender-smartscreen"></a>Configurer Microsoft Defender SmartScreen

**Valeur par défaut :** Activé

Activé par défaut pour protéger les utilisateurs finaux.

#### <a name="microsoft-defender-smartscreen-prompts-for-sites"></a>Invites Microsoft Defender SmartScreen pour les sites

**Valeur par défaut :** Activé

Nous vous déconseillons de désactiver ce paramètre car cela permettrait aux utilisateurs d’ignorer les avertissements et de continuer à des sites potentiellement malveillants.

#### <a name="prevent-bypassing-of-microsoft-defender-smartscreen-warnings-about-downloads"></a>Empêcher le contournement des avertissements Microsoft Defender SmartScreen concernant les téléchargements

**Valeur par défaut :** Activé

Nous vous déconseillons de désactiver ce paramètre car cela permettrait aux utilisateurs d’ignorer les avertissements et d’effectuer des téléchargements non vérifiés.

### <a name="adobe-flash"></a>Adobe Flash

#### <a name="default-adobe-flash-setting"></a>Paramètre Adobe Flash par défaut

**Valeur par défaut :** Activation

Il n’est pas recommandé d’utiliser flash en raison des risques de sécurité associés. Si vous avez encore des processus qui dépendent d’un flash, définissez la stratégie **[PluginsAllowedForUrls](https://docs.microsoft.com/deployedge/microsoft-edge-policies#pluginsallowedforurls)** pour activer Flash pour les sites qui en ont besoin. Si ne peut pas conserver une liste autorisée de sites pour utiliser Flash, déposez une demande de modification pour modifier la valeur **sur Cliquer pour lire**, ce qui permet aux utilisateurs de choisir le moment approprié pour exécuter Flash.

### <a name="password-manager"></a>Gestionnaire de mots de passe

#### <a name="enable-saving-passwords-to-the-password-manager"></a>Activer l’enregistrement des mots de passe dans le gestionnaire de mots de passe

**Valeur par défaut :** Activation

Nous vous déconseillons d’autoriser les utilisateurs finaux à enregistrer les mots de passe sur leur appareil.

### <a name="other-settings"></a>Autres paramètres

#### <a name="enable-site-isolation-for-every-site"></a>Activer l’isolation de site pour chaque site

**Valeur par défaut :** Activé

Lorsque cette stratégie est activée, les utilisateurs ne peuvent pas désactiver le comportement par défaut dans lequel chaque site s’exécute dans son propre processus.

#### <a name="supported-authentication-schemes"></a>Modèles d’authentification pris en charge

**Valeur par défaut :** NTLM, Negotiate

Microsoft Managed Desktop ne prend pas en charge les schémas d’authentification de base ou Digest.

#### <a name="automatically-import-another-browsers-data-and-settings-at-first-run"></a>Importer automatiquement les données et les paramètres d’un autre navigateur lors de la première exécution

**Valeur par défaut :** Importer automatiquement tous les types de données et les paramètres pris en charge à partir du navigateur par défaut 

Une fois cette stratégie appliquée, l’expérience de première exécution ignorera la section d’importation, réduisant ainsi les interactions avec l’utilisateur. Les données de navigateur des versions antérieures de Microsoft Edge seront toujours migrées silencieusement lors de la première exécution, quel que soit ce paramètre. 


## <a name="settings-you-manage"></a>Paramètres que vous gérez

Vous pouvez déployer n’importe quel paramètre de serveur de pointe non décrit précédemment à l’aide du profil des modèles d’administration dans Microsoft Intune. Pour plus d’informations, reportez-vous à la rubrique [configure Microsoft Edge Policy Settings with Microsoft Intune](https://docs.microsoft.com/deployedge/configure-edge-with-intune). Si vous souhaitez évaluer une stratégie qui n’est pas actuellement incluse dans les modèles d’administration Microsoft Edge dans Intune, vous pouvez utiliser des paramètres personnalisés pour les appareils Windows 10 dans Intune.

### <a name="enabling-specific-chrome-extensions"></a>Activation d’extensions de chrome spécifiques

Le modèle d’administration offre un paramètre permettant de déployer des extensions chrome spécifiques avec Microsoft Intune. Vous pouvez le trouver dans **configuration de l’ordinateur > extensions Microsoft Edge > > autoriser l’installation d’extensions spécifiques**.

### <a name="install-extensions-silently"></a>Installer les extensions en mode silencieux

Vous pouvez également utiliser le modèle d’administration pour configurer Microsoft Edge de sorte qu’il installe les extensions sans alerter l’utilisateur. Vous pouvez le trouver dans **configuration de l’ordinateur > extensions de > Microsoft Edge > contrôler les extensions installées**de manière silencieuse.

### <a name="other-common-enterprise-policies"></a>Autres stratégies d’entreprise courantes

Microsoft Edge offre un grand nombre de stratégies supplémentaires. Voici quelques-uns des plus courants :
 
- [Configurer des sites sur la liste de sites d’entreprise et le mode IE](https://docs.microsoft.com/deployedge/edge-ie-mode-sitelist)
- [Configurer les paramètres de démarrage, de page d’accueil et de nouvelle page d’onglets](https://docs.microsoft.com/deployedge/microsoft-edge-policies#startup-home-page-and-new-tab-page)
- [Configurer le paramètre de jeu de surf](https://docs.microsoft.com/deployedge/microsoft-edge-policies#allowsurfgame)
- [Configurer les paramètres du serveur proxy](https://docs.microsoft.com/deployedge/microsoft-edge-policies#proxy-server)

