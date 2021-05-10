---
title: Configurer les Antivirus Microsoft Defender avec la stratégie de groupe
description: Découvrez comment utiliser une stratégie de groupe pour configurer et gérer les Antivirus Microsoft Defender sur vos points de terminaison dans Microsoft Defender for Endpoint.
keywords: stratégie de groupe, GPO, configuration, paramètres
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 05/08/2021
ms.reviewer: ksarens, jtoole, pahuijbr
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.openlocfilehash: 74f58959c22313806ebc95aef14e8ccb2d75326b
ms.sourcegitcommit: 58d74ff60303a879e35d112f10f79724ba41188f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2021
ms.locfileid: "52302099"
---
# <a name="use-group-policy-settings-to-configure-and-manage-microsoft-defender-antivirus"></a>Utiliser les paramètres de stratégie de groupe pour configurer et gérer les Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez utiliser [la stratégie de](/windows/win32/srvnodes/group-policy) groupe pour configurer et gérer les Antivirus Microsoft Defender sur vos points de terminaison.

## <a name="configure-microsoft-defender-antivirus-using-group-policy"></a>Configurer les Antivirus Microsoft Defender à l’aide de la stratégie de groupe

En règle générale, vous pouvez utiliser la procédure suivante pour configurer ou modifier Antivirus Microsoft Defender de stratégie de groupe :

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. À **l’aide de l’Éditeur de gestion des stratégies de** groupe, go to **Computer configuration**.

3. Cliquez **sur Modèles d’administration.**

4. Développez l’arborescence **Windows composants**  >  **Antivirus Microsoft Defender**.

5. Développez la section (appelée Emplacement dans le tableau de cette rubrique) qui contient le paramètre que vous souhaitez configurer, double-cliquez sur le paramètre pour l’ouvrir et a apporté des modifications de configuration. 

6. [Déployez l’GPO mis à jour comme vous le faites normalement.](/windows/win32/srvnodes/group-policy) 

## <a name="group-policy-settings-and-resources"></a>Ressources et paramètres de stratégie de groupe

Le tableau suivant de cette rubrique répertorie les paramètres de stratégie de groupe disponibles dans Windows 10, version 1703 et fournit des liens vers la rubrique appropriée dans cette bibliothèque de documentation (le cas échéant). 

> [!TIP]
> Téléchargez la feuille de calcul Paramètres de référence de la stratégie de groupe pour Windows 10 mise à jour de mai [2020 (2004)](https://www.microsoft.com/download/101451). Cette feuille de calcul répertorie les paramètres de stratégie pour les configurations des ordinateurs et des utilisateurs qui sont inclus dans les fichiers de modèles d’administration remis pour la mise à jour Windows 10 mai 2020 (2004). Vous pouvez configurer la référence à la feuille de calcul lorsque vous modifiez des objets de stratégie de groupe.

| Emplacement | Paramètre | Article |
|:---|:---|:---|
| Interface client | Activer le mode d’interface utilisateur sans en-tête | [Empêcher les utilisateurs de voir ou d’interagir avec l Antivirus Microsoft Defender’interface utilisateur](prevent-end-user-interaction-microsoft-defender-antivirus.md) |
| Interface client | Afficher du texte supplémentaire pour les clients lorsqu’ils doivent effectuer une action | [Configurer les notifications qui apparaissent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md) |
| Interface client | Supprimer toutes les notifications | [Configurer les notifications qui apparaissent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md) |
| Interface client | Supprime les notifications de redémarrage | [Configurer les notifications qui apparaissent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md) |
| Exclusions | Exclusions d’extensions | [Configurer et valider des exclusions dans Antivirus Microsoft Defender analyses](configure-exclusions-microsoft-defender-antivirus.md) |
| Exclusions | Exclusions de chemins d’accès | [Configurer et valider des exclusions dans Antivirus Microsoft Defender analyses](configure-exclusions-microsoft-defender-antivirus.md) |
| Exclusions | Exclusions de processus | [Configurer et valider des exclusions dans Antivirus Microsoft Defender analyses](configure-exclusions-microsoft-defender-antivirus.md) | 
| Exclusions | Désactiver les exclusions automatiques | [Configurer et valider des exclusions dans Antivirus Microsoft Defender analyses](configure-exclusions-microsoft-defender-antivirus.md) |
| MAPS | Configurer la fonctionnalité « Bloquer à la première vue » | [Activer bloquer à la première vue](configure-block-at-first-sight-microsoft-defender-antivirus.md) |
| MAPS | Rejoindre Microsoft MAPS | [Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) |
| MAPS | Envoyer des exemples de fichiers lorsque des analyses plus approfondies sont requises | [Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) |
| MAPS | Configurer le remplacement de paramètre local pour la création de rapports à Microsoft MAPS | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| MpEngine | Configurer la vérification cloud étendue | [Configurer le délai de blocage du cloud](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md) |
| MpEngine | Sélectionner le niveau de protection cloud | [Spécifier le niveau de protection pour le cloud](specify-cloud-protection-level-microsoft-defender-antivirus.md) |
| Système d’inspection du réseau | Spécifier des ensembles de définitions supplémentaires pour l’inspection du trafic réseau | [Spécifier des ensembles de définitions supplémentaires pour l’inspection du trafic réseau](specify-additional-definitions-network-traffic-inspection-mdav.md) |
| Système d’inspection du réseau | Activer le retrait des définitions | [Configurer le retrait des définitions](turn-on-definition-retirement.md)  |
| Système d’inspection du réseau | Activer la reconnaissance de protocole | [Activer la reconnaissance de protocole](turn-on-protocol-recognition.md)  |
| Quarantaine | Configurer le remplacement de paramètre local pour la suppression des éléments du dossier de mise en quarantaine | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Quarantaine | Configurer la suppression des éléments du dossier de mise en quarantaine | [Configurer la correction pour Antivirus Microsoft Defender analyses](configure-remediation-microsoft-defender-antivirus.md) |
| Protection en temps réel | Configurer le remplacement des paramètres locaux pour surveiller l’activité des fichiers et des programmes sur votre ordinateur | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Protection en temps réel | Configurer le remplacement de paramètre local pour la surveillance de l’activité des fichiers entrants et sortants | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Protection en temps réel | Configurer le remplacement de paramètre local pour l’analyse de tous les fichiers et pièces jointes téléchargés | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Protection en temps réel | Configurer le remplacement de paramètre local pour activer l’analyse du comportement | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Protection en temps réel | Configurer le remplacement de paramètre local pour activer la protection en temps réel | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Protection en temps réel | Définir la taille maximale des fichiers et pièces jointes téléchargés à scanner | [Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Protection en temps réel | Surveiller l’activité des fichiers et des programmes sur votre ordinateur | [Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Protection en temps réel | Analyser tous les fichiers et pièces jointes téléchargés | [Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Protection en temps réel | Désactiver la protection en temps réel | [Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Protection en temps réel | Activer l’analyse du comportement | [Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Protection en temps réel | Activer l’analyse des processus chaque fois que la protection en temps réel est activée | [Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Protection en temps réel | Activer les notifications d’écriture de volume brut | [Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Protection en temps réel | Configurer la surveillance de l’activité des fichiers et des programmes entrants et sortants | [Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Correction | Configurer le remplacement de paramètre local pour l’heure de la journée afin d’exécuter une analyse complète programmée pour terminer la correction | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Correction | Spécifier le jour de la semaine pour exécuter une analyse complète programmée afin de terminer la correction | [Configurer des analyses de Antivirus Microsoft Defender programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Correction | Spécifier l’heure de la journée pour exécuter une analyse complète programmée afin de terminer la correction | [Configurer des analyses de Antivirus Microsoft Defender programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Reporting | Désactiver les notifications améliorées | [Configurer les notifications qui apparaissent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)
| Root | Désactiver la Antivirus Microsoft Defender | Non utilisé (ce paramètre  doit être configuré sur Non configuré pour s’assurer que les applications antivirus tierces installées fonctionnent correctement)
| Root | Définir des adresses pour contourner le serveur proxy | Inutilisé |
| Root | Définir la connexion automatique du proxy (.pac) pour la connexion au réseau | Inutilisé |
| Root | Définir un serveur proxy pour la connexion au réseau | Inutilisé |
| Root | Configurer le comportement de fusion de l’administrateur local pour les listes | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Root | Autoriser le démarrage du service anti-programme malveillant avec une priorité normale | [Configurer la correction pour Antivirus Microsoft Defender analyses](configure-remediation-microsoft-defender-antivirus.md) |
| Root | Autoriser le service anti-programme malveillant à rester en cours d’exécution | [Configurer la correction pour Antivirus Microsoft Defender analyses](configure-remediation-microsoft-defender-antivirus.md) |
| Root | Désactiver la correction de routine | [Configurer la correction pour Antivirus Microsoft Defender analyses](configure-remediation-microsoft-defender-antivirus.md) |
| Root | Randomize scheduled task times | [Configurer des analyses programmées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Analyser | Autoriser les utilisateurs à suspendre l’analyse | [Empêcher les utilisateurs de voir ou d’interagir avec Antivirus Microsoft Defender’interface utilisateur](prevent-end-user-interaction-microsoft-defender-antivirus.md) (non pris en charge Windows 10) |
| Analyser | Recherchez les dernières définitions de virus et de logiciels espions avant d’exécution d’une analyse programmée | [Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md) |
| Analyser | Définir le nombre de jours après lesquels une analyse de rattrapage est forcée | [Gérer les mises à jour des points de terminaison qui ne sont plus à jour](manage-outdated-endpoints-microsoft-defender-antivirus.md) |
| Analyser | Activer l’analyse complète de rattrapage | [Gérer les mises à jour des points de terminaison qui ne sont plus à jour](manage-outdated-endpoints-microsoft-defender-antivirus.md) |
| Analyser | Activer l’analyse rapide de rattrapage | [Gérer les mises à jour des points de terminaison qui ne sont plus à jour](manage-outdated-endpoints-microsoft-defender-antivirus.md) |
| Analyser | Configurer le remplacement de paramètre local pour le pourcentage maximal d’utilisation du processeur | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Analyser | Configurer le remplacement de paramètre local pour le jour de l’analyse de planification | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Analyser | Configurer le remplacement de paramètre local pour le temps d’analyse rapide programmé | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Analyser | Configurer le remplacement de paramètre local pour l’heure d’analyse programmée | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Analyser | Configurer le remplacement de paramètre local pour le type d’analyse à utiliser pour une analyse programmée | [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) |
| Analyser | Créer un point de restauration du système | [Configurer la correction pour Antivirus Microsoft Defender analyses](configure-remediation-microsoft-defender-antivirus.md) |
| Analyser | Activer la suppression des éléments du dossier d’historique d’analyse | [Configurer la correction pour Antivirus Microsoft Defender analyses](configure-remediation-microsoft-defender-antivirus.md) |
| Analyser | Activer l’heuristique | [Activer et configurer Antivirus Microsoft Defender protection et surveillance toujours actives](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Analyser | Activer l’analyse du courrier électronique | [Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Analyser | Activer l’analyse des points d’analyse | [Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Analyser | Exécuter une analyse complète sur des lecteurs réseau mappés | [Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Analyser | Analyser les fichiers d’archive | [Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Analyser | Analyser les fichiers réseau | [Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Analyser | Analyser les exécutables packés | [Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Analyser | Analyser les lecteurs amovibles | [Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Analyser | Spécifier la profondeur maximale pour analyser les fichiers d’archivage | [Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Analyser | Spécifier le pourcentage maximal d’utilisation du processeur pendant une analyse | [Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Analyser | Spécifier la taille maximale des fichiers d’archivage à scanner | [Configurer les options d’analyse dans Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Analyser | Spécifier le jour de la semaine pour exécuter une analyse programmée | [Configurer des analyses programmées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Analyser | Spécifier l’intervalle pour exécuter des analyses rapides par jour | [Configurer des analyses programmées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Analyser | Spécifier le type d’analyse à utiliser pour une analyse programmée | [Configurer des analyses programmées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Analyser | Spécifier l’heure d’une analyse rapide quotidienne | [Configurer des analyses programmées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Analyser | Spécifier l’heure de la journée pour exécuter une analyse programmée | [Configurer des analyses programmées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Analyser | Démarrer l’analyse programmée uniquement lorsque l’ordinateur est en cours d’utilisation | [Configurer des analyses programmées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Autoriser les mises à jour des informations de sécurité à partir de Microsoft Update | [Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Autoriser les mises à jour d’informations de sécurité lors de l’exécution sur batterie | [Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Autoriser les notifications à désactiver les rapports basés sur des définitions pour Microsoft MAPS | [Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Autoriser les mises à jour d’informations de sécurité en temps réel basées sur des rapports à Microsoft MAPS | [Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Recherchez les dernières définitions de virus et de logiciels espions au démarrage | [Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Définir des partages de fichiers pour le téléchargement des mises à jour d’informations de sécurité | [Gérer les mises à jour Antivirus Microsoft Defender protection et d’intelligence de la sécurité](manage-protection-updates-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Définir le nombre de jours après lesquels une mise à jour de l’intelligence de sécurité de rattrapage est requise | [Gérer les mises à jour des points de terminaison qui ne sont pas à jour](manage-outdated-endpoints-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Définir le nombre de jours avant que les définitions de logiciels espions ne soient considérées comme non à jour | [Gérer les mises à jour des points de terminaison qui ne sont pas à jour](manage-outdated-endpoints-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Définir le nombre de jours avant que les définitions de virus soient considérées comme non à jour | [Gérer les mises à jour des points de terminaison qui ne sont pas à jour](manage-outdated-endpoints-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Définir l’ordre des sources pour le téléchargement des mises à jour de l’intelligence de la sécurité | [Gérer les mises à jour Antivirus Microsoft Defender protection et d’intelligence de la sécurité](manage-protection-updates-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Lancer la mise à jour des informations de sécurité au démarrage | [Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Spécifier le jour de la semaine pour vérifier les mises à jour des informations de sécurité | [Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Spécifier l’intervalle pour vérifier les mises à jour des informations de sécurité | [Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Spécifier l’heure de recherche des mises à jour de l’intelligence de la sécurité | [Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md) |
| Mises à jour de l’intelligence de la sécurité | Activer l’analyse après la mise à jour des informations de sécurité | [Configurer des analyses programmées pour Antivirus Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Menaces | Spécifier les niveaux d’alerte contre les menaces pour lesquels aucune action par défaut ne doit être prise lorsqu’elle est détectée | [Configurer la correction pour Antivirus Microsoft Defender analyses](configure-remediation-microsoft-defender-antivirus.md) |
| Menaces | Spécifier les menaces sur lesquelles l’action par défaut ne doit pas être prise lorsqu’elle est détectée | [Configurer la correction pour Antivirus Microsoft Defender analyses](configure-remediation-microsoft-defender-antivirus.md) |

## <a name="see-also"></a>Voir aussi

- [Rubriques de référence pour les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
