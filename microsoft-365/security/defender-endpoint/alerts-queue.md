---
title: Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison
description: Découvrez comment fonctionnent les files d’attente d’alertes Microsoft Defender pour point de terminaison et comment trier et filtrer des listes d’alertes.
keywords: alertes, files d’attente, file d’attente d’alertes, trier, commander, filtrer, gérer les alertes, nouveau, en cours, résolu, plus récent, heure dans la file d’attente, gravité, période, alertes d’experts en menaces Microsoft
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.topic: conceptual
ms.date: 03/27/2020
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 53bd35b7e7066a6a57765f264422b03fd8fb3336
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68629168"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-alerts-queue"></a>Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-alertsq-abovefoldlink)

La **file d’attente Alertes** affiche une liste d’alertes marquées à partir d’appareils de votre réseau. Par défaut, la file d’attente affiche les alertes affichées au cours des 30 derniers jours dans une vue groupée. Les alertes les plus récentes sont affichées en haut de la liste pour vous aider à voir les alertes les plus récentes en premier.

> [!NOTE]
> Les alertes sont considérablement réduites grâce à l’examen et à la correction automatisés, ce qui permet aux experts en opérations de sécurité de se concentrer sur des menaces plus sophistiquées et d’autres initiatives de grande valeur. Lorsqu’une alerte contient une entité prise en charge pour une investigation automatisée (par exemple, un fichier) sur un appareil doté d’un système d’exploitation pris en charge, une investigation et une correction automatisées peuvent démarrer. Pour plus d’informations sur les enquêtes automatisées, consultez [Vue d’ensemble des enquêtes automatisées](automated-investigations.md).

Vous pouvez choisir parmi plusieurs options pour personnaliser l’affichage des alertes.

En haut de la navigation, vous pouvez :

- Personnaliser des colonnes pour ajouter ou supprimer des colonnes
- Appliquer des filtres
- Afficher les alertes pour une durée particulière comme 1 jour, 3 jours, 1 semaine, 30 jours et 6 mois
- Exporter la liste d’alertes vers Excel
- Gérer les alertes

:::image type="content" source="images/alerts-queue-list.png" alt-text="Page de la file d’attente Alertes" lightbox="images/alerts-queue-list.png":::

## <a name="sort-and-filter-alerts"></a>Trier et filtrer les alertes 

Vous pouvez appliquer les filtres suivants pour limiter la liste des alertes et obtenir une vue plus ciblée des alertes.

### <a name="severity"></a>Severity

Gravité de l’alerte|Description
---|---
Élevé <br> (Rouge)|Alertes couramment vues associées à des menaces persistantes avancées (APT). Ces alertes indiquent un risque élevé en raison de la gravité des dommages qu’elles peuvent infliger aux appareils. Voici quelques exemples : activités d’outils de vol d’informations d’identification, activités de ransomware non associées à un groupe, falsification des capteurs de sécurité ou activités malveillantes indiquant un adversaire humain.
Moyen <br> (Orange)|Alertes provenant des comportements de détection et de réponse de point de terminaison post-violation qui peuvent faire partie d’une menace persistante avancée (APT). Ces comportements incluent les comportements observés typiques des phases d’attaque, les modifications anormales du Registre, l’exécution de fichiers suspects, etc. Bien que certains puissent faire partie de tests de sécurité internes, cela nécessite une investigation, car il peut également faire partie d’une attaque avancée.
Faible <br> (Jaune)|Alertes sur les menaces associées aux programmes malveillants répandus. Par exemple, les outils de piratage, les outils de piratage non malveillants, tels que l’exécution de commandes d’exploration, l’effacement des journaux, etc., qui n’indiquent souvent pas une menace avancée ciblant l’organisation. Il peut également provenir d’un outil de sécurité isolé testé par un utilisateur de votre organisation.
Informatif <br> (Gris)|Alertes qui peuvent ne pas être considérées comme dangereuses pour le réseau, mais qui peuvent conduire à une prise de conscience de la sécurité organisationnelle sur les problèmes de sécurité potentiels.

#### <a name="understanding-alert-severity"></a>Présentation de la gravité de l’alerte

Microsoft Defender gravités des alertes antivirus et Defender pour point de terminaison sont différentes, car elles représentent des étendues différentes.

Le Microsoft Defender gravité des menaces antivirus représente la gravité absolue de la menace détectée (programme malveillant) et est attribué en fonction du risque potentiel pour l’appareil individuel, s’il est infecté.

La gravité de l’alerte Defender pour point de terminaison représente la gravité du comportement détecté, le risque réel pour l’appareil, mais surtout le risque potentiel pour l’organisation.

Par exemple :

- La gravité d’une alerte Defender pour point de terminaison concernant un antivirus Microsoft Defender a détecté une menace qui a été évitée et qui n’a pas infecté l’appareil est classée comme « Informationnelle », car il n’y a pas eu de dommages réels.
- Une alerte concernant un programme malveillant commercial a été détectée lors de l’exécution, mais bloquée et corrigée par Microsoft Defender Antivirus est classée comme « Faible », car elle peut avoir causé des dommages à l’appareil individuel, mais ne présente aucune menace organisationnelle.
- Une alerte sur les programmes malveillants détectés lors de l’exécution, qui peut constituer une menace non seulement pour l’appareil individuel, mais aussi pour l’organisation, qu’elle ait finalement été bloquée, peut être classée comme « Moyen » ou « Élevé ».
- Les alertes comportementales suspectes, qui n’ont pas été bloquées ou corrigées, seront classées « Bas », « Moyen » ou « Élevé » en suivant les mêmes considérations relatives aux menaces organisationnelles.

### <a name="status"></a>État

Vous pouvez choisir de filtrer la liste des alertes en fonction de leur état.

> [!NOTE]
> Si vous voyez un état *d’alerte de type d’alerte non pris en charge* , cela signifie que les fonctionnalités d’investigation automatisée ne peuvent pas récupérer cette alerte pour exécuter une investigation automatisée. Toutefois, vous pouvez [examiner ces alertes manuellement](../defender/investigate-incidents.md#alerts).

### <a name="categories"></a>Categories

Nous avons redéfini les catégories d’alertes pour les aligner sur les [tactiques d’attaque d’entreprise](https://attack.mitre.org/tactics/enterprise/) dans la [matrice MITRE ATT&CK](https://attack.mitre.org/). Les nouveaux noms de catégorie s’appliquent à toutes les nouvelles alertes. Les alertes existantes conservent les noms de catégories précédents.

### <a name="service-sources"></a>Sources de service

Spécialistes des menaces Microsoft participants en préversion peuvent désormais filtrer et voir les détections du nouveau service de chasse géré par les experts en menaces.

Filtrez les alertes en fonction des sources de service suivantes :

- Microsoft Defender pour l’identité
- Microsoft Defender for Cloud Apps
- Microsoft Defender pour point de terminaison
- Microsoft 365 Defender
- Microsoft Defender pour Office 365
- Gouvernance des applications
- AAD Identity Protection

> [!NOTE]
> Le filtre Antivirus s’affiche uniquement si les appareils utilisent Microsoft Defender Antivirus comme produit anti-programme malveillant de protection en temps réel par défaut.

### <a name="tags"></a>Balises

Vous pouvez filtrer les alertes en fonction des balises affectées aux alertes.

### <a name="policy"></a>Stratégie 

Vous pouvez filtrer les alertes en fonction des stratégies suivantes :

|Source de détection|Valeur d’API|
|---|---|
|Capteurs tiers|ThirdPartySensors|
|Antivirus|WindowsDefenderAv|
|Investigation automatisée|AutomatedInvestigation|
|Détection personnalisée|CustomDetection|
|TI personnalisée|CustomerTI|
|EDR|WindowsDefenderAtp|
|Microsoft 365 Defender|Mtp|
|Microsoft Defender pour Office 365|OfficeATP|
|Spécialistes des menaces Microsoft|ThreatExperts|
|Smartscreen|WindowsDefenderSmartScreen|

### <a name="entities"></a>Entités

Vous pouvez filtrer les alertes en fonction du nom ou de l’ID de l’entité. 

### <a name="automated-investigation-state"></a>État d’investigation automatisé

Vous pouvez choisir de filtrer les alertes en fonction de leur état d’investigation automatisé.



## <a name="related-topics"></a>Voir aussi

- [Gérer les alertes Microsoft Defender pour point de terminaison](manage-alerts.md)
- [Examiner les alertes Microsoft Defender pour point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte de Microsoft Defender pour point de terminaison](investigate-files.md)
- [Examiner les appareils dans la liste des appareils Microsoft Defender pour point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Microsoft Defender pour point de terminaison](investigate-ip.md)
- [Examiner un domaine associé à une alerte de Microsoft Defender pour point de terminaison](investigate-domain.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour point de terminaison](investigate-user.md)
