---
title: Accès partenaire via les API Microsoft 365 Defender
description: Découvrez comment créer une application AAD pour accéder par programme à Microsoft 365 Defender au nom de vos clients
keywords: partenaire, Access, API, multi-locataire, consentement, jeton d’accès, application
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: eb40d5d2d82f57be225515ad0aa566038397bbbd
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48844983"
---
# <a name="partner-access-through-microsoft-365-defender-apis"></a>Accès partenaire via les API Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

>[!IMPORTANT] 
>Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.


Cette page explique comment créer une application AAD pour accéder par programme à Microsoft 365 Defender au nom de vos clients.

Microsoft 365 Defender expose une grande partie de ses données et actions via un ensemble d’API de programmation. Ces API vous aideront à automatiser les flux de travail et innoveront en fonction des fonctionnalités de Microsoft 365 Defender. L’accès à l’API nécessite l’authentification OAuth 2.0. Pour plus d’informations, reportez-vous au [flux de code d’autorisation OAuth 2,0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En règle générale, vous devez effectuer les étapes suivantes pour utiliser les API :
- Créez une **application AAD mutualisée** .
- Obtenir l’autorisation de l’administrateur de votre client pour accéder aux ressources Microsoft 365 Defender dont il a besoin.
- Obtenir un jeton d’accès à l’aide de cette application.
- Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Les étapes suivantes vous expliquent comment créer une application AAD, obtenir un jeton d’accès à Microsoft 365 Defender et valider le jeton.

## <a name="create-the-multi-tenant-app"></a>Créer l’application mutualisée

1. Ouvrez une session sur votre [client Azure](https://portal.azure.com) avec un utilisateur qui dispose du rôle d' **administrateur général** .

2. Accédez à **Azure Active Directory**  >  **app Registrations**  >  **New Registration**. 

   ![Image de Microsoft Azure et navigation de l’application](../../media/atp-azure-new-app2.png)

3. Dans le formulaire d’inscription :

    - Choisissez un nom pour votre application.

    - Types de comptes pris en charge-comptes dans n’importe quel annuaire d’organisation.

    - URI de redirection-type : Web, URI : https://portal.azure.com

    ![Image de l’inscription de l’application partenaire Microsoft Azure](../../media/atp-api-new-app-partner.png)


4. Autorisez votre application à accéder à Microsoft 365 Defender et attribuez-lui le jeu d’autorisations minimal requis pour terminer l’intégration.

   - Sur la page de votre application, cliquez sur autorisations de l' **API**  >  **Ajouter** une  >  **API que mon organisation utilise** > tapez **Microsoft 365 Defender** et cliquez sur **Microsoft 365 Defender**.

   >[!NOTE]
   >Microsoft 365 Defender n’apparaît pas dans la liste d’origine. Vous devez commencer à écrire son nom dans la zone de texte pour l’afficher.

   ![Image de l’accès à l’API et de la sélection de l’API](../../media/apis-in-my-org-tab.PNG)
   
   ### <a name="request-api-permissions"></a>Demander des autorisations d’API

   Pour déterminer les autorisations qui vous sont nécessaires, consultez la section **autorisations** dans l’API que vous souhaitez appeler. 

   Dans l’exemple suivant, nous allons utiliser l’autorisation **« lire tous les incidents »** :

   Choose **application permissions**  >  **incidents. Read. All** > cliquez sur **Ajouter des autorisations**

   ![Image de l’accès à l’API et de la sélection de l’API](../../media/request-api-permissions.PNG)


5. Cliquez sur **accorder le consentement**

    >[!NOTE]
    >Chaque fois que vous ajoutez une autorisation, vous devez cliquer sur **accorder le consentement** pour que la nouvelle autorisation prenne effet.

    ![Image des autorisations accorder](../../media/grant-consent.PNG)

6. Ajoutez un secret à l’application.

    - Cliquez sur **certificats & secrets** , ajoutez une description à la clé secrète, puis cliquez sur **Ajouter**.

    >[!IMPORTANT]
    > Après avoir sélectionné **Ajouter** , **Copiez la valeur secrète générée**. Vous ne pourrez pas récupérer une fois que vous aurez quitté !

    ![Image de la clé créer une application](../../media/webapp-create-key2.png)

7. Notez l’ID de votre application :

   - Sur la page de votre application, accédez à **vue d’ensemble** et copiez les éléments suivants :

   ![Image de l’ID d’application créé](../../media/app-id.png)

8. Ajoutez l’application au client de votre client.

    Vous avez besoin que votre application soit approuvée dans chaque locataire client sur lequel vous envisagez de l’utiliser. Cela est dû au fait que votre application interagit avec l’application Microsoft 365 Defender au nom de votre client.

    Un utilisateur disposant d’un **administrateur général** du client de votre client doit cliquer sur le lien de consentement et approuver votre application.

    Le lien de consentement est de la forme :

    ```
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
    ```

    Où 00000000-0000-0000-0000-000000000000 doit être remplacé par l’ID de votre application

    Après avoir cliqué sur le lien de consentement, connectez-vous avec l’administrateur général du client du client et acceptez l’application.

    ![Image de consentement](../../media/app-consent-partner.png)

    De plus, vous devrez demander à votre client son ID de client et l’enregistrer pour une utilisation ultérieure lors de l’acquisition du jeton.

- **Terminé!** Vous avez correctement inscrit une application ! 
- Voir des exemples ci-dessous pour l’acquisition et la validation de jetons.

## <a name="get-an-access-token-examples"></a>Obtenir des exemples de jeton d’accès :

>[!NOTE]
> Pour obtenir un jeton d’accès au nom de votre client, utilisez l’ID de client du client sur les acquisitions de jetons suivantes.

<br>Pour plus d’informations sur le jeton AAD, reportez-vous au [didacticiel AAD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds) .

### <a name="using-powershell"></a>Utiliser PowerShell

```
# That code gets the App Context Token and save it to a file named "Latest-token.txt" under the current directory
# Paste below your Tenant ID, App ID and App Secret (App key).

$tenantId = '' ### Paste your tenant ID here
$appId = '' ### Paste your Application ID here
$appSecret = '' ### Paste your Application key here

$resourceAppIdUri = 'https://api.security.microsoft.com'
$oAuthUri = "https://login.windows.net/$TenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$token = $authResponse.access_token
Out-File -FilePath "./Latest-token.txt" -InputObject $token
return $token
```

### <a name="using-c"></a>À l’aide de C# :

>Le code ci-dessous a été testé avec NuGet Microsoft. IdentityModel. clients. ActiveDirectory

- Créer une application console
- Installer NuGet [Microsoft. IdentityModel. clients. ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)
- Ajoutez le suivant à l’aide de

    ```
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

- Copiez/collez le code ci-dessous dans votre application (n’oubliez pas de mettre à jour les 3 variables : ```tenantId, appId, appSecret``` )

    ```
    string tenantId = "00000000-0000-0000-0000-000000000000"; // Paste your own tenant ID here
    string appId = "11111111-1111-1111-1111-111111111111"; // Paste your own app ID here
    string appSecret = "22222222-2222-2222-2222-222222222222"; // Paste your own app secret here for a test, and then store it in a safe place! 

    const string authority = "https://login.windows.net";
    const string mtpResourceId = "https://api.security.microsoft.com";

    AuthenticationContext auth = new AuthenticationContext($"{authority}/{tenantId}/");
    ClientCredential clientCredential = new ClientCredential(appId, appSecret);
    AuthenticationResult authenticationResult = auth.AcquireTokenAsync(mtpResourceId, clientCredential).GetAwaiter().GetResult();
    string token = authenticationResult.AccessToken;
    ```



### <a name="using-curl"></a>Utilisation de la boucle

> [!NOTE]
> La procédure ci-dessous est censée boucler pour Windows est déjà installée sur votre ordinateur.

- Ouvrir une fenêtre de commande
- Définir CLIENT_ID à votre ID d’application Azure
- Définir CLIENT_SECRET à votre code secret d’application Azure
- Définissez TENANT_ID sur l’ID de client Azure du client qui souhaite utiliser votre application pour accéder à l’application Microsoft 365 Defender
- Exécutez la commande ci-dessous :

```
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://api.security.microsoft.com.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Vous obtiendrez une réponse du formulaire :

```
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Valider le jeton

Vérification de la santé pour vérifier que vous avez bien reçu un jeton correct :

- Copier/coller dans [JWT](https://jwt.ms) le jeton que vous obtenez à l’étape précédente afin de le décoder
- Vérifier que vous obtenez une revendication « Roles » avec les autorisations souhaitées
- Dans la capture d’écran ci-dessous, vous pouvez voir un jeton décodé acquis auprès d’une application avec plusieurs autorisations pour Microsoft 365 Defender :
- La revendication « TID » est l’ID de client auquel appartient le jeton.

![Image de la validation du jeton](../../media/webapp-decoded-token.png)

## <a name="use-the-token-to-access-microsoft-365-defender-api"></a>Utiliser le jeton pour accéder à l’API Microsoft 365 Defender

- Sélectionnez l’API que vous souhaitez utiliser, pour plus d’informations, consultez la rubrique [Microsoft 365 Defender API pris en charge](api-supported.md) .
- Définissez l’en-tête Authorization dans la requête HTTP que vous envoyez à « porteur {Token} » (porteur est le modèle d’autorisation)
- Le délai d’expiration du jeton est de 1 heure (vous pouvez envoyer plusieurs demandes avec le même jeton)

- Exemple d’envoi d’une demande pour obtenir une liste d’incidents **à l’aide de C#** 
    ```
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/incidents");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="related-topics"></a>Voir aussi 

- [Accéder aux API Microsoft 365 Defender](api-access.md)
- [Accéder à Microsoft 365 Defender avec le contexte d’application](api-create-app-web.md)
- [Accéder à Microsoft 365 Defender avec le contexte utilisateur](api-create-app-user-context.md)
