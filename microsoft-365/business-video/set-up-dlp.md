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
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment gérer la configuration des stratégies de protection contre la perte de données.
ms.openlocfilehash: 93c06af0203a5eb590d22d86e597d7485d7af238
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49702245"
---
# <a name="prevent-data-loss-with-dlp"></a>Prévention des pertes de données avec DLP

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3TGvL?autoplay=false]

Les stratégies de protection contre la perte de données permettent d’identifier et de protéger les informations sensibles de votre entreprise, telles que les numéros de sécurité sociale ou les enregistrements médicaux. 

## <a name="try-it"></a>Essayez !

1. Pour commencer, accédez au centre d' [administration](https://admin.microsoft.com), puis sélectionnez **configuration**.
1. Faites défiler vers le bas pour **configurer la protection contre la perte de données**, puis sélectionnez **Afficher**, puis **gérer**.
1. Pour modifier une stratégie, sélectionnez-la, choisissez **modifier la stratégie**, puis sélectionnez les éléments à modifier. Par exemple, sélectionnez **emplacements** pour modifier ce qui est analysé.
1. Pour activer l’analyse de contenu dans Microsoft Teams, activez le bouton bascule sur la position **activé** , puis sélectionnez **Enregistrer**.
1. Pour modifier les paramètres de stratégie, sélectionnez **modifier**.
1. Vous devez définir des règles distinctes qui s’appliquent aux petites et grandes quantités de contenu sensible détectées. Développez votre règle de volume faible. Choisissez **modifier la règle**.
1. Vérifiez vos paramètres et ajustez-les si nécessaire. Par exemple, vous pouvez **personnaliser le texte du message électronique** et **personnaliser le texte de l’info-bulle de la stratégie**. Sélectionnez **Enregistrer**.
1. Répétez l’opération pour la règle de volume élevée. Sélectionnez **Enregistrer**, puis **Fermer**.
1. Pour créer une stratégie, sélectionnez **créer une stratégie**.
1. Vous pouvez créer une stratégie personnalisée ou commencer avec un modèle. Par exemple, pour créer une stratégie HIPAA, sélectionnez le modèle **Medical and Health** , puis sélectionnez **U.S. Health Insurance Act (HIPAA)**. Sélectionnez **Suivant**.
1. Entrez un nom et une description pour votre stratégie. Sélectionnez **Suivant**.
1. Choisissez les emplacements à analyser. Sélectionnez **Suivant**.
1. Choisissez le type de contenu que vous souhaitez protéger. Sélectionnez **Suivant**.
1. Choisissez ce qui doit se produire en cas de détection d’informations sensibles. Sélectionnez **Suivant**.
1. Personnalisez vos autorisations d’accès et de remplacement. Sélectionnez **Suivant**.
1. Choisissez le moment auquel vous souhaitez que la stratégie prenne effet. Sélectionnez **Suivant**.
1. Vérifiez vos paramètres, puis sélectionnez **créer**. Une fois que votre stratégie prend effet, le courrier électronique qui contient les informations sensibles décrites est bloqué et l’expéditeur qui a tenté d’envoyer ces informations verra apparaître un message d’avertissement.