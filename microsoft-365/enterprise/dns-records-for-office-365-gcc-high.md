---
title: Enregistrements DNS pour Office 365 GCC High
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
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
ms.openlocfilehash: 9edcda4616d50d05331db0e2d6c4d89967b02fdc
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59181205"
---
# <a name="dns-records-for-office-365-gcc-high"></a>Enregistrements DNS pour Office 365 GCC High

*Cet article s’applique aux Office 365 Cloud de la communauté du secteur public High et Microsoft 365 Cloud de la communauté du secteur public High*

Dans le cadre de l’intégration à Office 365 Cloud de la communauté du secteur public High, vous devez ajouter vos domaines SMTP et SIP à votre client de services en ligne.  Pour ce faire, utilisez l'New-MsolDomain dans Azure AD PowerShell ou utilisez le portail [Azure Government pour](https://portal.azure.us) démarrer le processus d’ajout du domaine et prouver la propriété.

Une fois vos domaines ajoutés à votre client et validés, utilisez les instructions suivantes pour ajouter les enregistrements DNS appropriés pour les services ci-dessous.  Vous devrez peut-être modifier le tableau ci-dessous pour répondre aux besoins de votre organisation en ce qui concerne le ou les enregistrement(s) MX entrant(s) et tous les enregistrement(s) de découverte automatique Exchange existant(s) que vous avez en place.  Nous vous recommandons vivement de coordonner ces enregistrements DNS avec votre équipe de messagerie afin d’éviter toute panne ou mauvaise remise des messages électroniques.

## <a name="exchange-online"></a>Exchange Online

| Type (Type) | Priority (Priorité) | Nom d’hôte | Points vers l’adresse ou la valeur | Durée de vie |
| --- | --- | --- | --- | --- |
| MX | 0 | @ | *tenant*.mail.protection.office365.us (voir ci-dessous pour plus d’informations) | 1 Hour |
| TXT | - | @ | v=spf1 include:spf.protection.office365.us -all | 1 heure |
| CNAME | - | autodiscover | autodiscover.office365.us | 1 Hour |

### <a name="exchange-autodiscover-record"></a>Exchange Enregistrement de découverte automatique

Si vous avez Exchange Server en local, nous vous recommandons de laisser votre enregistrement existant en place pendant la migration vers Exchange Online, puis de mettre à jour cet enregistrement une fois que vous avez terminé la migration. 

### <a name="exchange-online-mx-record"></a>Exchange Online Enregistrement MX

La valeur d’enregistrement MX pour vos domaines acceptés suit un format standard  comme indiqué ci-dessus : *client*.mail.protection.office365.us, en remplaçant le client par la première partie de votre nom de client par défaut.

Par exemple, si le nom de votre client contoso.onmicrosoft.us, vous devez utiliser **contoso.mail.protection.office365.us** comme valeur pour votre enregistrement MX.

## <a name="skype-for-business-online"></a>Skype Entreprise Online

### <a name="cname-records"></a>Enregistrements CNAME

| Type | Nom d’hôte | Points vers l’adresse ou la valeur | Durée de vie |
| --- | --- | --- | --- |
| CNAME | sip | sipdir.online.gov.skypeforbusiness.us | 1 heure |
| CNAME | lyncdiscover | webdir.online.gov.skypeforbusiness.us | 1 Hour |

### <a name="srv-records"></a>Enregistrements SRV

| Type | Service | Protocole | Port | Pondération | Priorité | Nom | Target | Durée de vie |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRV | \_sip | \_tls | 443 | 1 | 100 | @ | sipdir.online.gov.skypeforbusiness.us | 1 heure |
| SRV | \_sipfederationtls | \_tcp | 5061 | 1 | 100 | @ | sipfed.online.gov.skypeforbusiness.us | 1 Hour |

## <a name="additional-dns-records"></a>Enregistrements DNS supplémentaires

> [!IMPORTANT]
> Si vous avez un enregistrement *CNAME msoid* existant dans  votre zone DNS, vous devez supprimer l’enregistrement du DNS pour le moment.  L’enregistrement msoid est incompatible avec Microsoft 365 Entreprise Apps *(anciennement Office 365 ProPlus)* et empêche l’activation de réussir.
