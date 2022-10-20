---
title: Créer une règle de notification d’intégration ou de retrait
description: Recevez une notification lorsqu’un script d’intégration ou de désintégrage local est utilisé.
keywords: intégration, désintégrage, local, script, notification, règle
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 1ff70c961a8598465634525928b994e2e310c0ea
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68626070"
---
# <a name="create-a-notification-rule-when-a-local-onboarding-or-offboarding-script-is-used"></a>Créer une règle de notification lorsqu’un script d’intégration ou de désintégrage local est utilisé

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


Créez une règle de notification afin que, lorsqu’un script d’intégration ou de désintégrage local est utilisé, vous soyez averti.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez avoir accès à :

- Power Automate (plan par utilisateur au minimum). Pour plus d’informations, consultez la [page de tarification de Power Automate](https://flow.microsoft.com/pricing/).
- Table Azure ou liste Ou bibliothèque SharePoint / base de données SQL.

## <a name="create-the-notification-flow"></a>Créer le flux de notification

1. Dans [flow.microsoft.com](https://flow.microsoft.com/).

2. Accédez à **Mes flux > Nouveau > planifié - à partir de vide**.

   :::image type="content" source="images/new-flow.png" alt-text="Le flux" lightbox="images/new-flow.png":::


3. Générez un flux planifié.
   1. Entrez un nom de flux.
   2. Spécifiez le début et l’heure.
   3. Spécifiez la fréquence. Par exemple, toutes les 5 minutes.

   :::image type="content" source="images/build-flow.png" alt-text="Flux de notification" lightbox="images/build-flow.png":::

4. Sélectionnez le bouton + pour ajouter une nouvelle action. La nouvelle action sera une requête HTTP adressée à l’API defender pour centre de sécurité de point de terminaison. Vous pouvez également le remplacer par le « connecteur WDATP » (action : « Machines - Obtenir la liste des machines »).

   :::image type="content" source="images/recurrence-add.png" alt-text="Récurrence et ajout de l’action" lightbox="images/recurrence-add.png":::

5. Entrez les champs HTTP suivants :

   - Méthode : « GET » comme valeur pour obtenir la liste des appareils.
   - URI : Entrez `https://api.securitycenter.microsoft.com/api/machines`.
   - Authentification : sélectionnez « Active Directory OAuth ».
   - Locataire : connectez-vous et accédez à https://portal.azure.com **Azure Active Directory > Inscriptions d’applications** et obtenez la valeur d’ID de locataire.
   - Public: `https://securitycenter.onmicrosoft.com/windowsatpservice\`
   - ID client : connectez-vous à https://portal.azure.com **Azure Active Directory > Inscriptions d’applications** et obtenez la valeur d’ID client.
   - Type d’informations d’identification : sélectionnez « Secret ».
   - Secret : connectez-vous et accédez à https://portal.azure.com **Azure Active Directory > Inscriptions d’applications** et obtenez la valeur de l’ID de locataire.

    :::image type="content" source="images/http-conditions.png" alt-text="Conditions HTTP" lightbox="images/http-conditions.png":::

6. Ajoutez une nouvelle étape en sélectionnant **Ajouter une nouvelle action** , puis recherchez **Opérations de données** et sélectionnez **Analyser JSON**.

   :::image type="content" source="images/data-operations.png" alt-text="Entrée des opérations de données" lightbox="images/data-operations.png":::

7. Ajoutez Body dans le champ **Contenu** .

   :::image type="content" source="images/parse-json.png" alt-text="Section JSON d’analyse" lightbox="images/parse-json.png":::

8. Sélectionnez **l’exemple de charge utile Utiliser pour générer le lien de schéma** .

   :::image type="content" source="images/parse-json-schema.png" alt-text="Analyser JSON avec la charge utile" lightbox="images/parse-json-schema.png":::

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

10. Extrayez les valeurs de l’appel JSON et vérifiez si le ou les appareils intégrés sont / sont déjà inscrits dans la liste SharePoint à titre d’exemple :

    - Si oui, aucune notification ne sera déclenchée
    - Si ce n’est pas le cas, inscrit le ou les nouveaux appareils intégrés dans la liste SharePoint et une notification est envoyée à l’administrateur Defender pour point de terminaison

    :::image type="content" source="images/flow-apply.png" alt-text="Application du flux à chaque élément" lightbox="images/flow-apply.png":::

    :::image type="content" source="images/apply-to-each.png" alt-text="Application du flux à l’élément Get items" lightbox="images/apply-to-each.png":::

11. Sous **condition**, ajoutez l’expression suivante : « length(body('Get_items')?[' valeur']) » et définissez la condition sur 0.

    :::image type="content" source="images/apply-to-each-value.png" alt-text="Application du flux à chaque condition" lightbox="images/apply-to-each-value.png":::
    :::image type="content" source="images/conditions-2.png" alt-text="Condition-1" lightbox="images/conditions-2.png":::
    :::image type="content" source="images/condition3.png" alt-text="Condition-2" lightbox="images/condition3.png":::
    :::image type="content" source="images/send-email.png" alt-text="Section Envoyer un e-mail" lightbox="images/send-email.png":::

## <a name="alert-notification"></a>Notification d’alerte

L’image suivante est un exemple de notification par e-mail.

:::image type="content" source="images/alert-notification.png" alt-text="Écran de notification par e-mail" lightbox="images/alert-notification.png":::

## <a name="tips"></a>Conseils

- Vous pouvez filtrer ici à l’aide de lastSeen uniquement :
  - Toutes les 60 minutes :
    - Prenez tous les appareils vus pour la dernière fois au cours des 7 derniers jours.

- Pour chaque appareil :
  - Si la propriété vue pour la dernière fois se trouve sur l’intervalle d’une heure de [-7 jours, -7 jours + 60 minutes ] -> Alerte pour la possibilité de désinstégation.
  - Si la première vue se trouve sur la dernière heure -> Alerte pour l’intégration.

Dans cette solution, vous n’aurez pas d’alertes en double : il existe des locataires qui ont de nombreux appareils. L’obtention de tous ces appareils peut être très coûteuse et nécessiter une pagination.

Vous pouvez le fractionner en deux requêtes :

1. Pour le désintégrage, prenez uniquement cet intervalle à l’aide de la $filter OData et notifiez uniquement si les conditions sont remplies.
2. Prenez tous les appareils vus pour la dernière fois au cours de la dernière heure et vérifiez la première propriété vue pour eux (si la première propriété vue est sur la dernière heure, la dernière vue doit être là aussi).
