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
ms.openlocfilehash: 31cc897fe28f557a65cba9c99e5dcecbf7c2b0e5
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50917639"
---
# <a name="work-with-app-control"></a>Utiliser le contrôle d’application

Une fois que le contrôle d’application a été déployé dans votre environnement, vous et les opérations Bureau géré Microsoft avez des responsabilités en cours. Par exemple, vous pouvez ajouter une nouvelle application dans l’environnement ou ajouter (ou supprimer) un signataire approuvé. Pour améliorer la sécurité, toutes les applications doivent être signées par code avant de les publier pour les utilisateurs. Les détails de l’éditeur d’une application incluent des informations sur le signataire.


## <a name="add-a-new-app"></a>Ajout d’une nouvelle application

Pour ajouter une nouvelle application, suivez les étapes suivantes :

1. Ajoutez l’application [à Microsoft Intune.](/mem/intune/apps/apps-win32-app-management)
2. Déployez l’application sur n’importe quel appareil de l’anneau Test. 
3. Testez votre application en fonction de vos processus d’entreprise standard. 
4. Vérifiez l’Observateur d’événements sous Journaux des applications et des **services\Microsoft\Windows\AppLocker**, en cherchant les **événements 8003** ou **8006.** Ces événements indiquent que l’application sera bloquée. Pour plus d’informations sur tous les événements App Locker et leurs significations, voir Utilisation de l’Observateur d’événements [avec AppLocker.](/windows/security/threat-protection/windows-defender-application-control/applocker/using-event-viewer-with-applocker)
5. Si vous trouvez l’un de ces événements, ouvrez une demande de signataire avec les opérations Bureau géré Microsoft.

## <a name="add-or-remove-a-trusted-signer"></a>Ajouter (ou supprimer) un signataire approuvé

Lorsque vous ouvrez une demande de signataire, vous devez d’abord fournir des détails importants sur l’éditeur. Ensuite, suivez les étapes suivantes :

1. [Rassemblez les détails de l’éditeur.](#gather-publisher-details)
2. Ouvrez un ticket avec microsoft Managed Desktop Operations pour demander la règle du signataire et inclure les détails suivants :  
    - Nom de l’application 
    - Version de l’application 
    - Description 
    - Type de modification (« ajouter » ou « supprimer »)  
    - Détails de l’éditeur (par exemple : « O= <publisher name> ,L= <location> ,S=State,C=Country ») 

> [!NOTE]
> Pour supprimer l’confiance pour une application, suivez les mêmes étapes, mais définissez **le type de modification** à *supprimer.*

Les opérations déploieront progressivement des stratégies dans des groupes de déploiement en suivant cette planification :


|Groupe de déploiement  |Type de stratégie  |Calendrier  |
|---------|---------|---------|
|Tester     |  Audit       |  Jour 0       |
|Premier     | Enforced        | Jour 1        |
|Rapide     | Enforced        |  Jour 2       |
|Larges     | Enforced        |  Jour 3       |


Vous pouvez suspendre ou revenir en arrière le déploiement à tout moment pendant le déploiement. Pour ce faire, ouvrez une autre demande de service avec Operations.

> [!NOTE]
> Si vous suspendez la publication d’une règle de signataire, cette règle doit être soit mise à jour, soit terminée avant qu’un autre déploiement puisse démarrer.

## <a name="gather-publisher-details"></a>Collecter les détails de l’éditeur

Pour accéder aux données d’éditeur d’une application, suivez les étapes suivantes :

1. Recherchez un appareil Bureau géré Microsoft dans l’anneau Test sur la stratégie mode Audit appliquée. 
2. Essayez d’installer l’application sur l’appareil.
3. Ouvrez l’Observateur d’événements sur cet appareil. 
4. Dans l’Observateur d’événements, accédez à Journaux des applications et **des services\Microsoft\Windows,** puis sélectionnez **AppLocker.** 
5. Recherchez **un événement 8003** ou **8006,** puis copiez les informations de l’événement : 
    - Nom de l’application 
    - Version de l’application 
    - Description 
    - Détails de l’éditeur (par exemple : « O= <publisher name> , L= <location> , S=State, C=Country »)