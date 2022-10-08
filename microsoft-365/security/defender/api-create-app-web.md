---
title: Créer une application pour accéder à Microsoft 365 Defender sans utilisateur
description: Découvrez comment créer une application pour accéder à Microsoft 365 Defender sans utilisateur.
keywords: application, access, api, create
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.custom: api
ms.openlocfilehash: 168d935aeb534251f19d32fc9d83377731b1d1ee
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68067067"
---
# <a name="create-an-app-to-access-microsoft-365-defender-without-a-user"></a>Créer une application pour accéder à Microsoft 365 Defender sans utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Cette page explique comment créer une application pour obtenir un accès programmatique à Microsoft 365 Defender sans utilisateur défini, par exemple, si vous créez un démon ou un service en arrière-plan.

Si vous avez besoin d’un accès par programmation à Microsoft 365 Defender pour le compte d’un ou de plusieurs utilisateurs, consultez [Créer une application pour accéder aux API Microsoft 365 Defender pour le compte d’un utilisateur](api-create-app-user-context.md) et [Créer une application avec accès partenaire aux API Microsoft 365 Defender](api-partner-access.md). Si vous ne savez pas quel type d’accès vous avez besoin, consultez [Prise en main](api-access.md).

Microsoft 365 Defender expose une grande partie de ses données et actions par le biais d’un ensemble d’API programmatiques. Ces API vous aident à automatiser les flux de travail et à utiliser les fonctionnalités de Microsoft 365 Defender. Cet accès à l’API nécessite une authentification OAuth2.0. Pour plus d’informations, consultez [le flux de code d’autorisation OAuth 2.0](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En général, vous devez effectuer les étapes suivantes pour utiliser ces API :

- Créez une application Azure Active Directory (Azure AD).
- Obtenez un jeton d’accès à l’aide de cette application.
- Utilisez le jeton pour accéder à Microsoft 365 Defender API.

Cet article explique comment :

- Créer une application Azure AD
- Obtenir un jeton d’accès pour Microsoft 365 Defender
- Validez le jeton.

## <a name="create-an-app"></a>Créer une application

1. Connectez-vous à [Azure](https://portal.azure.com) en tant qu’utilisateur avec le rôle **Administrateur général** .

2. Accédez à **l’inscription** **Azure Active Directory** >  inscriptions d'applications  > **New**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Onglet Nouvelle inscription dans le portail Microsoft 365 Defender" lightbox="../../media/atp-azure-new-app2.png":::

3. Dans le formulaire, choisissez un nom pour votre application, puis **sélectionnez Inscrire**.

4. Dans la page de votre application, sélectionnez **Autorisations d’API Ajouter des** >  API **d’autorisation** > **que mon organisation utilise** >, tapez **Microsoft Threat Protection**, puis sélectionnez **Microsoft Threat Protection**. Votre application peut désormais accéder à Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* est un ancien nom pour Microsoft 365 Defender et n’apparaît pas dans la liste d’origine. Vous devez commencer à écrire son nom dans la zone de texte pour l’afficher.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Onglet Utilisation des API de l’organisation dans le portail Microsoft 365 Defender" lightbox="../../media/apis-in-my-org-tab.PNG":::

5. Sélectionnez **Autorisations d’application**. Choisissez les autorisations appropriées pour votre scénario (par exemple, **Incident.Read.All**), puis sélectionnez **Ajouter des autorisations**.

   :::image type="content" source="../../media/request-api-permissions.PNG" alt-text="Volet Autorisations de l’application dans le portail Microsoft 365 Defender" lightbox="../../media/request-api-permissions.PNG":::

    > [!NOTE]
    > Vous devez sélectionner les autorisations appropriées pour votre scénario. *Lire tous les incidents* n’est qu’un exemple. Pour déterminer l’autorisation dont vous avez besoin, consultez la section **Autorisations** de l’API que vous souhaitez appeler.
    >
    > Par exemple, pour [exécuter des requêtes avancées](api-advanced-hunting.md), sélectionnez l’autorisation « Exécuter des requêtes avancées » ; pour [isoler un appareil](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), sélectionnez l’autorisation « Isoler l’ordinateur ».

6. Sélectionnez **Accorder le consentement de l’administrateur**. Chaque fois que vous ajoutez une autorisation, vous devez sélectionner **Accorder le consentement administrateur** pour qu’elle prenne effet.

    :::image type="content" source="../../media/grant-consent.PNG" alt-text="Volet relatif à l’octroi de consentement dans le portail Microsoft 365 Defender" lightbox="../../media/grant-consent.PNG":::

7. Pour ajouter un secret à l’application, sélectionnez **Certificats & secrets**, ajoutez une description au secret, puis sélectionnez **Ajouter**.

    > [!TIP]
    > Après avoir sélectionné **Ajouter**, sélectionnez **copier la valeur de secret générée**. Vous ne pourrez pas récupérer la valeur du secret après votre départ.

    :::image type="content" source="../../media/defender-endpoint/webapp-create-key2.png" alt-text="Volet Créer une application dans le portail Microsoft 365 Defender" lightbox="../../media/defender-endpoint/webapp-create-key2.png":::

8. Enregistrez votre ID d’application et votre ID de locataire dans un endroit sûr. Ils sont répertoriés sous **Vue d’ensemble** sur la page de votre application.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Volet Vue d’ensemble dans le portail Microsoft 365 Defender" lightbox="../../media/app-and-tenant-ids.png":::

9. **Pour Microsoft 365 Defender partenaires uniquement** : [suivez ces instructions](./api-partner-access.md) pour l’accès des partenaires via les API Microsoft 365 Defender, définissez votre application sur multilocataire afin qu’elle puisse être disponible dans tous les locataires une fois que vous avez reçu le consentement de l’administrateur. L’accès partenaire est **requis** pour les applications tierces, par exemple, si vous créez une application destinée à s’exécuter dans les locataires de plusieurs clients. Il **n’est pas obligatoire** si vous créez un service que vous souhaitez exécuter uniquement dans votre locataire, par exemple une application pour votre propre utilisation qui interagit uniquement avec vos propres données. Pour définir votre application comme multilocataire :

    - Accédez à **l’authentification** et ajoutez https://portal.azure.com **l’URI de redirection**.

    - En bas de la page, sous **Types de comptes pris en charge**, sélectionnez **comptes dans n’importe quel** consentement d’application d’annuaire organisationnel pour votre application mutualisée.

    Étant donné que votre application interagit avec Microsoft 365 Defender au nom de vos utilisateurs, elle doit être approuvée pour chaque locataire sur lequel vous envisagez de l’utiliser.

    L’administrateur général Active Directory pour chaque locataire doit sélectionner le lien de consentement et approuver votre application.

    Le lien de consentement a la structure suivante :

    ```http
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=<00000000-0000-0000-0000-000000000000>&response_type=code&sso_reload=true
    ```

    Les chiffres doivent être remplacés `00000000-0000-0000-0000-000000000000` par votre ID d’application.  

**Terminé !** Vous avez inscrit une application avec succès ! Consultez les exemples ci-dessous pour l’acquisition et la validation des jetons.

## <a name="get-an-access-token"></a>Obtenir un jeton d’accès

Pour plus d’informations sur les jetons Azure Active Directory, consultez le [didacticiel Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Bien que les exemples de cette section vous encouragent à coller des valeurs secrètes à des fins de test, vous **ne devez jamais coder en dur les secrets** dans une application en cours d’exécution en production. Un tiers peut utiliser votre secret pour accéder aux ressources. Vous pouvez aider à sécuriser les secrets de votre application à l’aide [d’Azure Key Vault](/azure/key-vault/general/about-keys-secrets-certificates). Pour obtenir un exemple pratique de la façon dont vous pouvez protéger votre application, consultez [Gérer les secrets dans vos applications serveur avec Azure Key Vault](/training/modules/manage-secrets-with-azure-key-vault/).

### <a name="get-an-access-token-using-powershell"></a>Obtenir un jeton d’accès à l’aide de PowerShell

```PowerShell
# This code gets the application context token and saves it to a file named "Latest-token.txt" under the current directory.

$tenantId = '' # Paste your directory (tenant) ID here
$clientId = '' # Paste your application (client) ID here
$appSecret = '' # Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

$resourceAppIdUri = 'https://api.security.microsoft.com'
$oAuthUri = "https://login.windows.net/$tenantId/oauth2/token"

$authBody = [Ordered] @{
    resource = $resourceAppIdUri
    client_id = $clientId
    client_secret = $appSecret
    grant_type = 'client_credentials'
}

$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$token = $authResponse.access_token

Out-File -FilePath "./Latest-token.txt" -InputObject $token

return $token
```

### <a name="get-an-access-token-using-c"></a>Obtenir un jeton d’accès à l’aide de C\#

> [!NOTE]
> Le code suivant a été testé avec Nuget Microsoft.Identity.Client 3.19.8.

> [!IMPORTANT]
> Le package [NuGet Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) et Azure AD Authentication Library (ADAL) ont été dépréciés. Aucune nouvelle fonctionnalité n’a été ajoutée depuis le 30 juin 2020.   Nous vous encourageons vivement à effectuer la mise à niveau. Pour plus d’informations, consultez le [guide de migration](/azure/active-directory/develop/msal-migration) .

1. Créez une application console.

1. Installez NuGet [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client/).

1. Ajoutez la ligne suivante :

    ```C#
    using Microsoft.Identity.Client;
    ```

1. Copiez et collez le code suivant dans votre application (n’oubliez pas de mettre à jour les trois variables : `tenantId`, `clientId`, `appSecret`) :

    ```C#
    csharp
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

### <a name="get-an-access-token-using-python"></a>Obtenir un jeton d’accès à l’aide de Python

```Python
import json
import urllib.request
import urllib.parse

tenantId = '' # Paste your directory (tenant) ID here
clientId = '' # Paste your application (client) ID here
appSecret = '' # Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

url = "https://login.windows.net/%s/oauth2/token" % (tenantId)

resourceAppIdUri = 'https://api.security.microsoft.com'

body = {
    'resource' : resourceAppIdUri,
    'client_id' : clientId,
    'client_secret' : appSecret,
    'grant_type' : 'client_credentials'
}

data = urllib.parse.urlencode(body).encode("utf-8")

req = urllib.request.Request(url, data)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
aadToken = jsonResponse["access_token"]
```

### <a name="get-an-access-token-using-curl"></a>Obtenir un jeton d’accès à l’aide de curl

> [!NOTE]
> Curl est préinstallé sur Windows 10, versions 1803 et ultérieures. Pour les autres versions de Windows, téléchargez et installez l’outil directement à partir du [site web curl officiel](https://curl.haxx.se/windows/).

1. Ouvrez une invite de commandes et définissez CLIENT_ID sur votre ID d’application Azure.

1. Définissez CLIENT_SECRET sur votre secret d’application Azure.

1. Définissez TENANT_ID sur l’ID de locataire Azure du client qui souhaite utiliser votre application pour accéder à Microsoft 365 Defender.

1. Exécutez la commande suivante :

   ```bash
   curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://api.security.microsoft.com/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
   ```

   Une réponse correcte se présente comme suit :

   ```bash
   {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
   ```

## <a name="validate-the-token"></a>Valider le jeton

1. Copiez et collez le jeton dans le [site web du validateur de jeton web JSON, JWT,](https://jwt.ms) pour le décoder.

1. Assurez-vous que la revendication *de rôles* dans le jeton décodé contient les autorisations souhaitées.

   Dans l’image suivante, vous pouvez voir un jeton décodé acquis à partir d’une application, avec `Incidents.Read.All`, `Incidents.ReadWrite.All`et `AdvancedHunting.Read.All` des autorisations :

   :::image type="content" source="../../media/defender-endpoint/webapp-decoded-token.png" alt-text="Volet Jeton décodé dans le portail Microsoft 365 Defender" lightbox="../../media/defender-endpoint/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>Utiliser le jeton pour accéder à l’API Microsoft 365 Defender

1. Choisissez l’API que vous souhaitez utiliser (incidents ou repérage avancé). Pour plus d’informations, consultez LES [API Microsoft 365 Defender prises en charge](api-supported.md).

2. Dans la requête http que vous êtes sur le point d’envoyer, définissez l’en-tête d’autorisation `"Bearer" <token>`sur , *le porteur* étant le schéma d’autorisation et le *jeton* étant votre jeton validé.

3. Le jeton expire dans un délai d’une heure. Vous pouvez envoyer plusieurs demandes pendant cette période avec le même jeton.

L’exemple suivant montre comment envoyer une demande pour obtenir une liste d’incidents **à l’aide de C#**.

```C#
    var httpClient = new HttpClient();
    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/incidents");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();
```

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble des API Microsoft 365 Defender](api-overview.md)
- [Accéder aux API Microsoft 365 Defender](api-access.md)
- [Créer une application « Hello World »](api-hello-world.md)
- [Créer une application pour accéder aux API Microsoft 365 Defender pour le compte d’un utilisateur](api-create-app-user-context.md)
- [Créer une application avec un accès partenaire multilocataire aux API Microsoft 365 Defender](api-partner-access.md)
- [En savoir plus sur les limites d’API et les licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
- [Gérer les secrets dans vos applications serveur avec Azure Key Vault](/training/modules/manage-secrets-with-azure-key-vault/)
- [Autorisation OAuth 2.0 pour la connexion utilisateur et l’accès à l’API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
