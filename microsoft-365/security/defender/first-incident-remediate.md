---
title: Étape 2. Corriger votre premier incident
description: Comment commencer à corriger votre premier incident dans Microsoft 365 Defender.
keywords: incidents, alertes, examen, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyberattaque
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
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
- m365solution-firstincident
- highpri
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 63c9e47f30e113a6b79e0b290d19b8fe9e9a6399
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67482293"
---
# <a name="step-2-remediate-your-first-incident"></a>Étape 2. Corriger votre premier incident

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Microsoft 365 Defender fournit non seulement des fonctionnalités de détection et d’analyse, mais également la maîtrise et l’éradication des programmes malveillants. L’endiguement comprend des étapes pour réduire l’impact de l’attaque, tandis que l’éradication garantit que toutes les traces de l’activité de l’attaquant sont supprimées du réseau. Microsoft 365 Defender propose plusieurs actions de correction qui peuvent être configurées pour corriger [automatiquement](m365d-autoir.md) en fonction du système d’exploitation des appareils affectés et du type d’attaque.

Microsoft 365 Defender propose plusieurs actions de correction que les analystes peuvent lancer manuellement. Les actions sont séparées en deux catégories : Actions sur les appareils et actions sur les fichiers. Certaines actions peuvent être utilisées pour arrêter immédiatement la menace, tandis que d’autres permettent d’approfondir l’analyse judiciaire.

## <a name="actions-on-devices"></a>Actions sur des appareils

- **Isoler l’appareil** : cette activité bloque immédiatement tout le trafic réseau (Internet et interne) pour réduire la propagation des programmes malveillants et permettre aux analystes de poursuivre l’analyse sans qu’un acteur malveillant puisse poursuivre une attaque. La seule connexion autorisée est au cloud de service Microsoft Defender pour Identity afin que Microsoft Defender pour Identity puisse continuer à surveiller l’appareil. 
- **Restreindre l’exécution de l’application** : pour empêcher l’exécution d’une application, une stratégie d’intégrité du code est appliquée qui autorise uniquement l’exécution des fichiers s’ils sont signés par un certificat émis par Microsoft. Cette méthode de restriction peut aider à empêcher un attaquant de contrôler les appareils compromis et d’effectuer d’autres activités malveillantes.
- **Exécuter l’analyse antivirus** : une analyse antivirus Microsoft Defender peut s’exécuter en même temps que d’autres solutions antivirus, que Defender Antivirus soit ou non la solution antivirus active. Si un autre produit du fournisseur d’antivirus est la solution principale de protection des points de terminaison, vous pouvez exécuter l’antivirus Defender en mode passif.
- **Lancer une investigation automatisée** : vous pouvez démarrer une nouvelle enquête automatisée à usage général sur l’appareil. Pendant l’exécution d’une enquête, toute autre alerte générée à partir de l’appareil est ajoutée à une enquête automatisée en cours jusqu’à ce que cette enquête soit terminée. En outre, si la même menace est visible sur d’autres appareils, ces appareils sont ajoutés à l’enquête.
- **Lancer une réponse en direct** : la réponse en direct est une fonctionnalité qui vous donne un accès instantané à un appareil à l’aide d’une connexion d’interpréteur de commandes distante. Cela vous donne la possibilité d’effectuer un travail d’investigation approfondi et de prendre des mesures de réponse immédiates pour contenir rapidement les menaces identifiées en temps réel. La réponse dynamique est conçue pour améliorer les investigations en vous permettant de collecter des données légales, d’exécuter des scripts, d’envoyer des entités suspectes à des fins d’analyse, de corriger les menaces et de rechercher de manière proactive les menaces émergentes.
- **Collecter le package d’enquête** : dans le cadre du processus d’investigation ou de réponse, vous pouvez collecter un package d’enquête à partir d’un appareil. En collectant le package d’investigation, vous pouvez identifier l’état actuel de l’appareil et mieux comprendre les outils et techniques utilisés par l’attaquant. 
- **Consultez un expert en menaces** (disponible à la fois dans Actions sur les appareils et les fichiers) : vous pouvez consulter un expert en menaces Microsoft pour obtenir plus d’informations sur les appareils ou appareils potentiellement compromis qui sont déjà compromis. Les experts en menaces Microsoft peuvent être engagés directement à partir de Microsoft 365 Defender pour une réponse rapide et précise. 

## <a name="actions-on-files"></a>Actions sur les fichiers

- **Arrêter et mettre en quarantaine un fichier** : cette action inclut l’arrêt des processus en cours d’exécution, la mise en quarantaine des fichiers et la suppression de données persistantes, telles que toutes les clés de Registre. Cette action prend effet sur les appareils avec Windows 11 ou Windows 10, version 1703 ou ultérieure, où le fichier a été observé au cours des 30 derniers jours. 
- **Ajouter des indicateurs pour bloquer ou autoriser un fichier** : empêchez la propagation d’une attaque dans votre organisation en interdisant les fichiers potentiellement malveillants ou les programmes malveillants suspects. Cette opération empêche la lecture, l’écriture ou l’exécution du fichier sur les appareils de votre organisation.
- **Télécharger ou collecter un fichier** : cette action permet aux analystes de télécharger un fichier dans un fichier d’archive protégé par mot de passe .zip pour une analyse plus approfondie par l’organisation.
- **Analyse approfondie** : cette action exécute un fichier dans un environnement cloud sécurisé et entièrement instrumenté. Les résultats d’analyse approfondie montrent les activités du fichier, les comportements observés et les artefacts associés, tels que les fichiers supprimés, les modifications de Registre et la communication avec les adresses IP. 

En poursuivant l’exemple de [détection, de triage et d’analyse des incidents](first-incident-analyze.md#analyze-your-first-incident), un analyste peut corriger cet incident avec les actions suivantes :

1. Réinitialiser immédiatement le mot de passe du compte d’utilisateur
2. Isoler l’appareil dans Microsoft 365 Defender jusqu’à ce que l’analyse approfondie soit terminée
3. Vérifier que le fichier malveillant a été mis en quarantaine à partir de SharePoint
4. Vérifier quels points de terminaison ont été affectés par des programmes malveillants
5. Reconstruire des systèmes
6. Rechercher des alertes de Microsoft Defender for Cloud Apps similaires pour d’autres utilisateurs
7. Créer un indicateur personnalisé dans Microsoft Defender pour point de terminaison pour bloquer une adresse IP Tor
8. Créez une action de gouvernance dans Microsoft Defender for Cloud Apps pour ce type d’alerte, comme dans l’image suivante :

   :::image type="content" source="../../media/first-incident-remediate/first-incident-mcas-governance.png" alt-text="Actions de gouvernance dans le portail Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-remediate/first-incident-mcas-governance.png":::

La plupart des actions de correction peuvent être appliquées et suivies dans Microsoft 365 Defender.

## <a name="using-playbooks"></a>Utilisation de playbooks

En outre, la correction automatisée peut être créée à l’aide de playbooks. Actuellement, Microsoft dispose de [modèles de playbook sur GitHub](https://github.com/microsoft/Microsoft-Cloud-App-Security/tree/master/Playbooks) qui fournissent des playbooks pour les scénarios suivants :

- Supprimer le partage de fichiers sensibles après avoir demandé la validation de l’utilisateur
- Triage automatique des alertes de pays peu fréquentes
- Demander l’action du gestionnaire avant de désactiver un compte
- Désactiver les règles de boîte de réception malveillantes

Les playbooks utilisent Power Automate pour créer des flux d’automatisation de processus robotisés personnalisés afin d’automatiser certaines activités une fois que des critères spécifiques ont été déclenchés. Les organisations peuvent créer des playbooks à partir de modèles existants ou à partir de zéro. 

Voici un exemple.
 
:::image type="content" source="../../media/first-incident-remediate/first-incident-power-automate.png" alt-text="Un flux d’automatisation de processus robotisés personnalisé Power Automate" lightbox="../../media/first-incident-remediate/first-incident-power-automate.png"::: 
 
Des playbooks peuvent également être créés lors de la [révision post-incident](first-incident-post.md) pour créer des actions de correction à partir d’incidents résolus. 

## <a name="next-step"></a>Étape suivante

Découvrez comment [effectuer une révision post-incident d’un incident](first-incident-post.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
