---
title: Résoudre les problèmes de sécurité et de mobilité de base
f1.keywords: NOCSH
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
ms.custom: AdminSurgePortfolio
description: Suivez ces étapes pour suivre les problèmes de sécurité et de mobilité de base
ms.openlocfilehash: 43e7533e598f769dd5f2bcae28c4252f96a9be76
ms.sourcegitcommit: aeb94601a81db3ead8610c2f36cff30eb9fe10e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "47430155"
---
# <a name="troubleshoot-basic-mobility-and-security"></a>Résoudre les problèmes de sécurité et de mobilité de base

Si vous rencontrez des problèmes lorsque vous essayez d’inscrire un appareil dans le cadre de la sécurité et de la mobilité de base, essayez les étapes suivantes pour suivre le problème. Si la procédure générale ne résout pas le problème, reportez-vous à l’une des sections suivantes avec des étapes spécifiques pour votre type d’appareil.

## <a name="steps-to-try-first"></a>Étapes à essayer en premier lieu

Pour commencer, vérifiez les points suivants :

- Assurez-vous que l’appareil n’est pas déjà associé à un autre fournisseur de gestion des appareils mobiles, comme Intune.
    
- Assurez-vous que l’appareil est défini sur la date et l’heure correctes.
    
- Basculez vers un autre réseau Wi-Fi ou cellulaire sur l’appareil.
    
- Pour les appareils Android ou iOS, désinstallez et réinstallez l’application portail d’entreprise Intune sur l’appareil. 

## <a name="ios-phone-or-tablet"></a>téléphone ou tablette iOS

- Assurez-vous que vous avez configuré un certificat APNs. Pour plus d’informations, consultez la rubrique [créer un certificat APNs pour les appareils iOS](create-an-apns-certificate-for-ios-devices.md).
    
- Dans **paramètres**   >  **généraux**   >  **profil (ou gestion des appareils)**, assurez-vous qu’aucun profil de gestion n’est déjà installé. Si c’est le cas, supprimez-le.
    
- Si vous voyez le message d’erreur « Échec de l’inscription de l’appareil », connectez-vous à Microsoft 365 et assurez-vous qu’une licence qui inclut Exchange Online a été affectée à l’utilisateur connecté à l’appareil.
    
- Si vous voyez le message d’erreur « Échec de l’installation du profil », effectuez l’une des opérations suivantes :
    
    - Assurez-vous que Safari est le navigateur par défaut sur l’appareil et que les cookies ne sont pas désactivés.
    
    - Redémarrez l’appareil, puis accédez à portal.manage.microsoft.com. Connectez-vous avec votre ID d’utilisateur et votre mot de passe Microsoft 365, puis essayez d’installer le profil manuellement.    

## <a name="windows-rt"></a>Windows RT

- Assurez-vous que votre domaine est configuré dans Microsoft 365 pour fonctionner avec la sécurité et la mobilité de base. Pour plus d’informations, consultez la rubrique [Set Up Basic Mobility and Security](set-up.md).
    
- Assurez-vous que l’utilisateur choisit **activer**   plutôt que de **joindre**.    

## <a name="windows-10-pc"></a>PC Windows 10

- Assurez-vous que votre domaine est configuré dans Microsoft 365 pour fonctionner avec la sécurité et la mobilité de base. Pour plus d’informations, consultez la rubrique [Set Up Basic Mobility and Security](set-up.md).
    
- À moins d’avoir Azure Active Directory Premium, assurez-vous que l’utilisateur choisit **inscrire dans la gestion des appareils uniquement**   plutôt que de choisir **connecter**.

## <a name="android-phone-or-tablet"></a>Téléphone Android ou tablette

- Assurez-vous que l’appareil exécute Android 4,4 ou une version ultérieure.
    
- Assurez-vous que Chrome est à jour et qu’il est défini en tant que navigateur par défaut.
    
- Si vous voyez le message d’erreur « nous n’avons pas pu inscrire ce périphérique », connectez-vous à Microsoft 365 et assurez-vous qu’une licence qui inclut Exchange Online a été affectée à l’utilisateur connecté à l’appareil.
    
- Vérifiez la zone de notification sur l’appareil pour voir si des actions de l’utilisateur final requises sont en attente et, le cas échéant, effectuez les actions.