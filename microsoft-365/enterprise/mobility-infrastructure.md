---
title: 'Phase 5 : gestion des appareils mobiles'
description: Microsoft 365 entreprise inclut la gestion des appareils mobiles à l’aide de Microsoft Intune. Passez en revue les exigences et les conditions préalables, configurer Intune à l’aide de vos ressources Azure Active Directory, inscrivez iOS, Mac OS, Android et Windows appareils, déployer des applications, créer un profil de configuration, utilisez une stratégie de conformité et activer l’accès mobile conditionnelle gestion des périphériques avec Microsoft 365 pour entreprises.
keywords: Documentation Microsoft 365, Microsoft 365 pour entreprises, Microsoft 365, gestion des appareils mobiles, Intune
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/18/2018
ms.topic: conceptual
audience: ITPro
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.assetid: fb4182e6-5e78-45d0-9641-d791c4519441
ms.custom: microsoft-intune
ms.openlocfilehash: 8d048ec6628cb8f7cb9c5e0d4c7960481bc69de1
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867496"
---
# <a name="phase-5-mobile-device-management-for-microsoft-365-enterprise"></a>Phase 5 : Gestion des appareils mobiles Microsoft 365 entreprise

![](./media/deploy-foundation-infrastructure/mobiledevicemgmt_icon.png)

*Cette fonctionnalité ne s’applique aux versions de Microsoft 365 entreprise E3 et E5*

Microsoft 365 entreprise inclut des fonctionnalités permettant de gérer les périphériques et leurs applications, au sein de votre organisation. À l’aide de Microsoft Intune, vous pouvez gérer iOS, Android, Mac OS et appareils Windows pour protéger l’accès aux ressources de votre organisation, y compris vos données. Intune s’intègre avec Azure Active Directory (AD Azure) et permet les scénarios d’entreprise pour Microsoft 365 :

- Stocker et partager des fichiers internes ou externes à votre entreprise pour travailler en toute transparence au-delà des frontières structurelles
- Travailler en toute sécurité avec votre appareil en tout lieu et à tout moment pour atteindre plus d’objectifs, en conservant une méthode de travail flexible
- Assurer la tranquillité d’esprit grâce à des contrôles et une visibilité sur votre conformité, vérifiée par le secteur, avec les normes internationales
- Protéger vos informations et réduire le risque de perte de données
- Détecter et assurez la protection contre les menaces externes
- Surveiller, signaler et analyser l’activité pour réagir rapidement pour fournir la sécurité de l’organisation
- Protéger les utilisateurs et leurs comptes

Pour plus d’informations, reportez-vous à la page relative à la [transformation numérique avec Microsoft 365](http://transform.microsoft.com). 

Durant cette phase, vous inscrivez vos périphériques dans Intune, créez et appliquer des stratégies pour vous aider à maintenir vos données sécurisées et protégées. Est l’intégralité de la bibliothèque de documentation Intune [disponibles en ligne](https://docs.microsoft.com/intune). Il est également conseillé de consulter la [planification du déploiement Intune, guide de conception et d’implémentation](https://docs.microsoft.com/intune/planning-guide) avant de commencer.

## <a name="step-1-plan-for-your-scenario"></a>Étape 1 : Planifier votre scénario

Une des principales raisons pour gérer les appareils mobiles consiste à sécuriser et protéger les ressources de votre organisation. [Manières courantes d’utiliser Microsoft Intune](https://docs.microsoft.com/intune/common-scenarios) répertorie quelques exemples concrètes, y compris la protection des données et messagerie Office 365.

Intune vous donne la possibilité de gérer l’accès à votre organisation à l’aide de la [gestion de périphérique Mobile (MDM) ou Mobile Application Management (MAM)](https://docs.microsoft.com/intune/byod-technology-decisions). Mobile Device Manager est lorsque leurs appareils dans Intune utilisateurs « s’inscrire ». Une fois inscrit, ils sont des périphériques gérés et peuvent recevoir des stratégies, les règles et les paramètres utilisés par votre organisation. Par exemple, vous pouvez installer des applications de détail, créer une stratégie de mot de passe, installer une connexion VPN et bien plus encore.

Les utilisateurs de leurs propres périphériques personnels souhaitent pas inscrire leurs périphériques, ou être géré par Intune et vos stratégies. Mais, vous devez protéger les ressources et les données de votre organisation. Dans ce scénario, vous pouvez protéger vos applications à l’aide de MAM. Par exemple, vous pouvez utiliser une stratégie MAM qui oblige l’utilisateur à entrer un code confidentiel pour accéder à SharePoint sur l’appareil.

Vous devez également déterminer comment vous allez gérer les périphériques personnels ou appartenant à l’organisation. Vous souhaiterez peut-être traiter les périphériques différemment, en fonction de leur utilisation. Par exemple, vous souhaiterez différents plans pour les utilisateurs dans les ressources humaines (RH) ou les utilisateurs du service commercial. [Scénarios de cas d’utilisation de gestion identifier appareil mobile](https://docs.microsoft.com/intune/planning-guide-scenarios) peut vous aider à démarrer et inclut des conseils sur les différents scénarios.

## <a name="step-2-get-your-prerequisites"></a>Étape 2 : Obtenir la configuration requise

Ensuite, obtenez la configuration requise en fonction de vos besoins et vos scénarios créés à l’étape précédente. [Mettre en œuvre votre plan](https://docs.microsoft.com/intune/planning-guide-onboarding) répertorie la configuration requise. Voici les éléments significatives, que vous avez besoin pour Intune avec 365 Microsoft :

- **Abonnement Intune**: inclus avec Microsoft 365 et vous donne accès à Microsoft Intune dans le [portail Azure](https://portal.azure.com)
- **Abonnement à Office 365**: inclus avec Microsoft 365 et est utilisé pour les applications Office, y compris le courrier électronique
- **Premium Azure Active Directory (AD)**: inclus avec Microsoft 365 et est utilisée pour créer des groupes de sécurité ou utilisateur. Ces groupes reçoivent Intune stratégies que vous créez, par exemple forcer une longueur de mot de passe pour déverrouiller un périphérique. Les groupes que vous créez dans [Phase 2 : identité](https://docs.microsoft.com/microsoft-365/enterprise/identity-infrastructure) peut être utilisé.

Il peut exister des exigences supplémentaires, en fonction des besoins de votre organisation. Par exemple, si vous allez gérer les appareils iOS, vous devez un certificat Apple Mobile Device Manager Push. Si vous utilisez Exchange sur site, vous devrez alors le connecteur Exchange sur site. Ces exigences supplémentaires sont présentées lorsque vous accédez à ces étapes.

## <a name="step-3-set-up-intune"></a>Étape 3 : Configurer Intune

Intune utilise de nombreuses fonctionnalités dans Azure AD, y compris votre domaine, vos utilisateurs et vos groupes. Vous pouvez également créer de nouveaux utilisateurs et des groupes en fonction des besoins de votre entreprise. Par exemple, vous pouvez créer un groupe appelé **appareils iOS**ou **aux utilisateurs de toutes les ressources humaines**.  Tirez parti des [Groupes dynamiques](https://docs.microsoft.com/intune/groups-add) qui vous permet de créer des utilisateurs ou groupes de périphériques basées sur des règles simples ou avancées.

Cette étape se concentre sur la configuration Intune et préparation vous permet de gérer vos périphériques.

1. **[Confirmer vos périphériques sont pris en charge](https://docs.microsoft.com/intune/supported-devices-browsers)**. Vérifiez votre iOS, Mac OS, les appareils Android, Galaxy et Windows sont pris en charge par Intune. Si votre organisation inclut des périphériques qui ne sont pas pris en charge, les stratégies ne sont pas appliquées à ces périphériques.

2. **[Personnaliser votre nom de domaine](https://docs.microsoft.com/intune/custom-domain-name-configure)**. Par défaut, un domaine nommé par exemple, **votre domain.onmicrosoft.com** est automatiquement créé dans Azure AD. **onmicrosoft.com** peut être personnalisé pour votre organisation. Lorsque vous personnalisez, il procure également aux utilisateurs un domaine familière lors de la connexion à Intune et l’utilisation des ressources.

3. **[Se connecter à Intune](https://docs.microsoft.com/intune/account-sign-up)**. Lorsque vous vous connectez, vous pouvez être invité à entrer des informations sur votre organisation. Intune est inclus avec Microsoft 365 et peut être ouverts directement à partir du [portail d’administration d’Office 365](https://portal.office.com/). Vous pouvez également ouvrir Intune directement à partir du [portail Azure](https://portal.azure.com).

4. **[Choisir votre configuration de la gestion des appareils mobiles](https://docs.microsoft.com/intune/mdm-authority-set)**. La première fois que vous utilisez Intune, vous devez activer la gestion de périphériques. Intune peut être utilisé comme un service en nuage uniquement, un déploiement hybride avec Intune et System Center Configuration Manager ou à l’aide de la gestion des périphériques mobiles pour Office 365. Vous pouvez choisir les paramètres convient le mieux pour votre organisation.

5. **[Ajouter des utilisateurs](https://docs.microsoft.com/intune/users-add)** et **[Ajouter des groupes](https://docs.microsoft.com/intune/groups-add)**. 

   Vous pouvez manuellement ajouter des utilisateurs, ou vous connecter à AD Azure aux utilisateurs de la synchronisation avec Intune. Vous pouvez également attribuer des rôles d’administrateur à des utilisateurs spécifiques. Les utilisateurs sont requis, sauf si vos périphériques sont « userless », tels que les appareils kiosk.

   Azure AD groupes sont utilisés pour simplifier la gestion des périphériques et des utilisateurs dans Intune. À l’aide de groupes, vous pouvez effectuer plusieurs tâches différentes. Par exemple, votre organisation souhaite nécessitent une application spécifique sur les appareils Android. Vous pouvez créer un groupe de périphériques Android et déployer une stratégie de cette application au groupe.

    Dans Intune, vous pouvez ajouter des utilisateurs ou des groupes que vous créez dans [Phase 2 : identité](https://docs.microsoft.com/microsoft-365/enterprise/identity-infrastructure)

6. **[Attribution de licences](https://docs.microsoft.com/intune/licenses-assign)**. Pour des utilisateurs ou des périphériques à inscrire dans Intune, dont ils ont besoin d’une licence sur l’appareil. Chaque utilisateur ou périphérique userless nécessite une licence de Intune pour accéder au service Intune. Ces licences sont inclus avec Microsoft 365 et doivent être assignés dans Intune.

## <a name="step-4-enroll-devices"></a>Étape 4 : Inscrire des périphériques

Pour gérer les périphériques, les périphériques doivent être inscrits dans Intune. En tant qu’administrateur, vous allez définir des restrictions d’inscription et des stratégies pour vos utilisateurs et des périphériques. Chaque plate-forme de périphérique (iOS, Android, Mac OS et Windows) a de nombreuses options. Vous pouvez demander à vos utilisateurs lui-même s’inscrire. Ou bien, vous pouvez automatiser l’inscription afin que les utilisateurs simplement se connecter au périphérique.

L’inscription est une étape clée lors de l’utilisation Intune. [Inscrire les appareils](https://docs.microsoft.com/intune/device-enrollment) répertorie les étapes pour les différents appareils.

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide de laboratoire de test : iOS et inscription de l’appareil Android](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md) |
|||


## <a name="step-5-add-and-deploy-apps"></a>Étape 5 : Ajouter et déployer des applications

Les applications sur les appareils mobiles sont souvent que les manière dont les utilisateurs plus rapides accéder à vos ressources d’entreprise. 

Il existe difficultés lors de l’utilisation des applications, il existe différents appareils, y compris les périphériques personnels et entreprise. Et, que vous souhaitez protéger les ressources de votre organisation et ses données régulations utilisateurs sont productifs.

Intune peut gérer des applications, y compris ajouter des applications, les affecter à différents utilisateurs ou groupes et passez en revue les autres détails de la clé. Par exemple, vous pouvez voir les applications échouent de l’installation, vérifiez la version d’une application et bien plus encore.

Lorsque les utilisateurs obtiennent un appareil mobile, une des premières tâches consiste à accéder aux documents et au courrier électronique d’organisation. À l’aide de Intune, vous pouvez [créer et déployer les paramètres du courrier](https://docs.microsoft.com/intune/email-settings-configure) à l’aide d’applications de messagerie sont pré-installé sur les appareils. 

[Ajouter les applications](https://docs.microsoft.com/intune/app-management) répertorie les étapes pour ajouter, déployer, surveiller, configurer et protéger des applications sur des périphériques au sein de votre organisation.

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide de laboratoire de test : Stratégies de gestion des applications mobiles](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md) |
|||

## <a name="step-6-turn-on-compliance-and-conditional-access"></a>Étape 6 : Activer la conformité et l’accès conditionnel

Dans les étapes précédentes, vous configurez votre environnement et activé Intune. Maintenant, vous êtes prêt à créer des stratégies à l’aide d’accès conditionnel et conformité.

Accès conditionnel et conformité sont importants pour la gestion des appareils. **[Stratégies de conformité](https://docs.microsoft.com/intune/device-compliance-get-started)** sont créés pour vous aider à protéger les ressources de votre organisation. Lorsque vous créez une stratégie de conformité, vous définissez la norme ou « planifié » d’un périphérique doit avoir. Par exemple, choisissez un niveau acceptable (ou inacceptable) menace, bloquer jailbroken périphériques, exiger une longueur de mot de passe et bien plus encore. Si ces périphériques ne répondent pas à vos règles, ce qui signifie qu’ils ne sont pas compatibles, vous pouvez bloquer l’accès à vos ressources.

Il présente les **[accès conditionnel](https://docs.microsoft.com/intune/conditional-access)**« blocage ». Si un périphérique est considéré comme non conforme, vous pouvez bloquer l’accès au courrier électronique et SharePoint.

Intune dans le [portail Azure](https://portal.azure.com) vous permet de créer ces stratégies et les appliquer à vos utilisateurs et des périphériques. Meilleure pratique, commencez petit et utilisez une approche progressive. Par exemple, créer une stratégie d’iOS qui bloque les périphériques jailbroken. Appliquer (appelée « attribuer » dans Intune) de la stratégie à un groupe pilote ou de test. Après le test initial, ajoutez davantage d’utilisateurs dans le groupe pilote. À l’aide d’une approche intermédiaire, vous pouvez obtenir des commentaires à partir d’un large éventail de types d’utilisateur.

[Prendre en main des stratégies de conformité périphérique](https://docs.microsoft.com/intune/device-compliance-get-started) et [What ' s accès conditionnel ?](https://docs.microsoft.com/intune/conditional-access) peut vous aider à démarrer.

## <a name="step-7-apply-features-and-settings"></a>Étape 7 : Appliquer des fonctionnalités et des paramètres

Ces fonctionnalités et les paramètres sont souvent considérés comme la partie « cool » de Intune et sont très puissants. Une fois que vous avez correctement appliqué des stratégies de conformité à l’aide d’accès conditionnel, vous êtes prêt à créer des **profils de périphérique**.

Intune dans le [portail Azure](https://portal.azure.com) permet de créer des profils différents en fonction de votre plate-forme de périphérique - iOS, Mac OS, Android et Windows. Par exemple, vous pouvez :

- Utilisez Endpoint protection sur des appareils Windows 10 pour activer les différentes options de BitLocker, y compris le chiffrement.
- Utiliser la fonctionnalité d’applications restreints sur des appareils iOS pour créer une liste des applications approuvées qui peut être installé. Ou bien, créez une liste d’applications interdites.
- Utilisez les paramètres Kiosk pour choisir les applications qui peuvent être utilisées sur les appareils Android en cours d’exécution en mode plein écran.
- Appliquer une connexion Wi-Fi et ses paramètres, notamment le type de sécurité sur les appareils exécutant Mac OS.
- Et bien plus encore

[Présentation des profils de périphérique Microsoft Intune ?](https://docs.microsoft.com/intune/device-profiles) est l’endroit idéal pour en savoir plus sur les profils, voir créer un profil et bien plus encore.

N’oubliez pas, commencez petit et utiliser une approche progressive. Attribuer le profil à un groupe pilote ou de test. Affecter le profil à plusieurs groupes de pilotes.

## <a name="step-8-get-to-know-the-other-features"></a>Étape 8 : Apprenez à connaître les autres fonctionnalités

Intune est un service puissant et inclut de nombreuses fonctionnalités. Voici d’autres tâches que vous pouvez effectuer à l’aide de Intune :

- Gérer les logiciels et les mises à jour sur les [appareils](https://docs.microsoft.com/intune/windows-update-for-business-configure)Windows & [PC](https://docs.microsoft.com/intune/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)et appareils [iOS](https://docs.microsoft.com/intune/software-updates-ios)
- Activer [Windows Defender Advanced Threat Protection (DAV)](https://docs.microsoft.com/intune/advanced-threat-protection) sur vos périphériques Windows 10 et permet de protéger l’accès aux ressources d’entreprise, tels que SharePoint ou Exchange Online accès conditionnel et conformité
- Utilisez [affût](https://docs.microsoft.com/intune/lookout-mobile-threat-defense-connector), [Symantec](https://docs.microsoft.com/intune/skycure-mobile-threat-defense-connector)et autres partenaires de menace de défense mobile
- Ajouter une [autorité de certification partenaire (CA)](https://docs.microsoft.com/intune/certificate-authority-add-scep-overview) pour émettre et renouveler des certificats
- [Conseils de fournir à vos utilisateurs finaux](https://docs.microsoft.com/intune/end-user-educate) sur l’application de portail d’entreprise, mise en route apps, etc.
- Surveiller des [applications](https://docs.microsoft.com/intune/apps-monitor), surveiller [la conformité du périphérique](https://docs.microsoft.com/intune/compliance-policy-monitor), de surveiller [les profils de configuration](https://docs.microsoft.com/intune/compliance-policy-monitor)et télémétrie plus à l’aide des journaux d’audit. Vous pouvez également vous connecter à l' [Entrepôt de données Intune](https://docs.microsoft.com/intune/reports-nav-create-intune-reports) et utiliser Power BI pour les besoins en matière de création de rapports encore plus.


## <a name="identity-and-device-access-recommendations"></a>Recommandations d’accès aux identités et des périphériques

Microsoft propose un ensemble de recommandations pour l' [accès identité et de périphérique](microsoft-365-policies-configurations.md) garantir un personnel sécurisé et efficace. Accès des appareils, utilisez les recommandations et les paramètres dans les articles suivants, ainsi que les étapes de cette phase :

- [Conditions préalables](identity-access-prerequisites.md)
- [Stratégies communes pour les identités et l’accès aux appareils](identity-access-policies.md)

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Découvrez comment les experts informatiques chez Microsoft planifiées pour et déploiement gestion EMS et des périphériques avec ces ressources :

- [Gérer la productivité à l’ère mobile avec Enterprise Mobility + Security](https://www.microsoft.com/itshowcase/Article/Content/972/Managing-modern-mobile-productivity-with-Enterprise-Mobility--Security)
- [Connexion pour travailler sur votre appareil Windows 10 avec Microsoft Intune](https://www.microsoft.com/itshowcase/Article/Content/783/Connecting-to-work-on-your-Windows-10-device-with-Microsoft-Intune)
- [Optimisation de la productivité mobile pour les appareils Android, iOS et OS X chez Microsoft](https://www.microsoft.com/itshowcase/Article/Content/773/Enabling-mobile-productivity-for-iOS-OS-X-and-Android-devices-at-Microsoft)

## <a name="how-contoso-did-microsoft-365-enterprise"></a>Comment Contoso est-elle passée à Microsoft 365 Entreprise ?

Voir comment la société Contoso, une entreprise multinationale fictive mais représentative, [déployé son infrastructure de gestion des appareils mobiles](contoso-mdm.md) avec Microsoft 365 services en nuage.

![](./media/contoso-overview/contoso-icon.png)

## <a name="next-step"></a>Étape suivante

[Critères de sortie de l’infrastructure de gestion appareil mobile](mobility-infrastructure-exit-criteria.md)

