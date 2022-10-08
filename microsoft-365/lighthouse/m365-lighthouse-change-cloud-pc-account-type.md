---
title: Modifier un type de compte PC cloud Windows 365 Affaires dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: katmartin
audience: Admin
ms.topic: article
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
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment définir ou modifier un type de compte PC cloud Windows 365 Affaires.
ms.openlocfilehash: 23187448697453bda024e3729ccb14f5a0d8733c
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68196070"
---
# <a name="change-a-windows-365-business-cloud-pc-account-type-in-microsoft-365-lighthouse"></a>Modifier un type de compte PC cloud Windows 365 Affaires dans Microsoft 365 Lighthouse

Les techniciens du fournisseur de services managés (MSP) peuvent définir le type de compte d’un PC Cloud d’entreprise ou apporter des modifications à un type de compte existant. Les types de comptes suivants sont disponibles :

- **Utilisateur standard (recommandé)** : les comptes d’utilisateur standard ont l’autorisation d’installer des logiciels uniquement à partir du Microsoft Store.

- **Administrateur local** : les comptes d’administrateur local ont l’autorisation d’installer tous les logiciels et d’apporter des modifications à n’importe quelle partie du système d’exploitation. Sélectionnez ce type de compte uniquement si nécessaire, car les programmes malveillants peuvent utiliser des autorisations d’administrateur pour infecter ou endommager des fichiers.

> [!NOTE]
> Vous pouvez définir ou modifier le type de compte uniquement pour les PC cloud disposant d’une licence Entreprise. Vous ne pouvez pas modifier le type de compte pour les PC cloud avec une licence Entreprise.

## <a name="before-you-begin"></a>Avant de commencer 

Vous devez être administrateur Windows 365 ou administrateur général dans le locataire partenaire.

## <a name="set-or-change-a-windows-365-business-cloud-pc-account-type"></a>Définir ou modifier un type de compte PC cloud Windows 365 Affaires

1.  Dans le volet de navigation gauche de Lighthouse, sélectionnez **Appareils** >  **Windows 365**.

2.  Sélectionnez l’onglet **Tous les PC cloud** .

3.  Utilisez la barre d’annotation de nombre de couleurs pour explorer les PC cloud dont l’état **est Provisionné** .

4.  Dans le menu déroulant **Filtres** , sélectionnez le type de licence **Entreprise** pour afficher la liste de tous les PC cloud disposant d’une licence Entreprise au sein de vos locataires clients.

5.  Dans la liste des PC cloud, sélectionnez le PC cloud pour lequel vous souhaitez modifier le type de compte.

6.  Dans le volet d’informations du PC cloud, **sélectionnez Modifier le type de compte**.

7.  Dans le volet **Modifier le type de compte DE PC Cloud** , sélectionnez le type de compte pour le PC cloud, puis **sélectionnez Enregistrer**.

## <a name="next-steps"></a>Prochaines étapes

Une fois la mise à jour appliquée, l’utilisateur affecté du PC cloud doit se connecter au PC cloud ou redémarrer son appareil. L’apparition des nouvelles modifications dans Microsoft 365 Lighthouse peut prendre plusieurs minutes. L’administrateur de PC cloud peut également redémarrer à distance le PC cloud, mais l’utilisateur peut perdre toutes les données non enregistrées.

## <a name="related-content"></a>Contenu associé

[Contrôle d’accès en fonction du rôle pc cloud](/windows-365/enterprise/role-based-access) (article)\
[Vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse](m365-lighthouse-win365-page-overview.md) (article)\
[Reprovisionner un Windows 365 PC Cloud dans Microsoft 365 Lighthouse](m365-lighthouse-reprovision-cloudpc.md) (article)
