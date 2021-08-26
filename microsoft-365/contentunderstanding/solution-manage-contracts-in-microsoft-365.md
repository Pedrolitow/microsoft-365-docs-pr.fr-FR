---
title: Gérer des contrats en utilisant la solution Microsoft 365
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.prod: microsoft-365-enterprise
ms.collection: m365solution-managecontracts m365solution-overview
search.appverid: ''
localization_priority: None
ROBOTS: ''
description: Découvrez comment gérer les contrats à l’aide Microsoft 365 solution SharePoint Syntex, SharePoint listes, Microsoft Teams et Power Automate.
ms.openlocfilehash: d890305912c8b86065a89dac1b7da8f797604405
ms.sourcegitcommit: 6c342a956b2dbc32be33bac1a23a5038490f1b40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58533374"
---
# <a name="manage-contracts-using-a-microsoft-365-solution"></a>Gérer des contrats en utilisant la solution Microsoft 365

Cet article explique comment créer une solution de gestion des contrats pour votre organisation à l’aide de SharePoint Syntex et de composants de Microsoft 365. Il vous fournit une infrastructure pour vous aider à planifier et à créer une solution qui répond aux besoins uniques de votre entreprise. Même si cette solution parle de gestion des contrats, vous pouvez l’adapter pour créer d’autres solutions de gestion de documents, telles que des déclarations de travail ou des factures.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWJUR0]

</br>

## <a name="identify-the-business-problem"></a>Identifier le problème d’entreprise

La première étape de la planification de votre système de gestion des contrats consiste à comprendre le problème que vous essayez de résoudre. Pour cette solution, quatre problèmes clés doivent être résolus :

- **Identifier les contrats**. Votre organisation travaille avec de nombreux documents, tels que des factures, des contrats, des déclarations de travail, etc.  Certains sont des biens numériques envoyés par courrier électronique, d’autres des biens papier envoyés par courrier électronique traditionnel. Vous avez besoin d’un moyen d’identifier tous les contrats client de tous les autres documents, puis de les classer comme tels.

- **Suivi de l’historique des approbations de contrat.** Votre organisation a besoin d’un moyen fiable pour déterminer si les contrats ont été approuvés ou rejetés, et si le paiement a été effectué. 

- **Site pour gérer les approbations de contrat.** Votre organisation doit configurer un site de collaboration dans lequel toutes les parties prenantes requises peuvent facilement examiner les contrats. Les parties prenantes doivent pouvoir examiner l’intégralité du contrat si nécessaire, mais se soucient principalement de voir plusieurs champs clés de chaque contrat (par exemple, le nom du client, le numéro de bon de service et le coût total). Les parties prenantes doivent pouvoir facilement approuver ou rejeter les contrats entrants.

- **Contrats révisés d’itinéraire.** Les contrats approuvés et rejetés doivent être acheminés via un flux de travail spécifique. Les contrats approuvés doivent être acheminés vers une application tierce pour le traitement des paiements. Les contrats rejetés doivent être acheminés pour une révision supplémentaire.

## <a name="overview-of-the-solution"></a>Vue d’ensemble de la solution

  ![Diagramme de la solution à l’aide SharePoint Syntex, SharePoint listes, Teams et Power Automate.](../media/content-understanding/syntex-solution-manage-contracts-setup-steps.png)

Cette solution de gestion des contrats comprend quatre composants de Microsoft 365 :

- **Microsoft SharePoint Syntex**: créez des modèles pour identifier et classer vos fichiers de contrat, puis extrayez-y les données appropriées.

- **Listes SharePoint Microsoft**: utilisez la mise en forme disponible dans les listes SharePoint modernes pour présenter les contrats dans un format commercial convivial.

- **Microsoft Teams**: utilisez les fonctionnalités d’un canal Teams et des onglets associés pour permettre à vos parties prenantes de réviser et de gérer les contrats.

- **Power Automate**: utilisez des flux pour guider les contrats dans le processus d’approbation, puis vers une application tierce pour le paiement.

### <a name="how-it-all-works"></a>Fonctionnement

  ![Diagramme de la solution montrant le flux de travail pour télécharger des documents, extraire des données, avertir les parties prenantes et approuver ou rejeter le contrat.](../media/content-understanding/syntex-solution-manage-contracts-overview.png)

1. Les documents sont téléchargés vers une bibliothèque SharePoint documents. Un SharePoint Syntex de compréhension de document a été appliqué à la bibliothèque de documents. Il vérifie chaque fichier pour voir s’il y a une correspondance avec un type de contenu « contrat » qu’il est entraîné à rechercher. S’il trouve une correspondance, il classifie le fichier en tant que « contrat » et met à jour le type de contenu pour le document.

2. Le modèle retire également des données spécifiques à partir de chaque fichier de contrat que les parties prenantes sont intéressées à voir, telles que le *client,* *le* coût et le montant *des frais.*

    La page suivante est un exemple de contrat que le modèle est formé pour identifier.

      ![Exemple de contrat.](../media/content-understanding/contract.png)

3. Dans Microsoft Teams, toutes les parties prenantes sont membres d’un canal Teams sécurisé dans lequel tous les contrats de la bibliothèque de documents sont visibles pour approbation ou rejet. À l’Teams, toutes les parties prenantes sont averties lorsque de nouveaux contrats doivent être révisés.

4. À l’Power Automate, les contrats sont déplacés via le processus d’approbation dans Teams canal. Lorsqu’un membre approuve un contrat, l’état du contrat passe à approuvé, tous les membres sont avertis par le biais d’un billet de Teams et un élément de ligne est créé pour montrer que le contrat est prêt pour le paiement. Ce processus peut être étendu pour écrire directement dans une application financière tierce pour paiement.

5. Lorsqu’un membre rejette un contrat, l’état est rejeté et tous les membres sont avertis par le biais d’Teams billet.

6. Le résultat final de cette solution est un processus d’entreprise automatisé pour votre organisation. Les employés peuvent facilement utiliser la vue de vignette personnalisée dans Teams pour lancer et surveiller le flux de travail d’approbation de vos documents. 

     ![Onglet Contrats.](../media/content-understanding/tile-view.png)

### <a name="licensing-requirements"></a>Conditions d'octroi de licence

Cette solution s’appuie sur les fonctionnalités suivantes, disponibles dans le cadre d’une licence Microsoft 365 Entreprise (E1, E3, E5, F3) ou Business (De base, Standard ou Premium) :

- Microsoft SharePoint Syntex
- Microsoft Teams
- Power Automate

### <a name="learn-how-to-use-sharepoint-syntex"></a>Découvrez comment utiliser les SharePoint Syntex

Vous n’SharePoint Syntex ? Découvrez comment utiliser les SharePoint Syntex pour gérer du contenu à l’aide de l’IA.

La prise en charge de [l’apprentissage SharePoint Syntex](/learn/paths/syntex-get-started) vous montre comment utiliser les modèles de compréhension et de traitement des formulaires pour classifier des documents, extraire du texte et étiqueter vos documents pour une gestion rapide et facile des connaissances.

## <a name="create-the-solution"></a>Créer la solution

Les sections suivantes détailleront la configuration de votre solution de gestion des contrats. Il est divisé en trois étapes :

- [Étape 1. Utiliser SharePoint Syntex pour identifier les fichiers de contrat et extraire des données](solution-manage-contracts-step1.md)
- [Étape 2. Utiliser Microsoft Teams pour créer votre canal de gestion de contrat](solution-manage-contracts-step2.md)
- [Étape 3. Utiliser Power Automate pour créer le flux pour traiter vos contrats](solution-manage-contracts-step3.md)
