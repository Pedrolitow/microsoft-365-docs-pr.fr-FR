---
title: Étape 2. Utiliser Microsoft Teams pour créer votre canal de gestion de contrat
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: None
ROBOTS: ''
description: Découvrez comment utiliser Microsoft Teams pour créer votre canal de gestion de contrat à l’aide d’Microsoft 365 solution.
ms.openlocfilehash: bafce28689e4340c3ff73694d150bac294a95b5a
ms.sourcegitcommit: 6c342a956b2dbc32be33bac1a23a5038490f1b40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58532870"
---
# <a name="step-2-use-microsoft-teams-to-create-your-contract-management-channel"></a>Étape 2. Utiliser Microsoft Teams pour créer votre canal de gestion de contrat

Lorsque votre organisation définit une solution de gestion des contrats, vous avez besoin d’un emplacement central dans lequel les parties prenantes peuvent examiner et gérer les contrats. À cet effet, vous pouvez utiliser [Microsoft Teams](/microsoftteams/) pour configurer un canal Teams et utiliser les fonctionnalités Teams pour :

- **Créez un emplacement pour que les parties prenantes voient facilement tous les contrats qui nécessitent une action.** Par exemple, dans Teams vous pouvez créer un onglet **Contrats** dans le canal de gestion des contrats dans lequel les membres peuvent voir une vue de vignette utile de tous les contrats qui ont besoin d’approbation. Vous pouvez également configurer l’affichage afin que chaque « carte » répertorie les données importantes qui vous intéressent (par exemple, *client,* indépendant et *montant des frais).* 

     ![Onglet Contrats.](../media/content-understanding/tile-view.png)

- **Avoir un emplacement où les membres peuvent interagir les uns avec les autres et voir les événements importants.** Par exemple, dans Teams,  l’onglet Publications peut être utilisé pour avoir des conversations, obtenir des mises à jour et voir les actions (par exemple, un membre rejetant un contrat). Lorsqu’un événement s’est produit (par exemple, un nouveau contrat soumis pour approbation), l’onglet **Publications** peut être utilisé non seulement pour l’annoncer, mais aussi pour conserver un enregistrement de celui-ci. Et si les membres s’abonnez aux notifications, ils sont avertis chaque fois qu’une mise à jour est en cours.

     ![Onglet Publications.](../media/content-understanding/posts.png)

- **Avoir un emplacement pour que les membres voient les contrats approuvés afin de savoir quand ils peuvent être envoyés pour paiement.** Dans SharePoint, vous devez créer une  liste pour le paiement et inclure des colonnes  pour le **client,** **l’accès** et le montant des **frais,** en sélectionnant une seule ligne de texte comme type de colonne. Vous devrez ajouter  la liste des paiements sous la direction d’un onglet Teams dans le canal de gestion des contrats, de la même manière que pour [l’onglet **Contrats.**](solution-manage-contracts-step2.md#attach-your-sharepoint-document-library-to-the-contracts-tab) **L’onglet Paiement** sera la liste de tous les contrats qui devront être envoyés pour paiement. Vous pouvez facilement étendre cette solution pour écrire ces informations directement dans une application financière tierce (par exemple, Dynamics CRM). 


## <a name="attach-your-sharepoint-document-library-to-the-contracts-tab"></a>Joindre votre bibliothèque SharePoint documents à l’onglet Contrats

Une fois que vous avez créé un onglet **Contrats** dans votre canal de gestion des contrats, vous devez y attacher [SharePoint bibliothèque de documents.](https://support.microsoft.com/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b) La SharePoint de documents que vous souhaitez attacher est celle à laquelle vous avez appliqué votre modèle de SharePoint Syntex document dans la section précédente.

Une fois que vous avez SharePoint bibliothèque de documents, vous pouvez afficher les contrats classifiés via un affichage de liste par défaut.

   ![Affichage Liste de SharePoint bibliothèque.](../media/content-understanding/list-view.png)

## <a name="customize-your-contracts-tab-tile-view"></a>Personnaliser l’affichage des vignettes de l’onglet Contrats

> [!NOTE]
> Cette section fait référence à des exemples de code qui sont contenus dans le [ContractTileFormatting.js](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) sur le fichier qui est inclus dans le référentiel des ressources de la solution de gestion [des contrats.](https://github.com/pnp/syntex-samples/tree/main/scenario%20assets/Contracts%20Management)

Bien Teams vous permet d’afficher vos contrats dans une vue en mosaïque, vous pouvez le personnaliser pour afficher les données de contrat que vous souhaitez rendre visibles dans la carte de contrat. Par exemple, pour l’onglet **Contrats,** il est important que les membres voient le client, le fournisseur et le montant des frais sur la carte de contrat. Tous ces champs ont été extraits de chaque contrat via votre modèle SharePoint Syntex qui a été appliqué à votre bibliothèque de documents. Vous souhaitez également être en mesure de modifier la barre d’en-tête de vignette en différentes couleurs pour chaque état afin que les membres puissent facilement voir où se trouve le contrat dans le processus d’approbation. Par exemple, tous les contrats approuvés auront une barre d’en-tête bleue.

   ![Affichage en mosaïque de SharePoint bibliothèque.](../media/content-understanding/tile.png)

La vue de vignette personnalisée que vous utilisez nécessite que vous ayiez apporté des modifications au fichier JSON utilisé pour mettre en forme la vue de vignette actuelle. Vous pouvez référencer le fichier JSON utilisé pour créer l’affichage de carte enContractTileFormatting.js[fichier on.](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) Dans les sections suivantes, vous verrez des sections spécifiques du code pour les fonctionnalités qui se voient dans les cartes de contrat.

Si vous souhaitez afficher ou modifier le code JSON de votre affichage dans votre canal Teams, dans le canal Teams, sélectionnez le menu déroulant d’affichage, puis sélectionnez Mettre en forme l’affichage **actuel.**

   ![Capture d’écran du format json dans Teams canal.](../media/content-understanding/jason-format.png)

## <a name="card-size-and-shape"></a>Taille et forme de la carte

Dans la [ContractTileFormatting.jsdu](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) fichier, consultez la section suivante pour voir le code de mise en forme de la taille et de la forme de la carte.

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

Le code suivant vous permet de définir l’état de chaque carte de titre. Notez que chaque valeur d’état (*Nouveau*, *En révision,* *Approuvé* et Rejeté *)* affiche un code de couleur différent pour chacun d’eux. Dans la [ContractTileFormatting.jssur le](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) fichier, regardez la section qui définit l’état.

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

Chaque carte de contrat affiche trois champs qui ont été extraits pour chaque contrat (*Client*, *Fournisseur* et Montant *des frais*). En outre, vous souhaitez également afficher l’heure/la date de classement du fichier par le modèle SharePoint Syntex utilisé pour l’identifier.

Dans le [ContractTileFormatting.jssur le](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) fichier, les sections suivantes définissent chacune d’elles.

### <a name="client"></a>Client

Cette section définit la façon dont « Client » s’affichera sur la carte et utilise la valeur du contrat spécifique.

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

### <a name="contractor"></a>Resoe

Cette section définit la façon dont le « Programme d’entreprise » s’affichera sur la carte et utilise la valeur du contrat spécifique.

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

Cette section définit la façon dont le « montant des frais » s’affichera sur la carte et utilise la valeur du contrat spécifique.

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

Cette section définit la façon dont « Classification » s’affichera sur la carte et utilise la valeur du contrat spécifique.

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

[Étape 3. Utiliser Power Automate pour créer le flux pour traiter vos contrats](solution-manage-contracts-step3.md)
