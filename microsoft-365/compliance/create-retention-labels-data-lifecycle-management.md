---
title: Créer des étiquettes de rétention pour les exceptions
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Instructions pour créer des étiquettes de rétention pour les exceptions aux stratégies de rétention pour la gestion du cycle de vie des données afin de pouvoir conserver ce dont vous avez besoin et supprimer ce dont vous n’avez pas besoin.
ms.openlocfilehash: 0951ce1fea2f9324c19ec0bf17451d458b4914d1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632572"
---
# <a name="create-retention-labels-for-exceptions-to-your-retention-policies"></a>Créer des étiquettes de rétention pour les exceptions à vos stratégies de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Dans le cadre de votre stratégie de gouvernance des données pour conserver ce dont vous avez besoin et supprimer ce dont vous n’avez pas besoin, vous devrez peut-être créer quelques étiquettes de rétention pour les éléments qui nécessitent des exceptions à vos stratégies de rétention.

Alors que les stratégies de rétention s'appliquent automatiquement à tous les éléments au niveau du conteneur (tels que les sites SharePoint, les boîtes aux lettres des utilisateurs, etc.), les étiquettes de rétention s'appliquent à des éléments individuels, tels qu'un document SharePoint ou un message électronique.

Veillez à bien comprendre les [principes de rétention](retention.md#the-principles-of-retention-or-what-takes-precedence) avant d’utiliser des étiquettes de rétention pour compléter une stratégie de rétention pour des éléments SharePoint, OneDrive ou Exchange spécifiques. En règle générale, vous utilisez des étiquettes de rétention pour conserver des éléments spécifiques plus longtemps qu’une stratégie de rétention appliquée, mais elles peuvent également être utilisées pour remplacer la suppression automatique à la fin de la période de rétention ou appliquer une autre période de suppression.

Par exemple : la majorité du contenu de vos sites SharePoint doit être conservée pendant trois ans, ce qui est couvert par une stratégie de rétention. Toutefois, certains documents de contrat doivent être conservés pendant sept ans. Ces exceptions peuvent être traitées avec des étiquettes de rétention. Après avoir affecté la stratégie de rétention à tous les sites SharePoint, vous appliquez les étiquettes de rétention aux documents du contrat. Tous les éléments SharePoint seront conservés pendant trois ans, et uniquement les documents de contrat seront conservés pendant sept ans.

Pour plus d’exemples sur la façon dont les étiquettes de rétention peuvent être utilisées comme exceptions aux stratégies de rétention, consultez [Combinaison des stratégies de rétention et des étiquettes de rétention](retention.md#combining-retention-policies-and-retention-labels).

Les étiquettes de rétention offrent également plus de fonctionnalités que les stratégies de rétention. Pour plus d’informations, consultez [Comparer les fonctionnalités des stratégies de rétention et des étiquettes de rétention](retention.md#compare-capabilities-for-retention-policies-and-retention-labels).

Utilisez les informations suivantes pour vous aider à créer des étiquettes de rétention pour compléter les stratégies de rétention dans le cadre de votre stratégie de gestion du cycle de vie des données.

> [!NOTE]
> Créez des étiquettes de rétention à partir de la solution de **Gestion des enregistrements** plutôt que de la solution de **Gestion du cycle de vie des données** si vous devez utiliser des étiquettes de rétention pour gérer les éléments de grande valeur pour les exigences commerciales, légales ou réglementaires en matière de conservation des enregistrements. Par exemple, vous souhaitez utiliser la rétention basée sur les événements ou la révision avant destruction. Pour obtenir des instructions, consultez [Utiliser le plan de fichiers pour créer et gérer des étiquettes de rétention](file-plan-manager.md).

## <a name="before-you-begin"></a>Avant de commencer

L’administrateur général de votre organisation dispose de toutes les autorisations pour créer et gérer les étiquettes de rétention et leurs stratégies. Si vous ne vous connectez pas en tant qu’administrateur général, consultez [Autorisations pour les stratégies de rétention et les étiquettes de rétention](get-started-with-data-lifecycle-management.md#permissions-for-retention-policies-and-retention-labels).

## <a name="how-to-create-retention-labels-for-data-lifecycle-management"></a>Comment créer des étiquettes de rétention pour la gestion du cycle de vie des données

1. Dans le [Portail de conformité Microsoft Purview](https://compliance.microsoft.com/), accédez à l’onglet **Solutions** > **Gestion du cycle de vie des données** > **Étiquettes** > + **Créer une étiquette**
    
    Vous ne voyez pas immédiatement la solution **Gestion du cycle de vie des données** ? Sélectionnez tout d’abord **Afficher tout**. 

2. Suivez les invites pour créer l’étiquette de rétention. Faites attention au nom que vous choisissez, car il ne peut pas être modifié après l’enregistrement de l’étiquette.
    
    Pour plus d’informations sur les paramètres de rétention, voir Paramètres pour [conserver et supprimer du contenu.](retention-settings.md#settings-for-retaining-and-deleting-content)

3. Une fois l’étiquette créée, les options permettant de la publier s’affichent. Appliquez automatiquement l’étiquette, ou enregistrez-la simplement : sélectionnez **Enregistrez simplement l’étiquette pour l'instant**, puis sélectionnez **Terminé**.

4. Répétez ces étapes pour créer d’autres étiquettes de rétention dont vous avez besoin pour différents paramètres de rétention.

Pour modifier une étiquette existante, sélectionnez-la, puis sélectionnez l’option **Modifier l’étiquette** pour démarrer la configuration Modifier l'étiquette de rétention qui vous permet de modifier les descriptions d'étiquettes et tous les paramètres éligibles.

La plupart des paramètres ne peuvent pas être modifiés une fois l’étiquette créée et enregistrée, notamment :
- Nom de l’étiquette de rétention et paramètres de rétention, à l’exception de la période de rétention. Cependant, vous ne pouvez pas modifier la période de rétention lorsque la période de rétention est basée sur la période d’étiquetage des éléments.

## <a name="next-steps"></a>Prochaines étapes

Maintenant que vous avez créé des étiquettes de rétention, elles sont prêtes à être ajoutées aux éléments en les publiant ou en les appliquant automatiquement :
- [Publier des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)
- [Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)
