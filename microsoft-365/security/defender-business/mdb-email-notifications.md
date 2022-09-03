---
title: Configurer des notifications par e-mail pour votre équipe de sécurité
description: Configurez des notifications par e-mail pour informer votre équipe de sécurité des alertes et des vulnérabilités dans Defender entreprise.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365solution-mdb-setup
- highpri
ms.openlocfilehash: d59f22b8325f63a2f10164cb56f7604465e54569
ms.sourcegitcommit: 511d15831b97d02e5a0f5e11834ad52617abd0f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67600266"
---
# <a name="set-up-email-notifications"></a>Configurer des notifications par e-mail

Vous pouvez configurer des notifications par e-mail pour votre équipe de sécurité. Ensuite, à mesure que des alertes sont générées ou que de nouvelles vulnérabilités sont découvertes, les membres de votre équipe de sécurité sont avertis automatiquement. 

## <a name="what-to-do"></a>Procédure

1. [Découvrez les types de notifications par e-mail](#types-of-email-notifications).
2. [Afficher et modifier les paramètres de notification par e-mail](#view-and-edit-email-notifications).
3. [Passez à vos étapes suivantes](#next-steps).

## <a name="types-of-email-notifications"></a>Types de notifications par e-mail

Lorsque vous configurez des notifications par e-mail, vous pouvez choisir parmi deux types, comme décrit dans le tableau suivant :

| Type de notification  | Description  |
|---------|---------|
| Vulnérabilités  | Chaque fois que de nouveaux exploits ou événements de vulnérabilité sont détectés, les destinataires reçoivent un e-mail. |
| Alertes & vulnérabilités  | Lorsque des alertes sont générées parce que des menaces sont détectées sur les appareils, ou lorsque de nouveaux exploits ou événements de vulnérabilité sont détectés, les destinataires reçoivent un e-mail. |

> [!TIP]
> **Email notifications ne sont pas la seule façon pour votre équipe de sécurité d’en savoir plus sur les nouvelles alertes ou vulnérabilités**.
> 
> Email notifications sont un moyen pratique de tenir votre équipe de sécurité informée, en temps réel. Mais il y en a d’autres ! Par exemple, chaque fois que votre équipe de sécurité se connecte au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), elle voit des cartes mettant en évidence les nouvelles menaces, alertes et vulnérabilités. Defender entreprise est conçu pour mettre en évidence les informations importantes qui intéressent votre équipe de sécurité dès qu’elle se connecte.
> 
> Votre équipe de sécurité peut également choisir **Incidents** dans le volet de navigation pour afficher les informations. Pour plus d’informations, consultez [Afficher et gérer les incidents dans Defender entreprise](mdb-view-manage-incidents.md).

## <a name="view-and-edit-email-notifications"></a>Afficher et modifier les notifications par e-mail

Pour afficher ou modifier les paramètres de notification par e-mail de votre entreprise, procédez comme suit :

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, sélectionnez **Paramètres**, puis les **points de terminaison**. Ensuite, sous **Général**, sélectionnez **Email notifications**. 

3. Passez en revue les informations sous les **onglets Alertes** et **vulnérabilités** .

   - Si vous ne voyez pas d’éléments répertoriés sous l’onglet **Alertes** , vous pouvez créer une règle pour que les utilisateurs soient avertis lorsque des alertes sont générées. Pour obtenir de l’aide sur cette tâche, consultez [Créer des règles pour les notifications d’alerte](../defender-endpoint/configure-email-notifications.md).

   - Si vous ne voyez pas d’éléments répertoriés sous l’onglet **Vulnérabilités** , vous pouvez créer une règle pour que les personnes soient averties chaque fois qu’une nouvelle vulnérabilité est détectée. Pour obtenir de l’aide sur cette tâche, consultez [Créer des règles pour les événements de vulnérabilité](../defender-endpoint/configure-vulnerability-email-notifications.md).

   - Si des règles sont créées, sélectionnez une règle pour la modifier. Vous pouvez également supprimer une règle. 

> [!IMPORTANT]
> Lorsque vous configurez des notifications par e-mail dans Defender entreprise, vous devez affecter les règles de notification à des utilisateurs spécifiques. Defender entreprise n’utilise pas le [contrôle d’accès en fonction du rôle, comme le fait Defender pour point de terminaison](../defender-endpoint/rbac.md). En outre, les notifications par e-mail ne peuvent pas être appliquées aux groupes d’appareils dans Defender entreprise. 

## <a name="next-steps"></a>Prochaines étapes

Effectuez les actions suivantes:

- [Étape 4 : Intégrer des appareils à Defender entreprise](mdb-onboard-devices.md)
