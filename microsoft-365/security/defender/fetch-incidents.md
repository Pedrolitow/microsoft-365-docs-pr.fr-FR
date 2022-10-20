---
title: Récupérer les incidents Microsoft 365 Defender
description: Découvrez comment récupérer Microsoft 365 Defender incidents à partir d’un locataire client
keywords: fournisseur de services de sécurité managé, mssp, configure, integration
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m65-security-compliance
- tier3
ms.topic: conceptual
ms.custom: api
ms.openlocfilehash: 968fbce5b913835b303246144fe049761b8d2bf9
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68645602"
---
# <a name="fetch-microsoft-365-defender-incidents"></a>Récupérer les incidents Microsoft 365 Defender 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> [!NOTE]
> Cette action est effectuée par le MSSP.

Il existe deux façons d’extraire des alertes :

- Utilisation de la méthode SIEM
- Utilisation d’API

## <a name="fetch-incidents-into-your-siem"></a>Récupérer des incidents dans votre SIEM

Pour extraire des incidents dans votre système SIEM, vous devez effectuer les étapes suivantes :

- Étape 1 : Créer une application tierce
- Étape 2 : Obtenir des jetons d’accès et d’actualisation auprès du locataire de votre client
- Étape 3 : autoriser votre application sur Microsoft 365 Defender

### <a name="step-1-create-an-application-in-azure-active-directory-azure-ad"></a>Étape 1 : Créer une application dans Azure Active Directory (Azure AD)

Vous devez créer une application et lui accorder des autorisations pour extraire des alertes du locataire Microsoft 365 Defender de votre client.

1. Connectez-vous au [portail Azure AD](https://aad.portal.azure.com/).

2. Sélectionnez **Azure Active Directory** \> **inscriptions d'applications**.

3. Cliquez sur **Nouvelle inscription**.

4. Spécifiez les valeurs suivantes :

    - Nom : \<Tenant_name\> Connecteur SIEM MSSP (remplacez Tenant_name par le nom d’affichage du locataire)

    - Types de comptes pris en charge : compte dans cet annuaire organisationnel uniquement
    - URI de redirection : sélectionnez Web et type `https://<domain_name>/SiemMsspConnector`(remplacez <domain_name> par le nom du locataire)

5. Cliquez sur **S'inscrire**. L’application s’affiche dans la liste des applications dont vous êtes propriétaire.

6. Sélectionnez l’application, puis cliquez sur **Vue d’ensemble**.

7. Copiez la valeur du champ **ID d’application (client)** dans un emplacement sûr. Vous en aurez besoin à l’étape suivante.

8. Sélectionnez **Certificat & secrets** dans le nouveau panneau d’application.

9. Cliquez sur **Nouveau secret client**.

    - Description : entrez une description de la clé.
    - Expire : Sélectionner **dans 1 an**

10. Cliquez sur **Ajouter**, copiez la valeur de la clé secrète client dans un emplacement sûr. Vous en aurez besoin à l’étape suivante.

### <a name="step-2-get-access-and-refresh-tokens-from-your-customers-tenant"></a>Étape 2 : Obtenir des jetons d’accès et d’actualisation auprès du locataire de votre client

Cette section vous guide sur l’utilisation d’un script PowerShell pour obtenir les jetons du locataire de votre client. Ce script utilise l’application de l’étape précédente pour obtenir les jetons d’accès et d’actualisation à l’aide du flux de code d’autorisation OAuth.

Après avoir fourni vos informations d’identification, vous devez accorder le consentement à l’application afin que l’application soit approvisionnée dans le locataire du client.

1. Créez un dossier et nommez-le : `MsspTokensAcquisition`.

2. Téléchargez le [module LoginBrowser.psm1](https://github.com/shawntabrizi/Microsoft-Authentication-with-PowerShell-and-MSAL/blob/master/Authorization%20Code%20Grant%20Flow/LoginBrowser.psm1) et enregistrez-le dans le `MsspTokensAcquisition` dossier.

    > [!NOTE]
    > Dans la ligne 30, remplacez par `authorzationUrl` `authorizationUrl`.

3. Créez un fichier avec le contenu suivant et enregistrez-le avec le nom `MsspTokensAcquisition.ps1` dans le dossier :

    ```powershell
    param (
        [Parameter(Mandatory=$true)][string]$clientId,
        [Parameter(Mandatory=$true)][string]$secret,
        [Parameter(Mandatory=$true)][string]$tenantId
    )
    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12

    # Load our Login Browser Function
    Import-Module .\LoginBrowser.psm1

    # Configuration parameters
    $login = "https://login.microsoftonline.com"
    $redirectUri = "https://SiemMsspConnector"
    $resourceId = "https://graph.windows.net"

    Write-Host 'Prompt the user for his credentials, to get an authorization code'
    $authorizationUrl = ("{0}/{1}/oauth2/authorize?prompt=select_account&response_type=code&client_id={2}&redirect_uri={3}&resource={4}" -f
                        $login, $tenantId, $clientId, $redirectUri, $resourceId)
    Write-Host "authorzationUrl: $authorizationUrl"

    # Fake a proper endpoint for the Redirect URI
    $code = LoginBrowser $authorizationUrl $redirectUri

    # Acquire token using the authorization code

    $Body = @{
        grant_type = 'authorization_code'
        client_id = $clientId
        code = $code
        redirect_uri = $redirectUri
        resource = $resourceId
        client_secret = $secret
    }

    $tokenEndpoint = "$login/$tenantId/oauth2/token?"
    $Response = Invoke-RestMethod -Method Post -Uri $tokenEndpoint -Body $Body
    $token = $Response.access_token
    $refreshToken= $Response.refresh_token

    Write-Host " ----------------------------------- TOKEN ---------------------------------- "
    Write-Host $token

    Write-Host " ----------------------------------- REFRESH TOKEN ---------------------------------- "
    Write-Host $refreshToken
    ```
4. Ouvrez une invite de commandes PowerShell avec élévation de privilèges dans le `MsspTokensAcquisition` dossier.

5. Exécutez la commande suivante : `Set-ExecutionPolicy -ExecutionPolicy Bypass`

6. Entrez les commandes suivantes : `.\MsspTokensAcquisition.ps1 -clientId <client_id> -secret <app_key> -tenantId <customer_tenant_id>`

    - Remplacez \<client_id\> par **l’ID d’application (client)** obtenu à l’étape précédente.
    - Remplacez \<app_key\> par la **clé secrète client** que vous avez créée à l’étape précédente.
    - Remplacez par \<customer_tenant_id\> **l’ID de locataire** de votre client.

7. Vous serez invité à fournir vos informations d’identification et votre consentement. Ignorez la redirection de page.

8. Dans la fenêtre PowerShell, vous recevrez un jeton d’accès et un jeton d’actualisation. Enregistrez le jeton d’actualisation pour configurer votre connecteur SIEM.

### <a name="step-3-allow-your-application-on-microsoft-365-defender"></a>Étape 3 : Autoriser votre application sur Microsoft 365 Defender

Vous devez autoriser l’application que vous avez créée dans Microsoft 365 Defender.

Vous devez disposer de l’autorisation **Gérer les paramètres système du portail** pour autoriser l’application. Sinon, vous devrez demander à votre client d’autoriser l’application pour vous.

1. Accédez à `https://security.microsoft.com?tid=<customer_tenant_id>` (remplacez \<customer_tenant_id\> par l’ID de locataire du client.

2. Cliquez sur **PARAMÈTRES** \> **POINTS DE TERMINAISON** \> **API** \> **SIEM**.

3. Sélectionnez l’onglet **MSSP** .

4. Entrez **l’ID d’application** de la première étape et votre **ID de locataire**.

5. Cliquez sur **Autoriser l’application**.

Vous pouvez maintenant télécharger le fichier de configuration approprié pour votre SIEM et vous connecter à l’API Microsoft 365 Defender. Pour plus d’informations, consultez Les [alertes d’extraction vers vos outils SIEM](../defender-endpoint/configure-siem.md).

- Dans le fichier de configuration ArcSight /Fichier de propriétés d’authentification Splunk, écrivez votre clé d’application manuellement en définissant la valeur du secret.
- Au lieu d’acquérir un jeton d’actualisation dans le portail, utilisez le script de l’étape précédente pour acquérir un jeton d’actualisation (ou l’acquérir par d’autres moyens).

## <a name="fetch-alerts-from-mssp-customers-tenant-using-apis"></a>Récupérer des alertes à partir du locataire du client MSSP à l’aide d’API

Pour plus d’informations sur la récupération des alertes à l’aide de l’API REST, consultez [Les alertes pull à l’aide de l’API REST](../defender-endpoint/pull-alerts-using-rest-api.md).
