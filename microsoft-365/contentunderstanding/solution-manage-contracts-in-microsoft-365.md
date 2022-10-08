---
title: Gérer des contrats en utilisant la solution Microsoft 365
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.service: microsoft-365-enterprise
ms.collection:
- m365solution-managecontracts
- m365solution-overview
- highpri
- m365initiative-syntex
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Découvrez comment gérer les contrats à l’aide d’une solution Microsoft 365 de SharePoint Syntex, de listes SharePoint, de Microsoft Teams et de Power Automate.
ms.openlocfilehash: edb05502ff9f4a84f194e4f991307886ce85bd46
ms.sourcegitcommit: 674dfa2cb2f20546d2f7822e09bacf0e12e2718b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68041170"
---
# <a name="manage-contracts-using-a-microsoft-365-solution"></a>Gérer des contrats en utilisant la solution Microsoft 365

Cet article explique comment créer une solution de gestion des contrats pour votre organisation à l’aide de SharePoint Syntex et de composants de Microsoft 365. Il vous fournit un framework pour vous aider à planifier et à créer une solution qui répond à vos besoins métier uniques. Même si cette solution parle de gestion des contrats, vous pouvez l’adapter pour créer d’autres solutions de gestion des documents, telles que des relevés de travail ou des factures.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWJUR0]

</br>

## <a name="identify-the-business-problem"></a>Identifier le problème métier

La première étape de la planification de votre système de gestion des contrats consiste à comprendre le problème que vous essayez de résoudre. Pour cette solution, quatre problèmes clés doivent être résolus :

- **Identifiez les contrats**. Votre organisation travaille avec de nombreux documents, tels que des factures, des contrats, des relevés de travail, etc.  Certains sont des ressources numériques envoyées par e-mail, et d’autres sont des ressources en papier envoyées par courrier traditionnel. Vous avez besoin d’un moyen d’identifier tous les contrats clients de tous les autres documents, puis de les classer comme tels.

- **Suivez l’historique des approbations de contrat**. Votre organisation a besoin d’un moyen fiable de déterminer si les contrats ont été approuvés ou rejetés, et si le paiement a été traité. 

- **Site pour gérer les approbations de contrat**. Votre organisation doit configurer un site collaboratif dans lequel toutes les parties prenantes requises peuvent facilement passer en revue les contrats. Les parties prenantes doivent être en mesure d’examiner l’ensemble du contrat si nécessaire, mais se soucient surtout de voir plusieurs champs clés de chaque contrat (par exemple, le nom du client, le numéro de bon de commande et le coût total). Les parties prenantes doivent être en mesure d’approuver ou de rejeter facilement les contrats entrants.

- **Acheminer les contrats examinés**. Les contrats approuvés et rejetés doivent être acheminés via un flux de travail spécifique. Les contrats approuvés doivent être acheminés vers une demande tierce pour le traitement des paiements. Les contrats rejetés doivent être routées pour une révision supplémentaire.

## <a name="overview-of-the-solution"></a>Vue d’ensemble de la solution

  ![Diagramme de la solution utilisant SharePoint Syntex, des listes SharePoint, Teams et Power Automate.](../media/content-understanding/syntex-solution-manage-contracts-setup-steps.png)

Cette solution de gestion des contrats comprend quatre composants de Microsoft 365 :

- **Microsoft SharePoint Syntex** : Créez des modèles pour identifier et classifier vos fichiers de contrat, puis extrayez les données appropriées à partir de ces fichiers.

- **Listes Microsoft SharePoint** : utilisez la mise en forme disponible dans les listes SharePoint modernes pour présenter les contrats dans un format convivial.

- **Microsoft Teams** : utilisez les fonctionnalités d’un canal Teams et des onglets associés pour permettre à vos parties prenantes d’examiner et de gérer les contrats.

- **Power Automate** : Utilisez des flux pour guider les contrats tout au long du processus d’approbation, puis vers une demande de paiement tierce.

### <a name="how-it-all-works"></a>Fonctionnement de tout cela

  ![Diagramme de la solution montrant le flux de travail permettant de charger des documents, d’extraire des données, d’avertir les parties prenantes et d’approuver ou de rejeter le contrat.](../media/content-understanding/syntex-solution-manage-contracts-overview.png)

1. Les documents sont chargés dans une bibliothèque de documents SharePoint. Un modèle de compréhension de document SharePoint Syntex a été appliqué à la bibliothèque de documents. Il vérifie chaque fichier pour voir s’il correspond à un type de contenu « contrat » qu’il est formé à rechercher. S’il trouve une correspondance, il classe le fichier en tant que « contrat » et met à jour le type de contenu du document.

2. Le modèle extrait également des données spécifiques de chaque fichier de contrat que les parties prenantes souhaitent voir, telles que le *montant du client*, de l’entrepreneur et *des frais*. 

    La page suivante est un exemple de contrat que le modèle est formé pour identifier.

      ![Exemple de contrat.](../media/content-understanding/contract.png)

3. Dans Microsoft Teams, toutes les parties prenantes sont membres d’un canal Teams sécurisé dans lequel tous les contrats de la bibliothèque de documents sont visibles pour approbation ou rejet. À l’aide de la fonctionnalité Teams, toutes les parties prenantes sont averties quand de nouveaux contrats doivent être examinés.

4. À l’aide de Power Automate, les contrats sont déplacés via le processus d’approbation dans le canal Teams. Lorsqu’un membre approuve un contrat, l’état du contrat est remplacé par approuvé, tous les membres sont avertis par le biais d’un billet Teams et un élément de ligne est créé pour montrer que le contrat est prêt pour le paiement. Ce processus peut être étendu pour écrire directement dans une demande de paiement financière tierce.

5. Lorsqu’un membre rejette un contrat, l’état est remplacé par rejeté et tous les membres sont avertis par le biais d’un billet Teams.

6. Le résultat final de cette solution est un processus métier automatisé pour votre organisation. Les employés peuvent facilement utiliser la vue de vignette personnalisée dans Teams pour lancer et surveiller le flux de travail d’approbation de vos documents. 

     ![Onglet Contrats.](../media/content-understanding/tile-view.png)

### <a name="licensing-requirements"></a>Conditions d'octroi de licence

Cette solution s’appuie sur les fonctionnalités suivantes, toutes disponibles dans le cadre d’une licence Microsoft 365 Entreprise (E1, E3, E5, F3) ou Business (De base, Standard ou Premium) :

- Microsoft SharePoint Syntex
- Microsoft Teams
- Power Automate

### <a name="learn-how-to-use-sharepoint-syntex"></a>Découvrez comment utiliser SharePoint Syntex

Vous débutez avec SharePoint Syntex ? Découvrez comment utiliser SharePoint Syntex pour gérer du contenu à l’aide de l’IA.

La prise [en main de SharePoint Syntex](/training/paths/syntex-get-started) parcours d’apprentissage vous apprend à utiliser des modèles de compréhension de document et de traitement de formulaires pour classifier des documents, extraire du texte et étiqueter vos documents pour une gestion rapide et facile des connaissances.

## <a name="create-the-solution"></a>Créer la solution

Les sections suivantes expliquent en détail comment configurer votre solution de gestion des contrats. Il est divisé en trois étapes :

- [Étape 1. Utiliser SharePoint Syntex pour identifier les fichiers de contrat et extraire des données](solution-manage-contracts-step1.md)
- [Étape 2. Utiliser Microsoft Teams pour créer votre canal de gestion des contrats](solution-manage-contracts-step2.md)
- [Étape 3. Utiliser Power Automate pour créer le flux de traitement de vos contrats](solution-manage-contracts-step3.md)
