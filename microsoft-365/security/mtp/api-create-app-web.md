---
title: Créer une application pour accéder à Microsoft 365 Defender sans utilisateur
description: Découvrez comment créer une application pour accéder à Microsoft 365 Defender sans utilisateur
keywords: application, Access, API, Create
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
ms.openlocfilehash: 446db803cc47bfd519642928a4a0257c4b3d57c8
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48846067"
---
# <a name="create-an-app-to-access-microsoft-365-defender-without-a-user"></a>Créer une application pour accéder à Microsoft 365 Defender sans utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

>[!IMPORTANT] 
>Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Cette page explique comment créer une application pour accéder par programme à Microsoft 365 Defender sans utilisateur. Si vous avez besoin d’un accès par programme à Microsoft 365 Defender au nom d’un utilisateur, reportez-vous à la rubrique [Get Access with User Context](api-create-app-user-context.md). Si vous n’êtes pas certain de l’accès dont vous avez besoin, consultez la rubrique [prise en main](api-access.md).

Microsoft 365 Defender expose une grande partie de ses données et actions via un ensemble d’API de programmation. Ces API vous aideront à automatiser les flux de travail et innoveront en fonction des fonctionnalités de Microsoft 365 Defender. L’accès à l’API nécessite l’authentification OAuth 2.0. Pour plus d’informations, reportez-vous au [flux de code d’autorisation OAuth 2,0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En règle générale, vous devez effectuer les étapes suivantes pour utiliser les API :
- Créez une application Azure Active Directory (Azure AD).
- Obtenir un jeton d’accès à l’aide de cette application.
- Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Cet article explique comment créer une application Azure AD, obtenir un jeton d’accès à Microsoft 365 Defender et valider le jeton.

## <a name="create-an-app"></a>Créer une application

1. Connectez-vous à [Azure](https://portal.azure.com) avec un utilisateur disposant du rôle d' **administrateur général** .

2. Accédez à **Azure Active Directory**  >  **app Registrations**  >  **New Registration**. 

   ![Image de Microsoft Azure et navigation de l’application](../../media/atp-azure-new-app2.png)

3. Dans le formulaire d’inscription, choisissez un nom pour votre application, puis sélectionnez **Enregistrer**.

4. Pour permettre à votre application d’accéder à Microsoft 365 Defender et de lui attribuer des autorisations, dans la page de votre application, sélectionnez autorisations de l' **API**  >  **Ajouter** une  >  **API mon organisation utilise** >, tapez **Microsoft 365 Defender** , puis sélectionnez **Microsoft 365 Defender**.

   > [!NOTE]
   > Microsoft 365 Defender n’apparaît pas dans la liste d’origine. Vous devez commencer à écrire son nom dans la zone de texte pour l’afficher.

   ![Image de l’accès à l’API et de la sélection de l’API](../../media/apis-in-my-org-tab.PNG)

   - Sélectionnez **autorisations d’Application** > choisissez les autorisations appropriées pour votre scénario, par exemple, **incident. Read. All** , puis sélectionnez **Ajouter des autorisations**.

   ![Image de l’accès à l’API et de la sélection de l’API](../../media/request-api-permissions.PNG)

    >[!NOTE]
    >Vous devez sélectionner les autorisations appropriées pour votre scénario, **« lire tous les incidents »** est un exemple. Pour déterminer les autorisations qui vous sont nécessaires, consultez la section **autorisations** dans l’API que vous souhaitez appeler.

5. Sélectionnez **accorder le consentement**.

     > [!NOTE]
     > Chaque fois que vous ajoutez une autorisation, vous devez sélectionner **accorder le consentement** pour que la nouvelle autorisation prenne effet.

    ![Image des autorisations accorder](../../media/grant-consent.PNG)

6. Pour ajouter une clé secrète à l’application, sélectionnez **certificats & secrets** , ajoutez une description à la clé secrète, puis sélectionnez **Ajouter**.

    > [!NOTE]
    > Une fois que vous avez sélectionné **Ajouter** , sélectionnez **copier la valeur secrète générée**. Vous ne pourrez pas récupérer cette valeur une fois que vous aurez quitté.

    ![Image de la clé créer une application](../../media/webapp-create-key2.png)

7. Notez l’ID de votre application et votre ID de client. Sur la page de votre application, accédez à **vue d’ensemble** et copiez ce qui suit.

   ![Image de l’ID d’application créé](../../media/app-and-tenant-ids.png)

8. **Pour les partenaires Microsoft 365 Defender uniquement**. [Suivez les instructions ci-dessous](https://docs.microsoft.com/microsoft-365/security/mtp/api-partner-access). Configurez votre application de sorte qu’elle soit multi-locataire (disponible dans tous les clients après consentement). Cette condition est **requise** pour les applications tierces (par exemple, si vous créez une application conçue pour s’exécuter dans le client de plusieurs clients). Cette opération n’est **pas nécessaire** si vous créez un service que vous souhaitez exécuter uniquement dans votre client (par exemple, si vous créez une application pour votre propre utilisation qui interagira uniquement avec vos propres données). Pour configurer votre application pour qu’elle soit mutualisée :

    - Accédez à **authentification** et ajoutez https://portal.azure.com en tant qu' **URI de redirection**.

    - En bas de la page, sous **types de comptes pris en charge** , sélectionnez les **comptes dans n’importe quel consentement d’application d’annuaire d’organisation** pour votre application mutualisée.

    Vous avez besoin que votre application soit approuvée dans chaque client où vous avez l’intention de l’utiliser. Cela est dû au fait que votre application interagit avec Microsoft 365 Defender au nom de votre client.

    Vous (ou votre client si vous rédigez une application tierce) devez sélectionner le lien de consentement et approuver votre application. L’autorisation doit être faite avec un utilisateur disposant de privilèges d’administrateur dans Active Directory.

    Le lien de consentement est formé comme suit : 

    ```
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
    ```

    Où 00000000-0000-0000-0000-000000000000 est remplacé par votre ID d’application.


**Terminé!** Vous avez correctement inscrit une application ! Voir des exemples ci-dessous pour l’acquisition et la validation de jetons.

## <a name="get-an-access-token"></a>Obtenir un jeton d’accès

Pour plus d’informations sur les jetons Azure AD, consultez le [didacticiel Azure ad](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="use-powershell"></a>Utiliser PowerShell

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

### <a name="use-c"></a>Utiliser C# :

Le code suivant a été testé avec NuGet Microsoft. IdentityModel. clients. ActiveDirectory 3.19.8.

1. Créez une nouvelle application console.
1. Installez NuGet [Microsoft. IdentityModel. clients. ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).
1. Ajoutez les éléments suivants :

    ```
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

1. Copiez et collez le code suivant dans votre application (n’oubliez pas de mettre à jour les trois variables : ```tenantId, appId, appSecret``` ) :

    ```
    string tenantId = "00000000-0000-0000-0000-000000000000"; // Paste your own tenant ID here
    string appId = "11111111-1111-1111-1111-111111111111"; // Paste your own app ID here
    string appSecret = "22222222-2222-2222-2222-222222222222"; // Paste your own app secret here for a test, and then store it in a safe place! 

    const string authority = "https://login.windows.net";
    const string wdatpResourceId = "https://api.security.microsoft.com";

    AuthenticationContext auth = new AuthenticationContext($"{authority}/{tenantId}/");
    ClientCredential clientCredential = new ClientCredential(appId, appSecret);
    AuthenticationResult authenticationResult = auth.AcquireTokenAsync(wdatpResourceId, clientCredential).GetAwaiter().GetResult();
    string token = authenticationResult.AccessToken;
    ```


### <a name="use-python"></a>Utiliser python 

```
import json
import urllib.request
import urllib.parse

tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here

url = "https://login.windows.net/%s/oauth2/token" % (tenantId)

resourceAppIdUri = 'https://api.securitycenter.windows.com'

body = {
    'resource' : resourceAppIdUri,
    'client_id' : appId,
    'client_secret' : appSecret,
    'grant_type' : 'client_credentials'
}

data = urllib.parse.urlencode(body).encode("utf-8")

req = urllib.request.Request(url, data)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
aadToken = jsonResponse["access_token"]
```
### <a name="use-curl"></a>Utilisation de la boucle

> [!NOTE]
> La procédure suivante part du principe que la boucle pour Windows est déjà installée sur votre ordinateur.

1. Ouvrez une invite de commandes et définissez CLIENT_ID à votre ID d’application Azure.
1. Définissez CLIENT_SECRET à la clé secrète de votre application Azure.
1. Définissez TENANT_ID sur l’ID de client Azure du client qui souhaite utiliser votre application pour accéder à Microsoft 365 Defender.
1. Exécutez la commande suivante :

```
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Vous obtiendrez une réponse sous la forme suivante :

```
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Valider le jeton

Assurez-vous que vous avez obtenu le bon jeton :

1. Copiez et collez le jeton que vous avez reçu à l’étape précédente dans [JWT](https://jwt.ms) afin de le décoder.
1. Vérifiez que vous obtenez une revendication « Roles » avec les autorisations souhaitées.
1. Dans l’image suivante, vous pouvez voir un jeton décodé acquis à partir d’une application avec ```Incidents.Read.All``` , ```Incidents.ReadWrite.All``` et des ```AdvancedHunting.Read.All``` autorisations :

![Image de la validation du jeton](../../media/webapp-decoded-token.png)

## <a name="use-the-token-to-access-microsoft-365-defender-api"></a>Utiliser le jeton pour accéder à l’API Microsoft 365 Defender

1. Choisissez l’API que vous souhaitez utiliser. Pour plus d’informations, consultez la rubrique [API Microsoft 365 Defender prises en charge](api-supported.md).

2. Définissez l’en-tête Authorization dans la requête HTTP que vous envoyez à « porteur {Token} » (porteur est le modèle d’autorisation).

3. Le délai d’expiration du jeton est d’une heure. Vous pouvez envoyer plusieurs demandes avec le même jeton.

Voici un exemple d’envoi d’une demande pour obtenir une liste d’incidents **à l’aide de C#** : 

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
