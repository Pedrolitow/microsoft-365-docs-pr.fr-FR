---
title: Classification des données pour votre environnement de test Microsoft 365 Enterprise
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-security-compliance
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce guide de laboratoire de test pour créer et utiliser des étiquettes de rétention Office 365 sur des documents dans votre environnement de test Microsoft 365 Enterprise.
ms.openlocfilehash: 6534eff67e9c91423eb6f81415cb3ef2e965dcc1
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42067991"
---
# <a name="data-classification-for-your-microsoft-365-enterprise-test-environment"></a>Classification des données pour votre environnement de test Microsoft 365 Enterprise

*Ce Guide de Laboratoire Test peut être utilisé pour les environnements de test Microsoft 365 Enterprise et Office 365 Enterprise.*

Avec les instructions de cet article, vous configurez la classification des données à l’aide des étiquettes de rétention Office 365 dans votre environnement de test Microsoft 365 entreprise.

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Créer l’environnement de test Microsoft 365 Entreprise.

Si vous souhaitez simplement configurer des étiquettes de rétention Office 365 de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer des étiquettes de rétention Office 365 dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des étiquettes de rétention Office 365 ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester les licences automatiques et les appartenances aux groupes et de les tester dans un environnement qui représente une organisation typique. 

## <a name="phase-2-create-office-365-retention-labels"></a>Phase 2 : créer des étiquettes de rétention Office 365

Dans cette phase, vous allez créer les étiquettes de rétention pour les différents niveaux de rétention pour les dossiers de documents SharePoint Online.

1. Connectez-vous au [Centre de sécurité Microsoft 365](https://security.microsoft.com/homepage) avec votre compte d’administrateur général.
    
2. À partir de l’onglet **Accueil-Microsoft 365 sécurité** de votre navigateur, cliquez sur **classification > étiquettes de rétention**.
    
3. Cliquez sur **Créer une étiquette**.
    
4. Dans le volet **nom de l’étiquette** , tapez **public interne** dans **nom de votre étiquette**, puis cliquez sur **suivant**.

5. Dans le volet **fichiers de descripteurs de plan de fichiers** , cliquez sur **suivant**.
    
6. Dans le volet **paramètres d’étiquette** , si nécessaire, définissez **rétention** **sur activé**, puis cliquez sur **suivant**.
    
7. Dans le volet **vérifier vos paramètres** , cliquez sur **créer l’étiquette**.
    
8. Répétez les étapes 3 à 7 pour les étiquettes supplémentaires avec ces noms :
    
  - Private
    
  - Sensible
    
  - Hautement confidentiel
  
9. Dans le volet **étiquettes de rétention** , cliquez sur **publier les étiquettes**.
    
10. Dans le volet **choisir les étiquettes à publier** , cliquez sur **choisir les étiquettes à publier**.
    
11. Dans le volet **choisir des étiquettes** , cliquez sur **Ajouter** et sélectionnez les quatre étiquettes.
    
12. Cliquez sur **Ajouter**, puis sur **Terminer**.
    
13. Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Suivant**.
    
14. Dans le volet **Choisir les emplacements**, cliquez sur **Suivant**.
    
15. Dans le volet **Nom de votre stratégie**, saisissez **Exemple d’organisation** sous **Nom**, puis cliquez sur **Suivant**.
    
16. Dans le volet **vérifier vos paramètres** , cliquez sur **publier les étiquettes**.
 
Notez que la publication des étiquettes de rétention peut prendre quelques minutes.

## <a name="phase-3-apply-office-365-retention-labels-to-documents"></a>Phase 3 : appliquer des étiquettes de rétention Office 365 à des documents

Dans cette phase, vous découvrez le comportement par défaut de l’étiquette de rétention pour les fichiers du dossier Documents d’un site SharePoint Online et vous modifiez manuellement l’étiquette de rétention d’un document.

Tout d’abord, créez un site d’équipe SharePoint Online de niveau sensible :
  
1. À l’aide d’une instance privée de votre navigateur, connectez-vous au [portail Office 365](https://portal.office.com) à l’aide de votre compte d’administrateur général.
    
2. Dans la liste des vignettes, cliquez sur **SharePoint**.
    
3. Dans le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **créer un site**.
    
4. Dans la page **Créer un site**, cliquez sur **Site d’équipe**.
    
5. Dans **nom du site d’équipe**, tapez **SensitiveFiles**.
    
6. Dans **Description du site d’équipe**, tapez **site SharePoint pour les fichiers sensibles**.
    
7.  Dans **Paramètres de confidentialité**, sélectionnez **Privé - Seuls les membres peuvent accéder à ce site**, puis cliquez sur **Suivant**.
    
8. Dans le volet **qui voulez-vous ajouter ?** , cliquez sur **Terminer**.
    
Ensuite, configurez le dossier des documents du site d’équipe SensitiveFiles pour l’étiquette de rétention sensible.
  
1. Dans l’onglet **SensitiveFiles** de votre navigateur, cliquez sur **documents**.
    
2. Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
    
3. Sous **autorisations et gestion**, cliquez sur **appliquer une étiquette aux éléments de cette liste ou bibliothèque**. Si cette option ne s’affiche pas, vos étiquettes de rétention ne sont pas encore publiées. Essayez cette étape ultérieurement.
    
4. Dans **paramètres-appliquer l’étiquette**, sélectionnez **sensible** dans la zone de liste déroulante, puis cliquez sur **Enregistrer**.

Ensuite, créez un nouveau document dans le site SensitiveFiles et modifiez son étiquette de rétention.
    
1. Dans le dossier documents, cliquez sur **nouveau > document Word**.
    
2. Tapez du texte dans le document vide. Attendez que le texte soit enregistré.
    
3. Dans la barre de menus, cliquez sur **documents partagés**.
    
4. Cliquez sur les points de suspension verticaux en regard du nom du fichier **document. docx** , puis cliquez sur **Détails**.
    
5. Dans le volet de droite, dans la section **Propriétés** , sous **appliquer l’étiquette de rétention**, Notez que l’étiquette de rétention **sensible** a été automatiquement appliquée au document.
    
6. Cliquez sur **modifier tout**.
    
7. Dans le volet **document. docx** , sous **appliquer une étiquette de rétention**, sélectionnez l’étiquette **hautement confidentiel** , puis cliquez sur **Enregistrer**.

Voir l’étape [configure Classification for your Environment](infoprotect-configure-classification.md) dans la phase **information protection** pour obtenir des informations et des liens vers la façon de déployer des étiquettes de rétention Office 365 en production.

## <a name="next-step"></a>Étape suivante

Découvrez les fonctionnalités et les fonctionnalités de [protection des informations](m365-enterprise-test-lab-guides.md#information-protection) supplémentaires dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)

 
