---
title: Utilisation de Microsoft Consulting Services
description: Préparation et étapes à suivre pour travailler avec MCS afin de mettre en package vos applications
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: db48122ea5551fe3e9f8cd676785bbd3eef81d0b
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59163817"
---
# <a name="working-with-microsoft-consulting-services"></a>Utilisation de Microsoft Consulting Services

Vous pouvez interagir avec Microsoft Consulting Services (MCS) pour obtenir vos applications empaquetées pour une utilisation avec Microsoft Manged Desktop. Pour plus d’informations, contactez votre représentant de compte pour contacter MCS et déterminer l’étendue de votre projet d’empaquetage d’application spécifique.

## <a name="roles-and-responsibilities"></a>Rôles et responsabilités

Pour travailler avec l’empaquetage d’application MCS, **vous devez fournir les éléments ci-après**:

- Fichiers du programme d’installation source (par exemple, setup.exe ou .msi).
- Instructions d’installation spécifiant l’apparence de l’installation finale. Par exemple, doit-il y avoir un raccourci bureau vers l’application ? Quelle doit être la visibilité de l’application ? L’application doit-elle se connecter à un serveur et, si c’est le cas, laquelle ? Pour plus d’informations, voir le modèle de demande [d’empaquetage d’application.](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/app-packaging-template.docx)
- Vous devez effectuer vos propres tests d’acceptation pour vérifier que l’application fonctionne comme vous le souhaitez dans votre environnement.

**MCS s’occupe des actions ci-après :**

- Vérification de l’interdiction ou de la restriction de l’application dans l Microsoft Manged Desktop de l’application.
- Test de l’installation, du démarrage et de la désinstallation de l’application pour garantir la compatibilité avec Windows 10. Si MCS découvre un problème de compatibilité, il va remettre l’application au programme [App Assure](/fasttrack/products-and-capabilities#app-assure) pour correction.
- Empaquetage de l’application selon vos spécifications, puis test du déploiement de l’application à l’aide Microsoft Intune.

## <a name="app-delivery-schedule"></a>Planification de remise des applications

Démarrez le processus d’empaquetage en téléchargeant les informations de l’application sur Microsoft Manged Desktop portail. L’équipe de packaging examine les nouvelles soumissions tous les jeudis. Après révision et empaquetage, les applications empaquetées sont livrées le vendredi suivant. Jusqu’à cinq applications par semaine peuvent être empaquetées pour démarrer, mais le service peut être mis à l’échelle en fonction de vos besoins.

![calendrier montrant l’entrée entrante de l’application un jeudi (le 21 dans cet exemple), la validation multimédia le jour suivant, l’empaquetage le lundi suivant (le 25) et la remise de l’application le vendredi suivant (le 29).](../../media/MCS-cal.png)

Une fois l’application livrée, vous en serez informé. À ce stade, vous avez 21 jours pour effectuer des tests d’acceptation et approuver le travail dans Microsoft Manged Desktop portail. Si vous découvrez un problème avec l’application lors de vos tests d’acceptation, rejetez l’application dans le portail Microsoft Manged Desktop et vous serez connecté par courrier électronique à un programme de package MCS pour comprendre et résoudre le problème.

## <a name="testing-accounts-and-environment"></a>Test des comptes et de l’environnement

Pour que l’équipe de packaging termine la migration vers Microsoft Intune, nous vous recommandons de fournir certaines autorisations :

- Accès aux fonctionnalités Microsoft Intune déploiement d’application du programme de package pour ajouter et affecter l’application
- Tester les groupes, les comptes d’utilisateur et les licences des packageurs pour pouvoir tester les applications

MCS utilisera ces autorisations pour effectuer les actions suivantes :

- S’assurer que l’application fonctionne sur une machine virtuelle configurée pour Microsoft Manged Desktop
- Téléchargement de l’application vers Microsoft Intune pour le déploiement vers vos utilisateurs

Sans ces autorisations, mcS peut avancer, mais il ne pourra pas télécharger les applications vers votre environnement.
