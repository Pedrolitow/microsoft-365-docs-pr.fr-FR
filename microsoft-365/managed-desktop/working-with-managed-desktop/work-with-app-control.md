---
title: Utiliser le contrôle d’application
description: ''
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 89ab1bf675c3668e01b31ff380f54ee993205374
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2022
ms.locfileid: "62281410"
---
# <a name="work-with-app-control"></a>Utiliser le contrôle d’application

Une fois que le contrôle d’application a été déployé dans votre environnement, vous et Microsoft Manged Desktop des opérations ont des responsabilités en cours. Par exemple, vous pouvez ajouter une nouvelle application dans l’environnement, ou ajouter (ou supprimer) un signataire approuvé. Pour améliorer la sécurité, toutes les applications doivent être signées par code avant de les publier pour les utilisateurs. Les détails de l’éditeur d’une application incluent des informations sur le signataire.

## <a name="add-a-new-app"></a>Ajout d’une nouvelle application

**Pour ajouter une nouvelle application :**

1. Ajoutez l’application [à Microsoft Intune](/mem/intune/apps/apps-win32-app-management).
1. Déployez l’application sur n’importe quel appareil de l’anneau Test.
1. Testez votre application en fonction de vos processus d’entreprise standard.
1. Vérifiez l’Observateur d’événements sous **Journaux des applications et des services\Microsoft\Windows\AppLocker**. Recherchez les **événements 8003** ou **8006** . Ces événements indiquent que l’application sera bloquée. Pour plus d’informations sur tous les événements App Locker et leurs significations, voir Utilisation de l’Observateur d’événements [avec AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/using-event-viewer-with-applocker).
1. Si vous trouvez l’un de ces événements, ouvrez une demande de signataire avec Microsoft Manged Desktop Operations.

## <a name="add-or-remove-a-trusted-signer"></a>Ajouter (ou supprimer) un signataire approuvé

Lorsque vous ouvrez une demande de signataire, vous devez d’abord fournir des détails importants sur l’éditeur.

**Pour ajouter (ou supprimer) un signataire approuvé :**

1. [Rassemblez les détails de l’éditeur](#gather-publisher-details).
1. Ouvrez un ticket avec Microsoft Manged Desktop Operations pour demander la règle du signataire et inclure les détails suivants :  

    - Nom de l’application
    - Version de l’application
    - Description
    - Type de modification (« ajouter » ou « supprimer »)  
    - Publisher détails détaillés (par exemple : « O=<publisher name>,L=<location>,S=State,C=Country »)

> [!NOTE]
> Pour supprimer l’confiance pour une application, suivez les mêmes étapes, mais définissez le **type de modification** à *supprimer*.

Les opérations déploieront progressivement des stratégies dans des groupes de déploiement en suivant cette planification :

|Groupe de déploiement  |Type de stratégie  |Calendrier  |
|---------|---------|---------|
|Tester     |  Audit       |  Jour 0       |
|Premier     | Enforced        | Jour 1        |
|Rapide     | Enforced        |  Jour 2       |
|Larges     | Enforced        |  Jour 3       |

Vous pouvez suspendre ou revenir en arrière le déploiement à tout moment pendant le déploiement. Pour suspendre ou revenir en arrière, ouvrez une autre demande de support avec Microsoft Manged Desktop Operations.

> [!NOTE]
> Si vous suspendez la publication d’une règle de signataire, cette règle doit être soit mise à jour, soit terminée avant qu’un autre déploiement puisse démarrer.

## <a name="gather-publisher-details"></a>Collecter les détails de l’éditeur

**Pour accéder aux données d’éditeur d’une application :**

1. Recherchez un Microsoft Manged Desktop de test sur l’anneau test sur la stratégie du mode Audit appliquée.
1. Essayez d’installer l’application sur l’appareil.
1. Ouvrez l’Observateur d’événements sur cet appareil.
1. Dans l’Observateur d’événements, accédez à Journaux des applications et des **services\Microsoft\Windows**, puis **sélectionnez AppLocker**.
1. Recherchez **un événement 8003** ou **8006** , puis copiez les informations de l’événement :

    - Nom de l’application
    - Version de l’application
    - Description
    - Publisher détails détaillés (par exemple : « O=<publisher name>, L=<location>, S=State, C=Country »)
