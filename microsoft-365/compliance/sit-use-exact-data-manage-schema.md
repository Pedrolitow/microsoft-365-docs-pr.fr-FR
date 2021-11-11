---
title: Gérer votre schéma exact de correspondance de données
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment modifier ou supprimer votre schéma exact de correspondance de données.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7fb535f08b178cf934ec7586579a00725747a3ce
ms.sourcegitcommit: 8410a49995a084e4cc9b3f7286c8d506b7a85d79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2021
ms.locfileid: "60914790"
---
# <a name="manage-your-exact-data-match-schema"></a>Gérer votre schéma exact de correspondance de données

## <a name="editing-the-schema-for-edm-based-classification-manually"></a>Modification manuelle du schéma pour la classification EDM

Si vous souhaitez apporter des modifications à votre schéma EDM, par exemple le fichier **edm.xml,** par exemple en modifiant les champs utilisés pour la classification EDM, suivez les étapes suivantes :

> [!TIP]
> Vous pouvez modifier votre schéma EDM et votre fichier source de table d’informations sensibles pour tirer parti **d’une correspondance configurable.** Lorsqu’il est configuré, EDM ignore les différences de casse et certains séparateurs lorsqu’il évalue un élément. Cela simplifie la définition de votre schéma XML et de vos fichiers de données sensibles. Pour en savoir plus, [utilisez les champs caseInsensitive et ignoredDelimiters](sit-get-started-exact-data-match-create-schema.md#using-the-caseinsensitive-and-ignoreddelimiters-fields).

1. Modifiez **votreedm.xml** (il s’agit du fichier abordé dans le schéma Créer le schéma pour les types d’informations sensibles basés sur la correspondance de données [exactes.](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)

2. Connectez-vous au Centre de sécurité et conformité en utilisant la procédure [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

3. Pour mettre à jour votre schéma de base de données, exécutez les cmdlets suivantes, l’une après l’autre :

      ```powershell
      $edmSchemaXml=Get-Content .\\edm.xml -Encoding Byte -ReadCount 0
      Set-DlpEdmSchema -FileData $edmSchemaXml -Confirm:$true
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
      > Si vous souhaitez que vos modifications se produisent sans confirmation, à l’étape 3, utilisez plutôt la cmdlet Set-DlpEdmSchema -FileData $edmSchemaXml

      > [!NOTE]
      > La mise à jour du schéma EDMS avec les ajouts peut prendre de 10 à 60 minutes. La mise à jour doit être terminée avant d’exécuter les étapes qui utilisent les ajouts.--->

## <a name="removing-the-schema-for-edm-based-classification-manually"></a>Suppression manuelle du schéma pour la classification EDM

Si vous souhaitez supprimer le schéma que vous utilisez pour la classification EDM, suivez les étapes suivantes :

1. Connectez-vous au Centre de sécurité et conformité en utilisant la procédure [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

2. Exécutez les cmdlets PowerShell suivantes, en remplaçant le nom du magasin de données des « enregistrements de patients » par celui que vous souhaitez supprimer (à l’aide du magasin patientrecords comme exemple) :

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
      >  Si vous souhaitez que vos modifications se produisent sans confirmation, à l’étape 2, utilisez plutôt la cmdlet Remove-DlpEdmSchema -Identity patientrecords -Confirm:$false

### <a name="edit-or-delete-the-edm-schema-with-the-wizard"></a>Modifier ou supprimer le schéma EDM à l’aide de l’Assistant

1. Ouvrez **le Centre de conformité** Classification des  >  **données**  >  **Correspondances exactes.**

2. Choisissez **les schémas EDM.**

3. Choisissez l’EDM SIT que vous souhaitez modifier.

4. Choisissez **Modifier le schéma EDM ou** supprimer le schéma **EDM** du flyout.

> [!IMPORTANT]
> Si vous voulez supprimer un schéma et que celui-ci est déjà associé à un type d’informations sensibles EDM, vous devez commencer par supprimer le type d’informations sensibles EDM. Vous pouvez ensuite supprimer le schéma.