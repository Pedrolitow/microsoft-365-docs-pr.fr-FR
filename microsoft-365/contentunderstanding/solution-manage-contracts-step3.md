---
title: Étape 3. Utiliser Power Automate pour créer le flux pour traiter vos contrats
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Découvrez comment utiliser Power Automate créer votre flux pour traiter vos contrats à l’aide d’Microsoft 365 solution.
ms.openlocfilehash: d83fb6e5ca911cbafc6f064c615ab15ae0f570c7
ms.sourcegitcommit: f3c912780bbcf5a5b47de192202adb3afbd5952b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2022
ms.locfileid: "62219004"
---
# <a name="step-3-use-power-automate-to-create-the-flow-to-process-your-contracts"></a>Étape 3. Utiliser Power Automate pour créer le flux pour traiter vos contrats

Vous avez créé votre canal de gestion des contrats et attaché votre SharePoint de documents. L’étape suivante consiste à créer un flux Power Automate pour traiter vos contrats que votre modèle SharePoint Syntex identifie et classifie. Vous pouvez réaliser cette étape en [créant un flux Power Automate dans votre bibliothèque SharePoint documents.](https://support.microsoft.com/office/create-a-flow-for-a-list-or-library-in-sharepoint-or-onedrive-a9c3e03b-0654-46af-a254-20252e580d01)

Pour votre solution de gestion des contrats, vous souhaitez créer un flux Power Automate pour réaliser les actions suivantes :

-  Une fois qu’un contrat a été classé par votre modèle SharePoint Syntex, modifiez l’état du contrat sur **En révision.**
- Le contrat est ensuite examiné et approuvé ou rejeté.
- Pour les contrats approuvés, les informations sur le contrat sont publiées dans un onglet pour le traitement des paiements.
- Pour les contrats rejetés, l’équipe est avertie pour analyse approfondie. 

Le diagramme suivant illustre le flux Power Automate pour la solution de gestion des contrats.

![Flow diagramme montrant l’intégralité de la solution.](../media/content-understanding/flow-entire-process.png)

## <a name="prepare-your-contract-for-review"></a>Préparer votre contrat pour révision

Lorsqu’un contrat est identifié et classé par votre modèle de SharePoint Syntex document, le flux de Power Automate change d’abord l’état en **In review**.

![Mettre à jour l’état.](../media/content-understanding/flow-overview.png)

Après avoir vérifié le fichier, modifiez la valeur d’état sur **En révision.**

![Dans l’état de l’avis.](../media/content-understanding/in-review.png)

L’étape suivante consiste à créer une carte adaptative indiquant que le contrat attend une révision et la publie sur le canal de gestion des contrats.

![Publication de révision de contrat.](../media/content-understanding/contract-approval-post.png)


![Créez une carte adaptative pour révision.](../media/content-understanding/adaptive-card.png)

Le code suivant est le JSON utilisé pour cette étape dans le Power Automate flux.

```JSON
{
"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
"type": "AdaptiveCard",
"version": "1.0",
"body": [
    {
    "type": "TextBlock",
    "text": "Contract approval request",
    "size": "large",
    "weight": "bolder",
     "wrap": true
    },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Date created",
                            "value": "@{triggerOutputs()?['body/Modified']} "
                        },
                        {
                            "title": "Link",
                            "value": "[@{triggerOutputs()?['body/{FilenameWithExtension}']}](@{triggerOutputs()?['body/{Link}']})"
                        }
                    ]
                }
            ]
         },
    {
    "type": "TextBlock",
    "text": "Comment:"
    },
        {
            "type": "Input.Text",
            "placeholder": "Enter comments",
            "id": "acComments"
        }
],
"actions": [
    {
    "type": "Action.Submit",
    "title": "Approve",
    "data": {
        "x": "Approve"
    }
    },
    {
    "type": "Action.Submit",
    "title": "Reject",
    "data": {
        "x": "Reject"
    }
    }
]
}
```


## <a name="conditional-context"></a>Contexte conditionnel

Dans votre flux, vous devez ensuite créer une condition dans laquelle votre contrat sera [approuvé ou](#if-the-contract-is-approved) [rejeté.](#if-the-contract-is-rejected)

![Conditionnel.](../media/content-understanding/condition.png)

## <a name="if-the-contract-is-approved"></a>Si le contrat est approuvé

Lorsqu’un contrat a été approuvé, les éléments suivants se produisent :

- Sous l’onglet **Contrats,** l’état de la carte de contrat passe à **Approuvé**.

   ![État de la carte approuvé.](../media/content-understanding/approved-contracts-tab.png)

- Dans votre flux, l’état est modifié en **Approuvé**.

   ![Flow statut approuvé.](../media/content-understanding/status-approved.png)

- Dans cette solution, les données de  contrat sont ajoutées à l’onglet Paiement afin que les paiements soient gérés. Ce processus peut être étendu pour permettre au flux de soumettre les contrats en paiement par une application financière tierce (par exemple, Dynamics CRM).

   ![Contrat déplacé vers Payer.](../media/content-understanding/for-payout.png)

- Dans le flux, vous créez l’élément suivant pour déplacer les contrats approuvés vers **l’onglet** Paiement.

   ![Flow’élément à déplacer vers Payer.](../media/content-understanding/ready-for-payout.png)

    Pour obtenir les expressions pour les informations nécessaires à partir de la carte Teams, utilisez les valeurs indiquées dans le tableau suivant.
 
    |Nom     |Expression |
    |---------|-----------|
    | État d’approbation  | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')? ['submitActionId']         |
    | Approuvé par     | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')? ['responder'] ['displayName']        |
    | Date d’approbation     | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')? ['responseTime']         |
    | Commentaire     | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')? ['data']? ['acComments']         |
    
    L’exemple suivant montre comment utiliser la zone de formule dans Power Automate pour écrire une expression.

   ![Capture d’écran Power Automate montrant une formule d’expression.](../media/content-understanding/expression-formula-power-automate.png)    

- Une carte adaptative indiquant que le contrat a été approuvé est créée et publiée sur le canal de gestion des contrats.

   ![Approbation de contrat publiée.](../media/content-understanding/adaptive-card-approval.png)

   ![Approbation de carte adaptative.](../media/content-understanding/adaptive-card.png)


   Le code suivant est le JSON utilisé pour cette étape dans le Power Automate flux.

```JSON
{ 
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "Container",
            "style": "emphasis",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "size": "Large",
                                    "weight": "Bolder",
                                    "text": "CONTRACT APPROVED"
                                }
                            ],
                            "width": "stretch"
                        }
                    ]
                }
            ],
            "bleed": true
        },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Approval by",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responder']['displayName']}"
                        },
                        {
                            "title": "Approved date",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responseTime']}"
                        },
                        {
                            "title": "Approval comment",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['data']?['acComments']}"
                        },
                        {
                            "title": " ",
                            "value": " "
                        },
                        {
                            "title": "Status",
                            "value": "Ready for payout"
                        }
                    ]
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2",
    "fallbackText": "This card requires Adaptive Cards v1.2 support to be rendered properly."
}
```

## <a name="if-the-contract-is-rejected"></a>Si le contrat est rejeté

Lorsqu’un contrat a été rejeté, les choses suivantes se produisent :

- Sous l’onglet **Contrats,** l’état de la carte de contrat passe à **Rejeté**.

   ![État de la carte rejeté.](../media/content-understanding/rejected-contracts-tab.png)

- Dans votre flux, vous consultez le fichier de contrat, modifiez l’état sur **Rejeté,** puis ré-consultez le fichier.

   ![Flow statut rejeté dans le fichier de contrat.](../media/content-understanding/reject-flow.png)

- Dans votre flux, vous créez une carte adaptative indiquant que le contrat a été rejeté.

   ![Flow’état de la carte adaptative s’affiche.](../media/content-understanding/reject-flow-item.png)

Le code suivant est le JSON utilisé pour cette étape dans le Power Automate flux.

```JSON
{ 
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "Container",
            "style": "attention",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "size": "Large",
                                    "weight": "Bolder",
                                    "text": "CONTRACT REJECTED"
                                }
                            ],
                            "width": "stretch"
                        }
                    ]
                }
            ],
            "bleed": true
        },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Rejected by",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responder']['displayName']}"
                        },
                        {
                            "title": "Rejected date",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responseTime']}"
                        },
                        {
                            "title": "Comment",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['data']?['acComments']}"
                        },
                        {
                            "title": " ",
                            "value": " "
                        },
                        {
                            "title": "Status",
                            "value": "Needs review"
                        }
                    ]
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2",
    "fallbackText": "This card requires Adaptive Cards v1.2 support to be rendered properly."
}
```

- La carte est publiée dans le canal de gestion des contrats.

   ![Flow carte adaptative à rejeter.](../media/content-understanding/rejected.png)
