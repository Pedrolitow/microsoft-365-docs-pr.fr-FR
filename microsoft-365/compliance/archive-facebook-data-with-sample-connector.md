---
title: Configurer un connecteur pour archiver des données Facebook
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Découvrez comment configurer & utiliser un connecteur dans le portail de conformité Microsoft Purview pour importer & données d’archive à partir de pages Facebook Business vers Microsoft 365.
ms.openlocfilehash: 2d732352d8b6eebaee304a030736f35bcf32b84c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099320"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>Configurer un connecteur pour archiver les données Facebook (préversion)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Utilisez un connecteur dans le portail de conformité Microsoft Purview pour importer et archiver des données à partir de pages Facebook Business vers Microsoft 365. Après avoir configuré et configuré le connecteur, il se connecte à la page Facebook Business (sur une base planifiée), convertit le contenu des éléments Facebook au format d’e-mail, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois les données Facebook importées, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation du contentieux, la recherche de contenu, l’archivage In-Place, l’audit, la conformité des communications et les stratégies de rétention Microsoft 365 aux données Facebook. Par exemple, lorsqu’une boîte aux lettres est placée en attente de litige ou affectée à une stratégie de rétention, les données Facebook sont conservées. Vous pouvez rechercher des données tierces à l’aide de la recherche de contenu ou associer la boîte aux lettres dans laquelle les données Facebook sont stockées avec un consignateur dans un cas de découverte électronique Microsoft Purview (Premium). L’utilisation d’un connecteur pour importer et archiver des données Facebook dans Microsoft 365 peut aider votre organisation à rester conforme aux politiques gouvernementales et réglementaires.

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>Conditions préalables à la configuration d’un connecteur pour les pages Facebook Business

Remplissez les conditions préalables suivantes avant de pouvoir configurer et configurer un connecteur dans le portail de conformité pour importer et archiver des données à partir des pages Facebook Business de votre organisation. 

- Vous avez besoin d’un compte Facebook pour les pages métier de votre organisation (vous devez vous connecter à ce compte lors de la configuration du connecteur). Actuellement, vous ne pouvez archiver que les données des pages Facebook Business ; vous ne pouvez pas archiver des données à partir de profils Facebook individuels.

- Votre organisation doit disposer d’un abonnement Azure valide. Si vous n’avez pas d’abonnement Azure existant, vous pouvez vous inscrire à l’une des options suivantes :

    - [S’inscrire à un abonnement Azure gratuit d’un an](https://azure.microsoft.com/free)

    - [S’inscrire à un abonnement Azure avec paiement à l’utilisation](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [L’abonnement gratuit Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md) inclus dans votre abonnement Microsoft 365 ne prend pas en charge les connecteurs dans le portail de conformité.

- Le connecteur pour les pages Facebook Business peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 articles Facebook Business par jour, aucun de ces articles ne sera importé dans Microsoft 365.

- L’utilisateur qui configure le connecteur personnalisé dans le portail de conformité (à l’étape 5) doit disposer du rôle Administrateur du connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

La première étape consiste à inscrire une nouvelle application dans Azure Active Directory (AAD). Cette application correspond à la ressource d’application web que vous implémentez à l’étape 4 et à l’étape 5 pour le connecteur Facebook.

Pour obtenir des instructions pas à pas, consultez [Créer une application dans Azure Active Directory](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory).

À la fin de cette étape (en suivant les instructions pas à pas précédentes), vous allez enregistrer les informations suivantes dans un fichier texte. Ces valeurs sont utilisées dans les étapes ultérieures du processus de déploiement.

- ID d’application AAD

- AAD secret d’application

- ID de locataire

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Étape 2 : Déployer le service web du connecteur à partir de GitHub sur votre compte Azure

L’étape suivante consiste à déployer le code source de l’application de connecteur Pages d’entreprise Facebook qui utilisera l’API Facebook pour se connecter à votre compte Facebook et extraire des données afin de pouvoir l’importer dans Microsoft 365. Le connecteur Facebook que vous déployez pour votre organisation charge les éléments de vos pages Facebook Business vers l’emplacement stockage Azure créé à cette étape. Une fois que vous avez créé un connecteur de pages d’entreprise Facebook dans le portail de conformité (à l’étape 5), le service d’importation copie les données des pages d’entreprise Facebook à partir de l’emplacement stockage Azure vers une boîte aux lettres de votre organisation Microsoft 365. Comme expliqué précédemment dans la section [Conditions préalables](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages), vous devez disposer d’un abonnement Azure valide pour créer un compte stockage Azure.

Pour obtenir des instructions pas à pas, consultez [Déployer le service web du connecteur à partir de GitHub sur votre compte Azure](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

Dans les instructions pas à pas pour effectuer cette étape, vous allez fournir les informations suivantes :

- APISecretKey : vous créez ce secret à la fin de cette étape. Il est utilisé à l’étape 5.

- TenantId : ID de locataire de votre organisation Microsoft 365 que vous avez copiée après avoir créé l’application de connecteur Facebook dans Azure Active Directory à l’étape 1.

Une fois cette étape terminée, veillez à copier l’URL du service d’application Azure (par exemple, https://fbconnector.azurewebsites.net). Vous devez utiliser cette URL pour effectuer les étapes 3, 4 et 5).

## <a name="step-3-register-the-web-app-on-facebook"></a>Étape 3 : Inscrire l’application web sur Facebook

L’étape suivante consiste à créer et configurer une application sur Facebook. Le connecteur de pages d’affaires Facebook que vous créez à l’étape 5 utilise l’application web Facebook pour interagir avec l’API Facebook afin d’obtenir des données à partir des pages Facebook Business de votre organisation.

Pour obtenir des instructions pas à pas, consultez [Inscrire l’application Facebook](deploy-facebook-connector.md#step-3-register-the-facebook-app).

À la fin de cette étape (en suivant les instructions pas à pas), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs sont utilisées pour configurer l’application de connecteur Facebook à l’étape 4.

- ID d’application Facebook

- Secret d’application Facebook

- Les webhooks Facebook vérifient le jeton

## <a name="step-4-configure-the-facebook-connector-app"></a>Étape 4 : Configurer l’application de connecteur Facebook

L’étape suivante consiste à ajouter des paramètres de configuration à l’application de connecteur Facebook que vous avez chargée lorsque vous avez créé la ressource d’application web Azure à l’étape 1. Pour ce faire, accédez à la page d’accueil de votre application de connecteur et configurez-la.

Pour obtenir des instructions pas à pas, consultez [Configurer l’application de connecteur Facebook](archive-facebook-data-with-sample-connector.md#step-4-configure-the-facebook-connector-app).

À la fin de cette étape (en suivant les instructions pas à pas), vous fournissez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes précédentes) :

- ID d’application Facebook (obtenu à l’étape 3)

- Secret d’application Facebook (obtenu à l’étape 3)

- Les webhooks Facebook vérifient le jeton (obtenu à l’étape 3)

- Azure Active Directory ID d’application (ID d’application AAD obtenu à l’étape 1)

- Azure Active Directory secret d’application (AAD secret d’application obtenu à l’étape 1)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-compliance-portal"></a>Étape 5 : Configurer un connecteur de pages Facebook Business dans le portail de conformité

La dernière étape consiste à configurer le connecteur dans le portail de conformité qui importera des données de vos pages Facebook Business vers une boîte aux lettres spécifiée dans Microsoft 365. Une fois cette étape terminée, le service d’importation Microsoft 365 commence à importer des données à partir de vos pages Facebook Business vers Microsoft 365.

Pour obtenir des instructions pas à pas, consultez [l’étape 5 : Configurer un connecteur Facebook dans le portail de conformité](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-compliance-portal).

À la fin de cette étape (en suivant les instructions pas à pas), vous fournissez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes).

- AAD ID d’application (obtenu à l’étape 1)

- URL d’Azure App Service (obtenue à l’étape 1; par exemple, https://fbconnector.azurewebsites.net)

- APISecretKey (que vous avez créé à l’étape 2)
