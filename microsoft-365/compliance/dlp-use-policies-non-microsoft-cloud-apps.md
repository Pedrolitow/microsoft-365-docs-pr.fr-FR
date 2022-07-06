---
title: Utiliser des stratégies DLP pour les applications cloud non Microsoft
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
description: Découvrez comment utiliser des stratégies dlp pour les applications cloud autres que Microsoft.
ms.openlocfilehash: a50849b53819a7c5872c3ec8cb279ffa8d14e27f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634394"
---
# <a name="use-data-loss-prevention-policies-for-non-microsoft-cloud-apps"></a>Utiliser des stratégies de protection contre la perte de données pour les applications cloud non Microsoft

Vous pouvez étendre les stratégies DLP à Microsoft Defender for Cloud Apps pour surveiller, détecter et prendre des mesures lorsque des éléments sensibles sont utilisés et partagés via des applications cloud non-Microsoft.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="skusubscriptions-licensing"></a>Licences SKU/abonnements

Avant de commencer à utiliser des stratégies DLP, confirmez votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) et tous les modules complémentaires. Pour accéder à cette fonctionnalité et l’utiliser, vous devez disposer de l’un de ces abonnements ou modules complémentaires :

- Microsoft 365 E5
- Microsoft 365 E5 Conformité
- Microsoft 365 E5 Sécurité

### <a name="permissions"></a>Autorisations
L’utilisateur qui crée la stratégie DLP doit être un :

- Administrateur général
- Administrateur de conformité : assigner dans Azure AD
- Administrateur de données de conformité : assigner dans Azure AD

### <a name="prepare-your-defender-for-cloud-apps-environment"></a>Préparer votre environnement Defender pour Cloud Apps

Avant de configurer des stratégies DLP étendues à Microsoft Defender for Cloud Apps, vous devez préparer votre environnement Defender pour Cloud Apps. Pour obtenir des instructions, consultez [démarrage rapide : Bien démarrer avec Microsoft Defender for Cloud Apps](/defender-cloud-apps/get-started).

### <a name="connect-a-non-microsoft-cloud-app"></a>Connecter une application cloud non-Microsoft

Pour utiliser une stratégie DLP étendue à une application cloud non Microsoft spécifique, l’application doit être connectée à Defender pour Cloud Apps. Pour plus d’informations, voir :

- [Connect Box](/defender-cloud-apps/connect-box)
- [Connecter Dropbox](/defender-cloud-apps/connect-dropbox)
- [Connecter Google Workspace](/defender-cloud-apps/connect-google-workspace)
- [Connecter Salesforce](/defender-cloud-apps/connect-salesforce)
- [Connecter Cisco Webex](/defender-cloud-apps/connect-webex)

Une fois que vous avez connecté vos applications cloud à Defender pour Cloud Apps, vous pouvez créer des stratégies DLP pour elles.

## <a name="create-a-dlp-policy-scoped-to-a-non-microsoft-cloud-app"></a>Créer une stratégie DLP étendue à une application cloud non Microsoft

Reportez-vous à [Créer, tester et paramétrer une stratégie DLP](create-test-tune-dlp-policy.md) pour les procédures permettant de créer une stratégie DLP. Gardez ces points à l’esprit lorsque vous configurez votre stratégie.

- Sélectionnez l’activation de l’emplacement **Microsoft Defender for Cloud Apps**.
- Pour sélectionner une application ou une instance spécifique, **sélectionnez Choisir une instance**. Si vous ne sélectionnez pas d’instance, la stratégie sera étendue à toutes les applications connectées dans votre locataire Microsoft Defender for Cloud Apps.
- Vous pouvez sélectionner un certain nombre **d’actions** à appliquer sur des applications tierces. Pour restreindre les applications tierces, sélectionnez **Restreindre les applications tierces** , puis sélectionnez les actions spécifiques.

![liste des actions à appliquer sur les applications cloud connectées](../media/dlp-non-microsoft-cloud-app-restrict-third-party-apps.png)

> [!NOTE]
> Lorsque vous créez une stratégie DLP limitée à Microsoft Defender for Cloud Apps, la même stratégie est automatiquement créée dans Microsoft Defender for Cloud Apps.

## <a name="see-also"></a>Voir aussi

- [Créer un test et paramétrer une stratégie DLP](./create-test-tune-dlp-policy.md)
- [Prise en main de la stratégie DLP par défaut](./get-started-with-the-default-dlp-policy.md)
- [Création d’une stratégie DLP à partir d’un modèle](./create-a-dlp-policy-from-a-template.md)
