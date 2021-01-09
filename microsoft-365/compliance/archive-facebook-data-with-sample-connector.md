---
title: Configurer un connecteur pour archiver des données Facebook
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
description: Découvrez comment configurer & utiliser un connecteur dans le Centre de conformité Microsoft 365 pour importer des données d’archivage & des pages Facebook Business vers Microsoft 365.
ms.openlocfilehash: df86897defa92788399f704c53c00ebb9e4f4269
ms.sourcegitcommit: 7d4aa58ae9fc893825b6e648fa3f072c3ac59628
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2021
ms.locfileid: "49790148"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>Configurer un connecteur pour archiver les données Facebook (aperçu)

Utilisez un connecteur dans le Centre de conformité Microsoft 365 pour importer et archiver des données des pages Facebook Business vers Microsoft 365. Après avoir configuré et configuré le connecteur, il se connecte à la page Facebook Business (de manière programmée), convertit le contenu des éléments Facebook au format de message électronique, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois les données Facebook importées, vous pouvez appliquer aux données Facebook des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu, l’archivage In-Place, l’audit, la conformité des communications et les stratégies de rétention Microsoft 365. Par exemple, lorsqu’une boîte aux lettres est placée en conservation pour litige ou affectée à une stratégie de rétention, les données Facebook sont conservées. Vous pouvez rechercher des données tierces à l’aide de la recherche de contenu ou associer la boîte aux lettres dans laquelle les données Facebook sont stockées à un dépositaire dans un cas Advanced eDiscovery. L’utilisation d’un connecteur pour importer et archiver des données Facebook dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>Conditions préalables à la configuration d’un connecteur pour les pages Facebook Business

Remplissez les conditions préalables suivantes avant de pouvoir configurer un connecteur dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir des pages Facebook Business de votre organisation. 

- Vous avez besoin d’un compte Facebook pour les pages professionnelles de votre organisation (vous devez vous y inscrire lors de la configuration du connecteur). Actuellement, vous pouvez uniquement archiver des données à partir de pages Facebook Business ; vous ne pouvez pas archiver des données à partir de profils Facebook individuels.

- Votre organisation doit avoir un abonnement Azure valide. Si vous n’avez pas d’abonnement Azure existant, vous pouvez vous inscrire à l’une des options ci-après :

    - [S’inscrire à un abonnement Azure gratuit d’un an](https://azure.microsoft.com/free)

    - [S’inscrire à un abonnement Azure de paiement par abonnement](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [L’abonnement Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md) gratuit inclus dans votre abonnement Microsoft 365 ne prend pas en charge les connecteurs dans le Centre de sécurité & conformité.

- Le connecteur pour les pages Facebook Business peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 éléments Facebook Business par jour, aucun de ces éléments ne sera importé dans Microsoft 365.

- L’utilisateur qui définit le connecteur personnalisé dans le Centre de conformité Microsoft 365 (à l’étape 5) doit se voir attribuer le rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) [Créer](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ».

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

La première étape consiste à inscrire une nouvelle application dans Azure Active Directory (AAD). Cette application correspond à la ressource d’application web que vous implémentez aux étapes 4 et 5 pour le connecteur Facebook. 

Pour obtenir des instructions détaillées, voir [Créer une application dans Azure Active Directory.](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory)

À la fin de cette étape (en suivant les instructions pas à pas précédentes), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs sont utilisées dans les étapes ultérieures du processus de déploiement.

- ID d’application AAD

- Secret d’application AAD

- ID de client

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Étape 2 : Déployer le service web de connecteur à partir de GitHub vers votre compte Azure

L’étape suivante consiste à déployer le code source pour l’application connecteur de pages d’entreprise Facebook qui utilisera l’API Facebook pour se connecter à votre compte Facebook et extraire des données afin de pouvoir les importer dans Microsoft 365. Le connecteur Facebook que vous déployez pour votre organisation charge les éléments de vos pages Facebook Business vers l’emplacement de stockage Azure créé au cours de cette étape. Après avoir créé un connecteur de pages d’entreprise Facebook dans le Centre de conformité Microsoft 365 (à l’étape 5), le service d’importation copie les données des pages d’entreprise Facebook à partir de l’emplacement de stockage Azure vers une boîte aux lettres de votre organisation Microsoft 365. Comme expliqué précédemment dans la section [Conditions préalables,](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages) vous devez avoir un abonnement Azure valide pour créer un compte de stockage Azure.

Pour obtenir des instructions détaillées, voir Déployer le service web de connecteur à partir de [GitHub sur votre compte Azure.](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account)

Dans les instructions détaillées pour effectuer cette étape, vous allez fournir les informations suivantes :

- APISecretKey : vous créez cette clé secrète à la fin de cette étape. Il est utilisé à l’étape 5.

- TenantId : ID de locataire de votre organisation Microsoft 365 que vous avez copié après avoir créé l’application connecteur Facebook dans Azure Active Directory à l’étape 1.

Après avoir effectué cette étape, assurez-vous de copier l’URL du service d’application Azure (par exemple, https://fbconnector.azurewebsites.net) . Vous devez utiliser cette URL pour effectuer les étapes 3, 4 et 5.

## <a name="step-3-register-the-web-app-on-facebook"></a>Étape 3 : Inscrire l’application web sur Facebook

L’étape suivante consiste à créer et configurer une nouvelle application sur Facebook. Le connecteur de pages d’entreprise Facebook que vous créez à l’étape 5 utilise l’application web Facebook pour interagir avec l’API Facebook afin d’obtenir des données à partir des pages Facebook Business de votre organisation.

Pour obtenir des instructions détaillées, voir [Enregistrer l’application Facebook.](deploy-facebook-connector.md#step-3-register-the-facebook-app)

À la fin de cette étape (en suivant les instructions pas à pas), vous enregistrez les informations suivantes dans un fichier texte. Ces valeurs sont utilisées pour configurer l’application connecteur Facebook à l’étape 4.

- ID d’application Facebook

- Secret d’application Facebook

- Jeton de vérification des webhooks Facebook

## <a name="step-4-configure-the-facebook-connector-app"></a>Étape 4 : Configurer l’application connecteur Facebook

L’étape suivante consiste à ajouter des paramètres de configuration à l’application connecteur Facebook que vous avez téléchargée lorsque vous avez créé la ressource Azure Web App à l’étape 1. Pour ce faire, vous allez sur la page d’accueil de votre application de connecteur et la configurez.

Pour obtenir des instructions détaillées, voir [Configurer l’application connecteur Facebook.](archive-facebook-data-with-sample-connector.md#step-4-configure-the-facebook-connector-app)

Au cours de cette étape (en suivant les instructions pas à pas), vous fournissez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes précédentes) :

- ID d’application Facebook (obtenu à l’étape 3)

- Secret d’application Facebook (obtenu à l’étape 3)

- Les webhooks Facebook vérifient le jeton (obtenu à l’étape 3)

- ID d’application Azure Active Directory (ID d’application AAD obtenu à l’étape 1)

- Secret d’application Azure Active Directory (secret d’application AAD obtenu à l’étape 1)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-microsoft-365-compliance-center"></a>Étape 5 : Configurer un connecteur de pages Facebook Business dans le Centre de conformité Microsoft 365

La dernière étape consiste à configurer le connecteur dans le Centre de conformité Microsoft 365 qui importera les données de vos pages Facebook Business vers une boîte aux lettres spécifiée dans Microsoft 365. Une fois cette étape terminée, le service d’importation Microsoft 365 commence à importer des données de vos pages Facebook Business vers Microsoft 365.

Pour obtenir des instructions détaillées, voir Étape 5 : Configurer un connecteur Facebook dans le Centre de conformité [Microsoft 365.](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-microsoft-365-compliance-center) 

Au cours de cette étape (en suivant les instructions pas à pas), vous fournissez les informations suivantes (que vous avez copiées dans un fichier texte après avoir effectué les étapes).

- ID d’application AAD (obtenu à l’étape 1)

- URL du service d’application Azure (obtenue à l’étape 1 ; par exemple, https://fbconnector.azurewebsites.net)

- APISecretKey (que vous avez créé à l’étape 2)
