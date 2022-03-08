---
title: Noms de l’appareil
description: Comment Microsoft Manged Desktop gestion des noms d’appareils
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: fe29027dab3b3395c14729ee7e04cbe7cebf7261
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317162"
---
# <a name="device-names"></a>Noms de l’appareil

Microsoft Manged Desktop utilise Windows Autopilot, Azure Active Directory et Microsoft Intune.

Pour que ces services fonctionnent ensemble en toute transparence, les appareils ont besoin de noms cohérents et normalisés. Microsoft Manged Desktop un format de nom standardisé (au `MMD-%RAND11`format ) lorsque les appareils sont inscrits. Windows Autopilot affecte ces noms. Pour plus d’informations sur Autopilot, consultez l’expérience de première expérience avec [Autopilot et la page État de l’inscription](../get-started/esp-first-run.md).

## <a name="automated-name-changes"></a>Modifications automatiques de noms

Si un appareil est renommé ultérieurement, Microsoft Manged Desktop le renommera automatiquement en un nouveau nom au format standardisé. Ce processus se produit toutes les quatre heures. Le changement de nom a lieu lors du prochain redémarrage de l’appareil par l’utilisateur.

> [!IMPORTANT]
> Si votre environnement dépend de noms d’appareils spécifiques (par exemple, pour prendre en charge une configuration réseau particulière), vous devez examiner les options pour supprimer cette dépendance avant de vous inscrire à Microsoft Manged Desktop.<br><br>Si vous devez conserver la dépendance de nom, vous pouvez envoyer une demande via le [](../working-with-managed-desktop/admin-support.md) portail d’administration pour désactiver la fonction de changement de nom et utiliser le format de nom souhaité.
