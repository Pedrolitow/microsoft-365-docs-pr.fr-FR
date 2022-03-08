---
title: Configurer un connecteur pour archiver des données Twitter
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Découvrez comment les administrateurs peuvent configurer et utiliser un connecteur natif pour importer des données Twitter dans Microsoft 365.
ms.openlocfilehash: 959cdd49d229334f3129eb21505c4489d23ded4f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320632"
---
# <a name="set-up-a-microsoft-connector-to-archive-twitter-data-preview"></a>Configurer un connecteur Microsoft pour archiver les données Twitter (aperçu)

Utilisez un connecteur dans le Centre de conformité Microsoft 365 pour importer et archiver des données de Twitter vers Microsoft 365. Après avoir configuré et configuré le connecteur, il se connecte au compte Twitter de votre organisation (de manière programmée), convertit le contenu d’un élément au format de message électronique, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois les données Twitter importées, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu, l’archivage In-Place, l’audit et les stratégies de rétention Microsoft 365 aux données Twitter. Par exemple, lorsqu’une boîte aux lettres est placée en conservation pour litige ou affectée à une stratégie de rétention, les données Twitter sont conservées. Vous pouvez rechercher des données tierces à l’aide de la recherche de contenu ou associer la boîte aux lettres dans laquelle les données Twitter sont stockées à un dépositaire dans Advanced eDiscovery cas. L’utilisation d’un connecteur pour importer et archiver des données Twitter dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

Une fois les données Twitter importées, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu, l’archivage In-Place, l’audit, la conformité des communications et les stratégies de rétention Microsoft 365 aux données stockées dans la boîte aux lettres. Par exemple, vous pouvez rechercher des données Twitter à l’aide de la recherche de contenu ou associer la boîte aux lettres dans laquelle les données sont stockées à un dépositaire dans Advanced eDiscovery cas. L’utilisation d’un connecteur pour importer et archiver des données Twitter dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

Remplissez les conditions préalables suivantes avant de pouvoir configurer un connecteur dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir du compte Twitter de votre organisation.

- Vous avez besoin d’un compte Twitter pour votre organisation . vous devez vous connectez à ce compte lors de la configuration du connecteur.

- Votre organisation doit avoir un abonnement Azure valide. Si vous n’avez pas d’abonnement Azure existant, vous pouvez vous inscrire à l’une des options ci-après :

    - [S’inscrire à un abonnement Azure gratuit d’un an](https://azure.microsoft.com/free) 

    - [S’inscrire à un abonnement Azure de paiement par abonnement](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [L’abonnement Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md) gratuit inclus dans votre abonnement Microsoft 365 ne prend pas en charge les connecteurs dans le Centre de conformité Microsoft 365.

- Le connecteur Twitter peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 éléments Twitter par jour, aucun de ces éléments n’est importé dans Microsoft 365.

- L’utilisateur qui définit le connecteur Twitter dans le Centre de conformité Microsoft 365 (à l’étape 5) doit se voir attribuer le rôle d’administrateur du connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le Centre de conformité Microsoft 365. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et conformité » dans Autorisations dans le Centre de sécurité [& conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

La première étape consiste à inscrire une nouvelle application dans Azure Active Directory (AAD). Cette application correspond à la ressource d’application web que vous implémentez à l’étape 2 pour le connecteur Twitter.

Pour obtenir des instructions détaillées, voir [Créer une application dans Azure Active Directory](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).

À la fin de cette étape (en suivant les instructions pas à pas), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs seront utilisées dans les étapes ultérieures du processus de déploiement.

- AAD’application

- AAD’application secrète

- ID de client

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a>Étape 2 : Déployer le service web connecteur à partir GitHub référentiel vers votre compte Azure

L’étape suivante consiste à déployer le code source pour l’application connecteur Twitter qui utilisera l’API Twitter pour se connecter à votre compte Twitter et extraire des données afin de pouvoir les importer dans Microsoft 365. Le connecteur Twitter que vous déployez pour votre organisation charge les éléments à partir du compte Twitter de votre organisation vers l’emplacement stockage Azure qui est créé au cours de cette étape. Après avoir créé un connecteur Twitter dans le Centre de conformité Microsoft 365 (à l’étape 5), le service d’importation Microsoft 365 copie les données Twitter de l’emplacement stockage Azure vers une boîte aux lettres dans Microsoft 365. Comme expliqué précédemment dans [la section Avant](#before-you-set-up-a-connector) de configurer un connecteur, vous devez avoir un abonnement Azure valide pour créer un compte stockage Azure client.

Pour déployer le code source de l’application connecteur Twitter :

1. Go to [this GitHub site](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet).

2. Cliquez **sur Déployer sur Azure**.

Pour obtenir des instructions détaillées, voir Déployer le service web de connecteur à partir de [GitHub votre compte Azure](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

Bien que vous suiviez les instructions pas à pas pour effectuer cette étape, vous fournissez les informations suivantes :

- APISecretKey : vous créez cette clé secrète à la fin de cette étape. Il est utilisé à l’étape 5.

- tenantId : ID de locataire de votre organisation Microsoft 365 que vous avez copiée après la création de l’application Twitter à l Azure Active Directory étape 1.

Après avoir effectué cette étape, assurez-vous de copier l’URL du service d’application (par exemple, `https://twitterconnector.azurewebsites.net`). Vous devez utiliser cette URL pour effectuer les étapes 3, 4 et 5.

## <a name="step-3-create-developer-app-on-twitter"></a>Étape 3 : Créer une application de développeur sur Twitter

L’étape suivante consiste à créer et configurer une application de développeur sur Twitter. Le connecteur personnalisé que vous créez à l’étape 7 utilise l’application Twitter pour interagir avec l’API Twitter afin d’obtenir des données à partir du compte Twitter de votre organisation.

Pour obtenir des instructions détaillées, voir [Créer l’application Twitter](deploy-twitter-connector.md#step-3-create-the-twitter-app).

À la fin de cette étape (en suivant les instructions pas à pas), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs seront utilisées pour configurer l’application connecteur Twitter à l’étape 4.

- Clé d’API Twitter

- Clé secrète de l’API Twitter

- Jeton d’accès Twitter

- Secret du jeton d’accès Twitter

## <a name="step-4-configure-the-twitter-connector-app"></a>Étape 4 : Configurer l’application connecteur Twitter

L’étape suivante consiste à ajouter des paramètres de configuration à l’application connecteur Twitter que vous avez déployée à l’étape 2. Pour ce faire, vous allez sur la page d’accueil de votre application de connecteur et la configurez.

Pour obtenir des instructions détaillées, voir [Configurer l’application web du connecteur](deploy-twitter-connector.md#step-4-configure-the-connector-web-app).

Au cours de cette étape (en suivant les instructions pas à pas), vous fournirez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes précédentes) :

- Clé d’API Twitter (obtenue à l’étape 3)

- Clé secrète de l’API Twitter (obtenue à l’étape 3)

- Jeton d’accès Twitter (obtenu à l’étape 3)

- Secret du jeton d’accès Twitter (obtenu à l’étape 3)

- Azure Active Directory’ID d’application (ident AAD’application obtenue à l’étape 1)

- Azure Active Directory’application secrète (la AAD de l’application obtenue à l’étape 1)

## <a name="step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center"></a>Étape 5 : Configurer un connecteur Twitter dans le Centre de conformité Microsoft 365

La dernière étape consiste à configurer le connecteur Twitter dans le Centre de conformité Microsoft 365 qui importera les données du compte Twitter de votre organisation vers une boîte aux lettres spécifiée dans Microsoft 365. Une fois cette étape terminée, le service d’importation Microsoft 365 commence à importer des données à partir du compte Twitter de votre organisation vers Microsoft 365.

Pour obtenir des instructions détaillées, voir Configurer un connecteur [Twitter dans le Centre de conformité Microsoft 365](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center). 

Au cours de cette étape (en suivant les instructions pas à pas), vous fournirez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes).

- URL du service d’application Azure (obtenue à l’étape 2 ; par exemple, `https://twitterconnector.azurewebsites.net`)

- APISecretKey (que vous avez créé à l’étape 2)