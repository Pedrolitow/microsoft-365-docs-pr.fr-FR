---
title: Créer une application pour accéder à Microsoft Defender pour point de terminaison sans utilisateur
ms.reviewer: ''
description: Découvrez comment concevoir une application web pour obtenir un accès programmatique à Microsoft Defender pour point de terminaison sans utilisateur.
keywords: api, api graphe, api prises en charge, acteur, alertes, appareil, utilisateur, domaine, ip, fichier, repérage avancé, requête
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: ca448d64b544e7c7a390b243c77a878dd9afc55a
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67324492"
---
# <a name="create-an-app-to-access-microsoft-defender-for-endpoint-without-a-user"></a>Créer une application pour accéder à Microsoft Defender pour point de terminaison sans utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/index.yml)

> [!IMPORTANT]
> Les fonctionnalités de chasse avancées ne sont pas incluses dans Defender entreprise. Consultez [Comparer les Microsoft Defender pour entreprises à Microsoft Defender pour point de terminaison plans 1 et 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Cette page explique comment créer une application pour obtenir un accès programmatique à Defender pour point de terminaison sans utilisateur. Si vous avez besoin d’un accès programmatique à Defender pour point de terminaison pour le compte d’un utilisateur, consultez [Obtenir l’accès avec le contexte utilisateur](exposed-apis-create-app-nativeapp.md). Si vous n’êtes pas sûr de l’accès dont vous avez besoin, consultez [Prise en main](apis-intro.md).

Microsoft Defender pour point de terminaison expose une grande partie de ses données et actions par le biais d’un ensemble d’API programmatiques. Ces API vous aideront à automatiser les flux de travail et à innover en fonction des fonctionnalités de Defender pour point de terminaison. L’accès à l’API nécessite l’authentification OAuth2.0. Pour plus d’informations, consultez [le flux de code d’autorisation OAuth 2.0](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En général, vous devez effectuer les étapes suivantes pour utiliser les API :
- Créez une application Azure Active Directory (Azure AD).
- Obtenez un jeton d’accès à l’aide de cette application.
- Utilisez le jeton pour accéder à l’API Defender pour point de terminaison.

Cet article explique comment créer une application Azure AD, obtenir un jeton d’accès pour Microsoft Defender pour point de terminaison et valider le jeton.

## <a name="create-an-app"></a>Créer une application

1. Connectez-vous à [Azure](https://portal.azure.com) avec un utilisateur qui a le rôle **Administrateur général** .

2. Accédez à **Azure Active Directory** \> **inscriptions d'applications** \> **Nouvelle inscription**. 

    :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Volet d’inscription d’application" lightbox="images/atp-azure-new-app2.png":::

3. Dans le formulaire d’inscription, choisissez un nom pour votre application, puis **sélectionnez Inscrire**.

4. Pour permettre à votre application d’accéder à Defender pour point de terminaison et de lui attribuer l’autorisation **« Lire toutes les alertes »,** dans la page de votre application, sélectionnez **Autorisations d’API Ajouter des** \> API d’autorisation  \> que **mon organisation utilise** >, tapez **WindowsDefenderATP**, puis sélectionnez **WindowsDefenderATP**.

   > [!NOTE]
   > *WindowsDefenderATP* n’apparaît pas dans la liste d’origine. Commencez à écrire son nom dans la zone de texte pour l’afficher.

   :::image type="content" source="images/add-permission.png" alt-text="Volet Autorisations de l’API" lightbox="images/add-permission.png":::

   Sélectionnez **Autorisations** \> d’application **Alert.Read.All**, puis sélectionnez **Ajouter des autorisations**.

   :::image type="content" source="images/application-permissions.png" alt-text="Volet d’informations sur les autorisations d’application" lightbox="images/application-permissions.png":::

     Vous devez sélectionner les autorisations appropriées. « Lire toutes les alertes » n’est qu’un exemple. Par exemple :

     - Pour [exécuter des requêtes avancées](run-advanced-query-api.md), sélectionnez l’autorisation « Exécuter des requêtes avancées ».
     - Pour [isoler un appareil](isolate-machine.md), sélectionnez l’autorisation « Isoler l’ordinateur ».
     - Pour déterminer l’autorisation dont vous avez besoin, consultez la section **Autorisations** de l’API que vous souhaitez appeler.

5. Sélectionnez **Accorder le consentement**.

     > [!NOTE]
     > Chaque fois que vous ajoutez une autorisation, vous devez sélectionner **Accorder le consentement** pour que la nouvelle autorisation prenne effet.

    :::image type="content" source="images/grant-consent.png" alt-text="Page Accorder des autorisations" lightbox="images/grant-consent.png":::

6. Pour ajouter un secret à l’application, sélectionnez **Certificats & secrets**, ajoutez une description au secret, puis sélectionnez **Ajouter**.

    > [!NOTE]
    > Après avoir sélectionné **Ajouter**, sélectionnez **copier la valeur de secret générée**. Vous ne pourrez pas récupérer cette valeur après votre départ.

      :::image type="content" source="images/webapp-create-key2.png" alt-text="Option créer une application" lightbox="images/webapp-create-key2.png":::

7. Notez votre ID d’application et votre ID de locataire. Dans la page de votre application, accédez à **Vue d’ensemble** et copiez ce qui suit.

   :::image type="content" source="images/app-and-tenant-ids.png" alt-text="ID d’application et de locataire créés" lightbox="images/app-and-tenant-ids.png":::

8. **Pour Microsoft Defender pour point de terminaison partenaires uniquement**. Définissez votre application comme mutualisée (disponible dans tous les locataires après consentement). Cela est **nécessaire** pour les applications tierces (par exemple, si vous créez une application destinée à s’exécuter dans le locataire de plusieurs clients). Cela **n’est pas obligatoire** si vous créez un service que vous souhaitez exécuter uniquement dans votre locataire (par exemple, si vous créez une application pour votre propre utilisation qui interagit uniquement avec vos propres données). Pour définir votre application comme mutualisée :

    - Accédez à **l’authentification** et ajoutez `https://portal.azure.com` **l’URI de redirection**.

    - En bas de la page, sous **Types de comptes pris en charge**, sélectionnez **comptes dans n’importe quel** consentement d’application d’annuaire organisationnel pour votre application mutualisée.

    Vous avez besoin que votre application soit approuvée dans chaque locataire où vous envisagez de l’utiliser. Cela est dû au fait que votre application interagit avec Defender pour point de terminaison pour le compte de votre client.

    Vous (ou votre client si vous écrivez une application tierce) devez sélectionner le lien de consentement et approuver votre application. Le consentement doit être effectué avec un utilisateur disposant de privilèges d’administration dans Active Directory.

    Le lien de consentement est formé comme suit : 

    ```https
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
    ```

    Où 00000000-0000-0000-0000-0000000000000 est remplacé par votre ID d’application.


**Terminé !** Vous avez inscrit une application avec succès ! Consultez les exemples ci-dessous pour l’acquisition et la validation des jetons.

## <a name="get-an-access-token"></a>Obtenir un jeton d’accès

Pour plus d’informations sur les jetons Azure AD, consultez le [didacticiel Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

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
$token
```

### <a name="use-c"></a>Utilisez C# :

Le code suivant a été testé avec NuGet Microsoft.Identity.Client 3.19.8.

> [!IMPORTANT]
> Le package [NuGet Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) et Azure AD Authentication Library (ADAL) ont été dépréciés. Aucune nouvelle fonctionnalité n’a été ajoutée depuis le 30 juin 2020.   Nous vous encourageons vivement à effectuer la mise à niveau. Pour plus d’informations, consultez le [guide de migration](/azure/active-directory/develop/msal-migration) .

1. Créez une application console.
1. Installez NuGet [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client/).
1. Ajoutez les éléments suivants :

    ```csharp
    using Microsoft.Identity.Client;
    ```

1. Copiez et collez le code suivant dans votre application (n’oubliez pas de mettre à jour les trois variables : ```tenantId, appId, appSecret```:

    ```csharp
    string tenantId = "00000000-0000-0000-0000-000000000000"; // Paste your own tenant ID here
    string appId = "11111111-1111-1111-1111-111111111111"; // Paste your own app ID here
    string appSecret = "22222222-2222-2222-2222-222222222222"; // Paste your own app secret here for a test, and then store it in a safe place! 
    const string authority = https://login.microsoftonline.com;
    const string audience = https://api.securitycenter.microsoft.com;

    IConfidentialClientApplication myApp = ConfidentialClientApplicationBuilder.Create(appId).WithClientSecret(appSecret).WithAuthority($"{authority}/{tenantId}").Build();

    List<string> scopes = new List<string>() { $"{audience}/.default" };

    AuthenticationResult authResult = myApp.AcquireTokenForClient(scopes).ExecuteAsync().GetAwaiter().GetResult();

    string token = authResult.AccessToken;
    ```
### <a name="use-python"></a>Utiliser Python

Voir [Obtenir un jeton à l’aide de Python](run-advanced-query-sample-python.md#get-token).

### <a name="use-curl"></a>Utiliser Curl

> [!NOTE]
> La procédure suivante suppose que Curl pour Windows est déjà installé sur votre ordinateur.

1. Ouvrez une invite de commandes et définissez CLIENT_ID sur votre ID d’application Azure.
1. Définissez CLIENT_SECRET sur votre secret d’application Azure.
1. Définissez TENANT_ID sur l’ID de locataire Azure du client qui souhaite utiliser votre application pour accéder à Defender pour point de terminaison.
1. Exécutez la commande suivante :

    ```console
    curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
    ```
    
    Vous obtiendrez une réponse sous la forme suivante :
    
    ```console
    {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
    ```
    
## <a name="validate-the-token"></a>Valider le jeton

Vérifiez que vous avez obtenu le jeton correct :

1. Copiez et collez le jeton obtenu à l’étape précédente dans [JWT](https://jwt.ms) pour le décoder.

1. Vérifiez que vous obtenez une revendication de « rôles » avec les autorisations souhaitées.

   Dans l’image suivante, vous pouvez voir un jeton décodé acquis à partir d’une application avec des autorisations sur tous les rôles de Microsoft Defender pour point de terminaison :

   :::image type="content" source="images/webapp-decoded-token.png" alt-text="Partie détails du jeton" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Utiliser le jeton pour accéder à Microsoft Defender pour point de terminaison API

1. Choisissez l’API que vous souhaitez utiliser. Pour plus d’informations, consultez [Les API Defender pour point de terminaison prises en charge](exposed-apis-list.md).
1. Définissez l’en-tête d’autorisation dans la requête http que vous envoyez au « Porteur {token} » (le porteur est le schéma d’autorisation).
1. L’heure d’expiration du jeton est d’une heure. Vous pouvez envoyer plusieurs demandes avec le même jeton.

Voici un exemple d’envoi d’une demande d’obtention d’une liste d’alertes **à l’aide de C#** :

```csharp
var httpClient = new HttpClient();

var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

// Do something useful with the response
```

## <a name="see-also"></a>Voir aussi
- [API prises en charge Microsoft Defender pour point de terminaison](exposed-apis-list.md)
- [Accès Microsoft Defender pour point de terminaison pour le compte d’un utilisateur](exposed-apis-create-app-nativeapp.md)
