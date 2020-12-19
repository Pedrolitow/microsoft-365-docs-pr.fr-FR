---
title: Créer une application pour accéder à Microsoft 365 Defender sans utilisateur
description: Découvrez comment créer une application pour accéder à Microsoft 365 Defender sans utilisateur.
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
ms.openlocfilehash: de925fa52056a051592fe5024c0abd40b51ad57b
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719355"
---
# <a name="create-an-app-to-access-microsoft-365-defender-without-a-user"></a>Créer une application pour accéder à Microsoft 365 Defender sans utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Cette page explique comment créer une application pour accéder par programme à Microsoft 365 Defender sans utilisateur défini, par exemple, si vous créez un service de démon ou d’arrière-plan.

Si vous avez besoin d’un accès par programme à Microsoft 365 Defender au nom d’un ou de plusieurs utilisateurs, reportez-vous à [la rubrique créer une application pour accéder aux API microsoft 365 Defender de la part d’un utilisateur](api-create-app-user-context.md) et [créer une application avec un accès partenaire aux API Microsoft 365 Defender](api-partner-access.md). Si vous n’êtes pas certain du type d’accès dont vous avez besoin, consultez la rubrique [prise en main](api-access.md).

Microsoft 365 Defender expose une grande partie de ses données et actions via un ensemble d’API de programmation. Ces API vous aident à automatiser les flux de travail et à utiliser les fonctionnalités de Microsoft 365 Defender. Cet accès à l’API nécessite l’authentification OAuth 2.0. Pour plus d’informations, reportez-vous au [flux de code d’autorisation OAuth 2,0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En règle générale, vous devez effectuer les étapes suivantes pour utiliser ces API :

- Créez une application Azure Active Directory (Azure AD).
- Obtenir un jeton d’accès à l’aide de cette application.
- Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Cet article explique comment :

- Créer une application Azure AD
- Obtenir un jeton d’accès à Microsoft 365 Defender
- Validez le jeton.

## <a name="create-an-app"></a>Créer une application

1. Connectez-vous à [Azure](https://portal.azure.com) en tant qu’utilisateur doté du rôle d' **administrateur général** .

2. Accédez à **Azure Active Directory**  >  **app Registrations**  >  **New Registration**.

   ![Image de Microsoft Azure et navigation de l’application](../../media/atp-azure-new-app2.png)

3. Dans le formulaire, choisissez un nom pour votre application, puis sélectionnez **Enregistrer**.

4. Sur la page de votre application, sélectionnez **autorisations d’API**  >  **Ajouter une**  >  **API mon organisation utilise** des >, tapez **Microsoft Threat Protection**, puis sélectionnez **Microsoft Threat Protection**. Votre application peut maintenant accéder à Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* est un ancien nom pour Microsoft 365 Defender et n’apparaît pas dans la liste d’origine. Vous devez commencer à écrire son nom dans la zone de texte pour l’afficher.

   ![Image de la sélection des autorisations de l’API](../../media/apis-in-my-org-tab.PNG)

5. Sélectionnez **autorisations d’application**. Choisissez les autorisations appropriées pour votre scénario (par exemple, **incident. Read. All**), puis sélectionnez **Ajouter des autorisations**.

   ![Image de l’accès à l’API et de la sélection de l’API](../../media/request-api-permissions.PNG)

    > [!NOTE]
    > Vous devez sélectionner les autorisations appropriées pour votre scénario. *Read All incidents* n’est qu’un exemple. Pour déterminer les autorisations qui vous sont nécessaires, consultez la section **autorisations** dans l’API que vous souhaitez appeler.
    >
    > Par exemple, pour [exécuter des requêtes avancées](api-advanced-hunting.md), sélectionnez l’autorisation « exécuter des requêtes avancées »; pour [isoler un appareil](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), sélectionnez l’autorisation « isoler l’ordinateur ».

6. Sélectionnez **accorder le consentement** de l’administrateur. Chaque fois que vous ajoutez une autorisation, vous devez sélectionner **accorder le consentement** de l’administrateur pour qu’elle prenne effet.

    ![Image des autorisations accorder](../../media/grant-consent.PNG)

7. Pour ajouter une clé secrète à l’application, sélectionnez **certificats & secrets**, ajoutez une description à la clé secrète, puis sélectionnez **Ajouter**.

    > [!TIP]
    > Une fois que vous avez sélectionné **Ajouter**, sélectionnez **copier la valeur secrète générée**. Vous ne pourrez pas récupérer la valeur secrète une fois que vous aurez quitté.

    ![Image de la clé créer une application](../../media/webapp-create-key2.png)

8. Enregistrez votre ID d’application et votre ID de client dans un endroit sûr. Elles sont indiquées sous **vue d’ensemble** sur votre application.

   ![Image de l’ID d’application créé](../../media/app-and-tenant-ids.png)

9. **Pour les partenaires microsoft 365 Defender uniquement**: [suivez ces instructions](https://docs.microsoft.com/microsoft-365/security/mtp/api-partner-access) pour accéder aux partenaires via les API Microsoft 365 Defender, définissez votre application sur multi-locataire, afin qu’elle puisse être disponible dans tous les clients une fois que vous avez reçu le consentement de l’administrateur. L’accès partenaire est **requis** pour les applications tierces, par exemple, si vous créez une application conçue pour s’exécuter dans les clients de plusieurs clients. Il n’est **pas obligatoire** si vous créez un service que vous souhaitez exécuter uniquement dans votre client, tel qu’une application pour votre propre utilisation qui interagira uniquement avec vos propres données. Pour définir votre application sur plusieurs locataires, procédez comme suit :

    - Accédez à **authentification** et ajoutez https://portal.azure.com en tant qu' **URI de redirection**.

    - En bas de la page, sous **types de comptes pris en charge**, sélectionnez les **comptes dans n’importe quel consentement d’application d’annuaire d’organisation** pour votre application mutualisée.

    Étant donné que votre application interagit avec Microsoft 365 Defender au nom de vos utilisateurs, elle doit être approuvée pour chaque client sur lequel vous envisagez de l’utiliser.

    L’administrateur général Active Directory de chaque client doit sélectionner le lien de consentement et approuver votre application.

    Le lien de consentement a la structure suivante :

    ```http
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=<00000000-0000-0000-0000-000000000000>&response_type=code&sso_reload=true
    ```

    Les chiffres `00000000-0000-0000-0000-000000000000` doivent être remplacés par l’ID de votre application.  

**Terminé!** Vous avez correctement inscrit une application ! Voir des exemples ci-dessous pour l’acquisition et la validation de jetons.

## <a name="get-an-access-token"></a>Obtenir un jeton d’accès

Pour plus d’informations sur les jetons Azure Active Directory, consultez le [didacticiel Azure ad](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Bien que les exemples de cette section vous encouragent à coller des valeurs secrètes à des fins de test, vous ne devez **jamais coder les secrets** dans une application exécutée en production. Un tiers peut utiliser votre clé secrète pour accéder aux ressources. Vous pouvez protéger les secrets de votre application en utilisant [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/general/about-keys-secrets-certificates). Pour obtenir un exemple pratique de la façon dont vous pouvez protéger votre application, voir [Manage secrets in your Server Apps with Azure Key Vault](https://docs.microsoft.com/learn/modules/manage-secrets-with-azure-key-vault/).

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
> Le code suivant a été testé avec NuGet Microsoft. IdentityModel. clients. ActiveDirectory 3.19.8.

1. Créez une nouvelle application console.

1. Installez NuGet [Microsoft. IdentityModel. clients. ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

1. Ajoutez la ligne suivante :

    ```C#
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

1. Copiez et collez le code suivant dans votre application (n’oubliez pas de mettre à jour les trois variables : `tenantId` , `clientId` , `appSecret` ) :

    ```C#
    string tenantId = ""; // Paste your directory (tenant) ID here
    string clientId = ""; // Paste your application (client) ID here
    string appSecret = ""; // Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

    const string authority = "https://login.windows.net";
    const string wdatpResourceId = "https://api.security.microsoft.com";

    AuthenticationContext auth = new AuthenticationContext($"{authority}/{tenantId}/");
    ClientCredential clientCredential = new ClientCredential(clientId, appSecret);
    AuthenticationResult authenticationResult = auth.AcquireTokenAsync(wdatpResourceId, clientCredential).GetAwaiter().GetResult();
    string token = authenticationResult.AccessToken;
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

resourceAppIdUri = 'https://api.securitycenter.windows.com'

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

### <a name="get-an-access-token-using-curl"></a>Obtenir un jeton d’accès à l’aide de la boucle

> [!NOTE]
> La fonction bouclé est préinstallée sur Windows 10, versions 1803 et ultérieures. Pour les autres versions de Windows, téléchargez et installez l’outil directement à partir du [site Web officiel](https://curl.haxx.se/windows/).

1. Ouvrez une invite de commandes et définissez CLIENT_ID à votre ID d’application Azure.

1. Définissez CLIENT_SECRET à la clé secrète de votre application Azure.

1. Définissez TENANT_ID sur l’ID de client Azure du client qui souhaite utiliser votre application pour accéder à Microsoft 365 Defender.

1. Exécutez la commande suivante :

   ```bash
   curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
   ```

   Une réponse réussie se présente comme suit :

   ```bash
   {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
   ```

## <a name="validate-the-token"></a>Valider le jeton

1. Copiez et collez le jeton dans le site Web du [validateur de jeton Web JSON, JWT,](https://jwt.ms) pour le décoder.

1. Assurez-vous que la revendication de *rôles* dans le jeton décodé contient les autorisations souhaitées.

   Dans l’image suivante, vous pouvez voir un jeton décodé acquis à partir d’une application, avec `Incidents.Read.All` , `Incidents.ReadWrite.All` et des `AdvancedHunting.Read.All` autorisations :

   ![Image de la validation du jeton](../../media/webapp-decoded-token.png)

## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>Utiliser le jeton pour accéder à l’API Microsoft 365 Defender

1. Choisissez l’API que vous souhaitez utiliser (incidents ou chasse avancée). Pour plus d’informations, consultez la rubrique [API Microsoft 365 Defender prises en charge](api-supported.md).

2. Dans la requête HTTP que vous allez envoyer, définissez l’en-tête d’autorisation sur `"Bearer" <token>` , le *porteur* étant le modèle d’autorisation et le *jeton* comme jeton validé.

3. Le jeton expire dans une heure. Vous pouvez envoyer plusieurs demandes pendant ce temps avec le même jeton.

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
- [Créer une application « Hello World »](api-hello-world.md)
- [Créer une application pour accéder aux API Microsoft 365 Defender au nom d’un utilisateur](api-create-app-user-context.md)
- [Créer une application avec un accès partenaire mutualisée aux API Microsoft 365 Defender](api-partner-access.md)
- [En savoir plus sur les limites d’API et la gestion des licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
- [Gérer les secrets dans vos applications serveur avec le coffre de clés Azure](https://docs.microsoft.com/learn/modules/manage-secrets-with-azure-key-vault/)
- [Autorisation 2,0 OAuth pour l’authentification de l’utilisateur et l’accès à l’API](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
