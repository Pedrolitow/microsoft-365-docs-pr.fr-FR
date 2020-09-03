---
title: Réinitialiser un appareil mobile dans la sécurité et la mobilité de base
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: Utilisez la sécurité et la mobilité de base intégrées pour supprimer les informations des périphériques.
ms.openlocfilehash: 4d854c7d4d81cd0b49ec7f81a49de5478b08f049
ms.sourcegitcommit: 2179abfe0b7a8bea917eb1c1057ed3795bdf91e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "47336853"
---
# <a name="wipe-a-mobile-device-in-basic-mobility-and-security"></a>Réinitialiser un appareil mobile dans la sécurité et la mobilité de base

Vous pouvez utiliser la mobilité et la sécurité de base intégrées pour Microsoft 365 pour supprimer uniquement les informations organisationnelles, ou pour effectuer une réinitialisation en usine afin de supprimer toutes les informations d’un appareil mobile et de les restaurer aux paramètres d’usine.

## <a name="before-you-begin"></a>Avant de commencer

Les appareils mobiles peuvent stocker des informations organisationnelles sensibles et fournir un accès aux ressources Microsoft 365 de votre organisation. Pour vous aider à protéger les informations de votre organisation, vous pouvez procéder à la réinitialisation ou à la suppression des données d’entreprise :
    
- **Réinitialisation en usine**: supprime toutes les données sur l’appareil mobile d’un utilisateur, y compris les applications installées, les photos et les informations personnelles. Une fois la réinitialisation terminée, l’appareil est restauré à ses paramètres d’usine.
    
- **Supprimer les données**de l’entreprise : supprime uniquement les données de l’organisation et laisse les applications, les photos et les informations personnelles installées sur l’appareil mobile d’un utilisateur.   

- **Lorsqu’un appareil est effacé (réinitialisation ou suppression des données d’entreprise)**, l’appareil est supprimé de la liste des appareils gérés.
    
- **Réinitialiser un appareil automatiquement**: vous pouvez configurer une stratégie de sécurité et de mobilité de base qui réinitialise automatiquement un appareil une fois que l’utilisateur n’a pas tenté d’entrer le mot de passe d’appareil un certain nombre de fois. Pour ce faire, suivez les étapes décrites dans [Create Device Security Policies in Basic Mobility and Security](create-device-security-policies-in-basic-mmobility-and-security.md).
    
- **Si vous souhaitez connaître l’expérience utilisateur lors de la** réinitialisation de son appareil, consultez  [la rubrique quel est l’impact sur les utilisateurs et les appareils ?](#whats-the-user-and-device-impact).   

## <a name="wipe-a-mobile-device"></a>Réinitialiser un appareil mobile

1. Accédez au [Centre d’administration Microsoft 365](https://support.microsoft.com/office/758befc4-0888-4009-9f14-0d147402fd23).
    
2. Tapez gestion des appareils mobiles dans le champ de recherche, puis sélectionnez **gestion des appareils mobiles** dans la liste des résultats. 

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Option de gestion de l’appareil mobile secruity et de la mobilité de base":::

3. Sélectionnez **gérer les appareils**.

4. Sélectionnez l’appareil que vous voulez réinitialiser.

5. Sélectionnez **gérer**.

6. Sélectionnez le type de réinitialisation à distance que vous voulez effectuer.

    - Pour effectuer un nettoyage complet et restaurer les paramètres d’usine de l’appareil, sélectionnez **réinitialisation usine**.
    - Pour effectuer une réinitialisation sélective et supprimer uniquement les informations de l’organisation Microsoft 365, sélectionnez **Supprimer les données**de l’entreprise.
    - Pour supprimer l’appareil de votre organisation, sélectionnez **Supprimer l’appareil**.

7. Cliquez sur **Oui** pour confirmer.

## <a name="how-do-i-know-it-worked"></a>Comment puis-je savoir si elle a fonctionné ?

L’appareil mobile n’apparaît plus dans la liste des appareils gérés.

## <a name="why-would-you-want-to-wipe-a-device"></a>Pourquoi effacer un appareil ?

Réinitialiser un appareil pour les raisons suivantes :

- Les appareils mobiles tels que les smartphones et les tablettes sont de plus en plus complets. Cela signifie qu’il est plus facile pour vos utilisateurs de stocker des informations d’entreprise sensibles, telles que des communications personnelles ou confidentielles, et d’y accéder dès que vous le souhaitez. Si l’un de ces appareils mobiles est perdu ou volé, l’effacement de l’appareil peut empêcher les informations de votre organisation de se terminer de façon incorrecte.
- Lorsqu’un utilisateur quitte l’organisation à l’aide d’un appareil personnel qui est intégré à la mobilité et à la sécurité de base, vous pouvez empêcher les informations organisationnelles de passer à cet utilisateur en effectuant une réinitialisation d’usine.
- Si votre organisation fournit des appareils mobiles aux utilisateurs, vous devrez peut-être réaffecter des appareils de temps à autre. La réinitialisation d’une usine sur un appareil avant de l’affecter à un nouvel utilisateur permet de s’assurer que toutes les informations sensibles du propriétaire précédent sont supprimées.

## <a name="whats-the-user-and-device-impact"></a>Quel est l’impact sur les utilisateurs et les appareils ?

La réinitialisation est envoyée immédiatement à l’appareil mobile et l’appareil est marqué comme non conforme dans Azure Active Directory. Tandis que toutes les données sont supprimées lorsqu’un appareil est réinitialisé aux valeurs par défaut d’origine, le tableau suivant décrit le contenu qui est supprimé pour chaque type d’appareil lorsque vous supprimez des données d’entreprise.

|**Impacer le contenu**|**iOS 10 et versions ultérieures**|**Android 5 et versions ultérieures**|
|:-----|:-----|:-----|
|Les données de l’application Microsoft 365 sont effacées si l’appareil est protégé par les stratégies Intune App protection. Les applications ne sont pas supprimées. Pour les appareils qui ne sont pas protégés par les stratégies de gestion des applications mobiles (MAM), Outlook et OneDrive ne supprimeront pas les données mises en cache.<br/>**Note** Pour appliquer les stratégies de protection des applications Intune, vous devez disposer d’une licence Intune.|Oui|Oui|
|Les paramètres de stratégie appliqués par la sécurité et la mobilité de base aux appareils ne sont plus appliqués ; les utilisateurs peuvent modifier les paramètres.|Oui|Oui|
|Les profils de messagerie créés par la mobilité et la sécurité de base sont supprimés et le courrier mis en cache sur l’appareil est supprimé.|Oui|N/D|
>[!NOTE] 
>L’application portail d’entreprise est disponible dans le magasin d’applications pour iOS et le magasin de jeux pour les appareils Android.

## <a name="related-topics"></a>Voir aussi

[Configurer Mobility + Security](set-up-basic-mobility-and-security.md)