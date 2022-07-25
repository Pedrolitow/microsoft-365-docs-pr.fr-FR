---
title: Définition d’entité de clé de compte de stockage Azure (générique)
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’entité de type d’informations sensibles de clé de compte Stockage Azure (générique).
ms.openlocfilehash: 88139dfe26e654e664d74e8543ea791fd171da63
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996420"
---
# <a name="azure-storage-account-key-generic"></a>Clé de compte de stockage Azure (générique)

## <a name="format"></a>Format

Toute combinaison de 86 lettres minuscules ou majuscules, chiffres, barre oblique (/) ou signe plus (+), précédée ou suivie des caractères indiqués dans le modèle ci-dessous.

## <a name="pattern"></a>Modèle

- zéro à l’un des symboles supérieurs (>), apostrophe ('), signe égal (=), guillemet (« ) ou signe numérique (#)
- toute combinaison de 86 caractères qui sont des lettres minuscules ou majuscules, des chiffres, la barre oblique (/) ou le signe plus (+)
- deux signes égaux (=)

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `CEP_Regex_AzureStorageAccountKeyGeneric` trouve un contenu qui correspond au modèle.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```