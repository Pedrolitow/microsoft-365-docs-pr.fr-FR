---
title: Résoudre les problèmes et les messages d’erreur dans Microsoft 365 Lighthouse
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
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, obtenez de l’aide pour résoudre les problèmes et les messages d’erreur.
ms.openlocfilehash: 1bd98a90af19d60aba2e0891c3f993e77523a12c
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64632358"
---
# <a name="troubleshoot-and-resolve-problems-and-error-messages-in-microsoft-365-lighthouse"></a>Résoudre les problèmes et les messages d’erreur dans Microsoft 365 Lighthouse

Cet article décrit les messages d’erreur et les problèmes que vous pouvez rencontrer lors de l’utilisation de Microsoft 365 Lighthouse et fournit des mesures de résolution des problèmes que vous pouvez prendre pour les résoudre.

## <a name="partner-onboarding"></a>Intégration de partenaires

### <a name="message-when-trying-to-access-lighthouse-microsoft-365-lighthouse-doesnt-support-indirect-providers-at-this-time-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Message lors d’une tentative d’accès à l’aide du service : « Microsoft 365 Lighthouse ne prend pas en charge les fournisseurs indirects pour le moment, vous devez être un revendeur indirect ou un partenaire de facture directe pour utiliser ce service »

**Cause :** Vous avez tenté d’accéder à L’Île en tant que partenaire à facture indirecte. Pour l’instant, Il prend uniquement en charge les revendeurs indirects et les partenaires à facture directe.

**Résolution :** Pour obtenir la liste complète des qualifications et des exigences, voir [Requirements for Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Si vous n’êtes pas un fournisseur indirect et pensez que vous avez reçu ce message par erreur, contactez le support technique. Pour plus d’informations, voir [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-trying-to-access-lighthouse-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Message lors de la tentative d’accès à l’aide du service : « Vous devez être un revendeur indirect ou un partenaire à facture directe pour utiliser ce service »

**Cause :** Vous avez tenté d’accéder au Groupement et vous n’êtes pas un partenaire Microsoft. Vous devez être inscrit au programme fournisseur de solutions Cloud (CSP) en tant que revendeur indirect ou partenaire à facture directe pour pouvoir utiliser Le Lieu.

**Résolution :** Pour obtenir la liste complète des qualifications et des exigences, voir [Requirements for Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Si vous êtes éligible pour accéder au Groupe de travail et que vous pensez avoir reçu ce message par erreur, contactez le support technique. Pour plus d’informations, voir [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-signing-in-to-lighthouse-accept-the-partner-amendment"></a>Message lors de la signature à l’Inscription : « Accepter la modification du partenaire »

**Cause :** Vous avez tenté d’accéder à l’accès au Contrôle d’accès avant qu’un administrateur global du client partenaire ait signé la modification du partenaire.

**Résolution :** Un administrateur global doit se connecter au Groupement et accepter la modification du partenaire avant de pouvoir accéder à l’environnement de travail et travailler dans ce dernier. Si l’erreur persiste après qu’un administrateur global a signé la modification, contactez le support technique. Pour plus d’informations, voir [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="customer-tenant-onboarding"></a>Intégration du client client  

### <a name="customer-tenants-show-a-status-other-than-active-in-the-tenant-list"></a>Les locataires du client indiquent un état autre que « Actif » dans la liste des clients  

**Cause :** Les locataires de vos clients ne répondent pas aux critères suivants :

  - Doit avoir un accès délégué pour que le fournisseur de services gérés (MSP) puisse gérer le client*
  - Doit avoir au moins une licence Microsoft 365 Business Premium, Microsoft 365 E3 ou une licence Windows 365 Affaires licence
  - Ne doit pas avoir plus de 1 000 utilisateurs sous licence 

**Résolution :** Le tableau suivant décrit les différents statuts de client qui nécessitent une action et explique comment les résoudre.

*Des privilèges d’administration délégués (DAP) sont requis pour intégrer des clients à l’entreprise. Nous vous recommandons également d’établir des privilèges d’administration délégués granulaires (GDAP) avec vos clients pour permettre un accès délégué plus sécurisé. Bien que DAP et GDAP coexistent, GDAP est prioritaire pour les clients où les deux modèles sont en place. Bientôt, les clients  ayant uniquement GDAP (et pas de DAP) pourront intégrer le groupe.


| État | Description | Résolution |
|--|--|--|
| Inactif | Le client a été mis hors carte à la demande du MSP et n’est plus géré dans le Groupement. | Vous devez réactiver le client. Dans la page **Locataires** , sélectionnez les trois points (autres actions) en côté du client que vous souhaitez réactiver, puis sélectionnez **Activer le client**. Il faut entre 24 et 48 heures pour que les données initiales du client apparaissent dans le Groupement. |
| Inéligible - DAP ou GDAP n’est pas installé | Vous n’avez pas de privilèges d’administrateur DAP ou GDAP mis en place avec le client, ce qui est requis par le Propriétaire. | Configurer des privilèges d’administrateur DAP ou GDAP dans l’Microsoft Partner Center. |
| Inéligible - La licence requise est manquante | Une licence requise est manquante pour le client. Ils ont besoin d’au moins une licence Microsoft 365 Business Premium, Microsoft 365 E3 ou Windows 365 Affaires licence. | Assurez-vous que le client dispose d’au moins Microsoft 365 Business Premium, Microsoft 365 E3 ou Windows 365 Affaires licence attribuée. |
| Inéligible : nombre d’utilisateurs dépassé | Le client a plus de 1 000 utilisateurs sous licence autorisés par le locataire. | Vérifiez que le client ne peut pas avoir plus de 1 000 utilisateurs sous licence. |
| Inéligible - Échec de la vérification géographique | Vous et votre client ne résidez pas dans la même région géographique, ce qui est obligatoire par le cas échéant. | Vérifiez que le client réside dans votre région géographique. Si ce n’est pas le cas, vous ne pouvez pas gérer le client dans le Cas d’une autre. |
| In process | Le propriétaire a découvert le client, mais est toujours en train de les intégrer. | Autorisez l’intégration du client pendant 48 heures. |

Si vous avez confirmé que votre client répond aux critères d’intégration et qu’il n’est toujours  pas en cours d’affichage, contactez le support technique. Pour plus d’informations, voir [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="access-and-permissions"></a>Accès et autorisations

### <a name="message-when-trying-to-access-lighthouse-not-authorized-or-insufficient-privileges-or-access-restriction-insufficient-or-lack-of-permissions-is-causing-access-restriction"></a>Message lors de la tentative d’accès à l’accès à l’accès : « Non autorisé » ou « Privilèges insuffisants » ou « Restriction d’accès : l’insuffisance ou l’absence d’autorisations provoque une restriction d’accès » 

**Cause :** Vous n’appartenez pas au groupe de sécurité correct dans Azure AD, ou vous n’avez pas reçu le rôle correct dans l’Partner Center pour pouvoir accéder à l’accès à l’Centre de partenaires.

**Résolution :** Assurez-vous qu’un administrateur de votre client partenaire avec les autorisations appropriées vous a affecté au groupe de sécurité GDAP approprié dans Azure AD et vous a affecté le rôle approprié dans l’Partner Center. En outre, gardez à l’esprit que certaines actions dans le cas de l’état État exigent que vous soyez un administrateur global. Pour en savoir plus sur les rôles GDAP et ce que chaque rôle peut faire, voir Vue d’ensemble des [autorisations dans Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md). Pour obtenir une description détaillée de tous Azure AD et autorisations intégrées pour GDAP, voir Azure AD [rôles intégrés](/azure/active-directory/roles/permissions-reference).

Pour les clients ayant des relations DAP, l’administrateur partenaire doit vous attribuer le rôle d’agent d’administration ou d’agent du service d’aide dans l’Partner Center. Pour obtenir une description détaillée de tous les rôles et autorisations de l’Partner Center, voir [Attribuer des rôles et des autorisations aux utilisateurs](/partner-center/permissions-overview).

### <a name="i-dont-see-complete-data-in-certain-areas-of-lighthouse-or-i-cant-perform-certain-tasks-or-i-cant-access-certain-tenants"></a>Je ne vois pas les données complètes dans certaines zones de la région, je ne peux pas effectuer certaines tâches ou je ne peux pas accéder à certains clients.

**Cause :** Vous avez un accès GDAP limité en fonction des rôles attribués au groupe de sécurité Azure AD que vous êtes.

**Résolution :** Assurez-vous qu’un administrateur de votre client partenaire avec les autorisations appropriées vous a affecté au groupe de sécurité GDAP approprié dans Azure AD. En outre, gardez à l’esprit que certaines actions dans le cas de l’état État exigent que vous soyez un administrateur global. Pour en savoir plus sur les rôles GDAP et ce que chaque rôle peut faire, voir Vue d’ensemble des [autorisations dans Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md). Pour obtenir une description détaillée de tous Azure AD et autorisations intégrées pour GDAP, voir Azure AD [rôles intégrés](/azure/active-directory/roles/permissions-reference).

## <a name="customer-tenant-management"></a>Gestion des clients  

### <a name="customer-tenant-has-no-data-showing-in-lighthouse"></a>Le locataire du client n’a aucune donnée à afficher en île

**Cause :** Vous tentez d’afficher les données dans le Dossier Avant la fin de l’intégration du client.

**Résolution :** Il faut entre 24 et 48 heures pour que les données initiales du client apparaissent dans le Groupement. Si cela fait plus de 48 heures que vous avez intégré le client et que vous n’êtes toujours pas en mesure d’afficher ou de charger des données client, ou si vous ne parvenez pas à afficher ou charger des données que vous aviez précédemment pu consulter, contactez le support technique. Pour plus d’informations, voir [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Soyez prêt à fournir des journaux réseau pertinents et une liste des options qui ont pu être modifiées.

### <a name="customer-tenant-data-isnt-updating-after-making-changes-in-the-customer-tenant"></a>Les données client ne sont pas mises à jour après avoir apporté des modifications au client

**Cause :** Les modifications que vous a faites au sein du client peuvent prendre jusqu’à 4 heures pour se synchroniser avec les données client dans le Centre d’informations.

**Résolution :** Si cela fait plus de 4 heures et que les données du client client ne sont toujours pas mises à jour dans le centre d’informations, contactez le support technique. Pour plus d’informations, voir [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Soyez prêt à fournir des informations sur le client.

### <a name="message-when-applying-a-baseline-to-a-customer-tenant-process-error-occurred"></a>Message lors de l’application d’une ligne de base à un client : « Une erreur de processus s’est produite »  

**Cause :** Vous n’avez pas réussi à terminer la configuration des Microsoft Intune au sein du client.

**Résolution :** Vérifiez que vous avez effectué les étapes de configuration de base Intune au sein du client. Si le problème persiste après avoir vérifié que la configuration Intune est terminée pour le client, contactez le support technique. Pour plus d’informations, voir [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="cant-access-partner-tenant-data-in-lighthouse"></a>Can't access partner tenant data in Lighthouse

**Cause :** Ce dernier prend uniquement en charge *l’affichage et* la gestion des locataires du client. Il ne prend actuellement pas en charge l’affichage et la gestion des *locataires* partenaires.

**Résolution :** Continuez à utiliser la méthode que vous avez utilisée pour afficher et gérer votre client partenaire.

## <a name="device-and-threat-management"></a>Gestion des appareils et des menaces 

### <a name="i-dont-see-any-customer-tenant-data-on-the-device-compliance-and-threat-management-pages-of-lighthouse"></a>Je ne vois pas de données client sur les pages conformité des appareils et gestion des menaces du Centre d’administration Des clients

**Cause 1 :** Le client n’a pas terminé l’intégration à Intune. Les données client client ne seront pas disponibles sur les pages de conformité des appareils ou de gestion des menaces de l’Application avant que le client n’ait terminé l’intégration à Intune.

**Résolution :** Vérifiez que le client pour qui vous essayez d’afficher les données a terminé l’intégration à Intune. Une fois l’intégration terminée dans Intune, autorisez 4 heures pour que les données de l’appareil apparaissent dans le Dossier.

**Cause 2 :** Le client a été récemment intégré au Groupement et les données sont toujours en cours de chargement.

**Résolution :** Une fois qu’un client est intégré au Programme, autorisez 24 à 48 heures pour l’apparition des données client initiales.

**Cause 3 :** L’appareil client est nouveau et les données de l’appareil sont toujours en cours de chargement dans le Centre d’appels.

**Résolution :** Lorsqu’un appareil client est ajouté, autorisez 4 heures pour que les données de l’appareil apparaissent dans le Périphérique.

Si les données n’apparaissent toujours pas dans les pages de conformité des appareils et de gestion des menaces après avoir suivi les instructions de résolution, contactez le support technique. Pour plus d’informations, voir [Obtenir de l’aide et du support pour Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="related-content"></a>Contenu connexe

[Problèmes connus avec Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)\
[Obtenir de l’aide et du support Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (article)