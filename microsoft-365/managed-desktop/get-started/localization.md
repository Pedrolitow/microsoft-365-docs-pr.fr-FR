---
title: Localiser l’expérience utilisateur
description: Comment trouver des appareils pour les utilisateurs
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
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
ms.openlocfilehash: a1a042047e3203d8c401f5435e87bafa20aa952ca9e32a051b47ea3a038b7aad
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53800689"
---
# <a name="localize-the-user-experience"></a>Localiser l’expérience utilisateur

Les utilisateurs Microsoft Manged Desktop peuvent sélectionner la langue de leur choix pendant le processus d’installation (expérience « out-of-box experience ») ou par la suite.

## <a name="during-setup-the-out-of-box-experience"></a>Lors de l’installation (expérience « out-of-box »)

Pendant le processus de configuration, les utilisateurs peuvent sélectionner la langue de leur choix. Cette sélection affecte les attributs ci-après :

- Windows 10 fonctionnalités linguistiques :
    - Langue d’affichage
    - Langue du clavier
    - Fonctionnalités liées à la langue à la demande

- Microsoft 365 Apps pour Enterprise fonctionnalités linguistiques :
    - Langue d’affichage
    - Outils de preuve et de authoring

> [!NOTE]
> Les utilisateurs peuvent uniquement obtenir des fonctionnalités liées à la langue à la demande en sélectionnant la langue pendant le processus d’installation.

## <a name="after-completing-setup"></a>Après avoir terminé l’installation

Les utilisateurs peuvent sélectionner la langue de leur choix pour Windows 10 et Microsoft 365 Apps pour Enterprise à tout moment une fois le processus d’installation terminé. Notamment :

- Windows 10 fonctionnalités linguistiques :
    - Langue d’affichage
    - Langue du clavier

- Microsoft 365 Apps pour Enterprise fonctionnalités linguistiques :
    - Langue d’affichage
    - Outils de preuve et de authoring

Pour rendre les langues Microsoft 365 Apps pour Enterprise prise en charge disponibles pour vos [utilisateurs,](#supported-languages) ajoutez-les au groupe Espace de travail **Office-Language_Packs** moderne. Les langues seront disponibles dans le Portail d’entreprise Intune.


## <a name="supported-languages"></a>Langues prises en charge

Pour les nouveaux appareils, votre fabricant doit fournir des images d’appareil qui incluent les langues dont vous avez besoin. Si l’image de votre fabricant inclut des langues autres que celles fournies dans la liste des langues prise en charge, elle est toujours prise en charge par le service.

Si vous réutilisez des appareils existants, vous devrez peut-être travailler avec votre représentant de compte Microsoft pour obtenir les images appropriées. Pour plus d’informations, voir [Images d’appareil.](../service-description/device-images.md)

[L’image universelle](../service-description/device-images.md#universal-image) fournie par Microsoft Manged Desktop inclut ces langues et pour les Windows 10 :

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

Microsoft 365 Apps pour Enterprise peut être prise en charge d’une liste légèrement différente.

Si vos utilisateurs ont besoin d’une langue autre que celle répertoriée ici, déposez une demande de [support](../working-with-managed-desktop/admin-support.md) à l’aide du [portail d’administration.](access-admin-portal.md)

## <a name="languages-for-support-and-operations"></a>Langues pour la prise en charge et les opérations

### <a name="user-support"></a>Support pour les utilisateurs
Microsoft Manged Desktop ne fournit une prise en charge qu’en anglais. Si les utilisateurs choisissent une autre langue dans l’application Aide, ils obtiennent le support des canaux de support microsoft généraux, au lieu d’être directement Microsoft Manged Desktop. Pour plus d’informations, voir [Obtenir de l’aide pour les utilisateurs.](../working-with-managed-desktop/end-user-support.md)

Si vos utilisateurs ont besoin d’une prise en charge dans d’autres langues, vous devrez le fournir via des sources de support non-Microsoft ou à partir de votre propre organisation.

### <a name="admin-support-and-operations"></a>Support et opérations de l’administrateur
Microsoft Manged Desktop prise en charge de l’administrateur uniquement en anglais. Cela inclut le portail d’administration et toutes les communications avec Microsoft Manged Desktop opérations. Vous devez supposer que toutes les interactions et interfaces liées à l’administrateur seront en anglais, sauf indication contraire.


