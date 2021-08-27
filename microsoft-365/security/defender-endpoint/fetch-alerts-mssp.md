---
title: Récupérer des alertes à partir du client MSSP client
description: Découvrez comment récupérer des alertes à partir d’un client
keywords: fournisseur de services de sécurité géré, mssp, configurer, intégration
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: a8e67bda0a33699f3d1934d943dd52db5a3354be
ms.sourcegitcommit: 132b8dc316bcd4b456de33d6a30e90ca69b0f956
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58610952"
---
# <a name="fetch-alerts-from-mssp-customer-tenant"></a>Récupérer des alertes à partir du client MSSP client

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> Cette action est prise par le MSSP.

Il existe deux façons d’extraire des alertes :

- Utilisation de la méthode SIEM
- Utilisation des API

## <a name="fetch-alerts-into-your-siem"></a>Récupérer des alertes dans votre SIEM

Pour récupérer des alertes dans votre système SIEM, vous devez suivre les étapes suivantes :

- Étape 1 : Créer une application tierce
- Étape 2 : Obtenir des jetons d’accès et d’actualisation à partir du client de votre client
- Étape 3 : autoriser votre application sur Microsoft 365 Defender

### <a name="step-1-create-an-application-in-azure-active-directory-azure-ad"></a>Étape 1 : Créer une application dans Azure Active Directory (Azure AD)

Vous devez créer une application et lui accorder des autorisations pour récupérer des alertes à partir du client Microsoft Defender for Endpoint de votre client.

1. Connectez-vous au [portail Azure AD.](https://aad.portal.azure.com/)

2. Sélectionnez **Azure Active Directory** \> **inscriptions d’application.**

3. Cliquez **sur Nouvelle inscription.**

4. Spécifiez les valeurs suivantes :

    - Nom : \<Tenant_name\> Connecteur MSSP SIEM (remplacez Tenant_name par le nom complet du client)

    - Types de comptes pris en charge : compte dans cet annuaire d’organisation uniquement
    - URI de redirection : sélectionnez Web et tapez `https://<domain_name>/SiemMsspConnector` (remplacez <domain_name> par le nom du client)

5. Cliquez sur **S'inscrire**. L’application s’affiche dans la liste des applications que vous possédez.

6. Sélectionnez l’application, puis cliquez sur **Vue d’ensemble.**

7. Copiez la valeur du champ ID de **l’application (client)** dans un endroit sûr. Vous en aurez besoin à l’étape suivante.

8. Sélectionnez **Certificat & secrets dans** le nouveau panneau d’application.

9. Cliquez **sur Nouvelle secret client**.

    - Description : entrez une description de la clé.
    - Expire : sélection **dans 1 an**

10. Cliquez **sur** Ajouter , copiez la valeur de la question secrète client dans un endroit sûr. Vous en aurez besoin à l’étape suivante.

### <a name="step-2-get-access-and-refresh-tokens-from-your-customers-tenant"></a>Étape 2 : Obtenir des jetons d’accès et d’actualisation à partir du client de votre client

Cette section vous guide sur l’utilisation d’un script PowerShell pour obtenir les jetons du client de votre client. Ce script utilise l’application de l’étape précédente pour obtenir les jetons d’accès et d’actualisation à l’aide du code d’autorisation OAuth Flow.

Après avoir fourni vos informations d’identification, vous devez donner votre consentement à l’application afin que l’application soit mise en service dans le client du client.

1. Créez un dossier et nommez-le : `MsspTokensAcquisition` .

2. Téléchargez [le module LoginBrowser.psm1](https://github.com/shawntabrizi/Microsoft-Authentication-with-PowerShell-and-MSAL/blob/master/Authorization%20Code%20Grant%20Flow/LoginBrowser.psm1) et enregistrez-le dans le `MsspTokensAcquisition` dossier.

    > [!NOTE]
    > À la ligne 30, `authorzationUrl` remplacez par `authorizationUrl` .

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
4. Ouvrez une invite de commandes PowerShell avec élévation de niveaux dans le `MsspTokensAcquisition` dossier.

5. Exécutez la commande suivante : `Set-ExecutionPolicy -ExecutionPolicy Bypass`

6. Entrez les commandes suivantes : `.\MsspTokensAcquisition.ps1 -clientId <client_id> -secret <app_key> -tenantId <customer_tenant_id>`

    - \<client_id\>Remplacez-le **par l’ID d’application (client)** obtenu à l’étape précédente.
    - Remplacez \<app_key\> par la secret client **que** vous avez créée à l’étape précédente.
    - Remplacez \<customer_tenant_id\> par l’ID de **locataire de votre client.**

7. Vous serez invité à fournir vos informations d’identification et votre consentement. Ignorez la redirection de page.

8. Dans la fenêtre PowerShell, vous recevrez un jeton d’accès et un jeton d’actualisation. Enregistrez le jeton d’actualisation pour configurer votre connecteur SIEM.

### <a name="step-3-allow-your-application-on-microsoft-365-defender"></a>Étape 3 : Autoriser votre application sur Microsoft 365 Defender

Vous devez autoriser l’application que vous avez créée dans Microsoft 365 Defender.

Vous devez avoir l’autorisation Gérer les **paramètres système** du portail pour autoriser l’application. Dans le cas contraire, vous devrez demander à votre client d’autoriser l’application pour vous.

1. Go to `https://security.microsoft.com?tid=<customer_tenant_id>` (replace \<customer_tenant_id\> with the customer's tenant ID.

2. Cliquez **Paramètres** \> **LES API de points de** \> **terminaison** \> **SIEM.**

3. Sélectionnez **l’onglet MSSP.**

4. Entrez **l’ID d’application** à partir de la première étape et votre **ID de client.**

5. Cliquez **sur Autoriser l’application.**

Vous pouvez maintenant télécharger le fichier de configuration approprié pour votre SIEM et vous connecter à l’API Defender for Endpoint. Pour plus d’informations, voir [« Tirer des alertes vers vos outils SIEM](configure-siem.md)».

- Dans le fichier de configuration ArcSight /Splunk Authentication Properties, écrivez votre clé d’application manuellement en définir la valeur secrète.
- Au lieu d’acquérir un jeton d’actualisation dans le portail, utilisez le script de l’étape précédente pour acquérir un jeton d’actualisation (ou l’acquérir par d’autres moyens).

## <a name="fetch-alerts-from-mssp-customers-tenant-using-apis"></a>Récupérer des alertes à partir du client MSSP client à l’aide des API

Pour plus d’informations sur la récupération d’alertes à l’aide de l’API REST, voir [Extraire des alertes à l’aide de l’API REST.](pull-alerts-using-rest-api.md)

## <a name="see-also"></a>Voir aussi

- [Accorder l’accès MSSP au portail](grant-mssp-access.md)
- [Accéder au portail client MSSP](access-mssp-portal.md)
- [Configurer des notifications d’alerte](configure-mssp-notifications.md)
