---
title: Résoudre les messages d’erreur et les problèmes dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: crimora
audience: Admin
ms.topic: troubleshooting
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, obtenez de l’aide pour résoudre les messages d’erreur et les problèmes.
ms.openlocfilehash: b0fa45076bd3bcff600e51cb1f77d323db821291
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68187710"
---
# <a name="troubleshoot-error-messages-and-problems-in-microsoft-365-lighthouse"></a>Résoudre les messages d’erreur et les problèmes dans Microsoft 365 Lighthouse

Cet article décrit les messages d’erreur et les problèmes que vous pouvez rencontrer lors de l’utilisation de Microsoft 365 Lighthouse et fournit des étapes de dépannage que vous pouvez prendre pour les résoudre.

## <a name="partner-onboarding"></a>Intégration de partenaires

### <a name="message-when-trying-to-access-lighthouse-microsoft-365-lighthouse-doesnt-support-indirect-providers-at-this-time-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Message lors de la tentative d’accès à Lighthouse : « Microsoft 365 Lighthouse ne prend pas en charge les fournisseurs indirects pour l’instant, vous devez être un revendeur indirect ou un partenaire de facturation directe pour utiliser ce service »

**Cause :** Vous avez tenté d’accéder à Lighthouse en tant que partenaire à facturation indirecte. À l’heure actuelle, Lighthouse ne prend en charge que les revendeurs indirects et les partenaires à facturation directe.

**Résolution:** Pour obtenir la liste complète des qualifications et des exigences, consultez [La configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Si vous n’êtes pas un fournisseur indirect et que vous pensez avoir reçu ce message par erreur, contactez le support technique. Pour plus d’informations, consultez [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-trying-to-access-lighthouse-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Message lors de la tentative d’accès à Lighthouse : « Vous devez être un revendeur indirect ou un partenaire à facturation directe pour utiliser ce service »

**Cause :** Vous avez tenté d’accéder à Lighthouse et n’êtes pas un partenaire Microsoft. Vous devez être inscrit au programme Fournisseur de solutions Cloud (CSP) en tant que revendeur indirect ou partenaire à facturation directe pour utiliser Lighthouse.

**Résolution:** Pour obtenir la liste complète des qualifications et des exigences, consultez [La configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Si vous êtes éligible pour accéder à Lighthouse et que vous pensez avoir reçu ce message par erreur, contactez le support technique. Pour plus d’informations, consultez [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-signing-in-to-lighthouse-accept-the-partner-amendment"></a>Message lors de la connexion à Lighthouse : « Accepter l’amendement du partenaire »

**Cause :** Vous avez tenté d’accéder à Lighthouse avant qu’un administrateur général dans le locataire partenaire n’ait signé l’amendement du partenaire.

**Résolution:** Un administrateur général doit se connecter à Lighthouse et accepter l’amendement du partenaire avant de pouvoir accéder à Lighthouse et travailler dans celui-ci. Si l’erreur persiste une fois qu’un administrateur général a signé l’amendement, contactez le support technique. Pour plus d’informations, consultez [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="customer-tenant-onboarding"></a>Intégration du locataire client  

### <a name="customer-tenants-show-a-status-other-than-active-in-the-tenant-list"></a>Les locataires client affichent un état autre que « Actif » dans la liste des locataires  

**Cause :** Vos locataires clients ne répondent pas aux critères suivants :

- Doit avoir configuré l’accès délégué pour que le fournisseur de services managés (MSP) puisse gérer le locataire client*
- Doit avoir au moins une Microsoft 365 Business Premium, Microsoft 365 E3, Microsoft 365 E5, Windows 365 Affaires ou licence Microsoft Defender pour entreprises
- Ne doit pas avoir plus de 2 500 utilisateurs sous licence 

**Résolution:** Le tableau suivant décrit les différents états de locataire qui nécessitent une action et explique comment les résoudre.

Des privilèges délégués granulaires Administration (GDAP) plus une relation de revendeur indirect ou une relation de privilèges délégués Administration (DAP) sont nécessaires pour intégrer des clients à Lighthouse. Si DAP et GDAP coexistent dans un locataire client, les autorisations GDAP sont prioritaires pour les techniciens MSP dans les groupes de sécurité compatibles GDAP. Bientôt, les clients ayant des relations GDAP uniquement (sans relations de revendeur indirect) pourront intégrer Lighthouse.<br><br>

| État | Description | Résolution |
|--|--|--|
| Inactif | Le locataire a été retiré à la demande du MSP et n’est plus géré dans Lighthouse. | Vous devez réactiver le locataire. Dans la page **Locataires** , sélectionnez les trois points (autres actions) en regard du locataire que vous souhaitez réactiver, puis sélectionnez Activer le **locataire**. L’affichage des données client initiales dans Lighthouse peut prendre de 24 à 48 heures. |
| Non éligible - DAP ou GDAP n’est pas configuré | Vous n’avez pas de privilèges d’administrateur de revendeur indirect ou DAP ou GDAP configurés avec le locataire, ce qui est requis par Lighthouse. | Configurez DAP ou GDAP et les privilèges d’administrateur des revendeurs indirects dans l’Espace partenaires Microsoft. |
| Inéligible - La licence requise est manquante | Le locataire ne dispose pas d’une licence requise. Ils ont besoin d’au moins une licence Microsoft 365 Business Premium, Microsoft 365 E3, Microsoft 365 E5 ou Microsoft Defender pour entreprises. | Assurez-vous que le locataire a au moins une Microsoft 365 Business Premium, Microsoft 365 E3, Microsoft 365 E5, Windows 365 Affaires ou Microsoft Defender pour entreprises licence attribuée. |
| Non éligible - Nombre d’utilisateurs dépassé | Le locataire a plus de 2 500 utilisateurs sous licence autorisés par Lighthouse. | Vérifiez que le locataire n’a pas plus de 2 500 utilisateurs sous licence. |
| Non éligible - Échec de la vérification géographique | Vous et votre client ne résidez pas dans la même région géographique, ce qui est requis par Lighthouse. | Vérifiez que le client réside dans votre région géographique. Si ce n’est pas le cas, vous ne pouvez pas gérer le locataire dans Lighthouse. |
| En cours de traitement | Lighthouse a découvert le locataire, mais est toujours en cours d’intégration. | Autorisez Lighthouse 48 heures à terminer l’intégration du locataire. |

Si vous avez confirmé que votre locataire client répond aux critères d’intégration et qu’il ne s’affiche toujours pas comme **actif** dans Lighthouse, contactez le support technique. Pour plus d’informations, consultez [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="access-and-permissions"></a>Accès et autorisations

### <a name="message-when-trying-to-access-lighthouse-not-authorized-or-insufficient-privileges-or-access-restriction-insufficient-or-lack-of-permissions-is-causing-access-restriction"></a>Message lors de la tentative d’accès à Lighthouse : « Non autorisé » ou « Privilèges insuffisants » ou « Restriction d’accès : l’insuffisance ou l’absence d’autorisations entraîne une restriction d’accès » 

**Cause :** Vous n’appartenez pas au groupe de sécurité approprié dans Azure AD, ou vous n’avez pas reçu le rôle approprié dans l’Espace partenaires pour pouvoir accéder à Lighthouse.

**Résolution:** Assurez-vous qu’un administrateur de votre locataire partenaire disposant des autorisations appropriées vous a affecté au groupe de sécurité GDAP approprié dans Azure AD et vous a attribué le rôle approprié dans l’Espace partenaires. En outre, gardez à l’esprit que certaines actions dans Lighthouse vous obligent à être administrateur général. Pour en savoir plus sur les rôles GDAP et ce que chaque rôle peut faire, consultez [Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md). Pour obtenir une description détaillée de tous les rôles et autorisations intégrés Azure AD pour GDAP, consultez [les rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference).

Pour les clients ayant des relations DAP, l’administrateur partenaire doit vous affecter au rôle d’agent Administration ou d’agent du support technique dans l’Espace partenaires. Pour obtenir une description détaillée de tous les rôles et autorisations de l’Espace partenaires, consultez [Attribuer des rôles et des autorisations aux utilisateurs](/partner-center/permissions-overview).

### <a name="i-dont-see-complete-data-in-certain-areas-of-lighthouse-or-i-cant-perform-certain-tasks-or-i-cant-access-certain-tenants"></a>Je ne vois pas les données complètes dans certaines zones de Lighthouse, ou je ne peux pas effectuer certaines tâches, ou je ne peux pas accéder à certains locataires

**Cause :** Vous disposez d’un accès GDAP limité en fonction des rôles attribués au groupe de sécurité Azure AD dans lequel vous êtes.

**Résolution:** Assurez-vous qu’un administrateur de votre locataire partenaire disposant des autorisations appropriées vous a affecté au groupe de sécurité GDAP approprié dans Azure AD. En outre, gardez à l’esprit que certaines actions dans Lighthouse vous obligent à être administrateur général. Pour en savoir plus sur les rôles GDAP et ce que chaque rôle peut faire, consultez [Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md). Pour obtenir une description détaillée de tous les rôles et autorisations intégrés Azure AD pour GDAP, consultez [les rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference).

## <a name="customer-tenant-management"></a>Gestion des locataires clients  

### <a name="customer-tenant-has-no-data-showing-in-lighthouse"></a>Le locataire client n’a aucune donnée affichée dans Lighthouse

**Cause :** Vous tentez d’afficher les données dans Lighthouse avant la fin de l’intégration du locataire.

**Résolution:** L’affichage des données client initiales dans Lighthouse peut prendre de 24 à 48 heures. Si cela fait plus de 48 heures que vous avez intégré le locataire et que vous n’êtes toujours pas en mesure d’afficher ou de charger des données de locataire, ou si vous ne parvenez pas à afficher ou à charger des données que vous aviez pu auparavant, contactez le support technique. Pour plus d’informations, consultez [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Préparez-vous à fournir les journaux réseau pertinents et la liste des options qui ont pu être modifiées.

### <a name="customer-tenant-data-isnt-updating-after-making-changes-in-the-customer-tenant"></a>Les données client client ne sont pas mises à jour après avoir apporté des modifications au locataire client

**Cause :** Les modifications que vous apportez à l’intérieur du locataire client peuvent prendre jusqu’à 4 heures pour se synchroniser avec les données du locataire client dans Lighthouse.

**Résolution:** Si cela fait plus de 4 heures et que les données du locataire client ne sont toujours pas mises à jour dans Lighthouse, contactez le support technique. Pour plus d’informations, consultez [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Soyez prêt à fournir des informations sur le locataire du client.

### <a name="message-when-applying-a-baseline-to-a-customer-tenant-process-error-occurred"></a>Message lors de l’application d’une ligne de base à un locataire client : « Une erreur de processus s’est produite »  

**Cause :** Vous n’avez pas correctement terminé la configuration de Microsoft Intune au sein du locataire client.

**Résolution:** Vérifiez que vous avez effectué les étapes de configuration de base pour Intune au sein du locataire du client. Si le problème persiste après avoir vérifié que Intune configuration est terminée pour le locataire client, contactez le support technique. Pour plus d’informations, consultez [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="cant-access-partner-tenant-data-in-lighthouse"></a>Impossible d’accéder aux données du locataire partenaire dans Lighthouse

**Cause** : Lighthouse prend en charge l’affichage et la gestion des locataires *clients* uniquement. Il ne prend actuellement pas en charge l’affichage et la gestion des locataires *partenaires* .

**Résolution:** Continuez à utiliser la méthode que vous avez utilisée pour afficher et gérer votre locataire partenaire.

## <a name="device-and-threat-management"></a>Gestion des appareils et des menaces 

### <a name="i-dont-see-any-customer-tenant-data-on-the-device-compliance-and-threat-management-pages-of-lighthouse"></a>Je ne vois aucune donnée client sur les pages conformité des appareils et gestion des menaces de Lighthouse

**Cause 1 :** Le locataire client n’a pas terminé l’intégration à Intune. Les données client client ne seront pas disponibles dans les pages conformité de l’appareil ou gestion des menaces de Lighthouse tant que le locataire client n’a pas terminé l’intégration à Intune.

**Résolution:** Vérifiez que le locataire client pour lequel vous essayez d’afficher les données a terminé l’intégration à Intune. Une fois l’intégration terminée dans Intune, autorisez 4 heures pour que les données de l’appareil apparaissent dans Lighthouse.

**Cause 2 :** Le locataire client a récemment été intégré à Lighthouse et les données sont toujours en cours de chargement dans Lighthouse.

**Résolution:** Une fois qu’un locataire client est intégré à Lighthouse, autorisez l’affichage des données client initiales pendant 24 à 48 heures.

**Cause 3 :** L’appareil client client est nouveau et les données de l’appareil sont toujours en cours de chargement dans Lighthouse.

**Résolution:** Lorsqu’un appareil client est ajouté, autorisez 4 heures pour que les données de l’appareil apparaissent dans Lighthouse.

Si les données n’apparaissent toujours pas dans les pages conformité des appareils et gestion des menaces après avoir suivi les instructions de résolution, contactez le support technique. Pour plus d’informations, consultez [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="related-content"></a>Contenu associé

[Problèmes connus avec Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) (article)\
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)\
[Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (article)
