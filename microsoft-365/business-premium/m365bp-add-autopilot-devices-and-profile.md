---
title: Utiliser ce guide pas à pas pour ajouter des appareils et un profil Autopilot
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.localizationpriority: high
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: be5b6d90-3344-4c5e-bf40-5733eb845beb
description: Découvrez comment utiliser Windows AutoPilot pour configurer de nouveaux appareils Windows 10 pour votre entreprise afin qu’ils soient prêts à être utilisés par les employés.
ms.openlocfilehash: 6bedb478d0ef8f961c7b75eb7013b2b5e51ce2c9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092606"
---
# <a name="use-this-step-by-step-guide-to-add-autopilot-devices-and-profile"></a>Utiliser ce guide pas à pas pour ajouter des appareils et un profil Autopilot

> [!NOTE]
> Microsoft Defender pour les PME est déployée pour les clients Microsoft 365 Business Premium, à compter du 1er mars 2022. Cette offre fournit des fonctionnalités de sécurité supplémentaires pour les appareils. [Vue d’ensemble de Microsoft Defender pour les PME](../security/defender-business/mdb-overview.md).

Vous pouvez utiliser Windows AutoPilot pour configurer de **nouveaux** appareils Windows 10 pour votre entreprise afin qu'ils soient prêts à être utilisés par vos employés dès que vous les leur attribuez.
  
## <a name="device-requirements"></a>Configuration requise de l’appareil

Les appareils doivent respecter ces exigences :
  
- Windows 10, version 1703 ou supérieure

- Nouveaux appareils qui ne sont pas issus d'une expérience Windows prête à l'emploi.

## <a name="use-the-setup-guide-to-add-devices-and-profiles"></a>Utiliser le guide de configuration pour ajouter des appareils et des profils

Si vous n'avez pas encore créé de groupes d'appareils et de profils, la meilleure façon de commencer consiste à utiliser le guide pas à pas, mais vous pouvez également [ajouter des appareils Autopilot](m365bp-create-and-edit-autopilot-devices.md) et leur [attribuer des profils](../admin/devices/create-and-edit-autopilot-profiles.md) sans utiliser le guide.
  
1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

1. Dans le volet de navigation de gauche, choisissez **Appareils** \> **AutoPilot**.

    ![Dans le Centre d’administration, choisissez les appareils, puis AutoPilot.](../media/AutoPilot.png)
  
1. Sur la page **Autopilot**, cliquez ou appuyez sur **Guide de démarrage**.

    ![Click Start guide for step-by-step instructions for Autopilot.](../media/31662655-d1e6-437d-87ea-c0dec5da56f7.png)
  
1. Sur la page **Charger un fichier .csv avec une liste d'appareils**, recherchez l'emplacement où vous avez préparé le fichier .csv, puis cliquez sur **Ouvrir** \> **Suivant**. Le fichier doit avoir trois en-têtes :

    - Colonne A : Numéro de série de l'appareil
    - Colonne B : ID de produit Windows
    - Colonne C : Hachage du matériel

Vous pouvez obtenir ces informations à partir de votre fournisseur de matériel ou vous pouvez utiliser le [script Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) qui générera un fichier CSV.

Pour plus d'informations, voir [Fichier CSV de liste d'appareils](../admin/misc/device-list.md). Vous pouvez également télécharger un exemple de fichier sur la page **Charger un fichier .csv avec la liste des appareils**.

> [!NOTE]
> Ce script utilise WMI pour récupérer les propriétés nécessaires pour qu’un client inscrive un appareil auprès de Windows Autopilot. Notez qu’il est normal que le fichier CSV résultant ne collecte pas de valeur d’ID de produit Windows (PKID), car cela n’est pas nécessaire pour inscrire un appareil et que le PKID étant NULL dans le CSV de sortie est tout à fait correct. Seuls le numéro de série et le hachage matériel sont renseignés.

4. Sur la page **Attribuer un profil**, vous pouvez choisir un profil existant ou en créer un. Si vous n'en avez pas encore, vous êtes invité à en créer un.

    Un proﬁl est un ensemble de paramètres qui peuvent être appliqués à un seul appareil ou à un groupe d'appareils.

    Les fonctionnalités par défaut sont obligatoires et seront définies automatiquement. Les fonctionnalités par défaut sont :

    - Ignorer l'inscription Cortana, OneDrive et OEM.

    - Créez une expérience de connexion avec l'identité de votre entreprise.

    - Connecter vos appareils à des comptes Azure Active Directory et les inscrire automatiquement pour qu’ils soient gérés par Microsoft 365 Business Premium.

    Pour plus d’informations, consultez [À propos des paramètres de profil AutoPilot](m365bp-autopilot-profile-settings.md).

5. Les autres paramètres sont **Ignorer les paramètres de confidentialité** et **Ne pas autoriser l'utilisateur à devenir administrateur local**. Ils sont tous les deux définis sur **Désactivé** par défaut.

    Sélectionnez **Suivant**.

6. **Vous avez terminé** indique que le profil que vous avez créé (ou choisi) sera appliqué au groupe d'appareils que vous avez créé en chargeant la liste d'appareils. Ces paramètres seront appliqués lors de la prochaine connexion des utilisateurs de l'appareil. Choisissez **Fermer**.

## <a name="related-content"></a>Contenu connexe

- [À propos des paramètres du profil AutoPilot](../business-premium/m365bp-autopilot-profile-settings.md) (article)\
- [Options de protection de vos appareils et données d’application](../admin/devices/choose-device-security.md) (article)
- [Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)
