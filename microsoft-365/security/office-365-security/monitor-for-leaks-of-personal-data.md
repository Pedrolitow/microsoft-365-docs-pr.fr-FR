---
title: Surveillance des fuites de données personnelles
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 02/07/2018
audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
- GDPR
- M365-security-compliance
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
description: Découvrez trois outils qui permettent de surveiller les fuites de données personnelles.
ms.openlocfilehash: 2a00d639be3b43fb56e26dca2725f2c3dac54b39
ms.sourcegitcommit: 222fb7fe2b26dde3d8591b61cc02113d6135012c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "49760541"
---
# <a name="monitor-for-leaks-of-personal-data"></a>Surveillance des fuites de données personnelles

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Il existe de nombreux outils qui peuvent être utilisés pour surveiller l’utilisation et le transport des données personnelles. Cette rubrique décrit trois outils qui fonctionnent correctement.

![Outils permettant de surveiller l’utilisation et le transport des données personnelles](../../media/Monitor-for-leaks-of-personal-data-image1.png)

Dans cette illustration :

- Commencez par les rapports sur la protection contre la perte de données Microsoft 365 pour surveiller les données personnelles dans SharePoint Online, OneDrive Entreprise et le courrier électronique en transit. Ces rapports offrent le meilleur niveau de détail pour surveiller les données personnelles. Toutefois, ces rapports n’incluent pas tous les services dans Office 365.

- Utilisez ensuite les stratégies d’alerte et le journal d’audit pour surveiller l’activité des services. Configurez la surveillance continue ou faites des recherches dans le journal d’audit pour identifier un incident. Le journal d’audit fonctionne sur tous les services (Sway, PowerBI, eDiscovery, Dynamics 365, Microsoft Flow, Microsoft Teams, l’activité d’administration, OneDrive Entreprise, SharePoint Online, le courrier électronique en transit et les boîtes aux lettres au repos). Les conversations Skype sont incluses dans les boîtes aux lettres au repos.

- Enfin, utilisez Microsoft Cloud App Security pour surveiller les fichiers contenant des données sensibles chez d’autres fournisseurs SaaS. Il sera bientôt possible d’utiliser des types d’informations sensibles et des étiquettes unifiées dans Azure Information Protection et Office avec Cloud App Security. Vous pouvez configurer des stratégies qui s’appliquent à toutes vos applications SaaS ou des applications spécifiques (Box, par exemple). Cloud App Security ne découvre pas les fichiers dans Exchange Online, y compris les fichiers joints à un courrier électronique.

## <a name="data-loss-prevention-reports"></a>Rapports de protection contre la perte de données

Après avoir créé des stratégies de protection contre la perte de données, vous voulez vérifier qu’elles fonctionnent comme prévu et vous aident à maintenir la conformité. Avec les rapports DLP d’Office 365, vous pouvez rapidement visualiser le nombre de correspondances de stratégie DLP, de remplacements et de faux positifs, savoir si ce nombre augmente ou diminue dans le temps, filtrer le rapport de différentes manières et afficher plus de détails en sélectionnant un point sur une ligne du graphique.

Vous pouvez utiliser les rapports DLP pour :

- Vous concentrer sur des périodes de temps spécifiques et comprendre les raisons des pics et des tendances.

- Découvrir les processus d’entreprise qui enfreignent les stratégies DLP de votre organisation.

- Comprendre l’incidence des stratégies DLP sur l’entreprise.

- Afficher les motifs présentés par les utilisateurs lorsqu'ils passent outre une stratégie ou signalent un faux positif.

- Vérifier la conformité avec une stratégie DLP spécifique en affichant les correspondances pour cette stratégie.

- Afficher la liste des fichiers avec des données sensibles qui correspondent à vos stratégies DLP dans le volet de détails.

En outre, vous pouvez utiliser les rapports DLP pour affiner vos stratégies DLP lorsque vous les exécutez en mode test.

Les rapports DLP sont dans le centre de sécurité et le centre de conformité. Accéder aux rapports \>Afficher des rapports. Sous Protection contre la perte de données (DLP), choisissez soit Correspondances avec les règles et les stratégies DLP ou Remplacements et faux positifs DLP.

Pour plus d’informations, consultez la rubrique [Affichage des rapports de protection contre la perte de données](https://docs.microsoft.com/microsoft-365/compliance/view-the-dlp-reports).

![Rapport affichant les correspondances de stratégie DLP](../../media/Monitor-for-leaks-of-personal-data-image2.png)

## <a name="audit-log-and-alert-policies"></a>journal d’audit et stratégies d’alerte

Le journal d’audit contient les événements Exchange Online, SharePoint Online, OneDrive Entreprise, Azure Active Directory, Microsoft Teams, Power BI, Sway et d’autres services.

Le Centre de sécurité et de conformité propose deux méthodes pour surveiller et générer des rapports sur la base du journal d’audit :

- Configurer des stratégies d’alerte, afficher des alertes et surveiller les tendances : utilisez les nouveaux outils de tableau de bord d’alertes et de stratégie d’alerte dans le Centre de sécurité et de conformité.

- Effectuer des recherches directement dans le journal d’audit : vous pouvez rechercher tous les événements dans une plage de dates spécifiée ou filtrer les résultats en fonction de critères spécifiques, tels que l’utilisateur ayant effectué l’action, l’action ou l’objet cible.

Les équipes de conformité et de sécurité des informations peuvent utiliser ces outils pour revoir de façon proactive les activités effectuées par les utilisateurs finaux et les administrateurs dans les services. Des alertes automatiques peuvent être configurées pour envoyer des notifications par courrier électronique lorsque certaines activités se produisent sur des collections de sites spécifiques (par exemple, lorsque le contenu est partagé à partir de sites connus pour contenir des informations relatives au RGPD). Ainsi, ces équipes peuvent suivre les utilisateurs afin de vérifier que les stratégies de sécurité d’entreprise sont suivies, ou de fournir des formations supplémentaires.

Les équipes de sécurité des informations peuvent aussi effectuer des recherches dans le journal pour enquêter sur des violations de données présumées, déterminer la cause initiale et l’étendue de la violation. Cette fonctionnalité intégrée facilite la conformité à l’article 33 et 34 du RGPD, qui exige que des notifications soient fournies à l’autorité de surveillance du RGPD et aux personnes victimes d’une violation de données sur une période donnée. Les entrées du journal d’audit sont conservées pendant 90 jours seulement au sein du service (il est souvent recommandé que ces journaux soient conservés pour des périodes de temps plus longues et de nombreuses organisations en ont fait la demande).

Il existe des solutions qui s’abonnent aux journaux d’audit unifiés via l’API Activité de gestion Microsoft et qui peuvent à la fois stocker des entrées du journal et fournir des alertes et des tableaux de bord avancés. [Microsoft Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/oms-solution-office-365) en est un exemple.

Plus d’informations sur les stratégies d’alerte et l’exécution d’une recherche dans le journal d’audit :

- [Stratégies d’alerte dans le Centre de sécurité et de conformité Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/alert-policies)

- [Effectuer des recherches dans le journal d’audit dans le Centre de sécurité et de conformité Office 365](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log) (introduction)

- [Activer ou désactiver la recherche dans le journal d’audit](https://docs.microsoft.com/microsoft-365/compliance/turn-audit-log-search-on-or-off)

- [Rechercher le journal d’audit](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance)

- [Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog) (cmdlet)

- [Propriétés détaillées dans le journal d’audit](https://docs.microsoft.com/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log)

## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security

Microsoft Cloud App Security vous permet de découvrir d’autres applications SaaS utilisées dans vos réseaux et les données sensibles qui sont envoyées vers et depuis ces applications.

Microsoft Cloud App Security est un service complet fournissant une grande visibilité, des contrôles précis et une meilleure protection contre les menaces pour vos applications cloud. Il identifie plus de 15 000 applications cloud dans votre réseau (de tous les appareils) et fournit une notation des risques et une analyse et évaluation continues des risques. Aucun agent n’est obligatoire : les informations sont collectées à partir de vos pare-feu et proxys afin d’offrir une visibilité et un contexte complets pour l’utilisation du cloud et du Shadow IT.

Pour mieux comprendre votre environnement cloud, la fonctionnalité d’examen de Cloud App Security fournit une grande visibilité sur l’ensemble des activités, fichiers et comptes pour les applications approuvées et gérées. Vous pouvez obtenir des informations détaillées sur un niveau de fichier et découvrir où se déplacent les données dans les applications cloud.

Pour consulter des exemples, l’illustration suivante décrit deux stratégies Cloud App Security qui peuvent vous aider avec le RGPD.

![Exemple de stratégies Cloud App Security](../../media/Monitor-for-leaks-of-personal-data-image3.png)

La première stratégie signale lorsque des fichiers avec un attribut PII prédéfini ou une expression personnalisée que vous choisissez sont partagés en dehors de l’organisation à partir des applications SaaS que vous choisissez.

La seconde stratégie bloque les téléchargements de fichiers sur des appareils non gérés. Vous choisissez les attributs dans les fichiers à rechercher et les applications SaaS auxquelles vous souhaitez appliquer la stratégie.

Les types d’attribut suivants seront bientôt disponibles dans Cloud App Security :

- Types d’informations sensibles
- Étiquettes unifiées dans Microsoft 365 et Azure information protection

### <a name="cloud-app-security-dashboard"></a>Tableau de bord Cloud App Security

Si vous n’avez pas encore commencé à utiliser Cloud App Security, commencez par l’activer. Pour accéder à Cloud App Security : <https://portal.cloudappsecurity.com>.

Remarque : veillez à activer l’option 'Analyser automatiquement les fichiers pour les étiquettes de classification Azure Information Protection' (dans les paramètres généraux) lors de la prise en main de Cloud App Security ou avant d’attribuer des étiquettes. Après la configuration, Cloud App Security n’analyse pas de nouveau les fichiers existants tant qu’ils ne sont pas modifiés.

![Tableau de bord affichant des informations sur les alertes](../../media/Monitor-for-leaks-of-personal-data-image4.png)

Plus d’informations :

- Rubrique relative au [déploiement de Cloud App Security](https://docs.microsoft.com/cloud-app-security/getting-started-with-cloud-app-security)

- Rubrique relative aux [informations supplémentaires concernant Microsoft Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security)

- Rubrique relative au [blocage des téléchargements d’informations sensibles à l’aide du proxy Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/use-case-proxy-block-session-aad)

## <a name="example-file-and-activity-policies-to-detect-sharing-of-personal-data"></a>Exemple de stratégies d’activité et de fichier pour détecter le partage de données personnelles

### <a name="detect-sharing-of-files-containing-pii--credit-card-number"></a>Détection du partage de fichiers contenant des informations PII : numéro de carte de crédit

Alerte lorsqu’un fichier contenant un numéro de carte de crédit est partagé à partir d’une application cloud approuvée.

****

|Contrôle|Paramètres|
|---|---|
|Type de stratégie|Stratégie de fichier|
|Modèle de stratégie|Aucun modèle|
|Gravité de la stratégie|Importante|
|Catégorie|DLP|
|Paramètres de filtre|Niveau d’accès = Public (Internet), Public, Externe <p> Application = \<select apps\> (utiliser ce paramètre pour limiter la surveillance à des applications SaaS spécifiques)|
|Appliquer à|Tous les fichiers, tous les propriétaires|
|Inspection du contenu|Inclut les fichiers qui correspondent à une expression présente : Tous les pays: Finance: Numéro de carte de crédit <p> N’exige pas de contexte approprié : désactivé (ce paramètre correspondra aux mots-clés et aux expressions régulières) <p> Inclut les fichiers avec au moins 1 correspondance <p> Annuler le masquage des 4 derniers caractères de la violation : activé|
|Alertes|Crée une alerte pour chaque fichier correspondant : activé <p> Limite quotidienne d’alertes : 1 000 <p> Sélectionner une alerte en tant qu’e-mail : activé <p> À : infosec@contoso.com|
|Gouvernance|Microsoft OneDrive Entreprise <p> Donner un caractère privé : sélectionner Supprimer les utilisateurs externes <p> Tous les autres paramètres : désactivé <p> Microsoft SharePoint Online <p> Donner un caractère privé : sélectionner Supprimer les utilisateurs externes <p> Tous les autres paramètres : désactivé|
|

Stratégies similaires :

- Détection du partage de fichiers contenant des informations PII : adresse e-mail
- Détection du partage de fichiers contenant des informations PII : numéro de passeport

### <a name="detect-customer-or-hr-data-in-box-or-onedrive-for-business"></a>Détection des données client ou RH dans Box ou OneDrive Entreprise

Alerte lorsqu’un fichier étiqueté en tant que Données client ou Données RH est chargé dans OneDrive Entreprise ou Box.

Remarques :

- La surveillance de Box requiert un connecteur configuré à l’aide du kit de développement logiciel (SDK) du connecteur de l’API.
- Cette stratégie exige des fonctionnalités qui sont actuellement en Private Preview.

****

|Contrôle|Paramètres|
|---|---|
|Type de stratégie|Stratégie d’activité|
|Modèle de stratégie|Aucun modèle|
|Gravité de la stratégie|Importante|
|Catégorie|Contrôle partagé|
|Agir sur|Activité unique|
|Paramètres de filtre|Type d’activité = Charger un fichier <p> Application = Microsoft OneDrive Entreprise et Box <p> Étiquette de classification (actuellement en Private Preview) : Azure Information Protection = données sur les clients, ressources humaines - données sur le salaire, ressources humaines - données sur les employés|
|Alertes|Créer une alerte : activé <p> Limite quotidienne d’alertes : 1 000 <p> Sélectionner une alerte en tant qu’e-mail : activé <p> À : infosec@contoso.com|
|Gouvernance|Toutes les applications <p> Mettre l’utilisateur en quarantaine : activé <p> Tous les autres paramètres : désactivé <p> Office 365 <p> Mettre l’utilisateur en quarantaine : activé <p> Tous les autres paramètres : désactivé|
|

Stratégies similaires :

- Détection de téléchargements volumineux de données client ou de données RH : alerte lorsqu’un grand nombre de fichiers contenant des données client ou des données RH ont été téléchargés par un utilisateur unique dans un court délai.
- Détection du partage de données clients et de données RH : alerte lorsque des fichiers contenant des données clients ou des données RH sont partagés.
