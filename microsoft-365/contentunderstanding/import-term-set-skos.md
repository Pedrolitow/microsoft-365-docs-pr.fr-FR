---
title: Importer un ensemble de termes avec un format SKOS
description: Découvrez comment importer un ensemble de termes avec un format SKOS
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.service: ''
ms.collection: enabler-strategic
search.appverid: ''
localization_priority: Priority
ms.openlocfilehash: 8a1b61088d0a1594bf1a71542158ade389cce2ab
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59202283"
---
# <a name="import-a-term-set-using-a-skos-based-format"></a>Importer un ensemble de termes avec un format SKOS

Importer un ensemble de termes avec un format basé sur SKOS. Si vous souhaitez en savoir plus sur le format, veuillez consulter la rubrique [Référence de format SKOS pour la taxonomie SharePoint](skos-format-reference.md). Cette fonctionnalité nécessite une licence [SharePoint Syntex](index.md).

Nous vous recommandons d’inclure moins de 20 000 termes dans vos fichiers d’importation. Les fichiers plus volumineux peuvent augmenter le temps de validation et d’importation.

1. Dans le Centre d’administration SharePoint, développez **Services de contenu**, puis cliquez sur **Magasin de termes**.

2. Sélectionnez le groupe de termes où vous souhaitez importer l’ensemble de termes.

3. Dans la barre de commandes, cliquez sur **Importer l’ensemble de termes**.

4. Si vous voulez télécharger un fichier échantillon à utiliser en tant que modèle, cliquez sur **sample-metadata.ttl** pour obtenir un exemple de fichier qui utilise le format SKOS.

5. Créez le fichier d’importation contenant les ensembles de termes et les termes à importer.

6. Sous **Format de fichier**, sélectionnez **SKOS (*.ttl)**.

7. Cliquez sur **Parcourir**, puis ajoutez votre fichier d’importation.

8. Cliquez sur **Importer**. Ne fermez le panneau qu’une fois l’importation terminée.

Une fois le fichier correctement importé, un message de réussite s’affiche, puis le magasin de termes est actualisé. Vous pouvez alors accéder aux nouveaux ensembles de termes récemment créés.

## <a name="see-also"></a>Voir aussi

[Présentation des métadonnées gérées](/sharepoint/managed-metadata)

[Présentation de la compréhension de document](document-understanding-overview.md)

[Importer des ensembles de termes (niveau du site)](https://support.microsoft.com/office/168fbc86-7fce-4288-9a1f-b83fc3921c18)
