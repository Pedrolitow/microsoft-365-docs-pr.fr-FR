---
title: Déploiement d’un connecteur pour l’archivage des données Twitter
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
ROBOTS: NOINDEX, NOFOLLOW
description: Les administrateurs peuvent configurer un connecteur natif pour importer et archiver des données Twitter vers Microsoft 365. Une fois ces données importées dans Microsoft 365, vous pouvez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer la gouvernance des données Twitter de votre organisation.
ms.openlocfilehash: 0dd996802964b2a2fc58d26e23af57193c89ee8c
ms.sourcegitcommit: 6fc6aaa2b7610e148f41018abd229e3c55b2f3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49619910"
---
# <a name="deploy-a-connector-to-archive-twitter-data"></a>Déploiement d’un connecteur pour l’archivage des données Twitter

Cet article contient le processus étape par étape pour déployer un connecteur qui utilise le service d’importation Office 365 pour importer des données à partir du compte Twitter de votre organisation vers Microsoft 365. Pour une vue d’ensemble de ce processus et une liste des conditions préalables requises pour déployer un connecteur Twitter, reportez-vous à la rubrique [configurer un connecteur pour archiver les données Twitter ](archive-twitter-data-with-sample-connector.md). 

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : créer une application dans Azure Active Directory

1. Accédez à <https://portal.azure.com> et connectez-vous à l’aide des informations d’identification d’un compte d’administrateur général.

   ![Se connecter à Azure](../media/TCimage01.png)

2. Dans le volet de navigation de gauche, cliquez sur **Azure Active Directory**.

   ![Accéder à Azure Active Directory](../media/TCimage02.png)

3. Dans le volet de navigation de gauche, cliquez sur **inscriptions des applications (aperçu)** , puis cliquez sur **nouvelle inscription**.

   ![Créer une nouvelle inscription d’application](../media/TCimage03.png)

4. Inscrivez l’application. Sous **URI de redirection (facultatif)**, sélectionnez **Web** dans la liste déroulante type d’application, puis tapez `https://portal.azure.com` dans la zone de l’URI.

   ![Type https://portal.azure.com de l’URI de redirection ](../media/TCimage04.png)

5. Copiez l’ID d' **application (client)** et l' **ID de répertoire (** client) et enregistrez-les dans un fichier texte ou un autre emplacement sûr. Vous utilisez ces ID dans les étapes ultérieures.

    ![Copier et enregistrer l’ID de l’application et l’ID du répertoire](../media/TCimage05.png)

6. Accédez à **certificats & secrets de la nouvelle application** , puis sous **secrets client** , cliquez sur **nouvelle clé secrète client**.

   ![Créer une clé secrète client](../media/TCimage06.png)

7. Créer une nouvelle clé secrète. Dans la zone Description, tapez le secret, puis choisissez une période d’expiration. 

   ![Tapez le secret et choisissez la période d’expiration.](../media/TCimage08.png)

8. Copiez la valeur de la clé secrète et enregistrez-la dans un fichier texte ou dans un autre emplacement de stockage. Il s’agit de la clé secrète de l’application AAD que vous utilisez dans les étapes ultérieures.

   ![Copier et enregistrer la clé secrète](../media/TCimage09.png)


## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Étape 2 : déployer le service Web connecteur depuis GitHub vers votre compte Azure

1. Accédez à [ce site github](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet) et cliquez sur **déployer vers Azure**.

    ![Accéder à la page d’accueil Azure](../media/FBCimage11.png)

2. Une fois que vous avez cliqué sur **déployer vers Azure**, vous serez redirigé vers un portail Azure avec une page de modèle personnalisé. Renseignez les détails de **base** et les **paramètres** , puis cliquez sur **acheter**.

   ![Cliquez sur créer une ressource et tapez le compte de stockage.](../media/FBCimage12.png)

    - **Abonnement :** Sélectionnez votre abonnement Azure pour lequel vous souhaitez déployer le service Web du connecteur Twitter.
    
    - **Groupe de ressources :** Sélectionnez ou créez un groupe de ressources. Un groupe de ressources est un conteneur qui contient les ressources associées pour une solution Azure.

    - **Emplacement :** Choisissez un emplacement.

    - **Nom de l’application Web :** Fournissez un nom unique pour l’application Web de connecteur. Le nom doit comporter entre 3 et 18 caractères. Ce nom est utilisé pour créer l’URL du service d’application Azure ; par exemple, si vous spécifiez le nom de l’application Web **twitterconnector** , l’URL du service d’application Azure sera **twitterconnector.azurewebsites.net**.
    
    - **tenantId :** ID de client de votre organisation Microsoft 365 que vous avez copié après avoir créé l’application de connecteur Facebook dans Azure Active Directory à l’étape 1.
    
   - **APISecretKey :** Vous pouvez taper n’importe quelle valeur comme clé secrète. Il est utilisé pour accéder à l’application Web de connecteur à l’étape 5.

3. Une fois le déploiement réussi, la page ressemblera à la capture d’écran suivante :

    ![Cliquez sur stockage, puis sur compte de stockage.](../media/FBCimage13.png)

## <a name="step-3-create-the-twitter-app"></a>Étape 3 : créer l’application Twitter

1. Accédez à https://developer.twitter.com , connectez-vous à l’aide des informations d’identification pour le compte de développeur de votre organisation, puis cliquez sur **applications**.

   ![Accédez à https://developer.twitter.com et connectez-vous](../media/TCimage25-5.png)
2. Cliquez sur **créer une application**.
   
   ![Accéder à la page applications pour créer une application](../media/TCimage26.png)

3. Sous **Détails** de l’application, ajoutez des informations sur l’application.

   ![Entrer des informations sur l’application](../media/TCimage27.png)

4. Dans le tableau de bord du développeur Twitter, sélectionnez l’application que vous venez de créer, puis cliquez sur **Détails**.
   
   ![Copier et enregistrer l’ID de l’application](../media/TCimage28.png)

5. Sous l’onglet **clés et jetons** , sous **clés d’API consommateur** , copiez la clé d’API et la clé secrète d’API et enregistrez-les dans un fichier texte ou un autre emplacement de stockage. Ensuite, cliquez sur **créer** pour générer un jeton d’accès et un secret de jeton d’accès et les copier dans un fichier texte ou un autre emplacement de stockage.
   
   ![Copier et enregistrer dans la clé secrète de l’API](../media/TCimage29.png)

   Ensuite, cliquez sur **créer** pour générer un jeton d’accès et un secret de jeton d’accès, puis copiez-les dans un fichier texte ou un autre emplacement de stockage.

6. Cliquez sur l’onglet **autorisations** et configurez les autorisations comme indiqué dans la capture d’écran suivante :

   ![Configurer des autorisations](../media/TCimage30.png)

7. Une fois que vous avez enregistré les paramètres d’autorisation, cliquez sur l’onglet Détails de l' **application** , puis cliquez sur **modifier > modifier les détails**.

   ![Modifier les détails de l’application](../media/TCimage31.png)

8. Effectuez les tâches suivantes :

   - Activez la case à cocher pour autoriser l’application de connecteur à se connecter à Twitter.
   
   - Ajoutez l’URI de redirection OAuth en utilisant le format suivant : **\<connectorserviceuri> /views/TwitterOAuth**, où la valeur de *connectorserviceuri* est l’URL de service d’application Azure pour votre organisation ; par exemple, https://twitterconnector.azurewebsites.net/Views/TwitterOAuth .

    ![Autoriser l’application de connecteur à se connecter à Twitter et ajouter l’URI de redirection OAuth](../media/TCimage32.png)

L’application de développeur Twitter est maintenant prête à être utilisée.

## <a name="step-4-configure-the-connector-web-app"></a>Étape 4 : configuration de l’application Web de connecteur 

1. Accédez à https:// \<AzureAppResourceName> . azurewebsites.net (où **AzureAppResourceName** est le nom de votre ressource d’application Azure que vous avez nommée à l’étape 4). Par exemple, si le nom est **twitterconnector**, accédez à https://twitterconnector.azurewebsites.net . La page d’accueil de l’application se présente comme la capture d’écran suivante :

   ![Accéder à la page des ressources de l’application Azure](../media/FBCimage41.png)

2. Cliquez sur **configurer** pour afficher une page de connexion.

   ![Cliquez sur configurer pour afficher la page de connexion.](../media/FBCimage42.png)

3. Dans la zone ID de locataire, tapez ou collez l’ID de votre client (que vous avez obtenu à l’étape 2). Dans la zone mot de passe, tapez ou collez le APISecretKey (que vous avez obtenu à l’étape 2), puis cliquez sur **définir les paramètres de configuration** pour afficher la page Détails de la configuration.

   ![Se connecter à l’aide de l’ID de client et de la clé secrète d’API](../media/TCimage35.png)

4. Entrez les paramètres de configuration suivants 

   - **Clé de l’API Twitter :** Clé de l’API de l’application Twitter que vous avez créée à l’étape 3.
   
   - **Clé secrète de l’API Twitter :** Clé secrète de l’API pour l’application Twitter que vous avez créée à l’étape 3.
   
   - **Jeton d’accès Twitter :** Le jeton d’accès que vous avez créé à l’étape 3.
   
   - **Jeton d’accès Twitter secret :** Code secret de jeton d’accès que vous avez créé à l’étape 3.
   
   - **ID de l’application AAD :** L’ID d’application pour l’application Azure Active Directory que vous avez créée à l’étape 1
   
   - **Clé secrète de l’application AAD :** Valeur de la clé secrète APISecretKey que vous avez créée à l’étape 1.

5. Cliquez sur **Enregistrer** pour enregistrer les paramètres du connecteur.

## <a name="step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center"></a>Étape 5 : configurer un connecteur Twitter dans le centre de conformité Microsoft 365

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Sur la page **connecteurs de données** , sous **Twitter**, cliquez sur **Afficher**.

3. Sur la page **Twitter** , cliquez sur **Ajouter un connecteur**.

4. Sur la page **conditions de service** , cliquez sur **accepter**.

5. Dans la page **Ajouter des informations d’identification pour votre application connecteur** , entrez les informations suivantes, puis cliquez sur **valider la connexion**.

   ![Entrer les informations d’identification de l’application de connecteur](../media/TCimage38.png)

    - Dans la zone **nom** , tapez un nom pour le connecteur, tel que le **Gestionnaire d’aide Twitter**.
    
    - Dans la zone **URL du connecteur** , tapez ou collez l’URL du service d’application Azure. par exemple `https://twitterconnector.azurewebsites.net` .
    
    - Dans la zone **mot de passe** , tapez ou collez la valeur du APISecretKey que vous avez créé à l’étape 2.
    
    - Dans la zone ID d’application **Azure** , tapez ou collez la valeur de l’ID d’application Azure (également appelé *ID client*) que vous avez obtenu à l’étape 1.

6. Une fois la connexion correctement validée, cliquez sur **suivant**.

7. Sur la page **autoriser Microsoft 365 à importer des données** , tapez ou collez de nouveau le APISecretKey, puis cliquez sur  **application Web de connexion**.

8. Cliquez sur **connexion avec Twitter**.

9. Sur la page de connexion Twitter, connectez-vous à l’aide des informations d’identification du compte Twitter de votre organisation.

   ![Se connecter à un compte Twitter](../media/TCimage42.png)

   Une fois que vous êtes connecté, la page Twitter affiche le message suivant : « travail de connecteur Twitter correctement configuré ».

10. Cliquez sur **Continuer** pour terminer la configuration du connecteur Twitter.

11. Sur la page **définir les filtres** , vous pouvez appliquer un filtre pour importer initialement les éléments qui sont un certain âge. Sélectionnez un âge, puis cliquez sur **suivant**.

12. Dans la page **choisir l’emplacement de stockage** , tapez l’adresse de messagerie de la boîte aux lettres Microsoft 365 dans laquelle les éléments Twitter seront importés, puis cliquez sur **suivant**.

13. Cliquez sur **suivant** pour passer en revue les paramètres du connecteur, puis cliquez sur **Terminer** pour terminer l’installation du connecteur.

14. Dans le centre de conformité, accédez à la page **connecteurs de données** , puis cliquez sur l’onglet **connecteurs** pour voir la progression du processus d’importation.
