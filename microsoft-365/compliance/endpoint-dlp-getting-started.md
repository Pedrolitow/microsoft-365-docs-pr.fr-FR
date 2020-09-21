---
title: Prise en main des points de terminaison de protection contre la perte de données Microsoft 365 (Preview)
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/21/2020
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Configurez les points de terminaison contre la protection contre la perte de données Microsoft 365 pour surveiller les activités des fichiers et implémenter des actions de protection pour ces fichiers aux points de terminaison.
ms.openlocfilehash: 43ab2a30570f153f16819ede2eeed1f0e091da74
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47949844"
---
# <a name="get-started-with-endpoint-data-loss-prevention-preview"></a>Prise en main des points de terminaison de protection contre la perte de données (aperçu)

Microsoft Points de terminaison Protection contre la perte de données (Endpoint DLP) fait partie de la suite de fonctionnalités Microsoft 365 de protection contre la perte de données (DLP) que vous pouvez utiliser pour découvrir et protéger les éléments sensibles dans les services Microsoft 365. Pour plus d’informations sur les offres DLP de Microsoft, voir [Vue d’ensemble de la protection contre la perte de données](data-loss-prevention-policies.md). Pour en savoir plus sur Endpoint DLP, voir [En savoir plus sur Points de terminaison Protection contre la perte de données (Preview)](endpoint-dlp-learn-about.md)

Microsoft Endpoint DLP vous permet de surveiller les appareils Windows 10 et de détecter les situations d’utilisation et de partage des éléments sensibles. Ainsi, vous bénéficiez de la visibilité et du contrôle dont vous avez besoin pour vous assurer qu’ils sont utilisés et protégés correctement, et pour éviter tout comportement risqué susceptible de les compromettre.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="skusubscriptions-licensing"></a>Licences SKU/abonnements

Avant de commencer à utiliser point de terminaison DLP, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) et tous les modules complémentaires. Pour accéder à la fonctionnalité de points de terminaison DLP et l’utiliser, vous devez disposer de l’un de ces abonnements ou modules complémentaires.

- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 Conformité
- Microsoft 365 A5 Conformité
- Microsoft 365 E5, Protection des informations et gouvernance
- Microsoft 365 A5, Protection des informations et gouvernance

### <a name="permissions"></a>Autorisations

Pour activer la gestion des appareils, le compte que vous utilisez doit être membre de l’un de ces rôles :

- Administrateur global
- Administrateur de la sécurité
- Administrateur de mise en conformité

Si vous voulez utiliser un compte personnalisé pour afficher les paramètres de gestion des appareils, celui-ci doit se trouver dans l’un de ces rôles :

- Administrateur global
- Administrateur de mise en conformité
- Administrateur des données de mise en conformité
- Lecteur général

Si vous voulez utiliser un compte personnalisé pour accéder à la page d’intégration/déclassement, celui-ci doit se trouver dans l’un de ces rôles :

- Administrateur global
- Administrateur de mise en conformité

Si vous voulez utiliser un compte personnalisé pour activer/désactiver la surveillance de l’appareil, celui-ci doit se trouver dans l’un de ces rôles :

- Administrateur global
- Administrateur de mise en conformité

Les données du point de terminaison DLP peuvent être affichées dans [l’Explorateur d’activités](data-classification-activity-explorer.md). Il existe quatre rôles qui accordent l’autorisation à l’Explorateur d’activités, le compte que vous utilisez pour accéder aux données doit être membre de l’un d’eux.

- Administrateur global
- Administrateur de mise en conformité
- Administrateur de la sécurité
- Administrateur des données de mise en conformité

### <a name="prepare-your-endpoints"></a>Préparer vos points de terminaison

Assurez-vous que les appareils Windows 10 pour lesquels vous envisagez de déployer le point de terminaison DLP répondent à ces exigences.

1. Vous devez exécuter Windows 10 Build 1809 ou version ultérieure.
2. Tous les appareils doivent être [joints à Azure Active Directory (AAD)](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-ad-join) ou joints à Azure AD Hybride.
3. Installez le navigateur Microsoft Chromium Edge sur l’appareil de point de terminaison afin d’appliquer des actions de stratégie pour l’activité de téléchargement vers le Cloud. [Télécharger le nouveau Microsoft Edge sur la base de chrome](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium).

## <a name="onboarding-devices-into-device-management"></a>Dispositifs d’intégration dans la gestion des appareils

 Vous devez activer la surveillance des appareils et intégrer vos points de terminaison avant de pouvoir surveiller et protéger les éléments sensibles sur un appareil. Ces deux actions sont effectuées dans le portail de conformité Microsoft 365.

Lorsque vous voulez intégrer des appareils qui n’ont pas encore été intégrés, vous devez télécharger et déployer les scripts appropriés sur ces appareils. Suivez la procédure [d’intégration d’appareils](endpoint-dlp-getting-started.md#onboarding-devices).

Si vous disposez déjà d’appareils incorporés dans [Microsoft Defender Advanced Threat Protection (MDATP](https://docs.microsoft.com/windows/security/threat-protection/)), ceux-ci apparaissent déjà dans la liste des périphériques gérés. Suivez [Avec les appareils intégrés à la procédure MDATP](endpoint-dlp-getting-started.md#with-devices-onboarded-into-mdatp).

### <a name="onboarding-devices"></a>Intégration des appareils

Dans ce scénario de déploiement, vous allez intégrer des appareils qui n’ont pas encore été intégrés, et vous voulez simplement contrôler et protéger les éléments sensibles contre le partage involontaire sur les appareils Windows 10.

1. Ouvrez le [Centre de conformité Microsoft](https://compliance.microsoft.com).
2. Ouvrez la page Paramètres du centre de conformité et sélectionnez **Appareils intégrés**. 

   ![activer la gestion des appareils](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

   > [!NOTE]
   > Bien que l’activation de l’intégration des appareils dure généralement environ 60 secondes, patientez jusqu’à 30 minutes avant de contacter le support Microsoft.

3. Sélectionnez **Gestion des appareils** pour ouvrir la liste des **Appareils**. La liste est vide tant que vous n’avez pas intégré de périphériques.
4. Sélectionnez **Intégration** pour lancer le processus d’intégration.
5. Choisissez la manière dont vous voulez déployer ces autres appareils à partir de la liste**Méthode de déploiement**, puis **Télécharger le package**.

   ![Méthode de déploiement](../media/endpoint-dlp-getting-started-3-deployment-method.png)
6. Suivez les procédures appropriées dans [Outils et méthodes d’intégration pour les ordinateurs Windows 10](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Ce lien vous permet d’accéder à une page d’accueil dans laquelle vous pouvez accéder aux procédures MDATP qui correspondent au package de déploiement que vous avez sélectionné à l’étape 5 :
    - Intégrer les ordinateurs Windows 10 utilisant une stratégie de groupe
    - Intégrer les ordinateurs Windows à l’aide du gestionnaire de configuration de point de terminaison Microsoft
    - Intégrer les ordinateurs Windows 10 à l’aide des outils de gestion des appareils mobiles
    - Intégrer les ordinateurs Windows 10 utilisant un script local
    - Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.

Une fois l’opération effectuée et le point de terminaison intégré, celui-ci doit être visible dans la liste des appareils et commencer à créer des rapports d’activité d’audit dans l’Explorateur d’activités.

> [!NOTE]
> Cette expérience est sous l’application de la licence. Sans la licence requise, les données ne sont pas visibles ni accessibles.

### <a name="with-devices-onboarded-into-mdatp"></a>Avec les appareils intégrés à MDATP

Dans ce scénario, MDATP est déjà déployé et des points de terminaison y sont reportés. Tous ces points de terminaison s’affichent dans la liste des appareils gérés. Vous pouvez continuer à intégrer de nouveaux appareils dans le point de terminaison DLP pour étendre la couverture à l’aide de la [procédure d’intégration d’appareils](endpoint-dlp-getting-started.md#onboarding-devices).

1. Ouvrez le [Centre de conformité Microsoft](https://compliance.microsoft.com).
2. Ouvrez la page Paramètres du centre de conformité et sélectionnez **Activer la surveillance d’appareils**.
3. Sélectionnez **Gestion des appareils** pour ouvrir la liste des **Appareils**. Vous devriez voir la liste des appareils qui signalent déjà les MDATP. ![Gestion des appareils](../media/endpoint-dlp-getting-started-2-device-management.png)
4. Sélectionnez **Intégration** si vous avez besoin d’intégrer d’autres appareils.
5. Choisissez la manière dont vous voulez déployer ces autres appareils à partir de la liste**Méthode de déploiement**, puis **Télécharger le package**.
6. Suivez les procédures appropriées dans [Outils et méthodes d’intégration pour les ordinateurs Windows 10](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Ce lien vous permet d’accéder à une page d’accueil dans laquelle vous pouvez accéder aux procédures MDATP qui correspondent au package de déploiement que vous avez sélectionné à l’étape 5 :
    - Intégrer les ordinateurs Windows 10 utilisant une stratégie de groupe
    - Intégrer les ordinateurs Windows à l’aide du gestionnaire de configuration de point de terminaison Microsoft
    - Intégrer les ordinateurs Windows 10 à l’aide des outils de gestion des appareils mobiles
    - Intégrer les ordinateurs Windows 10 utilisant un script local
    - Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.

Une fois l’opération effectuée et le point de terminaison intégré, celui-ci doit être visible dans le tableau des **Appareils** et commencer à créer des rapports d’activité d’audit dans l’**Explorateur d’activités**.

> [!NOTE]
>Cette expérience est sous l’application de la licence. Sans la licence requise, les données ne sont pas visibles ni accessibles.

### <a name="viewing-endpoint-dlp-data-in-activity-explorer"></a>Affichage de données DLP de point de terminaison dans l’Explorateur d’activités

1. Ouvrez la [Page classification des données](https://compliance.microsoft.com/dataclassification?viewid=overview) pour votre domaine dans le centre de conformité Microsoft 365, puis sélectionnez Explorateur d’activités.
2. Reportez-vous aux procédures décrites dans [Prise en main de l’Explorateur d’activités](data-classification-activity-explorer.md) pour accéder aux données de vos appareils de point de terminaison et les filtrer.

![filtre de l’Explorateur d’activités pour les appareils de point de terminaison](../media/endpoint-dlp-4-getting-started-activity-explorer.png)

## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous disposez d’appareils intégrés et que vous pouvez afficher les données d’activité dans l’Explorateur d’activités, vous êtes prêt à passer à l’étape suivante dans laquelle vous créez des stratégies DLP qui protègent vos éléments sensibles.

- [Utilisation des points de terminaison de protection contre la perte de données (aperçu)](endpoint-dlp-using.md)

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les points de terminaison de protection contre la perte de données (Preview)](endpoint-dlp-learn-about.md)
- [Utilisation des points de terminaison de protection contre la perte de données (aperçu)](endpoint-dlp-using.md)
- [Vue d’ensemble de la protection contre la perte de données](data-loss-prevention-policies.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)
- [Microsoft Defender – Protection avancée contre les menaces (Microsoft Defender ATP)](https://docs.microsoft.com/windows/security/threat-protection/)
- [Outils et méthodes d’intégration pour les appareils Windows 10](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).
- [Abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (ADD) adhésion](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-ad-join)
- [Télécharger le nouveau Microsoft Edge sur la base de chrome](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
