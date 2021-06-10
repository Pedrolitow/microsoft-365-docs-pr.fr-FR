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
localization_priority: Normal
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Découvrez comment les administrateurs peuvent configurer et utiliser un connecteur natif pour importer des données Twitter dans Microsoft 365.
ms.openlocfilehash: 277af8ea7367936c4c9528a8ca50ccd678745bf6
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50922256"
---
# <a name="set-up-a-connector-to-archive-twitter-data-preview"></a>Configurer un connecteur pour archiver des données Twitter (aperçu)

Utilisez un connecteur dans le centre de conformité Microsoft 365 pour importer et archiver des données de Twitter vers Microsoft 365. Après avoir configuré et configuré le connecteur, il se connecte au compte Twitter de votre organisation (de manière programmée), convertit le contenu d’un élément au format de message électronique, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois les données Twitter importées, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu, l’archivage In-Place, l’audit et les stratégies de rétention Microsoft 365 aux données Twitter. Par exemple, lorsqu’une boîte aux lettres est placée en conservation pour litige ou affectée à une stratégie de rétention, les données Twitter sont conservées. Vous pouvez rechercher des données tierces à l’aide de la recherche de contenu ou associer la boîte aux lettres dans laquelle les données Twitter sont stockées à un dépositaire dans Advanced eDiscovery cas. L’utilisation d’un connecteur pour importer et archiver des données Twitter dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

Une fois les données Twitter importées, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu, l’archivage In-Place, l’audit, la conformité des communications et les stratégies de rétention Microsoft 365 aux données stockées dans la boîte aux lettres. Par exemple, vous pouvez rechercher des données Twitter à l’aide de la recherche de contenu ou associer la boîte aux lettres dans laquelle les données sont stockées à un dépositaire dans Advanced eDiscovery cas. L’utilisation d’un connecteur pour importer et archiver des données Twitter dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

Remplissez les conditions préalables suivantes avant de pouvoir configurer un connecteur dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir du compte Twitter de votre organisation.

- Vous avez besoin d’un compte Twitter pour votre organisation . vous devez vous connectez à ce compte lors de la configuration du connecteur.

- Votre organisation doit avoir un abonnement Azure valide. Si vous n’avez pas d’abonnement Azure existant, vous pouvez vous inscrire à l’une des options ci-après :

    - [S’inscrire à un abonnement Azure gratuit d’un an](https://azure.microsoft.com/free) 

    - [S’inscrire à un abonnement Azure de paiement par abonnement](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [L’abonnement Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md) gratuit inclus dans votre abonnement Microsoft 365 ne prend pas en charge les connecteurs dans le Centre de sécurité & conformité.

- Le connecteur Twitter peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 éléments Twitter dans une journée, aucun de ces éléments n’est importé dans Microsoft 365.

- L’utilisateur qui définit le connecteur Twitter dans le centre de conformité Microsoft 365 (à l’étape 5) doit se voir attribuer le rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

La première étape consiste à inscrire une nouvelle application dans Azure Active Directory (AAD). Cette application correspond à la ressource d’application web que vous implémentez à l’étape 2 pour le connecteur Twitter.

Pour obtenir des instructions détaillées, voir [Créer une application dans Azure Active Directory](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).

À la fin de cette étape (en suivant les instructions pas à pas), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs seront utilisées dans les étapes ultérieures du processus de déploiement.

- ID d’application AAD

- Secret d’application AAD

- ID de client

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a>Étape 2 : Déployer le service web connecteur à partir GitHub référentiel vers votre compte Azure

L’étape suivante consiste à déployer le code source pour l’application connecteur Twitter qui utilisera l’API Twitter pour se connecter à votre compte Twitter et extraire des données afin de pouvoir les importer dans Microsoft 365. Le connecteur Twitter que vous déployez pour votre organisation charge les éléments à partir du compte Twitter de votre organisation vers l’emplacement stockage Azure qui est créé au cours de cette étape. Après avoir créé un connecteur Twitter dans le centre de conformité Microsoft 365 (à l’étape 5), le service d’importation Microsoft 365 copie les données Twitter de l’emplacement stockage Azure vers une boîte aux lettres dans Microsoft 365. Comme expliqué précédemment dans la [section](#before-you-set-up-a-connector) Avant de configurer un connecteur, vous devez avoir un abonnement Azure valide pour créer un compte stockage Azure client.

Pour déployer le code source de l’application connecteur Twitter :

1. Go to [this GitHub site](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet).

2. Cliquez **sur Déployer sur Azure.**

Pour obtenir des instructions détaillées, voir Déployer le service web de connecteur depuis [GitHub vers votre compte Azure.](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account)

Bien que vous suiviez les instructions pas à pas pour effectuer cette étape, vous fournissez les informations suivantes :

- APISecretKey : vous créez cette clé secrète à la fin de cette étape. Il est utilisé à l’étape 5.

- tenantId : ID de locataire de votre organisation Microsoft 365 que vous avez copiée après la création de l’application Twitter à l Azure Active Directory l’étape 1.

Après avoir effectué cette étape, assurez-vous de copier l’URL du service d’application (par exemple, `https://twitterconnector.azurewebsites.net` ). Vous devez utiliser cette URL pour effectuer les étapes 3, 4 et 5.

## <a name="step-3-create-developer-app-on-twitter"></a>Étape 3 : Créer une application de développeur sur Twitter

L’étape suivante consiste à créer et configurer une application de développeur sur Twitter. Le connecteur personnalisé que vous créez à l’étape 7 utilise l’application Twitter pour interagir avec l’API Twitter afin d’obtenir des données à partir du compte Twitter de votre organisation.

Pour obtenir des instructions détaillées, voir [Créer l’application Twitter.](deploy-twitter-connector.md#step-3-create-the-twitter-app)

À la fin de cette étape (en suivant les instructions pas à pas), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs seront utilisées pour configurer l’application connecteur Twitter à l’étape 4.

- Clé d’API Twitter

- Clé secrète de l’API Twitter

- Jeton d’accès Twitter

- Secret du jeton d’accès Twitter

## <a name="step-4-configure-the-twitter-connector-app"></a>Étape 4 : Configurer l’application connecteur Twitter

L’étape suivante consiste à ajouter des paramètres de configuration à l’application connecteur Twitter que vous avez déployée à l’étape 2. Pour ce faire, vous allez sur la page d’accueil de votre application de connecteur et la configurez.

Pour obtenir des instructions détaillées, voir [Configurer l’application web du connecteur.](deploy-twitter-connector.md#step-4-configure-the-connector-web-app)

Au cours de cette étape (en suivant les instructions pas à pas), vous fournirez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes précédentes) :

- Clé d’API Twitter (obtenue à l’étape 3)

- Clé secrète de l’API Twitter (obtenue à l’étape 3)

- Jeton d’accès Twitter (obtenu à l’étape 3)

- Secret du jeton d’accès Twitter (obtenu à l’étape 3)

- Azure Active Directory’ID d’application (ID d’application AAD obtenu à l’étape 1)

- Azure Active Directory’application secrète (secret d’application AAD obtenu à l’étape 1)

## <a name="step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center"></a>Étape 5 : Configurer un connecteur Twitter dans le centre Microsoft 365 conformité

La dernière étape consiste à configurer le connecteur Twitter dans le centre de conformité Microsoft 365 qui importera les données du compte Twitter de votre organisation vers une boîte aux lettres spécifiée dans Microsoft 365. Une fois cette étape terminée, le service d’importation Microsoft 365 commence à importer des données à partir du compte Twitter de votre organisation vers Microsoft 365.

Pour obtenir des instructions détaillées, voir Configurer un connecteur Twitter dans le [centre Microsoft 365 conformité.](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center) 

Au cours de cette étape (en suivant les instructions pas à pas), vous fournirez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes).

- URL du service d’application Azure (obtenue à l’étape 2 ; par exemple, `https://twitterconnector.azurewebsites.net` )

- APISecretKey (que vous avez créé à l’étape 2)