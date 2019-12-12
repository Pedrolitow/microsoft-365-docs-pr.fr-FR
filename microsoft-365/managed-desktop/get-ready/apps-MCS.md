---
title: Utilisation de Microsoft Consulting Services
description: préparation et étapes à suivre pour utiliser MCS pour empaqueter vos applications
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation, applications, MCS, Packaging
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 4491504616eb4bb447f12d08dddb12c73c2a88ac
ms.sourcegitcommit: b65c80051e53d9be223f4769f4d42a39f5a07735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "39962621"
---
# <a name="working-with-microsoft-consulting-services"></a>Utilisation de Microsoft Consulting Services

Vous pouvez vous exercer avec Microsoft Consulting Services (MCS) pour obtenir les applications à utiliser avec le bureau géré Microsoft. Pour obtenir des informations exactes, collaborez avec votre représentant commercial pour contacter MCS et étendre votre projet d’empaquetage d’application spécifique.

## <a name="roles-and-responsibilities"></a>Rôles et responsabilités

Pour utiliser l’empaquetage d’applications MCS, **vous devez fournir les éléments**suivants :

- Fichiers du programme d’installation source (par exemple, Setup. exe ou. msi).
- Les instructions d’installation, spécifiant des détails sur la façon dont l’installation finale doit ressembler. Par exemple, un raccourci Bureau doit-il exister vers l’application ? Quelle doit être la visibilité de l’application ? L’application doit-elle se connecter à un serveur et, le cas échéant, laquelle ? Pour plus d’informations, consultez le [modèle de demande d’empaquetage d’application](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/app-packaging-template.docx).
- Vous devez effectuer vos propres tests d’acceptation pour vérifier que l’application fonctionne comme vous le souhaitez dans votre environnement.

**MCS se chargera des actions suivantes :**

- Vérifier si l’application est interdite ou restreinte dans l’environnement de bureau géré Microsoft.
- Test de l’installation, du démarrage et de la désinstallation de l’application pour garantir la compatibilité avec Windows 10. Si MCS identifie un problème de compatibilité, il remet l’application à l' [application de bureau pour garantir](https://docs.microsoft.com/fasttrack/win-10-desktop-app-assure) le programme de correction.
- Empaquetez l’application dans votre spécification, puis testez le déploiement de l’application à l’aide de Microsoft Intune.

## <a name="app-delivery-schedule"></a>Calendrier de remise d’application

Démarrez le processus d’empaquetage en téléchargeant les informations de l’application dans le portail de bureau géré Microsoft. L’équipe de Packaging examine les nouvelles soumissions tous les jeudis. Après la révision et l’empaquetage, les applications empaquetées sont fournies le vendredi suivant. Jusqu’à cinq applications par semaine peuvent être empaquetées pour démarrer, mais le service peut évoluer pour répondre à vos besoins.

![calendrier illustrant le flux d’applications sur un jeudi (21 dans cet exemple), la validation du contenu multimédia le lendemain, la mise en package le lundi suivant (le 25) et la remise de l’application le vendredi (29)](images/MCS-cal.png)

Vous serez informé une fois que l’application aura été livrée. À ce stade, vous disposez de 21 jours pour effectuer des tests d’acceptation et vous déconnecter du travail dans le portail de bureau géré Microsoft. Si vous rencontrez un problème avec l’application pendant le test d’acceptation, rejetez l’application dans le portail de bureau géré Microsoft et vous serez connecté par courrier électronique avec un gestionnaire de package MCS pour comprendre et résoudre le problème.

## <a name="testing-accounts-and-environment"></a>Test des comptes et de l’environnement

Pour que l’équipe de Packaging termine la migration vers Microsoft Intune, nous vous recommandons de fournir certaines autorisations :
 
-   Accès aux fonctionnalités de déploiement d’applications de Microsoft Intune pour le gestionnaire de package afin d’ajouter et d’affecter l’application 
-   Les groupes de test, les comptes d’utilisateur et les licences pour les logiciels d’empaquetage pour pouvoir tester les applications

MCS utilise ces autorisations pour effectuer les actions suivantes :
 
-   S’assurer que l’application fonctionne sur l’ordinateur virtuel configuré pour Microsoft Managed Desktop
-   Téléchargement de l’application vers Microsoft Intune pour le déploiement vers vos utilisateurs

Sans ces autorisations, il est possible que MCS se déplace vers l’avant, mais il ne pourra pas télécharger les applications dans votre environnement.


