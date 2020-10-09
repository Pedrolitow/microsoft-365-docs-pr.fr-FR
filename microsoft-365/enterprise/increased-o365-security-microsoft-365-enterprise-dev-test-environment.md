---
title: Amélioration de la sécurité Microsoft 365 pour votre environnement de test Microsoft 365 pour les entreprises
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-security-compliance
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce guide de laboratoire de test pour activer des paramètres de sécurité Microsoft 365 supplémentaires pour votre environnement de test Microsoft 365.
ms.openlocfilehash: 09a613261bc173cd71e9cc2dd58a32a9547ece21
ms.sourcegitcommit: cd17328baa58448214487e3e68c37590ab9fd08d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48398948"
---
# <a name="increased-microsoft-365-security-for-your-microsoft-365-for-enterprise-test-environment"></a>Amélioration de la sécurité Microsoft 365 pour votre environnement de test Microsoft 365 pour les entreprises

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Les instructions de cet article vous permettent de configurer des paramètres supplémentaires de Microsoft 365 pour renforcer la sécurité dans votre environnement de test Microsoft 365 pour les entreprises.

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan visuel de tous les articles de l’ensemble des guides de laboratoire de test de Microsoft 365 pour entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises

Si vous souhaitez simplement configurer une sécurité Microsoft 365 accrue de façon légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer la sécurité Microsoft 365 améliorée dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test la sécurité améliorée de Microsoft 365 ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester les licences automatiques et les appartenances aux groupes et de les tester dans un environnement qui représente une organisation typique. 

## <a name="phase-2-configure-increased-microsoft-365-security"></a>Phase 2 : configuration de la sécurité Microsoft 365 améliorée

Dans cette phase, vous allez activer la sécurité Microsoft 365 pour votre environnement de test Microsoft 365 pour les entreprises. Pour plus d’informations et de paramètres, consultez [la rubrique Configure Your Client for major Security](https://docs.microsoft.com/office365/securitycompliance/tenant-wide-setup-for-increased-security).

### <a name="configure-sharepoint-online-to-block-apps-that-dont-support-modern-authentication"></a>Configurer SharePoint Online pour bloquer les applications qui ne prennent pas en charge l’authentification moderne

Les applications qui ne prennent pas en charge l’authentification moderne ne peuvent pas avoir de [configurations d’identité et d’accès aux appareils](../security/office-365-security/microsoft-365-policies-configurations.md) appliquées, ce qui est un élément important de la sécurisation de votre abonnement Microsoft 365 et de ses biens numériques. 

1. Accédez au centre d’administration Microsoft 365 ( [https://portal.microsoft.com](https://portal.microsoft.com) ) et connectez-vous à votre abonnement de laboratoire de test microsoft 365 avec votre compte d’administrateur général.
    
  - Si vous utilisez l’environnement de test Microsoft 365 léger, connectez-vous à partir de votre ordinateur local.
    
  - Si vous utilisez l’environnement de test d’entreprise simulé de Microsoft 365, utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de client1.
 
2. Dans le nouvel onglet **Centre d’administration Microsoft 365** , sous **centres d’administration** dans le volet de navigation de gauche, cliquez sur **SharePoint**.
3. Dans le nouvel onglet **Centre d’administration SharePoint** , cliquez sur **stratégies > contrôle d’accès**.
4. Cliquez sur **applications qui ne prennent pas en charge l’authentification moderne**, sélectionnez **bloquer l’accès**, puis cliquez sur **Enregistrer**.


### <a name="enable-advanced-threat-protection-for-sharepoint-onedrive-for-business-and-microsoft-teams"></a>Activer la protection avancée contre les menaces pour SharePoint, OneDrive entreprise et Microsoft teams

Office 365 Advanced Threat Protection (ATP) for SharePoint, OneDrive et Microsoft teams protège votre organisation contre le partage accidentel de fichiers malveillants.

1. Accédez au [Centre de sécurité & conformité](https://protection.office.com) et connectez-vous avec votre compte d’administrateur général.

2. Dans le volet de navigation de gauche, sous **gestion des menaces**, cliquez sur **stratégie**, puis sur **pièces jointes approuvées ATP**. 

3. Sous **protéger les fichiers dans SharePoint, OneDrive et Microsoft teams**. Sélectionnez Activer la protection avancée contre **les menaces pour SharePoint, OneDrive et Microsoft teams**.

4. Cliquez sur **Enregistrer**.


### <a name="enable-anti-malware"></a>Activer le blocage des programmes malveillants

Les programmes malveillants sont constitués de virus et de logiciels espions. Les virus contaminent d'autres programmes et données, et ils se propagent dans votre ordinateur à la recherche de programmes à infecter. Les logiciels espions font référence aux programmes malveillants qui recueillent vos informations personnelles, telles que les informations de connexion et les données personnelles, et les renvoient à l’auteur de programmes malveillants. 

Microsoft 365 dispose de fonctionnalités intégrées de filtrage des courriers indésirables et des programmes malveillants qui permettent de protéger les messages entrants et sortants des logiciels malveillants et de vous protéger contre le courrier indésirable. Pour plus d’informations, consultez la rubrique [anti-spam & la protection contre les programmes malveillants](../security/office-365-security/anti-spam-and-anti-malware-protection.md).

Pour vérifier que le traitement anti-programme malveillant est effectué sur des fichiers avec des types de fichiers de pièces jointes courants :

1. Cliquez sur le bouton précédent de votre navigateur pour revenir à la page **stratégie** .
2. Cliquez sur **anti-programme malveillant**.
3. Double-cliquez sur la stratégie nommée **default**.
4. Dans la fenêtre **stratégie anti-programme malveillant** , cliquez sur **paramètres**.
4. Sous **Common Attachment types Filter**, sélectionnez **activé**, puis cliquez sur **Enregistrer**.


## <a name="phase-3-examine-the-security-dashboard"></a>Phase 3 : examiner le tableau de bord de sécurité

La gestion des menaces dans Microsoft 365 vous permet de contrôler et de gérer l’accès des appareils mobiles aux données de votre organisation, de protéger votre organisation contre la perte de données et de protéger les messages entrants et sortants contre les logiciels malveillants et le courrier indésirable. Vous pouvez également utiliser la gestion des menaces pour protéger la réputation de votre domaine et déterminer si les expéditeurs sont ou non usurpés de manière malveillante les comptes de votre domaine. 

Pour afficher le tableau de bord de sécurité :

1. Si nécessaire, accédez au [Centre de sécurité & conformité](https://protection.office.com) et connectez-vous avec votre compte d’administrateur général.

2. Dans le volet de navigation de gauche, sous **gestion des menaces**, cliquez sur **tableau de bord**.

Examinez attentivement toutes les cartes du tableau de bord pour vous familiariser avec les informations fournies.

Pour plus d’informations, consultez la rubrique [Security Dashboard](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-dashboard).


## <a name="phase-4-examine-microsoft-secure-score"></a>Phase 4 : examiner le score de sécurité Microsoft

Le score de sécurité Microsoft indique votre position de sécurité sous la forme d’un nombre, ce qui indique votre niveau actuel par rapport aux fonctionnalités disponibles dans votre abonnement. Elle vous fournit également une liste des actions d’amélioration que vous pouvez effectuer pour améliorer votre score.

1. Créez un nouvel onglet dans votre navigateur et accédez au [Centre de sécurité Microsoft 365](https://security.microsoft.com/), puis cliquez sur **score sécurisé**.
2. Sous l’onglet **vue d’ensemble**  , Notez votre score de sécurité actuel et sa comparaison avec la moyenne globale et les abonnements avec un nombre similaire de licences.
3. Dans l’onglet **actions d’amélioration** , consultez la liste des actions que vous pouvez effectuer pour augmenter votre score.

Pour plus d’informations, consultez la rubrique [Microsoft Secure score](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-secure-score).

## <a name="next-steps"></a>Étapes suivantes

Découvrez les fonctionnalités et les fonctionnalités de [protection des informations](m365-enterprise-test-lab-guides.md#information-protection) supplémentaires dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 pour entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
