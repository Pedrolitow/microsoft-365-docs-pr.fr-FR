---
title: Exigences et limitations pour les modèles dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez les limitations de fichiers, les types de fichiers, les langages pris en charge et d’autres exigences pour les modèles dans Microsoft Syntex.
ms.openlocfilehash: 967a47f96c2345772fb8a7eac12db6e95d5128c8
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68664093"
---
# <a name="requirements-and-limitations-for-models-in-microsoft-syntex"></a>Exigences et limitations pour les modèles dans Microsoft Syntex

<sup>**S’applique à :**  &ensp; &#10003; Tous les modèles &ensp; | &ensp; personnalisés &#10003; Tous les modèles prédéfinis</sup>

Microsoft Syntex vous permet de créer [des modèles personnalisés et des modèles prédéfinis](model-types-overview.md). Selon le type de modèle que vous choisissez, il peut y avoir différentes exigences, telles que le type et la taille de fichier, les langues qui doivent être prises en charge, les considérations géographiques et d’autres facteurs qui vous aideront à choisir le type de modèle à utiliser.

Modèles personnalisés :

- [Traitement de documents non structurés](#unstructured-document-processing)
- [Traitement de documents en forme libre](#freeform-document-processing)
- [Traitement de document structuré](#structured-document-processing)
 
Modèles prédéfinis :

- [Traitement des factures](#invoice-processing)
- [Traitement des reçus](#receipt-processing)

## <a name="custom-models"></a>Modèles personnalisés

### <a name="unstructured-document-processing"></a>Traitement de documents non structurés

| Icône          | Description   |
| ------------- | ------------- |
| ![Symbole de fichiers.](/office/media/icons/files-blue.png)  | **Types de fichiers pris en charge** <br>Ce modèle prend en charge les types de fichiers suivants : .csv, .doc, .docx, .eml, .heic, .heif, .htm, .html, .jpeg, .jpg, .md, .msg, .pdf, .png, .ppt, .pptx, .rtf, .tif, .tiff, .txt, .xls et .xlsx. |
| ![Symbole de conversation.](/office/media/icons/chat-room-conversation-blue.png)  | **Langues prises en charge** <br>Ce modèle prend en charge toutes les langues latines, notamment l’anglais, l’Français, l’allemand, l’italien et l’espagnol. |
| ![Symbole de paragraphe.](/office/media/icons/paragraph-writing-blue.png)  | **Considérations relatives à la reconnaissance optique de caractères** <br>Ce modèle utilise la technologie de reconnaissance optique de caractères (OCR) pour analyser les fichiers .pdf, les fichiers image et les fichiers .tiff. Le traitement OCR fonctionne mieux sur des documents respectant les conditions requises suivantes : <br> - Format de fichier .jpg, .png ou .pdf (texte ou analysé). Les fichiers .pdf incorporés dans le texte sont préférables, car il n’y aura pas d’erreurs dans l’extraction et l’emplacement des caractères. <br> - Si vos fichiers .pdf sont verrouillés par mot de passe, vous devez supprimer le verrou avant de les envoyer. <br> - La taille de fichier combinée des documents utilisés pour l’entraînement par collection ne doit pas dépasser 50 Mo, et les documents PDF ne doivent pas avoir plus de 500 pages. <br> - Pour les images, les dimensions doivent être comprises entre 50 x 50 et 10 000 x 10 000 pixels. Les images très larges ou ayant des dimensions spéciales (par exemple, des plans au sol) peuvent être tronquées dans le processus OCR et perdre en précision. <br> - Pour les fichiers .pdf, les dimensions doivent être au maximum de 17 x 17 pouces, correspondant aux formats de papier Legal ou A3 et plus petites. <br> - S’ils sont numérisés à partir de documents papier, les numérisations doivent être des images de haute qualité. <br> - Doit utiliser l’alphabet latin (caractères anglais). <br> Notez les différences suivantes concernant les fichiers texte microsoft Office et les fichiers analysés par OCR (.pdf, image ou .tiff) : <br> - Fichiers Office : tronqués à 64 000 caractères (lors de l’entraînement et lors de l’exécution sur les fichiers d’une bibliothèque de documents). <br> - Fichiers analysés par OCR : il existe une limite de 500 pages. Seuls les types de fichiers PDF et image sont traités par OCR. |
| ![Symbole de globe.](/office/media/icons/globe-internet.png)  | **Microsoft 365 Multigéographie** <br>Lorsque vous configurez Syntex dans un environnement [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo) , vous pouvez uniquement le configurer pour utiliser le type de modèle à l’emplacement central. Si vous souhaitez utiliser ce type de modèle dans un emplacement satellite, contactez le support Microsoft. |
| ![Symbole d’objets.](/office/media/icons/objects-blue.png)  | **Bibliothèques multimodèles** <br>Si plusieurs modèles entraînés sont appliqués à la même bibliothèque, le fichier est classé à l’aide du modèle qui a le score de confiance moyen le plus élevé. Les entités extraites proviennent uniquement du modèle appliqué. |

### <a name="freeform-document-processing"></a>Traitement de documents en forme libre

| Icône          | Description   |
| ------------- | ------------- |
| ![Symbole de fichiers.](/office/media/icons/files-blue.png)  | **Types de fichiers pris en charge** <br>Ce modèle prend en charge les types de fichiers suivants : consultez [Exigences relatives aux types de fichiers](/ai-builder/form-processing-model-requirements#requirements). |
| ![Symbole de conversation.](/office/media/icons/chat-room-conversation-blue.png)  | **Langues prises en charge** <br>Ce modèle prend en charge la langue suivante : anglais. |
| ![Symbole de paragraphe.](/office/media/icons/paragraph-writing-blue.png) | **Considérations relatives à la reconnaissance optique de caractères** <br>Ce modèle utilise la technologie de reconnaissance optique de caractères (OCR) pour analyser les fichiers .pdf, les fichiers image et les fichiers .tiff. Le traitement OCR fonctionne mieux sur les documents qui répondent à [ces exigences](/ai-builder/form-processing-model-requirements#requirements). |
| ![Symbole de bande passante/efficacité.](/office/media/icons/bandwidth-efficiency-blue.png)  | **Conseils d’optimisation** <br>Si votre modèle ne fonctionne pas comme vous le souhaitez, essayez [ces étapes pour améliorer les performances de votre modèle](/ai-builder/improve-form-processing-performance). |
| ![Symbole de globe.](/office/media/icons/globe-internet.png)  | **Microsoft 365 Multigéographie** <br>Lorsque vous configurez Syntex dans un environnement [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo) , vous pouvez uniquement le configurer pour utiliser le type de modèle à l’emplacement central. Si vous souhaitez utiliser ce type de modèle dans un emplacement satellite, contactez le support Microsoft. |
| ![Symbole de blocs.](/office/media/icons/blocks-blue.png)  | **Environnements Power Platform personnalisés** <br>Si vous utilisez un environnement personnalisé (plutôt que l’environnement par défaut) pour le traitement de Power Platform, il existe des exigences de configuration supplémentaires. Pour plus d’informations, consultez [Environnements Power Platform personnalisés](/microsoft-365/contentunderstanding/set-up-content-understanding#custom-power-platform-environments). |
| ![Symbole d’objets.](/office/media/icons/objects-blue.png)  | **Bibliothèques multimodèles** <br>Si plusieurs modèles entraînés sont appliqués à la même bibliothèque, le fichier est classé à l’aide du modèle qui a le score de confiance moyen le plus élevé. Les entités extraites proviennent uniquement du modèle appliqué. Vous ne pouvez avoir qu’une seule forme libre ou un modèle structuré par bibliothèque. |

### <a name="structured-document-processing"></a>Traitement de document structuré

| Icône          | Description   |
| ------------- | ------------- |
| ![Symbole de fichiers.](/office/media/icons/files-blue.png)  | **Types de fichiers pris en charge** <br>Ce modèle prend en charge les types de fichiers suivants : consultez [Exigences relatives aux types de fichiers](/ai-builder/form-processing-model-requirements#requirements). |
| ![Symbole de conversation.](/office/media/icons/chat-room-conversation-blue.png)  | **Langues prises en charge** <br>Ce modèle prend en charge 73 langues : consultez [langues prises en charge](/ai-builder/form-processing-model-requirements#languages-supported). |
| ![Symbole de paragraphe.](/office/media/icons/paragraph-writing-blue.png) | **Considérations relatives à la reconnaissance optique de caractères** <br>Ce modèle utilise la technologie de reconnaissance optique de caractères (OCR) pour analyser les fichiers .pdf, les fichiers image et les fichiers .tiff. Le traitement OCR fonctionne mieux sur les documents qui répondent à [ces exigences](/ai-builder/form-processing-model-requirements#requirements). |
| ![Symbole de bande passante/efficacité.](/office/media/icons/bandwidth-efficiency-blue.png)  | **Conseils d’optimisation** <br>Si votre modèle ne fonctionne pas comme vous le souhaitez, essayez [ces étapes pour améliorer les performances de votre modèle](/ai-builder/improve-form-processing-performance). |
| ![Symbole de globe.](/office/media/icons/globe-internet.png)  | **Microsoft 365 Multigéographie** <br>Lorsque vous configurez Syntex dans un environnement [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo) , vous pouvez uniquement le configurer pour utiliser le type de modèle à l’emplacement central. Si vous souhaitez utiliser ce type de modèle dans un emplacement satellite, contactez le support Microsoft. |
| ![Symbole de blocs.](/office/media/icons/blocks-blue.png)  | **Environnements Power Platform personnalisés** <br>Si vous utilisez un environnement personnalisé (plutôt que l’environnement par défaut) pour le traitement de Power Platform, il existe des exigences de configuration supplémentaires. Pour plus d’informations, consultez [Environnements Power Platform personnalisés](/microsoft-365/contentunderstanding/set-up-content-understanding#custom-power-platform-environments). |
| ![Symbole d’objets.](/office/media/icons/objects-blue.png)  | **Bibliothèques multimodèles** <br>Si plusieurs modèles entraînés sont appliqués à la même bibliothèque, le fichier est classé à l’aide du modèle qui a le score de confiance moyen le plus élevé. Les entités extraites proviennent uniquement du modèle appliqué. Vous ne pouvez avoir qu’une seule forme libre ou un modèle structuré par bibliothèque. |

## <a name="prebuilt-models"></a>Modèles préconçus

### <a name="invoice-processing"></a>Traitement des factures

| Icône          | Description   |
| ------------- | ------------- |
| ![Symbole de fichiers.](/office/media/icons/files-blue.png)  | **Types de fichiers pris en charge** <br>Ce modèle prend en charge les types de fichiers suivants : .bmp, .jpeg, .pdf, .png et .tiff. |
| ![Symbole de conversation.](/office/media/icons/chat-room-conversation-blue.png)  | **Langues prises en charge** <br>Ce modèle prend uniquement en charge les factures en anglais du États-Unis. |
| ![Symbole de paragraphe.](/office/media/icons/paragraph-writing-blue.png)  | **Considérations relatives à la reconnaissance optique de caractères** <br>Ce modèle utilise la technologie de reconnaissance optique de caractères (OCR) pour analyser les fichiers .pdf, les fichiers image et les fichiers .tiff. Le traitement OCR fonctionne mieux sur des documents respectant les conditions requises suivantes : <br> - Format de fichier .jpg, .png ou .pdf (texte ou analysé). Les fichiers .pdf incorporés dans le texte sont préférables, car il n’y aura pas d’erreurs dans l’extraction et l’emplacement des caractères. <br> - Pour les fichiers .pdf et .tiff, jusqu’à 2 000 pages peuvent être traitées. <br> - La taille du fichier doit être inférieure à 50 Mo. <br> - Pour les images, les dimensions doivent être comprises entre 50 x 50 et 10 000 x 10 000 pixels. <br> - Pour les fichiers .pdf, les dimensions doivent être au maximum de 17 x 17 pouces, correspondant aux formats de papier Legal ou A3 et plus petites. <br> - La taille totale des données d’apprentissage est de 500 pages ou moins. <br> Notez les différences suivantes concernant les fichiers texte microsoft Office et les fichiers analysés par OCR (.pdf, image ou .tiff) : <br> - Fichiers Office : tronqués à 64 000 caractères (lors de l’entraînement et lors de l’exécution sur les fichiers d’une bibliothèque de documents). <br> - Fichiers analysés par OCR : il existe une limite de 20 pages.|
| ![Symbole de globe.](/office/media/icons/globe-internet.png)  | **Microsoft 365 Multigéographie** <br>Lorsque vous configurez Syntex dans un environnement [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo) , vous pouvez uniquement le configurer pour utiliser le type de modèle à l’emplacement central. Si vous souhaitez utiliser ce type de modèle dans un emplacement satellite, contactez le support Microsoft. |
| ![Symbole d’objets.](/office/media/icons/objects-blue.png)  | **Bibliothèques multimodèles** <br>Si plusieurs modèles entraînés sont appliqués à la même bibliothèque, le fichier est classé à l’aide du modèle qui a le score de confiance moyen le plus élevé. Les entités extraites proviennent uniquement du modèle appliqué. |

### <a name="receipt-processing"></a>Traitement des reçus

| Icône          | Description   |
| ------------- | ------------- |
| ![Symbole de fichiers.](/office/media/icons/files-blue.png)  | **Types de fichiers pris en charge** <br>Ce modèle prend en charge les types de fichiers suivants : .bmp, .jpeg, .pdf, .png et .tiff. |
| ![Symbole de conversation.](/office/media/icons/chat-room-conversation-blue.png)  | **Langues prises en charge** <br>Ce modèle prend en charge les reçus de vente en anglais provenant de l’Australie, du Canada, de la Grande-Bretagne, de l’Inde et du États-Unis. |
| ![Symbole de paragraphe.](/office/media/icons/paragraph-writing-blue.png)  | **Considérations relatives à la reconnaissance optique de caractères** <br>Ce modèle utilise la technologie de reconnaissance optique de caractères (OCR) pour analyser les fichiers .pdf, les fichiers image et les fichiers .tiff. Le traitement OCR fonctionne mieux sur des documents respectant les conditions requises suivantes : <br> - Format de fichier .jpg, .png ou .pdf (texte ou analysé). Les fichiers .pdf incorporés dans le texte sont préférables, car il n’y aura pas d’erreurs dans l’extraction et l’emplacement des caractères. <br> - Pour les fichiers .pdf et .tiff, jusqu’à 2 000 pages peuvent être traitées. <br> - La taille du fichier doit être inférieure à 50 Mo. <br> - Pour les images, les dimensions doivent être comprises entre 50 x 50 et 10 000 x 10 000 pixels. <br> - Pour les fichiers .pdf, les dimensions doivent être au maximum de 17 x 17 pouces, correspondant aux formats de papier Legal ou A3 et plus petites. <br> - La taille totale des données d’apprentissage est de 500 pages ou moins. <br> Notez les différences suivantes concernant les fichiers texte microsoft Office et les fichiers analysés par OCR (.pdf, image ou .tiff) : <br> - Fichiers Office : tronqués à 64 000 caractères (lors de l’entraînement et lors de l’exécution sur les fichiers d’une bibliothèque de documents). <br> - Fichiers analysés par OCR : il existe une limite de 20 pages.|
| ![Symbole de globe.](/office/media/icons/globe-internet.png)  | **Microsoft 365 Multigéographie** <br>Lorsque vous configurez Syntex dans un environnement [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo) , vous pouvez uniquement le configurer pour utiliser le type de modèle à l’emplacement central. Si vous souhaitez utiliser ce type de modèle dans un emplacement satellite, contactez le support Microsoft. |
| ![Symbole d’objets.](/office/media/icons/objects-blue.png)  | **Bibliothèques multimodèles** <br>Si plusieurs modèles entraînés sont appliqués à la même bibliothèque, le fichier est classé à l’aide du modèle qui a le score de confiance moyen le plus élevé. Les entités extraites proviennent uniquement du modèle appliqué. |
