---
title: Enregistrements DNS pour Office 365 GCC High
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Résumé : Enregistrements DNS pour Office 365 Cloud de la communauté du secteur public élevé'
hideEdit: true
ms.openlocfilehash: 80c1a5d4473af0877e67b6bc9e14a9ffd890e3ba
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2022
ms.locfileid: "62806815"
---
# <a name="dns-records-for-office-365-gcc-high"></a>Enregistrements DNS pour Office 365 GCC High

*Cet article s’applique aux Office 365 Cloud de la communauté du secteur public High et Microsoft 365 Cloud de la communauté du secteur public High*

Dans le cadre de l’intégration à Office 365 Cloud de la communauté du secteur public High, vous devez ajouter vos domaines SMTP et SIP à votre client Online Services.  Pour ce faire, utilisez l'New-MsolDomain de Azure AD PowerShell ou utilisez le portail [Azure Government pour](https://portal.azure.us) démarrer le processus d’ajout du domaine et de preuve de propriété.

Une fois vos domaines ajoutés à votre client et validés, utilisez les instructions suivantes pour ajouter les enregistrements DNS appropriés pour les services ci-dessous.  Vous devrez peut-être modifier le tableau ci-dessous pour répondre aux besoins de votre organisation en ce qui concerne le ou les enregistrement(s) MX entrant(s) et tous les enregistrement(s) de découverte automatique Exchange existant(s) que vous avez en place.  Nous vous recommandons vivement de coordonner ces enregistrements DNS avec votre équipe de messagerie afin d’éviter toute panne ou mauvaise remise du courrier électronique.

## <a name="exchange-online"></a>Exchange Online

| Type (Type) | Priority (Priorité) | Nom d’hôte | Points vers l’adresse ou la valeur | Durée de vie |
| --- | --- | --- | --- | --- |
| MX | 0 | @ | *tenant.mail.protection.office365.us* (voir ci-dessous pour plus d’informations) | Une heure |
| TXT | - | @ | v=spf1 include:spf.protection.office365.us -all | Une heure |
| CNAME | - | autodiscover | autodiscover.office365.us | Une heure |

### <a name="exchange-autodiscover-record"></a>Exchange de découverte automatique

Si vous avez Exchange Server en local, nous vous recommandons de laisser votre enregistrement existant en place pendant la migration vers Exchange Online, puis de mettre à jour cet enregistrement une fois que vous avez terminé la migration. 

### <a name="exchange-online-mx-record"></a>Exchange Online MX Record

La valeur de l’enregistrement MX pour vos domaines acceptés suit un format standard comme indiqué ci-dessus : *tenant.mail.protection.office365.us*, en  remplaçant le client par la première partie du nom de votre client par défaut.

Par exemple, si le nom de votre client contoso.onmicrosoft.us, vous devez utiliser **contoso.mail.protection.office365.us** comme valeur pour votre enregistrement MX.

## <a name="skype-for-business-online"></a>Skype Entreprise Online

### <a name="cname-records"></a>Enregistrements CNAME

| Type | Nom d’hôte | Points vers l’adresse ou la valeur | Durée de vie |
| --- | --- | --- | --- |
| CNAME | sip | sipdir.online.gov.skypeforbusiness.us | Une heure |
| CNAME | lyncdiscover | webdir.online.gov.skypeforbusiness.us | Une heure |

### <a name="srv-records"></a>Enregistrements SRV

| Type | Service | Protocole | Port | Pondération | Priorité | Nom | Target | Durée de vie |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRV | \_sip | \_tls | 443 | 1 | 100 | @ | sipdir.online.gov.skypeforbusiness.us | Une heure |
| SRV | \_sipfederationtls | \_tcp | 5061 | 1 | 100 | @ | sipfed.online.gov.skypeforbusiness.us | Une heure |

## <a name="other-dns-records"></a>Autres enregistrements DNS

> [!IMPORTANT]
> Si vous avez un enregistrement *CNAME msoid* existant dans votre zone DNS, vous devez supprimer  l’enregistrement du DNS pour le moment.  L’enregistrement msoid est incompatible avec Microsoft 365 Entreprise Apps (anciennement *Office 365 ProPlus)* et empêche l’activation de réussir.
