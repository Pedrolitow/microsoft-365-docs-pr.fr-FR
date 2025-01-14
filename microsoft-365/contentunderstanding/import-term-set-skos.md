---
title: Importer un ensemble de termes avec un format SKOS
description: Découvrez comment importer un ensemble de termes à l’aide d’un format SKOS.
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.service: microsoft-syntex
ms.topic: article
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: admindeeplinkSPO
search.appverid: ''
ms.localizationpriority: high
ms.openlocfilehash: 389d211a3f094fa8e6956a2c7882d6efef5aa795
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68659980"
---
# <a name="import-a-term-set-using-a-skos-based-format"></a>Importer un ensemble de termes avec un format SKOS

Importer un ensemble de termes avec un format basé sur SKOS. Si vous souhaitez en savoir plus sur le format, veuillez consulter la rubrique [Référence de format SKOS pour la taxonomie SharePoint](skos-format-reference.md). Cette fonctionnalité nécessite une [licence Microsoft Syntex](syntex-licensing.md).

Nous vous recommandons d’inclure moins de 20 000 termes dans vos fichiers d’importation. Les fichiers plus volumineux peuvent augmenter le temps de validation et d’importation.

1. Dans le Centre d’administration SharePoint, développez **Services de contenu**, puis cliquez sur <a href="https://go.microsoft.com/fwlink/?linkid=2185073" target="_blank">**Magasin de termes**</a>.

2. Sélectionnez le groupe de termes où vous souhaitez importer l’ensemble de termes.

3. Dans la barre de commandes, cliquez sur **Importer l’ensemble de termes**.

4. Si vous voulez télécharger un fichier échantillon à utiliser en tant que modèle, cliquez sur **sample-metadata.ttl** pour obtenir un exemple de fichier qui utilise le format SKOS.

5. Créez le fichier d’importation contenant les ensembles de termes et les termes à importer.

6. Sous **Format de fichier**, sélectionnez **SKOS (*.ttl)**.

7. Cliquez sur **Parcourir**, puis ajoutez votre fichier d’importation.

8. Click **Import**. Do not close the panel until the import completes.

Une fois le fichier correctement importé, un message de réussite s’affiche, puis le magasin de termes est actualisé. Vous pouvez alors accéder aux nouveaux ensembles de termes récemment créés.

## <a name="see-also"></a>Voir aussi

[Présentation des métadonnées gérées](/sharepoint/managed-metadata)

[Vue d’ensemble du traitement des documents non structurés](document-understanding-overview.md)

[Importer des ensembles de termes (niveau du site)](https://support.microsoft.com/office/168fbc86-7fce-4288-9a1f-b83fc3921c18)
