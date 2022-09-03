---
title: Étape 2. Utiliser Microsoft Teams pour créer votre canal de gestion des contrats
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.service: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Découvrez comment utiliser Microsoft Teams pour créer votre canal de gestion des contrats à l’aide d’une solution Microsoft 365.
ms.openlocfilehash: 10d7598400f095dce34ed5fbb572608a7bd01306
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67579201"
---
# <a name="step-2-use-microsoft-teams-to-create-your-contract-management-channel"></a>Étape 2. Utiliser Microsoft Teams pour créer votre canal de gestion des contrats

Lorsque votre organisation configure une solution de gestion des contrats, vous avez besoin d’un emplacement central dans lequel les parties prenantes peuvent examiner et gérer les contrats. À cet effet, vous pouvez utiliser [Microsoft Teams](/microsoftteams/) pour configurer un canal Teams et utiliser les fonctionnalités de Teams pour :

- **Créez un emplacement pour que les parties prenantes voient facilement tous les contrats qui nécessitent une action.** Par exemple, dans Teams, vous pouvez créer un onglet Contrats dans le canal Gestion **des** contrats dans lequel les membres peuvent voir une vue en mosaïque utile de tous les contrats qui doivent être approuvés. Vous pouvez également configurer l’affichage afin que chaque « carte » répertorie les données importantes qui vous intéressent (par exemple, *client*, *entrepreneur* et *montant des frais*).

     ![Onglet Contrats.](../media/content-understanding/tile-view.png)

- **Disposez d’un emplacement où les membres peuvent interagir les uns avec les autres et voir les événements importants.** Par exemple, dans Teams, l’onglet **Publications** peut être utilisé pour avoir des conversations, obtenir des mises à jour et afficher des actions (par exemple, un membre rejetant un contrat). Lorsqu’un événement s’est produit (par exemple, un nouveau contrat soumis pour approbation), l’onglet **Publications** peut être utilisé non seulement pour l’annoncer, mais également pour conserver un enregistrement de celui-ci. Et si les membres s’abonnent aux notifications, ils sont avertis chaque fois qu’il y a une mise à jour.

     ![Onglet Publications.](../media/content-understanding/posts.png)

- **Disposez d’un emplacement pour que les membres puissent voir les contrats approuvés afin de savoir quand ils peuvent être soumis pour paiement.** Dans SharePoint, vous devez créer une liste pour le **paiement** et inclure des colonnes pour le **client**, **l’entrepreneur** et le **montant des frais**, en sélectionnant **une seule ligne de texte** comme type de colonne. Vous devez ajouter la liste **Pour le paiement** sous la forme d’un onglet Teams dans le canal Gestion des contrats, comme [pour l’onglet **Contrats**](solution-manage-contracts-step2.md#attach-your-sharepoint-document-library-to-the-contracts-tab). L’onglet **Paiement** répertorie tous les contrats qui devront être soumis pour paiement. Vous pouvez facilement étendre cette solution pour écrire ces informations directement dans une application financière tierce (par exemple, Dynamics CRM). 


## <a name="attach-your-sharepoint-document-library-to-the-contracts-tab"></a>Attacher votre bibliothèque de documents SharePoint à l’onglet Contrats

Après avoir créé un onglet **Contrats** dans votre canal Gestion des contrats, vous devez [y joindre votre bibliothèque de documents SharePoint](https://support.microsoft.com/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b). La bibliothèque de documents SharePoint à joindre est celle à laquelle vous avez appliqué votre modèle de compréhension de document SharePoint Syntex dans la section précédente.

Après avoir attaché la bibliothèque de documents SharePoint, vous pouvez afficher tous les contrats classifiés par le biais d’un affichage de liste par défaut.

   ![Affichage liste de la bibliothèque SharePoint.](../media/content-understanding/list-view.png)

## <a name="customize-your-contracts-tab-tile-view"></a>Personnaliser l’affichage de la vignette de l’onglet Contrats

> [!NOTE]
> Cette section fait référence à des exemples de code contenus dans le fichier [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) inclus dans le [référentiel des ressources de la solution de gestion des contrats](https://github.com/pnp/syntex-samples/tree/main/scenario%20samples/Contracts%20Management).

Bien que Teams vous permet d’afficher vos contrats dans une vue en mosaïque, vous pouvez les personnaliser pour afficher les données de contrat que vous souhaitez rendre visibles dans la carte de contrat. Par exemple, pour l’onglet Contrats, il est important que **les** membres voient le client, l’entrepreneur et le montant des frais sur la carte de contrat. Tous ces champs ont été extraits de chaque contrat par le biais de votre modèle SharePoint Syntex qui a été appliqué à votre bibliothèque de documents. Vous souhaitez également pouvoir modifier la barre d’en-tête de vignette en différentes couleurs pour chaque état afin que les membres puissent facilement voir où se trouve le contrat dans le processus d’approbation. Par exemple, tous les contrats approuvés ont une barre d’en-tête bleue.

   ![Vue mosaïque de la bibliothèque SharePoint.](../media/content-understanding/tile.png)

La vue mosaïque personnalisée que vous utilisez vous oblige à apporter des modifications au fichier JSON utilisé pour mettre en forme l’affichage de vignette actuel. Vous pouvez référencer le fichier JSON utilisé pour créer la vue de carte en examinant le fichier [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) . Dans les sections suivantes, vous verrez des sections spécifiques du code pour les fonctionnalités figurant dans les cartes de contrat.

Si vous souhaitez afficher ou apporter des modifications au code JSON de votre affichage dans votre canal Teams, dans le canal Teams, sélectionnez le menu déroulant affichage, puis sélectionnez Mettre en **forme l’affichage actuel**.

   ![Capture d’écran du format json dans le canal Teams.](../media/content-understanding/jason-format.png)

## <a name="card-size-and-shape"></a>Taille et forme de la carte

Dans le fichier [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) , consultez la section suivante pour voir le code de mise en forme de la taille et de la forme de la carte.

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

Le code suivant vous permet de définir l’état de chaque carte de titre. Notez que chaque valeur d’état (*New*, *In review*, *Approved* et *Rejected*) affiche un code de couleur différent pour chacune d’elles. Dans le fichier [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) , examinez la section qui définit l’état.

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

Chaque carte de contrat affiche trois champs qui ont été extraits pour chaque contrat (*client*, *entrepreneur* et *montant des frais*). En outre, vous souhaitez également afficher l’heure/la date à laquelle le fichier a été classé par le modèle SharePoint Syntex utilisé pour l’identifier.

Dans le fichier [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) , les sections suivantes définissent chacune d’elles.

### <a name="client"></a>Client

Cette section définit la façon dont « Client » s’affiche sur la carte et utilise la valeur du contrat spécifique.

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

Cette section définit la façon dont l'« entrepreneur » s’affichera sur la carte et utilise la valeur du contrat spécifique.

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

Cette section définit la façon dont le « montant des frais » s’affiche sur la carte et utilise la valeur du contrat spécifique.

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
