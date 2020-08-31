---
title: Mineurs et acquisition de compléments à partir du magasin
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
description: Découvrez le règlement général sur la protection des données (RGPD) qui régit les données personnelles des mineurs.
ms.openlocfilehash: a738e22a0ac0b995c8e44fcf4cc5a2eb47375be5
ms.sourcegitcommit: 555d756c69ac9031d1fb928f2e1f9750beede066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "47306550"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>Mineurs et acquisition de compléments à partir du magasin

Le règlement général sur la protection des données (RGPD) est un règlement de l’Union européenne qui devient effectif le 25 mai 2018. Il donne aux utilisateurs des droits et la protection de leurs données. L’un des aspects du RGPD est que les mineurs ne peuvent pas avoir leurs données personnelles envoyées aux parties que leur parent ou tuteur n’a pas approuvées. L’âge spécifique défini comme un mineur dépend de la région où se trouve la personne.
  
Les régions dont la réglementation statutaire est relative au consentement parental incluent les États-Unis, la Corée du Sud, le Royaume-Uni et l’Union européenne. Pour ces régions, un mineur est bloqué (via Azure Active Directory) pour obtenir les nouveaux compléments Office à partir du Store et exécuter des compléments qui ont été précédemment acquis. Pour les pays sans réglementation réglementaire, il n’y aura pas de restrictions de téléchargement.
  
Un utilisateur est considéré comme mineur en fonction des données spécifiées dans Azure Active Directory. L’administrateur de l’organisation est responsable de la déclaration du groupe d’âge légal et de l’autorisation parentale pour cet utilisateur.
  
Si le parent/tuteur est accepté par un utilisateur secondaire à l’aide d’un complément spécifique, l’administrateur de l’organisation peut utiliser un déploiement centralisé pour déployer ce complément sur tous les mineurs qui ont le consentement.
  
Pour être conforme à RGPD pour les mineurs, vous devez vous assurer que l’une des versions suivantes d’Office est déployée dans votre établissement scolaire ou votre organisation.
 
 **Pour Word, Excel, PowerPoint et Project**: 

|**Plateforme** <br/> |**Numéro de build** <br/> |
|:-----|:-----|
|Applications Microsoft 365 pour les entreprises (canal actuel)  <br/> |9001,2138   <br/> |
|Applications Microsoft 365 pour Enterprise (canal d’entreprise semi-annuel)  <br/> |8431,2159  <br/> |
|Office 2016 pour Windows  <br/> |16.0.4672.1000  <br/> |
|Office 2013 pour Windows  <br/> |15.0.5023.1000  <br/> |
|Office 2016 pour Mac  <br/> |16.11.18020200  <br/> |
|Office pour le web  <br/> |S/O  <br/> |
   
 **Pour Outlook**: 
  
|**Plateforme** <br/> |**Numéro de build** <br/> |
|:-----|:-----|
|Outlook 2016 pour Windows (MSI)  <br/> |Générer non TBD  <br/> |
|Outlook 2016 pour Windows (C2R)  <br/> |16.0.9323.1000  <br/> |
|Office 2016 pour Mac  <br/> |16.0.9318.1000  <br/> |
|Outlook Mobile pour iOS  <br/> |2.75.0  <br/> |
|Outlook Mobile pour Android  <br/> |2.2.145  <br/> |
|Outlook.com  <br/> |S/O  <br/> |

 **Configuration requise pour Office 2013**
  
Word, Excel et PowerPoint 2013 pour Windows prend en charge les mêmes vérifications de mineurs si la bibliothèque d’authentification Active Directory (ADAL) est activée. Il existe deux options pour la conformité, comme expliqué ci-dessous.
  
- **Activez Adal**. Cet article explique comment activer ADAL pour Office 2013 : utilisation de l' [authentification moderne Microsoft 365 avec les clients Office](https://docs.microsoft.com/microsoft-365/enterprise/modern-auth-for-office-2013-and-2016).<br/>Vous devez également définir les clés de Registre pour activer ADAL, comme expliqué dans la rubrique [activation de l’authentification moderne pour Office 2013 sur les appareils Windows](../security-and-compliance/enable-modern-authentication.md).<br/>En outre, vous devez installer les mises à jour d’avril suivantes pour Office 2013 :
    
  - [Description de la mise à jour de sécurité pour Office 2013:10 avril 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)
    
  - [2018 avril, mise à jour pour Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)
    
- **N’activez pas Adal**. Si vous ne parvenez pas à activer ADAL dans Office 2013, nous vous recommandons d’utiliser la stratégie de groupe pour désactiver le magasin pour les clients Office. Vous trouverez [ici](https://technet.microsoft.com/library/cc178992.aspx)des informations sur la façon de désactiver les paramètres de l’application pour Office.

## <a name="related-articles"></a>Articles connexes

[Déployer des compléments dans le centre d’administration](https://docs.microsoft.com/microsoft-365/admin/manage/manage-deployment-of-add-ins)

[Gérer des compléments dans le centre d’administration](https://docs.microsoft.com/microsoft-365/admin/manage/manage-addins-in-the-admin-center)
    
