---
title: Hello World pour l’API REST Microsoft Threat Protection
description: Découvrez comment créer une application et utiliser un jeton pour accéder aux API de protection contre les menaces Microsoft
keywords: application, jeton, Access, AAD, app, inscription de l’application, PowerShell, script, administrateur global, autorisation
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
ms.openlocfilehash: cdf3f6a0c007763d2772233b1a299d59c931b2e5
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48201326"
---
# <a name="hello-world-for-microsoft-threat-protection-rest-api"></a>Hello World pour l’API REST Microsoft Threat Protection 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

>[!IMPORTANT] 
>Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.


## <a name="get-incidents-using-a-simple-powershell-script"></a>Obtenir des incidents à l’aide d’un script PowerShell simple

### <a name="how-long-it-takes-to-go-through-this-example"></a>Combien de temps faut-il pour suivre cet exemple ?
Il faut seulement 5 minutes en deux étapes :
- Inscription de l’application
- Utiliser des exemples : nécessite uniquement une opération copier/coller d’un court script PowerShell

### <a name="do-i-need-a-permission-to-connect"></a>Ai-je besoin d’une autorisation pour se connecter ?
Pour l’étape d’inscription de l’application, vous devez disposer d’un rôle d' **administrateur général** dans votre client Azure Active Directory (Azure AD).

### <a name="step-1---create-an-app-in-azure-active-directory"></a>Étape 1 : créer une application dans Azure Active Directory

1. Connectez-vous à [Azure](https://portal.azure.com) avec votre utilisateur d' **administrateur général** .

2. Accédez à **Azure Active Directory**  >  **app Registrations**  >  **New Registration**. 

   ![Image de Microsoft Azure et navigation de l’application](../../media/atp-azure-new-app2.png)

3. Dans le formulaire d’inscription, choisissez un nom pour votre application, puis sélectionnez **Enregistrer**.

4. Autorisez votre application à accéder à Microsoft Defender ATP et attribuez-lui l’autorisation **lire tous les incidents** :

   - Sur la page de votre application, sélectionnez **autorisations d’API**  >  **Ajouter une**  >  **API mon organisation utilise** > tapez **Microsoft Threat Protection** et sélectionnez sur **Microsoft Threat Protection**.

   >[!NOTE]
   >La protection contre les menaces Microsoft ne s’affiche pas dans la liste d’origine. Vous devez commencer à écrire son nom dans la zone de texte pour l’afficher.

   ![Image de l’accès à l’API et de la sélection de l’API](../../media/apis-in-my-org-tab.PNG)

   - Choose **application permissions**  >  **incident. Read. All** > Select on **Add permissions**

   ![Image de l’accès à l’API et de la sélection de l’API](../../media/request-api-permissions.PNG)

   >[!IMPORTANT]
   >Vous devez sélectionner les autorisations appropriées. 

     Par exemple,

     - Pour déterminer les autorisations qui vous sont nécessaires, consultez la section **autorisations** dans l’API que vous souhaitez appeler.

5. Sélectionnez **accorder le consentement** de l’administrateur

    - >[!NOTE]
      > Chaque fois que vous ajoutez une autorisation, vous devez sélectionner sur **accorder le consentement** pour que la nouvelle autorisation prenne effet.

    ![Image des autorisations accorder](../../media/grant-consent.PNG)

6. Ajoutez un secret à l’application.

    - Sélectionnez **certificats & secrets**, ajoutez une description à la clé secrète et sélectionnez **Ajouter**.

    >[!IMPORTANT]
    > Après avoir sélectionné **Ajouter**, **Copiez la valeur secrète générée**. Vous ne pourrez pas récupérer une fois que vous aurez quitté !

    ![Image de la clé créer une application](../../media/webapp-create-key2.png)

7. Notez l’ID de votre application et votre ID de client :

   - Sur la page de votre application, accédez à **vue d’ensemble** et copiez les éléments suivants :

   ![Image de l’ID d’application créé](../../media/app-and-tenant-ids.png)


Terminé! Vous avez correctement inscrit une application.

### <a name="step-2---get-a-token-using-the-app-and-use-this-token-to-access-the-api"></a>Étape 2 : obtenir un jeton à l’aide de l’application et utiliser ce jeton pour accéder à l’API.

-   Copiez le script ci-dessous dans PowerShell ISE ou dans un éditeur de texte, et enregistrez-le sous le**Get-Token.ps1**
-   L’exécution de ce script générera un jeton et l’enregistrera dans le dossier de travail sous le nom «**Latest-token.txt**».

```
# That code gets the App Context Token and save it to a file named "Latest-token.txt" under the current directory
# Paste below your Tenant ID, App ID and App Secret (App key).

$tenantId = '' ### Paste your tenant ID here
$appId = '' ### Paste your Application ID here
$appSecret = '' ### Paste your Application secret here

$resourceAppIdUri = 'https://api.security.microsoft.com'
$oAuthUri = "https://login.windows.net/$TenantId/oauth2/token"
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

-   Vérification de la validité :<br>
Exécutez le script.<br>
Dans votre navigateur, accédez à : https://jwt.ms/ <br>
Copiez le jeton (contenu du fichier Latest-token.txt).<br>
Colle dans la zone supérieure.<br>
Recherchez la section « rôles ». Recherchez le ```Incidents.Read.All``` rôle.<br>
L’exemple ci-dessous provient d’une application qui possède ```Incidents.Read.All``` ```Incidents.ReadWrite.All``` les ```AdvancedHunting.Read.All``` autorisations et.

![Image jwt.ms](../../media/api-jwt-ms.png)

### <a name="lets-get-the-incidents"></a>Permet d’obtenir les incidents.

-   Le script ci-dessous utilisera **Get-Token.ps1** pour accéder à l’API et obtiendra la dernière mise à jour des incidents au cours des 48 dernières heures.
-   Enregistrez ce script dans le dossier dans lequel vous avez enregistré le script précédent **Get-Token.ps1**. 
-   Le script d’un fichier JSON avec les données dans le même dossier que les scripts.

```
# Returns Incidents last updated in the past 48 hours.

$token = ./Get-Token.ps1       #run the script Get-Token.ps1  - make sure you are running this script from the same folder of Get-Token.ps1

# Get Incidents from the last 48 hours. Make sure you have incidents in that time frame.
$dateTime = (Get-Date).ToUniversalTime().AddHours(-48).ToString("o")

# The URL contains the type of query and the time filter we created above
$url = "https://api.security.microsoft.com/api/incidents?$filter=lastUpdateTime+ge+$dateTime"

# Set the WebRequest headers
$headers = @{ 
    'Content-Type' = 'application/json'
    'Accept' = 'application/json'
    'Authorization' = "Bearer $token"
}

# Send the webrequest and get the results. 
$response = Invoke-WebRequest -Method Get -Uri $url -Headers $headers -ErrorAction Stop

# Extract the incidents from the results. 
$incidents =  ($response | ConvertFrom-Json).value | ConvertTo-Json -Depth 99

# Get string with the execution time. We concatenate that string to the output file to avoid overwrite the file
$dateTimeForFileName = Get-Date -Format o | foreach {$_ -replace ":", "."}    

# Save the result as json
$outputJsonPath = "./Latest Incidents $dateTimeForFileName.json"     

Out-File -FilePath $outputJsonPath -InputObject $incidents 
```

Vous avez tous fini ! Vous venez d’effectuer les opérations suivantes :
-   Créé et inscrit et application
-   Autorisation accordée à cette application pour lire les alertes
-   Connexion de l’API
-   Utilisation d’un script PowerShell pour renvoyer des incidents créés au cours des 48 dernières heures



## <a name="related-topic"></a>Voir aussi
- [Accéder aux API de protection contre les menaces Microsoft](api-access.md)
- [Accéder à la protection contre les menaces Microsoft avec le contexte d’application](api-create-app-web.md)
- [Accéder à la protection contre les menaces Microsoft avec le contexte utilisateur](api-create-app-user-context.md)
