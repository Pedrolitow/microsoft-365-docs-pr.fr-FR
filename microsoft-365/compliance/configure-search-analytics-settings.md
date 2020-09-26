---
title: Configurer les paramètres de recherche et d’analyse-enquêtes de données
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment configurer les paramètres de recherche et d’analyse, tels que les doublons, le Threading de messagerie électronique et les thèmes lors de la gestion des analyses de données.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: ebc04e68c4d8854c91ceae75b164cc061e77aad4
ms.sourcegitcommit: 1423e08a02d30f0a2b993fb99325c3f499c31787
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "48277076"
---
# <a name="configure-search-and-analytics-settings-in-data-investigations"></a>Configurer les paramètres de recherche et d’analyse dans les enquêtes de données

## <a name="near-duplicates-and-email-threading"></a>Quasi-doublons et thread de courrier

Dans cette section, vous pouvez définir des paramètres pour la détection des doublons, la détection des doublons et le Threading de messagerie.

- Activer/désactiver : inclut la détection des doublons, la détection à proximité des doublons et le Threading du courrier électronique dans le cadre du flux d’analyse s’il est activé. Étant donné qu’ils sont générés les uns sur les autres, vous devez tous les activer ou les désactiver tous.

- Seuil : si le niveau de similarité de deux documents est supérieur au seuil, ils seront placés dans le même ensemble presque en double.

- Masquer les doublons par défaut : si ce paramètre est activé, un filtre permettant de masquer les doublons de documents est appliqué par défaut dans le jeu de travail. Si nécessaire, le filtre peut être supprimé manuellement dans le jeu de travail.

- Nombre minimal/maximum de mots : les doublons et les threads de courrier électronique s’exécutent uniquement sur les documents qui contiennent au moins le nombre minimal de mots et le nombre maximal de mots.

Pour plus d’informations, consultez la rubrique [near Detection Detection](near-duplicates.md) and [email Threading](email-threading.md).

## <a name="themes"></a>Thèmes

Dans cette section, vous pouvez définir des paramètres pour les thèmes.

- Activer/désactiver : inclut le clustering thèmes dans le cadre du flux d’analyse s’il est activé.

- Ajuster dynamiquement le nombre maximal de thèmes : dans certains cas, il n’y a pas assez de documents pour produire le nombre de thèmes souhaité. Si ce paramètre est activé, au lieu d’essayer de forcer le nombre maximal de thèmes souhaités, le système ajuste le nombre maximal de thèmes de manière dynamique.

- Nombre maximal de thèmes : nombre souhaité de thèmes.

- Inclure les numéros dans les thèmes : lorsque ce dernier est activé, il inclut des numéros dans lors de la génération de thèmes.  

## <a name="optical-character-recognition-ocr"></a>Reconnaissance optique des caractères

Lorsque ce paramètre est activé, la reconnaissance optique de caractères est exécutée sur les images qui sont ingérées dans les jeux de travail afin qu’ils puissent être recherchés.

## <a name="ignore-text"></a>Ignorer le texte

Il existe des situations dans lesquelles certains textes réduisent la qualité de l’analyse, tels que des clauses de responsabilité longues qui sont ajoutées à certains courriers électroniques indépendamment du contenu du message. Si vous avez conscience de ces cas, vous pouvez exclure ce texte de l’analyse en spécifiant le texte (RegEx est pris en charge) et les modules pour lesquels le texte doit être exclu.
