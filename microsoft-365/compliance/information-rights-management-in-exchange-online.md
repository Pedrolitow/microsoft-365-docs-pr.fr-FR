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
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 2c956776-0016-4be6-b4cd-133a237f4a9e
ms.collection:
- tier3
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment configurer Exchange Online IRM pour utiliser Active Directory local Rights Management Service (AD RMS) pour répondre aux exigences de votre organisation.
ms.openlocfilehash: 9ea51944045dd635fbaf3d1b50c578fc607adae1
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68629212"
---
# <a name="exchange-online-mail-encryption-with-ad-rms"></a>Chiffrement du courrier Exchange Online avec AD RMS

Pour contribuer à la prévention des fuites d'informations, Exchange Online inclut des fonctionnalités de gestion des droits relatifs à l'information (IRM) qui offrent une protection en ligne et hors connexion des messages électroniques et des pièces jointes. Vous pouvez configurer Exchange Online IRM pour utiliser Active Directory local Rights Management Service (AD RMS), si nécessaire, pour répondre aux exigences de votre organisation. Cela n’est pas courant. Si vous n’avez pas besoin d’utiliser AD RMS, utilisez [Chiffrement de messages Microsoft Purview](ome.md) à la place.

La protection IRM peut être appliquée par les utilisateurs dans Microsoft Outlook ou Outlook sur le web et par les administrateurs à l'aide de règles de protection du transport ou de règles de protection Outlook. L'IRM vous aide, ainsi que vos utilisateurs, à contrôler l'accès, le transfert, l'impression ou la copie de données sensibles dans un courrier électronique.
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="changes-to-how-irm-works-with-message-encryption-and-azure-active-directory"></a>Modifications apportées au fonctionnement d’IRM avec le chiffrement des messages et Azure Active Directory

À compter de septembre 2017, lorsque vous configurez Chiffrement de messages Microsoft Purview pour votre organisation, vous configurez également IRM pour une utilisation avec Azure Rights Management (Azure RMS). Vous ne configurez plus l'IRM avec Azure RMS de manière distincte. Au lieu de cela, le chiffrement des messages et la gestion des droits fonctionnent en toute transparence. Pour plus d’informations sur Chiffrement de messages Microsoft Purview, consultez la [FAQ sur le chiffrement des messages](./ome-faq.yml). Si vous êtes prêt à commencer à utiliser Chiffrement de messages Microsoft Purview au sein de votre organisation, consultez [Configurer Chiffrement de messages Microsoft Purview](./set-up-new-message-encryption-capabilities.md).
  
## <a name="how-irm-works-with-exchange-online-and-active-directory-rights-management-services"></a>Fonctionnement de l’IRM avec Exchange Online et les services AD RMS (Active Directory Rights Management Services)

Exchange Online IRM uses on-premises Active Directory Rights Management Services (AD RMS), an information protection technology in Windows Server 2008 and later. IRM protection is applied to email by applying an AD RMS rights policy template to an email message. Rights are attached to the message itself so that protection occurs online and offline and inside and outside of your organization's firewall.
  
Users can apply a template to an email message to control the permissions that recipients have on a message. Actions, such as forwarding, extracting information from a message, saving a message or printing a message can be controlled by applying an AD RMS rights policy to the message.
  
Vous pouvez configurer l'IRM pour utiliser un serveur AD RMS exécutant Windows Server 2008 ou une version ultérieure. Ce serveur AD RMS permet de gérer les modèles de stratégies de droits AD RMS pour votre organisation en nuage. Outlook utilise également le serveur AD RMS pour permettre aux utilisateurs d'appliquer la protection IRM aux messages qu'ils envoient. Pour plus d’informations, consultez [Configurer IRM pour utiliser un serveur AD RMS local](configure-irm-to-use-an-on-premises-ad-rms-server.md).
  
Après avoir activé la protection IRM, vous pouvez l'appliquer aux messages de la manière suivante :
  
- **Users can manually apply a template using Outlook and Outlook on the web.** Users can apply an AD RMS rights policy template to an email message by selecting the template from the **Set permissions** list. When users send an IRM-protected message, any attached files that use a supported format also receive the same IRM protection as the message. IRM protection is applied to files associated with Word, Excel, and PowerPoint, as well as .xps files and attached email messages.

- **Administrators can use transport protection rules to apply IRM protection automatically to both Outlook and Outlook on the web.** You can create transport protection rules to IRM-protect messages. Configure the transport protection rule action to apply an AD RMS rights policy template to messages that meet the rule condition. After you enable IRM, your organization's AD RMS rights policy templates are available to use with the transport protection rule action called **Apply rights protection to the message with**.

- **Administrators can create Outlook protection rules.** Outlook protection rules automatically apply IRM-protection to messages in Outlook 2010 (not Outlook on the web) based on message conditions that include the sender's department, who the message is sent to, and whether recipients are inside or outside your organization. For details, see [Create an Outlook Protection Rule](/exchange/create-an-outlook-protection-rule-exchange-2013-help).
