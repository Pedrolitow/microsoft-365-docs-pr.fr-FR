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
ms.openlocfilehash: 7a967f5e4b2678b55ed87f2eaa68590703c55805
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52840885"
---
# <a name="working-with-microsoft-consulting-services"></a>Utilisation de Microsoft Consulting Services

Vous pouvez interagir avec Microsoft Consulting Services (MCS) pour obtenir vos applications empaquetées pour une utilisation avec Bureau géré Microsoft. Pour plus d’informations, contactez votre représentant de compte pour contacter MCS et déterminer l’étendue de votre projet d’empaquetage d’application spécifique.

## <a name="roles-and-responsibilities"></a>Rôles et responsabilités

Pour travailler avec l’empaquetage d’application MCS, **vous devez fournir les éléments ci-après**:

- Fichiers du programme d’installation source (par exemple, setup.exe ou .msi).
- Instructions d’installation, spécifiant des détails sur l’apparence de l’installation finale. Par exemple, doit-il y avoir un raccourci bureau vers l’application ? Quelle doit être la visibilité de l’application ? L’application doit-elle se connecter à un serveur et, si c’est le cas, laquelle ? Pour plus d’informations, voir le modèle de demande [d’empaquetage d’application.](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/app-packaging-template.docx)
- Vous devez effectuer vos propres tests d’acceptation pour vérifier que l’application fonctionne comme vous le souhaitez dans votre environnement.

**MCS s’occupe des actions ci-après :**

- Vérifier si l’application est interdite ou restreinte dans l’environnement Bureau géré Microsoft web.
- Test de l’installation, du démarrage et de la désinstallation de l’application pour garantir la compatibilité avec Windows 10. Si MCS découvre un problème de compatibilité, il va remettre l’application au programme [App Assure](/fasttrack/products-and-capabilities#app-assure) pour correction.
- Empaquetage de l’application selon vos spécifications, puis test du déploiement de l’application à l’aide Microsoft Intune.

## <a name="app-delivery-schedule"></a>Planification de remise des applications

Démarrez le processus d’empaquetage en téléchargeant les informations de l’application sur Bureau géré Microsoft portail. L’équipe de packaging examine les nouvelles soumissions tous les jeudis. Après révision et empaquetage, les applications empaquetées sont livrées le vendredi suivant. Jusqu’à cinq applications par semaine peuvent être empaquetées pour démarrer, mais le service peut être mis à l’échelle en fonction de vos besoins.

![calendrier montrant l’entrée entrante de l’application un jeudi (le 21 dans cet exemple), la validation multimédia le jour suivant, l’empaquetage le lundi suivant (le 25) et la remise de l’application le vendredi suivant (le 29)](../../media/MCS-cal.png)

Une fois l’application livrée, vous en serez informé. À ce stade, vous avez 21 jours pour effectuer des tests d’acceptation et approuver le travail dans Bureau géré Microsoft portail. Si vous découvrez un problème avec l’application lors de vos tests d’acceptation, rejetez l’application dans le portail Bureau géré Microsoft et vous serez connecté par courrier électronique à un programme de package MCS pour comprendre et résoudre le problème.

## <a name="testing-accounts-and-environment"></a>Test des comptes et de l’environnement

Pour que l’équipe de packaging termine la migration vers Microsoft Intune, nous vous recommandons de fournir certaines autorisations :

- Accès aux fonctionnalités Microsoft Intune déploiement d’application du programme de package pour ajouter et affecter l’application
- Tester les groupes, les comptes d’utilisateur et les licences des packageurs pour pouvoir tester les applications

MCS utilisera ces autorisations pour effectuer les actions suivantes :

- S’assurer que l’application fonctionne sur une machine virtuelle configurée pour Bureau géré Microsoft
- Téléchargement de l’application vers Microsoft Intune déploiement à vos utilisateurs

Sans ces autorisations, mcS peut avancer, mais il ne pourra pas télécharger les applications vers votre environnement.
