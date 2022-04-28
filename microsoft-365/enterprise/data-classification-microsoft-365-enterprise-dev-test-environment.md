---
title: Classification des données pour votre Microsoft 365 pour l’environnement de test d’entreprise
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.custom:
- Ent_TLGs
- admindeeplinkMAC
- admindeeplinkDEFENDER
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce guide de laboratoire de test pour créer et utiliser des étiquettes de rétention sur les documents de votre Microsoft 365 pour l’environnement de test d’entreprise.
ms.openlocfilehash: f5bcde88be148ed883b4ad10e3b8116ed21c9fa8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096807"
---
# <a name="data-classification-for-your-microsoft-365-for-enterprise-test-environment"></a>Classification des données pour votre Microsoft 365 pour l’environnement de test d’entreprise

*Ce guide de laboratoire de test peut être utilisé pour les Microsoft 365 pour les environnements de test d’entreprise et Office 365 Entreprise.*

Cet article explique comment configurer la classification des données à l’aide d’étiquettes de rétention dans votre Microsoft 365 pour l’environnement de test d’entreprise.

La classification des données dans votre environnement de test implique trois phases :
- [Phase 1 : Créer votre Microsoft 365 pour l’environnement de test d’entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Créer des étiquettes de rétention](#phase-2-create-retention-labels)
- [Phase 3 : Appliquer des étiquettes de rétention aux documents](#phase-3-apply-retention-labels-to-documents)

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Pour obtenir une carte visuelle de tous les articles du Microsoft 365 pour la pile des guides de laboratoire de test d’entreprise, accédez à [Microsoft 365 pour la pile des guides de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre Microsoft 365 pour l’environnement de test d’entreprise

Si vous souhaitez simplement configurer des étiquettes de rétention de manière légère avec les exigences minimales, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer des étiquettes de rétention dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des étiquettes de rétention ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt services de domaine Active Directory (AD DS). Il est fourni ici en tant qu’option afin que vous puissiez tester la gestion automatisée des licences et l’appartenance à un groupe et l’expérimenter dans un environnement qui représente une organisation classique.

## <a name="phase-2-create-retention-labels"></a>Phase 2 : Créer des étiquettes de rétention

Au cours de cette phase, créez les étiquettes de rétention pour les différents niveaux de rétention pour SharePoint dossiers de documents en ligne :

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> avec votre compte d’administrateur général.
1. Dans l’onglet **Accueil - Microsoft 365 sécurité** de votre navigateur, sélectionnez **Étiquettes ClassificationRetention** > .
1. Sélectionnez **Créer une étiquette**.
1. Dans le volet **Nom de votre étiquette** , entrez **Public interne** dans **Nom de votre étiquette**, puis sélectionnez **Suivant**.
1. Dans le volet **Descripteurs du plan** de fichiers, sélectionnez **Suivant**.
1. Dans le volet **Paramètres de l’étiquette** , si nécessaire, définissez **La rétention** **sur Activé**, puis sélectionnez **Suivant**.
1. Dans le volet **Vérifier vos paramètres** , sélectionnez **Créer l’étiquette**.
1. Répétez les étapes 3 à 7 pour les étiquettes supplémentaires avec ces noms :
  - Private
  - Sensible
  - Hautement confidentiel
1. Dans le volet **Étiquettes de rétention** , sélectionnez **Publier des étiquettes**.
1. Dans le volet **Choisir les étiquettes à publier** , **sélectionnez Choisir les étiquettes à publier**.
1. Dans le volet **Choisir des étiquettes** , sélectionnez **Ajouter** , puis sélectionnez les quatre étiquettes.
1. Sélectionnez **Ajouter**, puis **Terminé**.
1. Dans le volet **Choisir les étiquettes à publier** , sélectionnez **Suivant**.
1. Dans le volet **Choisir des emplacements** , sélectionnez **Suivant**.
1. Dans le volet **Nommer votre stratégie** , entrez **l’exemple d’organisation** dans **Nom**, puis sélectionnez **Suivant**.
1. Dans le volet **Vérifier vos paramètres** , sélectionnez **Publier des étiquettes**.
 
La publication des étiquettes de rétention peut prendre quelques minutes.

## <a name="phase-3-apply-retention-labels-to-documents"></a>Phase 3 : Appliquer des étiquettes de rétention aux documents

Au cours de cette phase, vous découvrez le comportement d’étiquette de rétention par défaut pour les fichiers dans le dossier Documents d’un site SharePoint Online et modifiez manuellement l’étiquette de rétention d’un document.

Tout d’abord, créez un site d’équipe SharePoint Online de niveau sensible :
  
1. À l’aide d’une instance privée de votre navigateur, connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> à l’aide de votre compte d’administrateur général.
1. Dans la liste des vignettes, sélectionnez **SharePoint**.
1. Sous le nouvel onglet **SharePoint** de votre navigateur, sélectionnez Créer un **site**.
1. Sur la page **Créer un site**, sélectionnez **Site d’équipe**.
1. Dans la zone **Nom du site d’équipe** , entrez **SensitiveFiles**.
1. Dans la zone **de description du site d’équipe**, entrez **SharePoint site pour les fichiers sensibles**.
1. Dans **paramètres de confidentialité**, sélectionnez **Privé : seuls les membres peuvent accéder à ce site**, puis sélectionnez **Suivant**.
1. Dans le **volet Qui voulez-vous ajouter ?** , sélectionnez **Terminer**.
    
Ensuite, configurez le dossier Documents du site d’équipe SensitiveFiles pour l’étiquette de rétention sensible.
  
1. Sous l’onglet **SensitiveFiles** de votre navigateur, sélectionnez **Documents**.
1. Sélectionnez l’icône **Paramètres**, puis sélectionnez **Paramètres de bibliothèque**.
1. Sous **Autorisations et gestion**, **sélectionnez Appliquer une étiquette aux éléments de cette liste ou bibliothèque**. Si cette option n’apparaît pas, vos étiquettes de rétention ne sont pas encore publiées. Essayez cette étape ultérieurement.
1. Dans **Paramètres-Appliquer l’étiquette**, sélectionnez **Sensible** dans la zone de liste déroulante, puis **sélectionnez Enregistrer**.

Ensuite, créez un document dans le site SensitiveFiles et modifiez son étiquette de rétention.
    
1. Dans le dossier documents, sélectionnez **Document NewWord** > .
1. Entrez du texte dans le document vide. Attendez que le texte soit enregistré.
1. Dans la barre de menus, sélectionnez **Documents partagés**.
1. En regard du **nom de fichierDocument.docx** , sélectionnez les points de suspension verticaux, puis sélectionnez **Détails**.
1. Dans le volet droit, dans la section **Propriétés** , sous **Appliquer l’étiquette de rétention**, notez que l’étiquette de rétention **sensible** a été appliquée automatiquement au document.
1. Cliquez sur **Modifier tout**.
1. Dans le volet **Document.docx** , sous **Appliquer l’étiquette de rétention**, sélectionnez l’étiquette **Hautement confidentiel** , puis **sélectionnez Enregistrer**.

## <a name="next-step"></a>Étape suivante

Explorez d’autres fonctionnalités et fonctionnalités de [protection des informations](m365-enterprise-test-lab-guides.md#information-protection) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)
