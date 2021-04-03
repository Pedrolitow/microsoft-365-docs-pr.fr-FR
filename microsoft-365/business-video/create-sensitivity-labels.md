---
title: Créer des étiquettes de sensibilité
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment créer et gérer des étiquettes de sensibilité.
ms.openlocfilehash: 997b05ba549d3dc57e1793585331dfcfae1e277b
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51578938"
---
# <a name="protect-documents-with-sensitivity-labels"></a>Protéger les documents avec des étiquettes de niveau de sensibilité

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3VRGT?autoplay=false]

Les étiquettes de niveau de sensibilité vous permettent de classifier et de protéger le contenu sensible à votre entreprise.

## <a name="try-it"></a>Essayez !

1. Dans le Centre [d’administration,](https://admin.microsoft.com)sélectionnez le **Centre d’administration** de la conformité.
1. Sélectionnez **Classification,** puis **Étiquettes de sensibilité.**
1. Sélectionnez **Créer une étiquette** et lorsque l’avertissement s’affiche, sélectionnez **Oui**.
1. Entrez un **nom d’étiquette,** **une boîte à outils** et une **description.** Sélectionnez **Suivant**.
1. Activer le **chiffrement**. Choisissez quand vous souhaitez attribuer des autorisations, si vous souhaitez que l’accès de vos utilisateurs au contenu expire et si vous souhaitez autoriser l’accès hors connexion.
1. **Sélectionnez Attribuer des autorisations,** puis **Ajoutez ces adresses e-mail ou domaines.**
1. Entrez une adresse de messagerie ou un nom de domaine (par exemple, Contoso.org).  Sélectionnez **Ajouter** et répétez l’étape pour chaque adresse e-mail ou domaine que vous souhaitez ajouter.
1. Sélectionnez **Choisir des autorisations à partir d’autorisations prédéfines ou personnalisées.**
1. Utilisez la liste de listes pour sélectionner  des autorisations prédéfinées, telles que réviseur ou visionneuse, ou des **autorisations** personnalisées. Si vous avez **choisi Personnalisé,** sélectionnez les autorisations dans la liste. Sélectionnez **Enregistrer,** **Enregistrer,** puis **Suivant.**
1. Activer le **marquage de** contenu et choisir les marquages que vous souhaitez utiliser.
1. Pour chaque marquage que vous choisissez, sélectionnez **Personnaliser le texte.** Entrez le texte que vous souhaitez voir apparaître dans le document, puis définissez les options de police et de mise en page. Sélectionnez **Enregistrer,** puis répétez les marques supplémentaires. Sélectionnez **Suivant**.
1. Éventuellement, activer la protection contre la perte **de données de point de terminaison.** Sélectionnez **Suivant**.
1. Éventuellement, activer **l’étiquetage automatique.** Ajoutez une condition. Par exemple, sous **Détecter le contenu qui contient**, **sélectionnez Ajouter une condition.** Entrez la condition ; par exemple, ajoutez une condition qui, si Passport, la sécurité sociale ou d’autres informations sensibles sont détectées, l’étiquette sera ajoutée. Sélectionnez **Suivant**.
1. Examinez vos paramètres, puis sélectionnez **Créer.** Votre étiquette a été créée. Répétez ce processus pour les étiquettes supplémentaires que vous souhaitez.
1. Par défaut, les étiquettes apparaissent dans les applications Office dans cet ordre : **Confidentiel,** **Interne** et **Public**. Pour modifier l’ordre, pour chaque étiquette, sélectionnez Plus **d’actions** (les ellipses), puis déplacez l’étiquette vers le haut ou vers le bas. En règle générale, les autorisations sont répertoriées du niveau d’autorisation le plus bas au niveau le plus élevé.
1. Pour ajouter une sous-étiquette à une étiquette, sélectionnez **Plus d’actions,** puis **Ajoutez un sous-niveau**.
1. Lorsque vous avez terminé, choisissez **Publier des étiquettes,** **choisissez les étiquettes à publier,** puis **Ajoutez**. Sélectionnez les étiquettes que vous souhaitez publier, puis sélectionnez **Ajouter,** **Terminé,** puis **Suivant**.
1. Par défaut, la nouvelle stratégie d’étiquette est appliquée à tout le monde. Si vous souhaitez limiter l’application de la stratégie, sélectionnez Choisir des utilisateurs ou des **groupes,** puis **Ajoutez**. Sélectionnez à qui vous souhaitez que la stratégie s’applique, puis sélectionnez **Ajouter,** **Terminé,** puis **Suivant**.
1. Si vous souhaitez une étiquette par défaut pour les documents et les e-mails, sélectionnez l’étiquette de votre choix dans la liste de listes. Examinez les paramètres restants, ajustez selon les besoins, puis sélectionnez **Suivant**.
1. Entrez un **nom et** une **description** pour votre stratégie. Sélectionnez **Suivant**.
1. Examinez vos paramètres, puis sélectionnez **Publier.**

Pour que vos étiquettes fonctionnent, chaque utilisateur doit télécharger le client d’étiquetage unifié Azure Information Protection. Recherchez des **AzinfoProtection_UL.exe** sur le web, puis téléchargez-le à partir du Centre de téléchargement Microsoft et exécutez-le sur les ordinateurs de vos utilisateurs.

La prochaine fois que vous ouvrirez une application Office telle que Word, vous verrez les étiquettes de niveau de sensibilité qui ont été créées. Pour modifier ou appliquer une étiquette, sélectionnez Sensibilité et choisissez une étiquette.

