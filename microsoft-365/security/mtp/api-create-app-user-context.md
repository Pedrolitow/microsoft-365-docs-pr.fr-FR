---
title: Créer une application pour accéder aux API Microsoft 365 Defender au nom d’un utilisateur
description: Découvrez comment accéder aux API Microsoft 365 Defender au nom d’un utilisateur.
keywords: accès, de la part de l’utilisateur, de l’API, de l’application, de l’utilisateur, du jeton d’accès, du jeton
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
ms.openlocfilehash: f1c0caea9ff7810f79026c789241a4f250ec5303
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719415"
---
# <a name="create-an-app-to-access-microsoft-365-defender-apis-on-behalf-of-a-user"></a>Créer une application pour accéder aux API Microsoft 365 Defender au nom d’un utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Cette page explique comment créer une application pour accéder par programme à Microsoft 365 Defender au nom d’un utilisateur unique.

Si vous avez besoin d’un accès par programme à Microsoft 365 Defender sans utilisateur défini (par exemple, si vous écrivez une application ou un démon en arrière-plan), consultez la rubrique [créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md). Si vous devez fournir un accès à plusieurs clients (par exemple, si vous utilisez une grande organisation ou un groupe de clients), voir [créer une application avec un accès partenaire aux API Microsoft 365 Defender](api-partner-access.md). Si vous n’êtes pas certain du type d’accès dont vous avez besoin, consultez la rubrique [prise en main](api-access.md).

Microsoft 365 Defender expose une grande partie de ses données et actions via un ensemble d’API de programmation. Ces API vous aident à automatiser les flux de travail et à utiliser les fonctionnalités de Microsoft 365 Defender. Cet accès à l’API nécessite l’authentification OAuth 2.0. Pour plus d’informations, reportez-vous au [flux de code d’autorisation OAuth 2,0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En règle générale, vous devez effectuer les étapes suivantes pour utiliser ces API :

- Créez une application Azure Active Directory (Azure AD).
- Obtenir un jeton d’accès à l’aide de cette application.
- Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Cet article explique comment :

- Créer une application Azure AD
- Obtenir un jeton d’accès à Microsoft 365 Defender
- Valider le jeton

> [!NOTE]
> Lors de l’accès à l’API Microsoft 365 Defender au nom d’un utilisateur, vous devez disposer des autorisations d’application et des autorisations utilisateur correctes.

> [!TIP]
> Si vous disposez de l’autorisation pour effectuer une action dans le portail, vous disposez de l’autorisation pour effectuer l’action dans l’API.

## <a name="create-an-app"></a>Créer une application

1. Connectez-vous à [Azure](https://portal.azure.com) en tant qu’utilisateur doté du rôle d' **administrateur général** .

2. Accédez à **Azure Active Directory**  >  **app Registrations**  >  **New Registration**.

   ![Image de Microsoft Azure et navigation de l’application](../../media/atp-azure-new-app2.png)

3. Dans le formulaire, choisissez un nom pour votre application et entrez les informations suivantes pour l’URI de redirection, puis sélectionnez **Enregistrer**.

   ![Image de la fenêtre créer une application](../../media/nativeapp-create2.PNG)

   - **Type d’application :** Client public
   - **URI de redirection :**https://portal.azure.com

4. Sur la page de votre application, sélectionnez **autorisations d’API**  >  **Ajouter une**  >  **API mon organisation utilise** des >, tapez **Microsoft Threat Protection**, puis sélectionnez **Microsoft Threat Protection**. Votre application peut maintenant accéder à Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* est un ancien nom pour Microsoft 365 Defender et n’apparaît pas dans la liste d’origine. Vous devez commencer à écrire son nom dans la zone de texte pour l’afficher.

   ![Image de la sélection des autorisations de l’API](../../media/apis-in-my-org-tab.PNG)

   - Sélectionnez **autorisations déléguées**. Choisissez les autorisations appropriées pour votre scénario (par exemple, **incident. Read**), puis sélectionnez **Ajouter des autorisations**.

   ![Image de l’accès à l’API et de la sélection de l’API](../../media/request-api-permissions-delegated.PNG)

    > [!NOTE]
    > Vous devez sélectionner les autorisations appropriées pour votre scénario. *Read All incidents* n’est qu’un exemple. Pour déterminer les autorisations qui vous sont nécessaires, consultez la section **autorisations** dans l’API que vous souhaitez appeler.
    >
    > Par exemple, pour [exécuter des requêtes avancées](api-advanced-hunting.md), sélectionnez l’autorisation « exécuter des requêtes avancées »; pour [isoler un appareil](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), sélectionnez l’autorisation « isoler l’ordinateur ».

5. Sélectionnez **accorder le consentement** de l’administrateur. Chaque fois que vous ajoutez une autorisation, vous devez sélectionner **accorder le consentement** de l’administrateur pour qu’elle prenne effet.

   ![Image des autorisations accorder](../../media/grant-consent-delegated.PNG)

6. Enregistrez votre ID d’application et votre ID de client dans un endroit sûr. Elles sont indiquées sous **vue d’ensemble** sur votre application.

   ![Image de l’ID d’application créé](../../media/app-and-tenant-ids.png)

## <a name="get-an-access-token"></a>Obtenir un jeton d’accès

Pour plus d’informations sur les jetons Azure Active Directory, consultez le [didacticiel Azure ad](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="get-an-access-token-using-powershell"></a>Obtenir un jeton d’accès à l’aide de PowerShell

```PowerShell
if(!(Get-Package adal.ps)) { Install-Package -Name adal.ps } # Install the ADAL.PS package in case it's not already present

$tenantId = '' # Paste your directory (tenant) ID here.
$clientId = '' # Paste your application (client) ID here.
$redirectUri = '' # Paste your app's redirection URI

$authority = "https://login.windows.net/$tenantId"
$resourceUrl = 'https://api.security.microsoft.com'

$response = Get-ADALToken -Resource $resourceUrl -ClientId $cleintId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:Always
$response.AccessToken | clip

$response.AccessToken
```

## <a name="validate-the-token"></a>Valider le jeton

1. Copiez et collez le jeton dans [JWT](https://jwt.ms) pour le décoder.
1. Assurez-vous que la revendication de *rôles* dans le jeton décodé contient les autorisations souhaitées.

Dans l’image suivante, vous pouvez voir un jeton décodé acquis à partir d’une application, avec ```Incidents.Read.All``` , ```Incidents.ReadWrite.All``` et des ```AdvancedHunting.Read.All``` autorisations :

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
- [Créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md)
- [Créer une application avec un accès partenaire mutualisée aux API Microsoft 365 Defender](api-partner-access.md)
- [En savoir plus sur les limites d’API et la gestion des licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
- [Autorisation 2,0 OAuth pour l’authentification de l’utilisateur et l’accès à l’API](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
