---
title: En savoir plus sur le tableau de bord Alertes de protection contre la perte de données
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez les alertes de protection contre la perte de données et le tableau de bord des alertes.
ms.openlocfilehash: b6fd698e535e006149f6ce3a2a5bc57d0c92c7e2
ms.sourcegitcommit: 07dea2aa98daf0c4086f8590375167830027c802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51760733"
---
# <a name="learn-about-the-data-loss-prevention-alerts-dashboard"></a>En savoir plus sur le tableau de bord Alertes de protection contre la perte de données

Lorsque les critères d'une stratégie de protection contre la perte de données (DLP) correspondent aux actions qu'un utilisateur réalise sur un élément sensible, la stratégie peut générer une alerte. Cela peut entraîner un volume élevé d'alertes. Les alertes DLP sont collectées dans le tableau de bord des alertes. Le tableau de bord des alertes vous permet d'effectuer une recherche approfondie de tous les détails concernant la correspondance de stratégie.  

<!-- [Microsoft 365 compliance center](https://compliance.microsoft.com/)-->

## <a name="workloads"></a>Charges de travail

Le tableau de bord de gestion des alertes [DLP,](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts)dans le Centre de conformité [Microsoft 365,](https://compliance.microsoft.com/)affiche des alertes pour les stratégies DLP sur ces charges de travail :

- Exchange
- SharePoint
- OneDrive
- Teams
- appareils Windows 10 

> [!TIP]
> Les clients qui utilisent [endpoint DLP](endpoint-dlp-learn-about.md) et éligibles à [Teams DLP](dlp-microsoft-teams.md) voient leurs alertes de stratégie DLP de point de terminaison et les alertes de stratégie DLP Teams dans le tableau de bord de gestion des alertes DLP.

## <a name="single-alert-and-aggregate-alert"></a>Alerte unique et alerte agrégée

Il existe deux types d'alertes qui peuvent être configurés dans les stratégies DLP.

Les alertes à événement unique sont généralement utilisées dans les stratégies qui surveillent les événements hautement sensibles qui se produisent dans un volume faible, comme un seul **e-mail** avec 10 numéros de carte de crédit client ou plus envoyés à l'extérieur de votre organisation.

**Les alertes d'événement** d'agrégation sont généralement utilisées dans les stratégies qui surveillent les événements qui se produisent dans un volume plus élevé sur une période de temps. Par exemple, une alerte d'agrégation peut être déclenchée lorsque 10 e-mails individuels avec un numéro de carte de crédit client sont envoyés en dehors de votre organisation pendant 48 heures.

## <a name="types-of-events"></a>Types d’événements

Voici quelques événements associés à une alerte. Dans l'interface utilisateur, vous pouvez choisir un événement particulier pour afficher ses détails. 

### <a name="event-details"></a>Détails de l'événement

|Nom de la propriété  |Description  |Types d’événements  |
|---------|---------|---------|
|ID |ID unique associé à l'événement |tous les événements |
|Emplacement |charge de travail où l'événement a été détecté|tous les événements |
|heure de l’activité     |heure de l’activité de l’utilisateur qui correspond aux critères de la stratégie DLP |

### <a name="impacted-entities"></a>Entités impactées

|Nom de la propriété |Description| Types d’événements|
|---------|---------|---------|
|utilisateur | utilisateur qui a pris l’action à l’origine de la correspondance de stratégie | tous les événements|
|hostname | nom d’hôte de l’ordinateur sur lequel la correspondance de stratégie DLP s’est produite | événements d’appareil|
|Adresse IP | Adresse IP de l’ordinateur sur lequel la correspondance de stratégie DLP s’est produite | événements d’appareil|
|sha1 |Hachage SHA-1 du fichier | événements d’appareil|
|sha256 | Hachage SHA-256 du fichier | événements d’appareil|
|ID d’appareil MDATP | ID MDATP de l’appareil de point de terminaison|
|taille du fichier | taille du fichier| Événements SharePoint, OneDrive et appareil|
|chemin d’accès du fichier | chemin d’accès absolu de l’élément impliqué dans la correspondance de stratégie DLP | Événements SharePoint, OneDrive et appareils|
|destinataires du courrier électronique |si un e-mail était l’élément sensible qui correspond à la stratégie DLP, ce champ inclut les destinataires de cet e-mail| Événements Exchange|
|objet de l’e-mail |objet de l’e-mail qui correspond à la stratégie DLP |Événements Exchange|
|pièces jointes d’e-mail | noms des pièces jointes dans l’e-mail qui correspondent à la stratégie DLP| Événements Exchange|
|propriétaire du site |nom du propriétaire du site| Événements SharePoint et OneDrive|
|URL du site |complète de l’URL du site SharePoint ou OneDrive où la correspondance de stratégie DLP s’est produite |Événements SharePoint et OneDrive|
|fichier créé |heure de création du fichier qui correspond à la stratégie DLP |Événements SharePoint et OneDrive|
|fichier de la dernière modification | la dernière fois que le fichier qui correspond à la stratégie DLP a été modifié | Événements SharePoint et OneDrive|
|taille du fichier | taille du fichier qui correspond à la stratégie DLP |Événements SharePoint et OneDrive|
|propriétaire du fichier |propriétaire du fichier qui correspond à la stratégie DLP |Événements SharePoint et OneDrive|  

### <a name="policy-details"></a>Détails de la stratégie

|Nom de la propriété |Description |Types d’événements |
|---------|---------|---------|
|Stratégie DLP en correspondance |nom de la stratégie DLP en correspondance |tous les événements|
|règle en correspondance |nom de la règle de stratégie DLP qui correspond |tous les événements|
|types d’informations sensibles détectés|Sits détectés dans le cadre de la correspondance de stratégie DLP |tous les événements|
|actions prises |actions qui ont été prises à l’origine de la correspondance de stratégie DLP| tous les événements|
|action de violation | action sur l'appareil de point de terminaison qui a élevé l'alerte DLP| événements d'appareil | 
|stratégie de overrode utilisateur |l'utilisateur a-t-il remplacer la stratégie via un conseil de stratégie | tous les événements|
|justification du remplacement de l'utilisation |texte de la raison fournie par l'utilisateur pour le remplacement ; | tous les événements|   

## <a name="see-also"></a>Voir aussi

- [Mise en place du tableau de bord d'alerte de protection contre la perte de données](dlp-alerts-dashboard-get-started.md)
- [Où commencer avec la protection contre la perte de données](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention)