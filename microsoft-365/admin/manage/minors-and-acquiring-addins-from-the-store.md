---
title: Mineurs et acquisition de modules dans le Store
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
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Découvrez les réglementations du Règlement général sur la protection des données (R GDPR) qui régissent les données personnelles des mineurs.
ms.openlocfilehash: 7ec9e54865ce21a55dc2bd5bf777e293f105c51e99625bf95ebc1a6dabb7ee22
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53824982"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>Mineurs et acquisition de modules dans le Store

Le Règlement général sur la protection des données (R GDPR) est une réglementation de l’Union européenne qui entre en vigueur le 25 mai 2018. Il accorde aux utilisateurs des droits et une protection de leurs données. L’un des aspects du R GDPR est que les mineurs ne peuvent pas avoir leurs données personnelles envoyées aux parties que leur parent ou leur guardian n’a pas approuvées. L’âge spécifique défini comme mineur dépend de la région où se trouve la personne.
  
Les régions qui ont des réglementations légales sur le consentement parental sont les États-Unis, la Corée du Sud, le Royaume-Uni et l’Union européenne. Pour ces régions, une mineure sera bloquée (via Azure Active Directory) pour obtenir de nouveaux Office à partir du Store et l’exécution de ceux qui ont été acquis précédemment. Pour les pays sans réglementation statutaire, il n’y aura aucune restriction de téléchargement.
  
Un utilisateur est déterminé comme mineur en fonction des données spécifiées dans Azure Active Directory. L’administrateur de l’organisation est responsable de la déclaration du groupe d’âge légal et du consentement parental de cet utilisateur.
  
Si le parent/guardian consent à un mineur à l’aide d’un add-In spécifique, l’administrateur de l’organisation peut utiliser le déploiement centralisé pour déployer ce module sur tous les mineurs qui ont le consentement.
  
Pour être conforme au R GDPR pour les mineurs, vous devez vous assurer que l’une des builds de Office suivantes est déployée dans votre établissement scolaire/organisation.
 
 **Pour Word, Excel, PowerPoint et Project**: 

|**Plateforme** <br/> |**Numéro de build** <br/> |
|:-----|:-----|
|Applications Microsoft 365 pour les grandes entreprises (canal actuel)  <br/> |9001.2138   <br/> |
|Applications Microsoft 365 pour les grandes entreprises (Canal semi-annuel Enterprise))  <br/> |8431.2159  <br/> |
|Office 2016 pour Windows  <br/> |16.0.4672.1000  <br/> |
|Office 2013 pour Windows  <br/> |15.0.5023.1000  <br/> |
|Office 2016 pour Mac  <br/> |16.11.18020200  <br/> |
|Office pour le web  <br/> |N/A  <br/> |
   
 **Pour Outlook**: 
  
|**Plateforme** <br/> |**Numéro de build** <br/> |
|:-----|:-----|
|Outlook 2016 for Windows (MSI)  <br/> |Build No TBD  <br/> |
|Outlook 2016 for Windows (C2R)  <br/> |16.0.9323.1000  <br/> |
|Office 2016 pour Mac  <br/> |16.0.9318.1000  <br/> |
|Outlook mobile pour iOS  <br/> |2.75.0  <br/> |
|Outlook mobile pour Android  <br/> |2.2.145  <br/> |
|Outlook.com  <br/> |N/A  <br/> |

 **Office 2013**
  
Word, Excel et PowerPoint 2013 pour Windows 2013 ront les mêmes contrôles de mineurs si la bibliothèque d’authentification Active Directory (ADAL) est activée. Il existe deux options de conformité, comme expliqué ci-après.
  
- **Activer ADAL**. Cet article explique comment activer ADAL pour Office 2013 : utilisation de l’authentification moderne Microsoft 365 avec Office [clients.](../../enterprise/modern-auth-for-office-2013-and-2016.md)<br/>Vous devez également définir les clés de Registre pour activer ADAL, comme expliqué dans Activer l’authentification moderne [pour Office 2013](../security-and-compliance/enable-modern-authentication.md)sur Windows appareils.<br/>En outre, vous devez installer les mises à jour d’avril suivantes Office 2013 :
    
  - [Description de la mise à jour de sécurité Office 2013 : 10 avril 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)
    
  - [3 avril 2018, mise à jour Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)
    
- **N’activez pas ADAL**. Si vous ne parvenez pas à activer ADAL dans Office 2013, il est recommandé d’utiliser la stratégie de groupe pour désactiver le Store pour les clients Office client. Des informations sur la façon de désactiver l’application pour Office paramètres sont disponibles [ici.](/previous-versions/office/office-2013-resource-kit/cc178992(v=office.15))

## <a name="related-articles"></a>Articles connexes

[Déployer des compléments dans le centre d’administration](./manage-deployment-of-add-ins.md)

[Gérer des compléments dans le centre d’administration](./manage-addins-in-the-admin-center.md)
