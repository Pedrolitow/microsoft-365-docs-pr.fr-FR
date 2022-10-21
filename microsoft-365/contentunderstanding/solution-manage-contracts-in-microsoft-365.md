---
title: Gérer des contrats en utilisant la solution Microsoft 365
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.service: microsoft-syntex
ms.collection:
- m365solution-managecontracts
- m365solution-overview
- highpri
- m365initiative-syntex
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Découvrez comment gérer les contrats à l’aide d’une solution Microsoft 365 de Microsoft Syntex, de listes SharePoint, de Microsoft Teams et de Power Automate.
ms.openlocfilehash: 2abb6e28f9bac16d374a4056b996c3067125c4f5
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68659191"
---
# <a name="manage-contracts-using-a-microsoft-365-solution"></a>Gérer des contrats en utilisant la solution Microsoft 365

Cet article explique comment créer une solution de gestion des contrats pour votre organisation à l’aide de Microsoft Syntex et des composants de Microsoft 365. Il vous fournit une infrastructure pour vous aider à planifier et à créer une solution qui répond à vos besoins métier uniques. Même si cette solution parle de gestion des contrats, vous pouvez l’adapter pour créer d’autres solutions de gestion de documents, telles que pour les relevés de travail ou les factures.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWJUR0]

</br>

## <a name="identify-the-business-problem"></a>Identifier le problème métier

La première étape de la planification de votre système de gestion des contrats consiste à comprendre le problème que vous essayez de résoudre. Pour cette solution, quatre problèmes clés doivent être résolus :

- **Identifier les contrats**. Votre organisation utilise de nombreux documents, tels que des factures, des contrats, des relevés de travail, etc.  Certaines sont des ressources numériques envoyées par courrier électronique, et d’autres sont des ressources papier envoyées par courrier traditionnel. Vous avez besoin d’un moyen d’identifier tous les contrats clients à partir de tous les autres documents, puis de les classer comme tels.

- **Suivez l’historique des approbations de contrat**. Votre organisation a besoin d’un moyen fiable de déterminer si les contrats ont été approuvés ou rejetés, et si le paiement a été traité. 

- **Site pour gérer les approbations de contrat.** Votre organisation doit configurer un site collaboratif dans lequel toutes les parties prenantes requises peuvent facilement examiner les contrats. Les parties prenantes doivent être en mesure d’examiner l’ensemble du contrat si nécessaire, mais se soucient principalement de voir plusieurs champs clés de chaque contrat (par exemple, le nom du client, le numéro de bon de commande et le coût total). Les parties prenantes doivent être en mesure d’approuver ou de rejeter facilement les contrats entrants.

- **Contrats révisés de routage**. Les contrats approuvés et rejetés doivent être routés via un workflow spécifique. Les contrats approuvés doivent être acheminés vers une application tierce pour le traitement des paiements. Les contrats rejetés doivent être routés pour un examen supplémentaire.

## <a name="overview-of-the-solution"></a>Vue d’ensemble de la solution

  ![Diagramme de la solution utilisant Syntex, les listes SharePoint, Teams et Power Automate.](../media/content-understanding/syntex-solution-manage-contracts-setup-steps.png)

Cette solution de gestion des contrats comprend quatre composants de Microsoft 365 :

- **Microsoft Syntex** : créez des modèles pour identifier et classifier vos fichiers de contrat, puis extrayez-en les données appropriées.

- **Listes Microsoft SharePoint** : utilisez la mise en forme disponible dans les listes SharePoint modernes pour présenter les contrats dans un format convivial pour l’entreprise.

- **Microsoft Teams** : utilisez les fonctionnalités d’un canal Teams et des onglets associés pour permettre à vos parties prenantes d’examiner et de gérer les contrats.

- **Power Automate** : utilisez des flux pour guider les contrats tout au long du processus d’approbation, puis vers une application tierce pour le paiement.

### <a name="how-it-all-works"></a>Fonctionnement de l’ensemble

  ![Diagramme de la solution montrant le flux de travail permettant de charger des documents, d’extraire des données, d’informer les parties prenantes et d’approuver ou de rejeter le contrat.](../media/content-understanding/syntex-solution-manage-contracts-overview.png)

1. Les documents sont chargés dans une bibliothèque de documents SharePoint. Un modèle syntex de traitement de document non structuré a été appliqué à la bibliothèque de documents. Il vérifie chaque fichier pour voir s’il correspond à un type de contenu « contrat » qu’il est entraîné à rechercher. S’il trouve une correspondance, il classe le fichier en tant que « contrat » et met à jour le type de contenu pour le document.

2. Le modèle extrait également des données spécifiques de chaque fichier de contrat que les parties prenantes sont intéressées à voir, telles que le *client*, *l’entrepreneur* et le *montant des frais*.

    La page suivante est un exemple de contrat que le modèle est entraîné à identifier.

      ![Exemple de contrat.](../media/content-understanding/contract.png)

3. Dans Microsoft Teams, toutes les parties prenantes sont membres d’un canal Teams sécurisé dans lequel tous les contrats de la bibliothèque de documents sont visibles pour approbation ou rejet. En utilisant la fonctionnalité Teams, toutes les parties prenantes sont averties lorsque de nouveaux contrats doivent être examinés.

4. À l’aide de Power Automate, les contrats sont déplacés via le processus d’approbation dans le canal Teams. Lorsqu’un membre approuve un contrat, l’état du contrat est remplacé par Approuvé, tous les membres sont avertis par le biais d’une publication Teams et un élément de ligne est créé pour indiquer que le contrat est prêt pour le paiement. Ce processus peut être étendu pour écrire directement dans une demande financière tierce pour paiement.

5. Lorsqu’un membre rejette un contrat, l’état est remplacé par Rejeté, et tous les membres sont avertis par le biais d’une publication Teams.

6. Le résultat final de cette solution est un processus métier automatisé pour votre organisation. Les employés peuvent facilement utiliser la vue de vignette personnalisée dans Teams pour lancer et surveiller le flux de travail d’approbation de vos documents. 

     ![Onglet Contrats.](../media/content-understanding/tile-view.png)

### <a name="licensing-requirements"></a>Conditions d'octroi de licence

Cette solution s’appuie sur les fonctionnalités suivantes, toutes disponibles dans le cadre d’une licence Microsoft 365 Entreprise (E1, E3, E5, F3) ou Business (De base, Standard ou Premium) :

- Microsoft Syntex
- Microsoft Teams
- Power Automate

### <a name="learn-how-to-use-syntex"></a>Découvrez comment utiliser Syntex

Vous débutez avec Microsoft Syntex ? Découvrez comment utiliser Syntex pour gérer du contenu à l’aide de l’IA.

Le parcours d’apprentissage [Prise en main de Microsoft Syntex](/training/paths/syntex-get-started) vous apprend à utiliser des modèles de traitement de documents non structurés, libres et non structurés pour classifier des documents, extraire du texte et étiqueter vos documents pour une gestion rapide et simple des connaissances.

## <a name="create-the-solution"></a>Créer la solution

Les sections suivantes expliquent en détail comment configurer votre solution de gestion des contrats. Il est divisé en trois étapes :

- [Étape 1. Utiliser Microsoft Syntex pour identifier les fichiers de contrat et extraire des données](solution-manage-contracts-step1.md)
- [Étape 2. Utiliser Microsoft Teams pour créer votre canal de gestion des contrats](solution-manage-contracts-step2.md)
- [Étape 3. Utiliser Power Automate pour créer le flux de traitement de vos contrats](solution-manage-contracts-step3.md)
