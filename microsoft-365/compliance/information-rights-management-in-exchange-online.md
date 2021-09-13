---
title: Chiffrement du courrier Exchange Online avec AD RMS
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/13/2017
audience: End User
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 2c956776-0016-4be6-b4cd-133a237f4a9e
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment configurer Exchange Online IRM pour utiliser le service AD RMS (Active Directory Rights Management Service) local afin de répondre aux exigences de votre organisation.
ms.openlocfilehash: d98cf5c762cd4dac0cbad6d25a3cc766d5c5310a
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59182248"
---
# <a name="exchange-online-mail-encryption-with-ad-rms"></a>Chiffrement du courrier Exchange Online avec AD RMS

Pour contribuer à la prévention des fuites d'informations, Exchange Online inclut des fonctionnalités de gestion des droits relatifs à l'information (IRM) qui offrent une protection en ligne et hors connexion des messages électroniques et des pièces jointes. Vous pouvez configurer Exchange Online IRM pour utiliser le service AD RMS (Active Directory Rights Management Service) local, si nécessaire, afin de répondre aux exigences de votre organisation. Cela n’est pas courant. Si vous n’avez pas besoin d’utiliser AD RMS, [chiffrement de messages Office 365](ome.md) à la place. 

La protection IRM peut être appliquée par les utilisateurs dans Microsoft Outlook ou Outlook sur le web et par les administrateurs à l'aide de règles de protection du transport ou de règles de protection Outlook. L’IRM vous aide, ainsi que vos utilisateurs, à contrôler l’accès, le transfert, l’impression ou la copie de données sensibles dans un courrier électronique.
  
## <a name="changes-to-how-irm-works-with-office-365-message-encryption-ome-and-azure-active-directory"></a>Changements concernant le fonctionnement de l’IRM avec le chiffrement de messages Office 365 (OME) et Azure Active Directory

Depuis septembre 2017, lorsque vous paramétrez les nouvelles fonctionnalités de chiffrement de messages Office 365 pour votre organisation, vous configurez également l'IRM pour son utilisation avec Azure Rights Management (Azure RMS). Vous ne configurez plus l'IRM avec Azure RMS de manière distincte. Désormais, l'OME et la gestion des droits fonctionnent conjointement de manière transparente. Pour plus de détails sur les nouvelles fonctionnalités, consultez la [FAQ sur le chiffrement de messages Office 365](./ome-faq.yml). Si vous êtes prêt à commencer à utiliser les nouvelles fonctionnalités d'OME au sein de votre organisation, consultez [Configurer les nouvelles fonctionnalités de chiffrement de messages Office 365 intégrées en haut de la Protection des informations Azure](./set-up-new-message-encryption-capabilities.md).
  
## <a name="how-irm-works-with-exchange-online-and-active-directory-rights-management-services"></a>Fonctionnement de l’IRM avec Exchange Online et les services AD RMS (Active Directory Rights Management Services)

L'IRM dans Exchange Online utilise les services AD RMS (Active Directory Rights Management Services), une technologie de protection des informations de Windows Server 2008 et versions ultérieures. La protection IRM permet d'appliquer un modèle de stratégie de droits AD RMS à un message électronique. Les droits sont liés au message lui-même. Ainsi la protection est assurée en ligne comme hors connexion, et à l'intérieur ou à l'extérieur du pare-feu de votre organisation.
  
Les utilisateurs peuvent appliquer un modèle à un message électronique afin de contrôler les autorisations dont disposent les destinataires sur un message. En appliquant une stratégie de droits AD RMS au message, vous pouvez contrôler des actions comme le transfert, l'extraction d'informations d'un message, l'enregistrement ou l'impression d'un message.
  
Vous pouvez configurer l'IRM pour utiliser un serveur AD RMS exécutant Windows Server 2008 ou une version ultérieure. Ce serveur AD RMS permet de gérer les modèles de stratégies de droits AD RMS pour votre organisation en nuage. Outlook utilise également le serveur AD RMS pour permettre aux utilisateurs d'appliquer la protection IRM aux messages qu'ils envoient. Pour plus d’informations, voir Configurer IRM pour utiliser un serveur [AD RMS local.](configure-irm-to-use-an-on-premises-ad-rms-server.md) 
  
Après avoir activé la protection IRM, vous pouvez l'appliquer aux messages de la manière suivante :
  
- **Les utilisateurs peuvent appliquer manuellement un modèle à l'aide d'Outlook et d'Outlook sur le web.** Les utilisateurs peuvent appliquer un modèle de stratégie de droits AD RMS à un message électronique en sélectionnant le modèle dans la liste **Définir les autorisations**. Quand les utilisateurs envoient un message protégé par IRM, les fichiers joints qui ont un format pris en charge bénéficient de la même protection IRM que le message. La protection IRM est appliquée aux fichiers associés à Word, Excel et PowerPoint, ainsi qu'aux fichiers .xps et aux messages électroniques joints. 
    
- **Les administrateurs peuvent utiliser les règles de protection de transport pour appliquer la protection IRM automatiquement à Outlook et à Outlook sur le web.** Vous pouvez créer des règles de protection de transport pour protéger des messages par IRM. Configurez l'action de la règle de protection de transport pour appliquer un modèle de stratégie de droits AD RMS aux messages qui répondent aux critères de la règle. Après avoir activé l'IRM, les modèles de stratégie de droits AD RMS de votre organisation peuvent être utilisés avec l'action de la règle appelée **Appliquer la protection des droits au message avec**.
    
- **Les administrateurs peuvent créer des règles de protection Outlook.** Les règles de protection Outlook appliquent automatiquement la protection IRM aux messages dans Outlook 2010 (et non dans Outlook sur le web) en fonction de critères applicables au message, tels que le service de l'expéditeur, le destinataire et si les destinataires font partie ou non de l'organisation. Pour plus d'informations, consultez la rubrique [Create an Outlook Protection Rule](/exchange/create-an-outlook-protection-rule-exchange-2013-help).
