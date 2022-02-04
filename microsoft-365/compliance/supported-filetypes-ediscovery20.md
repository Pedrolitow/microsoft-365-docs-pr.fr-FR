---
title: Types de fichiers pris en charge dans Advanced eDiscovery
f1.keywords:
  - NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: null
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
  - MOE150
  - MET150
description: 'Liste des types de fichiers pris en charge dans Microsoft 365 Advanced eDiscovery, y compris les types de fichiers image pris en charge par la fonctionnalité OCR dans Advanced eDiscovery.'
ms.custom: seo-marvel-apr2020
---

# <a name="supported-file-types-in-advanced-ediscovery"></a>Types de fichiers pris en charge dans Advanced eDiscovery

Advanced eDiscovery prend en charge de nombreux types de fichiers à de nombreux niveaux différents. Les types de fichiers de support sont décrits dans les tableaux suivants de cet article. Cette liste n’est pas finalisée et nous ajouterons de nouveaux types de fichiers à mesure que nous continuerons nos tests de validation. Ces tableaux indiquent si un type de fichier est pris en charge pour l’extraction de texte (et la reconnaissance optique de caractères ou l’extraction de texte OCR pour les fichiers image), consultable dans la visionneuse native et également pris en charge dans la visionneuse Annotate dans Advanced eDiscovery.

## <a name="archive--container"></a>Archive/Conteneur

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de conteneur|Extensions possibles|
|---|:---:|:---:|:---:|:---:|
|application/x-7z compressé|Oui|Oui|Oui|.7z|
|application/x-rar-compressed|Oui|Oui|Oui|.rar|
|application/x-tar|Oui|Oui|Oui|.tar|
|application/zip|Oui|Oui|Oui|.zip|
|

## <a name="audio--video"></a>Audio/Vidéo

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/mp4|Oui|Oui|Non|Oui|Non|.f4v; .m4a; .m4v; .mp4; .mp4v; .mpeg; .mpeg4|
|audio/mpeg|Oui|Oui|Non|Oui|Non|.mpeg|
|video/3gpp|Oui|Oui|Non|Oui|Non|.3gp|
|video/3gpp2|Oui|Oui|Non|Oui|Non|.3g2; .3gp2|
|video/quicktime|Oui|Oui|Non|Oui|Non|.moov; .mov; .qt|
|video/x-m4v|Oui|Oui|Non|Oui|Non|.m4v|
|

## <a name="database"></a>Database

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-msaccess|Oui|Oui|Oui|Non|Non|.mdb|
|

## <a name="email"></a>E-mail

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-outlook|Oui|Oui|Oui|Oui|Oui|.msg|
|message/rfc822|Oui|Oui|Oui|Oui|Oui|.eml|
|text/vcard-contact|Oui|Oui|Oui|Oui|Oui|.vcf|
|

## <a name="email-container"></a>Conteneur de messagerie

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de conteneur|Extensions possibles|
|---|:---:|:---:|:---:|:---:|
|application/mbox|Oui|Oui|Oui|.mbox|
|application/vnd.ms-outlook-pst|Oui|Oui|Oui|.pst|
|

## <a name="html"></a>HTML

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/xhtml+xml|Oui|Oui|Oui|Oui|Oui|.xhtml|
|application/xml|Oui|Oui|Oui|Oui|Oui|.xml|
|text/html|Oui|Oui|Oui|Oui|Oui|.htm; .html; .shtml|
|

## <a name="image"></a>Image

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte OCR|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|image/bmp|Oui|Oui|Oui|Oui|Oui|.bmp|
|image/emf|Oui|Oui|Oui|Oui|Oui|.emf|
|image/gif|Oui|Oui|Oui|Oui|Oui|.gif|
|image/jpeg|Oui|Oui|Oui|Oui|Oui|.jpeg; .jpg|
|image/png|Oui|Oui|Oui|Oui|Oui|.png|
|image/svg+xml|Oui|Oui|Oui|Oui|Non|.svg|
|image/tiff|Oui|Oui|Oui|Oui|Oui|.tif|
|image/vnd.dwg|Oui|Oui|Oui|Oui|Oui|.dwg; .dxf|
|image/wmf|Oui|Oui|Oui|Oui|Oui|.wmf|
|

## <a name="microsoft-excel"></a>Microsoft Excel

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-excel|Oui|Oui|Oui|Oui|Oui|.dat; .xls|
|application/vnd.ms-excel.sheet.binary.macroenabled.12|Oui|Oui|Oui|Oui|Non|.xlsb|
|application/vnd.ms-excel.sheet.macroenabled.12|Oui|Oui|Oui|Oui|Oui|.xlsm|
|application/vnd.ms-excel.template.macroenabled.12|Oui|Oui|Oui|Non|Non|.xltm|
|application/vnd.openxmlformats-officedocument.spreadsheetml.sheet|Oui|Oui|Oui|Oui|Oui|.xlsx|
|application/vnd.openxmlformats-officedocument.spreadsheetml.template|Oui|Oui|Oui|Oui|Oui|.xltx|
|

## <a name="microsoft-onenote"></a>Microsoft OneNote

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/onenote|Oui|Oui|Oui|Non|Non|.one|
|

## <a name="microsoft-powerpoint"></a>Microsoft PowerPoint

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-powerpoint|Oui|Oui|Oui|Oui|Oui|.pot; .pps; .ppt|
|application/vnd.openxmlformats-officedocument.presentationml.presentation|Oui|Oui|Oui|Oui|Oui|.pptx|
|application/vnd.openxmlformats-officedocument.presentationml.slideshow|Oui|Oui|Oui|Oui|Oui|.ppsx|
|application/vnd.openxmlformats-officedocument.presentationml.template|Oui|Oui|Oui|Oui|Oui|.potx|
|

## <a name="microsoft-project"></a>Microsoft Project

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-project|Oui|Oui|Oui|Non|Oui|.mpp|
|

## <a name="microsoft-publisher"></a>Microsoft Publisher

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-mspublisher|Oui|Oui|Oui|Oui|Oui|.pub|
|

## <a name="microsoft-visio"></a>Microsoft Visio

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-visio.drawing|Oui|Oui|Oui|Oui|Non||
|application/vnd.visio|Oui|Oui|Oui|Oui|Oui|.vsd|
|

## <a name="microsoft-word"></a>Microsoft Word

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/msword|Oui|Oui|Oui|Oui|Oui|.dat; .doc|
|application/rtf|Oui|Oui|Oui|Oui|Oui|.doc; .rtf|
|application/vnd.ms-word.document.macroenabled.12|Oui|Oui|Oui|Oui|Oui|.docm|
|application/vnd.ms-word.template.macroenabled.12|Oui|Oui|Oui|Oui|Oui|.dotm|
|application/vnd.openxmlformats-officedocument.wordprocessingml.document|Oui|Oui|Oui|Oui|Oui|.docx|
|application/vnd.openxmlformats-officedocument.wordprocessingml.template|Oui|Oui|Oui|Oui|Oui|.dotx|
|

## <a name="microsoft-works"></a>Microsoft Works

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-works-ss|Oui|Oui|Non|Non|Non|.wps|
|application/vnd.ms-works-wp|Oui|Oui|Non|Non|Non|.wps|
|

## <a name="open-document-format"></a>Open Document Format

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.oasis.opendocument.text|Oui|Oui|Oui|Oui|Oui|.odt|
|

## <a name="other"></a>Autre

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/json|Oui|Oui|Oui|Oui|Oui|N/A|
|application/octet-stream|Oui|Non|Non|Non|Non|.fluid|
|application/vnd.ms-graph|Oui|Oui|Non|Non|Non||
|application/winhlp|Oui|Oui|Non|Non|Non|.hlp|
|application/x-tnef|Oui|Oui|Non|Non|Non||
|

## <a name="plain-text"></a>Texte brut

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|text/csv|Oui|Oui|Oui|Oui|Oui|.csv|
|text/plain|Oui|Oui|Oui|Oui|Oui|.con; .css; .csv; .dat; .pl; .txt|
|

## <a name="portable-document-format"></a>Portable Document Format

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/pdf|Oui|Oui|Oui|Oui|Oui|.pdf|
|

## <a name="word-perfect"></a>Word Perfect

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.wordperfect; version=5.0|Oui|Oui|Oui|Non|Non|.wpd|
|application/vnd.wordperfect; version=5.1|Oui|Oui|Oui|Non|Non|.wpd|
|application/vnd.wordperfect; version=6.x|Oui|Oui|Oui|Non|Non|.wpd|
|

## <a name="word-pro"></a>Word Pro

<br>

****

|Type Mime|Identification de fichier|Extraction des métadonnées|Extraction de texte|Visionneuse native|Annoter la visionneuse|Extensions possibles|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.lotus-wordpro|Oui|Oui|Non|Non|Non|.lwp|
|
