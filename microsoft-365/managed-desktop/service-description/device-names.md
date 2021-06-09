---
title: Noms de l’appareil
description: Comment Bureau géré Microsoft gestion des noms d’appareils
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: adf4809e0d8dc29f170475435b19092abf2062fd
ms.sourcegitcommit: 55791ddab9ae484f76b30f0470eec8a4cf7b46d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2021
ms.locfileid: "51893894"
---
# <a name="device-names"></a>Noms de l’appareil

Bureau géré Microsoft utilise Windows Autopilot, Azure Active Directory et Microsoft Intune. Pour que ces services fonctionnent ensemble en toute transparence, les appareils ont besoin de noms cohérents et normalisés. Bureau géré Microsoft un format de nom standardisé (au format *MMD-%RAND11)* lorsque les appareils sont inscrits. Windows Autopilot attribue ces noms. Pour plus d’informations sur Autopilot, voir l’expérience de première expérience avec Autopilot et la page État de [l’inscription.](../get-started/esp-first-run.md)

## <a name="automated-name-changes"></a>Modifications automatiques de noms

Si un appareil est renommé ultérieurement, Bureau géré Microsoft le renommera automatiquement en un nouveau nom au format standardisé. Ce processus se produit toutes les quatre heures. Le changement de nom a lieu lors du prochain redémarrage de l’appareil par l’utilisateur.

> [!IMPORTANT]
> Si votre environnement dépend de noms d’appareils spécifiques (par exemple, pour prendre en charge une configuration réseau particulière), vous devez examiner les options pour supprimer cette dépendance avant de vous inscrire à Bureau géré Microsoft. Si vous devez conserver la dépendance de nom, [](../working-with-managed-desktop/admin-support.md) vous pouvez envoyer une demande via le portail d’administration pour désactiver la fonction de changement de nom et utiliser le format de nom souhaité.