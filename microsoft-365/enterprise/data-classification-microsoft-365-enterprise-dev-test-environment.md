---
title: Classification des données pour votre environnement de test Microsoft 365 pour entreprise
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
description: Utilisez ce guide de laboratoire de test pour créer et utiliser des étiquettes de rétention sur des documents dans votre environnement de test Microsoft 365 pour entreprise.
ms.openlocfilehash: 5cc77167db866d99f0beea5f554a777ecf355046
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487731"
---
# <a name="data-classification-for-your-microsoft-365-for-enterprise-test-environment"></a>Classification des données pour votre environnement de test Microsoft 365 pour entreprise

*Ce guide de laboratoire de test peut être utilisé pour les environnements de test Microsoft 365 pour les entreprises et Office 365 Entreprise.*

Cet article explique comment configurer la classification des données à l’aide d’étiquettes de rétention dans votre environnement de test Microsoft 365 pour entreprise.

La classification des données dans votre environnement de test implique trois phases :
- [Phase 1 : Créer votre environnement de test Microsoft 365 pour entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Création d’étiquettes de rétention](#phase-2-create-retention-labels)
- [Phase 3 : Appliquer des étiquettes de rétention aux documents](#phase-3-apply-retention-labels-to-documents)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Pour obtenir un plan visuel de tous les articles de la pile du Guide de laboratoire de test Microsoft 365 pour entreprise, allez à [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 pour entreprise

Si vous souhaitez simplement configurer les étiquettes de rétention de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère.](lightweight-base-configuration-microsoft-365-enterprise.md)
  
Si vous souhaitez configurer des étiquettes de rétention dans une entreprise simulée, suivez les instructions de [l’authentification directe.](pass-through-auth-m365-ent-test-environment.md)
  
> [!NOTE]
> Le test des étiquettes de rétention ne nécessite pas l’environnement de test d’entreprise simulée, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Il est fourni ici en tant qu’option afin que vous pouvez tester la gestion automatisée des licences et l’appartenance à un groupe et l’expérimenter dans un environnement qui représente une organisation classique.

## <a name="phase-2-create-retention-labels"></a>Phase 2 : Création d’étiquettes de rétention

Dans cette phase, créez les étiquettes de rétention pour les différents niveaux de rétention pour les dossiers de documents SharePoint Online :

1. Connectez-vous au Centre de sécurité [Microsoft 365](https://security.microsoft.com/homepage) avec votre compte d’administrateur global.
1. Dans **l’onglet Accueil - Sécurité Microsoft 365** de votre navigateur, sélectionnez   >  **Étiquettes de rétention de classification.**
1. Sélectionnez **Créer une étiquette**.
1. Dans le **volet Nom de votre étiquette,** entrez Public **interne** dans Nom de votre **étiquette,** puis sélectionnez **Suivant**.
1. Dans le **volet Descripteurs du plan de fichiers,** sélectionnez **Suivant.**
1. Dans le **volet Paramètres de l’étiquette,** si nécessaire, définissez rétention **sur Sur,** puis sélectionnez **Suivant**. 
1. Dans le **volet Examiner vos paramètres,** **sélectionnez Créer l’étiquette.**
1. Répétez les étapes 3 à 7 pour les étiquettes supplémentaires avec ces noms :
  - Private
  - Sensible
  - Hautement confidentiel
1. Dans le volet **Étiquettes de** rétention, **sélectionnez Publier des étiquettes.**
1. Dans le **volet Choisir les étiquettes à** publier, sélectionnez Choisir les **étiquettes à publier.**
1. Dans le volet Choisir **des étiquettes,** **sélectionnez Ajouter** et sélectionnez les quatre étiquettes.
1. **Sélectionnez** Ajouter, puis **Terminé**.
1. Dans le **volet Choisir les étiquettes à** publier, sélectionnez **Suivant.**
1. Dans le **volet Choisir des** emplacements, sélectionnez **Suivant.**
1. Dans le **volet Nom de votre** stratégie, entrez Exemple **d’organisation** dans **Nom,** puis sélectionnez **Suivant**.
1. Dans le **volet Examiner vos paramètres,** sélectionnez **Publier des étiquettes.**
 
La publication des étiquettes de rétention peut prendre quelques minutes.

## <a name="phase-3-apply-retention-labels-to-documents"></a>Phase 3 : Appliquer des étiquettes de rétention aux documents

Dans cette phase, vous découvrez le comportement par défaut des étiquettes de rétention pour les fichiers dans le dossier Documents d’un site SharePoint Online et modifiez manuellement l’étiquette de rétention d’un document.

Tout d’abord, créez un site d’équipe SharePoint Online de niveau sensible :
  
1. À l’aide d’une instance privée de votre navigateur, connectez-vous au Centre d’administration [Microsoft 365](https://admin.microsoft.com) à l’aide de votre compte d’administrateur global.
1. Dans la liste des vignettes, **sélectionnez SharePoint.**
1. Sous le nouvel **onglet SharePoint** de votre navigateur, sélectionnez **Créer un site.**
1. Sur la page **Créer un site**, sélectionnez **Site d’équipe**.
1. Dans la **zone Nom du site d’équipe,** entrez **SensitiveFiles**.
1. Dans la **zone de description du site** d’équipe, entrez le site **SharePoint pour les fichiers sensibles.**
1. Dans **les paramètres de confidentialité,** **sélectionnez Privé - seuls** les membres peuvent accéder à ce site, puis sélectionnez **Suivant**.
1. Dans le **volet Qui voulez-vous ajouter ?** sélectionnez **Terminer.**
    
Ensuite, configurez le dossier Documents du site d’équipe SensitiveFiles pour l’étiquette de rétention Sensible.
  
1. Dans **l’onglet SensitiveFiles** de votre navigateur, sélectionnez **Documents**.
1. Sélectionnez **l’icône Paramètres,** puis sélectionnez **Paramètres de la bibliothèque.**
1. Sous **Autorisations et gestion,** **sélectionnez Appliquer une étiquette aux éléments de cette liste ou bibliothèque.** Si cette option n’apparaît pas, vos étiquettes de rétention ne sont pas encore publiées. Essayez cette étape ultérieurement.
1. Dans **Paramètres - Appliquer l’étiquette,** **sélectionnez Sensible** dans la zone de mise en question, puis **sélectionnez Enregistrer.**

Ensuite, créez un document dans le site SensitiveFiles et modifiez son étiquette de rétention.
    
1. Dans le dossier documents, sélectionnez **Nouveau**  >  **document Word.**
1. Entrez du texte dans le document vide. Attendez que le texte soit enregistré.
1. Dans la barre de menus, sélectionnez **Documents partagés.**
1. EnDocument.docxnom **de** fichier, sélectionnez les sélections verticales, puis sélectionnez **Détails.**
1. Dans le volet droit, dans la section **Propriétés,** sous Appliquer  l’étiquette de **rétention,** notez que l’étiquette de rétention Sensible a été automatiquement appliquée au document.
1. Cliquez sur **Modifier tout**.
1. Dans le **Document.docx,** sous Appliquer l’étiquette de **rétention,** sélectionnez l’étiquette **Hautement** confidentiel, puis sélectionnez **Enregistrer.**

## <a name="next-step"></a>Étape suivante

Explorez [d’autres fonctionnalités de protection](m365-enterprise-test-lab-guides.md#information-protection) des informations dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
