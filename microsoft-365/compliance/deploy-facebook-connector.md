---
title: Déployer un connecteur pour archiver les données des pages Facebook Business
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ROBOTS: NOINDEX, NOFOLLOW
description: Les administrateurs peuvent configurer un connecteur natif pour importer et archiver des pages Facebook Business Microsoft 365. Une fois ces données importées dans Microsoft 365, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer la gouvernance des données Facebook de votre organisation.
ms.openlocfilehash: 1707236a889d03f272c5cce527245cf2a83f8949
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60170834"
---
# <a name="deploy-a-connector-to-archive-facebook-business-pages-data"></a>Déployer un connecteur pour archiver les données des pages Facebook Business

Cet article contient le processus pas à pas pour déployer un connecteur qui utilise le service d’importation Office 365 pour importer des données à partir de pages Facebook Business vers Microsoft 365. Pour une vue d’ensemble de ce processus et une liste des conditions préalables requises pour déployer un connecteur Facebook, voir Configurer un connecteur pour archiver les [données Facebook.](archive-facebook-data-with-sample-connector.md)

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

1. Go to <https://portal.azure.com> and sign in using the credentials of a global admin account.

    ![Créez une application dans AAD.](../media/FBCimage1.png)

2. Dans le volet de navigation gauche, cliquez sur **Azure Active Directory**.

    ![Cliquez sur Azure Active Directory.](../media/FBCimage2.png)

3. Dans le volet de navigation de gauche, cliquez sur **Inscriptions d’applications (prévisualisation),** puis sur **Nouvelle inscription.**

    ![Cliquez sur **Inscriptions d’applications (prévisualisation)**, puis sur **Nouvelle inscription**.](../media/FBCimage3.png)

4. Inscrivez l’application. Sous URI de redirection, sélectionnez Web dans la liste de listes listes des types d’application, puis tapez dans la zone de <https://portal.azure.com> l’URI.

   ![Inscrivez l’application.](../media/FBCimage4.png)

5. Copiez **l’ID d’application (client)** et l’ID d’annuaire **(client)** et enregistrez-les dans un fichier texte ou un autre emplacement sûr. Vous utiliserez ces ID dans les étapes ultérieures.

   ![Copiez l’ID d’application et l’ID d’annuaire et enregistrez-les.](../media/FBCimage5.png)

6. Go to **Certificates & secrets for the new app.**

   ![Go to Certificates & secrets for the new app.](../media/FBCimage6.png)

7. Cliquez **sur Nouvelle secret client**

   ![Cliquez sur Nouvelle secret client.](../media/FBCimage7.png)

8. Créez une nouvelle secret. Dans la zone de description, tapez le secret, puis choisissez une période d’expiration.

    ![Tapez la secret, puis choisissez une période d’expiration.](../media/FBCimage8.png)

9. Copiez la valeur de la secret et enregistrez-la dans un fichier texte ou un autre emplacement de stockage. Il s’agit de la question secrète de l’application AAD que vous utiliserez dans les étapes ultérieures.

   ![Copiez la valeur de la secret et enregistrez-la.](../media/FBCimage9.png)

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Étape 2 : Déployer le service web connecteur à partir de GitHub votre compte Azure

1. Go to [this GitHub site](https://github.com/microsoft/m365-sample-connector-csharp-aspnet) and click Deploy to **Azure**.

    ![Cliquez sur Déployer sur Azure.](../media/FBCGithubApp.png)

2. Une fois que **vous avez cliqué sur Déployer** vers Azure, vous êtes redirigé vers un portail Azure avec une page de modèle personnalisée. Remplissez les **informations de base** et **Paramètres,** puis cliquez sur **Acheter.**

   - **Abonnement :** Sélectionnez votre abonnement Azure sur qui vous souhaitez déployer le service web connecteur de pages Facebook Business.

   - **Groupe de ressources :** Choisissez ou créez un groupe de ressources. Un groupe de ressources est un conteneur qui contient des ressources associées pour une solution Azure.

   - **Emplacement :** Choisissez un emplacement.

   - **Nom de l’application web :** Fournissez un nom unique pour l’application web du connecteur. La longueur du nom doit être de 3 à 18 caractères. Ce nom est utilisé pour créer l’URL du service d’application Azure ; par exemple, si vous fournissez le nom de l’application Web **fbconnector,** l’URL du service d’application Azure **sera fbconnector.azurewebsites.net**.

   - **tenantId :** ID de client de votre organisation Microsoft 365 que vous avez copiée après la création de l’application connecteur Facebook à Azure Active Directory l’étape 1.

   - **APISecretKey :** Vous pouvez taper n’importe quelle valeur comme secret. Il permet d’accéder à l’application web de connecteur à l’étape 5.

     ![Cliquez sur Créer un compte de stockage de ressource et de type.](../media/FBCimage12.png)

3. Une fois le déploiement réussi, la page ressemble à la capture d’écran suivante :

   ![Cliquez Stockage puis cliquez sur Stockage compte.](../media/FBCimage13.png)

## <a name="step-3-register-the-facebook-app"></a>Étape 3 : Inscrire l’application Facebook

1. Go to <https://developers.facebook.com> , log in using the credentials for the account for your organization’s Facebook Business pages, and then click Add New **App**.

   ![Ajoutez une nouvelle page d’application pour Les entreprises Facebook.](../media/FBCimage25.png)

2. Créez un ID d’application.

   ![Créez un ID d’application.](../media/FBCimage26.png)

3. Dans le volet de navigation de gauche, cliquez sur Ajouter des **produits,** puis cliquez sur **Configurer** dans la vignette de **connexion Facebook.**

   ![Cliquez sur Ajouter des produits.](../media/FBCimage27.png)

4. Dans la page Intégrer la connexion Facebook, cliquez sur **Web.**

   ![Cliquez sur Le Web sur la page Intégrer la connexion à Facebook.](../media/FBCimage28.png)

5. Ajouter l’URL du service d’application Azure ; par `https://fbconnector.azurewebsites.net` exemple.

   ![Ajoutez l’URL du service d’application Azure.](../media/FBCimage29.png)

6. Complétez la section Démarrage rapide de la configuration de la connexion à Facebook.

   ![Terminez la section Démarrage rapide.](../media/FBCimage30.png)

7. Dans le volet de navigation de gauche sous **Connexion Facebook,** cliquez sur **Paramètres** et ajoutez l’URI de redirection OAuth dans la zone URI de redirection **OAuth** valide. Utilisez le format **\<connectorserviceuri> /Views/FacebookOAuth**, où la valeur de connectorserviceuri est l’URL du service d’application Azure pour votre organisation ; par exemple, `https://fbconnector.azurewebsites.net` .

   ![Ajoutez l’URI de redirection OAuth à la zone URI de redirection OAuth valide.](../media/FBCimage31.png)

8. Dans le volet de navigation de gauche, cliquez sur **Ajouter des** produits, puis sur **Webhooks.** Dans le menu déroulant **Page,** cliquez sur **Page.**

   ![Cliquez sur Ajouter des produits, puis sur **Webhooks.](../media/FBCimage32.png)

9. Ajoutez l’URL de rappel webhooks et ajoutez un jeton de vérification. Le format de l’URL de rappel, utilisez le format , où la valeur pour connectorserviceuri est l’URL du service d’application Azure pour `<connectorserviceuri>/api/FbPageWebhook` votre organisation ; par exemple `https://fbconnector.azurewebsites.net` .

   Le jeton de vérification doit être similaire à un mot de passe fort. Copiez le jeton de vérification dans un fichier texte ou un autre emplacement de stockage.

   ![Ajoutez le jeton de vérification.](../media/FBCimage33.png)

10. Testez et abonnez-vous au point de terminaison pour le flux.

    ![Testez et abonnez-vous au point de terminaison.](../media/FBCimage34.png)

11. Ajoutez une URL de confidentialité, une icône d’application et une utilisation professionnelle. Copiez également l’ID d’application et la secret de l’application dans un fichier texte ou un autre emplacement de stockage.

    ![Ajoutez une URL de confidentialité, une icône d’application et une utilisation professionnelle.](../media/FBCimage35.png)

12. Rendez l’application publique.

    ![Rendez l’application publique.](../media/FBCimage36.png)

13. Ajoutez un utilisateur au rôle d’administrateur ou de testeur.

    ![Ajoutez un utilisateur au rôle d’administrateur ou de testeur.](../media/FBCimage37.png)

14. Ajoutez **l’autorisation d’accès au contenu public de** la page.

    ![dd l’autorisation d’accès au contenu public de la page.](../media/FBCimage38.png)

15. Ajouter l’autorisation Gérer les pages.

    ![Ajouter l’autorisation Gérer les pages.](../media/FBCimage39.png)

16. Faites passer l’application en revue par Facebook.

    ![Faites passer l’application en revue par Facebook.](../media/FBCimage40.png)

## <a name="step-4-configure-the-connector-web-app"></a>Étape 4 : Configurer l’application web du connecteur

1. Go to `https://<AzureAppResourceName>.azurewebsites.net` (where AzureAppResourceName is the name of your Azure app resource that you named in Step 4). Par exemple, si le nom est **fbconnector**, allez à `https://fbconnector.azurewebsites.net` . La page d’accueil de l’application ressemblera à la capture d’écran suivante :

   ![Go to you connector web app.](../media/FBCimage41.png)

2. Cliquez **sur Configurer pour** afficher une page de signature.

   ![Cliquez sur Configurer pour afficher une page de signature.](../media/FBCimage42.png)

3. Dans la zone ID de locataire, tapez ou collez votre ID de client (que vous avez obtenu à l’étape 2). Dans la zone de mot de passe, tapez ou collez la clé APISecretKey (obtenue à l’étape 2), puis cliquez sur Définir la configuration **Paramètres** pour afficher la page de détails de configuration.

    ![Connectez-vous à l’aide de votre ID de client et de votre mot de passe, puis allez à la page des détails de configuration.](../media/FBCimage43.png)

4. Entrez les paramètres de configuration suivants

   - **ID d’application Facebook :** ID d’application pour l’application Facebook obtenue à l’étape 3.

   - **Secret d’application Facebook :** Secret d’application pour l’application Facebook que vous avez obtenu à l’étape 3.

   - **Les webhooks Facebook vérifient le jeton :** Jeton de vérification que vous avez créé à l’étape 3.

   - **ID d’application AAD :** ID de l’application Azure Active Directory que vous avez créée à l’étape 1.

   - **Secret d’application AAD :** Valeur de la clé secrète APISecretKey que vous avez créée à l’étape 1.

5. Cliquez **sur Enregistrer** pour enregistrer les paramètres du connecteur.

## <a name="step-5-set-up-a-facebook-connector-in-the-microsoft-365-compliance-center"></a>Étape 5 : Configurer un connecteur Facebook dans le Centre de conformité Microsoft 365

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and then click Data **connectors** in the left nav.

2. Dans la page **Connecteurs de données** sous **les pages Facebook Entreprise,** cliquez sur **Afficher**.

3. Dans la **page Des pages d’entreprise Facebook,** cliquez **sur Ajouter un connecteur.**

4. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

5. Dans la page **Ajouter des informations d’identification pour votre** application de connecteur, entrez les informations suivantes, puis cliquez sur Valider la **connexion.**

   ![Entrez les informations d’identification de l’application connecteur.](../media/TCimage38.png)

   - Dans la **zone** Nom, tapez un nom pour le connecteur, tel que la **page d’actualités facebook.**

   - Dans la **zone URL de** connexion, tapez ou collez l’URL du service d’application Azure . par `https://fbconnector.azurewebsites.net` exemple.

   - Dans la **zone Mot** de passe, tapez ou collez la valeur de l’APISecretKey que vous avez ajoutée à l’étape 2.

   - Dans la **zone ID** d’application Azure, tapez ou collez la valeur de l’ID d’application (client) également appelé ID d’application AAD que vous avez créé à l’étape 1.

6. Une fois la connexion validée, cliquez sur **Suivant.**

7. Dans la page **Autoriser Microsoft 365** importer des données, tapez ou collez de nouveau l’APISecretKey, puis cliquez sur Login **web app**.

8. Dans la page **Configurer l’application connecteur Facebook,** cliquez sur Se connecter avec **Facebook** et connectez-vous à l’aide des informations d’identification du compte pour les pages Facebook Business de votre organisation. Assurez-vous que le compte Facebook à qui vous vous êtes connecté se voit attribuer le rôle d’administrateur pour les pages Facebook Business de votre organisation.

   ![Connectez-vous avec Facebook.](../media/FBCimage50.png)

9. Une liste des pages d’entreprise gérées par le compte Facebook à qui vous vous êtes connecté s’affiche. Sélectionnez la page à archiver, puis cliquez sur **Suivant.**

   ![Sélectionnez la page d’entreprise de l’organisation que vous souhaitez archiver.](../media/FBCimage52.png)

10. Cliquez **sur Continuer** pour quitter la configuration de l’application de service connecteur.

11. Dans la page **Définir les filtres,** vous pouvez appliquer un filtre pour importer initialement des éléments d’un certain âge. Sélectionnez un âge, puis cliquez sur **Suivant**.

12. Dans la page **Choisir** l’emplacement de stockage, tapez l’adresse de messagerie Microsoft 365 boîte aux lettres dans Microsoft 365 vers qui les éléments Facebook seront importés, puis cliquez sur **Suivant**.

13. Cliquez **sur Suivant** pour passer en revue les paramètres du connecteur, puis cliquez sur **Terminer** pour terminer la configuration du connecteur.

14. Dans le centre de conformité, allez à la page **Connecteurs** de données, puis cliquez sur l’onglet **Connecteurs** pour voir la progression du processus d’importation.
