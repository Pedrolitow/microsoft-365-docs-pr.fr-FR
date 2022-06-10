---
title: Gérer votre schéma de correspondance exacte des données
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment modifier ou supprimer votre schéma de correspondance exacte des données.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 29cfefbd6bf9bb9f92fe5ed7664575ec75adfa12
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014671"
---
# <a name="manage-your-exact-data-match-schema"></a>Gérer votre schéma de correspondance exacte des données

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

## <a name="editing-the-schema-for-edm-based-classification-manually"></a>Modification manuelle du schéma pour la classification basée sur EDM

Si vous souhaitez apporter des modifications à votre schéma EDM, par exemple le fichier **edm.xml** , tel que la modification des champs utilisés pour la classification basée sur EDM, procédez comme suit :

> [!TIP]
> Vous pouvez modifier votre schéma EDM et votre fichier source de table d’informations sensibles pour tirer parti de la **correspondance configurable**. Lorsqu’il est configuré, EDM ignore les différences de casse et certains séparateurs lorsqu’il évalue un élément. Cela simplifie la définition de votre schéma XML et de vos fichiers de données sensibles. Pour en savoir plus, [consultez l’utilisation des champs caseInsensitive et ignoredDelimiters](sit-get-started-exact-data-match-create-schema.md#using-the-caseinsensitive-and-ignoreddelimiters-fields).

1. Modifiez votre fichier **edm.xml** (il s’agit du fichier décrit dans le [schéma Créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)).

2. [Connecter à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

3. Pour mettre à jour votre schéma de base de données, exécutez la commande suivante :

      ```powershell
      Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      Vous êtes invité à confirmer comme suit :

      > Confirmer
      >
      > Êtes-vous sûr de vouloir effectuer cette action ?
      >
      > Le schéma EDM pour le magasin de données « patientrecords » va être mis à jour.
      >
      > \[Y\] Oui \[A\] Oui pour tout \[N\] Non \[L\] Non pour tout \[?\] Aide (par défaut « Y ») :

      > [!TIP]
      > Si vous souhaitez que vos modifications se produisent sans confirmation, n’utilisez `-Confirm:$true` pas à l’étape 3.

      > [!NOTE]
      > La mise à jour du schéma EDMS avec les ajouts peut prendre de 10 à 60 minutes. Vous devez l’effectuer avant d’exécuter les étapes qui utilisent les ajouts.

## <a name="removing-the-schema-for-edm-based-classification-manually"></a>Suppression manuelle du schéma pour la classification basée sur EDM

Si vous souhaitez supprimer le schéma que vous utilisez pour la classification basée sur EDM, procédez comme suit :

1. [Connecter à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Exécutez la commande suivante, en remplaçant le nom du magasin de données « dossiers des patients » par celui que vous souhaitez supprimer (à l’aide du magasin patientrecords comme exemple) :

      ```powershell
      Remove-DlpEdmSchema -Identity 'patientrecords'
      ```

      Vous serez invité à confirmer :

      > Confirmer
      >
      > Êtes-vous sûr de vouloir effectuer cette action ?
      >
      > Le schéma EDM pour le magasin de données « patientrecords » va être supprimé.
      >
      > \[Y\] Oui \[A\] Oui pour tout \[N\] Non \[L\] Non pour tout \[?\] Aide (par défaut « Y ») :

      > [!TIP]
      > Si vous souhaitez que vos modifications se produisent sans confirmation, n’utilisez `-Confirm:$true` pas à l’étape 2.

### <a name="edit-or-delete-the-edm-schema-with-the-wizard"></a>Modifier ou supprimer le schéma EDM avec l’Assistant

1. Ouvrir la classification des données **du Centre** \> de **conformité** \> **Correspondances exactes des données**.

2. Choisissez **les schémas EDM**.

3. Choisissez le SIT EDM que vous souhaitez modifier.

4. Choisissez **Modifier le schéma EDM** ou **Supprimer le schéma EDM** dans le menu volant.

> [!IMPORTANT]
> Si vous voulez supprimer un schéma et que celui-ci est déjà associé à un type d’informations sensibles EDM, vous devez commencer par supprimer le type d’informations sensibles EDM. Vous pouvez ensuite supprimer le schéma.
