---
title: Étape 2. Utiliser Microsoft Teams pour créer votre canal de gestion des contrats
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.service: microsoft-syntex
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Découvrez comment utiliser Microsoft Teams pour créer votre canal de gestion des contrats à l’aide d’une solution Microsoft 365.
ms.openlocfilehash: 262312b2b8f43a7f3cc177ccd1544a9d12fbdcd1
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68661190"
---
# <a name="step-2-use-microsoft-teams-to-create-your-contract-management-channel"></a>Étape 2. Utiliser Microsoft Teams pour créer votre canal de gestion des contrats

Lorsque votre organisation configure une solution de gestion des contrats, vous avez besoin d’un emplacement central dans lequel les parties prenantes peuvent examiner et gérer les contrats. À cet effet, vous pouvez utiliser [Microsoft Teams](/microsoftteams/) pour configurer un canal Teams et utiliser les fonctionnalités de Teams pour :

- **Créez un emplacement pour permettre aux parties prenantes de voir facilement tous les contrats qui nécessitent une action.** Par exemple, dans Teams, vous pouvez créer un onglet **Contrats** dans le canal Gestion des contrats dans lequel les membres peuvent voir une vue par vignette utile de tous les contrats qui nécessitent une approbation. Vous pouvez également configurer l’affichage de sorte que chaque « carte » répertorie les données importantes qui vous intéressent (telles que *le client*, l’entrepreneur et le *montant des frais*). 

     ![Onglet Contrats.](../media/content-understanding/tile-view.png)

- **Disposez d’un emplacement pour que les membres interagissent entre eux et voient les événements importants.** Par exemple, dans Teams, l’onglet **Publications** peut être utilisé pour avoir des conversations, obtenir des mises à jour et voir des actions (par exemple, un membre rejetant un contrat). Lorsque quelque chose s’est produit (par exemple, un nouveau contrat soumis pour approbation), l’onglet **Publications** peut être utilisé non seulement pour l’annoncer, mais également pour en conserver un enregistrement. Et si les membres s’abonnent aux notifications, ils sont avertis chaque fois qu’il y a une mise à jour.

     ![Onglet Publications.](../media/content-understanding/posts.png)

- **Disposer d’un emplacement pour que les membres puissent voir les contrats approuvés afin de savoir quand ils peuvent être soumis pour paiement.** Dans SharePoint, vous devez créer une liste **Pour le paiement** et inclure des colonnes pour **Client**, **Entrepreneur** et Montant des **frais**, en sélectionnant **Une seule ligne de texte** comme type de colonne. Vous devez ajouter la liste **Pour le paiement** sous la forme d’un onglet Teams dans le canal Gestion des contrats, de la même façon [que pour l’onglet **Contrats**](solution-manage-contracts-step2.md#attach-your-sharepoint-document-library-to-the-contracts-tab). L’onglet **Pour le paiement** répertorie tous les contrats qui devront être soumis pour paiement. Vous pouvez facilement étendre cette solution pour écrire ces informations directement dans une application financière tierce (par exemple, Dynamics CRM). 

## <a name="attach-your-sharepoint-document-library-to-the-contracts-tab"></a>Joindre votre bibliothèque de documents SharePoint à l’onglet Contrats

Après avoir créé un onglet **Contrats** dans votre canal De gestion des contrats, vous devez [y joindre votre bibliothèque de documents SharePoint](https://support.microsoft.com/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b). La bibliothèque de documents SharePoint à joindre est celle à laquelle vous avez appliqué votre modèle de traitement de document non structuré dans la section précédente.

Une fois que vous avez joint la bibliothèque de documents SharePoint, vous pouvez afficher tous les contrats classifiés via un affichage liste par défaut.

   ![Affichage liste de la bibliothèque SharePoint.](../media/content-understanding/list-view.png)

## <a name="customize-your-contracts-tab-tile-view"></a>Personnaliser l’affichage des vignettes de l’onglet Contrats

> [!NOTE]
> Cette section fait référence à des exemples de code contenus dans le fichier [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) inclus dans le [référentiel Contracts Management Solution Assets](https://github.com/pnp/syntex-samples/tree/main/scenario%20samples/Contracts%20Management).

Bien que Teams vous permette d’afficher vos contrats dans une vue par vignette, vous pouvez le personnaliser pour afficher les données de contrat que vous souhaitez rendre visibles dans la carte de contrat. Par exemple, pour l’onglet **Contrats** , il est important que les membres voient le client, l’entrepreneur et le montant des frais sur la carte de contrat. Tous ces champs ont été extraits de chaque contrat via votre modèle Syntex qui a été appliqué à votre bibliothèque de documents. Vous souhaitez également pouvoir modifier la barre d’en-tête de vignette en couleurs différentes pour chaque état afin que les membres puissent facilement voir où se trouve le contrat dans le processus d’approbation. Par exemple, tous les contrats approuvés ont une barre d’en-tête bleue.

   ![Vue vignette de la bibliothèque SharePoint.](../media/content-understanding/tile.png)

L’affichage mosaïque personnalisé que vous utilisez vous oblige à apporter des modifications au fichier JSON utilisé pour mettre en forme la vue vignette actuelle. Vous pouvez référencer le fichier JSON utilisé pour créer la vue carte en examinant le fichier [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) . Dans les sections suivantes, vous verrez des sections spécifiques du code pour les fonctionnalités qui se trouvent dans les cartes de contrat.

Si vous souhaitez voir ou modifier le code JSON de votre affichage dans votre canal Teams, dans le canal Teams, sélectionnez le menu déroulant affichage, puis sélectionnez **Format de l’affichage actuel**.

   ![Capture d’écran du format json dans le canal Teams.](../media/content-understanding/jason-format.png)

## <a name="card-size-and-shape"></a>Taille et forme de la carte

Dans le fichier [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) , examinez la section suivante pour voir le code de la façon dont la taille et la forme de la carte sont mises en forme.

```JSON
                  {
                    "elmType": "div",
                    "style": {
                      "background-color": "#f5f5f5",
                      "padding": "5px",
                      "width": "180px"
                    },
                    "children": [
                      {
                        "elmType": "img",
                        "attributes": {
                          "src": "@thumbnail.large"
                        },
                        "style": {
                          "width": "185px",
                          "height": "248px"
                        }
                      }
```

## <a name="contract-status"></a>État du contrat

Le code suivant vous permet de définir l’état de chaque carte de titre. Notez que chaque valeur d’état (*Nouveau*, *En révision*, *Approuvé* et *Rejeté*) affiche un code de couleur différent pour chacune d’elles. Dans le fichier [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) , examinez la section qui définit l’état.

```JSON
          {
            "elmType": "div",
            "children": [
              {
                "elmType": "div",
                "style": {
                  "color": "white",
                  "background-color": "=if([$Status] == 'New', '#00b7c3', if([$Status] == 'In review', '#ffaa44', if([$Status] == 'Approved', '#0078d4', if([$Status] == 'Rejected', '#d13438', '#8378de'))))",
                  "padding": "5px 15px",
                  "height": "auto",
                  "text-transform": "uppercase",
                  "font-size": "12.5px"
                },
                "txtContent": "[$Status]"
              }
```

## <a name="extracted-fields"></a>Champs extraits

Chaque carte de contrat affiche trois champs qui ont été extraits pour chaque contrat (*Client*, *Entrepreneur* et *Montant des frais*). En outre, vous souhaitez également afficher l’heure/la date à laquelle le fichier a été classé par le modèle Syntex utilisé pour l’identifier.

Dans le fichier [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) , les sections suivantes définissent chacune d’elles.

### <a name="client"></a>Client

Cette section définit la façon dont « Client » s’affiche sur la carte et utilise la valeur pour le contrat spécifique.

```JSON
                      {
                        "elmType": "div",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px"
                        },
                        "txtContent": "Client"
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "16px",
                          "font-weight": "600"
                        },
                        "txtContent": "[$Client]"
                      },
```

### <a name="contractor"></a>Entrepreneur

Cette section définit comment le « Entrepreneur » s’affichera sur la carte et utilise la valeur pour le contrat spécifique.

```JSON
                        {
                          "elmType": "div",
                          "txtContent": "Contractor",
                          "style": {
                            "color": "#767676",
                            "font-size": "12px",
                            "margin-bottom": "2px"
                          }
                        },
                        {
                          "elmType": "div",
                          "style": {
                            "margin-bottom": "12px",
                            "font-size": "14px"
                          },
                          "txtContent": "[$Contractor]"
                        },
```

### <a name="fee-amount"></a>Montant des frais

Cette section définit la façon dont le « Montant des frais » s’affiche sur la carte et utilise la valeur du contrat spécifique.

```JSON
                      {
                        "elmType": "div",
                        "txtContent": "Fee amount",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px",
                          "margin-bottom": "2px"
                        }
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "14px"
                        },
                        "txtContent": "[$FeeAmount]"
                      },
```

### <a name="classification-date"></a>Date de classification

Cette section définit la façon dont « Classification » s’affiche sur la carte et utilise la valeur du contrat spécifique.

```JSON
                      {
                        "elmType": "div",
                        "txtContent": "Classified",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px",
                          "margin-bottom": "2px"
                        }
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "14px"
                        },
                        "txtContent": "[$PrimeLastClassified]"
                      }
```

## <a name="next-step"></a>Étape suivante

[Étape 3. Utiliser Power Automate pour créer le flux de traitement de vos contrats](solution-manage-contracts-step3.md)
