---
title: Créer des étiquettes de sensibilité
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
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
description: Découvrez comment créer et gérer des étiquettes de confidentialité.
ms.openlocfilehash: ff3f7eb5ffddf797e254fac0ed8fc87d96940455
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49702396"
---
# <a name="protect-documents-with-sensitivity-labels"></a>Protection des documents avec des étiquettes de confidentialité

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3VRGT?autoplay=false]

Les étiquettes de sensibilité vous permettent de classer et de protéger le contenu sensible à votre entreprise.

## <a name="try-it"></a>Essayez !

1. Dans le [Centre d’administration](https://admin.microsoft.com), sélectionnez le centre d’administration de la **conformité** .
1. Sélectionnez **classification**, puis **étiquettes de sensibilité**.
1. Sélectionnez **créer une étiquette**, puis, lorsque l’avertissement s’affiche, sélectionnez **Oui**.
1. Entrez un **nom d’étiquette**, une **info-bulle** et une **Description**. Sélectionnez **Suivant**.
1. Activez le **chiffrement**. Choisissez le moment auquel vous souhaitez attribuer des autorisations, selon que vous souhaitez que les utilisateurs accèdent au contenu et que vous souhaitez autoriser l’accès hors connexion.
1. **Sélectionnez attribuer des autorisations**, puis **Ajoutez ces adresses de messagerie ou domaines**.
1. Entrez une adresse de messagerie ou un nom de domaine (par exemple, Contoso.org).  Sélectionnez **Ajouter**, puis répétez l’opération pour chaque adresse de messagerie ou domaine que vous souhaitez ajouter.
1. Sélectionnez **choisir les autorisations à partir d’un préréglage ou personnalisé**.
1. Utilisez la liste déroulante pour sélectionner des autorisations prédéfinies, telles que le **réviseur** ou la **visionneuse**, ou sélectionnez autorisations **personnalisées** . Si vous avez choisi **personnaliser**, sélectionnez les autorisations dans la liste. Sélectionnez **Enregistrer**, **Enregistrer**, puis **suivant**.
1. Activez le **marquage de contenu**, puis choisissez les marques à utiliser.
1. Pour chaque marque que vous choisissez, sélectionnez **personnaliser le texte**. Entrez le texte que vous souhaitez voir apparaître dans le document, puis définissez les options de police et de mise en page. Sélectionnez **Enregistrer**, puis répétez l’opération pour toutes les marques supplémentaires. Sélectionnez **Suivant**.
1. Si vous le souhaitez, activez la **protection contre la perte de données de point de terminaison**. Sélectionnez **Suivant**.
1. Si vous le souhaitez, activez l' **étiquetage automatique**. Ajoutez une condition. Par exemple, sous **détecter le contenu qui contient**, sélectionnez **Ajouter une condition**. Entrez la condition ; par exemple, ajoutez une condition de détection de passeport, de sécurité sociale ou d’autres informations sensibles, l’étiquette est ajoutée. Sélectionnez **Suivant**.
1. Vérifiez vos paramètres, puis sélectionnez **créer**. Votre étiquette a été créée. Répétez cette procédure pour les étiquettes supplémentaires de votre choix.
1. Par défaut, les étiquettes apparaissent dans les applications Office dans l’ordre suivant : **confidentiel**, **interne** et **public**. Pour modifier l’ordre, pour chaque étiquette, sélectionnez **autres actions** (les points de suspension), puis déplacez l’étiquette vers le haut ou vers le bas. En règle générale, les autorisations sont répertoriées du niveau d’autorisation le plus bas au plus élevé.
1. Pour ajouter une sous-étiquette à une étiquette, sélectionnez **actions supplémentaires**, puis **Ajouter un sous-niveau**.
1. Lorsque vous avez terminé, choisissez **publier les étiquettes**, **sélectionnez les étiquettes à publier**, puis **Ajouter**. Sélectionnez les étiquettes à publier, puis sélectionnez **Ajouter**, **Terminer**, puis **suivant**.
1. Par défaut, la nouvelle stratégie d’étiquette est appliquée à tout le monde. Si vous souhaitez limiter l’application de la stratégie, sélectionnez **choisir les utilisateurs ou les groupes**, puis **Ajouter**. Sélectionnez la personne à laquelle vous souhaitez appliquer la stratégie, puis sélectionnez **Ajouter**, **Terminer**, puis **suivant**.
1. Si vous souhaitez une étiquette par défaut pour les documents et le courrier électronique, sélectionnez l’étiquette de votre choix dans la liste déroulante. Passez en revue les paramètres restants, ajustez-les selon vos besoins, puis cliquez sur **suivant**.
1. Entrez un **nom** et une **Description** pour votre stratégie. Sélectionnez **Suivant**.
1. Vérifiez vos paramètres, puis sélectionnez **publier**.

Pour que vos étiquettes fonctionnent, chaque utilisateur doit télécharger le client d’étiquetage unifié Azure information protection. Recherchez **AzinfoProtection_UL.exe** sur le Web, puis téléchargez-le à partir du centre de téléchargement Microsoft et exécutez-le sur les ordinateurs de vos utilisateurs.

La prochaine fois que vous ouvrirez une application Office comme Word, vous verrez les étiquettes de confidentialité qui ont été créées. Pour modifier ou appliquer une étiquette, sélectionnez sensibilité, puis choisissez une étiquette.

