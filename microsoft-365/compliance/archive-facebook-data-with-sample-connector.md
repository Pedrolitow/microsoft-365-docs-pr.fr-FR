---
title: Configurer un connecteur pour archiver des données Facebook
description: Découvrez comment configurer & utiliser un connecteur dans le portail de conformité Microsoft Purview pour importer des données d’archivage & à partir de pages Facebook Business vers Microsoft 365.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 07/15/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- tier3
- purview-compliance
- data-connectors
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 146dff25f3e4f2865d67a2e5734604bf8cecf97a
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68811962"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>Configurer un connecteur pour archiver les données Facebook (préversion)

Utilisez un connecteur dans le portail de conformité Microsoft Purview pour importer et archiver des données des pages Facebook Business vers Microsoft 365. Après avoir configuré et configuré le connecteur, il se connecte à la page Facebook Business (sur une base planifiée), convertit le contenu des éléments Facebook au format de message électronique, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois les données Facebook importées, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation pour litige, la recherche de contenu, l’archivage In-Place, l’audit, la conformité des communications et les stratégies de rétention Microsoft 365 aux données Facebook. Par exemple, lorsqu’une boîte aux lettres est placée en conservation pour litige ou affectée à une stratégie de rétention, les données Facebook sont conservées. Vous pouvez rechercher des données tierces à l’aide de la recherche de contenu ou associer la boîte aux lettres dans laquelle les données Facebook sont stockées à un consignataire dans un cas Microsoft Purview eDiscovery (Premium). L’utilisation d’un connecteur pour importer et archiver des données Facebook dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

Si vous souhaitez participer à la préversion, contactez l’équipe à dcfeedback@microsoft.com.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>Conditions préalables à la configuration d’un connecteur pour les pages Facebook Business

Remplissez les conditions préalables suivantes avant de pouvoir configurer et configurer un connecteur dans le portail de conformité pour importer et archiver des données à partir des pages Facebook Business de votre organisation. 

- Vous avez besoin d’un compte Facebook pour les pages professionnelles de votre organisation (vous devez vous connecter à ce compte lors de la configuration du connecteur). Actuellement, vous pouvez uniquement archiver les données des pages Facebook Business; Vous ne pouvez pas archiver les données des profils Facebook individuels.

- Votre organisation doit disposer d’un abonnement Azure valide. Si vous n’avez pas d’abonnement Azure existant, vous pouvez vous inscrire à l’une des options suivantes :

    - [S’inscrire gratuitement à un abonnement Azure d’un an](https://azure.microsoft.com/free)

    - [S’inscrire à un abonnement Azure avec paiement à l’utilisation](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [L’abonnement Azure Active Directory gratuit](use-your-free-azure-ad-subscription-in-office-365.md) inclus avec votre abonnement Microsoft 365 ne prend pas en charge les connecteurs dans le portail de conformité.

- Le connecteur pour les pages Facebook Business peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 éléments Facebook Business par jour, aucun de ces éléments n’est importé dans Microsoft 365.

- L’utilisateur qui configure le connecteur personnalisé dans le portail de conformité (à l’étape 5) doit se voir attribuer le rôle de Administration connecteur de données. Ce rôle est requis pour ajouter des connecteurs dans la page **Connecteurs de données** du portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les portails defender et de conformité » dans [Rôles et groupes de rôles dans les portails de conformité Microsoft 365 Defender et Microsoft Purview](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-defender-and-compliance-portals). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle de Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

La première étape consiste à inscrire une nouvelle application dans Azure Active Directory (AAD). Cette application correspond à la ressource d’application web que vous implémentez à l’étape 4 et à l’étape 5 pour le connecteur Facebook.

Pour obtenir des instructions pas à pas, consultez [Créer une application dans Azure Active Directory](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory).

À la fin de cette étape (à l’aide des instructions pas à pas précédentes), vous allez enregistrer les informations suivantes dans un fichier texte. Ces valeurs sont utilisées dans les étapes ultérieures du processus de déploiement.

- ID d’application AAD

- Secret de l’application AAD

- ID de locataire

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Étape 2 : Déployer le service web de connecteur à partir de GitHub sur votre compte Azure

L’étape suivante consiste à déployer le code source de l’application de connecteur de pages Facebook Business qui utilisera l’API Facebook pour se connecter à votre compte Facebook et extraire les données afin de pouvoir les importer dans Microsoft 365. Le connecteur Facebook que vous déployez pour votre organisation charge les éléments de vos pages Facebook Business vers l’emplacement de stockage Azure créé à cette étape. Après avoir créé un connecteur de pages professionnelles Facebook dans le portail de conformité (à l’étape 5), le service d’importation copie les données des pages professionnelles Facebook de l’emplacement de stockage Azure vers une boîte aux lettres de votre organisation Microsoft 365. Comme expliqué précédemment dans la section [Conditions préalables](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages) , vous devez disposer d’un abonnement Azure valide pour créer un compte de stockage Azure.

Pour obtenir des instructions pas à pas, consultez [Déployer le service web de connecteur à partir de GitHub sur votre compte Azure](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

Dans les instructions pas à pas pour effectuer cette étape, vous allez fournir les informations suivantes :

- APISecretKey : vous créez ce secret à la fin de cette étape. Il est utilisé à l’étape 5.

- TenantId : ID de locataire de votre organisation Microsoft 365 que vous avez copié après avoir créé l’application de connecteur Facebook dans Azure Active Directory à l’étape 1.

Après avoir effectué cette étape, veillez à copier l’URL d’Azure App Service (par exemple, https://fbconnector.azurewebsites.net). Vous devez utiliser cette URL pour effectuer les étapes 3, 4 et 5).

## <a name="step-3-register-the-web-app-on-facebook"></a>Étape 3 : Inscrire l’application web sur Facebook

L’étape suivante consiste à créer et configurer une application sur Facebook. Le connecteur pages professionnelles Facebook que vous créez à l’étape 5 utilise l’application web Facebook pour interagir avec l’API Facebook afin d’obtenir des données à partir des pages Facebook Business de votre organisation.

Pour obtenir des instructions pas à pas, consultez [Inscrire l’application Facebook](deploy-facebook-connector.md#step-3-register-the-facebook-app).

À la fin de cette étape (en suivant les instructions pas à pas), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs sont utilisées pour configurer l’application de connecteur Facebook à l’étape 4.

- ID d’application Facebook

- Secret de l’application Facebook

- Jeton de vérification des webhooks Facebook

## <a name="step-4-configure-the-facebook-connector-app"></a>Étape 4 : Configurer l’application de connecteur Facebook

L’étape suivante consiste à ajouter des paramètres de configuration à l’application de connecteur Facebook que vous avez chargée lorsque vous avez créé la ressource d’application web Azure à l’étape 1. Pour ce faire, accédez à la page d’accueil de votre application de connecteur et configurez-la.

Pour obtenir des instructions pas à pas, consultez [Configurer l’application de connecteur Facebook](archive-facebook-data-with-sample-connector.md#step-4-configure-the-facebook-connector-app).

À la fin de cette étape (en suivant les instructions pas à pas), vous fournissez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes précédentes) :

- ID d’application Facebook (obtenu à l’étape 3)

- Secret de l’application Facebook (obtenu à l’étape 3)

- Jeton de vérification des webhooks Facebook (obtenu à l’étape 3)

- ID d’application Azure Active Directory (ID d’application AAD obtenu à l’étape 1)

- Secret d’application Azure Active Directory (secret d’application AAD obtenu à l’étape 1)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-compliance-portal"></a>Étape 5 : Configurer un connecteur pages Facebook Business dans le portail de conformité

La dernière étape consiste à configurer le connecteur dans le portail de conformité qui importera les données de vos pages Facebook Business dans une boîte aux lettres spécifiée dans Microsoft 365. Une fois cette étape terminée, le service d’importation Microsoft 365 commence à importer des données de vos pages Facebook Business vers Microsoft 365.

Pour obtenir des instructions pas à pas, consultez [Étape 5 : Configurer un connecteur Facebook dans le portail de conformité](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-compliance-portal).

À la fin de cette étape (en suivant les instructions pas à pas), vous fournissez les informations suivantes (que vous avez copiées dans un fichier texte une fois les étapes terminées).

- ID d’application AAD (obtenu à l’étape 1)

- URL Azure App Service (obtenue à l’étape 1 ; par exemple, https://fbconnector.azurewebsites.net)

- APISecretKey (que vous avez créée à l’étape 2)
