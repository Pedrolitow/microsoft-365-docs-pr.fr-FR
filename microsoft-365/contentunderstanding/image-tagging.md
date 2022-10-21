---
title: Étiquetage d’images dans Microsoft Syntex
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.service: microsoft-syntex
ms.custom: admindeeplinkMAC
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: En savoir plus sur l’étiquetage d’images dans Microsoft Syntex.
ms.openlocfilehash: 35bcb403d743400dcc3c125a2ff633022d217fdf
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662267"
---
# <a name="image-tagging-in-microsoft-syntex"></a>Étiquetage d’images dans Microsoft Syntex

(Bientôt disponible)

Avec le balisage d’image dans Microsoft Syntex, les utilisateurs peuvent rechercher des images par le biais de la recherche en effectuant des recherches sur des étiquettes d’image et créer des flux de travail basés sur des étiquettes d’image. Par défaut, le balisage de base des images est activé pour SharePoint et OneDrive. Les images chargées dans l’un des emplacements sont automatiquement analysées et des balises valables sont appliquées, le cas échéant, à partir d’une liste de 37 balises de base. Les utilisateurs peuvent trouver des images en effectuant une recherche sur les balises d’images.

Lorsqu’un utilisateur charge une image, le processus de balisage s’exécute automatiquement. Si une image est modifiée, le processus de balisage s’exécute à nouveau pour la mise à jour des balises.

Les utilisateurs disposant d’autorisations sur le fichier image peuvent consulter et modifier les balises dans le volet d’informations sur le fichier ou dans la page des résultats de la recherche. Dès qu’un utilisateur modifie les balises d’une image, le système n’effectue plus le balisage automatique de cette image, même en cas de modification.

Si vous désactivez l’option de balisage, les images ne seront plus marquées automatiquement. Les balises existantes ne seront pas supprimées.

> [!NOTE]
> Les balises générées par le système peuvent changer avec les mises à jour de l’image ou notre technologie de balises.

## <a name="configure-image-tagging"></a>Configurer le balisage d’image

Après avoir [configuré Syntex](set-up-content-understanding.md), vous pouvez configurer l’étiquetage des images dans le Centre d'administration Microsoft 365.

Pour activer ou désactiver le balisage d’images

1. Dans la Centre d'administration Microsoft 365, sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Configuration**</a>.

2. Sous **Connaissances organisationnelles**, cliquez sur **Automatiser la compréhension de contenu**.

3. Cliquez sur **Gérer**.

4. Sous l’onglet **Balisage d'image**, cliquez sur **Modifier**.

5. Choisissez d’autoriser le **Balisage d’image** ou de le **Désactiver**.

6. Cliquez sur **Enregistrer**.

    ![Capture d’écran du contrôle d’étiquetage d’image.](../media/content-understanding/sharepoint-syntex-image-tagging-control.png)
