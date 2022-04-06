---
title: Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison
description: Découvrez le fonctionnement des files d’attente d’alertes Microsoft Defender pour les points de terminaison, ainsi que le tri et le filtrage des listes d’alertes.
keywords: alerts, queues, alerts queue, sort, order, filter, manage alerts, new, in progress, resolved, newest, time in queue, severity, time period, microsoft threat experts alerts
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 03/27/2020
ms.technology: mde
ms.openlocfilehash: 0d6b012d2e3dbe6778c8d9c70552cf24427f8a3d
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472042"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-alerts-queue"></a>Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-alertsq-abovefoldlink)

La **file d’attente Alertes** affiche la liste des alertes qui ont été signalées à partir d’appareils de votre réseau. Par défaut, la file d’attente affiche les alertes visibles au cours des 30 derniers jours dans un affichage groupé. Les alertes les plus récentes sont affichées en haut de la liste pour vous aider à voir les alertes les plus récentes en premier.

> [!NOTE]
> Les alertes sont considérablement réduites grâce à des examens et des corrections automatisés, ce qui permet aux experts en matière d’opérations de sécurité de se concentrer sur des menaces plus sophistiquées et d’autres initiatives à valeur élevée. Lorsqu’une alerte contient une entité prise en charge pour une investigation automatisée (par exemple, un fichier) sur un appareil qui dispose d’un système d’exploitation pris en charge, une investigation et une correction automatisées peuvent commencer. Pour plus d’informations sur les enquêtes automatisées, voir [Vue d’ensemble des enquêtes automatisées](automated-investigations.md).

Vous pouvez choisir parmi plusieurs options pour personnaliser l’affichage des alertes.

Dans la barre de navigation supérieure, vous pouvez :

- Personnaliser des colonnes pour ajouter ou supprimer des colonnes
- Appliquer des filtres
- Affichage des alertes pour une durée particulière telle que 1 jour, 3 jours, 1 semaine, 30 jours et 6 mois
- Exporter la liste des alertes vers Excel
- Gérer les alertes

:::image type="content" source="images/alerts-queue-list.png" alt-text="Page File d’attente des alertes" lightbox="images/alerts-queue-list.png":::

## <a name="sort-and-filter-alerts"></a>Trier et filtrer les alertes 

Vous pouvez appliquer les filtres suivants pour limiter la liste des alertes et obtenir une vue plus pointée des alertes.

### <a name="severity"></a>Severity

Gravité de l’alerte|Description
---|---
Élevé <br> (Rouge)|Alertes couramment associées à des menaces avancées persistantes (APT). Ces alertes indiquent un risque élevé en raison de la gravité des dommages qu’elles peuvent causer sur les appareils. Voici quelques exemples : activités des outils de vol d’informations d’identification, activités de ransomware non associées à un groupe, falsification des capteurs de sécurité ou toute activité malveillante indiquant un adversaire humain.
Moyen <br> (Orange)|Les alertes provenant protection évolutive des points de terminaison comportements post-violation qui peuvent faire partie d’une menace persistante avancée. Ces comportements incluent les comportements observés typiques des phases d’attaque, la modification anormale du Registre, l’exécution de fichiers suspects, etc. Bien que certaines d’entre elles font partie de tests de sécurité internes, elles nécessitent une enquête, car elles peuvent également faire partie d’une attaque avancée.
Faible <br> (Jaune)|Alertes sur les menaces associées à des programmes malveillants répandus. Par exemple, les outils de piratage, les outils de piratage non malveillants, tels que l’exécution de commandes d’exploration, l’effacement des journaux, etc., qui n’indiquent souvent pas de menace avancée ciblant l’organisation. Elle peut également être le fait d’un outil de sécurité isolé testé par un utilisateur de votre organisation.
Informatif <br> (Gris)|Alertes qui peuvent ne pas être considérées comme dangereuses pour le réseau, mais qui peuvent sensibiliser l’organisation à d’éventuels problèmes de sécurité.

#### <a name="understanding-alert-severity"></a>Comprendre la gravité des alertes

Antivirus Microsoft Defender (Microsoft Defender AV) et les gravités des alertes defender pour point de terminaison sont différentes, car elles représentent des étendues différentes.

La Antivirus Microsoft Defender gravité de la menace représente la gravité absolue de la menace détectée (programme malveillant) et est attribuée en fonction du risque potentiel pour l’appareil individuel, s’il est infecté.

La gravité de l’alerte Defender pour le point de terminaison représente la gravité du comportement détecté, le risque réel pour l’appareil, mais plus important encore le risque potentiel pour l’organisation.

Par exemple :

- La gravité d’une alerte Defender pour point de terminaison concernant une menace détectée par Antivirus Microsoft Defender qui a été empêchée et qui n’a pas infecté l’appareil est classée comme « Informationnelle », car il n’y a eu aucun dommages réel.
- Une alerte concernant un programme malveillant commercial a été détectée lors de l’exécution, mais bloquée et corrigé par Microsoft Defender AV, est classée comme « Faible », car elle a peut-être endommagé l’appareil, mais ne pose aucune menace pour l’organisation.
- Une alerte concernant les programmes malveillants détectés lors de l’exécution, qui peuvent représenter une menace non seulement pour l’appareil individuel, mais aussi pour l’organisation, même si elle a été finalement bloquée, peut être classée comme « Moyenne » ou « Élevée ».
- Les alertes de comportement suspectes, qui n’ont pas été bloquées ou corrigés, seront classées « Faible », « Moyenne » ou « Élevée » en fonction des mêmes considérations sur les menaces organisationnelles.

### <a name="status"></a>Statut

Vous pouvez choisir de filtrer la liste des alertes en fonction de leur état.

### <a name="categories"></a>Catégories

Nous avons redéfini les catégories d’alertes pour les aligner sur les [tactiques](https://attack.mitre.org/tactics/enterprise/) d’attaque d’entreprise dans la matrice [MITRE ATT&CK](https://attack.mitre.org/). Les nouveaux noms de catégorie s’appliquent à toutes les nouvelles alertes. Les alertes existantes conserveront les noms de catégorie précédents.

### <a name="service-sources"></a>Sources de service

Spécialistes des menaces Microsoft participants peuvent désormais filtrer et voir les détections à partir du nouveau service de repérage géré par des experts en menaces.

Filtrez les alertes en fonction des sources de service suivantes :

- Microsoft Defender pour l’identité
- Microsoft Defender for Cloud Apps
- Microsoft Defender pour point de terminaison
- Microsoft 365 Defender
- Microsoft Defender pour Office 365
- Gouvernance des applications
- AAD Identity Protection

> [!NOTE]
> Le filtre Antivirus s’affiche uniquement si les appareils utilisent Antivirus Microsoft Defender comme produit anti-programme malveillant de protection en temps réel par défaut.

### <a name="tags"></a>Balises

Vous pouvez filtrer les alertes en fonction des balises affectées aux alertes.

### <a name="policy"></a>Stratégie 

Vous pouvez filtrer les alertes en fonction des stratégies suivantes :

|Source de détection|Valeur d’API|
|---|---|
|Capteurs tiers|ThirdPartySensors|
|Antivirus|WindowsDefenderAv|
|Examen automatisé|AutomatedIgoigation|
|Détection personnalisée|CustomDetection|
|Ti personnalisée|CustomerTI|
|PEPT|WindowsDefenderAtp|
|Microsoft 365 Defender|MTP|
|Microsoft Defender pour Office 365|OfficeATP|
|Spécialistes des menaces Microsoft|ThreatExperts|
|SmartScreen|WindowsDefenderSmartScreen|

### <a name="entities"></a>Entités

Vous pouvez filtrer les alertes en fonction du nom ou de l’ID de l’entité. 

### <a name="automated-investigation-state"></a>État d’examen automatisé

Vous pouvez choisir de filtrer les alertes en fonction de leur état d’investigation automatisé.



## <a name="related-topics"></a>Sujets associés

- [Gérer les alertes microsoft Defender pour les points de terminaison](manage-alerts.md)
- [Examiner microsoft Defender pour les alertes de point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte Microsoft Defender pour le point de terminaison](investigate-files.md)
- [Examiner les appareils de la liste Microsoft Defender pour les appareils de point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Microsoft Defender pour le point de terminaison](investigate-ip.md)
- [Examiner un domaine associé à une alerte Microsoft Defender pour le point de terminaison](investigate-domain.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour le point de terminaison](investigate-user.md)
