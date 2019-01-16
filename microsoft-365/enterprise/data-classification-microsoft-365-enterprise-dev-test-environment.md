---
title: Environnement de test de classification des données pour votre entreprise 365 de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce Guide de laboratoire de Test pour créer et utiliser des étiquettes de Office 365 sur des documents dans votre environnement de test Microsoft 365 pour entreprises.
ms.openlocfilehash: 33ac1fa8e26c0037882e6c240cc04ec19e6a6a7b
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867453"
---
# <a name="data-classification-for-your-microsoft-365-enterprise-test-environment"></a>Environnement de test de classification des données pour votre entreprise 365 de Microsoft

Les instructions de cet article, vous permet de configurer la classification des données à l’aide des étiquettes de rétention d’Office 365 dans votre environnement de test Microsoft 365 pour entreprises.

![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Création de votre environnement de test Microsoft 365 pour entreprises

Si vous souhaitez simplement configurer des étiquettes d’Office 365 dans une solution légère avec la configuration minimale requise, suivez les instructions de [configuration de base léger](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer des étiquettes d’Office 365 dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test des étiquettes d’Office 365 ne nécessite pas l’environnement de test simulé entreprise, qui comprend un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est fourni ici en tant qu’option afin que vous puissiez licences automatisé et l’appartenance au groupe de test et tester dans un environnement qui représente une organisation classique. 

## <a name="phase-2-create-office-365-labels"></a>Phase 2 : Création d’étiquettes Office 365

Dans cette phase, vous créez les étiquettes pour les différents niveaux de rétention pour les dossiers de documents SharePoint Online.
  
1. Si nécessaire, utilisez une instance privée de votre navigateur Internet et connectez-vous au portail Office avec votre compte d’administrateur global. Pour une assistance, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Sous l’onglet **Accueil Microsoft Office**, cliquez sur la vignette **Administration**.
    
3. Sous le nouvel onglet **Centre d’administration Office** de votre navigateur, cliquez sur **Centres d’administration > Sécurité &amp; conformité**.
    
4. À partir du nouveau **Accueil - sécurité &amp; conformité** onglet de votre navigateur, cliquez sur **Classifications > étiquettes**. À partir de le **Accueil > étiquettes** volet, cliquez sur l’onglet de **rétention** .
    
5. Cliquez sur **créer une étiquette**.
    
6. Dans le volet **Nom de l’étiquette**, saisissez **Interne public** et cliquez sur **Suivant**.
    
7. Dans le volet **Paramètres de l’étiquette**, cliquez sur **Suivant**.
    
8. Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer cette étiquette**, puis cliquez sur **Fermer**.
    
9. Répétez les étapes 5 à 8 pour les autres étiquettes suivantes :
    
  - Privé
    
  - Sensible
    
  - Hautement confidentiel
    
10. Dans le volet **Accueil > Étiquettes**, cliquez sur **Publier des étiquettes**.
    
11. Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Choisir les étiquettes à publier**.
    
12. Dans le volet **Choisir des étiquettes**, cliquez sur **Ajouter** et sélectionnez les quatre étiquettes.
    
13. Cliquez sur **Terminé**.
    
14. Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Suivant**.
    
15. Dans le volet **Choisir les emplacements**, cliquez sur **Suivant**.
    
16. Dans le volet **Nom de votre stratégie**, saisissez **Exemple d’organisation** sous **Nom**, puis cliquez sur **Suivant**.
    
17. Dans le volet **Vérifier vos paramètres**, cliquez sur **Publier les étiquettes**, puis sur **Fermer**.

Notez qu’il peut prendre quelques minutes pour les étiquettes à publier.

## <a name="phase-3-apply-office-365-retention-labels-to-documents"></a>Phase 3 : Appliquer des étiquettes de rétention d’Office 365 à des documents

Durant cette phase, vous découvrez le comportement d’étiquette par défaut pour les fichiers dans le dossier Documents d’un site SharePoint Online et modifiez manuellement l’étiquette d’un document.

Tout d’abord, créez un site d’équipe SharePoint Online niveau critiques :
  
1. À l’aide d’un navigateur sur votre ordinateur local, connectez-vous au portail Office à l’aide de votre compte d’administrateur global. Pour une assistance, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Dans le nouvel onglet **SharePoint** dans votre navigateur, cliquez sur **créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **nom du site d’équipe**, tapez **SensitiveFiles**.
    
6. Dans la **description du site d’équipe**, tapez **le site SharePoint pour les fichiers sensibles**.
    
7.  Dans **Paramètres de confidentialité**, sélectionnez **Privé - Seuls les membres peuvent accéder à ce site**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.
    
Ensuite, configurez le dossier Documents du site d’équipe pour l’étiquette sensible SensitiveFiles.
  
1. Dans l’onglet **SensitiveFiles** de votre navigateur, cliquez sur **Documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
    
4. Dans **Les paramètres s’appliquent une étiquette**, sélectionnez **sensibles** dans la zone de liste déroulante, puis cliquez sur **Enregistrer**.

Ensuite, créez un nouveau document dans le site SensitiveFiles et modifier son étiquette.
    
1. Dans le dossier documents, cliquez sur **Nouveau > document Word**.
    
2. Tapez du texte dans le document. Attendez que le texte à enregistrer.
    
3. Dans la barre de menus, cliquez sur **Documents partagés**.
    
4. Cliquez sur l’icône en regard du nom de fichier **Document.docx** Word.
    
5. Dans le volet droit, dans la section **Propriétés** , sous l' **étiquette de rétention appliquer**, notez que le document a été l’étiquette **sensibles** appliquée automatiquement.
    
6. Cliquez sur **Modifier tous les**.
    
7. Dans le volet **Document.docx** , sous l' **étiquette de l’appliquer**, sélectionnez l’étiquette **Hautement confidentielles** , puis cliquez sur **Enregistrer**.

Dans la phase de **protection des informations** pour des informations et des liens vers les étiquettes de rétention d’Office 365 en production, voir l’étape de [classification configurer pour votre environnement](infoprotect-configure-classification.md) .

## <a name="next-step"></a>Étape suivante

Explorez les fonctionnalités supplémentaires de [protection des informations](m365-enterprise-test-lab-guides.md#information-protection) et fonctionnalités dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)

 