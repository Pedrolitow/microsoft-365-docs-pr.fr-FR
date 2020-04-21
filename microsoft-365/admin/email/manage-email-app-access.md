---
title: Gérer l’accès aux applications de messagerie dans le centre d’administration Microsoft 365
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- Adm_NonTOC
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
ms.assetid: d00b6b83-1f14-4e9c-a2c5-dbd9a92816f4
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment choisir les applications mobiles que les utilisateurs peuvent utiliser pour accéder à la messagerie, au calendrier et aux contacts.
ms.openlocfilehash: 8627a31f7ec5e3c14b853618bb0383ecc58597cc
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43628806"
---
# <a name="manage-email-app-access-in-the-microsoft-365-admin-center"></a>Gérer l’accès aux applications de messagerie dans le centre d’administration Microsoft 365

Utilisez les paramètres d’accès aux courriers électroniques mobiles pour choisir les applications mobiles que les membres de votre organisation peuvent utiliser pour accéder à leur compte professionnel ou scolaire afin d’accéder à la messagerie, au calendrier et aux contacts.
  
> [!IMPORTANT]
> Votre organisation aura accès à ce paramètre, sauf si vous utilisez Microsoft Intune ou si vous avez configuré les paramètres de gestion des appareils mobiles dans le centre d’administration Exchange. 
  
## <a name="manage-email-app-options"></a>Gérer les options de l’application de messagerie

> [!IMPORTANT]
>  Si vous n’utilisez pas cette fonctionnalité, aucune modification ne sera apportée à l’expérience de vos utilisateurs. Ils pourront utiliser n’importe quelle application de messagerie mobile pour accéder à leur compte professionnel ou scolaire pour le courrier électronique, le calendrier et les contacts à partir de leur appareil mobile. 
    
1. Dans le centre d’administration, cliquez sur la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Services &amp; Compléments</a>. 

2. Sur la page **options d’accès au courrier mobile** , activez la case à cocher, puis choisissez la manière dont les utilisateurs de votre organisation utilisent les applications de messagerie sur leurs appareils :
  
Choisissez l’option permettant de définir la façon dont les utilisateurs de votre organisation accèdent à leur compte professionnel ou scolaire à partir de leurs appareils mobiles.
  
- **Outlook uniquement** : les utilisateurs de votre organisation doivent utiliser l’application Outlook pour Android ou Outlook pour iOS sur leur appareil mobile. 
    
- **Toute application de messagerie** -tous les utilisateurs de votre organisation seront invités à utiliser Outlook, mais ils peuvent choisir d’utiliser n’importe quelle application de messagerie. 
    
- **Toute application de messagerie** : les nouveaux utilisateurs ou périphériques de votre organisation seront invités une fois à utiliser Outlook, mais ils peuvent choisir d’utiliser n’importe quelle application de messagerie. 
    
Pour plus d’informations, consultez les [options permettant d’accéder à la messagerie électronique à partir de votre appareil mobile](access-email-from-a-mobile-device.md).
  
## <a name="new-user-or-device-is-activated-in-your-organization"></a>Un nouvel utilisateur ou appareil est activé dans votre organisation

Dès qu’un utilisateur de votre organisation ajoute son courrier électronique professionnel ou scolaire à une application de messagerie tierce ou à un nouveau périphérique, il reçoit un courrier électronique de **la part de Microsoft au nom de votre organisation**. Le courrier électronique leur indiquera les avantages liés à l’utilisation de l’application mobile Outlook et fournira un lien vers l’emplacement de téléchargement. Vos utilisateurs peuvent alors choisir de continuer à utiliser l’application tierce ou d’utiliser l’application mobile Outlook. Pendant les 24 heures suivant la réception de ce message électronique, son appareil est en quarantaine, et les données de messagerie, de calendrier et de contact ne sont pas mises à jour. S’ils choisissent d’utiliser l’application mobile Outlook, l’application tierce reste mise en quarantaine et les données ne sont synchronisées qu’avec l’application mobile Outlook. S’ils décident de continuer à utiliser l’application tierce, les données commenceront à être synchronisées instantanément. Si aucune action n’est effectuée pendant les premières 24 heures, le courrier électronique est supprimé de sa boîte de réception et les données commencent à être synchronisées automatiquement à partir du serveur.
  
## <a name="previously-configured-users-in-your-organization"></a>Utilisateurs configurés précédemment dans votre organisation

Si vous décidez de recommander Outlook à tous les membres de votre organisation, outre l’expérience décrite ci-dessus pour les nouveaux utilisateurs, les utilisateurs qui ont précédemment connecté leur compte de messagerie professionnel ou scolaire à une application tierce recevront un courrier électronique de **Microsoft au nom de votre organisation dans les** 48 heures suivant l’activation de ce paramètre. Le courrier électronique leur indiquera les avantages liés à l’utilisation de l’application mobile Outlook et fournira un lien vers l’emplacement de téléchargement. Vos utilisateurs peuvent alors choisir de continuer à utiliser l’application tierce ou d’utiliser l’application mobile Outlook. Pendant les 24 heures suivant la réception de ce message électronique, son appareil est en quarantaine, et les données de messagerie, de calendrier et de contact ne sont pas mises à jour. S’ils choisissent d’utiliser l’application mobile Outlook, l’application tierce reste mise en quarantaine et les données ne sont synchronisées qu’avec l’application mobile Outlook. S’ils décident de continuer à utiliser l’application tierce, les données commenceront à être synchronisées instantanément. Si aucune action n’est effectuée pendant les premières 24 heures, le courrier électronique est supprimé de sa boîte de réception et les données commencent à être synchronisées automatiquement à partir du serveur. 
  

