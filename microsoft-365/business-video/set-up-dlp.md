---
title: Éviter les pertes de données
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
- okr_smb
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment gérer les stratégies de protection contre la perte de données.
ms.openlocfilehash: e963cf85fee887b6e91c6e54b00aaa9e5174e3b6
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49927957"
---
# <a name="prevent-data-loss-with-dlp"></a>Empêcher la perte de données avec DLP

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3TGvL?autoplay=false]

Les stratégies de protection contre la perte de données permettent d’identifier et de protéger les informations sensibles de votre entreprise, telles que les numéros de sécurité sociale ou les dossiers médicaux. 

## <a name="try-it"></a>Essayez !

1. To get started, go to the [admin center](https://admin.microsoft.com), and select **Setup**.
1. Faites défiler vers le bas **pour configurer la** protection contre la perte de données, puis **sélectionnez Afficher,** puis **Gérer**.
1. Pour modifier une stratégie, sélectionnez-la, sélectionnez **Modifier la stratégie,** puis ce qu’il faut modifier. Par exemple, sélectionnez **Emplacements** pour modifier ce qui est analysé.
1. Pour activer l’analyse du contenu dans Microsoft Teams, activez le bouton bascule en position **Activé,** puis sélectionnez **Enregistrer.**
1. Pour modifier les paramètres de stratégie, sélectionnez **Modifier.**
1. Vous devez définir des règles distinctes qui s’appliquent aux petites et grandes quantités de contenu sensible détecté. Développez votre règle de faible volume. Choose **Edit rule**.
1. Examinez vos paramètres et ajustez-les selon vos besoins. Par exemple, vous pouvez choisir de personnaliser **le texte** du message électronique et le texte du conseil **de stratégie.** Sélectionnez **Enregistrer**.
1. Répétez cette répétition pour la règle de volume élevé. Sélectionnez **Enregistrer,** puis **Fermez.**
1. Pour créer une stratégie, **sélectionnez Créer une stratégie.**
1. Vous pouvez créer une stratégie personnalisée ou commencer par un modèle. Par exemple, pour créer une stratégie  HIPAA, sélectionnez le modèle médical et de santé, puis sélectionnez loi américaine d’assurance maladie **(HIPAA).** Sélectionnez **Suivant**.
1. Entrez un nom et une description pour votre stratégie. Sélectionnez **Suivant**.
1. Choisissez les emplacements à analyser. Sélectionnez **Suivant**.
1. Choisissez le type de contenu que vous souhaitez protéger. Sélectionnez **Suivant**.
1. Choisissez ce que vous souhaitez faire si des informations sensibles sont détectées. Sélectionnez **Suivant**.
1. Personnalisez vos autorisations d’accès et de remplacement. Sélectionnez **Suivant**.
1. Choisissez quand vous souhaitez que la stratégie prenne effet. Sélectionnez **Suivant**.
1. Examinez vos paramètres, puis sélectionnez **Créer.** Une fois votre stratégie entrée en vigueur, le courrier électronique qui contient les informations sensibles décrites est bloqué et l’expéditeur qui a tenté d’envoyer ces informations voit un message d’avertissement.