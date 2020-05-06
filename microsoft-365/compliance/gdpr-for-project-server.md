---
title: RGPD pour Project Server
description: Découvrez comment répondre aux exigences en matière de Règlement général sur la protection des données (RGPD) dans un serveurs Project local.
f1.keywords:
- NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
titleSuffix: Microsoft GDPR
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3a7eb291d0da72adf171594aac307ec0ad91829d
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44036237"
---
# <a name="gdpr-for-project-server"></a>RGPD pour Project Server

Project Server utilise des scripts personnalisés pour exporter et supprimer des données utilisateur dans Project Web App. Le processus de base est le suivant :

1.  Recherchez les sites Project Web App dans votre batterie de serveurs.

2.  Recherchez les projets dans chaque site contenant l’utilisateur.

3.  Exportez et passez en revue les types de données que vous voulez examiner.

4.  Supprimez des données si nécessaire.

Ces étapes sont expliquées en détail dans les articles suivants :

- [Exportation de données utilisateur depuis Project Server](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [Suppression de données utilisateur de Project Server](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


Notez que Project Server est basé sur SharePoint Server et consigne les événements dans les journaux ULS de SharePoint et dans la base de données d’utilisation. Pour en savoir plus, consultez l’article qui traite du [RGPD dans SharePoint Server](gdpr-for-sharepoint-server.md).
