---
title: Problèmes connus liés à Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: crimora
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthous
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, consultez la liste des problèmes connus pour Lighthouse par zone de fonctionnalité.
ms.openlocfilehash: 9c30bcf4696f460a61827528f6dd1c01da98a599
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68165305"
---
# <a name="known-issues-with-microsoft-365-lighthouse"></a>Problèmes connus liés à Microsoft 365 Lighthouse

Cet article répertorie les problèmes connus pour Microsoft 365 Lighthouse par zone de fonctionnalité. Pour plus d’informations sur Lighthouse, consultez [Vue d’ensemble de Microsoft 365 Lighthouse](m365-lighthouse-overview.md).

## <a name="users"></a>Utilisateurs

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Aucune donnée ne s’affiche sous l’onglet OneDrive dans le volet détails de l’utilisateur** | Lorsqu’un technicien MSP tente d’afficher les données OneDrive sous l’onglet OneDrive dans le volet d’informations de l’utilisateur, il voit le message : « OneDrive n’est pas configuré pour cet utilisateur. Demandez à la personne d’aller à portal.office.com/onedrive pour la configurer. Ça peut prendre un certain temps. Si vous voyez toujours ce message 24 heures plus tard, contactez le support technique. » | L’onglet OneDrive ne prend pas en charge l’authentification déléguée pour l’instant. Pour contourner le problème, les techniciens MSP doivent afficher les données OneDrive dans le Centre d'administration Microsoft 365 en se connectant à l’aide des informations d’identification du client. |

## <a name="threat-management"></a>Gestion des menaces

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Le nom de la menace est manquant** | Lorsque les techniciens MSP affichent la liste des menaces à partir de la page de gestion des menaces, le nom de la menace peut manquer à certaines menaces. Cela se produit lorsque l’appareil sur lequel la menace a été détectée a été récemment supprimé de Intune. | Le problème sera résolu dans les 48 heures. Aucune étape supplémentaire n’est requise. |

## <a name="baselines"></a>Bases de référence

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Paramètres en conflit lors de la comparaison de l’authentification héritée de bloc et des étapes de déploiement MFA** | Si un locataire client a déployé l’authentification héritée de bloc et l’une des étapes de déploiement MFA, un test de comparaison décrit à tort ces paramètres comme étant en conflit. | Aucune solution de contournement n’est requise. Les paramètres ne sont pas réellement en conflit et les utilisateurs du locataire client ne sont pas affectés. |

## <a name="windows-365"></a>Windows 365

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Erreur d’approvisionnement de nouvelle tentative** | Les techniciens MSP reçoivent un message d’erreur « Vous n’avez pas les autorisations nécessaires » lors de la tentative de nouvelle tentative d’approvisionnement d’un PC cloud. | Pour contourner ce problème, connectez-vous au locataire client, puis réapprovisionnez les PC cloud à partir du Centre d’administration Microsoft Endpoint Manager. Pour obtenir des instructions, consultez [Reprovisionner un PC cloud](/windows-365/enterprise/reprovision-cloud-pc). |

## <a name="delegated-admin-privileges-dap"></a>Privilèges d’Administration délégués (DAP)

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Délai des autorisations lors de la modification des rôles DAP** | Si un technicien MSP est ajouté ou supprimé du groupe Agent Administration ou Agent du support technique, il peut y avoir un délai dans le reflet des autorisations appropriées dans Lighthouse. | Le problème sera résolu dans les 30 minutes. Aucune étape supplémentaire n’est requise. |

## <a name="granular-delegated-admin-privileges-gdap"></a>Privilèges de Administration délégués granulaires (GDAP)

Des privilèges délégués granulaires Administration (GDAP) plus une relation de revendeur indirect ou une relation de privilèges délégués Administration (DAP) sont nécessaires pour intégrer des clients à Lighthouse. Si DAP et GDAP coexistent dans un locataire client, les autorisations GDAP sont prioritaires pour les techniciens MSP dans les groupes de sécurité compatibles GDAP. Les clients ayant des relations GDAP uniquement (sans relations de revendeur indirect) ne peuvent actuellement pas s’intégrer à Lighthouse, mais ils pourront l’intégrer dans une version ultérieure.<br><br>

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
