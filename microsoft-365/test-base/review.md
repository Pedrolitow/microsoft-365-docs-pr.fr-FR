---
title: Révision
description: Passer en revue la section après l’intégration.
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 3bb6ef605d360e259ef9fa91ed51da35506a2942
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60208816"
---
# <a name="step-6-review-your-selections-to-create-your-package"></a>Étape 6 : examinez vos sélections pour créer votre package.

1. Sous cet onglet, le service affiche les détails de vos tests et exécute une vérification rapide de l’intégralité.

    Un **message de validation** réussi ou de **validation** a échoué indique si vous pouvez passer aux étapes suivantes ou non.

2. Examinez les détails de votre test et, si vous êtes satisfait, cliquez sur le **bouton** Créer.

    :::image type="content" alt-text="Afficher la validation." source="Media/validation.png" lightbox="Media/validation.png":::

3. Cela intégrera votre package à l’environnement de base de test. Si votre package est correctement créé, un test automatisé qui vérifie si votre package peut être correctement exécuté sur Azure sera déclenché.

    ![Résultat réussi.](Media/successful.png)

    > [!NOTE]
    > Vous recevez une notification du portail Azure pour vous informer de la réussite ou de l’échec de la vérification du package.
    >
    > Notez que le processus peut prendre jusqu’à 24 heures. Il est donc probable que votre page web arrive à terme si vous n’y êtes pas actif et, par conséquent, la notification ne vous informe pas de la fin de cette exécution à la demande.

    - Cela se produit, vous pouvez afficher l’état de votre package sous l’onglet Gérer **les packages.**

      :::image type="content" alt-text="Image de gestion des packages." source="Media/managepackages.png" lightbox="Media/managepackages.png":::

    - Pour des tests réussis, leurs résultats sont  visibles via les pages Résumé des **tests,** Mises à jour de sécurité Résultats et Mises à jour des fonctionnalités à **intervalles réguliers,** souvent en commençant quelques jours après votre chargement.
  
    - En cas d’échec des tests, vous devez télécharger un nouveau package. 

      Vous pouvez télécharger les **journaux** de  test pour une analyse plus approfondie à partir des pages de résultats des mises à jour de sécurité et des mises à jour des **fonctionnalités.**

    - Si vous faites face à des échecs de test répétés, contactez testbasepreview@microsoft.com avec les détails de votre erreur.

## <a name="next-steps"></a>Étapes suivantes

Découvrez nos recommandations en matière de contenu via le lien ci-dessous.

> [!div class="nextstepaction"]
> [Étape suivante](contentguideline.md)
