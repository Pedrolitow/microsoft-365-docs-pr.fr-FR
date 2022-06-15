---
title: Créer une application pour accéder aux API Microsoft 365 Defender pour le compte d’un utilisateur
description: Découvrez comment accéder à Microsoft 365 Defender API pour le compte d’un utilisateur.
keywords: access, pour le compte de l’utilisateur, de l’API, de l’application, de l’utilisateur, du jeton d’accès, du jeton,
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
ms.openlocfilehash: 41f2763d73bbb9ed0b7ae32dce431cb2c1a4d71f
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102589"
---
# <a name="create-an-app-to-access-microsoft-365-defender-apis-on-behalf-of-a-user"></a>Créer une application pour accéder aux API Microsoft 365 Defender pour le compte d’un utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Cette page explique comment créer une application pour obtenir un accès par programmation à Microsoft 365 Defender pour le compte d’un seul utilisateur.

Si vous avez besoin d’un accès par programmation à Microsoft 365 Defender sans utilisateur défini (par exemple, si vous écrivez une application ou un démon en arrière-plan), consultez [Créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md). Si vous devez fournir l’accès à plusieurs locataires , par exemple, si vous servez une grande organisation ou un groupe de clients, consultez [Créer une application avec un accès partenaire à Microsoft 365 Defender API](api-partner-access.md). Si vous n’êtes pas sûr du type d’accès dont vous avez besoin, consultez [Első lépések](api-access.md).

Microsoft 365 Defender expose une grande partie de ses données et actions par le biais d’un ensemble d’API programmatiques. Ces API vous aident à automatiser les flux de travail et à utiliser les fonctionnalités de Microsoft 365 Defender. Cet accès à l’API nécessite une authentification OAuth2.0. Pour plus d’informations, consultez [Flow du code d’autorisation OAuth 2.0](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En général, vous devez effectuer les étapes suivantes pour utiliser ces API :

- Créez une application Azure Active Directory (Azure AD).
- Obtenez un jeton d’accès à l’aide de cette application.
- Utilisez le jeton pour accéder à Microsoft 365 Defender API.

Cet article explique comment :

- Créer une application Azure AD
- Obtenir un jeton d’accès pour Microsoft 365 Defender
- Valider le jeton

> [!NOTE]
> Lorsque vous accédez à Microsoft 365 Defender API pour le compte d’un utilisateur, vous avez besoin des autorisations d’application et des autorisations utilisateur appropriées.

> [!TIP]
> Si vous avez l’autorisation d’effectuer une action dans le portail, vous avez l’autorisation d’effectuer l’action dans l’API.

## <a name="create-an-app"></a>Créer une application

1. Connectez-vous à [Azure](https://portal.azure.com) en tant qu’utilisateur avec le rôle **Administrateur général** .

2. Accédez à **Azure Active Directory** >  **App-registraties** >  **En savoir plus sur l’inscription**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Option Nouvelle inscription dans le volet Gérer du Azure-Portal" lightbox="../../media/atp-azure-new-app2.png":::

3. Dans le formulaire, choisissez un nom pour votre application, entrez les informations suivantes pour l’URI de redirection, puis **sélectionnez Inscrire**.

   :::image type="content" source="../../media/nativeapp-create2.PNG" alt-text="Volet Inscription de l’application dans le Azure-Portal" lightbox="../../media/nativeapp-create2.PNG":::
   

   - **Type d’application :** Client public
   - **URI de redirection :** https://portal.azure.com

4. Dans la page de votre application, sélectionnez **Autorisations d’API Ajouter des** >  API **d’autorisation** > **que mon organisation utilise** >, tapez **Microsoft Threat Protection**, puis sélectionnez **Microsoft Threat Protection**. Votre application peut désormais accéder à Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* est un ancien nom pour Microsoft 365 Defender et n’apparaît pas dans la liste d’origine. Vous devez commencer à écrire son nom dans la zone de texte pour l’afficher.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Volet API de votre organisation dans le portail Microsoft 365 Defender" lightbox="../../media/apis-in-my-org-tab.PNG":::

   - Choisissez **Autorisations déléguées**. Choisissez les autorisations appropriées pour votre scénario (par exemple **Incident.Read**), puis sélectionnez **Ajouter des autorisations**.

     :::image type="content" source="../../media/request-api-permissions-delegated.PNG" alt-text="Volet Autorisations déléguées dans le portail Microsoft 365 Defender" lightbox="../../media/request-api-permissions-delegated.PNG":::

    > [!NOTE]
    > Vous devez sélectionner les autorisations appropriées pour votre scénario. *Lire tous les incidents* n’est qu’un exemple. Pour déterminer l’autorisation dont vous avez besoin, consultez la section **Autorisations** de l’API que vous souhaitez appeler.
    >
    > Par exemple, pour [exécuter des requêtes avancées](api-advanced-hunting.md), sélectionnez l’autorisation « Exécuter des requêtes avancées » ; pour [isoler un appareil](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), sélectionnez l’autorisation « Isoler l’ordinateur ».

5. Sélectionnez **Accorder le consentement de l’administrateur**. Chaque fois que vous ajoutez une autorisation, vous devez sélectionner **Accorder le consentement administrateur** pour qu’elle prenne effet.

   :::image type="content" source="../../media/grant-consent-delegated.PNG" alt-text="Volet d’octroi de consentement de l’administrateur dans le portail Microsoft 365 Defender" lightbox="../../media/grant-consent-delegated.PNG":::

6. Enregistrez votre ID d’application et votre ID de locataire dans un endroit sûr. Ils sont répertoriés sous **Vue d’ensemble** sur la page de votre application.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Volet Vue d’ensemble dans le portail Microsoft 365 Defender" lightbox="../../media/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Obtenir un jeton d’accès

Pour plus d’informations sur Azure Active Directory jetons, consultez le [didacticiel Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="get-an-access-token-on-behalf-of-a-user-using-powershell"></a>Obtenir un jeton d’accès pour le compte d’un utilisateur à l’aide de PowerShell

Utilisez la bibliothèque MSAL.PS pour acquérir des jetons d’accès avec des autorisations déléguées. Exécutez les commandes suivantes pour obtenir un jeton d’accès au nom d’un utilisateur :

```PowerShell
Install-Module -Name MSAL.PS # Install the MSAL.PS module from PowerShell Gallery

$TenantId = " " # Paste your directory (tenant) ID here.
$AppClientId="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" # Paste your application (client) ID here.

$MsalParams = @{
   ClientId = $AppClientId
   TenantId = $TenantId
   Scopes   = 'https://graph.microsoft.com/User.Read.All','https://graph.microsoft.com/Files.ReadWrite'
}

$MsalResponse = Get-MsalToken @MsalParams
$AccessToken  = $MsalResponse.AccessToken
 
$AccessToken # Display the token in PS console
```
## <a name="validate-the-token"></a>Valider le jeton

1. Copiez et collez le jeton dans [JWT](https://jwt.ms) pour le décoder.
2. Assurez-vous que la revendication *de rôles* dans le jeton décodé contient les autorisations souhaitées.

Dans l’image suivante, vous pouvez voir un jeton décodé acquis à partir d’une application, avec ```Incidents.Read.All```, ```Incidents.ReadWrite.All```et ```AdvancedHunting.Read.All``` des autorisations :

:::image type="content" source="../../media/defender-endpoint/webapp-decoded-token.png" alt-text="Section Autorisations dans le volet Jeton décodé dans le portail Microsoft 365 Defender" lightbox="../../media/defender-endpoint/webapp-decoded-token.png":::

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
- [Créer une application avec un accès partenaire multilocataire aux API Microsoft 365 Defender](api-partner-access.md)
- [En savoir plus sur les limites d’API et les licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
- [Autorisation OAuth 2.0 pour la connexion utilisateur et l’accès à l’API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
