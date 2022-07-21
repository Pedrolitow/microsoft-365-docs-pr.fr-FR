---
title: Configurer les paramètres de confidentialité dans le Tableau blanc Microsoft
ms.author: v-jdeweese
author: johnddeweese
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Découvrez la conformité et comment configurer les paramètres de confidentialité dans le Tableau blanc Microsoft.
ms.openlocfilehash: 7f5026115b1d15b05dcf5dbb57293b22bf573c61
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66942469"
---
# <a name="configure-privacy-settings-in-microsoft-whiteboard"></a>Configurer les paramètres de confidentialité dans le Tableau blanc Microsoft

>[!NOTE]
> Si vous ou vos utilisateurs souhaitez en savoir plus sur les paramètres de confidentialité par défaut, les expériences connectées facultatives et la façon dont les données de diagnostic sont collectées, dirigez-les vers la [confidentialité et la conformité du Tableau blanc Microsoft](https://support.microsoft.com/office/privacy-and-compliance-ed9f0de9-71be-44c2-837d-e0f448660be1).

Si vous êtes l’administrateur du Tableau blanc Microsoft pour votre organisation, vous pouvez contrôler les éléments suivants :

- Quel niveau de données de diagnostic est collecté et envoyé à Microsoft à propos du logiciel client Tableau blanc s’exécutant sur l’appareil de l’utilisateur.

- Indique si les expériences connectées facultatives dans le Tableau blanc sont disponibles pour vos utilisateurs.

Pour configurer le niveau des données de diagnostic, connectez-vous au [Centre d'administration Microsoft 365](/microsoft-365/admin/admin-overview/admin-center-overview) avec votre compte d’administrateur. À partir de la page d’accueil du centre d’administration, accédez à **Afficher tous les paramètres > > paramètres de l’organisation > tableau blanc**.

Pour configurer la disponibilité d’expériences connectées facultatives, utilisez le service de stratégie [cloud Office](/deployoffice/admincenter/overview-office-cloud-policy-service) dans le [centre d’administration Microsoft 365 Apps](https://config.office.com). Connectez-vous avec votre compte d’administrateur et accédez à **Personnalisation > Gestion des stratégies**. La stratégie que vous souhaitez configurer est nommée : **Autoriser l’utilisation d’expériences connectées facultatives supplémentaires dans Office**.

## <a name="diagnostic-data-setting-for-your-organization"></a>Paramètre de données de diagnostic pour votre organisation

Vous pouvez choisir le niveau de données de diagnostic collectées et envoyées à Microsoft à propos du logiciel client Tableau blanc s’exécutant sur les appareils de votre organisation. Les données de diagnostic facultatives sont envoyées à Microsoft, sauf si vous modifiez le paramètre dans le Centre d'administration Microsoft 365. Si vous choisissez d’envoyer des données de diagnostic facultatives, les données de diagnostic requises sont également incluses.

En plus de **Obligatoire** ou **Facultatif**, il existe également le choix ni l’un **ni l’autre**. Si vous choisissez cette option, aucune donnée de diagnostic sur le logiciel client Tableau blanc en cours d’exécution sur l’appareil de l’utilisateur n’est envoyée à Microsoft. Toutefois, cette option limite considérablement la capacité de Microsoft à détecter, diagnostiquer et corriger les problèmes que vos utilisateurs peuvent rencontrer lors de l’utilisation du Tableau blanc.

Vos utilisateurs ne pourront pas modifier le niveau de données de diagnostic de leurs appareils s’ils sont connectés au Tableau blanc avec leurs informations d’identification d’organisation (parfois appelées compte professionnel ou scolaire). Toutefois, s’ils sont connectés au Tableau blanc avec un compte Microsoft, par exemple une adresse e-mail outlook.com personnelle, ils peuvent modifier le niveau de données de diagnostic sur leurs appareils en accédant à **Paramètres > Confidentialité et sécurité**.

## <a name="optional-connected-experiences-setting-for-your-organization"></a>Paramètre d’expériences connectées facultatif pour votre organisation

Vous pouvez choisir de mettre des expériences connectées facultatives dans le Tableau blanc à la disposition de vos utilisateurs. Ces expériences connectées seront disponibles pour vos utilisateurs, sauf si vous modifiez le paramètre dans le Centre d'administration Microsoft 365. 

Ces expériences connectés sont différentes car elles ne sont pas couvertes par le contrat commerciale de votre organisation avec Microsoft. Les expériences connectées facultatives supplémentaires offertes par Microsoft directement à vos utilisateurs sont régies par le [Contrat de services Microsoft](https://www.microsoft.com/servicesagreement) au lieu des [Conditions d'utilisation des services en ligne](https://www.microsoft.com/licensing/product-licensing/products).

Même si vous choisissez de mettre ces expériences connectées facultatives à la disposition de vos utilisateurs, vos utilisateurs ont la possibilité de les désactiver en tant que groupe en accédant à **Paramètres > Confidentialité et sécurité**. Vos utilisateurs n’ont ce choix que s’ils sont connectés au Tableau blanc avec leurs informations d’identification organisationnelles (parfois appelées compte professionnel ou scolaire), et non s’ils sont connectés avec un compte Microsoft, tel qu’une adresse e-mail outlook.com personnelle.

## <a name="required-diagnostic-data-events-collected-by-whiteboard"></a>Événements de données de diagnostic requis collectés par tableau blanc

Voici les événements de données de diagnostic requis collectés par le Tableau blanc, y compris une liste de champs de données dans chaque événement.

**Intentional.CanvasObject.Ink.DrawFirstStroke**

Les entrées manuscrites collectées pour la première fois sont ajoutées à un tableau dans le Tableau blanc Microsoft. Ces informations sont essentielles pour intercepter les erreurs associées à l’ajout d’entrée manuscrite à une carte. Microsoft utilise ces données pour diagnostiquer le problème afin de garantir que Microsoft Whiteboard s’exécute comme prévu.

- **Action** : type de trait d’encre
- **Source** : méthode d’entrée pour le trait d’encre

**Intentional.SurfSide.ActivationProtocol.LoadFromUri**

Collecté chaque fois que Microsoft Whiteboard est lancé par un appel d’une autre application ou processus. Ces informations sont essentielles à intercepter si le tableau blanc ne se lance pas lorsqu’il est correctement appelé par une autre application ou processus. Microsoft utilise ces données pour diagnostiquer le problème afin de garantir que Microsoft Whiteboard s’exécute comme prévu.

- **ApplicationExecutionState** : état d’exécution de l’application lorsque le protocole d’activation se produit
- **IsSignedIn** : l’utilisateur est l’état de l’authentification
- **Type** : application ou processus qui lance le Tableau blanc

**Intentionnel.Whiteboard.Init.DisplayWhiteboard**

Collecté la première fois que Microsoft Whiteboard est réellement affiché sur un client par session. Ces informations sont essentielles pour détecter les problèmes de lancement. Microsoft utilise ces données pour diagnostiquer le problème afin de garantir que Microsoft Whiteboard s’exécute comme prévu.

- **IsPrelaunched** – État de prélancement
- **IsProtocolActivation** : type de lancement d’application

**Intentionnel.Whiteboard.Init.StartApp**

Collecté à chaque lancement de Microsoft Whiteboard après la fin de l’état précédent sans blocage. Ces informations sont essentielles pour détecter les problèmes de blocage. Microsoft utilise ces données pour diagnostiquer le problème afin de garantir que Microsoft Whiteboard s’exécute comme prévu.

- **Premier démarrage** : l’application pour la première fois a été lancée sur le client

**Intentionnel.Whiteboard.KeyCategory.UseCategory**

Collecté chaque fois qu’une fonctionnalité est utilisée pour la première fois (et la première fois uniquement) par utilisateur/session/tableau blanc dans le Tableau blanc Microsoft. Ces informations sont essentielles pour vous assurer que les catégories clés sont utilisées. Microsoft utilise ces données pour diagnostiquer le problème afin de garantir que Microsoft Whiteboard s’exécute comme prévu.

- **CategoryName** : nom de la catégorie de clé

**Intentionnel.Whiteboard.KeyFeature.UseFeature**

Collecté chaque fois qu’une fonctionnalité est utilisée pour la première fois (et la première fois uniquement) par utilisateur/session/tableau blanc dans le Tableau blanc Microsoft. Ces informations sont essentielles pour s’assurer que les fonctionnalités sont appelées et utilisées. Microsoft utilise ces données pour diagnostiquer le problème afin de garantir que Microsoft Whiteboard s’exécute comme prévu.

- **FeatureName** : nom de la fonctionnalité clé

**Intentionnel.Whiteboard.SafeBoot.StartApp**

Collecté chaque fois que Microsoft Whiteboard se lance après que l’état précédent s’est terminé par un plantage. Ces informations sont essentielles pour détecter les problèmes de blocage. Microsoft utilise ces données pour diagnostiquer le problème afin de garantir que Microsoft Whiteboard s’exécute comme prévu.

- **Premier démarrage** : l’application pour la première fois a été lancée sur le client

**Intentionnel.Whiteboard.Scrub.LoadSettings**

Collecté à chaque lancement de Microsoft Whiteboard. Ces informations sont essentielles pour intercepter les erreurs associées aux paramètres configurés par l’utilisateur. Microsoft utilise ces données pour diagnostiquer le problème afin de garantir que Microsoft Whiteboard s’exécute comme prévu.

- **ActivePen** : état du mode stylet
- **CollectFullTelemetryWithoutSignIn** : collection de données de télémétrie complète sans activation de connexion
- **DefaultWhiteboardBackgroundColor** : couleur d’arrière-plan du tableau par défaut
- **DefaultWhiteboardBackgroundPattern** : modèle d’arrière-plan de tableau par défaut
- **FlightStatus** : état du vol
- **InkToShape** : activation de l’entrée manuscrite vers la forme
- **InkToTable** : activation de l’entrée manuscrite dans la table
- **SignInEnabled** : activation de la connexion utilisateur
- **SharingWithoutSignInEnabled** : activation de la carte de partage
- **ToolbarLocation** : emplacement par défaut de la barre d’outils à l’écran
- **TeamSettingsSource** – Activation des paramètres Teams
