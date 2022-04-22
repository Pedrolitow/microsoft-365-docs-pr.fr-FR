---
title: Problèmes connus liés à Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthous
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, consultez la liste des problèmes connus pour Lighthouse par zone de fonctionnalité.
ms.openlocfilehash: aa3b5980b60e966b4edfbac4a6e8d706c399e943
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2022
ms.locfileid: "65022767"
---
# <a name="known-issues-with-microsoft-365-lighthouse"></a>Problèmes connus liés à Microsoft 365 Lighthouse

Cet article répertorie les problèmes connus pour Microsoft 365 Lighthouse par zone de fonctionnalité. Pour plus d’informations sur Lighthouse, consultez [Vue d’ensemble de Microsoft 365 Lighthouse](m365-lighthouse-overview.md).

## <a name="users"></a>Utilisateurs

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **L’agent du support technique ne peut pas réinitialiser un mot de passe utilisateur** | Les techniciens du fournisseur de services managés (MSP) qui sont membres du groupe Agent du support technique ne peuvent pas réinitialiser les mots de passe des utilisateurs dans les locataires du client. Lorsqu’il tente de réinitialiser le mot de passe d’un utilisateur, il reçoit le message d’erreur suivant : « Vous n’êtes pas autorisé à le faire. [En savoir plus](m365-lighthouse-configure-portal-security.md) » | Pour contourner le problème d’autorisations, les agents du support technique doivent réinitialiser les mots de passe à l’aide du Centre d'administration Microsoft 365 ou du Azure Active Directory. |

## <a name="devices"></a>Appareils

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **La stratégie supprimée s’affiche** | Une fois qu’une stratégie de conformité d’appareil a été supprimée de Intune, elle continuera temporairement à être visible dans Lighthouse. Si les techniciens MSP tentent d’effectuer une comparaison de stratégie qui inclut une stratégie qui a été supprimée, les techniciens obtiennent l’erreur suivante : « Un problème s’est produit. Actualisez la page et réessayez. » | Pour résoudre l’erreur, effacez la stratégie supprimée de la comparaison de stratégie et comparez uniquement les stratégies existantes. |

## <a name="threat-management"></a>Gestion des menaces

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Le nom de la menace est manquant** | Lorsque les techniciens MSP affichent la liste des menaces à partir de la page Gestion des menaces, le nom de la menace peut manquer à certaines menaces. Cela se produit lorsque l’appareil sur lequel la menace a été détectée a été récemment supprimé de Intune. | Le problème sera résolu dans les 48 heures. Aucune étape supplémentaire n’est requise. |

## <a name="baselines"></a>Bases de référence

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Paramètres en conflit lors de la comparaison de l’authentification héritée de bloc et des étapes de déploiement MFA** | Si un locataire client a déployé l’authentification héritée de bloc et l’une des étapes de déploiement MFA, un test de comparaison décrit à tort ces paramètres comme étant en conflit. | Aucune solution de contournement n’est requise. Les paramètres ne sont pas réellement en conflit et les utilisateurs du locataire client ne sont pas affectés. |

## <a name="windows-365"></a>Windows 365

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Erreur d’approvisionnement de nouvelle tentative** | Les techniciens MSP reçoivent un message d’erreur « Vous n’avez pas les autorisations nécessaires » lors de la tentative de nouvelle tentative d’approvisionnement d’un PC cloud. | Pour contourner ce problème, connectez-vous au locataire client, puis réapprovisionnez les PC cloud à partir du Centre d’administration Microsoft Endpoint Manager. Pour obtenir des instructions, consultez [Reprovisionner un PC cloud](/windows-365/enterprise/reprovision-cloud-pc). |

## <a name="audit-logs"></a>Journaux d'audit


| Problème | Description | Solution |
|--|--|--|
| **Les actions de désactivation et de réactivation ne sont pas répertoriées dans les journaux d’audit** | Les activités suivantes ne sont actuellement pas signalées dans la page Journaux d’audit dans Lighthouse : <ul><li>Nom : action offboardTenant \| : désactiver un client</li> <li>Nom : resetTenantOnboardingStatus \| Action : Client réactif</li></ul> | Il n’y a pas de solution de contournement, mais nous travaillons sur un correctif. Ces activités apparaissent dans les journaux d’audit une fois le correctif déployé dans le service. |
| **Le filtre n’affiche pas tous les utilisateurs** | Lorsque les techniciens MSP tentent de filtrer à l’aide **d’Initialed By**, la liste de tous les noms d’utilisateur principal (UPN) correspondant aux ID d’e-mail des techniciens qui ont lancé des actions générant des journaux d’audit ne s’affiche pas entièrement sous le filtre.<br><br>Notez que les journaux d’audit eux-mêmes seront entièrement affichés ; seule la possibilité de les filtrer à l’aide **d’Initialed By** est affectée. | Il n’y a pas de solution de contournement, mais nous travaillons sur un correctif. Le filtre revient à son comportement attendu, en affichant la liste complète des upN à filtrer, une fois le correctif déployé dans le service. |

## <a name="delegated-admin-privileges-dap"></a>Privilèges d’administrateur délégués (DAP)

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Délai des autorisations lors de la modification des rôles DAP** | Si un technicien MSP est ajouté ou supprimé du groupe Agent d’administration ou Agent du support technique, il peut y avoir un délai pour refléter les autorisations appropriées dans Lighthouse. | Le problème sera résolu dans les 30 minutes. Aucune étape supplémentaire n’est requise. |

## <a name="granular-delegated-admin-privileges-gdap"></a>Privilèges d’administrateur délégués granulaires (GDAP)

> [!NOTE]
> GDAP est actuellement en [préversion technique](/partner-center/announcements/2022-february#6) (préversion publique) pour permettre aux partenaires d’attribuer des autorisations granulaires avant que GDAP soit généralement disponible.

Actuellement, DAP est nécessaire pour intégrer des clients à Lighthouse. Nous vous recommandons également d’établir GDAP avec vos clients pour permettre un accès délégué plus sécurisé. Bien que DAP et GDAP coexistent, GDAP est prioritaire pour les clients où les deux modèles sont en place. Bientôt, les clients disposant uniquement de GDAP (et pas de DAP) pourront intégrer Lighthouse.<br><br>

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Différents problèmes d’autorisation GDAP dans Lighthouse** | Certains rôles GDAP eux-mêmes n’accordent pas le même niveau d’accès aux données client dans Lighthouse que dans une expérience monolocataire. Si l’un des rôles suivants est attribué individuellement (ce qui n’est pas en combinaison avec d’autres rôles GDAP) aux techniciens MSP, ils peuvent rencontrer des erreurs, notamment :<ul><li>Les administrateurs de sécurité GDAP ne peuvent pas afficher les utilisateurs à risque, ignorer les risques ou confirmer les utilisateurs compromis dans Lighthouse.</li><li>Les lecteurs de sécurité GDAP ne peuvent pas afficher les utilisateurs à risque dans Lighthouse.</li><li>Les administrateurs généraux GDAP voient un message d’erreur lors de la tentative d’affichage de l’intégrité du service dans Lighthouse.</li><li>Les administrateurs généraux GDAP rencontrent des problèmes lors du déploiement des étapes du plan de déploiement dans Lighthouse.</li></ul> | La solution de contournement consiste à affecter une combinaison de rôles GDAP aux techniciens MSP en fonction du niveau d’accès aux données client dont ils ont besoin. Pour obtenir la liste des rôles GDAP recommandés pour utiliser Lighthouse, consultez [Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).<br><br>Pour les problèmes où même les autorisations d’administrateur général GDAP n’autorisent pas l’utilisation d’une fonctionnalité dans Lighthouse, la solution de contournement consiste à accéder au centre d’administration approprié à partir du locataire client pour gérer le client (par exemple, accéder au Centre d'administration Microsoft 365 à partir du locataire client pour vérifier l’intégrité du service). Pour obtenir des instructions sur la modification d’une relation GDAP, consultez [Obtenir des autorisations d’administrateur granulaires pour gérer le service d’un client - Espace partenaires](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). |

## <a name="localization"></a>Localisation

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Problèmes de traduction** | Les utilisateurs peuvent rencontrer des problèmes de traduction de langue lorsque la langue de leur navigateur, ou leur sélection dans Lighthouse, est autre que l’anglais. | Pour réduire les problèmes de traduction dans Lighthouse, assurez-vous que la sélection de la langue du navigateur correspond à celle du paramètre de langue dans le portail Lighthouse. Pour modifier la sélection de langue dans Lighthouse, connectez-vous à Lighthouse et sélectionnez l’icône d’engrenage en haut de la page pour ouvrir la page paramètres du portail, sélectionnez **Langue + région**, puis sélectionnez la langue et les formats régionaux appropriés. |

## <a name="related-content"></a>Contenu associé

[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)\
[Résoudre les messages d’erreur et les problèmes dans Microsoft 365 Lighthouse](m365-lighthouse-troubleshoot.md) (article)\
[Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (article)
