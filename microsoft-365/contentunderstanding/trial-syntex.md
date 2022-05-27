---
title: Exécuter un essai de Microsoft SharePoint Syntex
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
description: Découvrez comment planifier, inscrire et exécuter un programme pilote d’essai pour SharePoint Syntex dans votre organisation.
ms.openlocfilehash: ccbf1208d5c655171825b5a96f3a78b25ea3bbf2
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754441"
---
# <a name="run-a-trial-of-microsoft-sharepoint-syntex"></a>Exécuter un essai de Microsoft SharePoint Syntex

Cet article explique comment configurer et exécuter un programme pilote d’essai pour déployer SharePoint Syntex dans votre organisation. Il recommande également les meilleures pratiques pour la version d’évaluation.

## <a name="sign-up-for-a-trial"></a>S’inscrire à une version d’évaluation

La version d’évaluation de SharePoint Syntex donne accès à 300 utilisateurs pendant 30 jours.

> [!NOTE]
> Jusqu’à 300 utilisateurs sont inclus dans la version d’évaluation pour garantir l’ajout automatique de 1 million de crédits AI Builder. Vous n’avez pas besoin d’inclure 300 utilisateurs pour qu’une version d’évaluation réussisse.

Vous pouvez obtenir la version d’évaluation à partir de l’une des sources suivantes :

- Page [du produit SharePoint Syntex](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex?activetab=pivot:overviewtab)

- Le [Centre d'administration Microsoft 365](https://admin.microsoft.com)
    1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com).
    2. Accédez aux <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**services d’achat**</a> **de facturation** > .
    3. Faites défiler la page vers le bas jusqu’à la section **Modules complémentaires**.
    4. Sur la vignette SharePoint Syntex, sélectionnez **Détails**.
    5. Sélectionnez **Démarrer l’essai gratuit**.
    6. Pour confirmer la version d’évaluation, suivez les étapes restantes de l’Assistant.

Vous devez être un administrateur général ou un administrateur de facturation Microsoft 365 pour activer une version d’évaluation.

### <a name="who-should-be-involved-in-a-trial"></a>Qui doit être impliqué dans un essai

|Rôle|Activité|
|---|---|
|Microsoft 365 administrateur général ou administrateur de facturation|Activer la version d’évaluation et attribuer des licences|
|Microsoft 365 administrateur global ouadministrateur SharePoint administrateur|Configurer SharePoint Syntex et créer des centres de contenu|
|Utilisateurs professionnels|Génération et test de modèles|

### <a name="before-you-activate-a-trial"></a>Avant d’activer une version d’évaluation

Pour planifier correctement un essai SharePoint Syntex, tenez compte des facteurs suivants :

- Les tests les plus significatifs sont effectués sur des scénarios et des données « réels ».
- Vous ne pouvez activer une version d’évaluation SharePoint Syntex qu’une seule fois par locataire.

Un locataire de test ou de démonstration peut être utilisé comme une « exécution à sec » pour parcourir les étapes d’activation et les contrôles d’administration. Mais il est probablement préférable d’évaluer le modèle en s’appuyant sur un locataire de production.

Pour optimiser la valeur d’une version d’évaluation sur un locataire de production, la planification et l’engagement de l’entreprise sont essentiels. Vous devez impliquer un ou plusieurs secteurs d’activité pour identifier trois à six cas d’usage qui pourraient être traités par SharePoint Syntex. Ces cas d’usage doivent :

- Incluez des scénarios qui pourraient être résolus par le traitement de formulaire ou le modèle de compréhension de document.
- Avoir une compréhension claire de l’objectif de toutes les métadonnées extraites ; Par exemple, affichez la mise en forme ou l’automatisation à l’aide de Power Automate. Bien que SharePoint Syntex se concentre sur la classification des documents et l’extraction des métadonnées, la valeur à quantifier est ce que ces métadonnées permettent.
- Être basé sur un jeu de données défini ; par exemple, des sites ou bibliothèques SharePoint spécifiques. Une idée fausse courante de SharePoint Syntex est que les modèles à usage général peuvent être appliqués à l’ensemble du contenu de l’organisation. Une vue plus précise est que des modèles sont créés pour aider à résoudre des problèmes métier spécifiques dans des emplacements ciblés.

Tous ces cas d’usage peuvent ne pas être adaptés à SharePoint Syntex. L’objectif d’un essai de qualité n’est pas de prouver que SharePoint Syntex s’adaptera à tous les scénarios. Au lieu de cela, la version d’évaluation doit vous aider à mieux comprendre la valeur du produit.

Pour chacun des cas d’usage planifiés, identifiez les utilisateurs qui sont des experts en la matière dans le contenu ou le processus associé. La création de modèles SharePoint Syntex est axée sur les experts du domaine dans le contenu, plutôt que sur les professionnels de l’informatique ou les ressources des développeurs.

## <a name="activate-a-trial"></a>Activer une version d’évaluation

Lorsque vous lancez un essai, vous devez :

- Attribuez des licences aux utilisateurs concernés.
- Effectuez [une configuration supplémentaire de SharePoint Syntex](set-up-content-understanding.md).
  - Vous souhaiterez peut-être [créer d’autres centres de contenu](create-a-content-center.md).

Une fois l’essai activé, vous pouvez créer des modèles et traiter des fichiers. Consultez [des conseils pour la création de modèles](create-a-content-center.md).

## <a name="during-a-trial"></a>Lors d’un essai

Les périodes d’essai étant limitées, il est préférable de se concentrer initialement sur la question de savoir si SharePoint Syntex modèles peuvent classifier des documents et extraire des métadonnées pour les cas d’usage définis. Une fois la période d’essai terminée, vous pouvez évaluer la façon dont les métadonnées peuvent être exploitées.

## <a name="after-a-trial"></a>Après un essai

En fonction du résultat de l’essai, vous pouvez décider s’il faut poursuivre l’utilisation de SharePoint Syntex en production.

### <a name="proceed-to-production-use"></a>Passer à l’utilisation en production

Pour garantir la continuité du service, vous devez acheter le nombre de [licences](syntex-licensing.md) requis et attribuer ces licences aux utilisateurs. Les utilisateurs d’évaluation qui n’ont pas de licence complète à la fin de la période d’essai ne pourront pas utiliser entièrement SharePoint Syntex.

Vous devrez peut-être estimer l’utilisation prévue du traitement des formulaires et planifier le nombre attendu de crédits AI Builder. Pour obtenir de [l’aide, consultez Estimer la capacité AI Builder qui vous convient](https://powerapps.microsoft.com/ai-builder-calculator/).

### <a name="dont-proceed-to-production-use"></a>Ne passez pas à l’utilisation en production

Si vous n’achetez pas de licences après la version d’évaluation :

- Vous ne pourrez pas créer de modèles.
- Les bibliothèques qui exécutaient des modèles ne classifient plus automatiquement les fichiers ni n’extraient les modèles.
- Les fichiers précédemment classifiés ou les métadonnées extraites ne seront pas affectés.
- Les centres de contenu et les modèles de compréhension de document ne sont pas automatiquement supprimés. Ceux-ci resteront disponibles si vous décidez d’acheter des licences à l’avenir.
- Les modèles de traitement de formulaire seront stockés dans l’instance Dataverse (précédemment nommée Common Data Service (CDS) de l’environnement Power Platform par défaut. Ceux-ci peuvent être utilisés avec les licences futures pour SharePoint Syntex ou avec les fonctionnalités AI Builder dans Power Platform.

## <a name="see-also"></a>Articles associés

[Démarrage l’adoption de SharePoint Syntex](adoption-getstarted.md)
