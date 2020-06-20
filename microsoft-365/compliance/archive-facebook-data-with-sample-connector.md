---
title: Configurer un connecteur pour archiver des données Facebook
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Découvrez comment configurer & utiliser un connecteur dans le centre de conformité Microsoft 365 pour importer des données d’archivage & à partir de pages Facebook Business vers Microsoft 365.
ms.openlocfilehash: 79f3c3914476a20c07a1c3ab4418b918c8f22c3e
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44818463"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>Configuration d’un connecteur pour l’archivage des données Facebook (aperçu)

Utilisez un connecteur dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir de pages d’entreprise Facebook vers Microsoft 365. Une fois que vous avez configuré et configuré le connecteur, il se connecte à la page d’entreprise Facebook (de manière planifiée), convertit le contenu des éléments Facebook en format de message électronique, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois les données Facebook importées, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, la recherche de contenu, l’archivage inaltérable, l’audit, la conformité de la communication et les stratégies de rétention de Microsoft 365 aux données Facebook. Par exemple, lorsqu’une boîte aux lettres est placée en conservation pour litige ou affectée à une stratégie de rétention, les données Facebook sont conservées. Vous pouvez rechercher des données tierces à l’aide de la recherche de contenu ou associer la boîte aux lettres dans laquelle les données Facebook sont stockées avec un dépositaire dans un cas avancé de découverte électronique. L’utilisation d’un connecteur pour importer et archiver des données Facebook dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>Conditions préalables à la configuration d’un connecteur pour les pages d’entreprise Facebook

Avant de pouvoir installer et configurer un connecteur dans le centre de conformité Microsoft 365, vous devez remplir les conditions préalables suivantes pour importer et archiver des données à partir des pages d’entreprise Facebook de votre organisation. 

- Vous avez besoin d’un compte Facebook pour les pages professionnelles de votre organisation (vous devez vous connecter à ce compte lors de la configuration du connecteur). Actuellement, vous pouvez uniquement archiver les données à partir de pages d’entreprise Facebook ; vous ne pouvez pas archiver les données de profils Facebook individuels.

- Votre organisation doit disposer d’un abonnement Azure valide. Si vous n’avez pas d’abonnement Azure existant, vous pouvez vous inscrire à l’une de ces options :

    - [Inscrivez-vous pour obtenir un abonnement Azure gratuit d’un an](https://azure.microsoft.com/free) 

    - [S’inscrire pour un abonnement Azure avec paiement en tant que](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > L' [abonnement Azure Active Directory gratuit](use-your-free-azure-ad-subscription-in-office-365.md) qui est inclus dans votre abonnement Microsoft 365 ne prend pas en charge les connecteurs dans le centre de sécurité & Compliance Center.

- Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Pour accepter cette demande, accédez à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent), connectez-vous à l’aide des informations d’identification d’un administrateur général, puis acceptez la demande.

- L’utilisateur qui configure le connecteur personnalisé dans le centre de conformité Microsoft 365 (à l’étape 5) doit se voir attribuer le rôle importation/exportation de boîte aux lettres dans Exchange Online. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : créer une application dans Azure Active Directory

La première étape consiste à inscrire une nouvelle application dans Azure Active Directory (AAD). Cette application correspond à la ressource Web App que vous implémentez à l’étape 4 et à l’étape 5 pour le connecteur Facebook. 

Pour obtenir des instructions pas à pas, consultez la rubrique [créer une application dans Azure Active Directory](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory).

Lors de l’exécution de cette étape (à l’aide des instructions étape par étape précédentes), vous enregistrerez les informations suivantes dans un fichier texte. Ces valeurs sont utilisées dans les étapes ultérieures du processus de déploiement.

- ID d’application AAD

- Clé secrète de l’application AAD

- ID de locataire

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Étape 2 : déployer le service Web connecteur depuis GitHub vers votre compte Azure

L’étape suivante consiste à déployer le code source pour l’application de connecteur de pages d’entreprise Facebook qui utilisera l’API Facebook pour se connecter à votre compte Facebook et extraire des données afin que vous puissiez les importer dans Microsoft 365. Le connecteur Facebook que vous déployez pour votre organisation télécharge les éléments à partir de vos pages Facebook dans l’emplacement de stockage Azure créé lors de cette étape. Une fois que vous avez créé un connecteur Facebook pour les pages d’entreprise dans le centre de conformité Microsoft 365 (à l’étape 5), le service d’importation copie les données des pages d’entreprise Facebook à partir de l’emplacement de stockage Azure vers une boîte aux lettres de votre organisation Microsoft 365. Comme indiqué précédemment dans la section [conditions préalables](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages) , vous devez disposer d’un abonnement Azure valide pour créer un compte de stockage Azure.

Pour obtenir des instructions pas à pas, consultez [la rubrique déployer le service Web connecteur depuis Github vers votre compte Azure](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

Dans les instructions pas à pas pour effectuer cette étape, vous devez fournir les informations suivantes :

- APISecretKey : vous créez cette clé secrète lors de l’exécution de cette étape. Elle est utilisée à l’étape 5.

- TenantId : ID de client de votre organisation Microsoft 365 que vous avez copié après avoir créé l’application de connecteur Facebook dans Azure Active Directory à l’étape 1.

Une fois cette étape terminée, veillez à copier l’URL du service d’application Azure (par exemple, https://fbconnector.azurewebsites.net) . Vous devez utiliser cette URL pour effectuer l’étape 3, étape 4, et étape 5).

## <a name="step-3-register-the-web-app-on-facebook"></a>Étape 3 : inscription de l’application Web sur Facebook

L’étape suivante consiste à créer et configurer une nouvelle application sur Facebook. Le connecteur Facebook des pages d’entreprise que vous créez à l’étape 5 utilise l’application Web Facebook pour interagir avec l’API Facebook afin d’obtenir des données à partir des pages d’entreprise Facebook de votre organisation.

Pour obtenir des instructions pas à pas, consultez [la rubrique enregistrer l’application Facebook](deploy-facebook-connector.md#step-3-register-the-facebook-app).

Lors de l’exécution de cette étape (en suivant les instructions pas à pas), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs sont utilisées pour configurer l’application de connecteur Facebook à l’étape 4.

- ID d’application Facebook

- Clé secrète de l’application Facebook

- Jeton de vérification des webhooks Facebook

## <a name="step-4-configure-the-facebook-connector-app"></a>Étape 4 : configuration de l’application de connecteur Facebook

L’étape suivante consiste à ajouter des paramètres de configuration à l’application de connecteur Facebook que vous avez chargée lors de la création de la ressource Azure Web App à l’étape 1. Pour ce faire, accédez à la page d’accueil de votre application de connecteur et configurez-la.

Pour obtenir des instructions pas à pas, consultez [la rubrique Configure the Facebook Connector App](archive-facebook-data-with-sample-connector.md#step-4-configure-the-facebook-connector-app).

Lors de l’exécution de cette étape (en suivant les instructions pas à pas), vous fournissez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes précédentes) :

- ID d’application Facebook (obtenu à l’étape 3)

- Clé secrète de l’application Facebook (obtenue à l’étape 3)

- Jeton de vérification des webhooks Facebook (obtenu à l’étape 3)

- ID d’application Azure Active Directory (l’ID d’application AAD obtenu à l’étape 1)

- Clé secrète de l’application Azure Active Directory (la clé secrète de l’application AAD obtenue à l’étape 1)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-microsoft-365-compliance-center"></a>Étape 5 : configurer un connecteur Facebook pour les pages d’entreprise dans le centre de conformité Microsoft 365

La dernière étape consiste à configurer le connecteur dans le centre de conformité Microsoft 365 qui importe les données de vos pages Facebook Business vers une boîte aux lettres spécifique dans Microsoft 365. Une fois cette étape terminée, le service d’importation Office 365 commencera à importer des données à partir de vos pages Facebook Business vers Microsoft 365.

Pour obtenir des instructions pas à pas, reportez-vous à [l’étape 5 : configurer un connecteur Facebook dans le centre de conformité Microsoft 365](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-microsoft-365-compliance-center). 

Lors de l’exécution de cette étape (en suivant les instructions pas à pas), vous fournissez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes).

- ID de l’application AAD (obtenu à l’étape 1)

- URL du service d’application Azure (obtenue à l’étape 1, par exemple,https://fbconnector.azurewebsites.net)

- APISecretKey (que vous avez créé à l’étape 2)
