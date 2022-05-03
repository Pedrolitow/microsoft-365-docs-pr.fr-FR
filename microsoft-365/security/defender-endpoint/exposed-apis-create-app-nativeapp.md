---
title: Utiliser Microsoft Defender pour point de terminaison API
ms.reviewer: ''
description: Découvrez comment concevoir une application Windows native pour obtenir un accès programmatique à Microsoft Defender pour point de terminaison sans utilisateur.
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
ms.openlocfilehash: aec4c7bdc0da76a6a52a8b8f19d89b8b54f3df9f
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173490"
---
# <a name="use-microsoft-defender-for-endpoint-apis"></a>Utiliser Microsoft Defender pour point de terminaison API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/index.yml)

> [!IMPORTANT]
> Les fonctionnalités de chasse avancées ne sont pas incluses dans Defender entreprise. Consultez [Comparer les Microsoft Defender pour les PME aux plans Microsoft Defender pour point de terminaison 1 et 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Cette page explique comment créer une application pour obtenir un accès programmatique à Defender pour point de terminaison pour le compte d’un utilisateur.

Si vous avez besoin d’un accès par programmation Microsoft Defender pour point de terminaison sans utilisateur, reportez-vous à [Access Microsoft Defender pour point de terminaison avec le contexte de l’application](exposed-apis-create-app-webapp.md).

Si vous n’êtes pas sûr de l’accès dont vous avez besoin, lisez la [page Introduction](apis-intro.md).

Microsoft Defender pour point de terminaison expose une grande partie de ses données et actions par le biais d’un ensemble d’API programmatiques. Ces API vous permettront d’automatiser les flux de travail et d’innover en fonction de Microsoft Defender pour point de terminaison fonctionnalités. L’accès à l’API nécessite l’authentification OAuth2.0. Pour plus d’informations, consultez [Flow du code d’autorisation OAuth 2.0](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En général, vous devez effectuer les étapes suivantes pour utiliser les API :

- Créer une application AAD
- Obtenir un jeton d’accès à l’aide de cette application
- Utiliser le jeton pour accéder à l’API Defender pour point de terminaison

Cette page explique comment créer une application AAD, obtenir un jeton d’accès pour Microsoft Defender pour point de terminaison et valider le jeton.

> [!NOTE]
> Lorsque vous accédez à Microsoft Defender pour point de terminaison API pour le compte d’un utilisateur, vous avez besoin de l’autorisation d’application et de l’autorisation utilisateur appropriées.
> Si vous n’êtes pas familiarisé avec les autorisations utilisateur sur Microsoft Defender pour point de terminaison, consultez [Gérer l’accès au portail à l’aide du contrôle d’accès en fonction du rôle](rbac.md).

> [!TIP]
> Si vous avez l’autorisation d’effectuer une action dans le portail, vous avez l’autorisation d’effectuer l’action dans l’API.

## <a name="create-an-app"></a>Créer une application

1. Connectez-vous à [Azure](https://portal.azure.com) avec un compte d’utilisateur qui a le rôle **Administrateur général** .

2. Accédez à **Azure Active Directory** \> **inscriptions d'applications** \> **Nouvelle inscription**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Page inscriptions d'applications dans le portail Microsoft Azure" lightbox="images/atp-azure-new-app2.png":::

3. Lorsque la page **Inscrire une application** s’affiche, saisissez les informations d’inscription de votre application :
   - **Nom** : saisissez un nom d’application cohérent qui s’affichera pour les utilisateurs de l’application.
   - **Types de compte pris en charge** : sélectionnez les comptes à prendre en charge par l’application.

     <br>

     |Types de comptes pris en charge|Description|
     |---|---|
     |**Comptes dans cet annuaire organisationnel uniquement**|Sélectionnez cette option si vous générez une application métier. Cette option n’est pas disponible si vous n’inscrivez pas l’application dans un annuaire. <p> Cette option s’applique à un compte Azure AD à locataire unique seulement. <p> Il s’agit de l’option par défaut, sauf si vous inscrivez l’application hors d’un annuaire. Dans les cas où l’application est inscrite hors d’un annuaire, l’option par défaut est comptes mutualisés Azure AD et comptes Microsoft personnels.|
     |**Comptes dans un annuaire organisationnel**|Sélectionnez cette option si vous souhaitez cibler tous les clients professionnels et éducatifs. <p> Cette option s’applique à un compte Azure AD multi-locataire seulement. <p> Si vous avez inscrit l’application comme compte Azure AD à locataire unique seulement, vous pouvez le mettre à jour vers un compte Azure AD multi-locataire et inversement via le panneau **Authentification**.|
     |**Comptes dans un annuaire organisationnel et comptes personnels Microsoft**|Sélectionnez cette option pour cibler l’ensemble le plus large de clients. <p> Cette option s’applique à des comptes Microsoft personnels et Azure AD multi-locataires. <p> Si vous avez inscrit l’application comme comptes Microsoft personnels et Azure AD multi-locataires, vous ne pouvez pas modifier cela dans l’interface utilisateur. Vous devez utiliser l’éditeur de manifeste de l’application pour modifier les types de compte pris en charge.|

   - **URI de redirection (facultatif)** : sélectionnez le type d’application que vous créez, **Web** ou **Client public (mobile et bureau)**, puis entrez l’URI de redirection (ou URL de réponse).

     - Pour les applications web, indiquez l’URL de base de votre application. Par exemple, `http://localhost:31544` peut être l’URL d’une application web en cours d’exécution sur votre ordinateur local. Les utilisateurs peuvent utiliser cette URL pour se connecter à une application web cliente.

     - Pour les applications de client public, indiquez l’URI utilisé par Azure AD pour renvoyer les réponses de jeton. Entrez une valeur spécifique de votre application, par exemple, `myapp://auth`.

     Pour accéder à des exemples spécifiques aux applications web ou natives, consultez les [Guides de démarrage rapides](/azure/active-directory/develop/#quickstarts).

     Lorsque vous avez terminé, sélectionnez **Inscrire**.

4. Autorisez votre application à accéder à Microsoft Defender pour point de terminaison et affectez-lui l’autorisation « Lire les alertes » :

   - Dans la page de votre application, sélectionnez **Autorisations d’API Ajouter des** \> API **d’autorisation** \> **que mon organisation utilise** > type **WindowsDefenderATP** , puis sélectionnez **Sur WindowsDefenderATP**.

     > [!NOTE]
     > *WindowsDefenderATP* n’apparaît pas dans la liste d’origine. Commencez à écrire son nom dans la zone de texte pour l’afficher.

     :::image type="content" alt-text="ajouter une autorisation." source="images/add-permission.png" lightbox="images/add-permission.png":::

   - Choisissez **Autorisations** \> déléguées **Alert.Read** > sélectionnez **Ajouter des autorisations**.

      :::image type="content" source="images/application-permissions-public-client.png" alt-text="Le type d’application et les volets d’autorisations" lightbox="images/application-permissions-public-client.png":::

   > [!IMPORTANT]
   > Sélectionnez les autorisations appropriées. Les alertes de lecture ne sont qu’un exemple.

     Par exemple :

     - Pour [exécuter des requêtes avancées](run-advanced-query-api.md), sélectionnez **Exécuter des requêtes avancées** .
     - Pour [isoler un appareil](isolate-machine.md), sélectionnez Isoler l’autorisation **de l’ordinateur** .
     - Pour déterminer l’autorisation dont vous avez besoin, consultez la section **Autorisations** dans l’API que vous souhaitez appeler.

   - Sélectionnez **Accorder le consentement**.

      > [!NOTE]
      > Chaque fois que vous ajoutez une autorisation, vous devez sélectionner le **consentement d’octroi** pour que la nouvelle autorisation prenne effet.

      :::image type="content" source="images/grant-consent.png" alt-text="Option de consentement de l’administrateur général" lightbox="images/grant-consent.png":::

5. Notez votre ID d’application et votre ID de locataire.

    Dans la page de votre application, accédez à **Vue d’ensemble** et copiez les informations suivantes :

    :::image type="content" source="images/app-and-tenant-ids.png" alt-text="ID d’application créé"  lightbox="images/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Obtenir un jeton d’accès

Pour plus d’informations sur AAD jetons, consultez [Azure AD didacticiel](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="using-c"></a>Utilisation de C\#

- Copiez/collez la classe ci-dessous dans votre application.
- Utilisez la méthode **AcquireUserTokenAsync** avec votre ID d’application, votre ID de locataire, votre nom d’utilisateur et votre mot de passe pour acquérir un jeton.

    ```csharp
    namespace WindowsDefenderATP
    {
        using System.Net.Http;
        using System.Text;
        using System.Threading.Tasks;
        using Newtonsoft.Json.Linq;

        public static class WindowsDefenderATPUtils
        {
            private const string Authority = "https://login.microsoftonline.com";

            private const string WdatpResourceId = "https://api.securitycenter.microsoft.com";

            public static async Task<string> AcquireUserTokenAsync(string username, string password, string appId, string tenantId)
            {
                using (var httpClient = new HttpClient())
                {
                    var urlEncodedBody = $"resource={WdatpResourceId}&client_id={appId}&grant_type=password&username={username}&password={password}";

                    var stringContent = new StringContent(urlEncodedBody, Encoding.UTF8, "application/x-www-form-urlencoded");

                    using (var response = await httpClient.PostAsync($"{Authority}/{tenantId}/oauth2/token", stringContent).ConfigureAwait(false))
                    {
                        response.EnsureSuccessStatusCode();

                        var json = await response.Content.ReadAsStringAsync().ConfigureAwait(false);

                        var jObject = JObject.Parse(json);

                        return jObject["access_token"].Value<string>();
                    }
                }
            }
        }
    }
    ```

## <a name="validate-the-token"></a>Valider le jeton

Vérifiez que vous avez obtenu un jeton correct :

- Copiez/collez dans [JWT](https://jwt.ms) le jeton que vous avez obtenu à l’étape précédente afin de le décoder.
- Vérifiez que vous obtenez une revendication « scp » avec les autorisations d’application souhaitées.
- Dans la capture d’écran ci-dessous, vous pouvez voir un jeton décodé acquis à partir de l’application dans le didacticiel :

  :::image type="content" source="images/nativeapp-decoded-token.png" alt-text="Page de validation de jeton" lightbox="images/nativeapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Utiliser le jeton pour accéder à Microsoft Defender pour point de terminaison API

- Choisissez l’API que vous souhaitez utiliser : [API Microsoft Defender pour point de terminaison prises en charge](exposed-apis-list.md).
- Définissez l’en-tête d’autorisation dans la requête HTTP que vous envoyez au « Porteur {token} » (le porteur est le schéma d’autorisation).
- L’heure d’expiration du jeton est de 1 heure (vous pouvez envoyer plusieurs demandes avec le même jeton).

- Exemple d’envoi d’une demande pour obtenir une liste d’alertes **à l’aide de C#** :

    ```csharp
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="see-also"></a>Voir aussi

- [API Microsoft Defender pour point de terminaison](exposed-apis-list.md)
- [Accéder Microsoft Defender pour point de terminaison avec le contexte d’application](exposed-apis-create-app-webapp.md)
