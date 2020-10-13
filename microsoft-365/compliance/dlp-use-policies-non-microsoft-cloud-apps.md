---
title: Utiliser des stratégies de protection contre la perte de données pour les applications Cloud non Microsoft (aperçu)
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
description: Découvrez comment utiliser les stratégies DLP pour les applications Cloud non Microsoft.
ms.openlocfilehash: dd5a7a4bc0725d0785daec6b7635047cd91f20a2
ms.sourcegitcommit: 39af527404cb06e05c5aa4550dbec39aec133016
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "48422732"
---
# <a name="use-data-loss-prevention-policies-for-non-microsoft-cloud-apps-preview"></a>Utiliser des stratégies de protection contre la perte de données pour les applications Cloud non Microsoft (aperçu)

Les stratégies de protection contre la perte de données (DLP) pour les applications Cloud non-Microsoft font partie de la suite de fonctionnalités DLP Microsoft 365. à l’aide de ces fonctionnalités, vous pouvez découvrir et protéger des éléments sensibles dans les services Microsoft 365. Pour plus d’informations sur toutes les offres Microsoft DLP, consultez la rubrique [vue d’ensemble de la protection contre la perte de données](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies?view=o365-worldwide).

Vous pouvez utiliser les stratégies DLP pour les applications Cloud non-Microsoft pour surveiller et détecter les éléments sensibles utilisés et partagés par les applications Cloud non Microsoft. L’utilisation de ces stratégies vous offre la visibilité et le contrôle dont vous avez besoin pour vous assurer qu’ils sont correctement utilisés et protégés, et cela permet d’éviter tout comportement risqué susceptible de les compromettre.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="skusubscriptions-licensing"></a>Licences SKU/abonnements

Avant de commencer à utiliser les stratégies DLP pour les applications Cloud non Microsoft, confirmez votre [abonnement microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) et tous les modules complémentaires. Pour accéder à cette fonctionnalité et l’utiliser, vous devez disposer de l’un des abonnements ou des modules complémentaires suivants :

- Microsoft 365 E5
- Microsoft 365 E5 Conformité
- Microsoft 365 E5 Sécurité

### <a name="prepare-your-cloud-app-security-environment"></a>Préparer votre environnement de sécurité d’application Cloud

Les stratégies DLP pour les applications Cloud non-Microsoft utilisent les fonctionnalités DLP de la sécurité des applications Cloud. Pour l’utiliser, vous devez préparer votre environnement de sécurité d’application Cloud. Pour obtenir des instructions, consultez [la rubrique Set isntant Visibility, protection, and Governance actions for Your Apps](https://docs.microsoft.com/cloud-app-security/getting-started-with-cloud-app-security#step-1-set-instant-visibility-protection-and-governance-actions-for-your-apps).

### <a name="connect-a-non-microsoft-cloud-app"></a>Connecter une application Cloud non-Microsoft

Pour utiliser la stratégie DLP pour une application Cloud non Microsoft spécifique, l’application doit être connectée à la sécurité de l’application Cloud. Pour plus d’informations, voir :

- [Zone de connexion](https://docs.microsoft.com/cloud-app-security/connect-box-to-microsoft-cloud-app-security)
- [Connecter Dropbox](https://docs.microsoft.com/cloud-app-security/connect-dropbox-to-microsoft-cloud-app-security)
- [Connecter G-suite](https://docs.microsoft.com/cloud-app-security/connect-google-apps-to-microsoft-cloud-app-security)
- [Connexion Salesforce](https://docs.microsoft.com/cloud-app-security/connect-salesforce-to-microsoft-cloud-app-security)
- [Connexion de Cisco Webex](https://docs.microsoft.com/cloud-app-security/connect-webex-to-microsoft-cloud-app-security)

Une fois que vous avez connecté vos applications Cloud à la sécurité des applications Cloud, vous pouvez créer des stratégies DLP Microsoft 365.

>[!NOTE]
>Il est également possible d’utiliser Microsoft Cloud App Security pour créer des stratégies DLP sur des applications Cloud Microsoft. Toutefois, il est recommandé d’utiliser Microsoft 365 pour créer et gérer des stratégies DLP sur des applications Cloud Microsoft.

## <a name="create-a-dlp-policy-to-a-non-microsoft-cloud-app"></a>Créer une stratégie DLP pour une application Cloud non Microsoft

Lorsque vous sélectionnez un emplacement pour la stratégie DLP, activez l’emplacement de sécurité de l' **application Cloud Microsoft** .

- Pour sélectionner une application ou une instance spécifique, sélectionnez **choisir une instance**.
- Si vous ne sélectionnez pas d’instance, la stratégie utilise toutes les applications connectées de votre client de sécurité Microsoft Cloud App.

   ![Emplacements auxquels appliquer la stratégie](../media/1-dlp-non-microsoft-cloud-app-choose-instance.png)

   ![Case-US et Box-General](../media/2-dlp-non-microsoft-cloud-app-box.png)

Vous pouvez choisir différentes actions pour toutes les applications Cloud non-Microsoft prises en charge. Pour chaque application, il existe différentes actions possibles (en fonction de l’API de l’application Cloud).

![Créer une règle](../media/3-dlp-non-microsoft-cloud-app-create-rule.png)

Lorsque vous créez une règle dans la stratégie DLP, vous pouvez sélectionner une action pour les applications Cloud non Microsoft. Pour restreindre les applications tierces, sélectionnez **restreindre les applications**tierces.

![Restreindre les applications tierces](../media/4-dlp-non-microsoft-cloud-app-restrict-third-party-apps.png)

Pour plus d’informations sur la création et la configuration des stratégies DLP, voir [Create test and tune a DLP Policy](https://docs.microsoft.com/microsoft-365/compliance/create-test-tune-dlp-policy?view=o365-worldwide).

## <a name="see-also"></a>Voir aussi

- [Créer un test et régler une stratégie DLP](https://docs.microsoft.com/microsoft-365/compliance/create-test-tune-dlp-policy?view=o365-worldwide)
- [Prise en main de la stratégie DLP par défaut](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-the-default-dlp-policy?view=o365-worldwide)
- [Création d’une stratégie DLP à partir d’un modèle](https://docs.microsoft.com/microsoft-365/compliance/create-a-dlp-policy-from-a-template?view=o365-worldwide)
