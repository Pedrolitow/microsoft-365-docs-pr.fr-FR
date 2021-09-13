---
title: Modifications de service et communication
description: Comment les modifications apportées au service se produisent et sont communiquées
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 20af244d14f8f29e0175fb5e8efdabff94ff9a2b
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204956"
---
# <a name="service-changes-and-communication"></a>Modifications de service et communication

Parfois, Microsoft peut avoir besoin de modifier les détails de la façon dont Microsoft Manged Desktop fonctionne. De même, vous devrez peut-être apporter des modifications qui affecteraient également le service. Ces changements sont gérés différemment en fonction de leur importance. Cette rubrique définit les modifications que nous considérons comme majeures et explique comment les gérer par rapport à d’autres modifications.



## <a name="changes-made-by-microsoft"></a>Modifications apportées par Microsoft

Nous vous fournirons une notification au moins 30 jours à l’avance pour toute modification majeure nécessitant une action. Nous vous en faire part à l’aide Microsoft Manged Desktop système de messagerie du portail d’administration.

**Les principales modifications** sont celles qui peuvent avoir un impact sur l’un de ces domaines :
- Modifications affectant la productivité quotidienne
- Modifications apportées aux fonctionnalités et applications personnalisées
- Augmentation ou diminution de la capacité visible
- Modifications apportées à la marque du produit qui peuvent provoquer une confusion ou un changement de l’utilisateur dans les processus du helpdesk et le matériel de référence ou les URL
- Modifications nécessitant des autorisations au-delà de celles requises par le service pour les opérations quotidiennes, à l’exclusion des actions qui empêchent ou corrigent les problèmes
- Modifications apportées à l’endroit où vos données sont stockées
- Ajout d’un nouveau service ou application de composant à l’étendue du service
- Suppression d’un service ou d’une application de composant de l’étendue du service
- Ajout d’une nouvelle fonctionnalité au service

> [!NOTE]
> Nous devons peut-être apporter des modifications pour atténuer les incidents ou les problèmes de sécurité qui seraient exclus de la stratégie de notification de 30 jours.

Nous apporterons régulièrement d’autres modifications au service pour améliorer l’expérience utilisateur, la sécurité, la fiabilité et la reporting. Voici quelques exemples de ces modifications :

- Installation des mises à jour Windows et Office jour
- Mises à jour de la ligne de base de sécurité appliquée aux appareils
- Appareils pris en charge. Pour voir les appareils recommandés, filtrez les Microsoft Manged Desktop sur le site [Windows 10 Professionnel d’entreprise.](https://www.microsoft.com/windowsforbusiness/view-all-devices)

Nous communiquerons ces modifications à l’aide de canaux établis. Si vous avez des questions sur les modifications, contactez l’équipe Microsoft Manged Desktop [Operations](../working-with-managed-desktop/admin-support.md). Les modifications apportées au service sont également documentées selon les besoins dans [l’historique des modifications.](../change-history-managed-desktop.md)

Microsoft Manged Desktop modifications et communications sont régies par deux stratégies Microsoft :
- [Stratégie moderne de cycle de vie](https://support.microsoft.com/help/30881/modern-lifecycle-policy)
- [Microsoft 365 Modifier la stratégie de communication](/office365/admin/manage/message-center)

## <a name="changes-you-make"></a>Modifications apportées

Certaines modifications que vous pouvez apporter à votre environnement peuvent avoir un impact sur Microsoft Manged Desktop. Pour ces modifications majeures, nous vous demandons de nous envoyer une notification d’au moins 30 jours en envoyant une demande de service dans le portail Microsoft Manged Desktop administrateur. Pour [plus d’Microsoft Manged Desktop,](../working-with-managed-desktop/admin-support.md) consultez la prise en charge de l’administrateur. Cela nous laisse suffisamment de temps pour planifier et préparer la modification afin d’éviter les perturbations.

Les principales modifications sont celles qui peuvent avoir un impact sur l’un de ces domaines :

- Groupes et systèmes d’identité
- Contrôles réseau et réseau tels que les pare-feu, les proxys ou la mise en cache et les systèmes VPN
- Contrôles d’accès aux configurations des services cloud
- Certificats d’utilisateur ou d’appareil utilisés pour l’identité ou la sécurisation des services réseau
- Systèmes de gestion qui interagissent avec le service
- Systèmes de sécurité ou agents qui interagissent avec le service
- Configuration de l’un des services Microsoft 365 cloud associés au service ou utilisés par celui-là

Ces modifications ne sont pas susceptibles d’être perturbantes, vous n’avez donc pas besoin de nous les faire savoir à l’avance :

- Nettoyage d’objet orphelin
- Ajout ou suppression d’utilisateurs du service
- Configuration du système qui n’a pas d’impact matériel sur la distribution du Microsoft Manged Desktop
- Mises à jour de la version de l’application, à l’exception des applications VPN ou proxy