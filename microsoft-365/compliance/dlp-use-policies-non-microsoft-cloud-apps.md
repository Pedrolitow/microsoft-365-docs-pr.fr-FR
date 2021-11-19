---
title: Utiliser des stratégies de protection contre la perte de données pour les applications cloud non Microsoft
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
description: Découvrez comment utiliser des stratégies dlp pour les applications cloud non Microsoft.
ms.openlocfilehash: b374f9b85d41b6dd6a5281e17347dffd414361da
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61109778"
---
# <a name="use-data-loss-prevention-policies-for-non-microsoft-cloud-apps"></a>Utiliser des stratégies de protection contre la perte de données pour les applications cloud non Microsoft

Les stratégies de protection contre la perte de données (DLP) pour les applications cloud non Microsoft font partie de la suite de fonctionnalités DLP Microsoft 365 ; à l’aide de ces fonctionnalités, vous pouvez découvrir et protéger les éléments sensibles dans les services Microsoft 365. Pour plus d’informations sur toutes les offres Microsoft DLP, voir [En savoir plus sur la protection contre la perte de données.](dlp-learn-about-dlp.md)

Vous pouvez utiliser des stratégies DLP pour les applications cloud non-Microsoft afin de surveiller et de détecter quand des éléments sensibles sont utilisés et partagés via des applications cloud non Microsoft. L’utilisation de ces stratégies vous donne la visibilité et le contrôle dont vous avez besoin pour vous assurer qu’elles sont correctement utilisées et protégées, et cela permet d’éviter les comportements risqués qui peuvent les compromettre.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="skusubscriptions-licensing"></a>Licences SKU/abonnements

Avant de commencer à utiliser des stratégies DLP pour les applications cloud non Microsoft, confirmez votre abonnement [Microsoft 365 et](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) les modules. Pour accéder à cette fonctionnalité et l’utiliser, vous devez avoir l’un de ces abonnements ou modules:

- Microsoft 365 E5
- Microsoft 365 E5 Conformité
- Microsoft 365 E5 Sécurité

### <a name="permissions"></a>Autorisations
L’utilisateur qui crée la stratégie DLP doit être :

- Administrateur général
- Administrateur de conformité : affecter dans Azure AD
- Administrateur de données de conformité : affecter dans Azure AD

### <a name="prepare-your-defender-for-cloud-apps-environment"></a>Préparer votre environnement Defender pour les applications cloud

Les stratégies DLP pour les applications cloud non Microsoft utilisent les fonctionnalités DLP de Defender for Cloud Apps. Pour l’utiliser, vous devez préparer votre environnement Defender pour Les applications cloud. Pour obtenir des instructions, voir Définir des actions de visibilité, de protection et de gouvernance [instantanées pour vos applications.](/cloud-app-security/getting-started-with-cloud-app-security#step-1-set-instant-visibility-protection-and-governance-actions-for-your-apps)

### <a name="connect-a-non-microsoft-cloud-app"></a>Connecter application cloud non Microsoft

Pour utiliser la stratégie DLP sur une application cloud non-Microsoft spécifique, l’application doit être connectée à Defender pour les applications cloud. Pour plus d’informations, voir :

- [Connecter Box](/cloud-app-security/connect-box-to-microsoft-cloud-app-security)
- [Connecter Dropbox](/cloud-app-security/connect-dropbox-to-microsoft-cloud-app-security)
- [Connecter G-Workspace](/cloud-app-security/connect-google-apps-to-microsoft-cloud-app-security)
- [Connecter Salesforce](/cloud-app-security/connect-salesforce-to-microsoft-cloud-app-security)
- [Connecter Cisco Webex](/cloud-app-security/connect-webex-to-microsoft-cloud-app-security)

Une fois que vous avez connecté vos applications cloud à Defender pour les applications cloud, vous pouvez créer Microsoft 365 stratégies DLP pour elles.

> [!NOTE]
> Il est également possible d’utiliser Microsoft Defender pour les applications cloud pour créer des stratégies DLP pour les applications cloud Microsoft. Toutefois, il est recommandé d’utiliser Microsoft 365 pour créer et gérer des stratégies DLP dans les applications cloud De Microsoft.

## <a name="create-a-dlp-policy-to-a-non-microsoft-cloud-app"></a>Créer une stratégie DLP pour une application cloud non-Microsoft

Lorsque vous sélectionnez un emplacement pour la stratégie DLP, sélectionnez **l’emplacement Microsoft Defender pour les applications cloud.**

- Pour sélectionner une application ou une instance spécifique, **sélectionnez Instance.**
- Si vous ne sélectionnez pas d’instance, la stratégie utilise toutes les applications connectées dans votre client Microsoft Defender pour les applications cloud.

   ![Emplacements à appliquer à la stratégie.](../media/1-dlp-non-microsoft-cloud-app-choose-instance.png)

   ![Box-US et Box-General.](../media/2-dlp-non-microsoft-cloud-app-box.png)

Vous pouvez choisir différentes actions pour chaque application cloud non-Microsoft prise en charge. Pour chaque application, il existe différentes actions possibles (dépend de l’API de l’application cloud).

![Créer une règle.](../media/3-dlp-non-microsoft-cloud-app-create-rule.png)

Lorsque vous créez une règle dans la stratégie DLP, vous pouvez sélectionner une action pour les applications cloud autres que Microsoft. Pour restreindre les applications tierces, **sélectionnez Restreindre les applications tierces.**

![Limiter les applications tierces.](../media/4-dlp-non-microsoft-cloud-app-restrict-third-party-apps.png)

> [!NOTE]
> Les stratégies DLP appliquées aux applications autres que Microsoft utilisent Microsoft Defender pour les applications cloud. Lorsque la stratégie DLP pour une application non-Microsoft est créée, la même stratégie est automatiquement créée dans Microsoft Defender pour les applications cloud.

Pour plus d’informations sur la création et la configuration des stratégies DLP, voir Créer un test et [régler une stratégie DLP.](./create-test-tune-dlp-policy.md)

## <a name="see-also"></a>Voir aussi

- [Créer un test et régler une stratégie DLP](./create-test-tune-dlp-policy.md)
- [Prise en main de la stratégie DLP par défaut](./get-started-with-the-default-dlp-policy.md)
- [Création d’une stratégie DLP à partir d’un modèle](./create-a-dlp-policy-from-a-template.md)
