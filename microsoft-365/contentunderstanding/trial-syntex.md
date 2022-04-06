---
title: Exécuter une version d’essai de Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris; jaeccles
ms.date: ''
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom:
- Adopt
- admindeeplinkMAC
search.appverid: ''
ms.localizationpriority: medium
description: Découvrez comment planifier, inscrire et exécuter un programme pilote d’essai pour SharePoint Syntex votre organisation.
ms.openlocfilehash: fc4221b0022aca8a0564c78e64d94028f6483104
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507096"
---
# <a name="run-a-trial-of-microsoft-sharepoint-syntex"></a>Exécuter une version d’essai de Microsoft SharePoint Syntex

Cet article explique comment configurer et exécuter un programme pilote d’essai pour déployer des SharePoint Syntex votre organisation. Il recommande également les meilleures pratiques pour la version d’essai.

## <a name="sign-up-for-a-trial"></a>S’inscrire à une version d’essai

La version d’SharePoint Syntex donne accès à 300 utilisateurs pendant 30 jours.

> [!NOTE]
> Jusqu’à 300 utilisateurs sont inclus dans la version d’essai pour garantir l’ajout automatique de 1 million de crédits générateur d’IA. Vous n’avez pas besoin d’inclure 300 utilisateurs pour qu’une version d’essai réussisse.

Vous pouvez obtenir la version d’essai à partir de l’une des sources suivantes :

- Page [SharePoint Syntex produit](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex?activetab=pivot:overviewtab)

- Le [Centre d'administration Microsoft 365](https://admin.microsoft.com)
    1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com).
    2. Go to <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**BillingPurchase**</a> >  Services.
    3. Faites défiler la page vers le bas jusqu’à la section **Modules complémentaires**.
    4. Sur la SharePoint Syntex, sélectionnez **Détails**.
    5. Sélectionnez **Démarrer l’essai gratuit**.
    6. Pour confirmer la version d’essai, suivez les étapes restantes de l’Assistant.

Vous devez être un administrateur Microsoft 365 général ou un administrateur de facturation pour activer une version d’essai.

### <a name="who-should-be-involved-in-a-trial"></a>Qui doivent être impliquées dans une version d’essai

|Rôle|Activité|
|---|---|
|Microsoft 365 administrateur global ou administrateur de facturation|Activer la version d’essai et attribuer des licences|
|Microsoft 365 administrateur global ouadministrateur SharePoint administrateur|Configurer SharePoint Syntex et créer des centres de contenu|
|Utilisateurs professionnels|Création et test de modèles|

### <a name="before-you-activate-a-trial"></a>Avant d’activer une version d’essai

Pour planifier correctement une SharePoint Syntex d’essai, prenons en compte les facteurs suivants :

- Les tests les plus significatifs sont effectués sur des scénarios et des données « réels ».
- Vous ne pouvez activer une version d SharePoint Syntex d’essai qu’une seule fois par client.

Un client de test ou de démonstration peut servir de « test » pour parcourir les étapes d’activation et les contrôles d’administration. Mais il est probablement préférable d’évaluer la construction de modèle sur un client de production.

Pour optimiser la valeur d’une version d’essai sur un client de production, la planification et l’engagement commercial sont essentiels. Vous devez impliquer un ou plusieurs secteurs d’activité pour identifier trois à six cas d’utilisation susceptibles d’être traités par SharePoint Syntex. Ces cas d’utilisation doivent :

- Incluez des scénarios qui pourraient être résolus par le modèle de traitement des formulaires ou de compréhension des documents.
- Comprendre clairement l’objectif de toutes les métadonnées extraites ; par exemple, afficher la mise en forme ou l’automatisation à l’aide Power Automate. Bien SharePoint Syntex se concentre sur la classification des documents et l’extraction des métadonnées, la valeur à quantifier est ce que cette métadonnées permet.
- Être basé sur un ensemble défini de données ; par exemple, des SharePoint sites ou bibliothèques spécifiques. Il est courant de se SharePoint Syntex que des modèles à usage général soient appliqués à l’ensemble du contenu de l’organisation. Une vue plus précise est que les modèles sont conçus pour aider à résoudre des problèmes métiers spécifiques dans des emplacements ciblés.

Tous ces cas d’utilisation peuvent ne pas être adaptés aux SharePoint Syntex. L’objectif d’un essai de qualité n’est pas de prouver SharePoint Syntex tous les scénarios. Au lieu de cela, la version d’essai doit vous aider à mieux comprendre la valeur du produit.

Pour chacun des cas d’utilisation planifiés, identifiez les utilisateurs qui sont des experts techniques dans le contenu ou le processus associé. La création de modèles SharePoint Syntex est axée sur les experts de domaine dans le contenu, plutôt que sur les professionnels de l’informatique ou les ressources de développement.

## <a name="activate-a-trial"></a>Activer une version d’essai

Lorsque vous lancez une version d’essai, vous devez :

- Attribuer des licences aux utilisateurs concernés.
- Effectuez [une configuration supplémentaire de SharePoint Syntex](set-up-content-understanding.md).
  - Vous souhaitez [peut-être créer des centres de contenu supplémentaires](create-a-content-center.md).

Une fois la version d’évaluation activée, vous pouvez créer des modèles et traiter des fichiers. Voir les [conseils pour la création de modèles](create-a-content-center.md).

## <a name="during-a-trial"></a>Pendant une version d’essai

Les périodes d’essai étant limitées, il est préférable de se concentrer initialement sur le fait que les modèles SharePoint Syntex peuvent classer des documents et extraire des métadonnées pour les cas d’utilisation définis. Une fois la période d’évaluation terminée, vous pouvez évaluer la façon dont les métadonnées peuvent être exploitées.

## <a name="after-a-trial"></a>Après une version d’essai

En fonction du résultat de l’essai, vous pouvez décider s’il faut passer à l’utilisation de production de SharePoint Syntex.

### <a name="proceed-to-production-use"></a>Passer à l’utilisation de la production

Pour garantir la continuité du service, vous devez acheter le nombre requis de licences et les attribuer aux utilisateurs. Les utilisateurs de la version d’essai qui ne sont pas titulaires d’une licence complète à la fin de la période d’essai ne pourront pas utiliser entièrement SharePoint Syntex.

Vous de devez peut-être estimer l’utilisation prévue du traitement des formulaires et planifier le montant prévu des crédits du Générateur d’IA. Pour obtenir de l’aide, [voir Estimer la capacité du Générateur d’IA qui vous est utile](https://powerapps.microsoft.com/ai-builder-calculator/).

### <a name="dont-proceed-to-production-use"></a>Ne pas passer à l’utilisation en production

Si vous n’achetez pas de licences après la version d’essai :

- Vous ne pourrez pas créer de nouveaux modèles.
- Les bibliothèques qui étaient des modèles en cours d’exécution ne classifient plus automatiquement les fichiers ni n’extraient les modèles.
- Les fichiers précédemment classifiés ou les métadonnées extraites ne seront pas affectés.
- Les centres de contenu et les modèles de compréhension des documents ne seront pas automatiquement supprimés. Ceux-ci resteront disponibles si vous décidez d’acheter des licences à l’avenir.
- Les modèles de traitement des formulaires sont stockés dans l’instance Dataverse (précédemment appelée Common Data Service [CDS]) de l’environnement power platform par défaut. Ceux-ci peuvent être utilisés avec des licences futures pour SharePoint Syntex ou avec les fonctionnalités du Générateur d’IA dans la plateforme Power.

## <a name="see-also"></a>Voir aussi

[Adoption SharePoint Syntex Microsoft : Démarrage](adoption-getstarted.md)
