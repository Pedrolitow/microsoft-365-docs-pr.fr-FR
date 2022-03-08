---
title: Méthodes d’inscription d’appareil dans Microsoft Manged Desktop
description: Informations sur les méthodes d’inscription de l’appareil Microsoft Manged Desktop
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 7d0cabc0a9d11d337e5adabde568bd2a56ceca86
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319125"
---
# <a name="device-registration-methods"></a>Méthodes d’inscription des appareils

Pour que Microsoft puisse gérer vos appareils dans Microsoft Manged Desktop, vous devez avoir des appareils enregistrés auprès du service.

## <a name="registration-process"></a>Processus d’inscription

Microsoft Manged Desktop est alimenté par le service Autopilot Windows pour le flux de travail d’inscription de l’appareil. L’inscription réussie de l’appareil nécessite un processus en deux étapes :

1. L’identité matérielle unique de l’appareil, appelée hachage matériel, est capturée et téléchargée vers le service Autopilot.
1. L’appareil est associé à un ID Azure Active Directory client.

Dans l’idéal, les deux étapes sont effectuées par l’OEM, le revendeur ou le distributeur sur lequel les appareils ont été achetés. Un OEM, ou un autre fournisseur d’appareils, utilise le processus d’autorisation d’inscription pour effectuer l’inscription de l’appareil en votre nom.

## <a name="registration-methods"></a>Méthodes d’inscription

L’inscription peut également être effectuée au sein de votre organisation en collectant l’identité matérielle à partir d’appareils nouveaux ou existants et en la téléchargeant manuellement. Vous trouverez ci-dessous les méthodes d’inscription des Microsoft Manged Desktop prend en charge :

- Inscription OEM
    - [Utilisation du portail partenaire](partner-registration.md#register-devices-using-the-partner-center)
    - [Utilisation des API OEM](partner-registration.md#register-devices-by-using-the-oem-api)
- [Inscription manuelle](manual-registration.md)
- [Inscription manuelle pour les appareils existants](manual-registration-existing-devices.md)

## <a name="recommended-resources"></a>Ressources recommandées

- [Vue d’ensemble de Windows Autopilot](/mem/autopilot/windows-autopilot)
- [Windows vue d’ensemble de l’inscription Autopilot](/mem/autopilot/registration-overview)

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de mise en Microsoft Manged Desktop

1. Accéder au[Portail d’administration](access-admin-portal.md).
1. [Ajouter et vérifier des contacts d’administrateur dans le portail d’administration](add-admin-contacts.md).
1. [Ajuster les paramètres après l’inscription](conditional-access.md).
1. Déployez et affectez le[Portail d’entreprise Intune](company-portal.md).
1. [Attribuer des licences](assign-licenses.md).
1. [Déployer des applications](deploy-apps.md).
1. [Préparez les appareils](prepare-devices.md).
1. Configurez l’[Expérience de première exécution avec Autopilot et la page d’état d’inscription](esp-first-run.md).
1. [Activer les fonctionnalités de support utilisateur](enable-support.md).
1. [Préparez vos utilisateurs à utiliser des appareils](get-started-devices.md).
1. [Démarrage avec le contrôle d’application](get-started-app-control.md).
