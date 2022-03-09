---
title: Résoudre les problèmes de mobilité et de sécurité de base
f1.keywords: NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
description: Suivez ces étapes pour suivre les problèmes de mobilité et de sécurité de base
ms.openlocfilehash: 2ac25e36fced24e5b50e7e89d36dae3e842fda04
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400362"
---
# <a name="troubleshoot-basic-mobility-and-security"></a>Résoudre les problèmes de mobilité et de sécurité de base

Si vous êtes face à des problèmes lorsque vous essayez d’inscrire un appareil dans Basic Mobility and Security, suivez les étapes ci-après pour le suivre. Si les étapes générales ne corrigent pas le problème, consultez l’une des sections suivantes avec des étapes spécifiques pour votre type d’appareil.

## <a name="steps-to-try-first"></a>Étapes à suivre pour essayer en premier

Pour commencer, vérifiez ce qui suit :

- Assurez-vous que l’appareil n’est pas déjà inscrit auprès d’un autre fournisseur de gestion d’appareils mobiles, tel qu’Intune.

- Assurez-vous que la date et l’heure de l’appareil sont correctes.

- Basculez vers un autre réseau WIFI ou cellulaire sur l’appareil.

- Pour les appareils Android ou iOS, désinstallez et réinstallez l’Portail d'entreprise Intune sur l’appareil. 

## <a name="ios-phone-or-tablet"></a>Téléphone ou tablette iOS

- Assurez-vous que vous avez bien installé un certificat APNs. Pour plus d’informations, voir [Créer un certificat APNs pour les appareils iOS](create-an-apns-certificate-for-ios-devices.md).

- Dans  **Paramètres** >  **GeneralProfile** >  **(ou** Gestion des appareils), assurez-vous qu’un profil de gestion n’est pas déjà installé. Si c’est le cas, supprimez-le.

- Si le message d’erreur « L’appareil n’a pas pu s’inscrire », connectez-vous à Microsoft 365 et assurez-vous qu’une licence incluant Exchange Online a été attribuée à l’utilisateur connecté à l’appareil.

- Si vous voyez le message d’erreur « Échec de l’installation du profil », essayez l’une des procédures suivantes :

    - Assurez-vous que Safari est le navigateur par défaut sur l’appareil et que les cookies ne sont pas désactivés.

    - Redémarrez l’appareil, puis accédez à portal.manage.microsoft.com. Connectez-vous avec votre Microsoft 365'utilisateur et votre mot de passe, puis essayez d’installer le profil manuellement.

## <a name="windows-rt"></a>Windows RT

- Assurez-vous que votre domaine est Microsoft 365 pour fonctionner avec basic Mobility and Security. Pour plus d’informations, voir [Configurer la mobilité et la sécurité de base](set-up.md).
    
- Assurez-vous que l’utilisateur  **choisitTurn Onrather**  plutôt  **queJoin**.

## <a name="windows-10-pc"></a>Windows 10 PC

- Assurez-vous que votre domaine est Microsoft 365 pour fonctionner avec basic Mobility and Security. Pour plus d’informations, voir [Configurer la mobilité et la sécurité de base](set-up.md).
    
- Sauf si vous avez Azure Active Directory Premium, assurez-vous que l’utilisateur ne choisitEnroll  **dans**  la gestion des appareils qu’en choisissant  **Connecter**.

## <a name="android-phone-or-tablet"></a>Téléphone ou tablette Android

- Assurez-vous que l’appareil exécute Android.

- Assurez-vous que Chrome est à jour et qu’il est le navigateur par défaut.

- Si le message d’erreur « Nous n’avons pas pu inscrire cet appareil » s’affiche, connectez-vous à Microsoft 365 et assurez-vous qu’une licence incluant Exchange Online a été attribuée à l’utilisateur connecté à l’appareil.

- Vérifiez la zone de notification sur l’appareil pour voir si des actions de l’utilisateur final requises sont en attente et, si c’est le cas, effectuer les actions.