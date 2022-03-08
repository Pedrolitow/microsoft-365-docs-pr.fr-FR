---
title: Sécurité accrue Microsoft 365 pour votre environnement de test Microsoft 365 entreprise
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Utilisez ce guide de laboratoire de test pour activer des paramètres Microsoft 365 de sécurité supplémentaires Microsoft 365 pour l’environnement de test d’entreprise.
ms.openlocfilehash: bf64bb23192eb4a4d2b3700a2b0c4390efc1f53e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327908"
---
# <a name="increased-microsoft-365-security-for-your-microsoft-365-for-enterprise-test-environment"></a>Sécurité accrue Microsoft 365 pour votre environnement de test Microsoft 365 entreprise

*Ce Guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

En suivant les instructions de cet article, vous configurez des paramètres de Microsoft 365 supplémentaires pour renforcer la sécurité dans votre environnement de test Microsoft 365'entreprise.

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](../downloads/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan visuel de tous les articles de l’ensemble des guides de laboratoire de test de Microsoft 365 pour entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 entreprise

Si vous souhaitez simplement configurer une sécurité Microsoft 365 plus simple avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer une sécurité Microsoft 365 plus grande dans une entreprise [simulée](pass-through-auth-m365-ent-test-environment.md), suivez les instructions de l’authentification directe.
  
> [!NOTE]
> Le test d’une sécurité accrue Microsoft 365 ne nécessite pas l’environnement de test d’entreprise simulée, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt AD DS (Active Directory Domain Services). Il est fourni ici en tant qu’option afin que vous pouvez tester la gestion automatisée des licences et l’appartenance à un groupe et l’expérimenter dans un environnement qui représente une organisation classique. 

## <a name="phase-2-configure-increased-microsoft-365-security"></a>Phase 2 : Configuration d’une sécurité Microsoft 365 plus grande

Dans cette phase, vous activez une sécurité Microsoft 365 plus grande pour Microsoft 365 pour l’environnement de test d’entreprise. Pour plus d’informations et de paramètres, voir [Configurer votre client pour une sécurité accrue](/office365/securitycompliance/tenant-wide-setup-for-increased-security).

### <a name="configure-sharepoint-online-to-block-apps-that-dont-support-modern-authentication"></a>Configurer SharePoint Online pour bloquer les applications qui ne permettent pas l’authentification moderne

Les applications qui ne permettent pas l’authentification moderne ne peuvent pas avoir de configurations d’identité et d’accès aux appareils qui leur sont [appliquées](../security/office-365-security/microsoft-365-policies-configurations.md), ce qui est un élément important de la sécurisation de votre abonnement Microsoft 365 et de ses biens numériques. 

1. Go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> and sign in to your Microsoft 365 test lab subscription with your global administrator account.
    
  - Si vous utilisez l’environnement de test Microsoft 365 léger, connectez-vous à partir de votre ordinateur local.
    
  - Si vous utilisez l’environnement de test Microsoft 365 entreprise simulée, utilisez le portail [Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de CLIENT1.
 
2. Sous le nouvel **onglet Centre d'administration Microsoft 365**, sous Centres d’administration dans le volet de navigation de gauche, cliquez **sur SharePoint**.
3. Sous le nouvel **onglet SharePoint centre d’administration**, sélectionnez **Contrôle** <a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank">**PoliciesAccess**</a> > .
4. **Sélectionnez les applications qui ne permettent pas l’authentification** moderne **, sélectionnez** Bloquer l’accès, puis sélectionnez **Enregistrer**.


### <a name="enable-defender-for-office-365-for-sharepoint-onedrive-for-business-and-microsoft-teams"></a>Activer Defender pour Office 365 pour SharePoint, OneDrive Entreprise et Microsoft Teams

Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams protects your organization from inadvertently sharing malicious files.

1. Go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Security & Compliance Center</a> and sign in with your global administrator account.

2. Dans le volet de navigation de gauche, sous Gestion des menaces **, cliquez** sur **Stratégie,** **puis cliquez Coffre pièces jointes**. 

3. Sous **Protéger les fichiers dans SharePoint, OneDrive et Microsoft Teams**. **sélectionnez Activer LAP pour SharePoint, OneDrive et Microsoft Teams**.

4. Cliquez sur **Enregistrer**.


### <a name="enable-anti-malware"></a>Activer la protection contre les programmes malveillants

Les programmes malveillants sont constitués de virus et de logiciels espions. Les virus contaminent d'autres programmes et données, et ils se propagent dans votre ordinateur à la recherche de programmes à infecter. Les logiciels espions font référence à des programmes malveillants qui collectent vos informations personnelles, telles que des informations de connectez-vous et des données personnelles, et les renvoient à l’auteur du programme malveillant. 

Microsoft 365 offre des fonctionnalités intégrées de filtrage des programmes malveillants et du courrier indésirable qui vous aident à protéger les messages entrants et sortants contre les logiciels malveillants et à vous protéger contre le courrier indésirable. Pour plus d’informations, [voir Anti-spam & protection contre les programmes malveillants](../security/office-365-security/anti-spam-and-anti-malware-protection.md).

Pour vous assurer que le traitement anti-programme malveillant est effectué sur des fichiers avec des types de fichiers de pièces jointes courants :

1. Cliquez sur le bouton Retour de votre navigateur pour revenir à la page **Stratégie** .
2. Cliquez **sur Anti-programme malveillant**.
3. Double-cliquez sur la stratégie nommée **Par défaut**.
4. Dans la **fenêtre Stratégie anti-programme** malveillant, cliquez **sur Paramètres**.
4. Sous **Filtre Types de pièces jointes courants**, **sélectionnez Sur**, puis cliquez sur **Enregistrer**.


## <a name="phase-3-examine-the-security-dashboard"></a>Phase 3 : Examiner le tableau de bord de sécurité

La gestion des menaces dans Microsoft 365 peut vous aider à contrôler et gérer l’accès des appareils mobiles aux données de votre organisation, à protéger votre organisation contre la perte de données et à protéger les messages entrants et sortants contre les logiciels malveillants et le courrier indésirable. Vous utilisez également la gestion des menaces pour protéger la réputation de votre domaine et pour déterminer si les expéditeurs usurpent des comptes malveillants à partir de votre domaine. 

Pour voir le tableau de bord de sécurité :

1. Si nécessaire, go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Security & Compliance Center</a> and sign in with your global administrator account.

2. Dans le volet de navigation de gauche, sous Gestion **des menaces**, cliquez sur **Tableau de bord**.

Regardez attentivement toutes les cartes du tableau de bord pour vous familiariser avec les informations fournies.

Pour plus d’informations, voir [Tableau de bord de sécurité](../security/office-365-security/security-dashboard.md).


## <a name="phase-4-examine-microsoft-secure-score"></a>Phase 4 : Examiner le score de sécurité Microsoft

Le degré de sécurisation Microsoft indique votre posture de sécurité sous la forme d’un nombre, ce qui indique votre niveau actuel par rapport aux fonctionnalités disponibles dans votre abonnement. Il fournit également une liste des actions d’amélioration que vous pouvez prendre pour améliorer votre score.

1. Créez un onglet dans votre navigateur, allez sur le portail <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, puis cliquez sur **Score de sécurisation**.
2. Sous **l’onglet**  Vue d’ensemble, notez votre score de sécurisation actuel et sa comparaison avec la moyenne globale et les abonnements avec un nombre de licences similaire.
3. Sous **l’onglet Actions** d’amélioration, lisez la liste des actions que vous pouvez prendre pour augmenter votre score.

Pour plus d’informations, voir [Score de sécurité Microsoft](../security/defender/microsoft-secure-score.md).

## <a name="next-steps"></a>Étapes suivantes

Explorez [d’autres fonctionnalités de protection](m365-enterprise-test-lab-guides.md#information-protection) des informations dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)
