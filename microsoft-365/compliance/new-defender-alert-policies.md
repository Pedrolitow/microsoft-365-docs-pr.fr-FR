---
title: Nouvelles stratégies d’alerte dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkDEFENDER
ROBOTS: noindex,nofollow
description: Nous publions de nouvelles stratégies d’alerte dans Microsoft Defender pour Office 365. Nous mettons également remplacé deux stratégies d’alerte existantes qui ont été mises hors service.
ms.openlocfilehash: 339d16f7cd4e481d408a13d2e738cdef9fc991bf
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939628"
---
# <a name="new-alert-policies-in-microsoft-defender-for-office-365"></a>Nouvelles stratégies d’alerte dans Microsoft Defender pour Office 365

Microsoft Defender pour Office 365 présente de nouvelles stratégies d’alerte améliorées relatives aux détections postérieures à la remise. Ceci inclut des améliorations aux playbooks Enquêtes et réponses automatisées (AIR) qui y sont associés. En outre, nous modifions la classification de gravité pour six stratégies d’alerte par défaut pour mieux aligner les alertes générées par ces stratégies sur leur impact dans votre organisation.

## <a name="post-delivery-detections"></a>Détections postérieures à la remise

Nous présenteront quatre nouvelles stratégies d’alerte par défaut relatives aux détections postérieures à la remise après la suppression des messages de boîte de réception par la Purge automatique zéro heure (ZAP) de Microsoft Defender pour Office 365. Ces quatre nouvelles stratégies d’alerte remplaceront deux stratégies d’alerte par défaut existantes couvrant les scénarios ZAP et fourniront aux organisations des détails améliorés sur la détection sous-jacente et les indicateurs associés. Ces alertes (et les playbooks AIR déclenchés par ces alertes) captureront avec exactitude les menaces des e-mails et des entités, notamment si l’URL pointe vers un fichier malveillant ou si le fichier contient une URL malveillante.

Le tableau suivant répertorie les nouvelles stratégies d’alerte et les stratégies d’alerte existantes qui seront supprimées. Consultez la section [Quelle sera la répercussion sur votre organisation](#how-this-will-affect-your-organization) pour obtenir des détails sur le déploiement.

|Stratégie d’alerte nouvelle ou existante|Nom de la stratégie d’alerte|ID de la stratégie d’alerte|
|---|---|---|
|Nouveau|**Messages de courrier contenant une URL malveillante supprimée après la remise**|8E6BA277-EF39-404E-AAF1-294F6D9A2B88|
|Nouveau|**Messages de courrier contenant un fichier malveillant supprimé après la remise**|4b1820ec-39dc-45f3-abf6-5ee80df51fd2|
|Nouveau|**Messages de courrier d’une campagne remis, puis supprimés ultérieurement**|c8522cbb-9368-4e25-4ee9-08d8d899dfab|
|Nouveau|**Messages électroniques supprimés après la remise**|b8f6b088-5487-4c70-037c-08d8d71a43fe|
|Existant (sera supprimé)|**Messages de courrier contenant des URL d’hameçonnage supprimées après la remise**|EA8169FA-0678-4751-8854-AEBEA7ADECEB|
|Existant (sera supprimé)|**Messages de courrier contenant un programme malveillant supprimé après la remise**|0179B3F7-3FDA-40C3-8F24-278563978DBB|

## <a name="alert-severity-enhancements"></a>Améliorations de la gravité de l’alerte

Le tableau suivant identifie les stratégies d’alerte par défaut dont les classifications de gravité sont en cours de modification. Nous modifions la classification de gravité de ces stratégies d’alerte pour mieux les aligner sur le risque potentiel et l’impact sur votre organisation et pour aider vos équipes de sécurité à classer par ordre de priorité les alertes générées par ces stratégies.

|Alerte|ID de la stratégie d’alerte|Ancienne gravité|Nouvelle gravité|
|---|---|---|---|
|**Activité suspecte de transfert d’e-mail**|BFD48F06-0865-41A6-85FF-ADB746423EBF|Moyen|Élevé|
|**E-mail signalé par l’utilisateur en tant que programme malveillant ou hameçonnage**|B26A5770-0C38-434A-9380-3A3C2C27BBB3|Informatif|Faible|
|**Augmentation inhabituelle des e-mails signalés en tant que hameçonnage**|A00D8C62-9320-4EEA-A7E5-966B9AC09558|Élevé|Moyen|
|**Résultat de soumission administrateur terminé**|AE9B83DD-6039-4EA9-B675-6B0AC3BF4A41|Faible|Informatif|
|**Création de règle de redirection/transfert**|D59A8FD4-1272-41EE-9408-86F7BCF72479|Faible|Informatif|
|**Recherche eDiscovery démarrée ou exportée**|6FDC5710-3998-47F0-AFBB-57CEFD7378A|Meduim|Informatif|

## <a name="when-will-these-changes-happen"></a>À quelle période se produiront ces modifications

Le tableau suivant définit la période à laquelle les nouvelles stratégies d’alerte commenceront à déclencher des alertes postérieures à la remise. Le tableau indique également le moment où les deux stratégies d’alerte existantes seront supprimées.

|Stratégie d’alerte|Date|
|---|---|
|**Messages de courrier contenant une URL malveillante supprimée après la remise** (nouvelle)|Les alertes se déclencheront le 11 avril 2021|
|**Messages de courrier contenant un fichier malveillant supprimé après la remise** (nouvelle)|Les alertes se déclencheront le 11 avril 2021|
|**Messages de courrier d’une campagne remis, puis supprimés ultérieurement** (nouvelle)|Les alertes se déclencheront le 28 mai 2021|
|**Courriers malveillants remis, puis supprimés ultérieurement** (nouvelle)|Les alertes se déclencheront le 28 mai 2021|
|**Messages de courrier contenant des URL d’hameçonnage supprimées après la remise** (existante, sera supprimée)|La stratégie d’alerte a été supprimée en juin 2021. Voir la section [Ce que vous devez faire pour vous préparer à ces changements](#what-you-need-to-do-to-prepare-for-these-changes).|
|**Messages de courrier contenant un programme malveillant supprimé après la remise** (existante, sera supprimée)|La stratégie d’alerte a été supprimée en juin 2021. Voir la section [Ce que vous devez faire pour vous préparer à ces changements](#what-you-need-to-do-to-prepare-for-these-changes).|

Le déploiement vers toutes les organisations des modifications de gravité d’alerte s’effectuera avant le 14 mai 2021.

## <a name="how-this-will-affect-your-organization"></a>Quelle sera la répercussion sur votre organisation

Les nouvelles alertes seront lancées et déclencheront les Enquêtes et réponses automatisées (AIR) dans votre organisation à compter des dates indiquées ci-dessus. Pour réduire l’impact sur les organisations de sécurité qui ont mis en œuvre les deux alertes qui doivent être supprimées, des alertes déclenchées par les stratégies d’alerte existantes *et* des alertes déclenchées par les nouvelles stratégies d’alerte s’afficheront entre le 5 avril et le 28 mai 2021. Ceci donne le temps aux équipes de sécurité de traiter les modifications requises. Pour faciliter le travail des équipes de sécurité avec le volume accru d’alertes au cours de cette brève période, les alertes existantes et les nouvelles alertes seront corrélées dans la même enquête et dans le même incident. Plus précisément, cela inclut le comportement suivant pour les alertes, les enquêtes AIR et les incidents :

- **Alertes** : par défaut, les paires d’alertes suivantes s’afficheront dans les alertes existantes et les nouvelles alertes :

  - **Messages de courrier contenant des URL d’hameçonnage supprimées après la remise** ET **Messages de courrier contenant des URL malveillantes supprimées après la remise**

  - **Messages de courrier contenant un programme malveillant supprimé après la remise** ET **Messages de courrier contenant un fichier malveillant supprimé après la remise**

  ![Paires d’alertes pour les nouvelles alertes et les alertes existantes.](../media/DefenderAlerts.png)

   Pour plus d’informations sur la gestion de ces paires d’alertes, voir la section [Ce que vous devez faire pour vous préparer à ces changements](#what-you-need-to-do-to-prepare-for-these-changes).

- **Enquêtes et réponses automatisées (AIR)** : les alertes seront corrélées dans une seule enquête AIR, l’une des alertes étant classée en tant que « déclenchante » et l’autre en tant que « répétée ».

  ![Paires d’alertes dans les enquêtes AIR.](../media/AIRAlerts.png)

- **Incidents** : les deux alertes seront corrélées dans le même incident.

  ![Paires d’alertes dans les incidents.](../media/IncidentsAlerts.png)

## <a name="what-you-need-to-do-to-prepare-for-these-changes"></a>Ce que vous devez faire pour vous préparer à ces changements

La façon dont votre organisation utilise ces alertes déterminera ce que vous devez faire pour vous préparer. Si vous avez mis en œuvre les alertes et que vous les utilisez ou que vous les utilisez via une API, une notification par e-mail d’alerte ou dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a> ou le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Portail Microsoft 365 Defender</a>, vous devrez modifier vos flux de travail.

**Si vous n’avez pas mis en œuvre ces alertes, vous pouvez effectuer l’une des opérations suivantes :**

- Désactivez les stratégies d’alerte suivantes (qui sont en cours de suppression) pour diminuer le volume d’alertes dans votre organisation :

  - **Messages de courrier contenant des URL d’hameçonnage supprimées après la remise**

  - **Messages de courrier contenant un programme malveillant supprimé après la remise**

- Ne rien faire. Nous désactiverons les stratégies d’alerte existantes le 28 mai 2021.

**Si vous avez mis en œuvre ces alertes** :

- Commencez à consommer les nouvelles alertes en tant que partie de votre flux de travail, en prévision de la suppression de la stratégie d’alerte existante le 28 mai 2021. Si vous disposez d’une logique personnalisée dans votre système de tickets, une boîte aux lettres de sécurité dans laquelle vous recevez des notifications d’alerte par e-mail, ou une solution d’Informations de sécurité et gestion d'événements (SIEM) qui dépend du nom d’alerte ou de l’ID de stratégie d’alerte (CorrelationId), vous devrez modifier la logique pour prendre la modification en charge.

  > [!NOTE]
  > Les informations dans les alertes, enquêtes et incidents n’ont pas changé. En fait, ces informations ont été améliorées à l’aide de détails supplémentaires sur les menaces qui y sont associées.

- Une fois les modifications effectuées, vous pouvez désactiver les stratégies d’alerte existantes pour diminuer le volume d’alertes dans votre organisation :

  - **Messages de courrier contenant des URL d’hameçonnage supprimées après la remise**

  - **Messages de courrier contenant un programme malveillant supprimé après la remise**

  Vous pouvez également laisser ces stratégies d’alerte activées jusqu’à leur suppression le 28 mai 2021.
