---
title: Sécurité Microsoft 365 accrue pour votre Microsoft 365 pour l’environnement de test d’entreprise
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.custom:
- Ent_TLGs
- admindeeplinkMAC
- admindeeplinkDEFENDER
- admindeeplinkSPO
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce guide de laboratoire de test pour activer d’autres paramètres de sécurité Microsoft 365 votre Microsoft 365 pour l’environnement de test d’entreprise.
ms.openlocfilehash: 4c69fadd3fb3e6744fad850e76282ea2339f48ee
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100718"
---
# <a name="increased-microsoft-365-security-for-your-microsoft-365-for-enterprise-test-environment"></a>Sécurité Microsoft 365 accrue pour votre Microsoft 365 pour l’environnement de test d’entreprise

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Avec les instructions de cet article, vous configurez des paramètres de Microsoft 365 supplémentaires pour renforcer la sécurité dans votre Microsoft 365 pour l’environnement de test d’entreprise.

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](../downloads/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan visuel de tous les articles de l’ensemble des guides de laboratoire de test de Microsoft 365 pour entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre Microsoft 365 pour l’environnement de test d’entreprise

Si vous souhaitez simplement configurer une sécurité accrue Microsoft 365 de manière légère avec les exigences minimales, suivez les instructions de [la configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer une sécurité accrue Microsoft 365 dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Les tests accrus Microsoft 365 sécurité ne nécessitent pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt services de domaine Active Directory (AD DS). Il est fourni ici en tant qu’option afin que vous puissiez tester la licence automatisée et l’appartenance à un groupe et l’expérimenter dans un environnement qui représente une organisation classique. 

## <a name="phase-2-configure-increased-microsoft-365-security"></a>Phase 2 : Configurer une sécurité Microsoft 365 accrue

Dans cette phase, vous activez une sécurité Microsoft 365 accrue pour votre Microsoft 365 pour l’environnement de test d’entreprise. Pour plus d’informations et de paramètres, consultez [Configurer votre locataire pour renforcer la sécurité](/office365/securitycompliance/tenant-wide-setup-for-increased-security).

### <a name="configure-sharepoint-online-to-block-apps-that-dont-support-modern-authentication"></a>Configurer SharePoint Online pour bloquer les applications qui ne prennent pas en charge l’authentification moderne

Les applications qui ne prennent pas en charge l’authentification moderne ne peuvent pas avoir [de configurations d’identité et d’accès aux appareils](../security/office-365-security/microsoft-365-policies-configurations.md) qui leur sont appliquées, ce qui est un élément important de la sécurisation de votre abonnement Microsoft 365 et de ses ressources numériques. 

1. Accédez à la <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> et connectez-vous à votre abonnement de laboratoire de test Microsoft 365 avec votre compte d’administrateur général.
    
  - Si vous utilisez l’environnement de test léger Microsoft 365, connectez-vous à partir de votre ordinateur local.
    
  - Si vous utilisez l’environnement de test Microsoft 365 entreprise simulé, utilisez le [Portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de CLIENT1.
 
2. Sous le nouvel onglet **Centre d'administration Microsoft 365**, sous **Centres d’administration** dans le volet de navigation gauche, cliquez sur **SharePoint**.
3. Sous le nouvel onglet **SharePoint centre d’administration**, sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank">**le contrôle PoliciesAccess**</a> > .
4. Sélectionnez **Applications qui ne prennent pas en charge l’authentification moderne**, **sélectionnez Bloquer l’accès**, puis **Enregistrez**.


### <a name="enable-defender-for-office-365-for-sharepoint-onedrive-for-business-and-microsoft-teams"></a>Activer Defender pour Office 365 pour SharePoint, OneDrive Entreprise et Microsoft Teams

Defender pour Office 365 pour SharePoint, OneDrive et Microsoft Teams protège votre organisation contre le partage involontaire de fichiers malveillants.

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre de sécurité & conformité</a> et connectez-vous avec votre compte d’administrateur général.

2. Dans le volet de navigation gauche, sous **Gestion des menaces**, cliquez sur **Stratégie**, puis sur **Coffre Pièces jointes**. 

3. Sous **Protéger les fichiers dans SharePoint, OneDrive et Microsoft Teams**. Sélectionnez **Activer ATP pour SharePoint, OneDrive et Microsoft Teams**.

4. Cliquez sur **Enregistrer**.


### <a name="enable-anti-malware"></a>Activer l’anti-programme malveillant

Les programmes malveillants sont constitués de virus et de logiciels espions. Les virus contaminent d'autres programmes et données, et ils se propagent dans votre ordinateur à la recherche de programmes à infecter. Les logiciels espions font référence à des programmes malveillants qui collectent vos informations personnelles, telles que les informations de connexion et les données personnelles, et les renvoient à l’auteur du programme malveillant. 

Microsoft 365 dispose de fonctionnalités intégrées de filtrage des programmes malveillants et du courrier indésirable qui permettent de protéger les messages entrants et sortants contre les logiciels malveillants et de vous protéger contre le courrier indésirable. Pour plus d’informations, consultez [Anti-spam & protection contre les programmes malveillants](../security/office-365-security/anti-spam-and-anti-malware-protection.md).

Pour vous assurer que le traitement anti-programme malveillant est effectué sur des fichiers avec des types de fichiers pièces jointes courants :

1. Cliquez sur le bouton Précédent de votre navigateur pour revenir à la page **Stratégie** .
2. Cliquez sur **Anti-programme malveillant**.
3. Double-cliquez sur la stratégie nommée **Par défaut**.
4. Dans la fenêtre **de stratégie anti-programme malveillant**, cliquez sur **Paramètres**.
4. Sous **filtre Types de pièces jointes courants**, sélectionnez **Activé**, puis cliquez sur **Enregistrer**.


## <a name="phase-3-examine-the-security-dashboard"></a>Phase 3 : Examiner le tableau de bord de sécurité

La gestion des menaces dans Microsoft 365 peut vous aider à contrôler et gérer l’accès des appareils mobiles aux données de votre organisation, à protéger votre organisation contre la perte de données et à protéger les messages entrants et sortants contre les logiciels malveillants et le courrier indésirable. Vous utilisez également la gestion des menaces pour protéger la réputation de votre domaine et déterminer si les expéditeurs usurpent ou non des comptes d’usurpation de votre domaine. 

Pour afficher le tableau de bord de sécurité :

1. Si nécessaire, accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre de sécurité & conformité</a> et connectez-vous avec votre compte d’administrateur général.

2. Dans le volet de navigation gauche, sous **Gestion des menaces**, cliquez sur **Tableau de bord**.

Examinez attentivement toutes les cartes du tableau de bord pour vous familiariser avec les informations fournies.

Pour plus d’informations, consultez [Tableau de bord de sécurité](../security/office-365-security/security-dashboard.md).


## <a name="phase-4-examine-microsoft-secure-score"></a>Phase 4 : Examiner le score de sécurité Microsoft

Microsoft Secure Score affiche votre posture de sécurité sous la forme d’un nombre, ce qui indique votre niveau actuel par rapport aux fonctionnalités disponibles dans votre abonnement. Il vous donne également une liste des actions d’amélioration que vous pouvez effectuer pour améliorer votre score.

1. Créez un onglet dans votre navigateur, accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, puis cliquez sur **Score sécurisé**.
2. Sous l’onglet **Vue d’ensemble**  , notez votre degré de sécurisation actuel et sa comparaison avec la moyenne globale et les abonnements avec un nombre similaire de licences.
3. Sous l’onglet **Actions d’amélioration** , lisez la liste des actions que vous pouvez effectuer pour augmenter votre score.

Pour plus d’informations, consultez [Microsoft Secure Score](../security/defender/microsoft-secure-score.md).

## <a name="next-steps"></a>Étapes suivantes

Explorez d’autres fonctionnalités et fonctionnalités de [protection des informations](m365-enterprise-test-lab-guides.md#information-protection) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)
