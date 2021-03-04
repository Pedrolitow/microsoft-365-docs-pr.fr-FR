---
title: Gérer les liens sécurisés
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment gérer les liens sécurisés pour protéger votre entreprise contre les sites malveillants.
ms.openlocfilehash: 0f0cc6845f699ba5b05c30e21f876f4b4d47b6a6
ms.sourcegitcommit: 355bd51ab6a79d5c36a4e4f57df74ae6873eba19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50422242"
---
# <a name="manage-safe-links"></a>Gérer les liens sécurisés

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvdwy?autoplay=false]

Microsoft Defender pour Office 365, anciennement appelé Microsoft 365 - Protection avancée contre les menaces, permet de protéger votre entreprise contre les sites malveillants lorsque les utilisateurs cliquent sur des liens dans les applications Office.

## <a name="try-it"></a>Essayez !

1. Go to the [admin center](https://admin.microsoft.com), and select **Setup**.
1. Faites défiler vers le bas **pour renforcer la protection contre les menaces avancées.** Sélectionnez **Afficher,** **Gérer,** puis **Liens sécurisés ATP.**
1. Sous **Stratégies qui s’appliquent à l’ensemble de l’organisation,** choisissez la stratégie par défaut, puis sélectionnez **l’icône** Modifier. 
1. Entrez une URL que vous souhaitez bloquer.
1. Sélectionnez **Utiliser des liens sécurisés dans les applications Office, Office pour iOS et Android**; select **Do not track when users click safe links**; et **sélectionnez Ne pas laisser les utilisateurs cliquer sur les liens sécurisés vers l’URL d’origine.** Elles peuvent déjà être sélectionnées si vous définissez la stratégie par défaut. Sélectionnez **Enregistrer**.
1. Sous **Stratégies qui s’appliquent à des destinataires spécifiques,** **sélectionnez** Règle de liens sécurisés recommandée, puis sélectionnez **l’icône** Modifier.
1. Sélectionnez **les paramètres,** faites défiler vers le bas, entrez l’URL que vous ne souhaitez pas vérifier, puis sélectionnez l’icône Ajouter. 
1. Sélectionnez **Appliqué à,** puis sélectionnez votre nom de domaine. Sélectionnez les domaines supplémentaires à appliquer à la règle. Sélectionnez **Ajouter,** **OK,** puis **Enregistrer.**

Les liens sécurisés ATP sont désormais configurés. Laissez jusqu’à 30 minutes pour que vos modifications prennent effet.

Lorsqu’un utilisateur reçoit un e-mail avec des liens, les liens sont analysés. Si les liens sont considérés comme sûrs, ils peuvent être cliqués. Toutefois, si le lien figure dans la liste des blocages, les utilisateurs voient un message s’ils l’ont bloqué.