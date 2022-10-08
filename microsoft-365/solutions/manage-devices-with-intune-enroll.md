---
title: Step 2. Enroll devices into management with Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- enroll devices into management
- enroll devices to Intune
- Intune mobile device platforms
manager: dougeby
audience: ITPro
description: Utilisez Intune et Autopilot pour inscrire des appareils dans la gestion afin de veiller à ce que les applications qui s’exécutent sur ceux-ci soient conformes et d’empêcher les fuites de données d’entreprise.
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: high
ms.collection:
- highpri
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
keywords: ''
ms.openlocfilehash: 0c6e49b3a654f29b76016487f88126ae77a2630c
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67986595"
---
# <a name="step-2-enroll-devices-to-intune"></a>Étape 2. Inscrire des appareils dans Intune

Il existe plusieurs façons de sécuriser le point de terminaison, un terme souvent utilisé pour désigner l'entité combinée, notamment les appareils, les applications et l'identité de l'utilisateur. Les politiques de sécurité doivent être appliquées de manière cohérente et fiable non seulement sur les applications, mais aussi sur l'appareil lui-même. L'inscription de l'appareil à Intune et son enregistrement auprès d'un fournisseur d'identité en nuage, tel qu'Azure Active Directory, constituent un excellent début.

Qu'il s'agisse d'un appareil BYOD personnel ou d'un appareil appartenant à l'entreprise et entièrement géré, il est bon d'avoir une visibilité sur les points de terminaison accédant aux ressources de votre organisation pour vous assurer que vous n'autorisez que des appareils sains et conformes. Cela inclut la santé et la fiabilité des applications mobiles et de bureau qui s'exécutent sur les terminaux. Vous voulez vous assurer que ces applications sont saines et conformes et qu'elles empêchent les données d'entreprise de fuir vers les applications ou les services grand public par le biais d'intentions malveillantes ou de moyens accidentels.

Le processus d'inscription de l'appareil établit une relation entre l'utilisateur, l'appareil et le service Microsoft Intune. L'utilisation de Microsoft Intune en tant que service autonome vous permet d'utiliser une console d'administration Web unique pour gérer les PC Windows, macOS et les plates-formes d'appareils mobiles les plus populaires.

This article recommends methods for enrolling devices to Intune. For more information about these methods and how to deploy each one, see [Deployment guidance: Enroll devices in Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment).

![Étapes de gestion des appareils](../media/devices/intune-mdm-steps-1.png#lightbox)

Utilisez les conseils de cet article avec cette version illustrée des options d’inscription pour chaque plateforme. 

[![Représentation visuelle des options d’inscription Intune par plateforme](../media/devices/msft-intune-enrollment-options-thumb-landscape.png)](https://download.microsoft.com/download/e/6/2/e6233fdd-a956-4f77-93a5-1aa254ee2917/msft-intune-enrollment-options.pdf) <br/> [PDF](https://download.microsoft.com/download/e/6/2/e6233fdd-a956-4f77-93a5-1aa254ee2917/msft-intune-enrollment-options.pdf) | [Visio](https://download.microsoft.com/download/e/6/2/e6233fdd-a956-4f77-93a5-1aa254ee2917/msft-intune-enrollment-options.vsdx) <br/> Mise à jour de juin 2022



## <a name="windows-enrollment"></a>Inscription de Windows
Il existe plusieurs options pour inscrire des appareils Windows 10 et Windows 11. Les méthodes les plus courantes incluent ces deux:

- Joindre Azure Active Directory (Azure AD) – Rejoint l'appareil à Azure Active Directory Domain Services et permet aux utilisateurs de se connecter à Windows avec leurs informations d'identification Azure AD. Si l'inscription automatique est activée, l'appareil est automatiquement inscrit dans Intune. L’avantage de l’inscription automatique est qu’il s’agit d’un processus à étape unique pour l’utilisateur. Autrement, il devra s’inscrire séparément par le biais de l’inscription à MDM uniquement, et entrer à nouveau ses informations d’identification. Les utilisateurs s’inscrivent de cette façon pendant la phase OOBE Windows initiale ou à partir de Paramètres. L'appareil est marqué comme un appareil appartenant à l'entreprise dans Intune.
- Pilote automatique – Automatise Azure AD Join et inscrit de nouveaux appareils appartenant à l'entreprise dans Intune. Cette méthode simplifie l'expérience prête à l'emploi et élimine le besoin d'appliquer des images de système d'exploitation personnalisées sur les appareils. Lorsque les administrateurs utilisent Intune pour gérer les appareils Autopilot, ils peuvent gérer les stratégies, les profils, les applications, etc. après leur inscription. Il existe quatre types de déploiement de pilote automatique : le mode de déploiement automatique (pour les kiosques, la signalisation numérique ou un appareil partagé), le mode piloté par l'utilisateur (pour les utilisateurs traditionnels), le pilote automatique Windows pour le déploiement pré-provisionné permet aux partenaires ou au personnel informatique de pré-provisionner un PC exécutant Windows 10 ou Windows 11 afin qu'il soit entièrement configuré et prêt pour l'entreprise, et Autopilot pour les appareils existants vous permet de déployer facilement la dernière version de Windows sur vos appareils existants.

Pour obtenir des options supplémentaires, notamment l’inscription d’appareils Windows BYOD, consultez [Inscrivez les appareils Windows dans Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-windows).

## <a name="ios-and-ipados-enrollment"></a>Inscription iOS et iPadOS

Pour les appareils appartenant à l'utilisateur (BYOD), vous pouvez laisser les utilisateurs inscrire leurs appareils personnels à Intune en utilisant l'une des méthodes suivantes.
- L'inscription de l'appareil est ce que vous pouvez considérer comme une inscription BYOD typique. Elle offre aux administrateurs un large éventail d'options de gestion.
- User enrollment is a more streamlined enrollment process that provides admins with a subset of device management options. This feature is currently in preview.

Pour les organisations qui achètent des appareils pour leurs utilisateurs, Intune prend en charge les méthodes d'inscription d'appareils appartenant à l'entreprise iOS/iPadOS suivantes :
- Inscription d’appareils automatisée Apple (ADE)
- Apple School Manager
- Inscription par le biais de l’Assistant Configuration Apple Configurator
- Inscription directe Apple Configurator

Pour plus d’informations, consultez [Inscrivez les appareils iOS et iPadOS dans Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados).

## <a name="android-enrollment"></a>Inscription Android 

There are several options for Android Enrollment depending on the type of device, the type of enrollment you’d like to support, as well as things like the Android version you are using or even the manufacturer (particularly Samsung). Most organizations use Android Work profiles for their end users, particular in BYOD scenarios. 

Avec un profil de travail Android, les informations de l'utilisateur final sont séparées distinctement avec des conteneurs de données ainsi que des applications distinctes pour le travail et l'utilisation personnelle. C'est un moyen idéal pour les utilisateurs d'inscrire leur appareil tout en préservant la confidentialité de leurs propres données et la sécurité des données d'entreprise. 

Cependant, si votre organisation fournit des appareils Android, vous pouvez choisir d'utiliser ce qu'on appelle un appareil entièrement géré (affinité utilisateur) ou dédié (aucune affinité utilisateur).

Pour en savoir plus sur l’inscription Android, consultez [Inscrire des appareils Android dans Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android).

## <a name="macos-enrollment"></a>Inscription macOS DEP

L'inscription pour macOS peut être un sujet délicat pour de nombreuses organisations informatiques. À moins qu'une majorité de vos utilisateurs ne soient des utilisateurs de Mac, vous ne gérez peut-être pas ces types d'appareils dans une large mesure. Si vous avez un petit nombre d'utilisateurs de macOS, nous vous recommandons l'inscription Intune uniquement. Si vous avez un grand nombre d'utilisateurs de macOS, nous vous recommandons l'inscription Intune + Jamf.  
- Inscription Intune uniquement : Ceci est pour la gestion de base des appareils macOS. Cela nécessitera un processus manuel tout comme la plupart des autres options d'inscription basées sur l'utilisateur. Mais si vous disposez d'un petit nombre d'appareils Mac, cela peut être plus facile que de mettre en place une infrastructure entièrement automatisée uniquement pour ces quelques utilisateurs. Avec l'inscription Intune uniquement, vous avez la possibilité de déployer des éléments tels que des certificats, des configurations de mot de passe et des applications. Vous pouvez également configurer des politiques de conformité et éclairer l'accès conditionnel ainsi que la possibilité d'appliquer le chiffrement et l'effacement des appareils. 
- Inscription à Intune et Jamf : Pour ceux qui recherchent la prise en charge la plus complète de la gestion Mac, avec Jamf + Intune pour l'accès conditionnel, nous avons une excellente solution qui combine les capacités étendues de gestion Mac de Jamf avec la conformité Intune pour activer l'accès conditionnel. Dans ce scénario, vous gérez toujours entièrement l'appareil avec Jamf tout en étant capable de prendre ces signaux de Jamf pour une sécurité accrue.

Pour en savoir plus sur l’inscription macOS, consultez [Inscrire des appareils Android dans Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-macos).

## <a name="next-steps"></a>Prochaines étapes

Passez à l'étape [3. Configurez des stratégies de conformité pour les appareils avec Intune](manage-devices-with-intune-compliance-policies.md).

