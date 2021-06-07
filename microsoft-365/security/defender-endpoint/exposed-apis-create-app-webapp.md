---
title: Créer une application pour accéder à Microsoft Defender pour le point de terminaison sans utilisateur
ms.reviewer: ''
description: Découvrez comment concevoir une application web pour obtenir un accès par programmation à Microsoft Defender pour endpoint sans utilisateur.
keywords: api, api de graphique, api pris en charge, acteur, alertes, appareil, utilisateur, domaine, ip, fichier, recherche avancée, requête
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 4742a32fd899f41d4e7772c52415891cdd8895bf
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52769520"
---
# <a name="create-an-app-to-access-microsoft-defender-for-endpoint-without-a-user"></a>Créer une application pour accéder à Microsoft Defender pour le point de terminaison sans utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Cette page explique comment créer une application pour obtenir l’accès par programme à Defender for Endpoint sans utilisateur. Si vous avez besoin d’un accès par programme à Defender for Endpoint pour le compte d’un utilisateur, voir [Obtenir l’accès avec le contexte utilisateur.](exposed-apis-create-app-nativeapp.md) Si vous n’êtes pas sûr de l’accès dont vous avez besoin, [consultez La mise en place.](apis-intro.md)

Microsoft Defender pour point de terminaison expose la plupart de ses données et actions par le biais d’un ensemble d’API de programmation. Ces API vous aideront à automatiser les flux de travail et à innover en fonction des fonctionnalités de Defender for Endpoint. L’accès à l’API nécessite une authentification OAuth2.0. Pour plus d’informations, [voir code d’autorisation OAuth 2.0 Flow](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En règle générale, vous devez suivre les étapes suivantes pour utiliser les API :
- Créez une Azure Active Directory application (Azure AD).
- Obtenez un jeton d’accès à l’aide de cette application.
- Utilisez le jeton pour accéder à l’API Defender for Endpoint.

Cet article explique comment créer une application Azure AD, obtenir un jeton d’accès à Microsoft Defender pour le point de terminaison et valider le jeton.

## <a name="create-an-app"></a>Créer une application

1. Connectez-vous [à Azure](https://portal.azure.com) avec un utilisateur qui a le **rôle Administrateur** général.

2. Accédez à **Azure Active Directory**  >  **Inscription de l’application Nouvelle**  >  **inscription.** 

   ![Image de la Microsoft Azure et de la navigation vers l’inscription de l’application](images/atp-azure-new-app2.png)

3. Dans le formulaire d’inscription, choisissez un nom pour votre application, puis sélectionnez **Enregistrer**.

4. Pour permettre à votre application d’accéder à Defender pour le point de terminaison et de lui attribuer l’autorisation « Lire toutes les **alertes** ». Sur votre page d’application, sélectionnez **Autorisations API** Ajouter des API d’autorisation que mon organisation utilise  >    >   >, tapez **WindowsDefenderATP,** puis sélectionnez **WindowsDefenderATP**.

   > [!NOTE]
   > *WindowsDefenderATP* n’apparaît pas dans la liste d’origine. Commencez à écrire son nom dans la zone de texte pour le voir apparaître.

   ![ajouter une autorisation](images/add-permission.png)

   - Sélectionnez **Autorisations**  >  **d’application Alert.Read.All,** puis **sélectionnez Ajouter des autorisations.**

   ![autorisation d’application](images/application-permissions.png)

     Vous devez sélectionner les autorisations pertinentes. « Lire toutes les alertes » n’est qu’un exemple. Par exemple :

     - Pour [exécuter des requêtes avancées,](run-advanced-query-api.md)sélectionnez l’autorisation « Exécuter des requêtes avancées ».
     - Pour [isoler un appareil,](isolate-machine.md)sélectionnez l’autorisation « Isoler l’ordinateur ».
     - Pour déterminer l’autorisation qui vous est nécessaire, regardez la section **Autorisations** de l’API que vous souhaitez appeler.

5. Sélectionnez **Accorder le consentement.**

     > [!NOTE]
     > Chaque fois que vous ajoutez une autorisation, vous devez sélectionner **Accorder le consentement** pour que la nouvelle autorisation prenne effet.

    ![Accorder des autorisations](images/grant-consent.png)

6. Pour ajouter une secret à l’application, sélectionnez **Certificats & secrets,** ajoutez une description à la secret, puis sélectionnez **Ajouter**.

    > [!NOTE]
    > Après avoir sélectionné **Ajouter,** **sélectionnez copier la valeur de secret générée.** Vous ne pourrez pas récupérer cette valeur après votre départ.

    ![Image de la clé de création d’application](images/webapp-create-key2.png)

7. Notez votre ID d’application et votre ID de client. Dans la page de votre application, allez à **Vue d’ensemble** et copiez ce qui suit.

   ![Image de l’ID d’application créé](images/app-and-tenant-ids.png)

8. **Pour Microsoft Defender pour les partenaires de point de terminaison uniquement.** Définissez votre application pour qu’elle soit multi-locataire (disponible dans tous les locataires après consentement). Cette étape **est requise** pour les applications tierces (par exemple, si vous créez une application destinée à s’exécuter dans le client de plusieurs clients). Cela **n’est** pas obligatoire si vous créez un service que vous souhaitez exécuter uniquement dans votre client (par exemple, si vous créez une application pour votre propre utilisation qui interagit uniquement avec vos propres données). Pour définir votre application pour qu’elle soit multi-locataire :

    - Go to **Authentication**, and add `https://portal.azure.com` as the Redirect **URI**.

    - En bas de la page, sous **Types** de comptes pris en charge, sélectionnez les comptes dans n’importe quel consentement d’application  d’annuaire d’organisation pour votre application multi-locataire.

    Votre application doit être approuvée dans chaque client où vous avez l’intention de l’utiliser. En effet, votre application interagit avec Defender for Endpoint pour le compte de votre client.

    Vous (ou votre client si vous écrivez une application tierce) devez sélectionner le lien de consentement et approuver votre application. Le consentement doit être effectué avec un utilisateur qui dispose de privilèges d’administration dans Active Directory.

    Le lien de consentement est constitué comme suit : 

    ```
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
    ```

    Où 00000000-0000-0000-0000-00000000000000 est remplacé par votre ID d’application.


**Terminé !** Vous avez réussi à inscrire une application ! Voir les exemples ci-dessous pour l’acquisition et la validation des jetons.

## <a name="get-an-access-token"></a>Obtenir un jeton d’accès

Pour plus d’informations sur les jetons Azure AD, voir le [didacticiel Azure AD.](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds)

### <a name="use-powershell"></a>Utiliser PowerShell

```powershell
# This script acquires the App Context Token and stores it in the variable $token for later use in the script.
# Paste your Tenant ID, App ID, and App Secret (App key) into the indicated quotes below.

$tenantId = '' ### Paste your tenant ID here
$appId = '' ### Paste your Application ID here
$appSecret = '' ### Paste your Application key here

$resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$token = $authResponse.access_token
```

### <a name="use-c"></a>Utilisez C# :

Le code suivant a été testé avec NuGet Microsoft.IdentityModel.Clients.ActiveDirectory 3.19.8.

1. Créez une application console.
1. Installez NuGet [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).
1. Ajoutez les valeurs suivantes :

    ```
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

1. Copiez et collez le code suivant dans votre application (n’oubliez pas de mettre à jour les trois variables ```tenantId, appId, appSecret``` :

    ```
    string tenantId = "00000000-0000-0000-0000-000000000000"; // Paste your own tenant ID here
    string appId = "11111111-1111-1111-1111-111111111111"; // Paste your own app ID here
    string appSecret = "22222222-2222-2222-2222-222222222222"; // Paste your own app secret here for a test, and then store it in a safe place! 

    const string authority = "https://login.microsoftonline.com";
    const string wdatpResourceId = "https://api.securitycenter.microsoft.com";

    AuthenticationContext auth = new AuthenticationContext($"{authority}/{tenantId}/");
    ClientCredential clientCredential = new ClientCredential(appId, appSecret);
    AuthenticationResult authenticationResult = auth.AcquireTokenAsync(wdatpResourceId, clientCredential).GetAwaiter().GetResult();
    string token = authenticationResult.AccessToken;
    ```


### <a name="use-python"></a>Utiliser Python

Voir [Obtenir un jeton à l’aide de Python.](run-advanced-query-sample-python.md#get-token)

### <a name="use-curl"></a>Utilisation de l’err.

> [!NOTE]
> La procédure suivante part du principe que La Windows est déjà installée sur votre ordinateur.

1. Ouvrez une invite de commandes et définissez CLIENT_ID sur votre ID d’application Azure.
1. Définissez CLIENT_SECRET sur votre secret d’application Azure.
1. Définissez TENANT_ID sur l’ID de client Azure du client qui souhaite utiliser votre application pour accéder à Defender for Endpoint.
1. Exécutez la commande suivante :

```
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Vous recevez une réponse sous la forme suivante :

```
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Valider le jeton

Assurez-vous que vous avez reçu le jeton correct :

1. Copiez et collez le jeton obtenu à l’étape précédente dans [JWT](https://jwt.ms) afin de le décoder.
1. Vérifier que vous obtenez une revendication « rôles » avec les autorisations souhaitées
1. Dans l’image suivante, vous pouvez voir un jeton décodé acquis à partir d’une application avec des autorisations pour tous les rôles de Microsoft Defender for Endpoint :

![Image de validation de jeton](images/webapp-decoded-token.png)

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Utiliser le jeton pour accéder à l’API Microsoft Defender for Endpoint

1. Choisissez l’API que vous souhaitez utiliser. Pour plus d’informations, [voir Supported Defender pour les API de point de terminaison.](exposed-apis-list.md)
1. Définissez l’en-tête d’autorisation dans la demande http que vous envoyez à « Bearer {token} » (le porteur est le schéma d’autorisation).
1. Le délai d’expiration du jeton est d’une heure. Vous pouvez envoyer plusieurs demandes avec le même jeton.

Voici un exemple d’envoi d’une demande pour obtenir une liste d’alertes à l’aide **C#**: 
```
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
```

## <a name="see-also"></a>Voir aussi
- [API prises en charge Microsoft Defender pour point de terminaison](exposed-apis-list.md).
- [Accéder à Microsoft Defender pour le point de terminaison au nom d’un utilisateur](exposed-apis-create-app-nativeapp.md)
