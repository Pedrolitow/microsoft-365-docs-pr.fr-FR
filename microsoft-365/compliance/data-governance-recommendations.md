---
title: Comment le contenu est identifié pour consulter des recommandations de gouvernance des données
f1.keywords:
- NOCSH
ms.author: brendonb
author: cabailey
manager: laurawi
ms.date: 1/15/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.custom: admindeeplinkDEFENDER
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Le Centre de sécurité et conformité Microsoft 365 et le Centre de conformité Microsoft 365 fournissent des recommandations pour la gouvernance des données basées sur la configuration actuelle de votre organisation et vous permet de configurer certaines actions en quelques clics. Certaines de ces recommandations détectent du contenu spécifique dans votre organisation, puis actualisent les étapes recommandées pour la gestion de ce contenu. Par exemple, une recommandation peut détecter les éléments qui présentent un contenu de critique commerciale (tel qu un privilège client-avocat ou informations accord de confidentialité) et vous permet automatiquement d’appliquer une étiquette de rétention à ces éléments pour vous assurer qu’ils soient classés et conservés selon vos besoins . Cette rubrique répertorie les recommandations de gouvernance des données que vous pouvez voir et décrit quel contenu est détecté au déclenchement de chacun d’eux.
ms.openlocfilehash: f6343ab8856393f1928edfdb917e26fe9d72cc97
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2021
ms.locfileid: "60963346"
---
# <a name="how-content-is-identified-for-data-governance-recommendations"></a>Comment le contenu est identifié pour consulter des recommandations de gouvernance des données

Le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Centre de sécurité Microsoft 365</a> et le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centre de conformité Microsoft 365</a> fournissent des recommandations pour la gouvernance des données en fonction de la configuration actuelle de votre organisation et vous permettent de configurer les choses en quelques clics. Certaines de ces recommandations détectent du contenu spécifique dans votre organisation, puis fournissent les étapes recommandées pour la gestion de ce contenu. Par exemple, une recommandation peut détecter les éléments qui contiennent du contenu critique pour l’entreprise (par exemple, le privilège avocat-client ou les informations NDA), puis vous permettre d’appliquer automatiquement une étiquette de rétention à ces éléments pour vous assurer qu’ils sont classifiés et conservés en fonction des besoins.

Cette rubrique répertorie les recommandations de gouvernance des données que vous pouvez voir et décrit le contenu est détecté au déclenchement de chacun d’eux.

## <a name="clean-up-voicemail"></a>Nettoyer la messagerie vocale

Cette recommandation s’affiche lorsque les messages électroniques identifiés comme message de type « messagerie vocale » sont détectés dans les boîtes aux lettres des utilisateurs. En savoir plus sur [propriétés dans Exchange de message](/exchange/policy-and-compliance/ediscovery/message-properties-and-search-operators#searchable-properties-in-exchange).

## <a name="label-attorney-client-privilege-content"></a>Étiquette du contenu client avocat privilège élevé

Cette recommandation s’affiche lorsqu’un des critères suivants est rempli.

- Une combinaison de ces mots clés est détectée dans le corps du message électronique:
  - ACP
  - Privilège Client Avocat  
  - Privilège Client-Avocat  
  - Privilège de Client/Avocat (A/C Privilégié)

- N’importe quelle combinaison de ces mots clés est détectée dans les fichiers SharePoint ou OneDrive:
  - ACP
  - Privilège Client Avocat*
  - Privilège AC

## <a name="retain-audio-files"></a>Conservation des fichiers audio

Cette recommandation s’affiche lorsque les types de fichiers suivants sont détectés dans SharePoint ou OneDrive.

- .MP3
- .WMA
- .WAV
- .RA
- .RAM
- .RM
- .MID
- .OGG
- .AIFF
- .PCM
- .AAC
- .FLAC
- . ALAC

## <a name="retain-cad-files"></a>Conservation des fichiers de CAD

Cette recommandation s’affiche lorsque les types de fichiers suivants sont détectés dans SharePoint ou OneDrive.

- .3DXML
- . ACIS
- .ARC

- .ASM
- .CAT*
- . CGR
- .DW*
- .DX*
- .EDRW
- .IAM
- .IGES
- . IGS
- .IPT
- .JT
- .MF1
- . NEU
- .PAR
- .PKG
- .PRC

- .PRT
- .PSM
- .PWD
- . SLD *
- .STEP
- . STL
- .STP
- .U3D
- . UNV
- . VRML
- . WRL
- .X_*
- .XAS
- .XMT*
- .XPR

## <a name="retain-image-files"></a>Conservation de fichiers image

Cette recommandation s’affiche lorsque les types de fichiers suivants sont détectés dans SharePoint ou OneDrive.

- .JPEG
- .GIF
- .TIF*
- .BMP
- .PNG
- .RAW
- .PSD
- .PSP

- .JPG
- .EXIF
- .PPM
- .PGM
- .PBM
- .PNM
- .WEBP

## <a name="retain-nda-content"></a>Conserver le contenu de l’accord de confidentialité

Cette recommandation s’affiche lorsqu’un des critères suivants est rempli.

- Une combinaison de ces mots clés est détectée dans le corps du message électronique:
  - ACCORD DE CONFIDENTIALITÉ
  - « Accord de confidentialité »
  - « Accord de confidentialité »

- N’importe quelle combinaison de ces mots clés est détectée en .PDF ou .DOC dans les fichiers SharePoint ou OneDrive:
  - ACCORD DE CONFIDENTIALITÉ
  - Accord de Non Divulgation

## <a name="retain-software-development-files"></a>Conservation des fichiers de développement de logiciel

Cette recommandation s’affiche lorsque les types de fichiers suivants sont détectés dans SharePoint ou OneDrive.

- .ASAX
- .ASM
- .ASP*
- .BAT
- .CONFIG
- .CS
- .CSS
- .DISCO
- .HTM*
- .INC
- .JAD
- .JAVA
- .JS*
- .LIB
- .O
- .PHP
- .RC
- .RESX
- . RPT
- .RSS
- .SCPT
- .SRC
- .VB*
- .WSF
- .XCODEPROJ
- .XML
- .XSD
- .XSL*

## <a name="retain-video-files"></a>Conservation des fichiers vidéo

Cette recommandation s’affiche lorsque les types de fichiers suivants sont détectés dans SharePoint ou OneDrive.

- .AVCHD
- .AVI
- .FLV
- .MOV
- .MP2V
- .MP4
- .MP4V
- .MPE
- MPEG
- .MPEG1
- .MPEG2
- .MPEG4
- .MPG
- .MPG2
- .MPG4
- .WMV
- .XMV
