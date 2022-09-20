---
title: Déployer un connecteur pour archiver les données Twitter
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ROBOTS: NOINDEX, NOFOLLOW
description: Les administrateurs peuvent configurer un connecteur natif pour importer et archiver des données Twitter dans Microsoft 365. Une fois ces données importées dans Microsoft 365, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer la gouvernance des données Twitter de votre organisation.
ms.openlocfilehash: f06fc649a4976b3c9266f75baeccc410846bc605
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67817419"
---
# <a name="deploy-a-connector-to-archive-twitter-data"></a>Déployer un connecteur pour archiver les données Twitter

Cet article contient le processus pas à pas pour déployer un connecteur qui utilise le service d’importation Office 365 pour importer des données à partir du compte Twitter de votre organisation vers Microsoft 365. Pour obtenir une vue d’ensemble générale de ce processus et une liste des conditions préalables requises pour déployer un connecteur Twitter, consultez [Configurer un connecteur pour archiver les données Twitter ](archive-twitter-data-with-sample-connector.md).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

1. Accédez à <https://portal.azure.com> et connectez-vous à l’aide des informations d’identification d’un compte d’administrateur général.

   ![Connectez-vous à Azure.](../media/TCimage01.png)

2. Dans le volet de navigation gauche, cliquez sur **Azure Active Directory**.

   ![Accédez à Azure Active Directory.](../media/TCimage02.png)

3. Dans le volet de navigation gauche, cliquez sur **inscriptions d'applications (préversion),** puis sur **Nouvelle inscription**.

   ![Créez une inscription d’application.](../media/TCimage03.png)

4. Inscription de l’application Sous **URI de redirection (facultatif),** sélectionnez **Web** dans la liste déroulante de type d’application, puis tapez `https://portal.azure.com` dans la zone de l’URI.

   ![Tapez https://portal.azure.com l’URI de redirection.](../media/TCimage04.png)

5. Copiez **l’ID d’application (client)** et **l’ID d’annuaire (locataire)** et enregistrez-les dans un fichier texte ou un autre emplacement sécurisé. Vous utiliserez ces ID dans les étapes suivantes.

    ![Copiez et enregistrez l’ID d’application et l’ID d’annuaire.](../media/TCimage05.png)

6. Accédez à **Certificats & secrets pour la nouvelle application** et, sous **Secrets client** , cliquez sur **Nouveau secret client**.

   ![Créez une clé secrète client.](../media/TCimage06.png)

7. Créez un secret. Dans la zone de description, tapez le secret, puis choisissez une période d’expiration.

   ![Tapez le secret et choisissez la période d’expiration.](../media/TCimage08.png)

8. Copiez la valeur du secret et enregistrez-la dans un fichier texte ou un autre emplacement de stockage. Il s’agit du secret d’application AAD que vous utiliserez dans les étapes ultérieures.

   ![Copiez et enregistrez le secret.](../media/TCimage09.png)


## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Étape 2 : Déployer le service web de connecteur à partir de GitHub sur votre compte Azure

1. Accédez à [ce site GitHub](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet) , puis cliquez sur **Déployer sur Azure**.

    ![Accédez à la page d’accueil Azure.](../media/FBCimage11.png)

2. Après avoir cliqué sur **Déployer sur Azure**, vous êtes redirigé vers un Portail Azure avec une page de modèle personnalisée. Renseignez les informations **de base** et **les paramètres** , puis cliquez sur **Acheter**.

   ![Cliquez sur Créer une ressource et tapez un compte de stockage.](../media/FBCimage12.png)

    - **Abonnement:** Sélectionnez votre abonnement Azure sur lequel vous souhaitez déployer le service web du connecteur Twitter.

    - **Groupe de ressources :** Choisissez ou créez un groupe de ressources. Un groupe de ressources est un conteneur qui contient des ressources associées pour une solution Azure.

    - **Emplacement:** Choisissez un emplacement.

    - **Nom de l’application web :** Fournissez un nom unique pour l’application web du connecteur. Le nom doit comporter entre 3 et 18 caractères. Ce nom est utilisé pour créer l’URL d’Azure App Service ; Par exemple, si vous fournissez le nom de l’application web **twitterconnector** , l’URL du service d’application Azure sera **twitterconnector.azurewebsites.net**.

    - **tenantId :** ID de locataire de votre organisation Microsoft 365 que vous avez copié après avoir créé l’application de connecteur Facebook dans Azure Active Directory à l’étape 1.

   - **APISecretKey :** Vous pouvez taper n’importe quelle valeur comme secret. Il est utilisé pour accéder à l’application web du connecteur à l’étape 5.

3. Une fois le déploiement réussi, la page ressemble à la capture d’écran suivante :

    ![Cliquez sur Stockage, puis sur Compte de stockage.](../media/FBCimage13.png)

## <a name="step-3-create-the-twitter-app"></a>Étape 3 : Créer l’application Twitter

1. Accédez à https://developer.twitter.com, connectez-vous à l’aide des informations d’identification du compte de développeur pour votre organisation, puis cliquez sur **Applications**.

   ![Accédez à https://developer.twitter.com et connectez-vous.](../media/TCimage25-5.png)
2. Cliquez sur **Créer une application**.

   ![Accédez à la page Applications pour créer une application.](../media/TCimage26.png)

3. Sous **Détails de l’application**, ajoutez des informations sur l’application.

   ![Entrez des informations sur l’application.](../media/TCimage27.png)

4. Dans le tableau de bord du développeur Twitter, sélectionnez l’application que vous venez de créer, puis cliquez sur **Détails**.

   ![Copiez et enregistrez l’ID d’application.](../media/TCimage28.png)

5. Sous l’onglet **Clés et jetons** , sous **Clés d’API grand public** , copiez la clé API et la clé secrète API et enregistrez-les dans un fichier texte ou un autre emplacement de stockage. Cliquez ensuite sur **Créer** pour générer un jeton d’accès et un secret de jeton d’accès, puis copiez-les dans un fichier texte ou un autre emplacement de stockage.

   ![Copiez et enregistrez dans la clé secrète API.](../media/TCimage29.png)

   Cliquez ensuite sur **Créer** pour générer un jeton d’accès et un secret de jeton d’accès, puis copiez-les dans un fichier texte ou un autre emplacement de stockage.

6. Cliquez sur l’onglet **Autorisations** et configurez les autorisations comme illustré dans la capture d’écran suivante :

   ![Configurez les autorisations.](../media/TCimage30.png)

7. Après avoir enregistré les paramètres d’autorisation, cliquez sur l’onglet **Détails de l’application** , puis cliquez sur **Modifier > Modifier les détails**.

   ![Modifiez les détails de l’application.](../media/TCimage31.png)

8. Effectuez les tâches suivantes :

   - Cochez la case pour autoriser l’application de connecteur à se connecter à Twitter.

   - Ajoutez l’URI de redirection OAuth au format suivant : **\<connectorserviceuri>/Views/TwitterOAuth**, où la valeur de *connectorserviceuri* est l’URL d’Azure App Service pour votre organisation ; par exemple, https://twitterconnector.azurewebsites.net/Views/TwitterOAuth.

    ![Autoriser l’application de connecteur à se connecter à Twitter et à ajouter l’URI de redirection OAuth.](../media/TCimage32.png)

L’application développeur Twitter est maintenant prête à être utilisée.

## <a name="step-4-configure-the-connector-web-app"></a>Étape 4 : Configurer l’application web du connecteur

1. Accédez à https://\<AzureAppResourceName>.azurewebsites.net (où **AzureAppResourceName** est le nom de votre ressource d’application Azure que vous avez nommée à l’étape 4). Par exemple, si le nom est **twitterconnector**, accédez à https://twitterconnector.azurewebsites.net. La page d’accueil de l’application ressemble à la capture d’écran suivante :

   ![Accédez à la page de ressources de l’application Azure.](../media/FBCimage41.png)

2. Cliquez sur **Configurer** pour afficher une page de connexion.

   ![Cliquez sur Configurer pour afficher la page de connexion.](../media/FBCimage42.png)

3. Dans la zone ID de locataire, tapez ou collez votre ID de locataire (que vous avez obtenu à l’étape 2). Dans la zone de mot de passe, tapez ou collez la clé APISecretKey (obtenue à l’étape 2), puis cliquez sur **Définir les paramètres de configuration** pour afficher la page des détails de configuration.

   ![Connectez-vous à l’aide de l’ID de locataire et de la clé secrète API.](../media/TCimage35.png)

4. Entrez les paramètres de configuration suivants

   - **Clé api Twitter :** Clé API de l’application Twitter que vous avez créée à l’étape 3.

   - **Clé secrète de l’API Twitter :** Clé secrète API pour l’application Twitter que vous avez créée à l’étape 3.

   - **Jeton d’accès Twitter :** Jeton d’accès que vous avez créé à l’étape 3.

   - **Secret du jeton d’accès Twitter :** Secret de jeton d’accès que vous avez créé à l’étape 3.

   - **ID d’application AAD :** ID d’application pour l’application Azure Active Directory que vous avez créée à l’étape 1

   - **Secret d’application AAD :** Valeur du secret APISecretKey que vous avez créé à l’étape 1.

5. Cliquez sur **Enregistrer** pour enregistrer les paramètres du connecteur.

## <a name="step-5-set-up-a-twitter-connector-in-the-compliance-portal"></a>Étape 5 : Configurer un connecteur Twitter dans le portail de conformité

1. Accédez à la portail de conformité Microsoft Purview, puis sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank"> la page **Connecteurs de données**</a.

2. Dans la page **Connecteurs de données** sous **Twitter**, cliquez sur **Afficher**.

3. Sur la page **Twitter** , cliquez sur **Ajouter un connecteur**.

4. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

5. Dans la page **Ajouter des informations d’identification pour votre application de connecteur** , entrez les informations suivantes, puis cliquez sur **Valider la connexion**.

   ![Entrez les informations d’identification de l’application connecteur.](../media/TCimage38.png)

    - Dans la zone **Nom** , tapez un nom pour le connecteur, tel que le **handle d’aide Twitter**.

    - Dans la zone **URL du connecteur** , tapez ou collez l’URL d’Azure App Service ; par exemple `https://twitterconnector.azurewebsites.net`.

    - Dans la zone **Mot de passe, tapez** ou collez la valeur de l’APISecretKey que vous avez créée à l’étape 2.

    - Dans la **zone d’ID Azure App**, tapez ou collez la valeur de l’ID d’application Azure Application (également appelé *ID client*) que vous avez obtenu à l’étape 1.

6. Une fois la connexion validée, cliquez sur **Suivant**.

7. Dans la page **Autoriser Microsoft 365 à importer des données** , tapez ou collez à nouveau apiSecretKey, puis cliquez sur  **Connexion à l’application web**.

8. Cliquez sur **Connexion avec Twitter**.

9. Sur la page de connexion Twitter, connectez-vous à l’aide des informations d’identification du compte Twitter de votre organisation.

   ![Connectez-vous au compte Twitter.](../media/TCimage42.png)

   Une fois que vous vous êtes connecté, la page Twitter affiche le message suivant : « Configuration réussie du travail du connecteur Twitter ».

10. Cliquez sur **Continuer** pour terminer la configuration du connecteur Twitter.

11. Dans la page **Définir les filtres** , vous pouvez appliquer un filtre pour importer initialement des éléments d’un certain âge. Sélectionnez un âge, puis cliquez sur **Suivant**.

12. Dans la page **Choisir l’emplacement de stockage, tapez** l’adresse e-mail de la boîte aux lettres Microsoft 365 vers laquelle les éléments Twitter seront importés, puis cliquez sur **Suivant**.

13. Cliquez sur **Suivant** pour passer en revue les paramètres du connecteur, puis cliquez sur **Terminer** pour terminer la configuration du connecteur.

14. Dans le centre de conformité, accédez à la page **Connecteurs de données** , puis cliquez sur l’onglet **Connecteurs** pour voir la progression du processus d’importation.
