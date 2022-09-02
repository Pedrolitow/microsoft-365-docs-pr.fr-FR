---
title: Enregistrements DNS pour Office 365 GCC High
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
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
description: 'Résumé : Enregistrements DNS pour Office 365 GCC High'
hideEdit: true
ms.openlocfilehash: 6a7970fd795408099aea9018d66422845db2f1ad
ms.sourcegitcommit: e9323a90a1156c10b037abca3e16d7367ef92dd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67570049"
---
# <a name="dns-records-for-office-365-gcc-high"></a>Enregistrements DNS pour Office 365 GCC High

*Cet article s’applique à Office 365 GCC High et Microsoft 365 GCC High*

Dans le cadre de l’intégration à Office 365 GCC High, vous devez ajouter vos domaines SMTP et SIP à votre locataire Services en ligne.  Pour ce faire, utilisez l’applet de commande New-MsolDomain dans Azure AD PowerShell ou utilisez le [portail Azure Government](https://portal.azure.us) pour démarrer le processus d’ajout du domaine et de preuve de la propriété.

Une fois que vos domaines ont été ajoutés à votre locataire et validés, utilisez les instructions suivantes pour ajouter les enregistrements DNS appropriés pour les services ci-dessous.  Vous devrez peut-être modifier le tableau ci-dessous pour répondre aux besoins de votre organisation en ce qui concerne les enregistrements MX entrants et les enregistrements de découverte automatique Exchange existants que vous avez en place.  Nous vous recommandons vivement de coordonner ces enregistrements DNS avec votre équipe de messagerie afin d’éviter toute panne ou toute mauvaise remise de courrier électronique.

## <a name="exchange-online"></a>Exchange Online

| Type (Type) | Priority (Priorité) | Nom d’hôte | Points vers l’adresse ou la valeur | Durée de vie |
| --- | --- | --- | --- | --- |
| MX | 0 | @ | *tenant.mail.protection.office365.us* (voir ci-dessous pour plus d’informations) | Une heure |
| TXT | - | @ | v=spf1 include:spf.protection.office365.us -all | Une heure |
| CNAME | - | autodiscover | autodiscover.office365.us | Une heure |

### <a name="exchange-autodiscover-record"></a>Enregistrement de découverte automatique Exchange

Si vous avez Exchange Server localement, nous vous recommandons de laisser votre enregistrement existant en place pendant la migration vers Exchange Online et de mettre à jour cet enregistrement une fois que vous avez terminé votre migration. 

### <a name="exchange-online-mx-record"></a>enregistrement MX Exchange Online

La valeur d’enregistrement MX pour vos domaines acceptés suit un format standard comme indiqué ci-dessus : *tenant.mail.protection.office365.us*, en remplaçant le *locataire* par la première partie de votre nom de locataire par défaut.

Par exemple, si votre nom de locataire est contoso.onmicrosoft.us, vous utiliseriez **contoso.mail.protection.office365.us** comme valeur pour votre enregistrement MX.

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
> Si vous disposez d’un enregistrement CNAME *msoid* existant dans votre zone DNS, vous devez **supprimer** l’enregistrement de DNS pour l’instant.  L’enregistrement msoid est incompatible avec Microsoft 365 Entreprise Apps *(anciennement Office 365 ProPlus)* et empêche l’activation de réussir.
