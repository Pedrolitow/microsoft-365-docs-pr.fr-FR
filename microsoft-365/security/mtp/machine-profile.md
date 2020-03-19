---
title: Profil de l’ordinateur dans le portail de sécurité Microsoft 365
description: Afficher les niveaux de risque et d’exposition d’un périphérique dans votre organisation. Analysez les menaces passées et actuelles, et protégez l’ordinateur avec les dernières mises à jour.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, protection Microsoft contre les menaces, MTP, centre de sécurité, Microsoft Defender ATP, Office 365 ATP, Azure ATP, ordinateur, page, liste des ordinateurs, profil d’ordinateur
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
ms.openlocfilehash: 7ab3f63008c65fca1a99128cc6f11f83bc86b2b4
ms.sourcegitcommit: fe4beef350ef9f39b1098755cff46fa2b8e7dc4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "42857606"
---
# <a name="machine-profile-page"></a>Page de profil d’ordinateur

Le portail de sécurité Microsoft 365 vous fournit des pages de profil d’ordinateur, afin que vous puissiez évaluer l’intégrité et l’état des appareils sur votre réseau. Chaque page de profil d’ordinateur contient une multitude d’informations sur l’appareil.

Vous pouvez consulter des informations détaillées sur les logiciels exécutés, sur les alertes ou les événements de sécurité passés et présents, et trouver des liens vers les correctifs logiciels pertinents.

Vous pouvez également utiliser le profil d’ordinateur pour effectuer des tâches courantes liées à la sécurité et examiner rapidement les détails de base sur l’appareil.

## <a name="navigating-the-machine-profile-page"></a>Navigation dans la page de profil d’ordinateur

Vous pouvez accéder à la page profil de l’ordinateur en sélectionnant directement un nom de périphérique dans la liste ordinateurs ou en choisissant **ouvrir la page** de l’ordinateur dans le menu volant liste des ordinateurs.

Une fois la page ouverte, vous constaterez qu’elle est divisée en trois sections.

![Image de la page de profil de l’ordinateur avec (1) barre d’onglets (2) et (3) actions mises en surbrillance en rouge](../../media/mtp-machine-profile/mtp-machine-profile-all.png)

La zone de contenu principale (1) contient sept onglets que vous pouvez parcourir pour afficher différents types d’informations sur l’ordinateur.

L’encadré (2) répertorie les détails de base sur l’ordinateur.

Des actions de réponse sont également disponibles dans un en-tête (3) avant les sections Sidebar et contenu principal. Vous pouvez utiliser les actions de cet en-tête pour effectuer des tâches courantes liées à la sécurité.

## <a name="tabs-section"></a>Section Onglets

Les onglets de profil d’ordinateur vous permettent d’afficher une vue d’ensemble des détails de la sécurité sur l’ordinateur, ainsi que des tableaux contenant une liste d’alertes, une chronologie, une liste de recommandations de sécurité, un inventaire logiciel, une liste de vulnérabilités découvertes et des éléments manquants. Ko (mises à jour de sécurité).

### <a name="overview-tab"></a>Onglet vue d’ensemble

L’onglet par défaut est **vue d’ensemble**. Elle fournit un aperçu rapide du plus important de la sécurité de l’appareil.

![Image de l’onglet vue d’ensemble pour le profil d’ordinateur](../../media/mtp-machine-profile/overview.png)

Ici, vous pouvez trouver un graphique du niveau de risque de l’appareil et des alertes actives, des utilisateurs actuellement connectés, d’une liste succincte des utilisateurs les plus fréquents et les moins fréquents, ainsi que des évaluations de sécurité qui détaillent le niveau d’exposition de l’appareil, les recommandations en matière de sécurité, les logiciels concernés et vulnérabilités découvertes.

### <a name="alerts-tab"></a>Onglet Alertes

L’onglet **alertes** contient la liste des alertes signalées sur l’appareil.

![Image de l’onglet Alertes pour le profil de l’ordinateur](../../media/mtp-machine-profile/alerts.png)

Vous pouvez personnaliser le nombre d’éléments affichés, ainsi que les colonnes affichées pour chaque élément. Le comportement par défaut consiste à répertorier 30 éléments par page et à afficher 11 colonnes sur Afficher.

Les colonnes de cet onglet incluent des informations sur la gravité de la menace qui a déclenché l’alerte, ainsi que sur l’État, l’état de l’enquête et l’identité de l’utilisateur auquel l’alerte a été affectée.

La colonne des *entités concernées* fait référence à l’ordinateur (entité) dont vous visualisez le profil que vous consultez actuellement, ainsi qu’aux autres machines de votre réseau qui sont affectées.

La sélection d’un élément dans cette liste permet d’ouvrir un lien vers l’alerte sélectionnée.

Cette liste peut être filtrée par gravité, État ou cessionnaire.

### <a name="timeline-tab"></a>Onglet chronologie

L’onglet **chronologie** inclut un graphique interactif et chronologique des événements déclenchés sur l’appareil. En déplacant la zone mise en surbrillance du graphique, vous pouvez afficher les événements sur des plages de temps différentes. Vous pouvez également taper dans une plage de dates personnalisée.

Sous le graphique se trouve une liste d’événements pour la plage de dates sélectionnée.

![Image de l’onglet chronologie pour le profil de l’ordinateur](../../media/mtp-machine-profile/timeline.png)

Le nombre d’éléments affichés et les colonnes de la liste peuvent être personnalisés. Les colonnes par défaut répertorient l’heure de l’événement, l’utilisateur actif, le type d’action, les entités (processus) et des informations supplémentaires sur l’événement.

La sélection d’un élément dans la liste ouvre un menu volant affichant un graphique d’entités d’événements, affichant les processus parents et enfants qui ont déclenché l’événement.

Cette liste peut être filtrée par type d’événement spécifique ; par exemple, des événements de registre ou des événements Smart Screen.

### <a name="security-recommendations-tab"></a>Onglet recommandations de sécurité

L’onglet **Security Recommendations** répertorie les actions que vous pouvez effectuer pour protéger l’appareil. La sélection d’un élément sur cette liste ouvre un menu volant dans lequel vous pouvez obtenir des instructions sur l’application de la recommandation.

![Image de l’onglet recommandations de sécurité pour le profil de l’ordinateur](../../media/mtp-machine-profile/security-recs.png)

Comme avec les onglets précédents, le nombre d’éléments affichés par page et les colonnes visibles peuvent être personnalisés.

L’affichage par défaut inclut des colonnes qui détaillent les faiblesses de sécurité traitées, la menace associée, le composant ou le logiciel associé concerné par la menace, et bien plus encore. Les éléments peuvent être filtrés selon l’état de la recommandation.

### <a name="software-inventory"></a>Inventaire des logiciels

L’onglet **inventaire logiciel** répertorie les logiciels installés sur l’appareil.

![Image de l’onglet inventaire logiciel pour le profil de l’ordinateur](../../media/mtp-machine-profile/software-inventory.png)

La vue par défaut affiche le fournisseur de logiciels, le numéro de version installé, le nombre de faiblesses logicielles connues, les informations de menace, le code de produit et les balises. Le nombre d’éléments affichés et les colonnes affichées peuvent être personnalisés.

La sélection d’un élément dans cette liste ouvre un lanceur contenant des détails supplémentaires sur le logiciel sélectionné, ainsi que le chemin d’accès et l’horodatage de la dernière fois que le logiciel a été trouvé.

Cette liste peut être filtrée par code de produit.

### <a name="discovered-vulnerabilities-tab"></a>Onglet vulnérabilités découvertes

L’onglet **vulnérabilités découvertes** répertorie les vulnérabilités et exploits courants (CVE) susceptibles d’affecter l’appareil.

![Image de l’onglet vulnérabilités découvertes pour le profil de l’ordinateur](../../media/mtp-machine-profile/discovered-vulnerabilities.png)

L’affichage par défaut répertorie la gravité de CVE, le score commun de vulnérabilité (CVS), le logiciel associé à CVE, le moment où le CVE a été publié, la date de la dernière mise à jour et les menaces associées à CVE.

Comme avec les onglets précédents, le nombre d’éléments affichés et les colonnes visibles peuvent être personnalisés.

La sélection d’un élément dans cette liste ouvrira un menu volant qui décrit le CVE.

### <a name="missing-kbs"></a>Ko manquants

L’onglet **Ko manquants** répertorie toutes les mises à jour Microsoft qui n’ont pas encore été appliquées à l’ordinateur. Le « Ko » en question sont des Articles de la [base de connaissances](https://support.microsoft.com/help/242450/how-to-query-the-microsoft-knowledge-base-by-using-keywords-and-query) qui décrivent ces mises à jour ; par exemple, [KB4551762](https://support.microsoft.com/help/4551762/windows-10-update-kb4551762).

![Image de l’onglet Ko manquants pour le profil de l’ordinateur](../../media/mtp-machine-profile/missing-kbs.PNG)

L’affichage par défaut répertorie le Bulletin contenant les mises à jour, la version du système d’exploitation, les produits concernés, les CVE traités, le numéro de la base de connaissances et les balises.

Le nombre d’éléments affichés par page et les colonnes affichées peuvent être personnalisés.

La sélection d’un élément ouvre un menu volant qui établit un lien vers la mise à jour.

## <a name="sidebar"></a>Gadgets

En regard de la zone de contenu principale de la page profil de l’ordinateur est l’encadré.

![Image de l’onglet du volet de navigation pour le profil d’ordinateur](../../media/mtp-machine-profile/sidebar.png)

Le volet de navigation fournit des informations de base importantes dans les sous-sections de petite taille, qui peuvent être ouvertes ou fermées.

* **Tags** -toutes les balises associées au périphérique
* **Informations de sécurité** -incidents ouverts, alertes actives, niveau d’exposition et niveau de risque
* **Détails des appareils** : domaine, système d’exploitation, groupe de biens, état d’intégrité, sensibilité des données et adresses IP
* **Activité réseau** : pour la première fois et pour la dernière fois, le périphérique a été vu sur le réseau

Cette section inclut également le nom et le niveau d’exposition du périphérique, ainsi qu’une icône indiquant s’il est actif sur le réseau.

## <a name="response-actions"></a>Actions de réponse

Les actions de réponse offrent un moyen rapide de se défendre et d’analyser les menaces.

![Image de l’onglet du volet de navigation pour le profil d’ordinateur](../../media/mtp-machine-profile/actions.PNG)

Les actions de réponse disponibles ici sont les suivantes :

* **Gérer les balises** : met à jour les balises personnalisées que vous avez appliquées à cet appareil.
* **Isoler l’ordinateur** : isole l’ordinateur du réseau de votre organisation tout en le gardant connecté à la protection avancée contre les menaces de Microsoft Defender. Vous pouvez choisir d’autoriser l’exécution d’Outlook, de teams et de Skype entreprise pendant que l’ordinateur est isolé, à des fins de communication.
* **Restreindre l’exécution de l’application** : empêche les applications qui ne sont pas signées par Microsoft de s’exécuter
* **Exécuter l’analyse antivirus** : met à jour les définitions de l’antivirus Windows Defender et exécute immédiatement une analyse antivirus. Choisissez entre analyse rapide ou analyse complète.
* **Recueillir** des informations sur l’ordinateur. Une fois l’enquête terminée, vous pouvez la télécharger.
* **Lancer une session Live Response session** : charge un environnement distant sur l’ordinateur pour les [examens de sécurité approfondis](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/live-response).
* **Lancer une enquête automatisée** : [enquête et corrige automatiquement les menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air). Bien que vous puissiez déclencher manuellement des analyses automatisées à exécuter à partir de cette page, [certaines stratégies d’alerte](https://docs.microsoft.com/microsoft-365/compliance/alert-policies?view=o365-worldwide#default-alert-policies) déclenchent des enquêtes automatiques.
* **Centre de notifications** : afficher l’état des actions soumises. Disponible uniquement si une autre action a déjà été sélectionnée.

## <a name="related-topics"></a>Sujets associés

* [Vue d’ensemble de la Protection Microsoft contre les menaces](microsoft-threat-protection.md)
* [Activer la Protection Microsoft contre les menaces](mtp-enable.md)
* [Examiner les entités sur les ordinateurs à l’aide de la réponse dynamique](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/live-response)
* [Recherche et réponse automatiques dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air)
