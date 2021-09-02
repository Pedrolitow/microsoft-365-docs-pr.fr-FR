---
title: Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison
description: Découvrez comment fonctionnent les files d’attente des alertes Microsoft Defender pour les points de terminaison, et comment trier et filtrer des listes d’alertes.
keywords: alerts, queues, alerts queue, sort, order, filter, manage alerts, new, in progress, resolved, newest, time in queue, severity, time period, microsoft threat experts alerts
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 03/27/2020
ms.technology: mde
ms.openlocfilehash: bf92c1764ed2b81b1f4409efc2e7bc7fae94185d
ms.sourcegitcommit: ef9cd046c47b340686a4f7bb123ea3b0a269769a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2021
ms.locfileid: "58863832"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-alerts-queue"></a>Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-alertsq-abovefoldlink)

La **file d’attente Alertes** affiche la liste des alertes qui ont été signalées à partir d’appareils de votre réseau. Par défaut, la file d’attente affiche les alertes visibles au cours des 30 derniers jours dans un affichage groupé. Les alertes les plus récentes sont affichés en haut de la liste pour vous aider à voir les alertes les plus récentes en premier.

> [!NOTE]
> La file d’attente des alertes est considérablement réduite grâce à des examens et des corrections automatisés, ce qui permet aux experts en matière d’opérations de sécurité de se concentrer sur des menaces plus sophistiquées et d’autres initiatives à valeur élevée. Lorsqu’une alerte contient une entité prise en charge pour l’examen automatisé (par exemple, un fichier) sur un appareil qui dispose d’un système d’exploitation pris en charge, une investigation et une correction automatisées peuvent démarrer. Pour plus d’informations sur les enquêtes automatisées, voir [Vue d’ensemble des enquêtes automatisées.](automated-investigations.md)

Vous pouvez choisir parmi plusieurs options pour personnaliser l’affichage de file d’attente des alertes.

Dans la barre de navigation supérieure, vous pouvez :

- Sélectionner un affichage groupé ou un affichage liste
- Personnaliser des colonnes pour ajouter ou supprimer des colonnes
- Sélectionner les éléments à afficher par page
- Naviguer entre les pages
- Appliquer des filtres

![Image de la file d’attente des alertes.](images/alerts-queue-list.png)

## <a name="sort-filter-and-group-the-alerts-queue"></a>Trier, filtrer et grouper la file d’attente des alertes

Vous pouvez appliquer les filtres suivants pour limiter la liste des alertes et obtenir une vue plus pointée des alertes.

### <a name="severity"></a>Severity

Gravité de l’alerte|Description
---|---
Élevé <br> (Rouge)|Alertes couramment associées à des menaces avancées persistantes (APT). Ces alertes indiquent un risque élevé en raison de la gravité des dommages qu’elles peuvent causer sur les appareils. Voici quelques exemples : activités des outils de vol d’informations d’identification, activités de ransomware non associées à un groupe, falsification des capteurs de sécurité ou toute activité malveillante indiquant un adversaire humain.
Moyen <br> (Orange)|Alertes provenant protection évolutive des points de terminaison comportements post-violation susceptibles de faire partie d’une menace persistante avancée. Cela inclut les comportements observés typiques des phases d’attaque, la modification anormale du Registre, l’exécution de fichiers suspects, etc. Bien que certaines d’entre elles font partie de tests de sécurité internes, elles nécessitent une enquête, car elles peuvent également faire partie d’une attaque avancée.
Faible <br> (Jaune)|Alertes sur les menaces associées à des programmes malveillants répandus. Par exemple, les outils de piratage, les outils de piratage non malveillants, tels que l’exécution de commandes d’exploration, l’effacement des journaux, etc., qui n’indiquent souvent pas de menace avancée ciblant l’organisation. Elle peut également être le fait d’un outil de sécurité isolé testé par un utilisateur de votre organisation.
Informatif <br> (Gris)|Alertes qui peuvent ne pas être considérées comme dangereuses pour le réseau, mais qui peuvent sensibiliser l’organisation à des problèmes de sécurité potentiels.

#### <a name="understanding-alert-severity"></a>Comprendre la gravité des alertes

Antivirus Microsoft Defender (Microsoft Defender AV) et Les gravités des alertes Defender pour les points de terminaison sont différentes, car elles représentent des étendues différentes.

La Antivirus Microsoft Defender gravité de la menace représente la gravité absolue de la menace détectée (programme malveillant) et est affectée en fonction du risque potentiel pour l’appareil individuel, s’il est infecté.

La gravité de l’alerte Defender pour le point de terminaison représente la gravité du comportement détecté, le risque réel pour l’appareil, mais plus important encore le risque potentiel pour l’organisation.

Par exemple :

- La gravité d’une alerte Defender pour point de terminaison concernant une menace détectée par Antivirus Microsoft Defender qui a été complètement évitée et qui n’a pas infecté l’appareil est classée comme « Informationnelle » car il n’y a eu aucun dommage réel.
- Une alerte concernant un programme malveillant commercial a été détectée lors de l’exécution, mais bloquée et corrigé par Microsoft Defender AV, est classée comme « Faible », car elle a peut-être endommagé l’appareil, mais ne pose aucune menace pour l’organisation.
- Une alerte concernant les programmes malveillants détectés lors de l’exécution, qui peuvent représenter une menace non seulement pour l’appareil individuel, mais aussi pour l’organisation, même si elle a été finalement bloquée, peut être classée comme « Moyenne » ou « Élevée ».
- Les alertes comportementales suspectes, qui n’ont pas été bloquées ou corrigés, seront classées « Faible », « Moyenne » ou « Élevée » en fonction des mêmes considérations sur les menaces organisationnelles.

#### <a name="understanding-alert-categories"></a>Comprendre les catégories d’alertes

Nous avons redéfini les catégories d’alertes pour s’aligner sur les [tactiques](https://attack.mitre.org/tactics/enterprise/) d’attaque d’entreprise dans la matrice [MITRE ATT&CK](https://attack.mitre.org/). Les nouveaux noms de catégorie s’appliquent à toutes les nouvelles alertes. Les alertes existantes conserveront les noms de catégorie précédents.

Le tableau ci-dessous répertorie les catégories actuelles et la façon dont elles sont généralement m mapper avec les catégories précédentes.

|Nouvelle catégorie|Nom de catégorie d’API|Activité ou composant de menace détecté|
|---|---|---|
|Collection|Collection|Recherche et collecte de données pour l’exfiltration.|
|Commande et contrôle|CommandAndControl|Connexion à une infrastructure réseau contrôlée par des personnes malveillantes pour relayer des données ou recevoir des commandes.|
|Accès aux informations d’identification|CredentialAccess|Obtention d’informations d’identification valides pour étendre le contrôle sur les appareils et les autres ressources du réseau.|
|Défense|DefenseEvasion|Pour éviter les contrôles de sécurité, par exemple en désélant les applications de sécurité, en supprimant des contrôles de sécurité et en exécutant des rootkits.|
|Discovery|Discovery|Collecte d’informations sur les appareils et les ressources importants, tels que les ordinateurs d’administrateur, les contrôleurs de domaine et les serveurs de fichiers.|
|Exécution|Exécution|Lancement d’outils malveillants et de code malveillant, y compris les fichiers d’accès à la base de données et les backdoors.|
|Exfiltration|Exfiltration|Extraction de données du réseau vers un emplacement externe contrôlé par l’attaquant.|
|Exploit|Exploit|Exploitez le code et l’activité d’exploitation possible.|
|Accès initial|InitialAccess|Obtenir une entrée initiale sur le réseau cible, impliquant généralement une estimation de mot de passe, des attaques ou des e-mails de hameçonnage.|
|Mouvement latéral|LateralMovement|Déplacement entre les appareils du réseau cible pour atteindre des ressources critiques ou obtenir la persistance du réseau.|
|Programme malveillant|Programme malveillant|Les backdoors, les chevaux de France et d’autres types de code malveillant.|
|Persistance|Persistance|Création de points d’extensibilité de démarrage automatique (ASEP) pour rester actif et résister aux redémarrages du système.|
|Escalade de privilèges|PrivilegeEscalation|Obtenir des niveaux d’autorisation supérieurs pour le code en l’exécutant dans le contexte d’un processus ou d’un compte privilégié.|
|Ransomware|Ransomware|Programme malveillant qui chiffre les fichiers et le paiement par extorts pour restaurer l’accès.|
|Activité suspecte|SuspiciousActivity|Activité non normale qui peut être une activité de programmes malveillants ou une partie d’une attaque.|
|Logiciels indésirables|UnwantedSoftware|Applications de faible réputation et applications qui ont une incidence sur la productivité et l’expérience utilisateur ; détecté comme applications potentiellement indésirables (PUA).|

### <a name="status"></a>Statut

Vous pouvez choisir de limiter la liste des alertes en fonction de leur état.

### <a name="investigation-state"></a>État de l’examen

Correspond à l’état d’examen automatisé.

### <a name="category"></a>Catégorie

Vous pouvez choisir de filtrer la file d’attente pour afficher des types spécifiques d’activités malveillantes.

### <a name="assigned-to"></a>Affectée à

Vous pouvez choisir entre l’affichage des alertes qui vous sont affectées ou l’automatisation.

### <a name="detection-source"></a>Source de détection

Sélectionnez la source qui a déclenché la détection d’alerte. Spécialistes des menaces Microsoft prévisualisation des participants peuvent désormais filtrer et voir les détections à partir du nouveau service de repérage géré par des experts en menaces.

> [!NOTE]
> Le filtre Antivirus s’affiche uniquement si les appareils utilisent Antivirus Microsoft Defender comme produit anti-programme malveillant de protection en temps réel par défaut.

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

### <a name="os-platform"></a>Plateforme du système d’exploitation

Limitez l’affichage de la file d’attente des alertes en sélectionnant la plateforme de système d’exploitation que vous souhaitez examiner.

### <a name="device-group"></a>Groupe d’appareils

Si vous avez des groupes d’appareils spécifiques que vous souhaitez vérifier, vous pouvez sélectionner les groupes pour limiter l’affichage de la file d’attente des alertes.

### <a name="associated-threat"></a>Menace associée

Utilisez ce filtre pour vous concentrer sur les alertes liées aux menaces de profil élevé. Vous pouvez voir la liste complète des menaces de haut niveau dans [l’analyse des menaces.](threat-analytics.md)

## <a name="related-topics"></a>Rubriques connexes

- [Gérer les alertes microsoft Defender pour les points de terminaison](manage-alerts.md)
- [Examiner microsoft Defender pour les alertes de point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte Microsoft Defender pour le point de terminaison](investigate-files.md)
- [Examiner les appareils de la liste Microsoft Defender pour les appareils de point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Microsoft Defender pour le point de terminaison](investigate-ip.md)
- [Examiner un domaine associé à une alerte Microsoft Defender pour le point de terminaison](investigate-domain.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour le point de terminaison](investigate-user.md)
