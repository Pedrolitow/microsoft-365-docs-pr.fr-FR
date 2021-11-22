---
title: Étape 2. Inscrire des appareils dans la gestion avec Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: dougeby
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.custom: seo-marvel-jun2020
keywords: ''
description: ''
ms.openlocfilehash: 466bb739085625a8992595a2d518e6f1cbdeb4a4
ms.sourcegitcommit: 2ea2105d40b60a87fc9aa30f392a73a3a9db6d99
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2021
ms.locfileid: "61129196"
---
# <a name="step-2-enroll-devices-into-management-with-intune"></a>Étape 2. Inscrire des appareils dans la gestion avec Intune

Il existe plusieurs façons de sécuriser le point de terminaison, un terme souvent utilisé pour désigner l'entité combinée, notamment les appareils, les applications et l'identité de l'utilisateur. Les politiques de sécurité doivent être appliquées de manière cohérente et fiable non seulement sur les applications, mais aussi sur l'appareil lui-même. L'inscription de l'appareil dans la gestion et l'enregistrement auprès d'un fournisseur d'identité cloud, tel qu'Azure Active Directory Domain Services, est un bon début.

Qu'il s'agisse d'un appareil BYOD personnel ou d'un appareil appartenant à l'entreprise et entièrement géré, il est bon d'avoir une visibilité sur les points de terminaison accédant aux ressources de votre organisation pour vous assurer que vous n'autorisez que des appareils sains et conformes. Cela inclut la santé et la fiabilité des applications mobiles et de bureau qui s'exécutent sur les terminaux. Vous voulez vous assurer que ces applications sont saines et conformes et qu'elles empêchent les données d'entreprise de fuir vers les applications ou les services grand public par le biais d'intentions malveillantes ou de moyens accidentels.

Le processus d'inscription de l'appareil établit une relation entre l'utilisateur, l'appareil et le service Microsoft Intune. L'utilisation de Microsoft Intune en tant que service autonome vous permet d'utiliser une console d'administration Web unique pour gérer les PC Windows, macOS et les plates-formes d'appareils mobiles les plus populaires.

Cet article recommande des méthodes pour inscrire des appareils dans la gestion à l'aide d'Intune. Pour plus d'informations sur ces méthodes et sur la façon de déployer chacune d'entre elles, consultez [Guide de déploiement : Enroll devices in Microsoft Intune](/microsoft-365/security/defender/eval-overview?view=o365-worldwide).

![Étapes de gestion des appareils](../media/devices/intune-mdm-steps-1.png#lightbox)

## <a name="windows-enrollment"></a>Inscription de Windows
Il existe plusieurs options pour inscrire des appareils Windows 10 et Windows 11. Les méthodes les plus courantes incluent ces deux:

- Joindre Azure Active Directory (Azure AD) – Rejoint l'appareil à Azure Active Directory Domain Services et permet aux utilisateurs de se connecter à Windows avec leurs informations d'identification Azure AD. Si l'inscription automatique est activée, l'appareil est automatiquement inscrit dans Intune. L'avantage de l'inscription automatique est un processus en une seule étape pour l'utilisateur. Sinon, ils devront s'inscrire séparément via l'inscription MDM uniquement et saisir à nouveau leurs informations d'identification. Les utilisateurs s'inscrivent de cette manière soit lors de l'OOBE initial de Windows, soit à partir des paramètres. L'appareil est marqué comme un appareil appartenant à l'entreprise dans Intune.
- Pilote automatique – Automatise Azure AD Join et inscrit de nouveaux appareils appartenant à l'entreprise dans Intune. Cette méthode simplifie l'expérience prête à l'emploi et élimine le besoin d'appliquer des images de système d'exploitation personnalisées sur les appareils. Lorsque les administrateurs utilisent Intune pour gérer les appareils Autopilot, ils peuvent gérer les stratégies, les profils, les applications, etc. après leur inscription. Il existe quatre types de déploiement de pilote automatique : le mode de déploiement automatique (pour les kiosques, la signalisation numérique ou un appareil partagé), le mode piloté par l'utilisateur (pour les utilisateurs traditionnels), le pilote automatique Windows pour le déploiement pré-provisionné permet aux partenaires ou au personnel informatique de pré-provisionner un PC exécutant Windows 10 ou Windows 11 afin qu'il soit entièrement configuré et prêt pour l'entreprise, et Autopilot pour les appareils existants vous permet de déployer facilement la dernière version de Windows sur vos appareils existants.

Pour des options supplémentaires, y compris l'inscription d'appareils Windows BYOD, consultez [Méthodes d'inscription Intune pour les appareils Windows](/mem/intune/enrollment/windows-enrollment-methods).

## <a name="iosipados-and-ipados-enrollment"></a>Inscription iOS/iPadOS et iPadOS

Pour les appareils appartenant à l'utilisateur (BYOD), vous pouvez autoriser les utilisateurs à inscrire leurs appareils personnels pour la gestion Intune à l'aide de l'une des méthodes suivantes.
- L'inscription de l'appareil est ce que vous pouvez considérer comme une inscription BYOD typique. Il fournit des admins avec un large éventail d'options de gestion.
- L'inscription des utilisateurs est un processus d'inscription plus rationalisé qui fournit aux administrateurs un sous-ensemble d'options de gestion des appareils. Cette fonctionnalité est actuellement en préversion.

Pour les organisations qui achètent des appareils pour leurs utilisateurs, Intune prend en charge les méthodes d'inscription d'appareils appartenant à l'entreprise iOS/iPadOS suivantes :
- Enrôlement automatisé des appareils (ADE) d'Apple
- Apple School Manager
- Inscription à l'assistant de configuration Apple Configurator
- Inscription directe à Apple Configurator

Pour plus d'informations, consultez [Inscrire des appareils iOS/iPadOS dans Intune](/mem/intune/enrollment/ios-enroll).

## <a name="android-enrollment"></a>Inscription Android 

Il existe plusieurs options pour l'inscription Android selon le type d'appareil, le type d'inscription que vous souhaitez prendre en charge, ainsi que des éléments tels que la version Android que vous utilisez ou même le fabricant (en particulier Samsung). La plupart des organisations utilisent des profils Android Work pour leurs utilisateurs finaux, en particulier dans les scénarios BYOD. 

Avec un profil de travail Android, les informations de l'utilisateur final sont distinctes avec des conteneurs de données ainsi que des applications distinctes pour le travail et l'utilisation personnelle. C'est un moyen idéal pour les utilisateurs d'inscrire leur appareil tout en préservant la confidentialité de leurs propres données et la sécurité des données d'entreprise. 

Cependant, si votre organisation prouve les appareils Android, vous pouvez choisir d'utiliser ce qu'on appelle un appareil entièrement géré (affinité utilisateur) ou dédié (aucune affinité utilisateur).

Pour en savoir plus sur l'inscription Android ainsi que sur l'inscription Android automatisée, voir [Inscrire des appareils Android](/mem/intune/enrollment/android-enroll).

## <a name="macos-enrollment"></a>Inscription macOS DEP

L'inscription pour macOS peut être un sujet délicat pour de nombreuses organisations informatiques. À moins qu'une majorité de vos utilisateurs ne soient des utilisateurs de Mac, vous ne gérez peut-être pas ces types d'appareils dans une large mesure. Si vous avez un petit nombre d'utilisateurs de macOS, nous vous recommandons l'inscription Intune uniquement. Si vous avez un grand nombre d'utilisateurs de macOS, nous vous recommandons l'inscription Intune + Jamf.  
- Intune Only Enrollment – Ceci est pour la gestion de base des appareils macOS. Cela nécessitera un processus manuel tout comme la plupart des autres options d'inscription basées sur l'utilisateur. Mais si vous disposez d'un petit nombre d'appareils Mac, cela peut être plus facile que de mettre en place une infrastructure entièrement automatisée uniquement pour ces quelques utilisateurs. Avec l'inscription Intune uniquement, vous avez la possibilité de déployer des éléments tels que des certificats, des configurations de mot de passe et des applications. Vous pouvez également configurer des politiques de conformité et éclairer l'accès conditionnel ainsi que la possibilité d'appliquer le chiffrement et l'effacement des appareils. 
- Inscription à Intune et Jamf – Pour ceux qui recherchent la prise en charge la plus complète de la gestion Mac, avec Jamf + Intune pour l'accès conditionnel, nous avons une excellente solution qui combine les capacités étendues de gestion Mac de Jamf avec la conformité Intune pour activer l'accès conditionnel. Dans ce scénario, vous gérez toujours entièrement l'appareil avec Jamf tout en étant capable de prendre ces signaux de Jamf pour une sécurité accrue.

Pour en savoir plus sur l'inscription macOS, consultez [Configurer l'inscription pour les appareils macOS dans Intune](/mem/intune/enrollment/macOS-enroll).

## <a name="next-steps"></a>Prochaines étapes

Passez à l'étape [3. Configurez des stratégies de conformité pour les appareils avec Intune](manage-devices-with-intune-compliance-policies.md).

