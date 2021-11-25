---
title: Créer une règle de notification d’intégration ou de retrait
description: Recevoir une notification lorsqu’un script d’intégration ou de mise hors-carte local est utilisé.
keywords: intégration, offboarding, local, script, notification, règle
search.appverid: met150
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
ms.technology: mde
ms.openlocfilehash: 36713496b5885866dd21a3402dcfe66b4af5b76e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61166769"
---
# <a name="create-a-notification-rule-when-a-local-onboarding-or-offboarding-script-is-used"></a>Créer une règle de notification lorsqu’un script d’intégration ou de mise hors-carte local est utilisé

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


Créez une règle de notification afin que, lorsqu’un script d’intégration ou de déclassage local soit utilisé, vous soyez averti.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez avoir accès à :

- Power Automate (plan par utilisateur au minimum). Pour plus d’informations, [voir Power Automate page de tarification.](https://flow.microsoft.com/pricing/)
- Table ou SharePoint Liste ou Bibliothèque /SQL DB Azure.

## <a name="create-the-notification-flow"></a>Créer le flux de notification

1. Dans [flow.microsoft.com](https://flow.microsoft.com/).

2. Accédez **à Mes flux > Nouveau > programmé - à partir d’un espace vide.**

    ![Image du flux.](images/new-flow.png)

3. Créez un flux programmé.
   1. Entrez un nom de flux.
   2. Spécifiez le début et l’heure.
   3. Spécifiez la fréquence. Par exemple, toutes les 5 minutes.

    ![Image du flux de notification.](images/build-flow.png)

4. Sélectionnez le bouton + pour ajouter une nouvelle action. La nouvelle action sera une demande HTTP à l’API du centre de sécurité Defender for Endpoint. Vous pouvez également le remplacer par le « connecteur WDATP » prédéfait (action : « Ordinateurs - Obtenir la liste des ordinateurs »).

    ![Image de la récurrence et ajout d’une action.](images/recurrence-add.png)

5. Entrez les champs HTTP suivants :

   - Méthode : « GET » comme valeur pour obtenir la liste des appareils.
   - URI : Entrez `https://api.securitycenter.microsoft.com/api/machines` .
   - Authentification : sélectionnez « Active Directory OAuth ».
   - Client : connectez-vous et accédez à Azure Active Directory >'inscription de l’application et obtenez la valeur https://portal.azure.com de l’ID de client. 
   - Public : `https://securitycenter.onmicrosoft.com/windowsatpservice\`
   - ID client : connectez-vous et accédez à Azure Active Directory >'inscription de l’application et obtenez la valeur https://portal.azure.com de l’ID client. 
   - Type d’informations d’identification : sélectionnez « Secret ».
   - Secret : connectez-vous et accédez à Azure Active Directory > inscriptions d’application et obtenez la valeur https://portal.azure.com de l’ID de client. 

    ![Image des conditions HTTP.](images/http-conditions.png)

6. Ajoutez une nouvelle étape en sélectionnant Ajouter **une nouvelle action,** puis recherchez Opérations de **données** et **sélectionnez Analyse JSON**.

    ![Image des opérations de données.](images/data-operations.png)

7. Ajouter le corps dans le **champ** Contenu.

    ![Image de l’utilisation du JSON d’une parse.](images/parse-json.png)

8. Sélectionnez **l’exemple de charge utile Utiliser pour générer un lien de** schéma.

    ![Image de l’image json d’une image avec la charge utile.](images/parse-json-schema.png)

9. Copiez et collez l’extrait de code JSON suivant :

    ```json
    {
        "type": "object",
        "properties": {
            "@@odata.context": {
                "type": "string"
            },
            "value": {
                "type": "array",
                "items": {
                    "type": "object",
                    "properties": {
                        "id": {
                            "type": "string"
                        },
                        "computerDnsName": {
                            "type": "string"
                        },
                        "firstSeen": {
                            "type": "string"
                        },
                        "lastSeen": {
                            "type": "string"
                        },
                        "osPlatform": {
                            "type": "string"
                        },
                        "osVersion": {},
                        "lastIpAddress": {
                            "type": "string"
                        },
                        "lastExternalIpAddress": {
                            "type": "string"
                        },
                        "agentVersion": {
                            "type": "string"
                        },
                        "osBuild": {
                            "type": "integer"
                        },
                        "healthStatus": {
                            "type": "string"
                        },
                        "riskScore": {
                            "type": "string"
                        },
                        "exposureScore": {
                            "type": "string"
                        },
                        "aadDeviceId": {},
                        "machineTags": {
                            "type": "array"
                        }
                    },
                    "required": [
                        "id",
                        "computerDnsName",
                        "firstSeen",
                        "lastSeen",
                        "osPlatform",
                        "osVersion",
                        "lastIpAddress",
                        "lastExternalIpAddress",
                        "agentVersion",
                        "osBuild",
                        "healthStatus",
                        "rbacGroupId",
                        "rbacGroupName",
                        "riskScore",
                        "exposureScore",
                        "aadDeviceId",
                        "machineTags"
                    ]
                }
            }
        }
    }

    ```

10. Extrayez les valeurs de l’appel JSON et vérifiez si le ou les appareils intégrés sont / sont déjà inscrits dans la liste SharePoint par exemple :

    - Si oui, aucune notification ne sera déclenchée
    - Si non, enregistre le ou les nouveaux appareils intégrés dans la liste SharePoint et une notification est envoyée à l’administrateur de Defender for Endpoint

    ![Image de s’appliquer à chacun d’eux.](images/flow-apply.png)

    ![Image de s’appliquer à chacun avec obtenir des éléments.](images/apply-to-each.png)

11. Under **Condition**, add the following expression: « length(body('Get_items')?[' value']) » et définissez la condition sur 0.

    ![Image d’application à chaque condition. ](images/apply-to-each-value.png)
     ![ Image de condition1. ](images/conditions-2.png)
     ![ Image de condition2. ](images/condition3.png)
     ![ Image de l’envoi d’un message électronique.](images/send-email.png)

## <a name="alert-notification"></a>Notification d’alerte

L’image suivante est un exemple de notification par courrier électronique.

![Image de la notification par courrier électronique.](images/alert-notification.png)

## <a name="tips"></a>Conseils 

- Vous pouvez filtrer ici à l’aide de lastSeen uniquement :
  - Toutes les 60 min :
    - Prenez tous les appareils vus pour la dernière fois au cours des 7 derniers jours.

- Pour chaque appareil :
  - Si la propriété vue pour la dernière fois est sur l’intervalle d’une heure de [-7 jours, -7days + 60 minutes] -> alerte pour la possibilité de retentation.
  - Si le premier aperçu a lieu au cours de l’heure >'alerte d’intégration.

Dans cette solution, vous n’aurez pas d’alertes en double : il existe des locataires qui ont de nombreux appareils. L’obtention de tous ces appareils peut être très coûteuse et nécessiter une pagination.

Vous pouvez le fractionner en deux requêtes :

1. Pour laboarding, prenez uniquement cet intervalle à l’aide de la $filter OData et notifiez uniquement si les conditions sont remplies.
2. Prenez tous les appareils vus pour la dernière fois au cours de l’heure passée et vérifiez leur première propriété vue (si la première propriété vue se trouve au cours de l’heure passée, la dernière vue doit également être là).
