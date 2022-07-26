---
title: Gérer les appareils mobiles pour les employés de première ligne
author: lanachin
ms.author: v-lanachin
ms.reviewer: mabolan
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
ms.localizationpriority: high
search.appverid: MET150
description: Obtenez une vue d’ensemble de la gestion des appareils mobiles pour les travailleurs de première ligne de votre organisation.
ms.collection: m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: e0da7bf29865520507d9355fe25115700c3d8e28
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66992136"
---
# <a name="manage-mobile-devices-for-frontline-workers"></a>Gérer les appareils mobiles pour les employés de première ligne

## <a name="overview"></a>Vue d’ensemble

Dans tous les secteurs d’activité, les employés de première ligne constituent une grande partie de la main-d’œuvre. Les rôles de l’employé de première ligne incluent les associés de vente au détail, les ouvriers d’usine, les techniciens de terrain et de service, le personnel de santé, et bien plus encore.

Étant donné que la main-d’œuvre est en grande partie mobile et souvent basée sur des équipes, la gestion des appareils utilisés par les travailleurs de première ligne est essentielle. Voici certaines des questions que vous pouvez vous poser :

- Les travailleurs utilisent-ils des appareils appartenant à l’entreprise ou leurs propres appareils personnels ?
- Les appareils appartenant à l’entreprise sont-ils partagés entre les travailleurs ou attribués à un individu ?
- Les travailleurs ramènent-ils des appareils à la maison ou les laissent-ils sur le lieu de travail ?

Il est important de définir une base de référence sécurisée et conforme pour gérer les appareils de votre personnel, qu’il s’agisse d’appareils partagés ou de leurs propres appareils. Cet article vous donne une vue d’ensemble des scénarios d’appareils de travailleur de première ligne et des fonctionnalités de gestion courantes pour aider à autonomiser votre personnel tout en protégeant les données de l’entreprise.

## <a name="my-staff"></a>Mon personnel

Avec la fonctionnalité [Mon personnel](/azure/active-directory/roles/my-staff-configure) dans Azure Active Directory (Azure AD), vous pouvez déléguer des tâches courantes de gestion des utilisateurs aux gestionnaires de première ligne via le portail Mon personnel. Les responsables de première ligne peuvent effectuer des réinitialisations de mot de passe ou gérer des numéros de téléphone pour les employés de première ligne directement à partir du magasin ou de l’usine, sans avoir à acheminer les demandes vers le support technique, les opérations ou le service informatique.

Mon personnel permet également aux responsables de première ligne d’inscrire les numéros de téléphone des membres de leur équipe pour la connexion par SMS. Si [l’authentification par SMS](/azure/active-directory/authentication/howto-authentication-sms-signin) est activée dans votre organisation, les employés de première ligne peuvent se connecter à Teams et à d’autres applications en utilisant uniquement leurs numéros de téléphone et un code secret unique envoyé par SMS. Cela rend la connexion pour les travailleurs de première ligne simple, sécurisée et rapide.

## <a name="shared-devices"></a>Appareils partagés

De nombreux travailleurs de première ligne utilisent des appareils mobiles partagés pour travailler. Les appareils partagés sont des appareils appartenant à l’entreprise qui sont partagés entre les employés à travers des tâches, des équipes ou des emplacements.

Voici un exemple de scénario classique. Une organisation dispose d’un pool d’appareils dans les berceaux de recharge à partager entre tous les employés. Au début d’un quart de travail, un employé récupère un appareil du pool et se connecte à Teams et à d’autres applications métier essentielles à son rôle. À la fin de leur quart de travail, ils se déconnectent et retournent l’appareil au pool. Même au sein d’un même quart de travail, un travailleur peut retourner un appareil lorsqu’il termine une tâche ou qu’il expire pour le déjeuner, puis en prendre un autre lorsqu’il revient en arrière.

Les appareils partagés présentent des défis de sécurité uniques. Par exemple, les employés peuvent avoir accès à des données d’entreprise ou de client qui ne doivent pas être accessibles à d’autres personnes sur le même appareil.

Cette section fournit une vue d’ensemble des fonctionnalités disponibles pour gérer les appareils partagés pour les travailleurs de première ligne.

### <a name="shared-device-mode"></a>Mode d’appareil partagé

[Mode appareil partagé](/azure/active-directory/develop/msal-shared-devices) est une fonctionnalité d’Azure AD qui vous permet de configurer les appareils à partager par les employés. Cette fonctionnalité permet l’authentification unique (SSO) et la déconnexion à l’échelle de l’appareil pour Microsoft Teams et toutes les autres applications qui prennent en charge le mode d’appareil partagé. Vous pouvez intégrer cette fonctionnalité dans vos applications métier à l’aide de la bibliothèque d’authentification Microsoft (MSAL).

Voici comment fonctionne le mode d’appareil partagé, en utilisant Teams comme exemple. Lorsqu’un employé se connecte à Teams au début de son quart de travail, il est automatiquement connecté à toutes les autres applications qui prennent en charge le mode d’appareil partagé sur l’appareil. À la fin de leur quart de travail, lorsqu’ils se déconnectent de Teams, ils sont déconnectés globalement de toutes les autres applications qui prennent en charge le mode d’appareil partagé. Après la déconnexion, les données de l’employé et de l’entreprise dans Teams (y compris les applications hébergées dans celui-ci) et dans toutes les autres applications qui prennent en charge le mode d’appareil partagé ne sont plus accessibles. L’appareil est prêt pour le prochain employé et peut être remis en toute sécurité.

Vous utilisez une solution de Gestion des périphériques mobiles (GPM) comme Microsoft Intune dans Microsoft Endpoint Manager pour préparer un appareil à partager en installant l’[application Microsoft Authenticator](https://support.microsoft.com/account-billing/how-to-use-the-microsoft-authenticator-app-9783c865-0308-42fb-a519-8cf666fe0acc) et en activant le mode partagé. Teams et toutes les autres applications qui prennent en charge le mode d’appareil partagé utilisent le paramètre de mode partagé pour gérer les utilisateurs sur l’appareil. La solution GPM que vous utilisez doit également effectuer un nettoyage de l’appareil lors de la déconnexion.

Le mode d’appareil partagé est actuellement pris en charge sur les appareils Android. Voici quelques ressources pour vous aider à commencer.

#### <a name="enroll-android-devices-into-shared-device-mode"></a>Inscrire des appareils Android en mode d’appareil partagé

Pour gérer et inscrire des appareils Android en mode d’appareil partagé à l’aide de Intune, les appareils doivent exécuter Android OS version 8.0 ou ultérieure et disposer d’une connectivité Google Mobile Services (GMS). Pour en savoir plus, reportez-vous à la rubrique :

- [Configurer l’inscription à Intune pour les appareils Android Entreprise dédiés](/mem/intune/enrollment/android-kiosk-enroll)
- [Inscrire des appareils Android Enterprise dédiés en mode d’appareil partagé Azure AD](https://techcommunity.microsoft.com/t5/intune-customer-success/enroll-android-enterprise-dedicated-devices-into-azure-ad-shared/ba-p/1820093)

Vous pouvez également choisir de déployer l'application Microsoft Managed Home Screen pour personnaliser l'expérience des utilisateurs sur leurs appareils Android dédiés inscrits à Intune. L'écran d'accueil géré sert de lanceur pour d'autres applications approuvées qui s'exécutent par-dessus, et vous permet de personnaliser les appareils et de restreindre l'accès des employés. Par exemple, vous pouvez définir comment les applications apparaissent sur l'écran d'accueil, ajouter le logo de votre entreprise, définir un papier peint personnalisé et permettre aux employés de définir un code confidentiel de session. Vous pouvez même configurer la déconnexion pour qu'elle se produise automatiquement après une période d'inactivité déterminée.  Pour en savoir plus, reportez-vous à la rubrique :

- [Configurer l’application Microsoft Managed Home Screen pour Android Enterprise](/mem/intune/apps/app-configuration-managed-home-screen-app)
- [Comment configurer Microsoft Managed Home Screen sur des appareils dédiés en mode plein écran multi-application](https://techcommunity.microsoft.com/t5/intune-customer-success/how-to-setup-microsoft-managed-home-screen-on-dedicated-devices/ba-p/1388060)

#### <a name="for-developers-creating-apps-for-shared-device-mode"></a>Pour les développeurs qui créent des applications pour le mode d’appareil partagé

Si vous êtes développeur, consultez les ressources suivantes pour plus d’informations sur l’intégration de votre application au mode d’appareil partagé :

- [Mode d’appareil partagé pour les appareils Android](/azure/active-directory/develop/msal-android-shared-devices)
- [Mode d’appareil partagé pour les appareils iOS](/azure/active-directory/develop/msal-ios-shared-devices)

## <a name="personal-devices-byod"></a>Appareils personnels (BYOD)

Certaines organisations utilisent un modèle BYOD (bring-your-own-device) dans lequel les employés de première ligne utilisent leurs propres appareils mobiles pour accéder à Teams et à d’autres applications métier. Voici une vue d’ensemble de certaines façons de gérer l’accès et la conformité sur les appareils personnels.

### <a name="enroll-android-and-ios-personal-devices"></a>Inscrire des appareils personnels Android et iOS

Outre les appareils appartenant à votre entreprise, vous pouvez [inscrire](/mem/intune/enrollment/device-enrollment) les appareils personnels des utilisateurs dans la gestion dans Intune. Pour l’inscription BYOD, vous ajoutez des utilisateurs d’appareils dans le Centre d’administration Microsoft Endpoint Manager, configurez leur expérience d’inscription et configurez des stratégies Intune. Les utilisateurs s’inscrivent eux-mêmes dans l’application Portail d'entreprise Intune installée sur leur appareil.

Dans certains cas, les utilisateurs peuvent être réticents à inscrire leurs appareils personnels dans la gestion. Si l’inscription des appareils n’est pas une option, vous pouvez choisir une approche de gestion des applications mobiles (GAM) et utiliser des [stratégies de protection des applications](/mem/intune/apps/app-protection-policies) pour gérer les applications qui contiennent des données d’entreprise. Par exemple, vous pouvez appliquer des stratégies de protection des applications aux applications mobiles Teams et Office pour empêcher la copie des données d’entreprise vers des applications personnelles sur l’appareil.

Pour plus d’informations, consultez [« Appareils personnels et appareils appartenant à l’organisation » dans le guide de planification Intune](/mem/intune/fundamentals/intune-planning-guide#personal-devices-vs-organization-owned-devices) et les [conseils de déploiement : Inscrire des appareils dans Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment).

### <a name="off-shift-access-controls-in-teams"></a>Contrôles d’accès hors décalage dans Teams

Les contrôles d’accès hors décalage vous aident à limiter l’accès à Teams lorsque les employés sont hors équipe. Avec cette fonctionnalité, vous pouvez définir Teams pour afficher un message lorsque les employés accèdent à l’application en dehors des heures de travail. Les travailleurs de première ligne doivent cliquer sur J’accepte pour accepter le message avant de pouvoir utiliser Teams.

Le message par défaut informe l’employé qu’il ne sera pas payé pour le temps passé sur Teams en dehors des heures de travail. Vous pouvez utiliser le message par défaut, choisir un message prédéfini ou afficher le vôtre. Cette fonctionnalité permet de s’assurer que les employés ne travaillent pas involontairement lorsqu’ils ne travaillent pas en équipe et aide à se conformer aux réglementations du travail.

Pour plus d’informations, consultez [L’accès hors équipe à Teams](manage-shift-based-access-flw.md#off-shift-access-to-teams).

## <a name="related-articles"></a>Articles connexes

- [Gestion des travailleurs de première ligne](/azure/active-directory/fundamentals/frontline-worker-management)
