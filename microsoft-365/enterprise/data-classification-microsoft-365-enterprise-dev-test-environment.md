---
title: Classification des données pour votre environnement de test Microsoft 365 entreprise
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.custom:
- Ent_TLGs
- admindeeplinkMAC
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce guide de laboratoire de test pour créer et utiliser des étiquettes de rétention sur les documents de votre Microsoft 365 environnement de test d’entreprise.
ms.openlocfilehash: 6f6e57ec31d889fac031caf6cb6be94f483a93e9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60198504"
---
# <a name="data-classification-for-your-microsoft-365-for-enterprise-test-environment"></a>Classification des données pour votre environnement de test Microsoft 365 entreprise

*Ce guide de laboratoire de test peut être utilisé pour les environnements Microsoft 365'entreprise et Office 365 Entreprise test.*

Cet article explique comment configurer la classification des données à l’aide d’étiquettes de rétention dans votre Microsoft 365 environnement de test d’entreprise.

La classification des données dans votre environnement de test implique trois phases :
- [Phase 1 : Créer votre environnement de test Microsoft 365 entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Création d’étiquettes de rétention](#phase-2-create-retention-labels)
- [Phase 3 : Appliquer des étiquettes de rétention aux documents](#phase-3-apply-retention-labels-to-documents)

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile Microsoft 365 guide de laboratoire de test pour entreprise, Microsoft 365 pour la pile de guides de laboratoire de [test d’entreprise.](../downloads/Microsoft365EnterpriseTLGStack.pdf)
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 entreprise

Si vous souhaitez simplement configurer les étiquettes de rétention de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère.](lightweight-base-configuration-microsoft-365-enterprise.md)
  
Si vous souhaitez configurer des étiquettes de rétention dans une entreprise simulée, suivez les instructions de [l’authentification directe.](pass-through-auth-m365-ent-test-environment.md)
  
> [!NOTE]
> Le test des étiquettes de rétention ne nécessite pas l’environnement de test d’entreprise simulée, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Il est fourni ici en tant qu’option afin que vous pouvez tester la gestion automatisée des licences et l’appartenance à un groupe et l’expérimenter dans un environnement qui représente une organisation classique.

## <a name="phase-2-create-retention-labels"></a>Phase 2 : Création d’étiquettes de rétention

Dans cette phase, créez les étiquettes de rétention pour les différents niveaux de rétention pour SharePoint dossiers de documents en ligne :

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">centre Microsoft 365 sécurité avec</a> votre compte d’administrateur global.
1. Dans **l’onglet Accueil - Microsoft 365 de** sécurité de votre navigateur, sélectionnez   >  **Étiquettes de rétention de classification.**
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

Dans cette phase, vous découvrez le comportement des étiquettes de rétention par défaut pour les fichiers dans le dossier Documents d’un site SharePoint Online et modifiez manuellement l’étiquette de rétention d’un document.

Tout d’abord, créez un site d’équipe SharePoint Online de niveau sensible :
  
1. À l’aide d’une instance privée de votre navigateur, connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) à l’aide de votre compte d’administrateur global.
1. Dans la liste des vignettes, **sélectionnez SharePoint**.
1. Sous le nouvel **onglet SharePoint** dans votre navigateur, sélectionnez Créer **un site.**
1. Sur la page **Créer un site**, sélectionnez **Site d’équipe**.
1. Dans la **zone Nom du site d’équipe,** entrez **SensitiveFiles**.
1. Dans la **zone de description du site** d’équipe, entrez SharePoint site pour les fichiers **sensibles.**
1. Dans **les paramètres de confidentialité,** **sélectionnez Privé - seuls** les membres peuvent accéder à ce site, puis sélectionnez **Suivant**.
1. Dans le **Qui voulez-vous ajouter ?** volet, sélectionnez **Terminer**.
    
Ensuite, configurez le dossier Documents du site d’équipe SensitiveFiles pour l’étiquette de rétention Sensible.
  
1. Dans **l’onglet SensitiveFiles** de votre navigateur, sélectionnez **Documents**.
1. Sélectionnez **l Paramètres** icône, puis sélectionnez **Paramètres de la bibliothèque.**
1. Sous **Autorisations et gestion,** sélectionnez Appliquer une **étiquette aux éléments de cette liste ou bibliothèque.** Si cette option n’apparaît pas, vos étiquettes de rétention ne sont pas encore publiées. Essayez cette étape ultérieurement.
1. Dans **Paramètres-Appliquer une étiquette,** **sélectionnez Sensible** dans la zone de baisse, puis sélectionnez **Enregistrer.**

Ensuite, créez un document dans le site SensitiveFiles et modifiez son étiquette de rétention.
    
1. Dans le dossier documents, sélectionnez **Nouveau**  >  **document Word.**
1. Entrez du texte dans le document vide. Attendez que le texte soit enregistré.
1. Dans la barre de menus, sélectionnez **Documents partagés.**
1. À côté du **Document.docx** de fichier, sélectionnez les sélections verticales, puis sélectionnez **Détails.**
1. Dans le volet droit, dans la section **Propriétés,** sous Appliquer  l’étiquette de **rétention,** notez que l’étiquette de rétention Sensible a été automatiquement appliquée au document.
1. Cliquez sur **Modifier tout**.
1. Dans le **Document.docx,** sous Appliquer l’étiquette de **rétention,** sélectionnez l’étiquette **Hautement** confidentiel, puis sélectionnez **Enregistrer.**

## <a name="next-step"></a>Étape suivante

Explorez [d’autres fonctionnalités de protection](m365-enterprise-test-lab-guides.md#information-protection) des informations dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)