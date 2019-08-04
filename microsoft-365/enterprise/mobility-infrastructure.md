---
title: 'Phase 5: gestion des appareils mobiles'
description: Microsoft 365 Enterprise inclut la gestion des appareils mobiles à l’aide de Microsoft Intune. Passez en revue les conditions requises et les conditions préalables, configurez Intune à l’aide de votre ressource Azure Active Directory, inscrivez iOS, macOS, Android et appareils Windows, déployer des applications, créer un profil, utiliser une stratégie de conformité et activer l’accès conditionnel pour les appareils mobiles gestion des appareils avec Microsoft 365 Enterprise.
keywords: Microsoft 365, Microsoft 365 entreprise, documentation Microsoft 365, gestion des appareils mobiles, Intune
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/18/2018
ms.topic: conceptual
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.assetid: fb4182e6-5e78-45d0-9641-d791c4519441
audience: ITPro
ms.custom: microsoft-intune
ms.openlocfilehash: 0ee9696d441d61fb41359f6502e6f73988749156
ms.sourcegitcommit: 12fbb429dba7517220191d90816e235583943fe0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "33623148"
---
# <a name="phase-5-mobile-device-management-for-microsoft-365-enterprise"></a>Phase 5: gestion des appareils mobiles pour Microsoft 365 Enterprise

![](./media/deploy-foundation-infrastructure/mobiledevicemgmt_icon.png)

*Cette fonctionnalité s’applique aux versions E3 et E5 de Microsoft 365 Enterprise*

Microsoft 365 Enterprise inclut des fonctionnalités qui permettent de gérer les appareils et leurs applications au sein de votre organisation. À l’aide de Microsoft Intune, vous pouvez gérer les appareils iOS, Android, macOS et Windows pour protéger l’accès aux ressources de votre organisation, y compris vos données. Intune s’intègre à Azure Active Directory (Azure AD) et active les scénarios d’entreprise suivants pour Microsoft 365:

- Stocker et partager des fichiers internes ou externes à votre entreprise pour travailler en toute transparence au-delà des frontières structurelles
- Travailler en toute sécurité avec votre appareil en tout lieu et à tout moment pour atteindre plus d’objectifs, en conservant une méthode de travail flexible
- Assurer la tranquillité d’esprit grâce à des contrôles et une visibilité sur votre conformité, vérifiée par le secteur, avec les normes internationales
- Protéger vos informations et réduire le risque de perte de données
- Détecter et se protéger contre les menaces externes
- Surveiller, créer des rapports et analyser l’activité afin de réagir rapidement à la sécurité de l’Organisation
- Protéger vos utilisateurs et leurs comptes

Pour plus d’informations, reportez-vous à la page relative à la [transformation numérique avec Microsoft 365](http://transform.microsoft.com). 

Lors de cette phase, vous allez inscrire vos appareils dans Intune, puis créer et appliquer des stratégies pour sécuriser et protéger vos données. La bibliothèque complète de la documentation Intune est [disponible en ligne](https://docs.microsoft.com/intune). Il est également recommandé de consulter le [Guide de planification, de conception et de mise en œuvre de Intune](https://docs.microsoft.com/intune/planning-guide) avant de commencer.

## <a name="step-1-plan-for-your-scenario"></a>Étape 1: planifier votre scénario

L’une des principales raisons de gérer les appareils mobiles est de sécuriser et de protéger les ressources de votre organisation. Les [méthodes courantes d’utilisation de Microsoft Intune](https://docs.microsoft.com/intune/common-scenarios) répertorient certains exemples concrets, notamment la sécurisation du courrier électronique et des données Office 365.

Intune vous offre des options pour gérer l’accès à votre organisation à l’aide de la [gestion des appareils mobiles (MDM) ou de la gestion des applications mobiles (MAM)](https://docs.microsoft.com/intune/byod-technology-decisions). MDM est lorsque les utilisateurs «inscrivent» leurs appareils dans Intune. Une fois l’enregistrement effectué, il s’agit d’appareils gérés et peut recevoir toutes les stratégies, les règles et les paramètres utilisés par votre organisation. Par exemple, vous pouvez installer des applications spécifiques, créer une stratégie de mot de passe, installer une connexion VPN, et bien plus encore.

Les utilisateurs disposant de leurs propres appareils personnels peuvent ne pas vouloir inscrire leurs appareils ou être gérés par Intune et vos stratégies. Toutefois, vous devez toujours protéger les ressources et les données de votre organisation. Dans ce scénario, vous pouvez protéger vos applications à l’aide de MAM. Par exemple, vous pouvez utiliser une stratégie MAM qui exige qu’un utilisateur entre un code confidentiel lors de l’accès à SharePoint sur l’appareil.

Vous allez également déterminer la manière dont vous allez gérer les appareils personnels ou appartenant à l’organisation. Vous souhaiterez peut-être traiter les appareils différemment en fonction de leur utilisation. Par exemple, vous pouvez souhaiter des plans différents pour les utilisateurs dans les ressources humaines (RH) ou les utilisateurs dans les ventes. [Identifier les scénarios d’utilisation de la gestion des appareils mobiles: les scénarios](https://docs.microsoft.com/intune/planning-guide-scenarios) peuvent vous aider à démarrer et incluent des conseils sur ces différents scénarios.

## <a name="step-2-get-your-prerequisites"></a>Étape 2: obtenir vos conditions préalables

Ensuite, obtenez vos conditions préalables en fonction de vos besoins et de vos scénarios créés à l’étape précédente. [Implement Your plan](https://docs.microsoft.com/intune/planning-guide-onboarding) répertorie toutes les conditions requises. Voici les éléments importants dont vous avez besoin pour Intune avec Microsoft 365:

- **Abonnement Intune**: inclus dans Microsoft 365 et vous donne accès à Microsoft Intune dans le [portail Azure](https://portal.azure.com)
- **Abonnement office 365**: inclus dans Microsoft 365 et est utilisé pour les applications Office, y compris le courrier électronique
- **Azure Active Directory (Azure AD) Premium**: inclus dans Microsoft 365 et permet de créer des groupes d’utilisateurs ou de sécurité. Ces groupes reçoivent des stratégies Intune que vous créez, par exemple en forçant une longueur de mot de passe pour déverrouiller un appareil. Les groupes que vous créez à la [phase 2: Identity](https://docs.microsoft.com/microsoft-365/enterprise/identity-infrastructure) peuvent être utilisés.

Il peut y avoir des exigences supplémentaires en fonction des besoins de votre organisation. Par exemple, si vous gérez des appareils iOS, vous aurez besoin d’un certificat de transmission de type tablette Apple. Si vous utilisez Exchange sur site, vous aurez besoin du connecteur Exchange local. Ces exigences supplémentaires sont décrites lorsque vous accédez à ces étapes.

## <a name="step-3-set-up-intune"></a>Étape 3: configurer Intune

Intune utilise de nombreuses fonctionnalités d’Azure AD, notamment votre domaine, vos utilisateurs et vos groupes. Vous pouvez également créer des utilisateurs et des groupes pour répondre aux besoins de votre entreprise. Par exemple, vous pouvez créer un groupe appelé **appareils iOS**ou **tous les utilisateurs RH**.  Tirez parti des [groupes dynamiques](https://docs.microsoft.com/intune/groups-add) qui vous permettent de créer des groupes d’utilisateurs ou des groupes d’appareils en fonction de règles simples ou avancées.

Cette étape traite de la configuration d’Intune et de la préparation de vos appareils.

1. **[Vérifiez que vos appareils sont pris en charge](https://docs.microsoft.com/intune/supported-devices-browsers)**. Vérifiez que les appareils iOS, macOS, Android, Galaxy et Windows sont pris en charge par Intune. Si votre organisation inclut des appareils qui ne sont pas pris en charge, les stratégies ne sont pas appliquées à ces appareils.

2. **[Personnalisez le nom de votre domaine](https://docs.microsoft.com/intune/custom-domain-name-configure)**. Par défaut, un domaine nommé « **Your-Domain.onmicrosoft.com** » est automatiquement créé dans Azure ad. les **onmicrosoft.com** peuvent être personnalisés pour votre organisation. Lorsque vous personnalisez, il fournit également aux utilisateurs un domaine familier lors de la connexion à Intune et de l’utilisation des ressources.

3. **[Connectez-vous à Intune](https://docs.microsoft.com/intune/account-sign-up)**. Lorsque vous vous connectez, vous pouvez être invité à entrer des informations sur votre organisation. Intune est inclus dans Microsoft 365 et peut être ouvert directement à partir du [Centre d’administration microsoft 365](https://admin.microsoft.com). Vous pouvez également ouvrir Intune directement à partir du [portail Azure](https://portal.azure.com).

4. **[Choisissez la configuration de la gestion des appareils mobiles](https://docs.microsoft.com/intune/mdm-authority-set)**. La première fois que vous utilisez Intune, vous devez activer la gestion des appareils. Intune peut être utilisé en tant que service en nuage seul, hybride avec Intune et System Center Configuration Manager, ou à l’aide de la gestion des appareils mobiles pour Office 365. Vous pouvez choisir le programme d’installation le mieux adapté à votre organisation.

5. **[Ajouter des utilisateurs](https://docs.microsoft.com/intune/users-add)** et **[Ajouter des groupes](https://docs.microsoft.com/intune/groups-add)**. 

   Vous pouvez ajouter manuellement des utilisateurs ou vous connecter à Azure AD pour synchroniser des utilisateurs avec Intune. Vous pouvez également attribuer des rôles d’administrateur à des utilisateurs spécifiques. Les utilisateurs sont obligatoires sauf si vos appareils sont des appareils «sans utilisateur», tels que des appareils Kiosk.

   Les groupes Azure AD sont utilisés pour simplifier la gestion des appareils et des utilisateurs dans Intune. À l’aide de groupes, vous pouvez effectuer de nombreuses tâches différentes. Par exemple, votre organisation souhaite exiger une application spécifique sur les appareils Android. Vous pouvez créer un groupe de périphériques Android et déployer une stratégie avec cette application dans le groupe.

    Dans Intune, vous pouvez ajouter des utilisateurs ou des groupes que vous créez à la [phase 2: Identity](https://docs.microsoft.com/microsoft-365/enterprise/identity-infrastructure)

6. **[Attribuer des licences](https://docs.microsoft.com/intune/licenses-assign)**. Pour les utilisateurs ou les appareils à inscrire dans Intune, ils ont besoin d’une licence sur l’appareil. Chaque utilisateur ou appareil sans utilisateur nécessite une licence Intune pour accéder au service Intune. Ces licences sont incluses dans Microsoft 365 et doivent être affectées dans Intune.

## <a name="step-4-enroll-devices"></a>Étape 4: inscrire des appareils

Pour gérer les appareils, les appareils doivent être déployés dans Intune. En tant qu’administrateur, vous pouvez configurer des stratégies et des restrictions d’inscription pour vos utilisateurs et appareils. Chaque plateforme de périphérique (iOS, Android, macOS et Windows) comporte plusieurs options. Vous pouvez faire en sorte que vos utilisateurs s’inscrivent eux-mêmes. Vous pouvez aussi automatiser l’inscription afin que les utilisateurs se connectent simplement à l’appareil.

L’enregistrement est une étape essentielle lors de l’utilisation d’Intune. [Inscrire des appareils](https://docs.microsoft.com/intune/device-enrollment) répertorie les étapes pour les différents appareils.

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide de laboratoire de test: enregistrement des appareils iOS et Android](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md) |
|||


## <a name="step-5-add-and-deploy-apps"></a>Étape 5: ajouter et déployer des applications

Les applications sur les appareils mobiles sont souvent le moyen le plus rapide pour les utilisateurs d’accéder à vos ressources d’entreprise. 

Il existe des difficultés lors de l’utilisation d’applications, car il existe différents appareils, notamment des appareils personnels et des appareils d’entreprise. De plus, vous souhaitez protéger les ressources de votre organisation et ses données tout en veillant à ce que les utilisateurs soient productifs.

Intune peut gérer les applications, y compris ajouter des applications, les affecter à différents utilisateurs ou groupes, et passer en revue d’autres détails clés. Par exemple, vous pouvez voir les applications dont l’installation a échoué, vérifier la version d’une application, et bien plus encore.

Lorsque les utilisateurs obtiennent un appareil mobile, l’une des premières tâches consiste à accéder aux documents et à la messagerie de l’organisation. À l’aide d’Intune, vous pouvez [créer et déployer des paramètres de messagerie](https://docs.microsoft.com/intune/email-settings-configure) à l’aide d’applications de messagerie pré-installées sur les appareils. 

[Ajouter des applications](https://docs.microsoft.com/intune/app-management) répertorie les étapes d’ajout, de déploiement, de surveillance, de configuration et de protection des applications sur les appareils au sein de votre organisation.

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide de laboratoire de test: stratégies de conformité des appareils](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md) |
|||

## <a name="step-6-turn-on-compliance-and-conditional-access"></a>Étape 6: activer la conformité et l’accès conditionnel

Dans les étapes précédentes, vous configurez votre environnement et vous avez activé Intune. À présent, vous êtes prêt à créer des stratégies à l’aide de la conformité et de l’accès conditionnel.

La conformité et l’accès conditionnel sont importants pour la gestion des appareils. Des **[stratégies de conformité](https://docs.microsoft.com/intune/device-compliance-get-started)** sont créées pour vous aider à protéger les ressources de votre organisation. Lorsque vous créez une stratégie de conformité, vous définissez la norme ou la «planification» de ce qu’un appareil doit disposer. Par exemple, vous pouvez choisir un niveau de menace acceptable (ou inacceptable), bloquer les appareils un jailbreak, exiger une longueur de mot de passe et bien plus encore. Si ces appareils ne répondent pas à vos règles, ce qui signifie qu’ils ne sont pas conformes, vous pouvez bloquer l’accès à vos ressources.

Ce «blocage» introduit un **[accès conditionnel](https://docs.microsoft.com/intune/conditional-access)**. Si un appareil est considéré comme non conforme, vous pouvez bloquer l’accès à la messagerie, à SharePoint et bien plus encore.

Intune dans le [portail Azure](https://portal.azure.com) vous permet de créer ces stratégies et de les appliquer à vos utilisateurs et appareils. Il est recommandé de commencer petit et d’utiliser une approche intermédiaire. Par exemple, créez une stratégie iOS qui bloque les périphériques un jailbreak. Apply (appelé «Assign» dans Intune) la stratégie à un groupe pilote ou à un groupe de test. Après les tests initiaux, ajoutez d’autres utilisateurs au groupe pilote. À l’aide d’une approche intermédiaire, vous pouvez obtenir des commentaires d’une large gamme de types d’utilisateurs.

[Prise en main des stratégies de conformité des appareils](https://docs.microsoft.com/intune/device-compliance-get-started) et [de l’accès conditionnel](https://docs.microsoft.com/intune/conditional-access) : peut vous aider à commencer.

## <a name="step-7-apply-features-and-settings"></a>Étape 7: application des fonctionnalités et des paramètres

Ces fonctionnalités et paramètres sont souvent considérés comme la partie «sympa» de Intune, qui sont très puissants. Une fois que vous avez appliqué certaines stratégies de conformité à l’aide de l’accès conditionnel, vous êtes prêt à créer des **profils d’appareil**.

Intune dans le [portail Azure](https://portal.azure.com) vous permet de créer différents profils en fonction de votre plateforme de périphérique-iOS, MacOS, Android et Windows. Par exemple, vous pouvez :

- Utilisez Endpoint Protection sur les appareils Windows 10 pour activer différentes options BitLocker, y compris le chiffrement.
- Utilisez la fonctionnalité applications restreintes sur des appareils iOS pour créer une liste des applications approuvées pouvant être installées. Ou créez une liste d’applications interdites.
- Utilisez les paramètres Kiosk pour choisir les applications qui peuvent être utilisées sur les appareils Android exécutés en mode plein écran.
- Appliquer une connexion Wi-Fi et ses paramètres, y compris le type de sécurité, sur les appareils exécutant macOS.
- Et bien plus encore

[Qu’est-ce que les profils d’appareils Microsoft Intune?](https://docs.microsoft.com/intune/device-profiles) est un emplacement idéal pour lire les profils, voir comment créer un profil, et bien plus encore.

N’oubliez pas que vous devez commencer petit et utiliser une approche intermédiaire. Affectez le profil à un groupe pilote ou à un groupe de test. Ensuite, affectez le profil à d’autres groupes pilotes.

## <a name="step-8-get-to-know-the-other-features"></a>Étape 8: Découvrez les autres fonctionnalités

Intune est un service puissant qui inclut de nombreuses fonctionnalités. Voici quelques autres tâches que vous pouvez effectuer à l’aide d’Intune:

- Gérer les logiciels et les mises à jour [](https://docs.microsoft.com/intune/windows-update-for-business-configure) & sur les[ordinateurs](https://docs.microsoft.com/intune/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)Windows et les appareils [iOS](https://docs.microsoft.com/intune/software-updates-ios)
- Activez [Windows Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/intune/advanced-threat-protection) sur vos appareils Windows 10 et utilisez la conformité et l’accès conditionnel pour protéger l’accès aux ressources d’entreprise, telles que SharePoint ou Exchange Online.
- Utiliser [Lookout](https://docs.microsoft.com/intune/lookout-mobile-threat-defense-connector), [Symantec](https://docs.microsoft.com/intune/skycure-mobile-threat-defense-connector)et d’autres partenaires de menaces de défense mobile
- Ajouter une [autorité](https://docs.microsoft.com/intune/certificate-authority-add-scep-overview) de certification partenaire pour émettre et renouveler des certificats
- [Fournir des conseils à vos utilisateurs finaux](https://docs.microsoft.com/intune/end-user-educate) sur l’application portail d’entreprise, obtenir des applications et plus encore
- Surveillez les [applications](https://docs.microsoft.com/intune/apps-monitor), surveillez la [conformité des appareils](https://docs.microsoft.com/intune/compliance-policy-monitor), surveillez les [profils de configuration](https://docs.microsoft.com/intune/compliance-policy-monitor)et la télémétrie à l’aide des journaux d’audit. Vous pouvez également vous connecter à l' [entrepôt de données Intune](https://docs.microsoft.com/intune/reports-nav-create-intune-reports) et utiliser Power bi pour répondre à des besoins de création de rapports supplémentaires.


## <a name="identity-and-device-access-recommendations"></a>Recommandations en matière d’identité et d’accès aux appareils

Microsoft fournit un ensemble de recommandations sur l’[accès aux appareils et à l’identité](microsoft-365-policies-configurations.md) pour garantir un personnel conforme et productif. Pour l’accès aux appareils, utilisez les recommandations et les paramètres présentés dans les articles suivants, ainsi que les étapes de cette phase:

- [Conditions préalables](identity-access-prerequisites.md)
- [Stratégies communes pour les identités et l’accès aux appareils](identity-access-policies.md)

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Découvrez comment les experts informatiques de Microsoft [gèrent les appareils avec EMS](https://www.microsoft.com/en-us/itshowcase/deploying-and-managing-microsoft-365#primaryR8).

## <a name="how-contoso-did-microsoft-365-enterprise"></a>Comment Contoso est-elle passée à Microsoft 365 Entreprise ?

Découvrez comment Contoso Corporation, une entreprise multinationale fictive mais représentative, a [déployé son infrastructure de gestion des appareils mobiles](contoso-mdm.md) avec les services Cloud de Microsoft 365.

![](./media/contoso-overview/contoso-icon.png)

## <a name="next-step"></a>Étape suivante

[Critères de sortie de l’infrastructure de gestion des appareils mobiles](mobility-infrastructure-exit-criteria.md)

