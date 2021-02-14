---
title: Mineurs et acquisition de modules dans le Store
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
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
ms.openlocfilehash: a738e22a0ac0b995c8e44fcf4cc5a2eb47375be5
ms.sourcegitcommit: 555d756c69ac9031d1fb928f2e1f9750beede066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "47306550"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>Mineurs et acquisition de modules dans le Store

Le Règlement général sur la protection des données (R GDPR) est une réglementation de l’Union européenne qui entre en vigueur le 25 mai 2018. Il accorde aux utilisateurs des droits et une protection de leurs données. L’un des aspects du R GDPR est que les mineurs ne peuvent pas avoir leurs données personnelles envoyées aux parties que leur parent ou leur guardian n’a pas approuvées. L’âge spécifique défini comme mineur dépend de la région où se trouve la personne.
  
Les régions qui ont des réglementations légales sur le consentement parental sont les États-Unis, la Corée du Sud, le Royaume-Uni et l’Union européenne. Pour ces régions, une mineure sera bloquée (via Azure Active Directory) pour obtenir de nouveaux modules office à partir du Windows Store et l’exécution de ceux qui ont été acquis précédemment. Pour les pays sans réglementation statutaire, il n’y aura aucune restriction de téléchargement.
  
Un utilisateur est déterminé comme mineur en fonction des données spécifiées dans Azure Active Directory. L’administrateur de l’organisation est responsable de la déclaration du groupe d’âge légal et du consentement parental de cet utilisateur.
  
Si le parent/guardian consent à un mineur à l’aide d’un add-In spécifique, l’administrateur de l’organisation peut utiliser le déploiement centralisé pour déployer ce module sur tous les mineurs qui ont le consentement.
  
Pour être conforme au R GDPR pour les mineurs, vous devez vous assurer que l’une des builds suivantes d’Office est déployée dans votre établissement scolaire/organisation.
 
 **Pour Word, Excel, PowerPoint et Project**: 

|**Plateforme** <br/> |**Numéro de build** <br/> |
|:-----|:-----|
|Applications Microsoft 365 pour les entreprises (canal actuel)  <br/> |9001.2138   <br/> |
|Applications Microsoft 365 pour les entreprises (canal d’entreprise semi-annuel)  <br/> |8431.2159  <br/> |
|Office 2016 pour Windows  <br/> |16.0.4672.1000  <br/> |
|Office 2013 pour Windows  <br/> |15.0.5023.1000  <br/> |
|Office 2016 pour Mac  <br/> |16.11.18020200  <br/> |
|Office pour le web  <br/> |S/O  <br/> |
   
 **Pour Outlook**: 
  
|**Plateforme** <br/> |**Numéro de build** <br/> |
|:-----|:-----|
|Outlook 2016 pour Windows (MSI)  <br/> |Build No TBD  <br/> |
|Outlook 2016 pour Windows (C2R)  <br/> |16.0.9323.1000  <br/> |
|Office 2016 pour Mac  <br/> |16.0.9318.1000  <br/> |
|Outlook Mobile pour iOS  <br/> |2.75.0  <br/> |
|Outlook Mobile pour Android  <br/> |2.2.145  <br/> |
|Outlook.com  <br/> |S/O  <br/> |

 **Conditions requises pour Office 2013**
  
Word, Excel et PowerPoint 2013 pour Windows 2013 ront les mêmes contrôles mineurs si la bibliothèque d’authentification Active Directory (ADAL) est activée. Il existe deux options de conformité, comme expliqué ci-après.
  
- **Activer ADAL**. Cet article explique comment activer ADAL pour Office 2013 : utilisation de [l’authentification moderne Microsoft 365 avec les clients Office.](https://docs.microsoft.com/microsoft-365/enterprise/modern-auth-for-office-2013-and-2016)<br/>Vous devez également définir les clés de Registre pour activer ADAL, comme expliqué dans Activer l’authentification moderne pour [Office 2013 sur les appareils Windows.](../security-and-compliance/enable-modern-authentication.md)<br/>En outre, vous devez installer les mises à jour d’avril suivantes pour Office 2013 :
    
  - [Description de la mise à jour de sécurité pour Office 2013 : 10 avril 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)
    
  - [3 avril 2018, mise à jour pour Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)
    
- **N’activez pas ADAL**. Si vous ne parvenez pas à activer ADAL dans Office 2013, il est recommandé d’utiliser une stratégie de groupe pour désactiver le Store pour les clients Office. Des informations sur la façon de désactiver les paramètres de l’application pour Office sont disponibles [ici.](https://technet.microsoft.com/library/cc178992.aspx)

## <a name="related-articles"></a>Articles connexes

[Déployer des compléments dans le centre d’administration](https://docs.microsoft.com/microsoft-365/admin/manage/manage-deployment-of-add-ins)

[Gérer des compléments dans le centre d’administration](https://docs.microsoft.com/microsoft-365/admin/manage/manage-addins-in-the-admin-center)
    
