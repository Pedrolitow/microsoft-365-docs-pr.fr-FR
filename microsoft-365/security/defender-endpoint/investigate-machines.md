---
title: Examiner les appareils dans la liste Des appareils Defender pour point de terminaison
description: Examinez les appareils affectés en examinant les alertes, les informations de connexion réseau, en ajoutant des balises et des groupes d’appareils et en vérifiant l’intégrité du service.
keywords: appareils, balises, groupes, point de terminaison, file d’attente d’alertes, alertes, nom d’appareil, domaine, dernière vue, adresse IP interne, alertes actives, catégorie de menaces, filtrer, trier, examiner les alertes, réseau, connexion, type, vol de mot de passe, ransomware, exploit, menace, gravité faible, intégrité du service
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 6b8529338522df41c25dafb30d25b879a5790861
ms.sourcegitcommit: b1ed6470645455c2f1fcf467450debc622c40147
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67709393"
---
# <a name="investigate-devices-in-the-microsoft-defender-for-endpoint-devices-list"></a>Examiner les appareils dans la liste des appareils Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatemachines-abovefoldlink)

Examinez les détails d’une alerte déclenchée sur un appareil spécifique pour identifier d’autres comportements ou événements susceptibles d’être liés à l’alerte ou à l’étendue potentielle de la violation.

> [!NOTE]
> Dans le cadre du processus d’investigation ou de réponse, vous pouvez collecter un package d’investigation à partir d’un appareil. Voici comment : [collecter un package d’investigation à partir d’appareils](/microsoft-365/security/defender-endpoint/respond-machine-alerts#collect-investigation-package-from-devices).

Vous pouvez cliquer sur les appareils affectés chaque fois que vous les voyez dans le portail pour ouvrir un rapport détaillé sur cet appareil. Les appareils affectés sont identifiés dans les domaines suivants :

- [Liste des appareils](investigate-machines.md)
- [File d’attente des alertes](alerts-queue.md)
- [Tableau de bord des opérations de sécurité](security-operations-dashboard.md)
- Toute alerte individuelle
- Affichage des détails des fichiers individuels
- Toute vue d’adresse IP ou de détails de domaine

Lorsque vous examinez un appareil spécifique, vous voyez :

- Détails sur l'appareil
- Actions de réponse
- Onglets (vue d’ensemble, alertes, chronologie, recommandations de sécurité, inventaire logiciel, vulnérabilités découvertes, ko manquantes)
- Cartes (alertes actives, utilisateurs connectés, évaluation de la sécurité, état d’intégrité des appareils) 
 

:::image type="content" source="images/specific-device.png" alt-text="Vue de l’appareil" lightbox="images/specific-device.png":::

> [!NOTE]
> En raison des contraintes de produit, le profil d’appareil ne prend pas en compte toutes les preuves informatiques lors de la détermination de la période « Dernière vue » (comme indiqué sur la page de l’appareil également).
> Par exemple, la valeur « Dernière vue » dans la page Appareil peut afficher une période plus ancienne, même si des alertes ou des données plus récentes sont disponibles dans la chronologie de l’ordinateur.

## <a name="device-details"></a>Détails sur l'appareil

La section détails de l’appareil fournit des informations telles que le domaine, le système d’exploitation et l’état d’intégrité de l’appareil. S’il existe un package d’investigation disponible sur l’appareil, vous verrez un lien qui vous permet de télécharger le package.

## <a name="response-actions"></a>Actions de réponse

Les actions de réponse s’exécutent en haut d’une page d’appareil spécifique et incluent :

- Gérer des balises
- Isoler l’appareil
- Restreindre l’exécution des applications
- Exécuter une analyse antivirus
- Collecter un package d’examen
- Lancer une session de réponse en direct
- Lancer une enquête automatisée
- Consulter un spécialiste des menaces
- Centre de notifications

Vous pouvez effectuer des actions de réponse dans le Centre d’actions, dans une page d’appareil spécifique ou dans une page de fichier spécifique.

Pour plus d’informations sur la façon d’agir sur un appareil, consultez [Action de réponse sur un appareil](respond-machine-alerts.md).

Pour plus d’informations, consultez [Examiner les entités utilisateur](investigate-user.md).

## <a name="tabs"></a>Onglets

Les onglets fournissent des informations pertinentes sur la sécurité et la prévention des menaces liées à l’appareil. Dans chaque onglet, vous pouvez personnaliser les colonnes affichées en sélectionnant **Personnaliser les colonnes** dans la barre située au-dessus des en-têtes de colonne.

### <a name="overview"></a>Vue d’ensemble

L’onglet **Vue d’ensemble** affiche les [cartes](#cards) pour les alertes actives, les utilisateurs connectés et l’évaluation de la sécurité.

:::image type="content" source="images/overview-device.png" alt-text="Onglet Vue d’ensemble de la page appareil" lightbox="images/overview-device.png":::

### <a name="alerts"></a>Alertes

L’onglet **Alertes** fournit la liste des alertes associées à l’appareil. Cette liste est une version filtrée de la [file d’attente d’alertes](alerts-queue.md) et affiche une brève description de l’alerte, de la gravité (élevée, moyenne, faible, informationnelle), de l’état dans la file d’attente (nouveau, en cours, résolu), de la classification (non défini, fausse alerte, alerte vraie), de l’état d’investigation, de la catégorie d’alerte, de la personne qui traite l’alerte et de la dernière activité. Vous pouvez également filtrer les alertes.

:::image type="content" source="images/alerts-device.png" alt-text="Onglet des alertes liées à l’appareil" lightbox="images/alerts-device.png":::

Lorsque l’icône de cercle à gauche d’une alerte est sélectionnée, un menu volant s’affiche. Dans ce panneau, vous pouvez gérer l’alerte et afficher plus de détails, tels que le numéro d’incident et les appareils associés. Plusieurs alertes peuvent être sélectionnées à la fois.

Pour afficher une vue de page complète d’une alerte, y compris le graphique d’incident et l’arborescence de processus, sélectionnez le titre de l’alerte.

### <a name="timeline"></a>Chronologie

L’onglet **Chronologie** fournit une vue chronologique des événements et des alertes associées qui ont été observées sur l’appareil. Cela peut vous aider à mettre en corrélation tous les événements, fichiers et adresses IP par rapport à l’appareil.

La chronologie vous permet également d’explorer de manière sélective les événements qui se sont produits au cours d’une période donnée. Vous pouvez afficher la séquence temporelle des événements qui se sont produits sur un appareil sur une période sélectionnée. Pour contrôler davantage votre affichage, vous pouvez filtrer par groupes d’événements ou personnaliser les colonnes.

> [!NOTE]
> Pour que les événements de pare-feu s’affichent, vous devez activer la stratégie d’audit. Consultez la [connexion à la plateforme de filtrage d’audit](/windows/security/threat-protection/auditing/audit-filtering-platform-connection).
>
> Le pare-feu couvre les événements suivants :
>
> - [5025](/windows/security/threat-protection/auditing/event-5025) - Arrêt du service de pare-feu
> - [5031](/windows/security/threat-protection/auditing/event-5031) : application bloquée pour accepter les connexions entrantes sur le réseau
> - [5157](/windows/security/threat-protection/auditing/event-5157) - Connexion bloquée

:::image type="content" source="images/timeline-device.png" alt-text="Chronologie de l’appareil avec des événements" lightbox="images/timeline-device.png":::

Voici quelques-unes des fonctionnalités suivantes :

- Rechercher des événements spécifiques
  - Utilisez la barre de recherche pour rechercher des événements de chronologie spécifiques.
- Filtrer les événements à partir d’une date spécifique
  - Sélectionnez l’icône de calendrier dans le coin supérieur gauche du tableau pour afficher les événements du dernier jour, semaine, 30 jours ou plage personnalisée. Par défaut, la chronologie de l’appareil est définie pour afficher les événements des 30 derniers jours.
  - Utilisez la chronologie pour passer à un moment spécifique dans le temps en mettant en surbrillance la section. Les flèches de la chronologie identifient les investigations automatisées
- Exporter des événements détaillés de chronologie des appareils
  - Exportez la chronologie de l’appareil pour la date actuelle ou une plage de dates spécifiée jusqu’à sept jours.

Pour plus d’informations sur certains événements, consultez la section **Informations supplémentaires** . Ces détails varient en fonction du type d’événement, par exemple :

- Contenu d’Application Guard : l’événement de navigateur web a été limité par un conteneur isolé
- Menace active détectée : la détection des menaces s’est produite pendant l’exécution de la menace
- Échec de la correction : une tentative de correction de la menace détectée a été appelée, mais a échoué
- Correction réussie : la menace détectée a été arrêtée et nettoyée
- Avertissement contourné par l’utilisateur : l’avertissement Windows Defender SmartScreen a été ignoré et remplacé par un utilisateur
- Script suspect détecté : un script potentiellement malveillant a été détecté en cours d’exécution
- Catégorie d’alerte : si l’événement a conduit à la génération d’une alerte, la catégorie d’alerte (« Mouvement latéral », par exemple) est fournie.

#### <a name="event-details"></a>Détails de l'événement

Sélectionnez un événement pour afficher les détails pertinents sur cet événement. Un panneau s’affiche pour afficher des informations générales sur l’événement. Le cas échéant et les données sont disponibles, un graphique montrant les entités associées et leurs relations est également affiché.

Pour inspecter davantage l’événement et les événements connexes, vous pouvez exécuter rapidement une requête de [chasse avancée](advanced-hunting-overview.md) en sélectionnant **Hunt pour les événements associés**. La requête retourne l’événement sélectionné et la liste des autres événements qui se sont produits en même temps sur le même point de terminaison.

:::image type="content" source="images/event-details.png" alt-text="Panneau Détails de l’événement" lightbox="images/event-details.png":::

### <a name="security-recommendations"></a>Recommandations en matière de sécurité

**Les recommandations de sécurité** sont générées à partir de la fonctionnalité [de gestion des vulnérabilités](tvm-dashboard-insights.md) de Microsoft Defender pour point de terminaison. La sélection d’une recommandation affiche un panneau dans lequel vous pouvez afficher les détails pertinents, tels que la description de la recommandation et les risques potentiels associés à son non-adoption. Pour plus [d’informations, consultez la recommandation de sécurité](tvm-security-recommendation.md) .

:::image type="content" source="images/security-recommendations-device.png" alt-text="Onglet Recommandations de sécurité" lightbox="images/security-recommendations-device.png":::

### <a name="software-inventory"></a>Inventaire de logiciels

L’onglet **Inventaire** logiciel vous permet d’afficher les logiciels sur l’appareil, ainsi que les éventuelles faiblesses ou menaces. Si vous sélectionnez le nom du logiciel, vous accédez à la page des détails du logiciel, où vous pouvez afficher les recommandations de sécurité, les vulnérabilités détectées, les appareils installés et la distribution des versions. Consultez [l’inventaire logiciel](tvm-software-inventory.md) pour plus d’informations

:::image type="content" source="images/software-inventory-device.png" alt-text="Onglet Inventaire logiciel" lightbox="images/software-inventory-device.png":::

### <a name="discovered-vulnerabilities"></a>Vulnérabilités découvertes

L’onglet **Vulnérabilités découvertes** affiche le nom, la gravité et les informations sur les menaces des vulnérabilités découvertes sur l’appareil. La sélection de vulnérabilités spécifiques affiche une description et des détails.

:::image type="content" source="images/discovered-vulnerabilities-device.png" alt-text="Onglet Vulnérabilités découvertes" lightbox="images/discovered-vulnerabilities-device.png":::

### <a name="missing-kbs"></a>Bases de connaissances manquantes
L’onglet **Bases de connaissances manquantes** répertorie les mises à jour de sécurité manquantes pour l’appareil.

:::image type="content" source="images/missing-kbs-device.png" alt-text="Onglet Ko manquants" lightbox="images/missing-kbs-device.png":::

## <a name="cards"></a>Cartes

### <a name="active-alerts"></a>Alertes actives

La carte **Azure Advanced Threat Protection** affiche une vue d’ensemble générale des alertes liées à l’appareil et à leur niveau de risque, si vous avez activé la fonctionnalité Microsoft Defender pour Identity et qu’il existe des alertes actives. Des informations supplémentaires sont disponibles dans l’exploration « Alertes ».

:::image type="content" source="images/risk-level-small.png" alt-text="Carte d’alertes active" lightbox="images/risk-level-small.png":::

> [!NOTE]
> Vous devez activer l’intégration sur Microsoft Defender pour Identity et Defender pour point de terminaison pour utiliser cette fonctionnalité. Dans Defender pour point de terminaison, vous pouvez activer cette fonctionnalité dans les fonctionnalités avancées. Pour plus d’informations sur l’activation des fonctionnalités avancées, consultez [Activer les fonctionnalités avancées](advanced-features.md).

### <a name="logged-on-users"></a>Utilisateurs connectés

La carte **Utilisateurs connectés** indique le nombre d’utilisateurs connectés au cours des 30 derniers jours, ainsi que les utilisateurs les plus fréquents et les moins fréquents. La sélection du lien « Afficher tous les utilisateurs » ouvre le volet d’informations, qui affiche des informations telles que le type d’utilisateur, le type de connexion et le moment où l’utilisateur a été vu pour la première et la dernière fois. Pour plus d’informations, consultez [Examiner les entités utilisateur](investigate-user.md).

:::image type="content" source="images/logged-on-users.png" alt-text="Volet détails de l’utilisateur" lightbox="images/logged-on-users.png":::

> [!NOTE]
> La valeur d’utilisateur « La plus fréquente » est calculée uniquement sur la base de preuves d’utilisateurs qui se sont connectés avec succès de manière interactive.
> Toutefois, le volet latéral « Tous les utilisateurs » calcule toutes sortes d’ouvertures de session utilisateur afin de voir des utilisateurs plus fréquents dans le volet latéral, étant donné que ces utilisateurs peuvent ne pas être interactifs.

### <a name="security-assessments"></a>Tests d’évaluation de la sécurité

La carte **d’évaluation de la sécurité** affiche le niveau d’exposition global, les recommandations de sécurité, les logiciels installés et les vulnérabilités découvertes. Le niveau d’exposition d’un appareil est déterminé par l’impact cumulé de ses recommandations de sécurité en attente.

:::image type="content" source="images/security-assessments.png" alt-text="Carte d’évaluation de la sécurité" lightbox="images/security-assessments.png":::

### <a name="device-health-status"></a>État d’intégrité de l’appareil

La carte **d’état d’intégrité** de l’appareil affiche un rapport d’intégrité résumé pour l’appareil spécifique. L’un des messages suivants s’affiche en haut de la carte pour indiquer l’état global de l’appareil (répertorié dans l’ordre de priorité la plus élevée à la plus basse) :

- Antivirus Defender non actif
- Le renseignement de sécurité n’est pas à jour
- Le moteur n’est pas à jour
- Échec de l’analyse rapide
- Échec de l’analyse complète
- La plateforme n’est pas à jour
- L’état de la mise à jour du renseignement de sécurité est inconnu
- L’état de mise à jour du moteur est inconnu
- L’état de l’analyse rapide est inconnu
- L’état complet de l’analyse est inconnu
- L’état de mise à jour de la plateforme est inconnu
- L’appareil est à jour
- État non disponible pour macOS & Linux

Les autres informations de la carte sont les suivantes : la dernière analyse complète, la dernière analyse rapide, la version de mise à jour du renseignement de sécurité, la version de mise à jour du moteur, la version de mise à jour de plateforme et le mode Antivirus Defender. 

Notez qu’un cercle gris indique que les données sont inconnues. 

> [!NOTE]
> Le message d’état global pour les appareils macOS et Linux s’affiche actuellement comme « État non disponible pour macOS & Linux ». Actuellement, le résumé de l’état est disponible uniquement pour les appareils Windows. Toutes les autres informations du tableau sont à jour pour afficher les états individuels de chaque signal d’intégrité d’appareil pour toutes les plateformes prises en charge. 

Pour obtenir une vue détaillée du rapport d’intégrité de l’appareil, vous pouvez accéder à **Rapports > Intégrité des appareils**. Pour plus d’informations, consultez le [rapport d’intégrité et de conformité des appareils dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/machine-reports). 

:::image type="content" source="images/device-health-status.png"  alt-text="Carte d’état d’intégrité de l’appareil" lightbox="images/device-health-status.png":::

## <a name="related-topics"></a>Voir aussi

- [Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Gérer les alertes Microsoft Defender pour point de terminaison](manage-alerts.md)
- [Examiner les alertes Microsoft Defender pour point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte Defender pour point de terminaison](investigate-files.md)
- [Examiner une adresse IP associée à une alerte Defender pour point de terminaison](investigate-ip.md)
- [Examiner un domaine associé à une alerte Defender pour point de terminaison](investigate-domain.md)
- [Examiner un compte d’utilisateur dans Defender pour point de terminaison](investigate-user.md)
- [Recommandation de sécurité](tvm-security-recommendation.md)
- [Inventaire des logiciels](tvm-software-inventory.md)