---
title: Différences entre les modèles personnalisés dans Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris
audience: admin
ms.topic: article
ms.service: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez les principales différences entre un modèle de compréhension de document et un modèle de traitement de formulaire.
ms.openlocfilehash: b17ab57cd7252c9a1cee7abb5a81359a965ca477
ms.sourcegitcommit: 078149c9645ce220911ccd6ce54f984a4c92ce53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67812093"
---
# <a name="differences-between-custom-models-in-microsoft-sharepoint-syntex"></a>Différences entre les modèles personnalisés dans Microsoft SharePoint Syntex 

La compréhension du contenu dans Microsoft SharePoint Syntex vous permet d’identifier et de classer les documents chargés dans les bibliothèques de documents SharePoint, puis d’extraire les informations pertinentes de chaque fichier. Par exemple, lorsque les fichiers sont téléchargés vers une bibliothèque de documents SharePoint, tous les fichiers identifiés comme *Bons de commande* sont classés comme tels, puis affichés dans une vue personnalisée de la bibliothèque de documents. De plus, vous pouvez extraire des informations spécifiques de chaque fichier (par exemple, le *Numéro de bon de commande* et le *Total*) et les afficher sous forme de colonne dans la vue de votre bibliothèque de documents. 

La compréhension de contenu vous permet de créer des *modèles* pour identifier et extraire les informations dont vous avez besoin. Les modèles peuvent vous aider à résoudre des problèmes commerciaux liés à la recherche, aux processus commerciaux, à la conformité et bien d’autres.

Vous pouvez utiliser deux types de modèles personnalisés :

- les [modèles de compréhension de document](document-understanding-overview.md)
- les [modèles de traitement de formulaire](form-processing-overview.md)

Bien que les deux modèles soient généralement utilisés dans le même but, les principales différences répertoriées ci-dessous affectent ceux que vous pouvez utiliser.

> [!NOTE]
> Pour plus d’informations sur le traitement des formulaires et les exemples de scénarios de compréhension des documents, consultez la rubrique [Prise en main de l’adoption de SharePoint Syntex](./adoption-getstarted.md).

## <a name="structured-versus-unstructured-and-semi-structured-content"></a>Contenu structuré, contenu non structuré ou contenu semi-structuré

Utilisez des modèles de compréhension de document pour identifier et extraire des données de documents non structurés, comme des lettres ou des contrats, dans lesquels les entités de texte que vous souhaitez extraire se trouvent dans des phrases ou des zones spécifiques du document. Par exemple, un document non structuré peut être une lettre de renouvellement de contrat, qui peut être rédigée de différentes manières. Toutefois, les informations existent de manière cohérente dans le corps de chaque document de renouvellement de contrat, comme la chaîne `Service start date of` de texte suivie d’une date réelle.

Utilisez des modèles de traitement de formulaire pour identifier les fichiers et extraire des données de documents structurés ou semi-structurés, tels que des formulaires ou des factures. Les modèles de traitement de formulaire sont formés pour comprendre la mise en page de votre formulaire à partir d’exemples de documents et apprendre à rechercher les données que vous devez extraire à partir d’emplacements similaires. En effet, les formulaires ont une mise en page plus structurée et les entités se trouvent à la même place (par exemple, un numéro de sécurité sociale sur un formulaire fiscal).

> [!NOTE]
> Vous devez avoir accès à un site de type centre de contenu pour créer un modèle de compréhension de document ou pour en appliquer un à une bibliothèque de documents SharePoint. 

## <a name="where-models-are-created"></a>Où les modèles sont créés

Les modèles de compréhension de document sont créés et gérés dans un site de type centre de contenu SharePoint. 

> [!NOTE]
> Si vous souhaitez en savoir plus sur les documents input, consultez l’article [Configuration requise et limitations du modèle de traitement de formulaire](/ai-builder/form-processing-model-requirements). 

Les modèles de traitement de formulaire sont créés dans Power Apps [AI Builder](/ai-builder/overview), mais la création commence directement à partir d’une bibliothèque de documents SharePoint. La création du modèle de traitement de formulaire d’une bibliothèque de documents doit être activée pour qu’un utilisateur puisse créer un modèle de traitement des formulaires pour celle-ci. Les administrateurs peuvent activer la création du modèle de traitement de formulaire dans le contenu comprenant les paramètres d’administration. Les modèles de traitement de formulaire utilisent des flux Power Automate pour traiter les fichiers lorsqu’ils sont chargés dans la bibliothèque de documents.

Lorsque vous créez un modèle de compréhension de document, vous créez un nouveau [type de contenu SharePoint](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978), qui est enregistré dans la galerie Types de contenu SharePoint. Vous pouvez également utiliser des types de contenu existants pour définir votre modèle si nécessaire.

Une fois qu’un type de contenu est créé et associé à un modèle, vous pouvez également le référencer à partir du panneau de propriétés **Type de contenu de site** .

:::image type="content" source="../media/content-understanding/site-content-type-panel.png" alt-text="Capture d’écran du panneau Type de contenu du site montrant le modèle compréhension de Document mis en évidence." lightbox="../media/content-understanding/site-content-type-panel.png":::

Les modèles de traitement de formulaire créent également de nouveaux [types de contenu SharePoint](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) et sont, eux aussi, stockés dans la galerie Types de contenu SharePoint.

## <a name="where-they-can-be-applied"></a>Où peuvent-ils être appliqués ?

Vous pouvez appliquer des modèles de compréhension de document aux bibliothèques de documents SharePoint auxquelles vous avez accès. Utilisez le centre de contenu pour créer un modèle de compréhension de document et appliquer celui-ci à différentes bibliothèques de documents. Le centre de contenu offre un contrôle plus central concernant l’utilisation des modèles de compréhension de document ainsi que leur application. Notez que ces informations doivent également être transmises à un centre de contenu.

Actuellement, les modèles de traitement de formulaire ne peuvent être appliqués qu’à la bibliothèque de documents SharePoint à partir de laquelle ils sont créés. Cela permet aux utilisateurs sous licence, ayant accès au site de créer un modèle de traitement de formulaire. Notez qu’un administrateur doit activer le traitement de formulaire sur une bibliothèque de documents SharePoint pour que les utilisateurs sous licence puissent l’utiliser.

## <a name="comparison-of-form-processing-and-document-understanding"></a>Comparaison du traitement des formulaires et de la compréhension des documents

Utilisez le tableau suivant pour comprendre quand utiliser le traitement des formulaires et quand utiliser la compréhension des documents.

| Fonctionnalité | Traitement des formulaires | Compréhension de document |
| ------- | ------- | ------- |
| Type de modèle : quand utiliser chaque modèle | Formats de fichiers structurés et semi-structurés, par exemple les fichiers PDF pour le contenu des formulaires, tels que les factures ou les bons de commande, où la disposition et la mise en forme sont similaires.  | Formats de fichiers non structurés ou semi-structurés, par exemple, documents Office où il existe des différences dans la disposition, mais encore des informations similaires à extraire. |
| Création de modèles | Modèle créé dans le Générateur d’intelligence artificielle avec un accès transparent à partir d’une bibliothèque de documents SharePoint.| Modèle créé dans SharePoint dans un nouveau site, le centre de contenu. |
| Type de classification| Le classificateur réglable est utilisé pour donner des indices au système sur les données à extraire.| Classifieur pouvant être formé avec des extracteurs facultatifs utilisant l’apprentissage automatique pour attribuer l’emplacement du document aux données à extraire.|
| Emplacements | Formé pour une seule bibliothèque de documents.| Peut être appliqué à plusieurs bibliothèques.|
| Types de fichiers pris en charge| Entraînez-vous au format PDF, JPG, PNG, un total de 50 Mo et 500 pages.| Entraînez-vous sur 5 à 10 fichiers PDF, Office ou courrier électronique, avec des exemples négatifs.<br>Les fichiers Office sont tronqués à 64 000 caractères. Les fichiers numérisés par OCR sont limités à 20 pages. Consultez [les types de fichiers pris en charge](document-understanding-overview.md#supported-file-types).|
| Intégration aux métadonnées gérées | Non | Oui, par l’extracteur de l’entité de formation qui fait référence à un champ de métadonnées gérées configurée.|
| Intégration des fonctionnalités de conformité à Protection des données Microsoft Purview | Définissez les étiquettes de rétention publiées.<br>Définissez les étiquettes de confidentialité à venir. | Définissez les étiquettes de rétention publiées.<br>Définissez les étiquettes de confidentialité publiées. |
| Régions pris en charge| Le traitement des formulaires s’appuie sur la plateforme Power. Pour plus d’informations sur la disponibilité globale de la plateforme Power et du Générateur d’intelligence artificielle, consultez [Disponibilité de la plateforme Power](https://dynamics.microsoft.com/geographic-availability/). | Disponible dans toutes les régions.|
| Coût transactionnel | Utilise des crédits de générateur d’intelligence artificielle.<br>3,5 Ko de crédits sont inclus pour chaque licence SharePoint Syntex par mois.<br>1M de crédits permet de traiter un fichier de 2 000 pages.<br>| Non applicable |
| Capacité | Utilise l’environnement de plateforme Power par défaut (environnements personnalisés pris en charge par la base de données de dataverse). | Ne comprend pas de restrictions de capacité.|
| Langues prises en charge| Prise en charge linguistique pour plus de [73 langues](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support). | Les modèles fonctionnent sur toutes les langues de l’alphabet latin. En plus de l’anglais : l’allemand, le suédois, le Français, l’espagnol, l’italien et le portugais.|


## <a name="see-also"></a>Voir aussi

[Formation : Améliorer les performances de votre entreprise avec AI Builder](/training/paths/improve-business-performance-ai-builder/?source=learn)

[Vue d’ensemble de la compréhension de document](document-understanding-overview.md)

[Vue d’ensemble du traitement des formulaires](form-processing-overview.md)

[Introduction à SharePoint Syntex](index.md)
