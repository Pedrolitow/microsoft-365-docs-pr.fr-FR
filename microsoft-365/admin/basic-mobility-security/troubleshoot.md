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
description: Essayez ces étapes pour rechercher les problèmes de mobilité et de sécurité de base
ms.openlocfilehash: c8c4fe674ff3a803659223a004e304a5779a83d7
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780719"
---
# <a name="troubleshoot-basic-mobility-and-security"></a>Résoudre les problèmes de mobilité et de sécurité de base

Si vous rencontrez des problèmes lorsque vous essayez d’inscrire un appareil dans Mobilité et sécurité de base, essayez les étapes ci-dessous pour suivre le problème. Si les étapes générales ne corrigent pas le problème, consultez l’une des sections suivantes avec des étapes spécifiques pour votre type d’appareil.

## <a name="steps-to-try-first"></a>Étapes à suivre pour essayer en premier

Pour commencer, vérifiez les points suivants :

- Assurez-vous que l’appareil n’est pas déjà inscrit auprès d’un autre fournisseur de gestion des appareils mobiles, tel que Intune.

- Assurez-vous que l’appareil est défini sur la date et l’heure correctes.

- Basculez vers un autre réseau WIFI ou cellulaire sur l’appareil.

- Pour les appareils Android ou iOS, désinstallez et réinstallez l’application Portail d'entreprise Intune sur l’appareil. 

## <a name="ios-phone-or-tablet"></a>Téléphone ou tablette iOS

- Vérifiez que vous avez configuré un certificat APNs. Pour plus d’informations, consultez [Créer un certificat APNs pour les appareils iOS](create-an-apns-certificate-for-ios-devices.md).

- Dans **Paramètres** >  **GeneralProfile** >  **(ou Gestion des appareils),** assurez-vous qu’un profil de gestion n’est pas déjà installé. Si c’est le cas, supprimez-le.

- Si vous voyez le message d’erreur « L’appareil n’a pas pu s’inscrire », connectez-vous à Microsoft 365 et assurez-vous qu’une licence incluant Exchange Online a été attribuée à l’utilisateur connecté à l’appareil.

- Si vous voyez le message d’erreur « Le profil n’a pas pu être installé », essayez l’une des opérations suivantes :

    - Assurez-vous que Safari est le navigateur par défaut sur l’appareil et que les cookies ne sont pas désactivés.

    - Redémarrez l’appareil, puis accédez à portal.manage.microsoft.com. Connectez-vous avec votre ID d’utilisateur et votre mot de passe Microsoft 365 et tentez d’installer le profil manuellement.

## <a name="windows-rt"></a>Windows RT

- Assurez-vous que votre domaine est configuré dans Microsoft 365 pour fonctionner avec la mobilité et la sécurité de base. Pour plus d’informations, consultez [Configurer la mobilité et la sécurité de base](set-up.md).
    
- Assurez-vous que l’utilisateur choisit **Activer** plutôt **que joindre.**

## <a name="windows-10-pc"></a>PC Windows 10

- Assurez-vous que votre domaine est configuré dans Microsoft 365 pour fonctionner avec la mobilité et la sécurité de base. Pour plus d’informations, consultez [Configurer la mobilité et la sécurité de base](set-up.md).
    
- Sauf si vous avez Azure Active Directory Premium, assurez-vous que l’utilisateur choisit **l’inscription dans Gestion des appareils uniquement** au lieu de choisir **Connecter**.

## <a name="android-phone-or-tablet"></a>Téléphone ou tablette Android

- Vérifiez que l’appareil exécute Android.

- Vérifiez que Chrome est à jour et qu’il est défini comme navigateur par défaut.

- Si vous voyez le message d’erreur « Nous n’avons pas pu inscrire cet appareil », connectez-vous à Microsoft 365 et assurez-vous qu’une licence incluant Exchange Online a été attribuée à l’utilisateur connecté à l’appareil.

- Vérifiez la zone de notification sur l’appareil pour voir si des actions de l’utilisateur final sont en attente et, le cas échéant, effectuez les actions.