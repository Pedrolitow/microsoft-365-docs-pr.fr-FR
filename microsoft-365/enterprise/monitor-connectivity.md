---
title: Surveiller la connectivité Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Dans cet article, vous allez découvrir les outils et techniques que vous pouvez utiliser pour surveiller et maintenir Microsoft 365 connectivité.
ms.openlocfilehash: 0e7c18a10dc851596af6a652fb80c9c72852ee0d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093304"
---
# <a name="monitor-microsoft-365-connectivity"></a>Surveiller la connectivité Microsoft 365

Une fois que vous avez déployé Microsoft 365, vous pouvez maintenir Microsoft 365 connectivité à l’aide de certains des outils et techniques ci-dessous. Vous voudrez comprendre les instructions officielles relatives à [l’intégrité et](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) à la continuité des services, ainsi que nos [meilleures pratiques pour l’utilisation de Microsoft 365 sur un réseau lent](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). Vous souhaiterez également récupérer [l’application d’administration Microsoft 365](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) et marquer notre [Microsoft 365 pour les entreprises - Aide de l’administrateur](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).
  
## <a name="monitoring-microsoft-365-connectivity"></a>Surveillance de la connectivité Microsoft 365

|Type de surveillance |Description |
|:-----|:-----|
|**Obtention d’une notification de nouveaux points de terminaison Microsoft 365** <br/> |Si vous [gérez Microsoft 365 points](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) de terminaison, vous souhaiterez recevoir des notifications lorsque nous publierons de nouveaux points de terminaison. Vous pouvez vous abonner à notre flux RSS à l’aide de votre lecteur RSS favori. Voici comment vous [abonner via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) ou vous pouvez [recevoir les mises à jour du flux RSS par e-mail](https://go.microsoft.com/fwlink/p/?LinkId=532417).  <br/> |
|**Utiliser System Center pour surveiller les Microsoft 365** <br/> |Si vous utilisez Microsoft System Center, vous pouvez télécharger le pack d’administration [Microsoft System Center Operations Manager pour Microsoft 365](https://www.microsoft.com/download/details.aspx?id=103379) pour commencer la surveillance Microsoft 365 dès aujourd’hui. Pour obtenir des conseils plus détaillés, consultez le guide des opérations du pack d’administration. <br/> |
|**Surveiller l’état d’Azure ExpressRoute** <br/> |Si vous vous connectez à Microsoft 365 à l’aide d’Azure ExpressRoute pour Microsoft 365, vous devez vous assurer que vous utilisez le tableau de bord Microsoft 365 Service Health ainsi que le [temps de résolution des problèmes Azure Reducing avec Azure Resource Health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**Utiliser Azure AD Connect Health avec AD FS** <br/> |Si vous utilisez AD FS pour une Sign-On unique avec Microsoft 365, vous pouvez commencer à [utiliser Azure AD Connecter Health pour surveiller votre infrastructure AD FS](/azure/active-directory/hybrid/how-to-connect-health-adfs).  <br/> |
|**Surveiller les Microsoft 365 par programmation** <br/> |Reportez-vous à nos conseils sur [l’API de gestion Microsoft 365](/office/office-365-management-api/office-365-management-apis-overview).  <br/> |

Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/monitorconnectivity365]()
  
## <a name="related-topics"></a>Voir aussi

[Configurer Microsoft 365 Entreprise services et applications](configure-services-and-applications.md)
  
[Préparer votre organisation pour Microsoft 365 Entreprise](get-your-organization-ready-for-office-365.md)
  
[Planification réseau et optimisation des performances pour Microsoft 365](network-planning-and-performance.md)
  
[intégration Microsoft 365 à des environnements locaux](microsoft-365-integration.md)
  
[Gestion des points de terminaison Microsoft 365](managing-office-365-endpoints.md)
