---
title: Sécurité Office 365 accrue pour votre environnement de test Microsoft 365 Entreprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce Guide de laboratoire de Test pour activer les paramètres de sécurité Office 365 supplémentaires à votre environnement de test Microsoft 365 pour entreprises.
ms.openlocfilehash: 62cf2347d3e003e9368c987912e7748029241501
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867106"
---
# <a name="increased-office-365-security-for-your-microsoft-365-enterprise-test-environment"></a>Sécurité Office 365 accrue pour votre environnement de test Microsoft 365 Entreprise

Les instructions de cet article, configurer les paramètres Office 365 supplémentaires pour renforcer la sécurité dans votre environnement de test Microsoft 365 pour entreprises.

![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Création de votre environnement de test Microsoft 365 pour entreprises

Si vous souhaitez simplement configurer une meilleure sécurité Office 365 dans une solution légère avec la configuration minimale requise, suivez les instructions de [configuration de base léger](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer une meilleure sécurité Office 365 dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test de renforcement de la sécurité Office 365 ne nécessite pas l’environnement de test simulé entreprise, qui comprend un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est fourni ici en tant qu’option afin que vous puissiez licences automatisé et l’appartenance au groupe de test et tester dans un environnement qui représente une organisation classique. 


## <a name="phase-2-configure-increased-office-365-security"></a>Phase 2 : Configurer une meilleure sécurité Office 365

Durant cette phase, vous activez une meilleure sécurité Office 365 pour votre environnement de test Microsoft 365 pour entreprises. Pour plus d’informations et les paramètres, consultez [configurer votre client Office 365 pour accroître la sécurité](https://docs.microsoft.com/office365/securitycompliance/tenant-wide-setup-for-increased-security).

### <a name="configure-sharepoint-online-to-block-apps-that-dont-support-modern-authentication"></a>Configurer SharePoint Online pour bloquer les applications qui ne prennent pas en charge l’authentification moderne

Les applications qui ne prennent pas en charge l’authentification moderne ne peut pas avoir d' [identité et périphérique d’accès aux configurations](microsoft-365-policies-configurations.md) appliquée, qui est un élément important de sécuriser votre abonnement Microsoft 365 et ses actifs numériques. 

1. Accédez au portail Office ([https://office.com](https://office.com)) et se connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.
    
  - Si vous utilisez l’environnement de test Microsoft 365 léger, connectez-vous à partir de votre ordinateur local.
    
  - Si vous utilisez l’environnement de test simulé entreprise Microsoft 365, utilisez le [portail Azure](https://portal.azure.com) pour se connecter à l’ordinateur virtuel CLIENT1 et puis se connecter à partir de CLIENT1.
 
2. Sous l’onglet **Centre d’administration Microsoft 365** , cliquez sur **Admin**.
3. Dans l’onglet **Centre d’administration Microsoft 365** nouveau, cliquez sur **centres d’administration > SharePoint**.
4. Dans l’onglet nouveau **Centre d’administration SharePoint** , cliquez sur **le contrôle d’accès**.
5. Sous **applications qui ne prennent en charge l’authentification moderne**, cliquez sur **Bloquer**, puis cliquez sur **OK**.


### <a name="enable-advanced-threat-protection-for-sharepoint-onedrive-for-business-and-microsoft-teams"></a>Activer les avancées de protection contre les menaces) pour SharePoint, OneDrive entreprise et les équipes Microsoft

Office 365 Advanced Threat Protection (DAV) est une fonctionnalité d’Exchange Online Protection (EOP) qui permet de conserver des programmes malveillants en dehors de votre courrier électronique. Avec DAV, vous créez des stratégies dans le centre d’administration Exchange (CAE) ou de la sécurité & centre de conformité qui permettent de garantir vos utilisateurs accéder uniquement des liens ou des pièces jointes dans les messages électroniques qui sont identifiés comme non malveillant. Pour plus d’informations, voir [protection contre les menaces avancées pour les pièces jointes fiables et les liens sécurisés](https://docs.microsoft.com/office365/securitycompliance/office-365-atp).

1. Dans l’onglet **Centre d’administration Microsoft 365** de votre navigateur, cliquez sur **centres d’administration > sécurité et conformité**.
2. Dans l’onglet **sécurité et conformité** nouveau, cliquez sur **Gestion des menaces > stratégie**.
3. Cliquez sur **les pièces jointes fiables DAV**.
4. Dans le volet **pièces jointes fiables** , sélectionnez **Activer DAV pour SharePoint, OneDrive et les équipes Microsoft**, puis cliquez sur **Enregistrer**.

### <a name="enable-anti-malware"></a>Activer les programmes malveillants

Programme malveillant est composé des virus et logiciels espions. Virus infectent autres programmes et des données, et ils répandent dans votre ordinateur que vous recherchez des programmes d’infection. Logiciels espions fait référence aux logiciels malveillants qui rassemble vos informations personnelles, telles que des données personnelles et les informations de connexion et l’envoie à l’auteur de programmes malveillants. 

Office 365 offre des programmes malveillants intégrée et les fonctionnalités qui permettent de protéger les messages entrants et sortants contre les logiciels malveillants et vous protéger contre le courrier indésirable de filtrage du courrier indésirable. Pour plus d’informations, consultez la rubrique [protection contre le courrier indésirable et anti-programme malveillant dans Office 365](https://docs.microsoft.com/office365/securitycompliance/anti-spam-and-anti-malware-protection)

Pour vous assurer que traitement anti-programme malveillant est en cours d’exécution sur les fichiers de types de fichiers courants :

1. Cliquez sur le bouton de retour de votre navigateur pour revenir à la page de **stratégie** .
2. Cliquez sur **contre les programmes malveillants**.
3. Double-cliquez sur la stratégie **par défaut**.
4. Dans la fenêtre **stratégie anti-programme malveillant** , cliquez sur **paramètres**.
4. Sous **filtre de pièce jointe courants**, cliquez sur **sur > Enregistrer**.


## <a name="phase-3-examine-office-365-security-tools-and-logs"></a>Phase 3 : Examiner les journaux et les outils de sécurité Office 365

Durant cette phase, vous examinez les services intégrés qui vous informent sur les événements de sécurité et mesurent vos défenses globale.

### <a name="threat-management-dashboard"></a>Tableau de bord de gestion des menaces

Gestion des menaces Office 365 peut vous aider à contrôler et gérer l’accès d’appareil mobile aux données de votre organisation, protéger votre organisation contre la perte de données et protéger les messages entrants et sortants à partir du courrier indésirable et les logiciels malveillants. Vous utilisez également threat management pour protéger la réputation de votre domaine et pour déterminer si les expéditeurs sont à des fins malveillantes usurpation de comptes à partir de votre domaine. Pour plus d’informations, voir [Gestion des menaces de la sécurité pour Microsoft Office 365 et le centre de conformité](https://docs.microsoft.com/office365/securitycompliance/threat-management).

Utilisez ces étapes pour afficher le tableau de bord de gestion Office 365 menace :

1. Dans l’onglet **Centre d’administration Microsoft 365** de votre navigateur, cliquez sur **centres d’administration > sécurité et conformité**.
2. Dans l’onglet **sécurité et conformité** nouveau, cliquez sur **Gestion des menaces > tableau de bord**.
3. Dans l’onglet nouveau **tableau de bord** dans votre navigateur, notez l’évolution des programmes malveillants, insights et autres sections du tableau de bord.

### <a name="office-365-cloud-app-security-dashboard"></a>Tableau de bord de sécurité des applications dans le nuage Office 365

Office 365 Cloud application sécurité, anciennement appelé Office 365 gestion avancée de sécurité, vous permet de créer des stratégies pour surveiller et vous informent des activités suspectes dans votre abonnement Office 365, afin que vous pouvez examiner et prendre possibles mesures correctives. Pour plus d’informations, voir [Vue d’ensemble d’Office 365 Cloud Application Security](https://docs.microsoft.com/office365/securitycompliance/office-365-cas-overview).

1. Dans l’onglet **Centre d’administration Microsoft 365** de votre navigateur, cliquez sur **centres d’administration > sécurité et conformité**.
2. Dans l’onglet **sécurité et conformité** nouveau, cliquez sur **alertes > Gestion avancée des alertes > accédez à la sécurité d’application Office 365 dans le nuage**.
3. Sous l’onglet **Sécurité du nuage application** nouvelle, notez l’affichage de tableau de bord et la liste des stratégies par défaut qui analyser pour les différentes activités dans votre abonnement Office 365.
4. Cliquez sur l’icône de tableau de bord pour consulter un résumé des activités de sécurité des applications dans le nuage sont suivis.
5. Cliquez sur **examiner** (l’icône LUNETTES), puis sur **journal d’activité** pour voir la liste des connexions récentes et autres activités.

### <a name="secure-score"></a>Sécuriser le Score

1. Créer un nouvel onglet dans votre navigateur et accédez à **securescore.office.com**.
2. Sous l' **onglet tableau de bord**, notez votre Score Secure actuel et la liste des actions dans la file d’attente pour augmenter votre score.

Voir l’étape de [configuration d’accroître la sécurité pour Office 365](increased-o365-security-microsoft-365-enterprise-dev-test-environment.md) dans la phase de **protection des informations** pour des informations et des liens pour configurer ces paramètres en production.

## <a name="next-step"></a>Étape suivante

Explorez les fonctionnalités supplémentaires de [protection des informations](m365-enterprise-test-lab-guides.md#information-protection) et fonctionnalités dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)

