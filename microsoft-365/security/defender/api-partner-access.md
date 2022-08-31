---
title: Accès aux partenaires par le biais d’API Microsoft 365 Defender
description: Découvrez comment créer une application pour obtenir un accès programmatique à Microsoft 365 Defender pour le compte de vos utilisateurs.
keywords: partenaire, accès, API, multilocataire, consentement, jeton d’accès, application
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
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.custom: api
ms.openlocfilehash: 03c87d32cf850d75fb83eefdc989927fcdc6ae90
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67479551"
---
# <a name="create-an-app-with-partner-access-to-microsoft-365-defender-apis"></a>Créer une application avec un accès partenaire aux API Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Cette page explique comment créer une application Azure Active Directory qui a un accès programmatique à Microsoft 365 Defender, pour le compte d’utilisateurs sur plusieurs locataires. Les applications mutualisée sont utiles pour servir de grands groupes d’utilisateurs.

Si vous avez besoin d’un accès programmatique à Microsoft 365 Defender pour le compte d’un seul utilisateur, consultez [Créer une application pour accéder aux API Microsoft 365 Defender pour le compte d’un utilisateur](api-create-app-user-context.md). Si vous avez besoin d’un accès sans un utilisateur défini explicitement (par exemple, si vous écrivez une application ou un démon en arrière-plan), consultez [Créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md). Si vous ne savez pas quel type d’accès vous avez besoin, consultez [Prise en main](api-access.md).

Microsoft 365 Defender expose une grande partie de ses données et actions par le biais d’un ensemble d’API programmatiques. Ces API vous aident à automatiser les flux de travail et à utiliser les fonctionnalités de Microsoft 365 Defender. Cet accès à l’API nécessite une authentification OAuth2.0. Pour plus d’informations, consultez [le flux de code d’autorisation OAuth 2.0](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En général, vous devez effectuer les étapes suivantes pour utiliser ces API :

- Créez une application Azure Active Directory (Azure AD).
- Obtenez un jeton d’accès à l’aide de cette application.
- Utilisez le jeton pour accéder à Microsoft 365 Defender API.

Étant donné que cette application est multilocataire, vous aurez également besoin du [consentement de l’administrateur](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) de chaque locataire pour le compte de ses utilisateurs.

Cet article explique comment :

- Créer une application Azure AD **mutualisée**
- Obtenez le consentement autorisé de votre administrateur d’utilisateurs pour que votre application accède aux Microsoft 365 Defender dont elle a besoin.
- Obtenir un jeton d’accès pour Microsoft 365 Defender
- Valider le jeton

Microsoft 365 Defender expose une grande partie de ses données et actions par le biais d’un ensemble d’API programmatiques. Ces API vous aideront à automatiser les flux de travail et à innover en fonction de Microsoft 365 Defender fonctionnalités. L’accès à l’API nécessite l’authentification OAuth2.0. Pour plus d’informations, consultez [le flux de code d’autorisation OAuth 2.0](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En général, vous devez effectuer les étapes suivantes pour utiliser les API :

- Créez une application Azure AD **multilocataire** .
- Obtenez l’autorisation (consentement) de votre administrateur utilisateur pour que votre application accède à Microsoft 365 Defender ressources dont elle a besoin.
- Obtenez un jeton d’accès à l’aide de cette application.
- Utilisez le jeton pour accéder à Microsoft 365 Defender API.

Les étapes suivantes vous guident dans la création d’une application Azure AD mutualisée, l’obtention d’un jeton d’accès pour Microsoft 365 Defender et la validation du jeton.

## <a name="create-the-multi-tenant-app"></a>Créer l’application mutualisée

1. Connectez-vous à [Azure](https://portal.azure.com) en tant qu’utilisateur avec le rôle **Administrateur général** .

2. Accédez à **l’inscription** **Azure Active Directory** >  inscriptions d'applications  > **New**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Section Inscription d’une application dans le portail Microsoft 365 Defender" lightbox="../../media/atp-azure-new-app2.png":::

3. Dans le formulaire d’inscription :

   - Choisissez un nom pour votre application.
   - Dans **les types de comptes pris en charge**, sélectionnez **Comptes dans n’importe quel annuaire organisationnel (tout annuaire Azure AD) - Mutualisé**.
   - Renseignez la section **URI de redirection** . Sélectionnez le type **Web** et attribuez à l’URI **https://portal.azure.com** de redirection .

   Une fois que vous avez terminé de remplir le formulaire, **sélectionnez Inscrire**.

   :::image type="content" source="../..//media/atp-api-new-app-partner.png" alt-text="Sections d’inscription d’une application dans le portail Microsoft 365 Defender" lightbox="../..//media/atp-api-new-app-partner.png":::

4. Dans la page de votre application, sélectionnez **Autorisations d’API Ajouter des** >  API **d’autorisation** > **que mon organisation utilise** >, tapez **Microsoft Threat Protection**, puis sélectionnez **Microsoft Threat Protection**. Votre application peut désormais accéder à Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* est un ancien nom pour Microsoft 365 Defender et n’apparaît pas dans la liste d’origine. Vous devez commencer à écrire son nom dans la zone de texte pour l’afficher.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Section Utilisation des API dans le portail Microsoft 365 Defender" lightbox="../../media/apis-in-my-org-tab.PNG":::

5. Sélectionnez **Autorisations d’application**. Choisissez les autorisations appropriées pour votre scénario (par exemple, **Incident.Read.All**), puis sélectionnez **Ajouter des autorisations**.

   :::image type="content" source="../../media/request-api-permissions.PNG" alt-text="Volet d’autorisations d’une application dans le portail Microsoft 365 Defender" lightbox="../../media/request-api-permissions.PNG":::

    > [!NOTE]
    > Vous devez sélectionner les autorisations appropriées pour votre scénario. *Lire tous les incidents* n’est qu’un exemple. Pour déterminer l’autorisation dont vous avez besoin, consultez la section **Autorisations** de l’API que vous souhaitez appeler.
    >
    > Par exemple, pour [exécuter des requêtes avancées](api-advanced-hunting.md), sélectionnez l’autorisation « Exécuter des requêtes avancées » ; pour [isoler un appareil](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), sélectionnez l’autorisation « Isoler l’ordinateur ».

6. Sélectionnez **Accorder le consentement de l’administrateur**. Chaque fois que vous ajoutez une autorisation, vous devez sélectionner **Accorder le consentement administrateur** pour qu’elle prenne effet.

    :::image type="content" source="../../media/grant-consent.PNG" alt-text="Section permettant d’accorder le consentement de l’administrateur dans le portail Microsoft 365 Defender" lightbox="../../media/grant-consent.PNG":::

7. Pour ajouter un secret à l’application, sélectionnez **Certificats & secrets**, ajoutez une description au secret, puis sélectionnez **Ajouter**.

    > [!TIP]
    > Après avoir sélectionné **Ajouter**, sélectionnez **copier la valeur de secret générée**. Vous ne pourrez pas récupérer la valeur du secret après votre départ.

      :::image type="content" source="../../media/webapp-create-key2.png" alt-text="Section Ajout de secret dans le portail Microsoft 365 Defender" lightbox="../../media/webapp-create-key2.png":::

8. Enregistrez votre ID d’application et votre ID de locataire dans un endroit sûr. Ils sont répertoriés sous **Vue d’ensemble** sur la page de votre application.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Volet Vue d’ensemble dans le portail Microsoft 365 Defender" lightbox="../../media/app-and-tenant-ids.png":::

9. Ajoutez l’application au locataire de votre utilisateur.

   Étant donné que votre application interagit avec Microsoft 365 Defender au nom de vos utilisateurs, elle doit être approuvée pour chaque locataire sur lequel vous envisagez de l’utiliser.

   Un **administrateur général** du locataire de votre utilisateur doit afficher le lien de consentement et approuver votre application.

   Le lien de consentement est au format suivant :

   ```HTTP
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Les chiffres doivent être remplacés `00000000-0000-0000-0000-000000000000` par votre ID d’application.

   Après avoir cliqué sur le lien de consentement, connectez-vous à l’administrateur général du locataire de l’utilisateur et consentez à l’application.

   :::image type="content" source="../../media/app-consent-partner.png" alt-text="Page d’application de consentement dans le portail Microsoft 365 Defender" lightbox="../../media/app-consent-partner.png":::

   Vous devez également demander à votre utilisateur son ID de locataire. L’ID de locataire est l’un des identificateurs utilisés pour acquérir des jetons d’accès.

- **Terminé !** Vous avez inscrit une application avec succès !
- Consultez les exemples ci-dessous pour l’acquisition et la validation des jetons.

## <a name="get-an-access-token"></a>Obtenir un jeton d’accès

Pour plus d’informations sur les jetons Azure AD, consultez le [didacticiel Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Bien que les exemples de cette section vous encouragent à coller des valeurs secrètes à des fins de test, vous **ne devez jamais coder en dur les secrets** dans une application en cours d’exécution en production. Un tiers peut utiliser votre secret pour accéder aux ressources. Vous pouvez aider à sécuriser les secrets de votre application à l’aide [d’Azure Key Vault](/azure/key-vault/general/about-keys-secrets-certificates). Pour obtenir un exemple pratique de la façon dont vous pouvez protéger votre application, consultez [Gérer les secrets dans vos applications serveur avec Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/).

> [!TIP]
> Dans les exemples suivants, utilisez l’ID de locataire d’un utilisateur pour tester que le script fonctionne.

### <a name="get-an-access-token-using-powershell"></a>Obtenir un jeton d’accès à l’aide de PowerShell

```PowerShell
# This code gets the application context token and saves it to a file named "Latest-token.txt" under the current directory.

$tenantId = '' # Paste your directory (tenant) ID here
$clientId = '' # Paste your application (client) ID here
$appSecret = '' # Paste your own app secret here to test, then store it in a safe place!

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
1. Définissez TENANT_ID sur l’ID de locataire Azure de l’utilisateur qui souhaite utiliser votre application pour accéder à Microsoft 365 Defender.
1. Exécutez la commande suivante :

```bash
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Une réponse correcte se présente comme suit :

```bash
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Valider le jeton

1. Copiez et collez le jeton dans le [site web du validateur de jeton web JSON, JWT,](https://jwt.ms) pour le décoder.
1. Assurez-vous que la revendication *de rôles* dans le jeton décodé contient les autorisations souhaitées.

Dans l’image suivante, vous pouvez voir un jeton décodé acquis à partir d’une application, avec ```Incidents.Read.All```, ```Incidents.ReadWrite.All```et ```AdvancedHunting.Read.All``` des autorisations :

:::image type="content" source="../../media/webapp-decoded-token.png" alt-text="Volet Jeton décodé dans le portail Microsoft 365 Defender" lightbox="../../media/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>Utiliser le jeton pour accéder à l’API Microsoft 365 Defender

1. Choisissez l’API que vous souhaitez utiliser (incidents ou repérage avancé). Pour plus d’informations, consultez LES [API Microsoft 365 Defender prises en charge](api-supported.md).
2. Dans la requête http que vous êtes sur le point d’envoyer, définissez l’en-tête d’autorisation `"Bearer" <token>`sur , le *porteur* étant le schéma d’autorisation et le *jeton* étant votre jeton validé.
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
- [Créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md)
- [Créer une application pour accéder aux API Microsoft 365 Defender pour le compte d’un utilisateur](api-create-app-user-context.md)
- [En savoir plus sur les limites d’API et les licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
- [Gérer les secrets dans vos applications serveur avec Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Autorisation OAuth 2.0 pour la connexion utilisateur et l’accès à l’API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
