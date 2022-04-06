---
title: Étape 2. Corriger votre premier incident
description: Comment commencer à corriger votre premier incident dans Microsoft 365 Defender.
keywords: incidents, alertes, examiner, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, courrier électronique, 365, microsoft, m365, réponse aux incidents, cyber-attaque
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 827b22ea2fb5e0864157dfae6748aa97ee4baf29
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499944"
---
# <a name="step-2-remediate-your-first-incident"></a>Étape 2. Corriger votre premier incident

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Microsoft 365 Defender fournit non seulement des fonctionnalités de détection et d’analyse, mais également de contenir et d’éradication des programmes malveillants. Le contenu inclut des étapes pour réduire l’impact de l’attaque, tandis que l’éradication garantit que toutes les traces d’activité de l’attaquant sont supprimées du réseau. Microsoft 365 Defender propose plusieurs actions de correction qui peuvent être configurées pour corriger automatiquement [](m365d-autoir.md) en fonction du système d’exploitation des appareils concernés et du type d’attaque.

Microsoft 365 Defender propose plusieurs actions de correction que les analystes peuvent lancer manuellement. Les actions sont séparées en deux catégories : Actions sur les appareils et actions sur les fichiers. Certaines actions peuvent être utilisées pour arrêter immédiatement la menace, tandis que d’autres actions aident à une analyse plus approfondie de l’investigation.

## <a name="actions-on-devices"></a>Actions sur des appareils

- **Isoler** l’appareil : cette activité bloque immédiatement tout le trafic réseau (internet et interne) pour réduire la propagation des programmes malveillants et permettre aux analystes de poursuivre l’analyse sans qu’un acteur malveillant puisse poursuivre une attaque. La seule connexion autorisée est le cloud du service Microsoft Defender pour l’identité afin que Microsoft Defender pour l’identité puisse continuer à surveiller l’appareil. 
- **Restreindre l’exécution** de l’application : pour empêcher l’exécution d’une application, une stratégie d’intégrité du code est appliquée, qui autorise uniquement l’exécution des fichiers s’ils sont signés par un certificat émis par Microsoft. Cette méthode de restriction permet d’empêcher une personne malveillante de contrôler des appareils compromis et d’effectuer d’autres activités malveillantes.
- **Exécuter une analyse antivirus** : une analyse Antivirus Microsoft Defender peut s’exécuter avec d’autres solutions antivirus, que l’Antivirus Defender soit ou non la solution antivirus active. Si un autre produit fournisseur d’antivirus est la solution de protection de point de terminaison principale, vous pouvez exécuter l’Antivirus Defender en mode passif.
- **Lancer une enquête automatisée** : vous pouvez démarrer une nouvelle enquête automatisée à usage général sur l’appareil. Pendant l’exécution d’un examen, toute autre alerte générée à partir de l’appareil est ajoutée à un examen automatisé en cours jusqu’à ce que l’examen soit terminé. En outre, si la même menace est vue sur d’autres appareils, ces appareils sont ajoutés à l’examen.
- **Lancer une réponse en direct** : la réponse en direct est une fonctionnalité qui vous permet d’accéder instantanément à un appareil à l’aide d’une connexion Shell distante. Cela vous permet d’approfondir votre travail d’investigation et de prendre des mesures de réponse immédiates pour contenir rapidement les menaces identifiées en temps réel. La réponse dynamique est conçue pour améliorer les enquêtes en vous permettant de collecter des données d’investigation, d’exécuter des scripts, d’envoyer des entités suspectes pour analyse, de corriger les menaces et de chercher de manière proactive les menaces émergentes.
- **Collecter un package d’examen** : dans le cadre du processus d’examen ou de réponse, vous pouvez collecter un package d’enquête à partir d’un appareil. En collectant le package d’examen, vous pouvez identifier l’état actuel de l’appareil et mieux comprendre les outils et techniques utilisés par l’attaquant. 
- Consultez un expert en menaces (disponible dans Actions sur les appareils et les fichiers) : vous pouvez consulter un **expert** microsoft en matière de menaces pour obtenir plus d’informations sur les appareils potentiellement compromis ou ceux qui sont déjà compromis. Les experts microsoft en matière de menaces peuvent être impliqués directement à partir Microsoft 365 Defender pour obtenir une réponse précise et rapide. 

## <a name="actions-on-files"></a>Actions sur les fichiers

- **Arrêter et mettre en quarantaine un** fichier : cette action inclut l’arrêt des processus en cours d’exécution, la mise en quarantaine des fichiers et la suppression de données persistantes, telles que les clés de Registre. Cette action prend effet sur les appareils avec Windows 11 ou Windows 10, version 1703 ou ultérieure, où le fichier a été observé au cours des 30 derniers jours. 
- **Ajoutez des indicateurs pour bloquer** ou autoriser les fichiers : empêchez toute propagation supplémentaire d’une attaque dans votre organisation en interdit les fichiers potentiellement malveillants ou les programmes malveillants suspects. Cette opération empêche la lecture, l’écriture ou l’exécution du fichier sur les appareils de votre organisation.
- **Télécharger ou collecter un fichier** : cette action permet aux analystes de télécharger un fichier dans un fichier d’archive protégé .zip mot de passe pour une analyse plus approfondie par l’organisation.
- **Analyse approfondie** : cette action exécute un fichier dans un environnement cloud sécurisé et entièrement instrumenté. Les résultats de l’analyse approfondie montrent les activités du fichier, les comportements observés et les artefacts associés, tels que les fichiers supprimés, les modifications du Registre et la communication avec les adresses IP. 

En continuant l’exemple [dans Détecter, trier](first-incident-analyze.md#analyze-your-first-incident) et analyser les incidents, un analyste peut corriger cet incident avec les actions ci-après :

1. Réinitialiser immédiatement le mot de passe du compte d’utilisateur
2. Isoler l’appareil dans Microsoft 365 Defender jusqu’à ce que l’analyse approfondie soit terminée
3. Vérifier que le fichier malveillant a été mis en quarantaine à partir SharePoint
4. Vérifier les points de terminaison affectés par les programmes malveillants
5. Reconstruire des systèmes
6. Recherchez des alertes Microsoft Defender pour les applications cloud similaires pour d’autres utilisateurs
7. Créer un indicateur personnalisé dans Microsoft Defender pour le point de terminaison pour bloquer une adresse IP tor
8. Créez une action de gouvernance dans Microsoft Defender pour les applications cloud pour ce type d’alerte, comme celui illustré dans l’image suivante :

   :::image type="content" source="../../media/first-incident-remediate/first-incident-mcas-governance.png" alt-text="Actions de gouvernance dans le portail Microsoft Defender pour les applications cloud" lightbox="../../media/first-incident-remediate/first-incident-mcas-governance.png":::

La plupart des actions de correction peuvent être appliquées et suivis dans Microsoft 365 Defender.

## <a name="using-playbooks"></a>Utilisation de playbooks

En outre, des corrections automatisées peuvent être créées à l’aide de manuels. Actuellement, Microsoft dispose [de modèles Playbook GitHub](https://github.com/microsoft/Microsoft-Cloud-App-Security/tree/master/Playbooks) qui fournissent des manuels pour les scénarios suivants :

- Supprimer le partage de fichiers sensibles après avoir demandé la validation de l’utilisateur
- Alertes de pays peu fréquentes de tri automatique
- Demander une action du responsable avant de désactiver un compte
- Désactiver les règles de boîte de réception malveillantes

Les playbooks utilisent Power Automate pour créer des flux d’automatisation de processus automatisés personnalisés afin d’automatiser certaines activités une fois que des critères spécifiques ont été déclenchés. Les organisations peuvent créer des manuels à partir de modèles existants ou à partir de zéro. 

Voici un exemple.
 
:::image type="content" source="../../media/first-incident-remediate/first-incident-power-automate.png" alt-text="Flux d Power Automate processus automatisé personnalisé" lightbox="../../media/first-incident-remediate/first-incident-power-automate.png"::: 
 
Les playbooks peuvent également être créés lors de [la révision post-incident](first-incident-post.md) pour créer des actions de correction à partir d’incidents résolus. 

## <a name="next-step"></a>Étape suivante

[![Étape 3 : Découvrez comment effectuer une révision post-incident d’un incident.](../../media/first-incident-overview/first-incident-path-step3.png)](first-incident-post.md)

Découvrez comment effectuer [une révision post-incident d’un incident](first-incident-post.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
