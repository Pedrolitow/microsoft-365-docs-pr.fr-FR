---
title: Créer une application pour accéder Microsoft 365 Defender API au nom d’un utilisateur
description: Découvrez comment accéder à Microsoft 365 Defender API au nom d’un utilisateur.
keywords: access, de la part de l’utilisateur, de l’api, de l’application, de l’utilisateur, du jeton d’accès, du jeton,
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: fdba7ee1b1cf2f46bd17c648c7cda48f1ca65490
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755214"
---
# <a name="create-an-app-to-access-microsoft-365-defender-apis-on-behalf-of-a-user"></a>Créer une application pour accéder Microsoft 365 Defender API au nom d’un utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Cette page explique comment créer une application pour obtenir un accès par programme à Microsoft 365 Defender pour le compte d’un seul utilisateur.

Si vous avez besoin d’un accès par programme à Microsoft 365 Defender sans utilisateur défini (par exemple, si vous écrivez une application en arrière-plan ou un daemon), voir Créer une application pour accéder à [Microsoft 365 Defender](api-create-app-web.md) sans utilisateur. Si vous devez fournir l’accès à plusieurs clients, par exemple, si vous fournissez des services à une grande organisation ou à un groupe de clients, voir Créer une application avec un accès partenaire aux API [Microsoft 365 Defender client.](api-partner-access.md) Si vous ne savez pas quel type d’accès vous avez besoin, consultez [La mise en place](api-access.md).

Microsoft 365 Defender expose la plupart de ses données et actions par le biais d’un ensemble d’API de programmation. Ces API vous aident à automatiser les flux de travail et à utiliser Microsoft 365 Defender fonctionnalités de l’utilisateur. Cet accès à l’API nécessite une authentification OAuth2.0. Pour plus d’informations, [voir code d’autorisation OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En règle générale, vous devez suivre les étapes suivantes pour utiliser ces API :

- Créez une application Azure Active Directory (Azure AD).
- Obtenez un jeton d’accès à l’aide de cette application.
- Utilisez le jeton pour accéder à Microsoft 365 Defender API.

Cet article explique comment :

- Créer une application Azure AD
- Obtenir un jeton d’accès Microsoft 365 Defender
- Valider le jeton

> [!NOTE]
> Lorsque vous accédez Microsoft 365 Defender API au nom d’un utilisateur, vous avez besoin des autorisations d’application et des autorisations utilisateur correctes.

> [!TIP]
> Si vous avez l’autorisation d’effectuer une action dans le portail, vous avez l’autorisation d’effectuer l’action dans l’API.

## <a name="create-an-app"></a>Créer une application

1. Connectez-vous [à Azure](https://portal.azure.com) en tant qu’utilisateur avec le **rôle Administrateur** général.

2. Accédez à **Azure Active Directory** >  **App registrationsNew** >  **registration**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Option Nouvelle inscription dans le volet Gérer dans le portail Azure" lightbox="../../media/atp-azure-new-app2.png":::

3. Dans le formulaire, choisissez un nom pour votre application, entrez les informations suivantes pour l’URI de redirection, puis sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/nativeapp-create2.PNG" alt-text="Volet d’inscription des applications dans le portail Azure" lightbox="../../media/nativeapp-create2.PNG":::
   

   - **Type d’application :** Client public
   - **URI de redirection :** https://portal.azure.com

4. Dans la page de votre application, sélectionnez Autorisations DE **L’API AutorisationSi** >  >  que mon organisation **utilise >,** tapez **Protection Microsoft** contre les menaces, puis sélectionnez **Protection Microsoft contre les menaces**. Votre application peut désormais accéder à Microsoft 365 Defender.

   > [!TIP]
   > *La Protection Microsoft contre les* menaces est un ancien nom Microsoft 365 Defender et n’apparaît pas dans la liste d’origine. Vous devez commencer à écrire son nom dans la zone de texte pour qu’il apparaisse.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Volet API de votre organisation dans le portail Microsoft 365 Defender" lightbox="../../media/apis-in-my-org-tab.PNG":::

   - Choisissez **Autorisations déléguées**. Choisissez les autorisations pertinentes pour votre scénario (par exemple **Incident.Read**), puis **sélectionnez Ajouter des autorisations**.

     :::image type="content" source="../../media/request-api-permissions-delegated.PNG" alt-text="Volet Autorisations déléguées dans le portail Microsoft 365 Defender" lightbox="../../media/request-api-permissions-delegated.PNG":::

    > [!NOTE]
    > Vous devez sélectionner les autorisations pertinentes pour votre scénario. *Lire tous les incidents* n’est qu’un exemple. Pour déterminer l’autorisation qui vous est nécessaire, consultez la section **Autorisations** de l’API que vous voulez appeler.
    >
    > Par exemple, pour [exécuter des requêtes avancées](api-advanced-hunting.md), sélectionnez l’autorisation « Exécuter des requêtes avancées » ; pour [isoler un appareil](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), sélectionnez l’autorisation « Isoler l’ordinateur ».

5. Sélectionnez **Accorder le consentement de l’administrateur**. Chaque fois que vous ajoutez une autorisation, vous devez sélectionner **Accorder le consentement de l’administrateur** pour qu’elle prenne effet.

   :::image type="content" source="../../media/grant-consent-delegated.PNG" alt-text="Volet d’octroi de consentement de l’administrateur dans le Microsoft 365 Defender web" lightbox="../../media/grant-consent-delegated.PNG":::

6. Enregistrez votre ID d’application et votre ID de client dans un endroit sûr. Ils sont répertoriés sous Vue **d’ensemble** sur la page de votre application.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Volet Vue d’ensemble du portail Microsoft 365 Defender web" lightbox="../../media/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Obtenir un jeton d’accès

Pour plus d’informations sur les jetons Azure Active Directory, voir le [didacticiel Azure AD’aide](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="get-an-access-token-using-powershell"></a>Obtenir un jeton d’accès à l’aide de PowerShell

```PowerShell
if(!(Get-Package adal.ps)) { Install-Package -Name adal.ps } # Install the ADAL.PS package in case it's not already present

$tenantId = '' # Paste your directory (tenant) ID here.
$clientId = '' # Paste your application (client) ID here.
$redirectUri = '' # Paste your app's redirection URI

$authority = "https://login.windows.net/$tenantId"
$resourceUrl = 'https://api.security.microsoft.com'

$response = Get-ADALToken -Resource $resourceUrl -ClientId $clientId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:Always
$response.AccessToken | clip

$response.AccessToken
```

## <a name="validate-the-token"></a>Valider le jeton

1. Copiez et collez le jeton dans [JWT](https://jwt.ms) pour le décoder.
1. Assurez-vous que la revendication *de rôles* dans le jeton décodé contient les autorisations souhaitées.

Dans l’image suivante, vous pouvez voir un jeton décodé acquis à partir d’une application, ```Incidents.Read.All```avec , ```Incidents.ReadWrite.All```et des ```AdvancedHunting.Read.All``` autorisations :

:::image type="content" source="../../media/defender-endpoint/webapp-decoded-token.png" alt-text="Section Autorisations dans le volet Jeton décodé du portail Microsoft 365 Defender" lightbox="../../media/defender-endpoint/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>Utiliser le jeton pour accéder à l’API Microsoft 365 Defender de connexion

1. Choisissez l’API que vous souhaitez utiliser (incidents ou recherche avancée). Pour plus d’informations, [voir API Microsoft 365 Defender pris en charge](api-supported.md).
2. Dans la requête http que vous êtes sur le point d’envoyer, `"Bearer" <token>`définissez l’en-tête d’autorisation *sur , le* porteur étant le schéma d’autorisation et le jeton comme jeton validé.
3. Le jeton expire dans un délai d’une heure. Vous pouvez envoyer plusieurs demandes pendant cette période avec le même jeton.

L’exemple suivant montre comment envoyer une demande pour obtenir une liste d’incidents à l’aide **C#**.

```C#
    var httpClient = new HttpClient();
    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/incidents");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();
```

## <a name="related-articles"></a>Articles connexes

- [présentation Microsoft 365 Defender API de Microsoft 365 Defender’api](api-overview.md)
- [Accéder aux API Microsoft 365 Defender de données](api-access.md)
- [Créer une application « Hello World »](api-hello-world.md)
- [Créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md)
- [Créer une application avec un accès partenaire multi-locataire aux API Microsoft 365 Defender client](api-partner-access.md)
- [En savoir plus sur les limites d’API et les licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
- [Autorisation OAuth 2.0 pour la connexion de l’utilisateur et l’accès à l’API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
