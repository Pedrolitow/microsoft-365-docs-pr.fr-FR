---
title: Isolation du client dans Office 365 Video
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Dans cet article, trouvez une explication de la façon dont l’isolation du client conserve les vidéos stockées de chaque client séparément dans Office 365 Video.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fc67b17aa40b3bca9ce6d73ebb7e18319e780339
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50918929"
---
# <a name="tenant-isolation-in-office-365-video"></a>Isolation du client dans Office 365 Video

> [!NOTE]
> Office 365 Video sera remplacé par Microsoft Stream. Pour en savoir plus sur le nouveau service vidéo d’entreprise qui ajoute de l’intelligence à la collaboration vidéo et en savoir plus sur les plans de transition pour les clients Microsoft 365 Video actuels, voir la présentation de la [transition d’Office 365 Video](/stream/migrate-from-office-365)vers Microsoft Stream.

## <a name="introduction"></a>Introduction

Le stockage Azure est utilisé pour stocker des données pour plusieurs services Office 365, notamment Office 365 Video et Sway. Le stockage Azure inclut le stockage Blob, qui est un magasin d’objets cloud basé sur REST hautement évolutif, utilisé pour stocker des données non structurées. Le stockage Azure utilise un modèle de contrôle d’accès simple . chaque abonnement Azure peut créer un ou plusieurs comptes de stockage. Chaque compte de stockage possède une clé secrète unique qui est utilisée pour contrôler l’accès à toutes les données de ce compte de stockage. Cela prend en charge le scénario classique où le stockage est associé à des applications et où ces applications ont un contrôle total sur leurs données associées ; par exemple, Sway stockant du contenu dans le stockage Azure. Tout le contenu client pour Sway est stocké dans des comptes de stockage Azure partagés. Le contenu de chaque utilisateur se trouve dans une arborescence distincte d’objets blob dans le stockage Azure.

Les systèmes gérant l’accès aux environnements clients (par exemple, le portail Azure, SMAPI, etc.) sont isolés au sein d’une application Azure gérée par Microsoft. Cela sépare logiquement l’infrastructure d’accès client des applications client et de la couche de stockage.

## <a name="tenant-isolation-in-office-365-video"></a>Isolation du client dans Office 365 Video

[Office 365 Video](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6) est un portail d’entreprise qui fournit aux organisations une destination hautement sécurisée à l’échelle de l’organisation pour la publication, le partage et la découverte de contenu vidéo. Dans Office 365 Video, les vidéos de chaque client sont isolées et chiffrées dans tous les emplacements et sont uniquement accessibles aux utilisateurs authentifiés qui ont accès aux vidéos de l’organisation et y ont accès. Office 365 Video utilise une combinaison de technologies pour ce faire :

- SharePoint Online est utilisé pour stocker le fichier vidéo et les métadonnées (titre de la vidéo, description, etc.). Il fournit également la couche sécurité et conformité (y compris l’authentification) et les fonctionnalités de recherche.
- Azure Media Services fournit des fonctionnalités de transcodage, de diffusion en continu adaptative, de remise sécurisée (à l’aide du chiffrement AES) et de miniatures.

[Azure Media Services est](https://azure.microsoft.com/services/media-services/) une offre de plateforme en tant que service qui permet d’activer des flux de travail multimédias de bout en bout dans le cloud. La plateforme fournit une API REST pour le téléchargement, le codage, le chiffrement (avec PlayReady) et la distribution de médias via des centres de données Azure dans le monde entier.

Tous les téléchargements pour Office 365 Video se produisent via HTTPS. Lorsqu’un fichier vidéo est téléchargé, il est stocké dans SharePoint Online et une copie du fichier est envoyée via un canal chiffré à Azure Media Services. Azure Media Services transcode la vidéo dans plusieurs formats optimisés pour l’affichage (par exemple, mobile, faible bande passante, bande passante élevée, etc.). Ces fichiers, ainsi que le fichier d’origine acquis lors du chargement, sont stockés dans le stockage Blob Azure. Les fichiers sont chiffrés à l’aide d’AES 128 par l’algorithme de packaging MPEG Common Encryption (ou une version antérieure de PlayReady) pour la lecture, et chiffrés à l’aide du chiffrement de stockage AES 256 avant d’être stockés dans le stockage Blob Azure. (À l’aide du SDK client Azure Media Services, les clients peuvent contrôler le chiffrement utilisé. Par exemple, un client peut appliquer le chiffrement de stockage Azure Media Services (AES 256) à un bien multimédia à valeur élevée avant de le télécharger.

Azure Media Services génère également une miniature pour la vidéo, qu’il transmet avec des métadonnées miniatures à SharePoint Online via un canal chiffré.