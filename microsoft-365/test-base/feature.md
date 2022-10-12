---
title: Validation de la mise à jour des fonctionnalités
description: Détails sur le chargement de votre application pour la validation des mises à jour de fonctionnalités
search.appverid: MET150
author: mansipatel-usl
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: test-base
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: tinachen
f1.keywords: NOCSH
ms.openlocfilehash: bd681f6dceec9182d3fbe80e6bb3beeae510c65a
ms.sourcegitcommit: 893add1e40c3e26e5624663eaf272d12a72d0141
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68540002"
---
# <a name="windows-feature-update-validation"></a>Validation de la mise à jour des fonctionnalités Windows

Avez-vous besoin d’informations sur la façon dont vos applications fonctionneront avec les dernières fonctionnalités de Windows , avant qu’elles ne soient disponibles sur le marché et sans que vous mainteniez un environnement ? 

Voulez-vous exécuter vos tests de validation sur les builds du programme Windows Insider dans notre environnement Azure ? 

**La validation des mises à jour** de fonctionnalités sur la base de test pour Microsoft 365 peut vous aider à atteindre tous ces objectifs et bien plus encore ! 

Consultez le plan détaillé ci-dessous pour savoir comment accéder à cette nouvelle fonctionnalité dans la base de test pour le service Microsoft 365. 

Pour commencer à valider la mise à jour des fonctionnalités dans La base de test pour Microsoft 365, chargez vos applications (et les fichiers associés) via le portail d’intégration en libre-service. 

Vous trouverez ci-dessous les étapes à suivre lorsque vous remplissez la **matrice de test** : 

Pour configurer les mises à jour des fonctionnalités, vous devez spécifier le produit cible et son canal d’aperçu dans la liste déroulante « Insider Channel ». 

![Type de système d’exploitation de validation de mise à jour des fonctionnalités.](Media/windowsfeatureupdatevalidation01-featureupdate.png)

Votre sélection inscrit votre application pour les tests automatiques sur les dernières mises à jour de fonctionnalités de votre canal de produit sélectionné et toutes les nouvelles mises à jour futures dans les dernières versions Windows Insider Preview de votre sélection. 

Vous pouvez également définir votre système d’exploitation actuel dans « Base de référence du système d’exploitation pour Insight ». Nous vous fournirons plus d’insights de test en effectuant une analyse de régression de votre environnement de système d’exploitation en l’état et du système d’exploitation cible le plus récent. 

![Validation de la mise à jour des fonctionnalités. Choix du canal bêta Insider.](Media/windowsfeatureupdatevalidation02-osbaseline.png) 

Pour en savoir plus sur les builds Windows Insider Preview, [reportez-vous à Flight Hub - Programme Windows Insider | Microsoft Docs](/../../../../MicrosoftDocs/windows-insider/tree/public/wip/flight-hub/index.md).


## <a name="next-steps"></a>Prochaines étapes

Passez à l’article suivant pour commencer à comprendre l’analyse de régression de la mémoire.
> [!div class="nextstepaction"]
> [Étape suivante](memory.md)

<!---
Add button for next page
-->
