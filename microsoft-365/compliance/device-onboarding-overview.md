---
title: Vue d’ensemble de l’intégration des appareils Windows 10 ou Windows 11 dans Microsoft 365
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Intégrer des appareils Windows 10 et Windows 11 dans Microsoft 365
ms.openlocfilehash: ec95fcbfca3ab41bb3a249534e5ff62721aac794
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2022
ms.locfileid: "62272077"
---
# <a name="onboard-windows-10-and-windows-11-devices-into-microsoft-365-overview"></a>Vue d’ensemble de l’intégration des appareils Windows 10 et Windows 11 dans Microsoft 365

**S’applique à :**

- [Protection contre la perte de données de point de terminaison (DLP) pour Microsoft 365](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

Microsoft 365 la protection contre la perte de données de point de terminaison (DLP) et la gestion des risques internes nécessitent que les appareils Windows 10 Windows et Windows 11 soient intégrés au service afin qu’ils puissent envoyer des données de surveillance aux services.
 
Microsoft 365 point de terminaison DLP vous permet de surveiller les appareils Windows 10 ou Windows 11 et de détecter les situations d’utilisation et de partage des éléments sensibles. Ainsi, vous bénéficiez de la visibilité et du contrôle dont vous avez besoin pour vous assurer qu’ils sont utilisés et protégés correctement, et pour éviter tout comportement risqué susceptible de les compromettre. Si vous souhaitez en savoir plus sur les offres DLP de Microsoft, veuillez consulter la rubrique [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md). Pour en savoir plus sur le point de terminaison DLP, voir [En savoir plus sur la protection contre la perte de données de point de terminaison.](endpoint-dlp-learn-about.md)

La gestion des risques internes utilise l’ensemble des indicateurs de service et tiers pour vous aider à identifier, trier et agir rapidement sur l’activité des utilisateurs à risque. À l’aide des journaux de Microsoft 365 et de Microsoft Graph, la gestion des risques internes vous permet de définir des stratégies spécifiques pour identifier les indicateurs de risque et prendre des mesures pour atténuer ces risques. Pour plus d’informations, voir [En savoir plus sur la gestion des risques internes dans Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365).

L’intégration d’appareil est partagée entre Microsoft 365 et Microsoft Defender pour le point de terminaison (MDE). Si vous avez déjà intégré des appareils à MDE, ils apparaissent dans la liste des appareils gérés et aucune autre étape n’est nécessaire pour intégrer ces appareils spécifiques. L’intégration d’appareils dans le Centre de conformité les intègre également dans MDE.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="skusubscriptions-licensing"></a>Licences SKU/abonnements

Vérifiez les conditions de licence [ici.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business)

### <a name="permissions"></a>Autorisations

Pour activer la gestion des appareils, le compte que vous utilisez doit être membre de l’un de ces rôles :

- Administrateur global
- Administrateur de la sécurité
- Administrateur de mise en conformité

Si vous voulez utiliser un compte personnalisé pour afficher les paramètres de gestion des appareils, celui-ci doit se trouver dans l’un de ces rôles :

- Administrateur global
- Administrateur de mise en conformité
- Administrateur des données de mise en conformité
- Lecteur général

Si vous voulez utiliser un compte personnalisé pour accéder à la page d’intégration/déclassement, celui-ci doit se trouver dans l’un de ces rôles :

- Administrateur global
- Administrateur de mise en conformité

Si vous voulez utiliser un compte personnalisé pour activer/désactiver la surveillance de l’appareil, celui-ci doit se trouver dans l’un de ces rôles :

- Administrateur global
- Administrateur de mise en conformité

### <a name="prepare-your-windows-devices"></a>Préparer vos appareils Windows

Assurez-vous que les appareils Windows que vous devez intégrer répondent à ces exigences.

1. Doit être en cours d’exécution de Windows 10 x64 build 1809 ou ultérieure ou une Windows 11.

2. La version du client logiciel anti-programme malveillant est 4.18.2110 ou ultérieure. Vérifiez votre version actuelle à l’aide de l’application Sécurité Windows, sélectionnez l’icône Paramètres, puis À propos de. Le numéro de version est répertorié sous version du client anti-programme malveillant. Effectuez une mise à jour vers la dernière version du client anti-programme malveillant en installant Windows Update KB4052623.

   > [!NOTE]
   > Aucune des composants de sécurité Windows ne doit être actif, mais la [protection en temps réel et le moniteur de comportement](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus)) doivent être activés.

3. Les mises à jour Windows suivantes pour Windows 10 sont installées pour les appareils qui seront surveillés.

   > [!NOTE]
   > Ces mises à jour ne sont pas une condition préalable à l’intégration d’un appareil, mais contiennent des correctifs pour les problèmes importants et doivent donc être installées avant d’utiliser le produit.
   >
    > - Pour Windows 10 version 1809 : KB4559003, KB4577069, KB4580390
    > - Pour Windows 10 version 1903 ou 1909 : KB4559004, KB4577062, KB4580386
    > - Pour Windows 10 version 2004 : KB4568831, KB4577063

4. Tous les appareils doivent être l’un de ceux-ci :

   - [Jointure Azure Active Directory (Azure AD)](/azure/active-directory/devices/concept-azure-ad-join)
   - [Jonction Azure AD Hybride](/azure/active-directory/devices/concept-azure-ad-join-hybrid)
   - [Inscrit à AAD](/azure/active-directory/user-help/user-help-register-device-on-network)

5. Une version prise en charge de Microsoft Office est installée et à jour. Pour bénéficier d’une protection et d’une expérience utilisateur robuste, vérifiez que Microsoft 365 Apps version 16.0.14701.0 ou ultérieure est installée.
> [!NOTE]
   >Si vous exécutez Office 265 : KB 4577063 est requis Si vous utilisez le canal d’entreprise mensuel de Microsoft 365 Apps versions 2004-2008, vous devez mettre à jour vers la version 2009 ou ultérieure. Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Historique des mises à jour de Microsoft 365 Apps (répertoriées par date)](/officeupdates/update-history-microsoft365-apps-by-date). Si vous souhaitez en savoir plus sur ce problème, veuillez consultez la section Suite Office, dans les [Notes de publication pour les publications du Canal actuel dans 2020](/officeupdates/current-channel#version-2010-october-27).

6. Si vous avez des points de terminaison qui utilisent un proxy de périphérique pour se connecter à l'internet, suivez les procédures de la section [Configurer le proxy de périphérique et les paramètres de connexion à l'internet pour la protection de l’information](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection).

## <a name="onboarding-windows-10-or-windows-11-devices"></a>Intégration d’appareils Windows 10 ou Windows 11

Vous devez activer la surveillance des appareils et intégrer vos points de terminaison avant de pouvoir surveiller et protéger les éléments sensibles sur un appareil. Ces deux actions sont effectuées dans le portail de conformité Microsoft 365.

Lorsque vous voulez intégrer des appareils qui n’ont pas encore été intégrés, vous devez télécharger et déployer les scripts appropriés sur ces appareils. Suivez les procédures d’intégration d’appareil ci-dessous.

Si vous disposez déjà d’appareils incorporés dans [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/), ceux-ci apparaissent déjà dans la liste des périphériques gérés.

Dans ce scénario de déploiement, vous allez intégrer des appareils Windows 10 ou Windows 11 qui n’ont pas encore été intégrés.

1. Ouvrez le [Centre de conformité Microsoft](https://compliance.microsoft.com). Choisissez **Paramètres**  >  **activer la surveillance des appareils.**

   > [!NOTE]
   > Bien que l’activation de l’intégration des appareils dure généralement environ 60 secondes, patientez jusqu’à 30 minutes avant de contacter le support Microsoft.

2. Ouvrez la page Paramètres du centre de conformité et sélectionnez **Appareils intégrés**.

   > [!div class="mx-imgBorder"]
   > ![activer la gestion des appareils.](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

3. Sélectionnez **Gestion des appareils** pour ouvrir la liste des **Appareils**. 

> [!NOTE]
> Si vous avez précédemment déployé Microsoft Defender pour le point de terminaison, tous les appareils qui ont été intégrés au cours de ce processus sont répertoriés dans la liste **Appareils.** Il n’est pas nécessaire de les intégrer à nouveau.

4. Sélectionnez **Intégration** pour lancer le processus d’intégration.

5. Choisissez la manière dont vous voulez déployer ces autres appareils à partir de la liste **Méthode de déploiement**, puis **Télécharger le package**.

6. Choisissez la procédure appropriée à suivre dans le tableau ci-dessous :

Rubrique | Description
:---|:---
[Intégrer les appareils Windows 10 ou 11 à l’aide de la stratégie de groupe](device-onboarding-gp.md) | Utilisez la stratégie de groupe pour déployer le package de configuration sur les appareils.
[Intégrer des appareils Windows 10 ou 11 à l’aide de Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md) | Vous pouvez utiliser Microsoft Endpoint Configuration Manager (current branch) version 1606 ou Microsoft Endpoint Configuration Manager (current branch) version 1602 ou antérieure pour déployer le package de configuration sur les appareils.
[Intégrer Windows 10 ou 11 appareils à l’aide des outils de gestion des appareils mobiles](device-onboarding-mdm.md) | Utilisez les outils de Gestion des appareils mobiles ou Microsoft Intune pour déployer le package de configuration sur l’appareil.
[intégrer des appareils Windows 10 ou 11 à l’aide d’un script local](device-onboarding-script.md) | Découvrez comment utiliser le script local pour déployer le package de configuration sur des points de terminaison.
[Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](device-onboarding-vdi.md) | Découvrez comment utiliser le package de configuration pour configurer des appareils VDI.

Une fois qu’un appareil est intégré, il doit être visible dans la liste des appareils et commencer à signaler l’activité du journal d’audit à l’Explorateur d’activités.

### <a name="viewing-endpoint-dlp-alerts-in-dlp-alerts-management-dashboard"></a>Affichage des alertes DLP de point de terminaison dans le tableau de bord de Gestion des alertes DLP

1. Ouvrez la page Protection contre la perte de données dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centre de conformité Microsoft 365</a> sélectionnez Alertes.

2. Reportez-vous aux procédures décrites dans [Comment configurer et afficher les alertes pour les stratégies DLP](dlp-configure-view-alerts-policies.md) pour afficher les alertes relatives à vos stratégies DLP de point de terminaison.

### <a name="viewing-endpoint-dlp-data-in-activity-explorer"></a>Affichage de données DLP de point de terminaison dans l’Explorateur d’activités

1. Ouvrez la [Page classification des données](https://compliance.microsoft.com/dataclassification?viewid=overview) pour votre domaine dans le centre de conformité Microsoft 365, puis sélectionnez Explorateur d’activités.

2. Reportez-vous aux procédures décrites dans [Prise en main de l’Explorateur d’activités](data-classification-activity-explorer.md) pour accéder aux données de vos appareils de point de terminaison et les filtrer.

   > [!div class="mx-imgBorder"]
   > ![filtre de l’Explorateur d’activités pour les appareils de point de terminaison.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)


## <a name="see-also"></a>Voir aussi

- [Découvrez les stratégies de gestion des risques internes dans Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
- [Découvrir la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md)
- [Utilisation de la prévention des pertes de données sur les points de terminaison](endpoint-dlp-using.md)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)
- [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/)
- [Outils et méthodes d’intégration pour les appareils Windows 10](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).
- [Abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure AD appareils joints](/azure/active-directory/devices/concept-azure-ad-join)
- [Télécharger le nouveau Microsoft Edge sur la base de chrome](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
