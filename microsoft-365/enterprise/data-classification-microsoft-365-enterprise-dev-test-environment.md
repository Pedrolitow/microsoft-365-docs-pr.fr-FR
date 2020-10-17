---
title: Classification des données pour votre environnement de test Microsoft 365 pour les entreprises
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
description: Utilisez ce guide de laboratoire de test pour créer et utiliser des étiquettes de rétention sur des documents dans votre environnement de test Microsoft 365 pour les entreprises.
ms.openlocfilehash: 5cc77167db866d99f0beea5f554a777ecf355046
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487731"
---
# <a name="data-classification-for-your-microsoft-365-for-enterprise-test-environment"></a>Classification des données pour votre environnement de test Microsoft 365 pour les entreprises

*Ce guide de laboratoire de test peut être utilisé pour les environnements de test Microsoft 365 pour les environnements de test d’entreprise et Office 365.*

Cet article explique comment configurer la classification des données à l’aide d’étiquettes de rétention dans votre environnement de test Microsoft 365 pour entreprise.

La classification des données dans votre environnement de test comprend trois phases :
- [Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : créer des étiquettes de rétention](#phase-2-create-retention-labels)
- [Phase 3 : appliquer des étiquettes de rétention aux documents](#phase-3-apply-retention-labels-to-documents)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Pour obtenir un plan de tous les Articles de la pile de guide de laboratoire de test Microsoft 365 pour Enterprise, accédez à [Microsoft 365 pour la pile de guide de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises

Si vous souhaitez simplement configurer des étiquettes de rétention de manière simple avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer des étiquettes de rétention dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des étiquettes de rétention ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester les licences automatiques et les appartenances aux groupes et de les tester dans un environnement qui représente une organisation typique.

## <a name="phase-2-create-retention-labels"></a>Phase 2 : créer des étiquettes de rétention

Dans cette phase, créez les étiquettes de rétention pour les différents niveaux de rétention pour les dossiers de documents SharePoint Online :

1. Connectez-vous au [Centre de sécurité Microsoft 365](https://security.microsoft.com/homepage) avec votre compte d’administrateur général.
1. À partir de l’onglet **Accueil-Microsoft 365 sécurité** de votre navigateur, sélectionnez **classification**des  >  **étiquettes de rétention**.
1. Sélectionnez **Créer une étiquette**.
1. Dans le volet **nom de l’étiquette** , entrez **public interne** dans **nom de votre étiquette**, puis cliquez sur **suivant**.
1. Dans le volet **fichiers de descripteurs de plan de fichiers** , sélectionnez **suivant**.
1. Dans le volet **paramètres d’étiquette** , si nécessaire, définissez **rétention** **sur activé**, puis cliquez sur **suivant**.
1. Dans le volet **vérifier vos paramètres** , sélectionnez **créer l’étiquette**.
1. Répétez les étapes 3 à 7 pour les étiquettes supplémentaires avec ces noms :
  - Private
  - Sensible
  - Hautement confidentiel
1. Dans le volet **étiquettes de rétention** , sélectionnez **publier les étiquettes**.
1. Dans le volet **choisir les étiquettes à publier** , sélectionnez **choisir les étiquettes à publier**.
1. Dans le volet **choisir des étiquettes** , sélectionnez **Ajouter** , puis sélectionnez les quatre étiquettes.
1. Sélectionnez **Ajouter**, puis sélectionnez **Terminer**.
1. Dans le volet **choisir les étiquettes à publier** , sélectionnez **suivant**.
1. Dans le volet **choisir les emplacements** , sélectionnez **suivant**.
1. Dans le **volet nom de votre stratégie** , saisissez **exemple d’organisation** dans **nom**, puis cliquez sur **suivant**.
1. Dans le volet **vérifier vos paramètres** , sélectionnez **publier les étiquettes**.
 
La publication des étiquettes de rétention peut prendre quelques minutes.

## <a name="phase-3-apply-retention-labels-to-documents"></a>Phase 3 : appliquer des étiquettes de rétention aux documents

Dans cette phase, vous découvrez le comportement par défaut de l’étiquette de rétention pour les fichiers du dossier Documents d’un site SharePoint Online et vous modifiez manuellement l’étiquette de rétention d’un document.

Tout d’abord, créez un site d’équipe SharePoint Online de niveau sensible :
  
1. À l’aide d’une instance privée de votre navigateur, connectez-vous au [Centre d’administration 365 de Microsoft](https://admin.microsoft.com) à l’aide de votre compte d’administrateur général.
1. Dans la liste des vignettes, sélectionnez **SharePoint**.
1. Dans le nouvel onglet **SharePoint** de votre navigateur, sélectionnez **créer un site**.
1. Sur la page **Créer un site**, sélectionnez **Site d’équipe**.
1. Dans la zone **nom du site d’équipe** , entrez **SensitiveFiles**.
1. Dans la zone **Description du site d’équipe** , entrez **site SharePoint pour les fichiers sensibles**.
1. Dans **paramètres de confidentialité**, sélectionnez **privé-seuls les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.
1. Dans le volet **qui voulez-vous ajouter ?** , sélectionnez **Terminer**.
    
Ensuite, configurez le dossier des documents du site d’équipe SensitiveFiles pour l’étiquette de rétention sensible.
  
1. Dans l’onglet **SensitiveFiles** de votre navigateur, sélectionnez **documents**.
1. Sélectionnez l’icône **paramètres** , puis sélectionnez Paramètres de la **bibliothèque**.
1. Sous **autorisations et gestion**, sélectionnez **appliquer une étiquette aux éléments de cette liste ou bibliothèque**. Si cette option ne s’affiche pas, vos étiquettes de rétention ne sont pas encore publiées. Essayez cette étape ultérieurement.
1. Dans **paramètres-appliquer l’étiquette**, sélectionnez **sensible** dans la zone de liste déroulante, puis sélectionnez **Enregistrer**.

Ensuite, créez un nouveau document dans le site SensitiveFiles et modifiez son étiquette de rétention.
    
1. Dans le dossier documents, sélectionnez **nouveau**  >  **document Word**.
1. Entrez du texte dans le document vide. Attendez que le texte soit enregistré.
1. Dans la barre de menus, sélectionnez **documents partagés**.
1. En regard du **Document.docx** nom de fichier, sélectionnez les points de suspension verticaux, puis sélectionnez **Détails**.
1. Dans le volet droit, dans la section **Propriétés** , sous **appliquer l’étiquette de rétention**, Notez que l’étiquette de rétention **sensible** a été automatiquement appliquée au document.
1. Cliquez sur **Editer tout **.
1. Dans le volet **Document.docx** , sous **appliquer une étiquette de rétention**, sélectionnez l’étiquette **hautement confidentiel** , puis sélectionnez **Enregistrer**.

## <a name="next-step"></a>Étape suivante

Découvrez les fonctionnalités et les fonctionnalités de [protection des informations](m365-enterprise-test-lab-guides.md#information-protection) supplémentaires dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 pour entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
