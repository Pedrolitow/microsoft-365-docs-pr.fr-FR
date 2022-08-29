---
title: Partager des alertes DLP
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
description: Découvrez comment partager des alertes de protection contre la perte de données aux utilisateurs disposant d’autorisations minimales pour l’investigation.
ms.openlocfilehash: 81336701a732a11e8ebd1b76e2e49ed758c00139
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67360554"
---
# <a name="share-data-loss-prevention-alerts-preview"></a>Partager des alertes de protection contre la perte de données (préversion)

Les [utilisateurs disposant des autorisations appropriées](dlp-configure-view-alerts-policies.md#roles) peuvent afficher les alertes Protection contre la perte de données Microsoft Purview (DLP) dans la console Alertes DLP. Toutefois, à mesure que les alertes sont triées et examinées, vous devrez peut-être les partager avec d’autres utilisateurs qui ne disposent pas, et ne devraient pas, d’autorisations complètes sur DLP et la console d’alertes.

Vous pouvez partager une alerte avec les utilisateurs indiquant que vous accordez des autorisations limitées à l’utilisation des procédures décrites dans cet article.

## <a name="before-you-begin"></a>Avant de commencer

Si vous n’êtes pas familiarisé avec les alertes DLP, consultez [Configurer et afficher des alertes pour les stratégies de protection contre la perte de données](/microsoft-365/compliance/dlp-configure-view-alerts-policies).

Dans cette procédure, vous devez créer un groupe de rôles personnalisé pour Purview. Si vous n’avez pas travaillé avec des autorisations, des rôles et des groupes de rôles dans Microsoft Purview, consultez [Autorisations dans le portail de conformité Microsoft Purview](/microsoft-365/compliance/microsoft-365-compliance-center-permissions) 

## <a name="configure-dlp-alert-urls-for-review"></a>Configurer les URL d’alerte DLP pour révision

1. Ouvrez le [portail de conformité Microsoft Purview](https://compliance.microsoft.com) avec un compte disposant d’autorisations d’Administration globales.

1. Créez un [groupe de rôles personnalisé](/microsoft-365/compliance/microsoft-365-compliance-center-permissions#create-a-custom-role-group) pour les utilisateurs avec lesquels vous souhaitez partager des alertes. Par exemple `DLPAlertInvestigator`. Ajoutez ces rôles au groupe :
    1. **Gestion de la conformité DLP en mode affichage uniquement** : obligatoire.
    1. **Visionneuse de contenu de classification des données** : obligatoire.
    1. **Aperçu** -  *ce rôle est facultatif*, affectez-le si le réviseur doit voir le contenu source.

1. Ajoutez les utilisateurs que vous avez créés dans le groupe de rôles personnalisé que vous venez de créer, dans cet exemple `DLPAlertInvestigator`.

1.  Ouvrez l’onglet **Alertes DLP** et sélectionnez l’alerte que vous souhaitez partager. Le volet volant s’ouvre.

1. Obtenez les valeurs **d’ID** d’alerte et **d’heure détectées** pour l’alerte.

![Image montrant les détails d’une alerte DLP](../media/dlp-alert-details1.png)

6. La valeur dans le champ **Heure détectée** est l’heure locale. Vous devez convertir cette valeur en heure UTC pour une utilisation dans le `creationtime` paramètre. Un certain nombre de convertisseurs de temps local à UTC sont disponibles via une recherche Internet.

7. Construisez l’URL partageable dans ce format :

`<compliance-portal-domain>/datalossprevention/alerts/eventdeeplink?eventid={eventId}&creationtime={creationTime}`
  
Par exemple :
 
`compliance.microsoft.com/datalossprevention/alerts/eventdeeplink?eventid=1eae3e53-c045-1c9b-ee00-08da7a6751dc&creationtime=2022-08-10T12:30:00Z`

Dans cet exemple, la valeur **heure détectée** est **le 9 août 2022 17:30** Heure d’été du Pacifique. Cette valeur est convertie en **10 août, 00:30** UTC ou `2022-08-10T12:30:00Z`

8. Vous pouvez partager ce lien avec des personnes du groupe que vous avez créé. Elles pourront accéder à l’alerte pour examen et investigation.

