---
title: Importer un ensemble de termes à l’aide d’un format basé sur SKOS
description: Découvrez comment importer un ensemble de termes à l’aide d’un format basé sur SKOS
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.service: ''
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: aaed88463f690853672780b48a8ee3857a956847
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48295892"
---
# <a name="import-a-term-set-using-a-skos-based-format"></a>Importer un ensemble de termes à l’aide d’un format basé sur SKOS

Vous pouvez importer un ensemble de termes à l’aide d’un format SKOS. Pour plus d’informations sur le format, reportez-vous à la rubrique [référence de format SKOS taxonomie SharePoint](skos-format-reference.md).

Nous vous recommandons de conserver vos fichiers d’importation à moins de 20 000 termes. Les fichiers plus volumineux peuvent augmenter le temps de validation et d’importation.

1. Dans le centre d’administration SharePoint, développez **services de contenu**, puis cliquez sur **magasin de termes**.

2. Sélectionnez le groupe de termes dans lequel vous souhaitez importer l’ensemble de termes.

3. Dans la barre de commandes, cliquez sur **importer l’ensemble de termes**.
 
4.  Si vous souhaitez télécharger un exemple de fichier à utiliser en tant que modèle, cliquez sur **Sample-Metadata. TTL** pour obtenir un exemple de fichier qui utilise le format SKOS.
 
5.  Créez le fichier d’importation contenant les ensembles de termes & termes que vous souhaitez importer.

6.  Sous **format de fichier**, sélectionnez **SKOS (*. TTL)**.

7.  Cliquez sur **Parcourir** , puis accédez à votre fichier d’importation et ajoutez-le.

8.  Cliquez sur **Importer**. Ne fermez pas le panneau tant que l’importation n’est pas terminée.

Lors de l’importation réussie du fichier, un message de réussite s’affiche et le magasin de termes est actualisé et vous pouvez accéder aux nouveaux ensembles de termes.

## <a name="see-also"></a>Voir aussi

[Présentation des métadonnées gérées](https://docs.microsoft.com/sharepoint/managed-metadata)

[Présentation de l’explication des documents](document-understanding-overview.md)

[Importer des ensembles de termes (niveau site)](https://support.microsoft.com/office/168fbc86-7fce-4288-9a1f-b83fc3921c18)