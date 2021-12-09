---
title: Déployer les Microsoft 365 Lighthouse base de référence
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment déployer des Microsoft 365 Lighthouse de référence.
ms.openlocfilehash: e60e364579abdc414ec9f7f3d16863f0139c9e6d
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61372647"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a>Déployer les Microsoft 365 Lighthouse base de référence 

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences.](m365-lighthouse-requirements.md) Si votre organisation n’a pas Microsoft 365 Lighthouse, [consultez s’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse de référence vous permet de déployer des configurations de client géré standard pour sécuriser les utilisateurs, les appareils et les données au sein des clients. Il existe six configurations de référence par défaut qui sont standard avec le Contrôle :

- Exiger l’mf pour les administrateurs
- Exiger l’mf pour les utilisateurs finaux
- Bloquer l’authentification héritée
- Configurer l’inscription des appareils dans Microsoft Endpoint Manager – Azure AD rejoindre
- Configurer la stratégie antivirus Defender pour les Windows mobiles
- Configurer la stratégie de conformité pour Windows appareils

## <a name="before-you-begin"></a>Avant de commencer

Assurez-vous que vous et vos clients respectez les conditions requises répertoriées dans [La](m365-lighthouse-requirements.md)Microsoft 365 Lighthouse .

## <a name="learn-more-about-the-default-baseline"></a>En savoir plus sur la ligne de base par défaut

Sélectionnez **Lignes de** base dans le volet de navigation gauche pour ouvrir la page Lignes de base. Vous verrez que la planification par défaut a déjà été ajoutée au groupe de locataires par défaut (tous les locataires). Pour afficher les configurations de référence par défaut, sélectionnez Afficher la ligne **de** base pour ouvrir la page de référence par défaut. Les configurations sont répertoriées en tant qu’étapes de déploiement. Sélectionnez l’une des étapes de déploiement pour afficher les détails du déploiement et l’impact sur l’utilisateur.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Capture d’écran de la page de référence par défaut.>.":::

## <a name="deploy-a-baseline-configuration"></a>Déployer une configuration de référence  

1. Dans la page de navigation de gauche, **sélectionnez Locataires** pour afficher la liste de vos locataires intégrés.

2. Sélectionnez le client sur qui vous souhaitez déployer la configuration de référence.

3. Sélectionnez **l’onglet Plans** de déploiement pour voir toutes les étapes de déploiement de la ligne de base qui ont été ajoutées au plan de déploiement du client.

4. Sélectionnez une étape de déploiement pour ouvrir la page étape du déploiement.

5. Sélectionnez **Appliquer** pour appliquer l’étape de déploiement sélectionnée au client. Si l’étape de déploiement indique « Cette action nécessite une étape manuelle », veillez à effectuer l’étape manuelle afin que l’étape de déploiement soit appliquée correctement.

## <a name="related-content"></a>Contenu associé

[Vue d’ensemble de l’utilisation des lignes de base pour déployer](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) des configurations client standard (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)
