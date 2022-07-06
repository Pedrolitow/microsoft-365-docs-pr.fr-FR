---
title: En savoir plus sur le tableau de bord des alertes DLP
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
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Découvrez les alertes de protection contre la perte de données et le tableau de bord des alertes.
ms.openlocfilehash: 1551b247e3302af6dc8ed9af62a88f2c24415122
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636158"
---
# <a name="learn-about-the-data-loss-prevention-alerts-dashboard"></a>En savoir plus sur le tableau de bord des alertes de protection contre la perte de données

Lorsque les critères d’une stratégie Protection contre la perte de données Microsoft Purview (DLP) sont mis en correspondance par les actions qu’un utilisateur effectue sur un élément sensible, la stratégie peut générer une alerte. Cette situation peut entraîner un volume élevé d’alertes. Les alertes DLP sont collectées dans le tableau de bord des alertes. Le tableau de bord des alertes vous offre un emplacement unique pour effectuer une investigation approfondie de tous les détails sur la correspondance de stratégie.  

<!-- [Microsoft Purview compliance portal](https://compliance.microsoft.com/)-->

## <a name="workloads"></a>Charges de travail

Le [tableau de bord de gestion des alertes DLP](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts), dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>, affiche des alertes pour les stratégies DLP sur ces charges de travail :

- Exchange
- SharePoint
- OneDrive
- Teams
- Appareils Windows 10 

> [!TIP]
> Les clients qui utilisent [endpoint DLP](endpoint-dlp-learn-about.md) qui sont éligibles à [Teams DLP](dlp-microsoft-teams.md) voient leurs alertes de stratégie DLP de point de terminaison et les alertes de stratégie DLP Teams dans le tableau de bord de gestion des alertes DLP.

## <a name="single-alert-and-aggregate-alert"></a>Alerte unique et alerte agrégée

Il existe deux types d’alertes qui peuvent être configurées dans les stratégies DLP.

Les **alertes d’événement unique sont généralement utilisées dans les** stratégies qui surveillent les événements hautement sensibles qui se produisent dans un volume faible, comme un seul e-mail avec 10 numéros de carte de crédit client ou plus envoyés en dehors de votre organisation.

**Les alertes d’événement d’agrégation sont généralement utilisées dans les** stratégies qui surveillent les événements qui se produisent dans un volume plus élevé sur une période donnée. Par exemple, une alerte d’agrégation peut être déclenchée quand 10 e-mails individuels contenant chacun un numéro de carte de crédit client sont envoyés en dehors de votre organisation pendant 48 heures.

## <a name="types-of-events"></a>Types d’événements

Voici quelques-uns des événements associés à une alerte. Dans l’interface utilisateur, vous pouvez choisir un événement particulier pour afficher ses détails. 

### <a name="event-details"></a>Détails de l'événement

|Nom de la propriété  |Description  |Types d’événements  |
|---------|---------|---------|
|ID |ID unique associé à l’événement |tous les événements |
|Emplacement |charge de travail dans laquelle l’événement a été détecté|tous les événements |
|temps d’activité     |heure de l’activité de l’utilisateur qui correspond aux critères de la stratégie DLP |

### <a name="affected-entities"></a>Entités affectées

|Nom de la propriété |Description| Types d’événements|
|---------|---------|---------|
|utilisateur | utilisateur qui a effectué l’action qui a provoqué la correspondance de stratégie | tous les événements|
|Hostname | nom d’hôte de l’ordinateur sur lequel la correspondance de stratégie DLP s’est produite | événements d’appareil|
|Adresse IP | Adresse IP de l’ordinateur sur lequel la correspondance de stratégie DLP s’est produite | événements d’appareil|
|sha1 |Hachage SHA-1 du fichier | événements d’appareil|
|sha256 | Hachage SHA-256 du fichier | événements d’appareil|
|ID d’appareil MDATP | ID MDATP de l’appareil de point de terminaison|
|taille du fichier | taille du fichier| Événements SharePoint, OneDrive et appareil|
|chemin d’accès du fichier | chemin absolu de l’élément impliqué dans la correspondance de stratégie DLP | Événements SharePoint, OneDrive et appareils|
|destinataires de l’e-mail |si un e-mail était l’élément sensible qui correspondait à la stratégie DLP, ce champ inclut les destinataires de cet e-mail| Événements Exchange|
|objet de l’e-mail |objet de l’e-mail correspondant à la stratégie DLP |Événements Exchange|
|pièces jointes d’e-mail | noms des pièces jointes dans l’e-mail correspondant à la stratégie DLP| Événements Exchange|
|propriétaire du site |nom du propriétaire du site| Événements SharePoint et OneDrive|
|URL du site |complète de l’URL du site SharePoint ou OneDrive où la correspondance de stratégie DLP s’est produite |Événements SharePoint et OneDrive|
|fichier créé |heure de création du fichier correspondant à la stratégie DLP |Événements SharePoint et OneDrive|
|dernier fichier modifié | la dernière fois que le fichier correspondant à la stratégie DLP a été modifié | Événements SharePoint et OneDrive|
|taille du fichier | taille du fichier correspondant à la stratégie DLP |Événements SharePoint et OneDrive|
|propriétaire du fichier |propriétaire du fichier correspondant à la stratégie DLP |Événements SharePoint et OneDrive|  

### <a name="policy-details"></a>Détails de la stratégie

|Nom de la propriété |Description |Types d’événements |
|---------|---------|---------|
|Stratégie DLP mise en correspondance |nom de la stratégie DLP correspondante |tous les événements|
|règle mise en correspondance |nom de la règle de stratégie DLP correspondante |tous les événements|
|types d’informations sensibles (SIT) détectés|SIT détectés dans le cadre de la correspondance de stratégie DLP |tous les événements|
|actions prises |actions qui ont provoqué la correspondance de stratégie DLP| tous les événements|
|violation de l’action | action sur l’appareil de point de terminaison qui a déclenché l’alerte DLP| événements d’appareil | 
|stratégie de dépassement d’utilisateur |l’utilisateur a-t-il remplacé la stratégie par le biais d’un conseil de stratégie ? | tous les événements|
|utiliser la justification de remplacement |le texte de la raison fournie par l’utilisateur pour le remplacement | tous les événements|   

## <a name="see-also"></a>Voir aussi

- [Prise en main du tableau de bord des alertes de protection contre la perte de données](dlp-alerts-dashboard-get-started.md)
- [Par où commencer avec la protection contre la perte de données](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention)
