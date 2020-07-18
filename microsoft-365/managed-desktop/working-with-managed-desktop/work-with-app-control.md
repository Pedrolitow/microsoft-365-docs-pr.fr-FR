---
title: Utiliser le contrôle d’application
description: ''
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
audience: ITpro
ms.topic: article
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 74cd1ec93058ed733e7d79da2d6932f04acfa5da
ms.sourcegitcommit: 63887d742c59cc660fc85537b335e98a9dc66fbe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "45170695"
---
# <a name="work-with-app-control"></a>Utiliser le contrôle d’application

Une fois que le contrôle d’application a été déployé dans votre environnement, vous et les opérations de bureau géré Microsoft ont des responsabilités permanentes. Par exemple, vous pouvez ajouter une nouvelle application dans l’environnement ou ajouter (ou supprimer) un signataire approuvé. Pour améliorer la sécurité, toutes les applications doivent être signées en code avant de les diffuser aux utilisateurs finaux. Les détails de l’éditeur d’une application incluent des informations sur le signataire.


## <a name="add-a-new-app"></a>Ajout d’une nouvelle application

Pour ajouter une nouvelle application, procédez comme suit :

1. Ajoutez l’application à [Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/apps-win32-app-management).
2. Déployez l’application sur n’importe quel appareil de la sonnerie de test. 
3. Testez votre application en fonction de vos processus d’entreprise standard. 
4. Consultez l’observateur d’événements sous **application et services Logs\Microsoft\Windows\AppLocker**, en recherchant les événements **8003** ou **8006** . Ces événements indiquent que l’application est bloquée. Pour plus d’informations sur tous les événements de blocage d’application et leurs significations, consultez la rubrique [utilisation de l’observateur d’événements avec AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/using-event-viewer-with-applocker).
5. Si vous trouvez l’un de ces événements, ouvrez une demande de signataire avec Microsoft Managed Desktop Operations.

## <a name="add-or-remove-a-trusted-signer"></a>Ajouter (ou supprimer) un signataire approuvé

Lorsque vous ouvrez une demande de signataire, vous devez d’abord fournir des informations importantes sur l’éditeur. Ensuite, procédez comme suit :

1. [Collecter les détails](#gather-publisher-details)de l’éditeur.
2. Ouvrez un ticket avec Microsoft Managed Desktop Operations pour demander la règle de signataire et incluez les informations suivantes :  
    - Nom de l’application 
    - Version de l’application 
    - Description 
    - Modifier le type (« ajouter » ou « supprimer »)  
    - Détails de l’éditeur (par exemple : "O = <publisher name> , L = <location> , S = État, C = pays") 

> [!NOTE]
> Pour supprimer l’approbation d’une application, suivez les mêmes étapes, mais définissez le **type de modification** sur *supprimer*.

Les opérations déploient progressivement des stratégies vers des groupes de déploiement suivant cette planification :


|Groupe de déploiement  |Type de stratégie  |Calendrier  |
|---------|---------|---------|
|Tester     |  Audit       |  Jour 0       |
|Premier     | Enforced        | Jour 1        |
|Rapide     | Enforced        |  Jour 3       |
|Larges     | Enforced        |  Jour 7       |


Vous pouvez suspendre ou restaurer le déploiement à tout moment pendant le déploiement. Pour ce faire, ouvrez une autre demande de service avec des opérations.

> [!NOTE]
> Si vous interrompez la publication d’une règle de signataire, cette règle doit être annulée ou terminée pour qu’un autre déploiement puisse démarrer.

## <a name="gather-publisher-details"></a>Collecter les détails de l’éditeur

Pour accéder aux données d’éditeur d’une application, procédez comme suit :

1. Recherchez un périphérique de bureau géré Microsoft dans l’anneau de test auquel une stratégie de mode audit est appliquée. 
2. Essayez d’installer l’application sur l’appareil.
3. Ouvrez l’observateur d’événements sur cet appareil. 
4. Dans l’observateur d’événements, accédez à **Logs\Microsoft\Windows d’applications et de services**, puis sélectionnez **AppLocker**. 
5. Recherchez un événement **8003** ou **8006** , puis copiez les informations à partir de l’événement : 
    - Nom de l’application 
    - Version de l’application 
    - Description 
    - Détails de l’éditeur (par exemple : "O = <publisher name> , L = <location> , S = État, C = pays") 