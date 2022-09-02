---
title: Enregistrements DNS pour Office 365 DoD
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
description: 'Résumé : Enregistrements DNS pour Office 365 DoD'
hideEdit: true
ms.openlocfilehash: a0b7c08805e5cdd07c798da3c45b3af82ceddd1d
ms.sourcegitcommit: 62368e5a48e569c8e475b07d194d7d8ff7d167ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67556345"
---
# <a name="dns-records-for-office-365-dod"></a>Enregistrements DNS pour Office 365 DoD

*Cet article s’applique à Office 365 DoD et Microsoft 365 DoD*

Dans le cadre de l’intégration à Office 365 DoD, vous devez ajouter vos domaines SMTP et SIP à votre locataire Services en ligne.  Pour ce faire, utilisez l’applet de commande New-MsolDomain dans Azure AD PowerShell ou utilisez le [portail Azure Government](https://portal.azure.us) pour démarrer le processus d’ajout du domaine et de preuve de la propriété.

Une fois que vos domaines ont été ajoutés à votre locataire et validés, utilisez les instructions suivantes pour ajouter les enregistrements DNS appropriés pour les services ci-dessous.  Vous devrez peut-être modifier le tableau ci-dessous pour répondre aux besoins de votre organisation en ce qui concerne les enregistrements MX entrants et les enregistrements de découverte automatique Exchange existants que vous avez en place.  Nous vous recommandons vivement de coordonner ces enregistrements DNS avec votre équipe de messagerie afin d’éviter toute panne ou toute mauvaise remise de courrier électronique.

## <a name="exchange-online"></a>Exchange Online

| Type (Type) | Priority (Priorité) | Nom d’hôte | Points vers l’adresse ou la valeur | Durée de vie |
| --- | --- | --- | --- | --- |
| MX | 0 | @ | *tenant.mail.protection.office365.us* (voir ci-dessous pour plus d’informations) | Une heure |
| TXT | - | @ | v=spf1 include:spf.protection.office365.us -all | Une heure |
| CNAME | - | autodiscover | autodiscover-dod.office365.us | Une heure |

### <a name="exchange-autodiscover-record"></a>Enregistrement de découverte automatique Exchange

Si vous avez Exchange Server localement, nous vous recommandons de laisser votre enregistrement existant en place pendant la migration vers Exchange Online et de mettre à jour cet enregistrement une fois que vous avez terminé votre migration.

### <a name="exchange-online-mx-record"></a>enregistrement MX Exchange Online

La valeur d’enregistrement MX pour vos domaines acceptés suit un format standard comme indiqué ci-dessus : *tenant.mail.protection.office365.us*, en remplaçant le *locataire* par la première partie de votre nom de locataire par défaut.

Par exemple, si votre nom de locataire est contoso.onmicrosoft.us, vous utiliseriez **contoso.mail.protection.office365.us** comme valeur pour votre enregistrement MX.

## <a name="skype-for-business-online"></a>Skype Entreprise Online

### <a name="cname-records"></a>Enregistrements CNAME

| Type | Nom d’hôte | Points vers l’adresse ou la valeur | Durée de vie |
| --- | --- | --- | --- |
| CNAME | sip | sipdir.online.dod.skypeforbusiness.us | Une heure |
| CNAME | lyncdiscover | webdir.online.dod.skypeforbusiness.us | Une heure | 

### <a name="srv-records"></a>Enregistrements SRV

| Type | Service | Protocole | Port | Pondération | Priorité | Nom | Target | Durée de vie |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRV | \_sip | \_tls | 443 | 1 | 100 | @ | sipdir.online.dod.skypeforbusiness.us | Une heure |
| SRV | \_sipfederationtls | \_tcp | 5061 | 1 | 100 | @ | sipfed.online.dod.skypeforbusiness.us | Une heure |

## <a name="other-dns-records"></a>Autres enregistrements DNS

> [!IMPORTANT]
> Si vous disposez d’un enregistrement CNAME *msoid* existant dans votre zone DNS, vous devez **supprimer** l’enregistrement de DNS pour l’instant.  L’enregistrement msoid est incompatible avec Microsoft 365 Entreprise Apps *(anciennement Office 365 ProPlus)* et empêche l’activation de réussir.
