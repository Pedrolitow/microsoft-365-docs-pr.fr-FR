---
title: Localiser l’expérience utilisateur
description: Comment trouver des appareils pour les utilisateurs
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
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
ms.openlocfilehash: 354f61284bbd95c1c7ca4cd50459a1644a89d090
ms.sourcegitcommit: 72795ec56a7c4db863dcaaff5e9f7c41c653fda8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52023260"
---
# <a name="localize-the-user-experience"></a>Localiser l’expérience utilisateur

Les utilisateurs d’appareils Bureau géré Microsoft peuvent sélectionner la langue de leur choix pendant le processus de configuration (expérience « out-of-box experience ») ou par la suite.

## <a name="during-setup-the-out-of-box-experience"></a>Lors de l’installation (expérience « out-of-box »)

Pendant le processus de configuration, les utilisateurs peuvent sélectionner la langue de leur choix. Cette sélection affecte les attributs ci-après :

- Fonctionnalités linguistiques de Windows 10 :
    - Langue d’affichage
    - Langue du clavier
    - Fonctionnalités liées à la langue à la demande

- Fonctionnalités linguistiques de Microsoft 365 Apps for Enterprise :
    - Langue d’affichage
    - Outils de preuve et de authoring

> [!NOTE]
> Les utilisateurs peuvent uniquement obtenir des fonctionnalités liées à la langue à la demande en sélectionnant la langue pendant le processus d’installation.

## <a name="after-completing-setup"></a>Après avoir terminé l’installation

Les utilisateurs peuvent sélectionner la langue de leur choix pour Windows 10 et Microsoft 365 Apps for Enterprise à tout moment une fois le processus d’installation terminé. Notamment :

- Fonctionnalités linguistiques de Windows 10 :
    - Langue d’affichage
    - Langue du clavier

- Fonctionnalités linguistiques de Microsoft 365 Apps for Enterprise :
    - Langue d’affichage
    - Outils de preuve et de authoring

Pour rendre les [langues](#supported-languages) prise en charge pour Microsoft 365 Apps for Enterprise disponibles pour que vos utilisateurs les installent, ajoutez-les au groupe Moderne **Workplace-Office-Language_Packs.** Les langues seront disponibles dans le portail d'entreprise Intune.


## <a name="supported-languages"></a>Langues prises en charge

Pour les nouveaux appareils, votre fabricant doit fournir des images d'appareil qui incluent les langues dont vous avez besoin. Si l'image de votre fabricant inclut des langues autres que celles fournies dans la liste des langues prise en charge, elle est toujours prise en charge par le service.

Si vous réutilisez des appareils existants, vous devrez peut-être travailler avec votre représentant de compte Microsoft pour obtenir les images appropriées. Pour plus d'informations, voir [Images d'appareil.](../service-description/device-images.md)

[L'image universelle](../service-description/device-images.md#universal-image) fournie par Bureau géré Microsoft inclut les langues suivantes et pour Windows 10 :

- Arabe
- Bulgare
- Chinois simplifié
- Chinois traditionnel
- Croate
- Tchèque
- Danois  
- Néerlandais  
- Anglais (États-Unis, GB, AU, CA, IN)
- Estonien
- Finnois 
- Français (France, Canada)
- Allemand
- Grec
- Hébreu
- Hongrois
- Indonésien
- Italien
- Japonais
- Coréen
- Letton
- Lituanien
- Norvégien (Bokmål)
- Polonais
- Portugais (Brésil)
- Portugais (Portugal)
- Roumain
- Russe 
- Serbe (alphabet latin)
- Slovaque
- Slovène
- Espagnol (Espagne, Mexique)
- Suédois
- Thaï
- Turc
- Ukrainien
- Vietnamien

Microsoft 365 Apps for Enterprise peut avoir une liste légèrement différente.

Si vos utilisateurs ont besoin d'une langue autre que celle répertoriée ici, déposez une demande de [support](../working-with-managed-desktop/admin-support.md) à l'aide du [portail d'administration.](access-admin-portal.md)

## <a name="languages-for-support-and-operations"></a>Langues pour la prise en charge et les opérations

### <a name="user-support"></a>Support pour les utilisateurs
Bureau géré Microsoft fournit une prise en charge uniquement en anglais. Si les utilisateurs choisissent une autre langue dans l'application Obtenir de l'aide, ils obtiennent le support des canaux de support microsoft généraux, plutôt que le support directement à partir du Bureau géré Microsoft. Pour plus d'informations, voir [Obtenir de l'aide pour les utilisateurs.](../working-with-managed-desktop/end-user-support.md)

Si vos utilisateurs ont besoin d'une prise en charge dans d'autres langues, vous devrez le fournir via des sources de support non-Microsoft ou à partir de votre propre organisation.

### <a name="admin-support-and-operations"></a>Support et opérations de l'administrateur
Bureau géré Microsoft fournit une prise en charge administrateur uniquement en anglais. Cela inclut le portail d’administration et toutes les communications avec les opérations Bureau géré Microsoft. Vous devez supposer que toutes les interactions et interfaces liées à l’administrateur seront en anglais, sauf indication contraire.


