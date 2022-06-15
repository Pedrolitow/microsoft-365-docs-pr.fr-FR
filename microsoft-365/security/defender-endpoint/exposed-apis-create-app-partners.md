---
title: Accès aux partenaires par le biais d’API Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Découvrez comment concevoir une application web pour obtenir un accès programmatique à Microsoft Defender pour point de terminaison pour le compte de vos utilisateurs.
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 7ca212cf6cdacdaf374dbe65f4fd88c74712bb34
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66101841"
---
# <a name="partner-access-through-microsoft-defender-for-endpoint-apis"></a>Accès aux partenaires par le biais d’API Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/index.yml)

> [!IMPORTANT]
> Les fonctionnalités de chasse avancées ne sont pas incluses dans Defender entreprise. Consultez [Comparer les Microsoft Defender pour entreprises à Microsoft Defender pour point de terminaison plans 1 et 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Cette page explique comment créer une application Azure Active Directory (Azure AD) pour obtenir un accès programmatique à Microsoft Defender pour point de terminaison pour le compte de vos clients.

Microsoft Defender pour point de terminaison expose une grande partie de ses données et actions par le biais d’un ensemble d’API programmatiques. Ces API vous aideront à automatiser les flux de travail et à innover en fonction de Microsoft Defender pour point de terminaison fonctionnalités. L’accès à l’API nécessite l’authentification OAuth2.0. Pour plus d’informations, consultez [Flow du code d’autorisation OAuth 2.0](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En général, vous devez effectuer les étapes suivantes pour utiliser les API :

- Créez une application Azure AD **multilocataire** .
- Obtenez l’autorisation (consentement) de votre administrateur client pour que votre application accède aux ressources Defender pour point de terminaison dont elle a besoin.
- Obtenez un jeton d’accès à l’aide de cette application.
- Utilisez le jeton pour accéder à Microsoft Defender pour point de terminaison API.

Les étapes suivantes vous guideront dans la création d’une application Azure AD, l’obtention d’un jeton d’accès pour Microsoft Defender pour point de terminaison et la validation du jeton.

## <a name="create-the-multi-tenant-app"></a>Créer l’application mutualisée

1. Connectez-vous à votre [locataire Azure](https://portal.azure.com) avec un utilisateur ayant le rôle **Administrateur général** .

2. Accédez à **Azure Active Directory** \> **App-registraties** \> **Nouvelle inscription**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Volet de navigation vers l’inscription d’application" lightbox="images/atp-azure-new-app2.png":::

3. Dans le formulaire d’inscription :

   - Choisissez un nom pour votre application.

   - Types de comptes pris en charge : comptes dans n’importe quel annuaire organisationnel.

   - URI de redirection - type : Web, URI : https://portal.azure.com

     :::image type="content" source="images/atp-api-new-app-partner.png" alt-text="Page d’inscription de l’application partenaire Microsoft Azure" lightbox="images/atp-api-new-app-partner.png":::

4. Autorisez votre application à accéder à Microsoft Defender pour point de terminaison et affectez-la avec le jeu minimal d’autorisations requis pour terminer l’intégration.

   - Dans la page de votre application, sélectionnez **Autorisations d’API Ajouter des** \> API **d’autorisation** \> **que mon organisation utilise** > type **WindowsDefenderATP** , puis sélectionnez **Sur WindowsDefenderATP**.

   - **Remarque** : *WindowsDefenderATP* n’apparaît pas dans la liste d’origine. Commencez à écrire son nom dans la zone de texte pour l’afficher.

     :::image type="content" source="images/add-permission.png" alt-text="Option Ajouter une autorisation" lightbox="images/add-permission.png":::

### <a name="request-api-permissions"></a>Demander des autorisations d’API

Pour déterminer l’autorisation dont vous avez besoin, consultez la section **Autorisations** de l’API que vous souhaitez appeler. Par exemple :

- Pour [exécuter des requêtes avancées](run-advanced-query-api.md), sélectionnez l’autorisation « Exécuter des requêtes avancées ».
- Pour [isoler un appareil](isolate-machine.md), sélectionnez l’autorisation « Isoler l’ordinateur »

Dans l’exemple suivant, nous allons utiliser l’autorisation **« Lire toutes les alertes »** :

1. Sélectionnez **Autorisations** \> d’application **Alert.Read.All** > sélectionnez **Ajouter des autorisations**

   :::image type="content" source="images/application-permissions.png" alt-text="Option qui permet d’ajouter une autorisation" lightbox="images/application-permissions.png":::

2. Sélectionner **Accorder le consentement**

   - **Remarque** : chaque fois que vous ajoutez une autorisation, vous devez sélectionner le **consentement d’octroi** pour que la nouvelle autorisation prenne effet.

   :::image type="content" source="images/grant-consent.png" alt-text="Option qui autorise l’octroi d’un consentement" lightbox="images/grant-consent.png":::

3. Ajoutez un secret à l’application.

   - Sélectionnez **Certificats & secrets**, ajoutez une description au secret, puis sélectionnez **Ajouter**.

    **Important** : après avoir cliqué sur Ajouter, **copiez la valeur secrète générée**. Vous ne pourrez pas récupérer après votre départ !

     :::image type="content" source="images/webapp-create-key2.png" alt-text="Créer une clé d’application" lightbox="images/webapp-create-key2.png":::

4. Notez votre ID d’application :

   - Dans la page de votre application, accédez à **Vue d’ensemble** et copiez les informations suivantes :

     :::image type="content" source="images/app-id.png" alt-text="ID de création de l’application" lightbox="images/app-id.png":::

5. Ajoutez l’application au locataire de votre client.

   Vous avez besoin que votre application soit approuvée dans chaque locataire client où vous envisagez de l’utiliser. Cela est dû au fait que votre application interagit avec Microsoft Defender pour point de terminaison application pour le compte de votre client.

   Un utilisateur disposant de **l’administrateur général** du locataire de votre client doit sélectionner le lien de consentement et approuver votre application.

   Le lien de consentement est au format suivant :

   ```http
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Où 00000000-0000-0000-0000-000000000000 doit être remplacé par votre ID d’application

   Après avoir cliqué sur le lien de consentement, connectez-vous à l’administrateur général du locataire du client et consentez à l’application.

   :::image type="content" source="images/app-consent-partner.png" alt-text="Bouton Accepter" lightbox="images/app-consent-partner.png":::

   En outre, vous devez demander à votre client son ID de locataire et l’enregistrer pour une utilisation ultérieure lors de l’acquisition du jeton.

6. **Terminé !** Vous avez inscrit une application avec succès ! Consultez les exemples ci-dessous pour l’acquisition et la validation des jetons.

## <a name="get-an-access-token-example"></a>Obtenir un exemple de jeton d’accès

**Note:** Pour obtenir un jeton d’accès pour le compte de votre client, utilisez l’ID de locataire du client lors des acquisitions de jetons suivantes.

Pour plus d’informations sur le jeton AAD, consultez [le didacticiel AAD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds)

### <a name="using-powershell"></a>Utiliser PowerShell

```powershell
# That code gets the App Context Token and save it to a file named "Latest-token.txt" under the current directory
# Paste below your Tenant ID, App ID and App Secret (App key).

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
Out-File -FilePath "./Latest-token.txt" -InputObject $token
return $token
```

### <a name="using-c"></a>Utilisation de C #

> Le code ci-dessous a été testé avec Nuget Microsoft.Identity.Client

> [!IMPORTANT]
> Le package [NuGet Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) et Azure AD Authentication Library (ADAL) ont été dépréciés. Aucune nouvelle fonctionnalité n’a été ajoutée depuis le 30 juin 2020. Nous vous encourageons vivement à effectuer la mise à niveau. Pour plus d’informations, consultez le [guide de migration](/azure/active-directory/develop/msal-migration) .

- Créer une application console
- Installer NuGet [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client/)
- Ajouter les éléments ci-dessous à l’aide de

    ```console
    using Microsoft.Identity.Client;
    ```

- Copiez/collez le code ci-dessous dans votre application (n’oubliez pas de mettre à jour les trois variables : `tenantId`, `appId`et `appSecret`)

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

### <a name="using-python"></a>Utilisation de Python

Reportez-vous à [Obtenir un jeton à l’aide de Python](run-advanced-query-sample-python.md#get-token)

### <a name="using-curl"></a>Utilisation de Curl

> [!NOTE]
> La procédure ci-dessous supposée Curl pour Windows est déjà installée sur votre ordinateur

- Ouvrir une fenêtre de commande
- Définir CLIENT_ID sur votre ID d’application Azure
- Définir CLIENT_SECRET sur votre secret d’application Azure
- Définissez TENANT_ID sur l’ID de locataire Azure du client qui souhaite utiliser votre application pour accéder à Microsoft Defender pour point de terminaison application
- Exécutez la commande ci-dessous :

```curl
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Vous obtiendrez une réponse du formulaire :

```console
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Valider le jeton

Contrôle d’intégrité pour vérifier que vous avez obtenu un jeton correct :

- Copier/coller dans [JWT](https://jwt.ms) le jeton obtenu à l’étape précédente pour le décoder
- Valider l’obtention d’une revendication « roles » avec les autorisations souhaitées
- Dans la capture d’écran ci-dessous, vous pouvez voir un jeton décodé acquis à partir d’une application avec plusieurs autorisations pour Microsoft Defender pour point de terminaison :
- La revendication « tid » est l’ID de locataire auquel le jeton appartient.

:::image type="content" source="images/webapp-decoded-token.png" alt-text="Page de validation de jeton" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Utiliser le jeton pour accéder à Microsoft Defender pour point de terminaison API

- Choisissez l’API que vous souhaitez utiliser. Pour plus d’informations, consultez LES [API Microsoft Defender pour point de terminaison prises en charge](exposed-apis-list.md)
- Définissez l’en-tête d’autorisation dans la requête Http que vous envoyez au « Porteur {token} » (le porteur est le schéma d’autorisation)
- L’heure d’expiration du jeton est de 1 heure (vous pouvez envoyer plusieurs demandes avec le même jeton)

- Exemple d’envoi d’une demande pour obtenir une liste d’alertes **à l’aide de C#**

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
