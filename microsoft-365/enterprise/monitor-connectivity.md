---
title: Surveiller la connectivité Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
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
description: Dans cet article, vous allez découvrir les outils et techniques que vous pouvez utiliser pour surveiller et maintenir la connectivité Microsoft 365.
ms.openlocfilehash: db3811b70f91efb9fd1e9f023df12d0852ce0189
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50920775"
---
# <a name="monitor-microsoft-365-connectivity"></a>Surveiller la connectivité Microsoft 365

Une fois que vous avez déployé Microsoft 365, vous pouvez maintenir la connectivité Microsoft 365 à l’aide de certains des outils et techniques ci-dessous. Vous souhaiterez comprendre les instructions officielles relatives à la continuité et à l’état du [service,](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) ainsi que nos meilleures pratiques d’utilisation de [Microsoft 365 sur un réseau lent.](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) Vous pouvez également récupérer l’application d’administration [Microsoft 365](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) et mettre en signet notre Microsoft 365 pour les entreprises [- Aide de l’administrateur.](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)
  
## <a name="monitoring-microsoft-365-connectivity"></a>Surveillance de la connectivité Microsoft 365

|||
|:-----|:-----|
|**Notification de nouveaux points de terminaison Microsoft 365** <br/> |Si vous gérez des points de terminaison [Microsoft 365,](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)vous souhaiterez recevoir des notifications lorsque nous publions de nouveaux points de terminaison, vous pouvez vous abonner à notre flux RSS à l’aide de votre lecteur RSS favori. Voici comment vous abonner [via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) ou vous pouvez envoyer par courrier électronique les mises à jour de flux [RSS.](https://go.microsoft.com/fwlink/p/?LinkId=532417)  <br/> |
|**Utiliser System Center pour surveiller Microsoft 365** <br/> |Si vous utilisez Microsoft System Center, vous pouvez télécharger le pack d’administration System Center pour [Office 365](https://www.microsoft.com/download/details.aspx?id=43708) afin de commencer à surveiller Microsoft 365 dès aujourd’hui. Pour obtenir des instructions plus détaillées, consultez le guide des opérations du pack d’administration ou ce billet de blog sur la surveillance [d’Office 365](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx) à l’aide de System Centre Operations Manager <br/> |
|**Surveiller l’état d’Azure ExpressRoute** <br/> |Si vous vous connectez à Microsoft 365 à l’aide d’Azure ExpressRoute pour Microsoft 365, vous devez vous assurer que vous utilisez à la fois le tableau de bord d’état du service Microsoft 365 et Azure Réduisant le temps de dépannage avec l’état des ressources [Azure](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**Utiliser Azure AD Connect Health avec AD FS** <br/> |Si vous utilisez AD FS pour Sign-On unique avec Microsoft 365, vous pouvez commencer à utiliser Azure AD Connect Health pour surveiller votre [infrastructure AD FS.](/azure/active-directory/hybrid/how-to-connect-health-adfs)  <br/> |
|**Surveiller Microsoft 365 par programme** <br/> |Reportez-vous à nos conseils sur l’API de gestion [Microsoft 365.](/office/office-365-management-api/office-365-management-apis-overview)  <br/> |

Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/monitorconnectivity365]()
  
## <a name="related-topics"></a>Rubriques connexes

[Configurer les applications et services Microsoft 365 Entreprise](configure-services-and-applications.md)
  
[Préparer votre organisation pour Microsoft 365 Entreprise](get-your-organization-ready-for-office-365.md)
  
[Planification réseau et optimisation des performances pour Microsoft 365](network-planning-and-performance.md)
  
[Intégration de Microsoft 365 aux environnements locaux](microsoft-365-integration.md)
  
[Gestion des points de terminaison Microsoft 365](managing-office-365-endpoints.md)