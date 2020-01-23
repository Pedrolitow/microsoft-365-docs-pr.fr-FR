---
title: Configuration d’un connecteur pour l’archivage des données Twitter
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: Les administrateurs peuvent configurer un connecteur natif pour importer des données Twitter dans Microsoft 365. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer la gouvernance des données tierces de votre organisation.
ms.openlocfilehash: cba4509c9752fbfefd8aadfdeac679aa45159711
ms.sourcegitcommit: 9b390881fe661deb0568b4b86a5a9094f3c795f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2020
ms.locfileid: "41269375"
---
# <a name="set-up-a-connector-to-archive-twitter-data"></a>Configuration d’un connecteur pour l’archivage des données Twitter

Utilisez un connecteur dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir de Twitter vers Microsoft 365. Une fois que vous avez configuré et configuré le connecteur, il se connecte au compte Twitter de votre organisation (de manière planifiée), convertit le contenu d’un élément en un format de message électronique, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois les données Twitter importées, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, la recherche de contenu, l’archivage inaltérable, l’audit et les stratégies de rétention 365 sur les données Twitter. Par exemple, lorsqu’une boîte aux lettres est placée en conservation pour litige ou affectée à une stratégie de rétention, les données Twitter sont conservées. Vous pouvez rechercher des données tierces à l’aide de la recherche de contenu ou associer la boîte aux lettres dans laquelle les données Twitter sont stockées avec un dépositaire dans un cas avancé de découverte électronique. L’utilisation d’un connecteur pour importer et archiver des données Twitter dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

Une fois les données Twitter importées, vous pouvez appliquer les fonctionnalités de conformité d’Office 365 telles que la conservation pour litige, la recherche de contenu, l’archivage inaltérable, l’audit, la conformité de la communication et les stratégies de rétention d’Office 365 aux données stockées dans la boîte aux lettres. Par exemple, vous pouvez rechercher des données Twitter à l’aide de la recherche de contenu ou associer la boîte aux lettres dans laquelle les données sont stockées avec un dépositaire dans un cas avancé de découverte électronique. L’utilisation d’un connecteur pour importer et archiver des données Twitter dans Office 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="prerequisites-for-setting-up-a-connector-for-twitter"></a>Conditions préalables à la configuration d’un connecteur pour Twitter

Avant de pouvoir installer et configurer un connecteur dans le centre de conformité Microsoft 365, vous devez remplir les conditions préalables suivantes pour importer et archiver des données à partir du compte Twitter de votre organisation.

- Vous avez besoin d’un compte Twitter pour votre organisation ; vous devez vous connecter à ce compte lors de la configuration du connecteur.

- Votre organisation doit disposer d’un abonnement Azure valide. Si vous n’avez pas d’abonnement Azure existant, vous pouvez vous inscrire à l’une de ces options :

    - [Inscrivez-vous pour obtenir un abonnement Azure gratuit d’un an](https://azure.microsoft.com/free) 

    - [S’inscrire pour un abonnement Azure avec paiement en tant que](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > L' [abonnement Azure Active Directory gratuit](use-your-free-azure-ad-subscription-in-office-365.md) qui est inclus avec votre abonnement Office 365 ne prend pas en charge les connecteurs dans le centre de sécurité & Compliance Center.

- Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Pour accepter cette demande, accédez à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent), connectez-vous à l’aide des informations d’identification d’un administrateur général Office 365, puis acceptez la demande.

- L’utilisateur qui configure le connecteur Twitter dans le centre de conformité Microsoft 365 (à l’étape 5) doit se voir attribuer le rôle importation/exportation de boîte aux lettres dans Exchange Online. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : créer une application dans Azure Active Directory

La première étape consiste à inscrire une nouvelle application dans Azure Active Directory (AAD). Cette application correspond à la ressource Web App que vous implémentez à l’étape 2 pour le connecteur Twitter.

Pour obtenir des instructions pas à pas, consultez la rubrique [créer une application dans Azure Active Directory](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).

Lors de l’exécution de cette étape (en suivant les instructions pas à pas), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs seront utilisées dans les étapes ultérieures du processus de déploiement.

- ID d’application AAD
- ID de locataire

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a>Étape 2 : déployer le service Web de connecteur depuis le référentiel GitHub vers votre compte Azure

L’étape suivante consiste à déployer le code source pour l’application de connecteur Twitter qui utilisera l’API Twitter pour se connecter à votre compte Twitter et extraire les données afin de pouvoir les importer dans Microsoft 365. Le connecteur Twitter que vous déployez pour votre organisation télécharge les éléments du compte Twitter de votre organisation vers l’emplacement de stockage Azure créé lors de cette étape. Une fois que vous avez créé un connecteur Twitter dans le centre de conformité Microsoft 365 (à l’étape 5), le service d’importation d’Office 365 copie les données Twitter de l’emplacement de stockage Azure vers une boîte aux lettres dans Microsoft 365. Comme indiqué précédemment dans la section [conditions préalables](#prerequisites-for-setting-up-a-connector-for-twitter) , vous devez disposer d’un abonnement Azure valide pour créer un compte de stockage Azure.

Le connecteur Twitter que vous déployez pour votre organisation télécharge les éléments à partir de Twitter vers l’emplacement de stockage Azure que vous créez au cours de cette étape. Une fois que vous avez créé un connecteur personnalisé dans le centre de sécurité & conformité (à l’étape 7), le service d’importation Office 365 copie les données Twitter à partir de l’emplacement de stockage Azure vers une boîte aux lettres dans Office 365. Comme indiqué précédemment dans la section [conditions préalables](#prerequisites-for-setting-up-a-connector-for-twitter) , vous devez disposer d’un abonnement Azure valide pour créer un compte de stockage Azure.

Pour déployer le code source pour l’application de connecteur Twitter,

1. Accédez à [ce site github](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet).
2. Cliquez sur le bouton **déployer vers Azure**

Pour obtenir des instructions pas à pas, consultez [la rubrique déployer le service Web connecteur depuis Github vers votre compte Azure](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

Pendant que vous suivez les instructions pas à pas pour effectuer cette étape, vous fournissez les informations suivantes

- APISecretKey : vous créez cette clé secrète lors de l’exécution de cette étape. Elle est utilisée à l’étape 5.
- tenantId : ID de client de votre organisation Microsoft 365 que vous avez copié après avoir créé l’application Twitter dans Azure Active Directory à l’étape 1.

Une fois cette étape terminée, veillez à copier l’URL du service d’application ( https://twitterconnector.azurewebsites.net)par exemple,. Vous devez utiliser cette URL pour effectuer l’étape 3, étape 4, et étape 5).

## <a name="step-3-create-developer-app-on-twitter"></a>Étape 3 : créer une application de développeur sur Twitter

L’étape suivante consiste à créer et configurer une application de développeur sur Twitter. Le connecteur personnalisé que vous créez à l’étape 7 utilise l’application Twitter pour interagir avec l’API Twitter afin d’obtenir des données à partir du compte Twitter de votre organisation.

Pour obtenir des instructions pas à pas, voir [Create the Twitter App](deploy-twitter-connector.md#step-3-create-the-twitter-app).

Lors de l’exécution de cette étape (en suivant les instructions pas à pas), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs seront utilisées pour configurer l’application connecteur Twitter à l’étape 4.

- Clé de l’API Twitter
- Clé secrète de l’API Twitter
- Jeton d’accès Twitter
- Jeton d’accès Twitter secret

## <a name="step-4-configure-the-twitter-connector-app"></a>Étape 4 : configurer l’application de connecteur Twitter

L’étape suivante consiste à ajouter des paramètres de configuration à l’application de connecteur Twitter que vous avez déployée à l’étape 2. Pour ce faire, accédez à la page d’accueil de votre application de connecteur et configurez-la.

Pour obtenir des instructions pas à pas, consultez [la rubrique Configure the Connector Web App](deploy-twitter-connector.md#step-4-configure-the-connector-web-app).

Lors de l’exécution de cette étape (en suivant les instructions pas à pas), vous devez fournir les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes précédentes) :

- Clé de l’API Twitter (obtenue à l’étape 3)
- Clé secrète de l’API Twitter (obtenue à l’étape 3)
- Jeton d’accès Twitter (obtenu à l’étape 3)
- Jeton d’accès Twitter secret (obtenu à l’étape 3)
- ID d’application Azure Active Directory (l’ID d’application AAD obtenu à l’étape 1)
- Clé secrète de l’application Azure Active Directory (la clé secrète de l’application AAD obtenue à l’étape 1)

## <a name="step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center"></a>Étape 5 : configurer un connecteur Twitter dans le centre de conformité Microsoft 365

La dernière étape consiste à configurer le connecteur Twitter dans le centre de conformité Microsoft 365 qui importe les données du compte Twitter de votre organisation vers une boîte aux lettres spécifiée dans Microsoft 365. Une fois cette étape terminée, le service d’importation Office 365 commence à importer les données du compte Twitter de votre organisation vers Microsoft 365.

Pour obtenir des instructions pas à pas, reportez-vous à [la rubrique Configurer un connecteur Twitter dans le centre de conformité Microsoft 365](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center). 

Lors de l’exécution de cette étape (en suivant les instructions pas à pas), vous devez fournir les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes).

- URL du service d’application Azure (obtenue à l’étape 2 ; `https://twitterconnector.azurewebsites.net`par exemple,)
- APISecretKey (que vous avez créé à l’étape 2)
