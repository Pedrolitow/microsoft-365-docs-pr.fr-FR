---
title: Profil d’appareil dans le portail de sécurité Microsoft 365
description: Afficher les niveaux de risque et d’exposition d’un périphérique dans votre organisation. Analysez les menaces passées et actuelles, et protégez l’appareil avec les dernières mises à jour.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, protection Microsoft contre les menaces, MTP, centre de sécurité, Microsoft Defender ATP, Office 365 ATP, Azure ATP, page appareil, profil d’appareil, page ordinateur, profil d’ordinateur
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
ms.author: v-maave
author: martyav
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.openlocfilehash: 3840a6beae3b586fc90420f7813ff6e9d3cc6c60
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48843851"
---
# <a name="device-profile-page"></a>Page profil de périphérique

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


Le portail de sécurité Microsoft 365 vous fournit des pages de profil de périphérique, afin que vous puissiez rapidement évaluer l’intégrité et l’état des appareils sur votre réseau.

> [!IMPORTANT]
> La page de profil de périphérique peut sembler légèrement différente, selon que l’appareil est ou non s’inscrire dans Microsoft Defender pour le point de terminaison, Microsoft Defender pour l’identité ou les deux.

Si le périphérique est intégré à Microsoft Defender pour le point de terminaison, vous pouvez également utiliser la page profil de l’appareil pour effectuer certaines tâches de sécurité courantes.

## <a name="navigating-the-device-profile-page"></a>Navigation dans la page de profil de l’appareil

La page profil est divisée en plusieurs sections.

![Image de la page de profil de périphérique avec (1) barre d’onglets (2) et (3) actions mises en surbrillance en rouge](../../media/mtp-device-profile/hybrid-device-overall.png)

L’encadré (1) répertorie les détails de base sur l’appareil.

La zone de contenu principale (2) contient des onglets que vous pouvez parcourir pour afficher différents types d’informations sur l’appareil.

Si le périphérique est inscrit dans Microsoft Defender pour le point de terminaison, vous verrez également une liste d’actions de réponse (3). Les actions de réponse vous permettent d’effectuer des tâches courantes liées à la sécurité.

## <a name="sidebar"></a>Gadgets

En regard de la zone de contenu principale de la page de profil d’appareil est l’encadré.

![Image de l’onglet du volet de navigation pour le profil d’appareil](../../media/mtp-device-profile/azure-atp-only-device-sidebar.png)

Le volet de navigation répertorie le nom complet et le niveau d’exposition de l’appareil. Elle fournit également des informations de base importantes dans les sous-sections de petite taille qui peuvent être ouvertes ou fermées, telles que :

* **Tags** -tout Microsoft Defender pour point de terminaison, Microsoft Defender pour l’identité ou les balises personnalisées associées au périphérique. Les balises de Microsoft Defender for Identity ne sont pas modifiables.
* **Informations de sécurité** -incidents ouverts et alertes actives. Le niveau d’exposition et le niveau de risque sont également affichés dans Microsoft Defender pour le point de terminaison.

> [!TIP]
> Le niveau d’exposition indique le degré de conformité de l’appareil aux recommandations en matière de sécurité, tandis que le niveau de risque est calculé en fonction d’un certain nombre de facteurs, dont les types et la gravité des alertes actives.

* **Détails** sur l’appareil-domaine, système d’exploitation, horodatage de la première vue de l’appareil, adresses IP, ressources. Les appareils qui sont intégrés à Microsoft Defender pour Endpoint affichent également l’état d’intégrité. Les appareils qui sont intégrés à Microsoft Defender pour Identity affichent le nom SAM et un horodatage pour la première création de l’appareil.
* **Activité réseau** : pour la première fois et pour la dernière fois, le périphérique a été vu sur le réseau.
* **Données d’annuaire** ( *uniquement pour les appareils qui sont intégrés à l’identité de Microsoft Defender* )-indicateurs [UAC](https://docs.microsoft.com/windows/security/identity-protection/user-account-control/user-account-control-overview) , [noms principaux](https://docs.microsoft.com/windows/win32/ad/service-principal-names)de propriété et appartenances aux groupes.

## <a name="response-actions"></a>Actions de réponse

Les actions de réponse offrent un moyen rapide de se défendre et d’analyser les menaces.

![Image de la barre d’action pour le profil d’appareil](../../media/mtp-device-profile/hybrid-device-long-action-bar.png)

> [!IMPORTANT]
> * Les [actions de réponse](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts) ne sont disponibles que si le périphérique est intégré à Microsoft Defender pour le point de terminaison.
> * Les appareils qui sont intégrés à Microsoft Defender pour le point de terminaison peuvent afficher plusieurs actions de réponse, en fonction du système d’exploitation et du numéro de version de l’appareil.

Les actions disponibles sur la page profil d’appareil sont les suivantes :

* **Gérer les balises** : met à jour les balises personnalisées que vous avez appliquées à cet appareil.
* **Isoler l’appareil** : isole l’appareil du réseau de votre organisation tout en le gardant connecté à Microsoft Defender pour le point de terminaison. Vous pouvez choisir d’autoriser l’exécution d’Outlook, de teams et de Skype entreprise lorsque l’appareil est isolé, à des fins de communication.
* **Centre de notifications** : afficher l’état des actions soumises. Disponible uniquement si une autre action a déjà été sélectionnée.
* **Restreindre l’exécution de l’application** : empêche les applications qui ne sont pas signées par Microsoft de s’exécuter.
* **Exécuter l’analyse antivirus** : met à jour les définitions de l’antivirus Windows Defender et exécute immédiatement une analyse antivirus. Choisissez entre analyse rapide ou analyse complète.
* **Recueillir** des informations sur l’appareil. Une fois l’enquête terminée, vous pouvez la télécharger.
* **Lancer une session Live Response session** : charge un environnement distant sur le périphérique pour les [examens de sécurité approfondis](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/live-response).
* **Lancer une enquête automatisée** : [enquête et corrige automatiquement les menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air). Bien que vous puissiez déclencher manuellement des analyses automatisées à exécuter à partir de cette page, [certaines stratégies d’alerte](https://docs.microsoft.com/microsoft-365/compliance/alert-policies?view=o365-worldwide#default-alert-policies) déclenchent des enquêtes automatiques.
* **Centre de notifications** : affiche des informations sur les actions de réponse en cours d’exécution.

## <a name="tabs-section"></a>Section Onglets

Les onglets de profil d’appareil vous permettent d’afficher une vue d’ensemble des détails de sécurité de l’appareil et des tableaux contenant une liste d’alertes.

Les appareils inscrits dans Microsoft Defender for Endpoint affichent également des onglets qui comportent une chronologie, une liste de recommandations de sécurité, un inventaire logiciel, une liste de vulnérabilités découvertes et des Kbits/s manquants (mises à jour de sécurité).

### <a name="overview-tab"></a>Onglet vue d’ensemble

L’onglet par défaut est **vue d’ensemble**. Elle fournit un aperçu rapide du plus important de la sécurité de l’appareil.

![Image de l’onglet vue d’ensemble du profil de périphérique](../../media/mtp-device-profile/hybrid-device-tab-overview.png)

Ici, vous pouvez obtenir un aperçu rapide des alertes actives de l’appareil et des utilisateurs actuellement connectés.

Si le périphérique est intégré à Microsoft Defender pour le point de terminaison, vous verrez également le niveau de risque de l’appareil et les données disponibles sur les évaluations de sécurité. Les évaluations de sécurité décrivent le niveau d’exposition de l’appareil, fournissent des recommandations en matière de sécurité et répertorient les logiciels concernés et les vulnérabilités découvertes.

### <a name="alerts-tab"></a>Onglet Alertes

L’onglet **alertes** contient la liste des alertes qui ont été déclenchées sur l’appareil, de Microsoft Defender pour l’identité et de Microsoft Defender pour le point de terminaison.

![Image de l’onglet Alertes pour le profil d’appareil](../../media/mtp-device-profile/hybrid-device-tab-alerts.png)

Vous pouvez personnaliser le nombre d’éléments affichés, ainsi que les colonnes affichées pour chaque élément. Le comportement par défaut consiste à répertorier trente éléments par page.

Les colonnes de cet onglet incluent des informations sur la gravité de la menace qui a déclenché l’alerte, ainsi que sur l’État, l’état de l’enquête et la personne à qui l’alerte a été affectée.

La colonne *entités concernées* fait référence au périphérique (entité) dont vous affichez actuellement le profil, ainsi qu’aux autres périphériques de votre réseau qui sont affectés.

La sélection d’un élément dans cette liste ouvrira un lanceur contenant encore plus d’informations sur l’alerte sélectionnée.

Cette liste peut être filtrée en fonction de la gravité, de l’État ou de la personne à qui l’alerte a été affectée.

### <a name="timeline-tab"></a>Onglet chronologie

L’onglet **chronologie** inclut un graphique interactif, chronologique, de tous les événements déclenchés sur l’appareil. En déplacant la zone mise en surbrillance du graphique vers la gauche ou la droite, vous pouvez afficher les événements sur différentes périodes de temps. Vous pouvez également choisir une plage de dates personnalisée dans le menu déroulant entre le graphique interactif et la liste des événements.

Sous le graphique se trouve une liste d’événements pour la plage de dates sélectionnée.

![Image de l’onglet chronologie pour le profil d’appareil](../../media/mtp-device-profile/hybrid-device-tab-timeline.png)

Le nombre d’éléments affichés et les colonnes de la liste peuvent être personnalisés. Les colonnes par défaut répertorient l’heure de l’événement, l’utilisateur actif, le type d’action, les entités (processus) et des informations supplémentaires sur l’événement.

La sélection d’un élément dans cette liste ouvrira un menu volant affichant un graphique d’entités d’événements, affichant les processus parents et enfants impliqués dans l’événement.

La liste peut être filtrée par type d’événement spécifique ; par exemple, des événements de registre ou des événements Smart Screen.

La liste peut également être exportée dans un fichier CSV, par téléchargement. Bien que le fichier ne soit pas limité par le nombre d’événements, la plage de temps maximale que vous pouvez choisir pour l’exportation est de sept jours.

### <a name="security-recommendations-tab"></a>Onglet recommandations de sécurité

L’onglet **Security Recommendations** répertorie les actions que vous pouvez effectuer pour protéger l’appareil. La sélection d’un élément sur cette liste ouvre un menu volant dans lequel vous pouvez obtenir des instructions sur l’application de la recommandation.

![Image de l’onglet recommandations de sécurité pour le profil d’appareil](../../media/mtp-device-profile/hybrid-device-tab-security-recs.png)

Comme avec les onglets précédents, le nombre d’éléments affichés par page, ainsi que les colonnes visibles, peuvent être personnalisés.

L’affichage par défaut inclut des colonnes qui détaillent les faiblesses de sécurité traitées, la menace associée, le composant ou le logiciel associé concerné par la menace, et bien plus encore. Les éléments peuvent être filtrés selon l’état de la recommandation.

### <a name="software-inventory"></a>Inventaire des logiciels

L’onglet **inventaire logiciel** répertorie les logiciels installés sur l’appareil.

![Image de l’onglet inventaire logiciel pour le profil d’appareil](../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png)

La vue par défaut affiche le fournisseur de logiciels, le numéro de version installé, le nombre de faiblesses logicielles connues, les informations de menace, le code de produit et les balises. Le nombre d’éléments affichés et les colonnes affichées peuvent être personnalisés.

La sélection d’un élément dans cette liste ouvre un lanceur contenant des détails supplémentaires sur le logiciel sélectionné, ainsi que le chemin d’accès et l’horodatage de la dernière fois que le logiciel a été trouvé.

Cette liste peut être filtrée par code de produit.

### <a name="discovered-vulnerabilities-tab"></a>Onglet vulnérabilités découvertes

L’onglet **vulnérabilités découvertes** répertorie les vulnérabilités et exploits courants (CVE) susceptibles d’affecter l’appareil.

![Image de l’onglet vulnérabilités découvertes pour le profil d’appareil](../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png)

L’affichage par défaut répertorie la gravité de CVE, le score commun de vulnérabilité (CVS), le logiciel associé à CVE, le moment où le CVE a été publié, la date de la dernière mise à jour et les menaces associées à CVE.

Comme avec les onglets précédents, le nombre d’éléments affichés et les colonnes visibles peuvent être personnalisés.

La sélection d’un élément dans cette liste ouvrira un menu volant qui décrit le CVE.

### <a name="missing-kbs"></a>Ko manquants

L’onglet **Ko manquants** répertorie toutes les mises à jour Microsoft qui n’ont pas encore été appliquées au périphérique. Le « Ko » en question sont des Articles de la [base de connaissances](https://support.microsoft.com/help/242450/how-to-query-the-microsoft-knowledge-base-by-using-keywords-and-query) qui décrivent ces mises à jour ; par exemple, [KB4551762](https://support.microsoft.com/help/4551762/windows-10-update-kb4551762).

![Image de l’onglet Ko manquants pour le profil d’appareil](../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG)

L’affichage par défaut répertorie le Bulletin contenant les mises à jour, la version du système d’exploitation, les produits concernés, les CVE traités, le numéro de la base de connaissances et les balises.

Le nombre d’éléments affichés par page et les colonnes affichées peuvent être personnalisés.

La sélection d’un élément ouvre un menu volant qui établit un lien vers la mise à jour.

## <a name="related-topics"></a>Voir aussi

* [Vue d’ensemble de Microsoft 365 Defender](microsoft-threat-protection.md)
* [Activer Microsoft 365 Defender](mtp-enable.md)
* [Examiner les entités sur les appareils à l’aide de la réponse dynamique](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/live-response)
* [Recherche et réponse automatiques dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air)
