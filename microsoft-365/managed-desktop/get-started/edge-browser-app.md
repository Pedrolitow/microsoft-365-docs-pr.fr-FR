---
title: Microsoft Edge
description: Explique comment le navigateur Microsoft Edge est déployé et mis à jour
keywords: navigateur, Microsoft Manged Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: aab02ec260f0131ab32d28834152f50b84abce21
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2022
ms.locfileid: "62444604"
---
# <a name="microsoft-edge"></a>Microsoft Edge

[Microsoft Edge](https://www.microsoft.com/edge) des performances et des valeurs de premier niveau avec :

- Plus de confidentialité et de protection contre les menaces externes.
- Un accès plus rapide à la productivité Office applications, fichiers, sites et Recherche Microsoft.
- Expérience transparente grâce à la synchronisation entre vos appareils avec la prise en charge et les profils sur plusieurs plateformes.

> [!IMPORTANT]
> L’application de bureau Internet Explorer 11 sera retirée et ne sera plus prise en charge le 15 juin 2022 (pour obtenir la liste des applications dans l’étendue, consultez la [FAQ](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/internet-explorer-11-desktop-app-retirement-faq/ba-p/2366549). Les mêmes applications et sites Internet Explorer 11 que vous utilisez aujourd’hui peuvent s’ouvrir dans Microsoft Edge en mode Internet Explorer. [Pour plus d’informations, voir ici](https://blogs.windows.com/windowsexperience/2021/05/19/the-future-of-internet-explorer-on-windows-10-is-in-microsoft-edge/).

## <a name="updates-to-microsoft-edge"></a>Mises à jour de Microsoft Edge

Microsoft Manged Desktop déploie le [canal stable](/deployedge/microsoft-edge-channels#extended-stable-channel) étendu de Microsoft Edge, qui est automatiquement mis à jour toutes les huit semaines. Les mises à jour sur le canal stable étendu sont déployées [](/deployedge/microsoft-edge-update-progressive-rollout) progressivement par le groupe de produits Microsoft Edge pour garantir la meilleure expérience pour les clients.

Le [canal bêta](/deployedge/microsoft-edge-channels#beta-channel) est déployé sur les appareils du groupe test pour une validation représentative au sein de l’organisation. Ce canal est entièrement pris en charge et automatiquement mis à jour avec de nouvelles fonctionnalités environ toutes les quatre semaines.

> [!IMPORTANT]
> Pour vous assurer que Microsoft Edge mises à jour sont correctes, ne modifiez pas les stratégies Microsoft Edge [de mise à jour.](/deployedge/microsoft-edge-update-policies)

## <a name="settings-managed-by-microsoft-managed-desktop"></a>Paramètres géré par Microsoft Manged Desktop

Microsoft Manged Desktop a créé un ensemble de stratégies par défaut pour Microsoft Edge pour sécuriser le navigateur. Les paramètres de navigateur par défaut sont les suivants :

### <a name="microsoft-edge-extensions"></a>Microsoft Edge extensions

La ligne de base de sécurité Microsoft Edge sur Microsoft Manged Desktop définit deux stratégies pour désactiver toutes les extensions Chrome et sécuriser les utilisateurs. Pour activer et déployer des extensions dans votre environnement, voir Paramètres [gérer](#settings-you-manage).

| Paramètres | Valeur par défaut | Description |
| ------ | ------ | ------ |
| Liste de blocage d’installation d’extension | Tous | Microsoft Manged Desktop cette stratégie pour empêcher l’installation des extensions Chrome sur les points de terminaison gérés. Il existe des risques connus associés au modèle d’extension Chromium, notamment la protection contre la perte de données, la confidentialité et d’autres risques qui peuvent compromettre les appareils. |
| Autoriser les hôtes de messagerie native au niveau de l’utilisateur (installés sans autorisations d’administrateur) | Désactivé | En désactivant cette stratégie, Microsoft Edge utilisera uniquement les hôtes de messagerie natifs installés au niveau du système. Les hôtes de messagerie native font partie des extensions Chrome, qui permettent au navigateur d’interagir avec d’autres parties du point de terminaison de l’utilisateur, ce qui crée divers problèmes de sécurité. |

### <a name="secure-sockets-layer-tlsssl"></a>Secure Sockets Layer (TLS/SSL)

| Paramètres | Valeur par défaut | Description
| ------ | ------ | ------ |
| Version TLS minimale | Minimum TLS 1.2 pris en charge | Si vous souhaitez utiliser le TLS 1.1 moins sécurisé, vous pouvez déposer une demande pour le faire. |
| Autoriser les utilisateurs à passer de la page d’avertissement SSL | Désactivé | Nous vous déconseillons d’activer ce paramètre, car il permet aux utilisateurs de visiter des sites avec des erreurs TSL. |

### <a name="microsoft-defender-smartscreen"></a>Microsoft Defender SmartScreen

| Paramètres | Valeur par défaut | Description
| ------ | ------ | ------ |
| Configurer Windows Defender SmartScreen | Activé | Activée par défaut pour protéger les utilisateurs. |
| Windows Defender’invites SmartScreen pour les sites | Activé | Nous vous déconseillons de désactiver ce paramètre, car cela permettrait aux utilisateurs d’ignorer les avertissements et de continuer à se rendre sur des sites potentiellement malveillants. |
| Empêcher le contournement des avertissements Windows Defender SmartScreen concernant les téléchargements | Activé | Nous vous déconseillons de désactiver ce paramètre, car cela permettrait aux utilisateurs d’ignorer les avertissements et d’effectuer des téléchargements non vérifiées. |

### <a name="adobe-flash"></a>Adobe Flash

| Paramètres | Valeur par défaut | Description
| ------ | ------ | ------ |
| Paramètre Adobe Flash par défaut | Désactivé | Nous vous déconseillons d’utiliser Flash en raison des risques de sécurité associés. <br><br> Si vous avez encore des processus qui dépendent de Flash, définissez la stratégie **[PluginsAllowedForUrls](/deployedge/microsoft-edge-policies#pluginsallowedforurls)** pour activer Flash pour les sites qui en ont besoin. Si vous ne pouvez pas gérer une liste autorisée de sites pour utiliser Flash, déposez une demande de modification pour modifier la valeur sur **Click to Play**, ce qui permet aux utilisateurs de choisir quand il convient d’exécuter Flash. |

### <a name="password-manager"></a>Gestionnaire de mots de passe

| Paramètres | Valeur par défaut | Description
| ------ | ------ | ------ |
| Activer l’enregistrement des mots de passe dans le gestionnaire de mots de passe | Désactivé | Le gestionnaire des mots de passe est désactivé par défaut. Si vous souhaitez activer cette fonctionnalité, déposez une demande de support et nos ingénieurs de service peuvent activer le paramètre dans votre environnement. |

### <a name="internet-explorer-mode-in-microsoft-edge"></a>Mode Internet Explorer dans Microsoft Edge

Le mode Internet Explorer sur Microsoft Edge facilite l’utilisation de tous les sites dont votre organisation a besoin dans un seul navigateur. Il utilise le moteur de Chromium intégré pour les sites compatibles avec le moteur de rendu Chromium web. Microsoft Edge utilise le moteur Trident MSHTML d’Internet Explorer 11 (IE11) pour les sites qui ne sont pas ou qui ont des dépendances sur les fonctionnalités d’Internet Explorer. [En savoir plus](/DeployEdge/edge-ie-mode)

Microsoft Manged Desktop active le mode Internet Explorer pour vos appareils par défaut.

| Paramètres | Valeur par défaut | Description
| ------ | ------ | ------ |
| Intégration du mode Internet Explorer | Mode Internet Explorer | Par défaut, les appareils sont définies pour utiliser le mode Internet Explorer, mais vous pouvez les configurer pour ouvrir des sites dans une fenêtre Internet Explorer 11 autonome à la place. Pour modifier ce comportement, déposez une demande de support. |
| Ajouter des sites à la liste Enterprise sites en mode d’accès | Voir la description | Pour que les sites s’ouvrent en mode Internet Explorer, vous devez les inclure dans la [liste Enterprise sites.](/DeployEdge/edge-ie-mode-sitelist) Il vous incombe de gérer et de déployer Enterprise liste des sites. Pour plus d’informations, voir [Configure using the Configure Enterprise Mode Site List policy](/DeployEdge/edge-ie-mode-policies#configure-using-the-configure-the-enterprise-mode-site-list-policy). |

### <a name="other-settings"></a>Autres paramètres

| Paramètres | Valeur par défaut | Description
| ------ | ------ | ------ |
| Activer l’isolation de site pour chaque site | Activé | Lorsque cette stratégie est activée, les utilisateurs ne peuvent pas refuser le comportement par défaut dans lequel chaque site s’exécute dans son propre processus. |
| Schémas d’authentification pris en charge | NTLM, Négocier | Microsoft Manged Desktop ne prend pas en charge les schémas d’authentification de base ou Digest. |
| Importer automatiquement les données et paramètres d’un autre navigateur lors de la première application | Importer automatiquement tous les types de données et paramètres pris en charge à partir du navigateur par défaut. | Avec cette stratégie appliquée, l’expérience de première utilisation ignore la section d’importation, réduisant ainsi l’interaction utilisateur. Les données de navigateur provenant d’anciennes versions Microsoft Edge seront toujours migrées en mode silencieux lors de la première utilisation, quel que soit ce paramètre. |

## <a name="settings-you-manage"></a>Paramètres vous gérez

Vous pouvez déployer tous les paramètres Microsoft Edge qui n’ont pas été précédemment décrits à l’aide du profil Modèles d’administration dans Microsoft Intune. Pour plus d’informations, [voir Configure Microsoft Edge policy settings with Microsoft Intune](/deployedge/configure-edge-with-intune). Si vous souhaitez évaluer une stratégie qui n’est pas actuellement incluse dans les modèles d’administration Microsoft Edge dans Intune, vous pouvez utiliser des paramètres personnalisés pour les appareils Windows 10 dans Intune.

| Setting | Description
| ------ | ------ |
| Activer des extensions Chrome spécifiques | Le modèle d’administration offre un paramètre pour déployer des extensions Chrome particulières avec Microsoft Intune. Vous pouvez le trouver dans **configuration ordinateur > Microsoft Edge > extensions > autoriser l’installation d’extensions spécifiques**. |
| Installer les extensions en mode silencieux | Vous pouvez également utiliser le modèle d’administration pour définir Microsoft Edge pour installer des extensions sans avertir l’utilisateur. Vous pouvez le trouver dans **les extensions > Microsoft Edge > configuration ordinateur > contrôler les extensions installées en mode silencieux**. |
| Microsoft Edge de mise à jour | Pour vous assurer que Microsoft Edge mises à jour sont correctes, ne modifiez pas les stratégies Microsoft Edge [de mise à jour.](/deployedge/microsoft-edge-update-policies) |
| Autres stratégies d’entreprise courantes | Microsoft Edge offre de nombreuses autres stratégies. Voici quelques-unes des plus courantes : <ul> <li> [Configurer des sites sur la liste Enterprise sites et le mode IE](/deployedge/edge-ie-mode-sitelist)</li><li> [Configurer les paramètres de démarrage, de page d’accueil et de page nouvel onglet](/deployedge/microsoft-edge-policies#startup-home-page-and-new-tab-page)</li> <li> [Configurer le paramètre du jeu](/deployedge/microsoft-edge-policies#allowsurfgame)</li> <li> [Configurer les paramètres du serveur proxy](/deployedge/microsoft-edge-policies#proxy-server)</li></ul>
