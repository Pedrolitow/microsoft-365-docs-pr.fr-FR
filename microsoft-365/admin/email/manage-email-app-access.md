---
title: Gérer l’accès aux applications de messagerie dans Centre d'administration Microsoft 365
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
ms.assetid: d00b6b83-1f14-4e9c-a2c5-dbd9a92816f4
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment choisir les applications mobiles que les utilisateurs peuvent utiliser pour accéder à la messagerie, au calendrier et aux contacts.
ms.openlocfilehash: 5f5a96a0ac44757cfe168db87deb494019759c36
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780234"
---
# <a name="manage-email-app-access-in-the-microsoft-365-admin-center"></a>Gérer l’accès aux applications de messagerie dans le Centre d'administration Microsoft 365

Utilisez les paramètres d’accès aux e-mails mobiles pour choisir les applications mobiles que les membres de votre organisation peuvent utiliser pour accéder à leur compte professionnel ou scolaire pour accéder à la messagerie, au calendrier et aux contacts.
  
> [!IMPORTANT]
> Votre organisation aura accès à ce paramètre, sauf si vous utilisez Microsoft Intune ou si vous avez configuré les paramètres de gestion des appareils mobiles dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a>.
  
## <a name="manage-email-app-options"></a>Gérer les options de l’application de messagerie

> [!IMPORTANT]
> Si vous n’utilisez pas cette fonctionnalité, aucune modification ne sera apportée à l’expérience de vos utilisateurs. Ils pourront utiliser n’importe quelle application de messagerie mobile pour accéder à leur compte professionnel ou scolaire pour la messagerie, le calendrier et les contacts à partir de leur appareil mobile.

1. Dans le centre d’administration, cliquez sur la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Services &amp; Compléments</a>.

2. Dans la page **Options d’accès à la messagerie mobile** , activez la case à cocher, puis choisissez comment les utilisateurs de votre organisation utilisent les applications de messagerie sur leurs appareils :
  
Choisissez l’option permettant de définir la façon dont les utilisateurs de votre organisation accèdent à leur compte professionnel ou scolaire à partir de leurs appareils mobiles
  
- **Outlook uniquement** : les utilisateurs de votre organisation doivent utiliser le Outlook pour Android ou Outlook pour l’application iOS sur leur appareil mobile.

- **N’importe quelle application de messagerie :** tous les utilisateurs de votre organisation sont invités à utiliser Outlook, mais ils peuvent choisir d’utiliser n’importe quelle application de messagerie.

- **Toute application e-mail** - les nouveaux utilisateurs ou appareils de votre organisation seront invités une fois à utiliser Outlook, mais ils peuvent choisir d’utiliser n’importe quelle application de messagerie.

Pour plus d’informations, consultez [Options d’accès à la messagerie à partir de votre appareil mobile](access-email-from-a-mobile-device.md).
  
## <a name="new-user-or-device-is-activated-in-your-organization"></a>Un nouvel utilisateur ou un nouvel appareil est activé dans votre organisation

Dès qu’un utilisateur de votre organisation ajoute son courrier professionnel ou scolaire à une application de messagerie tierce ou à un nouvel appareil, il reçoit un e-mail de **Microsoft au nom de votre organisation**. L’e-mail leur indiquera les avantages de l’utilisation de l’application mobile Outlook et fournira un lien vers l’emplacement de téléchargement. Vos utilisateurs peuvent ensuite choisir de continuer à utiliser l’application tierce ou d’utiliser l’application mobile Outlook. Au cours des 24 heures qui suivent la réception de cet e-mail par l’utilisateur, son appareil est mis en quarantaine et les données de courrier, de calendrier et de contact ne sont pas mises à jour. S’ils choisissent d’utiliser l’application mobile Outlook, l’application tierce reste en quarantaine et les données se synchronisent uniquement avec l’application mobile Outlook. S’ils décident de continuer à utiliser l’application tierce, les données commencent à se synchroniser instantanément. Si aucune action n’est effectuée au cours des premières 24 heures, l’e-mail est supprimé de sa boîte de réception et les données commencent à se synchroniser automatiquement à partir du serveur.
  
## <a name="previously-configured-users-in-your-organization"></a>Utilisateurs précédemment configurés dans votre organisation

Si vous décidez de recommander Outlook à tous les membres de votre organisation, en plus de l’expérience décrite ci-dessus pour les nouveaux utilisateurs, les utilisateurs qui ont précédemment connecté leur compte de messagerie professionnel ou scolaire à une application tierce recevront un e-mail de **Microsoft au nom de votre organisation** dans les 48 heures suivant l’activation de ce paramètre. L’e-mail leur indiquera les avantages de l’utilisation de l’application mobile Outlook et fournira un lien vers l’emplacement de téléchargement. Vos utilisateurs peuvent ensuite choisir de continuer à utiliser l’application tierce ou d’utiliser l’application mobile Outlook. Au cours des 24 heures qui suivent la réception de cet e-mail par l’utilisateur, son appareil est mis en quarantaine et les données de courrier, de calendrier et de contact ne sont pas mises à jour. S’ils choisissent d’utiliser l’application mobile Outlook, l’application tierce reste en quarantaine et les données se synchronisent uniquement avec l’application mobile Outlook. S’ils décident de continuer à utiliser l’application tierce, les données commencent à se synchroniser instantanément. Si aucune action n’est effectuée au cours des premières 24 heures, l’e-mail est supprimé de sa boîte de réception et les données commencent à se synchroniser automatiquement à partir du serveur.
