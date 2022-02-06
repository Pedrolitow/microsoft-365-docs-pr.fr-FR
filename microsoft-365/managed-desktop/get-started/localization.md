---
title: Localiser l’expérience utilisateur
description: Comment trouver des appareils pour les utilisateurs
keywords: 'Bureau géré Microsoft, Microsoft 365, service, documentation'
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
---

# <a name="localize-the-user-experience"></a>Localiser l’expérience utilisateur

Les utilisateurs Microsoft Manged Desktop peuvent sélectionner la langue de leur choix pendant le processus d’installation (expérience « out-of-box experience ») ou par la suite.

## <a name="during-setup-the-out-of-box-experience"></a>Lors de l’installation (expérience « out-of-box »)

Pendant l’installation, les utilisateurs peuvent sélectionner la langue de leur choix. Cette sélection affecte les attributs ci-après :

| Attribut | Description |
| ------ | ------ |
| Windows 10 de langue | <ul><li>Langue d’affichage</li><li>Langue du clavier</li><li>Fonctionnalités liées à la langue à la demande</li><ul> |
| Microsoft 365 Apps des fonctionnalités Enterprise langue | <ul><li>Langue d’affichage</li><li>Outils de preuve et de authoring</li></ul> |

> [!NOTE]
> Les utilisateurs peuvent uniquement obtenir des fonctionnalités liées à la langue à la demande en sélectionnant la langue pendant le processus d’installation.

## <a name="after-completing-setup"></a>Après avoir terminé l’installation

Les utilisateurs peuvent sélectionner la langue de leur choix pour Windows 10 et Microsoft 365 Apps pour Enterprise à tout moment une fois le processus d’installation terminé. Notamment :

| Fonctionnalité | Description |
| ------ | ------ |
| Windows 10 de langue | <ul><li>Langue d’affichage</li><li>Langue du clavier</li><ul> |
| Microsoft 365 Apps des fonctionnalités Enterprise langue | <ul><li>Langue d’affichage</li><li>Outils de preuve et de authoring</li></ul> |

Pour rendre les [langues](#supported-languages) Microsoft 365 Apps Enterprise prise en charge disponibles pour vos utilisateurs, ajoutez-les au groupe Espace de travail **Office-Language_Packs** moderne. Les langues seront disponibles dans le Portail d'entreprise Intune.

## <a name="supported-languages"></a>Langues prises en charge

Pour les nouveaux appareils, votre fabricant doit fournir des images d’appareil qui incluent les langues dont vous avez besoin. Si l’image de votre fabricant inclut des langues qui ne sont pas incluses dans la liste des langues prise en charge, l’appareil est toujours pris en charge par le service.

Si vous reutilisez des appareils existants, vous devrez peut-être travailler avec votre représentant de compte Microsoft pour obtenir les images appropriées. Pour plus d’informations, voir [Images d’appareil](../service-description/device-images.md).

[L’image universelle](../service-description/device-images.md#universal-image) fournie par Microsoft Manged Desktop inclut ces langues et pour Windows 10 :

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

> [!NOTE]
> Microsoft 365 Apps pour Enterprise peut être prise en charge d’une liste légèrement différente.

Si vos utilisateurs ont besoin d’une langue autre que celle répertoriée ici, déposez une demande de [support](../working-with-managed-desktop/admin-support.md) à l’aide du [portail d’administration](access-admin-portal.md).

## <a name="languages-for-support-and-operations"></a>Langues pour la prise en charge et les opérations

### <a name="user-support"></a>Support pour les utilisateurs

Microsoft Manged Desktop ne fournit une prise en charge qu’en anglais. Si les utilisateurs choisissent une autre langue dans l’application Aide, ils obtiennent le support des canaux de support microsoft généraux, au lieu d’être directement Microsoft Manged Desktop. Pour plus d’informations, voir [Obtenir de l’aide pour les utilisateurs](../working-with-managed-desktop/end-user-support.md).

Si vos utilisateurs ont besoin d’une prise en charge dans d’autres langues, vous devrez le fournir via des sources de support non-Microsoft ou à partir de votre propre organisation.

### <a name="admin-support-and-operations"></a>Support et opérations de l’administrateur

Microsoft Manged Desktop prise en charge de l’administrateur uniquement en anglais. Cette prise en charge inclut le portail d’administration et toutes les communications avec Microsoft Manged Desktop opérations. Vous devez supposer que toutes les interactions et interfaces liées à l’administrateur seront en anglais, sauf indication contraire.
