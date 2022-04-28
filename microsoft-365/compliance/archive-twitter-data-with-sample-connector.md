---
title: Configurer un connecteur pour archiver des données Twitter
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Découvrez comment les administrateurs peuvent configurer et utiliser un connecteur natif pour importer des données Twitter dans Microsoft 365.
ms.openlocfilehash: ba151d1ffae18a5df033fbb8696fcd3bf759f285
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094545"
---
# <a name="set-up-a-microsoft-connector-to-archive-twitter-data-preview"></a>Configurer un connecteur Microsoft pour archiver les données Twitter (préversion)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Utilisez un connecteur dans le portail de conformité Microsoft Purview pour importer et archiver des données de Twitter vers Microsoft 365. Après avoir configuré et configuré le connecteur, il se connecte au compte Twitter de votre organisation (sur une base planifiée), convertit le contenu d’un élément au format de message électronique, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois les données Twitter importées, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, la recherche de contenu, l’archivage In-Place, l’audit et les stratégies de rétention Microsoft 365 aux données Twitter. Par exemple, lorsqu’une boîte aux lettres est placée en attente de litige ou affectée à une stratégie de rétention, les données Twitter sont conservées. Vous pouvez rechercher des données tierces à l’aide de la recherche de contenu ou associer la boîte aux lettres où les données Twitter sont stockées avec un consignateur dans un cas de découverte électronique Microsoft Purview (Premium). L’utilisation d’un connecteur pour importer et archiver des données Twitter dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

Une fois les données Twitter importées, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, la recherche de contenu, l’archivage In-Place, l’audit, la conformité des communications et les stratégies de rétention Microsoft 365 aux données stockées dans la boîte aux lettres. Par exemple, vous pouvez rechercher des données Twitter à l’aide de la recherche de contenu ou associer la boîte aux lettres où les données sont stockées avec un consignateur dans un cas eDiscovery (Premium). L’utilisation d’un connecteur pour importer et archiver des données Twitter dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

Remplissez les conditions préalables suivantes avant de pouvoir configurer et configurer un connecteur dans le portail de conformité pour importer et archiver des données à partir du compte Twitter de votre organisation.

- Vous avez besoin d’un compte Twitter pour votre organisation; vous devez vous connecter à ce compte lors de la configuration du connecteur.

- Votre organisation doit disposer d’un abonnement Azure valide. Si vous n’avez pas d’abonnement Azure existant, vous pouvez vous inscrire à l’une des options suivantes :

    - [S’inscrire à un abonnement Azure gratuit d’un an](https://azure.microsoft.com/free) 

    - [S’inscrire à un abonnement Azure avec paiement à l’utilisation](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [L’abonnement gratuit Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md) inclus dans votre abonnement Microsoft 365 ne prend pas en charge les connecteurs dans le portail de conformité.

- Le connecteur Twitter peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 articles Twitter par jour, aucun de ces éléments ne sera importé dans Microsoft 365.

- Le rôle Administrateur du connecteur de données doit être attribué à l’utilisateur qui configure le connecteur Twitter dans le portail de conformité (à l’étape 5). Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

La première étape consiste à inscrire une nouvelle application dans Azure Active Directory (AAD). Cette application correspond à la ressource d’application web que vous implémentez à l’étape 2 pour le connecteur Twitter.

Pour obtenir des instructions pas à pas, consultez [Créer une application dans Azure Active Directory](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).

À la fin de cette étape (en suivant les instructions pas à pas), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs seront utilisées dans les étapes ultérieures du processus de déploiement.

- ID d’application AAD

- AAD secret d’application

- ID de locataire

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a>Étape 2 : Déployer un service web de connecteur à partir d’GitHub dépôt sur votre compte Azure

L’étape suivante consiste à déployer le code source de l’application de connecteur Twitter qui utilisera l’API Twitter pour se connecter à votre compte Twitter et extraire des données afin de pouvoir l’importer dans Microsoft 365. Le connecteur Twitter que vous déployez pour votre organisation charge les éléments à partir du compte Twitter de votre organisation vers l’emplacement stockage Azure créé à cette étape. Après avoir créé un connecteur Twitter dans le portail de conformité (à l’étape 5), le service d’importation Microsoft 365 copie les données Twitter de l’emplacement stockage Azure vers une boîte aux lettres dans Microsoft 365. Comme expliqué précédemment dans la section [Avant de configurer un connecteur](#before-you-set-up-a-connector), vous devez disposer d’un abonnement Azure valide pour créer un compte stockage Azure.

Pour déployer le code source de l’application de connecteur Twitter :

1. Accédez à [ce site GitHub](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet).

2. Cliquez sur **Déployer sur Azure**.

Pour obtenir des instructions pas à pas, consultez [Déployer le service web du connecteur à partir de GitHub sur votre compte Azure](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

Pendant que vous suivez les instructions pas à pas pour effectuer cette étape, vous fournissez les informations suivantes :

- APISecretKey : vous créez ce secret à la fin de cette étape. Il est utilisé à l’étape 5.

- tenantId : ID de locataire de votre organisation Microsoft 365 que vous avez copiée après avoir créé l’application Twitter à Azure Active Directory à l’étape 1.

Une fois cette étape terminée, veillez à copier l’URL app Service (par exemple, `https://twitterconnector.azurewebsites.net`). Vous devez utiliser cette URL pour effectuer les étapes 3, 4 et 5).

## <a name="step-3-create-developer-app-on-twitter"></a>Étape 3 : Créer une application développeur sur Twitter

L’étape suivante consiste à créer et configurer une application développeur sur Twitter. Le connecteur personnalisé que vous créez à l’étape 7 utilise l’application Twitter pour interagir avec l’API Twitter afin d’obtenir des données à partir du compte Twitter de votre organisation.

Pour obtenir des instructions pas à pas, consultez [Créer l’application Twitter](deploy-twitter-connector.md#step-3-create-the-twitter-app).

À la fin de cette étape (en suivant les instructions pas à pas), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs seront utilisées pour configurer l’application de connecteur Twitter à l’étape 4.

- Clé API Twitter

- Clé secrète de l’API Twitter

- Jeton d’accès Twitter

- Secret du jeton d’accès Twitter

## <a name="step-4-configure-the-twitter-connector-app"></a>Étape 4 : Configurer l’application de connecteur Twitter

L’étape suivante consiste à ajouter des paramètres de configuration à l’application de connecteur Twitter que vous avez déployée à l’étape 2. Pour ce faire, accédez à la page d’accueil de votre application de connecteur et configurez-la.

Pour obtenir des instructions pas à pas, consultez [Configurer l’application web du connecteur](deploy-twitter-connector.md#step-4-configure-the-connector-web-app).

À la fin de cette étape (en suivant les instructions pas à pas), vous fournirez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes précédentes) :

- Clé API Twitter (obtenue à l’étape 3)

- Clé secrète de l’API Twitter (obtenue à l’étape 3)

- Jeton d’accès Twitter (obtenu à l’étape 3)

- Secret du jeton d’accès Twitter (obtenu à l’étape 3)

- Azure Active Directory ID d’application (ID d’application AAD obtenu à l’étape 1)

- Azure Active Directory secret d’application (AAD secret d’application obtenu à l’étape 1)

## <a name="step-5-set-up-a-twitter-connector-in-the-compliance-portal"></a>Étape 5 : Configurer un connecteur Twitter dans le portail de conformité

La dernière étape consiste à configurer le connecteur Twitter dans le portail de conformité qui importera des données du compte Twitter de votre organisation vers une boîte aux lettres spécifiée dans Microsoft 365. Une fois cette étape terminée, le service d’importation Microsoft 365 commence à importer des données à partir du compte Twitter de votre organisation vers Microsoft 365.

Pour obtenir des instructions pas à pas, consultez [Configurer un connecteur Twitter dans le portail de conformité Microsoft Purview](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-compliance-portal).

À la fin de cette étape (en suivant les instructions pas à pas), vous fournirez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes).

- URL azure app service (obtenue à l’étape 2 ; par exemple, `https://twitterconnector.azurewebsites.net`)

- APISecretKey (que vous avez créé à l’étape 2)