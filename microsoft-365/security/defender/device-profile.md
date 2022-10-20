---
title: Profil d’appareil dans le portail de sécurité Microsoft 365
description: Affichez les niveaux de risque et d’exposition d’un appareil de votre organisation. Analysez les menaces passées et présentes, et protégez l’appareil avec les dernières mises à jour.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, Microsoft 365 Defender, security center, Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender pour Identity, page d’appareil, profil d’appareil, page ordinateur, profil d’ordinateur
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.localizationpriority: medium
ms.author: dansimp
author: martyav
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
search.appverid: met150
ms.openlocfilehash: 269670d86676896a1a217f224c74776c73388fa9
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68631015"
---
# <a name="device-profile-page"></a>Page Profil d’appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


Le portail de sécurité Microsoft 365 vous fournit des pages de profil d’appareil, ce qui vous permet d’évaluer rapidement l’intégrité et l’état des appareils sur votre réseau.

> [!IMPORTANT]
> La page de profil d’appareil peut apparaître légèrement différente, selon que l’appareil est inscrit dans Microsoft Defender pour point de terminaison, Microsoft Defender pour Identity ou les deux.

Si l’appareil est inscrit dans Microsoft Defender pour point de terminaison, vous pouvez également utiliser la page profil de l’appareil pour effectuer certaines tâches de sécurité courantes.

## <a name="navigating-the-device-profile-page"></a>Navigation dans la page de profil d’appareil

La page de profil est divisée en plusieurs sections larges.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-overall.png" alt-text="Page Profil d’appareil dans le portail Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-overall.png":::

La barre latérale (1) répertorie les détails de base sur l’appareil.

La zone de contenu principale (2) contient des onglets que vous pouvez basculer pour afficher différents types d’informations sur l’appareil.

Si l’appareil est inscrit dans Microsoft Defender pour point de terminaison, vous verrez également une liste d’actions de réponse (3). Les actions de réponse vous permettent d’effectuer des tâches courantes liées à la sécurité.

## <a name="sidebar"></a>Barre latérale

À côté de la zone de contenu principale de la page de profil d’appareil se trouve la barre latérale.

:::image type="content" source="../../media/mtp-device-profile/azure-atp-only-device-sidebar.png" alt-text="Onglet Barre latérale du profil d’appareil dans le portail Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/azure-atp-only-device-sidebar.png":::

La barre latérale répertorie le nom complet et le niveau d’exposition de l’appareil. Il fournit également des informations de base importantes dans les petites sous-sections qui peuvent être ouvertes ou fermées, telles que :

* **Balises** : toutes les balises Microsoft Defender pour point de terminaison, Microsoft Defender pour Identity ou personnalisées associées à l’appareil. Les balises de Microsoft Defender pour Identity ne sont pas modifiables.
* **Informations de sécurité** : ouvrez des incidents et des alertes actives. Les appareils inscrits dans Microsoft Defender pour point de terminaison affichent également le niveau d’exposition et le niveau de risque.

> [!TIP]
> Le niveau d’exposition est lié au niveau de conformité de l’appareil aux recommandations de sécurité, tandis que le niveau de risque est calculé en fonction d’un certain nombre de facteurs, notamment les types et la gravité des alertes actives.

* **Détails de** l’appareil : domaine, système d’exploitation, horodatage du moment où l’appareil a été vu pour la première fois, adresses IP, ressources. Les appareils inscrits dans Microsoft Defender pour point de terminaison affichent également l’état d’intégrité. Les appareils inscrits dans Microsoft Defender pour Identity affichent le nom SAM et un horodatage pour la première création de l’appareil.
* **Activité réseau** : horodatages pour la première fois et la dernière fois que l’appareil a été vu sur le réseau.
* **Données d’annuaire** (*uniquement pour les appareils inscrits dans Microsoft Defender pour Identity*) : indicateurs [UAC](/windows/security/identity-protection/user-account-control/user-account-control-overview), [SPN](/windows/win32/ad/service-principal-names) et appartenances aux groupes.

## <a name="response-actions"></a>Actions de réponse

Les actions de réponse offrent un moyen rapide de se défendre et d’analyser les menaces.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-long-action-bar.png" alt-text="Barre d’action pour le profil d’appareil dans le portail Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-long-action-bar.png":::

> [!IMPORTANT]
> * [Les actions de réponse](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts) sont disponibles uniquement si l’appareil est inscrit dans Microsoft Defender pour point de terminaison.
> * Les appareils inscrits dans Microsoft Defender pour point de terminaison peuvent afficher différents nombres d’actions de réponse, en fonction du système d’exploitation et du numéro de version de l’appareil.

Les actions disponibles sur la page de profil d’appareil sont les suivantes :

* **Gérer les balises** : Mises à jour balises personnalisées que vous avez appliquées à cet appareil.
* **Isoler l’appareil** : isole l’appareil du réseau de votre organisation tout en le maintenant connecté à Microsoft Defender pour point de terminaison. Vous pouvez choisir d’autoriser Outlook, Teams et Skype Entreprise à s’exécuter lorsque l’appareil est isolé, à des fins de communication.
* **Centre d’actions** : affichez l’état des actions soumises. Disponible uniquement si une autre action a déjà été sélectionnée.
* **Restreindre l’exécution de l’application** : empêche l’exécution des applications qui ne sont pas signées par Microsoft.
* **Exécuter l’analyse antivirus** - Mises à jour Microsoft Defender définitions antivirus et exécute immédiatement une analyse antivirus. Choisissez entre analyse rapide ou analyse complète.
* **Collecter le package d’investigation** : collecte des informations sur l’appareil. Une fois l’enquête terminée, vous pouvez la télécharger.
* **Lancer une session de réponse en direct** : charge un interpréteur de commandes distant sur l’appareil pour [des investigations de sécurité approfondies](/microsoft-365/security/defender-endpoint/live-response).
* **Lancer une investigation automatisée** : [examine et corrige automatiquement les menaces](../office-365-security/office-365-air.md). Bien que vous puissiez déclencher manuellement des investigations automatisées à exécuter à partir de cette page, [certaines stratégies d’alerte](../../compliance/alert-policies.md#default-alert-policies) déclenchent elles-mêmes des investigations automatiques.
* **Centre d’actions** : affiche des informations sur les actions de réponse en cours d’exécution.

## <a name="tabs-section"></a>Section Onglets

Les onglets de profil d’appareil vous permettent de parcourir une vue d’ensemble des détails de sécurité sur l’appareil et des tableaux contenant une liste d’alertes.

Les appareils inscrits dans Microsoft Defender pour point de terminaison affichent également des onglets qui comportent une chronologie, une liste de recommandations de sécurité, un inventaire logiciel, une liste des vulnérabilités découvertes et des bases de connaissances manquantes (mises à jour de sécurité).

### <a name="overview-tab"></a>Onglet Overview

L’onglet par défaut est **Vue d’ensemble**. Il fournit un aperçu rapide du fait de sécurité le plus important sur l’appareil.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-overview.png" alt-text="Onglet Vue d’ensemble du profil d’appareil dans le portail Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-overview.png":::

Ici, vous pouvez consulter rapidement les alertes actives de l’appareil et les utilisateurs actuellement connectés.

Si l’appareil est inscrit dans Microsoft Defender pour point de terminaison, vous verrez également le niveau de risque de l’appareil et toutes les données disponibles sur les évaluations de sécurité. Les évaluations de sécurité décrivent le niveau d’exposition de l’appareil, fournissent des recommandations de sécurité et répertorient les logiciels affectés et les vulnérabilités découvertes.

### <a name="alerts-tab"></a>Onglet Alertes

L’onglet **Alertes** contient une liste d’alertes qui ont été déclenchées sur l’appareil, à la fois à partir de Microsoft Defender pour Identity et de Microsoft Defender pour point de terminaison.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-alerts.png" alt-text="Onglet Alertes du profil d’appareil dans le portail Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-alerts.png":::

Vous pouvez personnaliser le nombre d’éléments affichés, ainsi que les colonnes affichées pour chaque élément. Le comportement par défaut consiste à répertorier trente éléments par page.

Les colonnes de cet onglet incluent des informations sur la gravité de la menace qui a déclenché l’alerte, ainsi que l’état, l’état d’investigation et les personnes auxquelles l’alerte a été affectée.

La colonne *d’entités affectées* fait référence à l’appareil (entité) dont vous affichez actuellement le profil, ainsi qu’à tous les autres appareils de votre réseau affectés.

La sélection d’un élément dans cette liste ouvre un menu volant contenant encore plus d’informations sur l’alerte sélectionnée.

Cette liste peut être filtrée par gravité, état ou à qui l’alerte a été affectée.

### <a name="timeline-tab"></a>Onglet Chronologie

L’onglet **Chronologie** inclut un graphique chronologique interactif de tous les événements déclenchés sur l’appareil. En déplaçant la zone mise en surbrillance du graphique à gauche ou à droite, vous pouvez afficher les événements sur différentes périodes de temps. Vous pouvez également choisir une plage personnalisée de dates dans le menu déroulant entre le graphique interactif et la liste des événements.

Sous le graphique se trouve une liste d’événements pour la plage de dates sélectionnée.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-timeline.png" alt-text="Onglet Chronologie du profil d’appareil dans le portail Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-timeline.png":::

Le nombre d’éléments affichés et les colonnes de la liste peuvent être personnalisés. Les colonnes par défaut répertorient l’heure de l’événement, l’utilisateur actif, le type d’action, les entités (processus) et des informations supplémentaires sur l’événement.

La sélection d’un élément dans cette liste ouvre un menu volant affichant un graphique d’entités d’événement, montrant les processus parent et enfant impliqués dans l’événement.

La liste peut être filtrée par le type d’événement spécifique ; par exemple, les événements du Registre ou les événements Smart Screen.

La liste peut également être exportée vers un fichier CSV, pour téléchargement. Bien que le fichier ne soit pas limité par le nombre d’événements, l’intervalle de temps maximal que vous pouvez choisir d’exporter est de sept jours.

### <a name="security-recommendations-tab"></a>Onglet Recommandations de sécurité

L’onglet **Recommandations de sécurité** répertorie les actions que vous pouvez effectuer pour protéger l’appareil. La sélection d’un élément dans cette liste ouvre un menu volant dans lequel vous pouvez obtenir des instructions sur la façon d’appliquer la recommandation.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-security-recs.png" alt-text="Onglet Recommandations de sécurité pour le profil d’appareil dans le portail Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-security-recs.png":::

Comme avec les onglets précédents, le nombre d’éléments affichés par page, ainsi que les colonnes visibles, peuvent être personnalisés.

La vue par défaut inclut des colonnes qui détaillent les faiblesses de sécurité traitées, la menace associée, le composant ou le logiciel associé affectés par la menace, etc. Les éléments peuvent être filtrés en fonction de l’état de la recommandation.

### <a name="software-inventory"></a>Inventaire de logiciels

**L’onglet Inventaire logiciel** répertorie les logiciels installés sur l’appareil.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png" alt-text="Onglet Inventaire logiciel du profil d’appareil dans le portail Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png":::

La vue par défaut affiche le fournisseur de logiciels, le numéro de version installé, le nombre de faiblesses logicielles connues, les informations sur les menaces, le code de produit et les balises. Le nombre d’éléments affichés et les colonnes affichées peuvent être personnalisés.

La sélection d’un élément dans cette liste ouvre un menu volant contenant plus de détails sur le logiciel sélectionné, ainsi que le chemin d’accès et l’horodatage pour la dernière fois que le logiciel a été trouvé.

Cette liste peut être filtrée par code de produit.

### <a name="discovered-vulnerabilities-tab"></a>Onglet Vulnérabilités découvertes

L’onglet **Vulnérabilités découvertes** répertorie toutes les vulnérabilités et exploits courants (CVE) susceptibles d’affecter l’appareil.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png" alt-text="Onglet Vulnérabilités découvertes pour le profil d’appareil dans le portail Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png":::

L’affichage par défaut répertorie la gravité du CVE, le score de vulnérabilité commun (CVS), le logiciel associé au CVE, lors de la publication du CVE, la dernière mise à jour du CVE et les menaces associées au CVE.

Comme avec les onglets précédents, le nombre d’éléments affichés et les colonnes visibles peuvent être personnalisés.

La sélection d’un élément dans cette liste ouvre un menu volant qui décrit le CVE.

### <a name="missing-kbs"></a>Bases de connaissances manquantes

L’onglet **Bases de connaissances manquantes** répertorie les Mises à jour Microsoft qui n’ont pas encore été appliquées à l’appareil. Les « bases de connaissances » en question sont des [articles de la Base de connaissances](https://support.microsoft.com/help/242450/how-to-query-the-microsoft-knowledge-base-by-using-keywords-and-query) qui décrivent ces mises à jour; par exemple, [KB4551762](https://support.microsoft.com/help/4551762/windows-10-update-kb4551762).

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG" alt-text="Onglet Bases de connaissances manquantes pour le profil d’appareil dans le portail Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG":::

L’affichage par défaut répertorie le bulletin contenant les mises à jour, la version du système d’exploitation, les produits affectés, les CVE traités, le numéro de base de connaissances et les balises.

Le nombre d’éléments affichés par page et les colonnes affichées peuvent être personnalisés.

La sélection d’un élément ouvre un menu volant qui est lié à la mise à jour.

## <a name="related-topics"></a>Voir aussi

* [vue d’ensemble de Microsoft 365 Defender](microsoft-365-defender.md)
* [Activer Microsoft 365 Defender](m365d-enable.md)
* [Examiner les entités sur les appareils à l’aide d’une réponse en direct](../defender-endpoint/live-response.md)
* [Investigation et réponse automatisées (AIR) dans Office 365](../office-365-security/office-365-air.md)
