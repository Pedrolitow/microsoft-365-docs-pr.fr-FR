---
title: Déploiement d’un connecteur pour l’archivage des données de pages d’entreprise Facebook
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
ms.collection: M365-security-compliance
ROBOTS: NOINDEX, NOFOLLOW
description: Les administrateurs peuvent configurer un connecteur natif pour importer et archiver des pages Facebook dans Microsoft 365. Une fois ces données importées dans Microsoft 365, vous pouvez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer la gouvernance des données Facebook de votre organisation.
ms.openlocfilehash: 48747dade98701303c4ca6a8c00192ec7faff34a
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42076035"
---
# <a name="deploy-a-connector-to-archive-facebook-business-pages-data"></a>Déploiement d’un connecteur pour l’archivage des données de pages d’entreprise Facebook

Cet article contient le processus étape par étape pour déployer un connecteur qui utilise le service d’importation Microsoft 365 pour importer des données à partir de pages d’entreprise Facebook vers Microsoft 365. Pour une vue d’ensemble de ce processus et une liste des conditions préalables requises pour déployer un connecteur Facebook, reportez-vous à la rubrique [configurer un connecteur pour archiver les données Facebook](archive-facebook-data-with-sample-connector.md). 

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : créer une application dans Azure Active Directory

1. Accédez à <https://portal.azure.com> et connectez-vous à l’aide des informations d’identification d’un compte d’administrateur global Office 365.

    ![Créer une application dans AAD](../media/FBCimage1.png)

2. Dans le volet de navigation de gauche, cliquez sur **Azure Active Directory**.

    ![Cliquez sur Azure Active Directory](../media/FBCimage2.png)

3. Dans le volet de navigation de gauche, cliquez sur **inscriptions des applications (aperçu)** , puis cliquez sur **nouvelle inscription**.

    ![Cliquez sur * * inscriptions des applications (aperçu) * *, puis cliquez sur * * nouvelle inscription * *](../media/FBCimage3.png)

4. Inscrivez l’application. Sous URI de redirection, sélectionnez Web dans la liste déroulante type d' <https://portal.azure.com> application, puis tapez dans la zone de l’URI.

   ![Inscription de l’application](../media/FBCimage4.png)

5. Copiez l’ID d' **application (client)** et l' **ID de répertoire (** client) et enregistrez-les dans un fichier texte ou un autre emplacement sûr. Vous utilisez ces ID dans les étapes ultérieures.

   ![Copiez l’ID de l’application et l’ID du répertoire et enregistrez-les.](../media/FBCimage5.png)

6. Accédez à **certificats & secrets de la nouvelle application.**

   ![Accéder aux certificats & secrets de la nouvelle application](../media/FBCimage6.png)

7. Cliquez sur **nouvelle clé secrète client**

   ![Cliquez sur nouvelle clé secrète client](../media/FBCimage7.png)

8. Créer une nouvelle clé secrète. Dans la zone Description, tapez le secret, puis choisissez une période d’expiration. 

    ![Tapez le secret, puis choisissez une période d’expiration.](../media/FBCimage8.png)

9. Copiez la valeur de la clé secrète et enregistrez-la dans un fichier texte ou dans un autre emplacement de stockage. Il s’agit de la clé secrète de l’application AAD que vous utilisez dans les étapes ultérieures.

   ![Copiez la valeur de la clé secrète et enregistrez-la.](../media/FBCimage9.png)


## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Étape 2 : déployer le service Web connecteur depuis GitHub vers votre compte Azure

1. Accédez à [ce site github](https://github.com/microsoft/m365-sample-connector-csharp-aspnet) et cliquez sur **déployer vers Azure**.

    ![Cliquez sur déployer vers Azure](../media/FBCGithubApp.png)

2. Une fois que vous avez cliqué sur **déployer vers Azure**, vous serez redirigé vers un portail Azure avec une page de modèle personnalisé. Renseignez les détails de **base** et les **paramètres** , puis cliquez sur **acheter**.

    - **Abonnement :** Sélectionnez votre abonnement Azure pour lequel vous souhaitez déployer le service Web du connecteur de pages d’entreprise Facebook.
    
    - **Groupe de ressources :** Sélectionnez ou créez un groupe de ressources. Un groupe de ressources est un conteneur qui contient les ressources associées pour une solution Azure.

    - **Emplacement :** Choisissez un emplacement.

    - **Nom de l’application Web :** Fournissez un nom unique pour l’application Web de connecteur. Le nom doit comporter entre 3 et 18 caractères. Ce nom est utilisé pour créer l’URL du service d’application Azure ; par exemple, si vous spécifiez le nom de l’application Web **fbconnector** , l’URL du service d’application Azure sera **fbconnector.azurewebsites.net**.
    
    - **tenantId :** ID de client de votre organisation Microsoft 365 que vous avez copié après avoir créé l’application de connecteur Facebook dans Azure Active Directory à l’étape 1.
    
   - **APISecretKey :** Vous pouvez taper n’importe quelle valeur comme clé secrète. Il est utilisé pour accéder à l’application Web de connecteur à l’étape 5.
   
     ![Cliquez sur créer une ressource et tapez le compte de stockage.](../media/FBCimage12.png)

3. Une fois le déploiement réussi, la page ressemblera à la capture d’écran suivante :

     ![Cliquez sur stockage, puis sur compte de stockage.](../media/FBCimage13.png)

## <a name="step-3-register-the-facebook-app"></a>Étape 3 : inscrire l’application Facebook

1. Accédez à <https://developers.facebook.com>, connectez-vous à l’aide des informations d’identification du compte pour les pages d’entreprise Facebook de votre organisation, puis cliquez sur **Ajouter une nouvelle application**.

   ![Ajouter une nouvelle application pour la page d’entreprise Facebook](../media/FBCimage25.png)

2. Créer un ID d’application.

   ![Créer un ID d’application](../media/FBCimage26.png)

3. Dans le volet de navigation de gauche, cliquez sur **Ajouter des produits** , puis cliquez sur **configurer** dans la vignette de **connexion Facebook** .

   ![Cliquez sur Ajouter des produits](../media/FBCimage27.png)

4. Sur la page intégration de la connexion Facebook, cliquez sur **Web**.

   ![Cliquez sur Web dans la page intégration de la connexion Facebook](../media/FBCimage28.png)

5. Ajoutez l’URL du service d’application Azure ; par exemple `https://fbconnector.azurewebsites.net`.

   ![Ajouter l’URL du service d’application Azure](../media/FBCimage29.png)

6. Complétez la section démarrage rapide de la configuration de connexion Facebook.

   ![Fin de la section démarrage rapide](../media/FBCimage30.png)

7. Dans le volet de navigation de gauche sous **connexion Facebook**, cliquez sur **paramètres**, puis ajoutez l’URI de redirection OAuth dans la zone **URI de redirection OAuth valide** . Utilisez le format ** \<connectorserviceuri>/views/facebookoauth**, où la valeur de connectorserviceuri est l’URL de service d’application Azure pour votre organisation ; par exemple, `https://fbconnector.azurewebsites.net`.

   ![Ajouter l’URI de redirection OAuth à la zone URI de redirection OAuth valide](../media/FBCimage31.png)

8. Dans le volet de navigation de gauche, cliquez sur **Ajouter des produits** , puis sur **webhooks.** Dans le menu déroulant **page** , cliquez sur **page**. 

   ![Cliquez sur Ajouter des produits, puis cliquez sur * * webhooks](../media/FBCimage32.png)

9. Ajoutez l’URL de rappel des webhooks et ajoutez un jeton de vérification. Le format de l’URL de rappel, utilisez le format ** <connectorserviceuri>/API/FbPageWebhook**, où la valeur de connectorserviceuri est l’URL de service d’application Azure pour votre organisation ; par exemple `https://fbconnector.azurewebsites.net`. 

    Le jeton Verify doit ressembler à un mot de passe fort. Copiez le jeton de vérification dans un fichier texte ou un autre emplacement de stockage.

        ![Add the verify token](../media/FBCimage33.png)

10. Testez et abonnez-vous au point de terminaison pour le flux.

    ![Tester et s’abonner au point de terminaison](../media/FBCimage34.png)

11. Ajoutez une URL de confidentialité, une icône d’application et une utilisation professionnelle. Copiez également l’ID de l’application et la clé secrète de l’application dans un fichier texte ou un autre emplacement de stockage.

    ![Ajouter une URL de confidentialité, une icône d’application et une utilisation professionnelle](../media/FBCimage35.png)

12. Rendez l’application publique.

    ![Rendez l’application publique](../media/FBCimage36.png)

13. Ajouter un utilisateur au rôle administrateur ou testeur.

    ![Ajouter un utilisateur au rôle administrateur ou testeur](../media/FBCimage37.png)

14. Ajoutez l’autorisation d' **accès au contenu public** de la page.

    ![DD autorisation d’accès au contenu public de la page](../media/FBCimage38.png)

15. Ajouter l’autorisation gérer les pages.

    ![Autorisation ajouter des pages](../media/FBCimage39.png)

16. Obtenir l’application examinée par Facebook.

    ![Obtenir l’application examinée par Facebook](../media/FBCimage40.png)

## <a name="step-4-configure-the-connector-web-app"></a>Étape 4 : configuration de l’application Web de connecteur

1. Accédez à https://\<AzureAppResourceName>. azurewebsites.net (où AzureAppResourceName est le nom de votre ressource d’application Azure que vous avez nommée à l’étape 4) par exemple, si le nom est **fbconnector**, accédez à `https://fbconnector.azurewebsites.net`. La page d’accueil de l’application se présente comme la capture d’écran suivante :

   ![Accéder à l’application Web de votre connecteur](../media/FBCimage41.png)

2. Cliquez sur **configurer** pour afficher une page de connexion.
 
   ![Cliquez sur configurer pour afficher une page de connexion.](../media/FBCimage42.png)

3. Dans la zone ID de locataire, tapez ou collez l’ID de votre client (que vous avez obtenu à l’étape 2). Dans la zone mot de passe, tapez ou collez le APISecretKey (que vous avez obtenu à l’étape 2), puis cliquez sur **définir les paramètres de configuration** pour afficher la page Détails de la configuration.

    ![Connectez-vous à l’aide de votre ID de client et de votre mot de passe, puis accédez à la page Détails de configuration](../media/FBCimage43.png)

4. Entrez les paramètres de configuration suivants 

   - **ID d’application Facebook :** ID de l’application Facebook que vous avez obtenue à l’étape 3.
   
   - **Clé secrète de l’application Facebook :** La clé secrète de l’application Facebook que vous avez obtenue à l’étape 3.
   
   - **Jeton de vérification des webhooks Facebook :** Le jeton de vérification que vous avez créé à l’étape 3.
   
   - **ID de l’application AAD :** L’ID d’application pour l’application Azure Active Directory que vous avez créée à l’étape 1.
   
   - **Clé secrète de l’application AAD :** Valeur de la clé secrète APISecretKey que vous avez créée à l’étape 1.

5. Cliquez sur **Enregistrer** pour enregistrer les paramètres du connecteur.

## <a name="step-5-set-up-a-facebook-connector-in-the-microsoft-365-compliance-center"></a>Étape 5 : configurer un connecteur Facebook dans le centre de conformité Microsoft 365

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Dans la page **connecteurs de données (aperçu)** , sous **pages professionnelles Facebook**, cliquez sur **affichage**.

3. Sur la page des **pages d’entreprise Facebook** , cliquez sur **Ajouter un connecteur**.

4. Sur la page **conditions de service** , cliquez sur **accepter**.

5.  Dans la page **Ajouter des informations d’identification pour votre application connecteur** , entrez les informations suivantes, puis cliquez sur **valider la connexion**.

    ![Entrer les informations d’identification de l’application de connecteur](../media/TCimage38.png)

    - Dans la zone **nom** , tapez un nom pour le connecteur, par exemple **page Facebook News**.
    
    - Dans la zone **URL de connexion** , tapez ou collez l’URL du service d’application Azure. par exemple `https://fbconnector.azurewebsites.net`.
    
    - Dans la zone **mot de passe** , tapez ou collez la valeur du APISecretKey que vous avez ajouté à l’étape 2.
    
    - Dans la zone ID d’application **Azure** , tapez ou collez la valeur de l’ID d’application (client) également appelé ID d’application AAD que vous avez créé à l’étape 1.
 
6. Une fois la connexion correctement validée, cliquez sur **suivant**.

7. Sur la page **autoriser Microsoft 365 à importer des données** , tapez ou collez de nouveau le APISecretKey, puis cliquez sur **application Web de connexion**.

8. Sur la page **configurer l’application Facebook Connector** , cliquez sur **connexion avec Facebook** et connectez-vous à l’aide des informations d’identification du compte pour les pages d’entreprise Facebook de votre organisation. Assurez-vous que le compte Facebook auquel vous vous êtes connecté se voit attribuer le rôle d’administrateur pour les pages d’entreprise Facebook de votre organisation.

   ![Se connecter avec Facebook](../media/FBCimage50.png)

9. Une liste des pages d’entreprise gérées par le compte Facebook auquel vous vous êtes connecté s’affiche. Sélectionnez la page à archiver, puis cliquez sur **suivant**.

    ![Sélectionnez la page d’entreprise que vous souhaitez archiver](../media/FBCimage52.png)

10. Cliquez sur **Continuer** pour quitter le programme d’installation de l’application de service connecteur.

11. Sur la page **définir les filtres** , vous pouvez appliquer un filtre pour importer initialement les éléments qui sont un certain âge. Sélectionnez un âge, puis cliquez sur **suivant**.

12. Dans la page **choisir l’emplacement de stockage** , tapez l’adresse de messagerie de la boîte aux lettres Microsoft 365 dans laquelle les éléments Facebook seront importés, puis cliquez sur **suivant**.

13. Sur l' **autorisation fournir un administrateur**, cliquez sur **accorder le consentement** , puis suivez les étapes. Vous devez être un administrateur général pour accorder le consentement du service d’importation Office 365 pour accéder aux données de votre organisation.

14. Cliquez sur **suivant** pour passer en revue les paramètres du connecteur, puis cliquez sur **Terminer** pour terminer l’installation du connecteur.

15. Dans le centre de conformité, accédez à la page **connecteurs de données** , puis cliquez sur l’onglet **connecteurs** pour voir la progression du processus d’importation.
