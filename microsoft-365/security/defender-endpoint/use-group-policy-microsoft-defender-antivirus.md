---
title: Configurer Antivirus Microsoft Defender avec stratégie de groupe
description: Découvrez comment utiliser une stratégie de groupe pour configurer et gérer des Antivirus Microsoft Defender sur vos points de terminaison dans Microsoft Defender pour point de terminaison.
keywords: stratégie de groupe, objet de stratégie de groupe, configuration, paramètres
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 01/04/2022
ms.reviewer: ksarens, jtoole, pahuijbr
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 53b24f0566b9b9d43ad725a832bb1e0fa8013923
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416373"
---
# <a name="use-group-policy-settings-to-configure-and-manage-microsoft-defender-antivirus"></a>Utiliser stratégie de groupe paramètres pour configurer et gérer Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez utiliser [stratégie de groupe](/windows/win32/srvnodes/group-policy) pour configurer et gérer Antivirus Microsoft Defender sur vos points de terminaison.

## <a name="configure-microsoft-defender-antivirus-using-group-policy"></a>Configurer Antivirus Microsoft Defender à l’aide de stratégie de groupe

En général, vous pouvez utiliser la procédure suivante pour configurer ou modifier Antivirus Microsoft Defender paramètres de stratégie de groupe :

1. Sur votre machine de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe (GPO) que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. À l’aide de **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Cliquez sur **Modèles d’administration**.

4. Développez l’arborescence pour **Windows composants** \> **Antivirus Microsoft Defender**.

5. Développez la section (appelée **Emplacement** dans le tableau de cette rubrique) qui contient le paramètre que vous souhaitez configurer, double-cliquez sur le paramètre pour l’ouvrir et apportez des modifications à la configuration.

6. [Déployez l’objet de stratégie de groupe mis à jour comme vous le faites normalement](/windows/win32/srvnodes/group-policy).

## <a name="group-policy-settings-and-resources"></a>stratégie de groupe paramètres et ressources

Le tableau suivant répertorie les paramètres stratégie de groupe couramment utilisés disponibles dans Windows 10.

> [!TIP]
> Téléchargez la feuille de calcul de référence stratégie de groupe, qui répertorie les paramètres de stratégie pour les configurations d’ordinateur et d’utilisateur incluses dans les fichiers de modèle d’administration fournis pour Windows. Vous pouvez configurer la feuille de calcul lorsque vous modifiez stratégie de groupe Objets. <br/><br/> Voici les versions les plus récentes :
> - [stratégie de groupe Paramètres feuille de calcul de référence pour Windows 10 mise à jour de mai 2020 (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [feuille de calcul de référence stratégie de groupe Paramètres pour Windows 11 mise à jour d’octobre 2021 (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

<br/><br/>

|Emplacement|Setting|Article|
|---|---|---|
|Interface client|Activer le mode d’interface utilisateur sans tête|[Empêcher les utilisateurs de voir ou d’interagir avec l’interface utilisateur Antivirus Microsoft Defender](prevent-end-user-interaction-microsoft-defender-antivirus.md)|
|Interface client|Afficher du texte supplémentaire aux clients lorsqu’ils ont besoin d’effectuer une action|[Configurer les notifications qui s’affichent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)|
|Interface client|Supprimer toutes les notifications|[Configurer les notifications qui s’affichent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)|
|Interface client|Supprime les notifications de redémarrage|[Configurer les notifications qui s’affichent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)|
|Exclusions|Exclusions d’extension|[Configurer et valider les exclusions dans les analyses Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)|
|Exclusions|Exclusions de chemin d’accès|[Configurer et valider les exclusions dans les analyses Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)|
|Exclusions|Exclusions de processus|[Configurer et valider les exclusions dans les analyses Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)|
|Exclusions|Désactiver les exclusions automatiques|[Configurer et valider les exclusions dans les analyses Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)|
|CARTES|Configurer la fonctionnalité « Bloquer à la première consultation »|[Activer le bloc à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md)|
|CARTES|Rejoindre Microsoft MAPS|[Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md)|
|CARTES|Envoyer des exemples de fichiers quand une analyse plus approfondie est requise|[Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md)|
|CARTES|Configurer le remplacement des paramètres locaux pour la création de rapports à Microsoft MAPS|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|MpEngine|Configurer la vérification cloud étendue|[Configurer le délai de blocage du cloud](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)|
|MpEngine|Sélectionner le niveau de protection cloud|[Spécifier le niveau de protection pour le cloud](specify-cloud-protection-level-microsoft-defender-antivirus.md)|
|Système d’inspection réseau|Spécifier des ensembles de définitions supplémentaires pour l’inspection du trafic réseau| Non utilisé (déconseillé) |
|Système d’inspection réseau|Activer la mise hors service des définitions| Non utilisé (déconseillé)|
|Système d’inspection réseau|Activer la reconnaissance de protocole| Non utilisé (déconseillé)|
|Quarantaine|Configurer le remplacement des paramètres locaux pour la suppression d’éléments du dossier Quarantaine|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Quarantaine|Configurer la suppression d’éléments du dossier De quarantaine|[Configurer la correction pour les analyses Antivirus Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Protection en temps réel|Configurer le remplacement des paramètres locaux pour surveiller l’activité de fichier et de programme sur votre ordinateur|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Protection en temps réel|Configurer le remplacement des paramètres locaux pour la surveillance de l’activité de fichier entrante et sortante|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Protection en temps réel|Configurer le remplacement des paramètres locaux pour l’analyse de tous les fichiers téléchargés et pièces jointes|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Protection en temps réel|Configurer le remplacement des paramètres locaux pour activer la surveillance du comportement|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Protection en temps réel|Configurer le remplacement de paramètre local pour activer la protection en temps réel|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Protection en temps réel|Définir la taille maximale des fichiers téléchargés et des pièces jointes à analyser|[Activer et configurer Antivirus Microsoft Defender protection et surveillance always-on](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Protection en temps réel|Surveiller l’activité des fichiers et des programmes sur votre ordinateur|[Activer et configurer Antivirus Microsoft Defender protection et surveillance always-on](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Protection en temps réel|Analyser tous les fichiers et pièces jointes téléchargés|[Activer et configurer Antivirus Microsoft Defender protection et surveillance always-on](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Protection en temps réel|Désactiver la protection en temps réel|[Activer et configurer Antivirus Microsoft Defender protection et surveillance always-on](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Protection en temps réel|Activer la surveillance du comportement|[Activer et configurer Antivirus Microsoft Defender protection et surveillance always-on](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Protection en temps réel|Activer l’analyse des processus chaque fois que la protection en temps réel est activée|[Activer et configurer Antivirus Microsoft Defender protection et surveillance always-on](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Protection en temps réel|Activer les notifications d’écriture de volume brut|[Activer et configurer Antivirus Microsoft Defender protection et surveillance always-on](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Protection en temps réel|Configurer la supervision pour l’activité de fichier et de programme entrante et sortante|[Activer et configurer Antivirus Microsoft Defender protection et surveillance always-on](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Assainissement|Configurer le remplacement des paramètres locaux pour l’heure de la journée afin d’exécuter une analyse complète planifiée pour terminer la correction|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Assainissement|Spécifier le jour de la semaine pour exécuter une analyse complète planifiée pour terminer la correction|[Configurer des analyses Antivirus Microsoft Defender planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Assainissement|Spécifier l’heure de la journée d’exécution d’une analyse complète planifiée pour terminer la correction|[Configurer des analyses Antivirus Microsoft Defender planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Rapports|Désactiver les notifications améliorées|[Configurer les notifications qui s’affichent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)
|Racine|Désactiver Antivirus Microsoft Defender|Non utilisé. Si vous utilisez ou envisagez d’utiliser un produit antivirus non Microsoft, consultez [Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité](microsoft-defender-antivirus-compatibility.md).|
|Racine|Définir des adresses pour contourner le serveur proxy|[Configurer les paramètres de proxy du dispositif et de connectivité Internet](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Racine|Définir la configuration automatique du proxy (.pac) pour la connexion au réseau|[Configurer les paramètres de proxy du dispositif et de connectivité Internet](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Racine|Définir le serveur proxy pour la connexion au réseau|[Configurer les paramètres de proxy du dispositif et de connectivité Internet](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Racine|Configurer le comportement de fusion de l’administrateur local pour les listes|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Racine|Autoriser le service anti-programme malveillant à démarrer avec une priorité normale|[Configurer la correction pour les analyses Antivirus Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Racine|Autoriser le service anti-programme malveillant à continuer à s’exécuter toujours|[Configurer la correction pour les analyses Antivirus Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Racine|Désactiver la correction de routine|[Configurer la correction pour les analyses Antivirus Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Racine|Durées aléatoires des tâches planifiées|[Configurer des analyses planifiées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Analyser|Autoriser les utilisateurs à suspendre l’analyse|[Empêcher les utilisateurs de voir ou d’interagir avec l’interface utilisateur Antivirus Microsoft Defender](prevent-end-user-interaction-microsoft-defender-antivirus.md) (Non pris en charge sur Windows 10)|
|Analyser|Rechercher les dernières définitions de virus et de logiciels espions avant d’exécuter une analyse planifiée|[Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Analyser|Définir le nombre de jours après lesquels une analyse de rattrapage est forcée|[Gérer les mises à jour pour les points de terminaison obsolètes](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Analyser|Activer l’analyse complète de rattrapage|[Gérer les mises à jour pour les points de terminaison obsolètes](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Analyser|Activer l’analyse rapide de rattrapage|[Gérer les mises à jour pour les points de terminaison obsolètes](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Analyser|Configurer le remplacement des paramètres locaux pour le pourcentage maximal d’utilisation du processeur|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Analyser|Configurer le remplacement des paramètres locaux pour le jour de l’analyse de planification|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Analyser|Configurer le remplacement des paramètres locaux pour le temps d’analyse rapide planifié|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Analyser|Configurer le remplacement des paramètres locaux pour l’heure d’analyse planifiée|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Analyser|Configurer le remplacement de paramètre local pour le type d’analyse à utiliser pour une analyse planifiée|[Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Analyser|Créer un point de restauration système|[Configurer la correction pour les analyses Antivirus Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Analyser|Activer la suppression d’éléments du dossier d’historique d’analyse|[Configurer la correction pour les analyses Antivirus Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Analyser|Activer l’heuristique|[Activer et configurer Antivirus Microsoft Defender protection et surveillance always-on](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Analyser|Activer l’analyse du courrier électronique|[Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Analyser|Activer l’analyse des points d’analyse|[Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Analyser|Exécuter une analyse complète sur les lecteurs réseau mappés|[Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Analyser|Analyser les fichiers d’archive|[Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Analyser|Analyser les fichiers réseau|[Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Analyser|Analyser les exécutables compressés|[Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
| Analyser | Analyser les scripts | [Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) <p>Consultez également [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender).|
|Analyser|Analyser les lecteurs amovibles|[Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Analyser|Spécifier la profondeur maximale pour analyser les fichiers d’archive|[Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Analyser|Spécifier le pourcentage maximal d’utilisation du processeur pendant une analyse|[Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Analyser|Spécifier la taille maximale des fichiers d’archive à analyser|[Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Analyser|Spécifier le jour de la semaine pour exécuter une analyse planifiée|[Configurer des analyses planifiées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Analyser|Spécifier l’intervalle pour exécuter des analyses rapides par jour|[Configurer des analyses planifiées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Analyser|Spécifier le type d’analyse à utiliser pour une analyse planifiée|[Configurer des analyses planifiées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Analyser|Spécifier l’heure d’une analyse rapide quotidienne|[Configurer des analyses planifiées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Analyser|Spécifier l’heure de la journée d’exécution d’une analyse planifiée|[Configurer des analyses planifiées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Analyser|Démarrer l’analyse planifiée uniquement lorsque l’ordinateur est activé mais qu’il n’est pas utilisé|[Configurer des analyses planifiées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Autoriser les mises à jour du renseignement de sécurité à partir de Microsoft Update|[Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Autoriser les mises à jour du renseignement de sécurité lors de l’exécution sur batterie|[Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Autoriser les notifications à désactiver les rapports basés sur des définitions dans Microsoft MAPS|[Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Autoriser les mises à jour du renseignement de sécurité en temps réel en fonction des rapports à Microsoft MAPS|[Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Rechercher les dernières définitions de virus et de logiciels espions au démarrage|[Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Définir des partages de fichiers pour le téléchargement des mises à jour du renseignement de sécurité|[Gérer Antivirus Microsoft Defender mises à jour de protection et de renseignement de sécurité](manage-protection-updates-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Définir le nombre de jours après lesquels une mise à jour du renseignement de sécurité de rattrapage est requise|[Gérer les mises à jour pour les points de terminaison obsolètes](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Définir le nombre de jours avant que les définitions de logiciels espions ne soient considérées comme obsolètes|[Gérer les mises à jour pour les points de terminaison obsolètes](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Définir le nombre de jours avant que les définitions de virus ne soient considérées comme obsolètes|[Gérer les mises à jour pour les points de terminaison obsolètes](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Définir l’ordre des sources pour le téléchargement des mises à jour du renseignement de sécurité|[Gérer Antivirus Microsoft Defender mises à jour de protection et de renseignement de sécurité](manage-protection-updates-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Lancer une mise à jour du renseignement de sécurité au démarrage|[Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Spécifier le jour de la semaine pour rechercher les mises à jour du renseignement de sécurité|[Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Spécifier l’intervalle pour rechercher les mises à jour du renseignement de sécurité|[Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Spécifier le temps nécessaire pour rechercher les mises à jour du renseignement de sécurité|[Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Mises à jour de la veille de sécurité|Activer l’analyse après la mise à jour du renseignement de sécurité|[Configurer des analyses planifiées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Menaces|Spécifier les niveaux d’alerte de menace auxquels l’action par défaut ne doit pas être effectuée lorsqu’elle est détectée|[Configurer la correction pour les analyses Antivirus Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|Menaces|Spécifier les menaces sur lesquelles l’action par défaut ne doit pas être effectuée lorsqu’elle est détectée|[Configurer la correction pour les analyses Antivirus Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="see-also"></a>Voir aussi

- [Rubriques de référence sur les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
