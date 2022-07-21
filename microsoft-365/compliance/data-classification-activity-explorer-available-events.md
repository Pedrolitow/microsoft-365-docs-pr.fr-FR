---
title: Actions d'étiquetage signalées dans l'Explorateur d'activités
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Liste des activités d’étiquetage disponibles dans l’Explorateur d’activités.
ms.openlocfilehash: 27a6bb3f0fe4293d5904c7e1661ef1e422fbac5b
ms.sourcegitcommit: 24827a509b3e78959ce67679646e572a0c996282
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66917867"
---
# <a name="labeling-activities-that-are-available-in-activity-explorer"></a>Activités d’étiquetage disponibles dans l’Explorateur d’activités

## <a name="sensitivity-label-applied"></a>Étiquette de confidentialité appliquée

Cet événement est généré chaque fois qu’un document sans étiquette est étiqueté ou qu’un e-mail est envoyé avec une étiquette de confidentialité.

- Il est capturé au moment de l’enregistrement dans les applications natives Office et les applications web.
- Il est capturé au moment de l’occurrence pour le client d’étiquetage unifié Azure Information Protection (AIP).
- Les actions de mise à niveau et de rétrogradation des étiquettes peuvent également être surveillées via le champ de *type d’événement Label* et le filtre.

|Source  |Signalé dans l’Explorateur d’activités | Remarque  |
|---------|---------|---------|
| Word, Excel, PowerPoint|Oui |
|Outlook| Oui | |
|SharePoint online, OneDrive|Oui | |
|Exchange        |Oui         | |
|Client unifié Azure Information Protection (AIP) et scanneur unifié AIP |Oui |L’action *nouvelle étiquette* AIP est mappée à *l’étiquette appliquée* dans l’Explorateur d’activités   |
|SDK Protection des données Microsoft (MIP)         |Oui|L’action *nouvelle étiquette* AIP est mappée à *l’étiquette appliquée* dans l’Explorateur d’activités|
|Rights Management Service (RMS)         |Non applicable         | |
|Power BI Desktop et web        | Non| Accessible dans les journaux d’audit Microsoft 365         |
|Microsoft Defender for Cloud Apps         |Non|         |

## <a name="sensitivity-label-changed"></a>Étiquette de confidentialité modifiée

Cet événement est généré chaque fois qu’une étiquette de confidentialité est mise à jour sur le document ou l’e-mail.

- Pour le client unifié AIP, le scanneur unifié AIP et les sources du Kit de développement logiciel (SDK) MIP, *l’étiquette de mise à niveau* AIP et l’action de *rétrogradage des étiquettes* sont mappées à l’étiquette De l’Explorateur d’activités *modifiée*

- Il est capturé au moment de l’enregistrement dans les applications natives Office et les applications web.
- Il est capturé au moment de l’occurrence pour les contrôles d’application du client d’étiquetage unifié AIP et du scanneur
- Les actions de mise à niveau et de rétrogradation des étiquettes peuvent également être surveillées via le champ de *type d’événement Label* et le filtre. Le texte *de justification* est également capturé, à l’exception de SharePoint Online et OneDrive.
- L’étiquetage de confidentialité effectué dans les applications natives Office sur Outlook collecte la dernière action qui a été générée avant les actions d’enregistrement de fichier/d’envoi d’e-mail. Par exemple, si l’utilisateur modifie l’étiquette d’un e-mail plusieurs fois avant l’envoi, la dernière étiquette trouvée sur l’e-mail lorsqu’il est envoyé est capturée dans le journal d’audit, puis signalée dans l’Explorateur d’activités.

|Source  |Signalé dans l’Explorateur d’activités|Remarque  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Oui         |
|Outlook         |Oui         |
|SharePoint Online, OneDrive         |Oui         |
|Exchange         |Oui         |
|Client unifié AIP         |Oui         |
|Scanneur unifié AIP         |Oui         |
|Kit de développement logiciel (SDK) MIP         |Oui         |
|Service RMS         |Non applicable         |
|Power BI Desktop et Web         |Non         |Accessible dans les journaux d’audit Microsoft 365 |
|Microsoft Defender for Cloud Apps     |Non         |         |

## <a name="sensitivity-label-removed"></a>Étiquette de confidentialité supprimée

Cet événement est généré chaque fois qu’une étiquette de confidentialité est supprimée d’un fichier ou d’un document.

- Cet événement est capturé au moment de l’enregistrement dans les applications natives Office et les applications web.
- Il est capturé au moment de l’occurrence pour le client d’étiquetage unifié Azure Information Protection (AIP).
- L’étiquetage de confidentialité, avec des étiquettes intégrées à Office, sur Outlook collecte le dernier événement d’étiquetage qui a été généré avant les actions d’enregistrement de fichier/d’envoi d’e-mail.

|Source  |Signalé dans l’Explorateur d’activités | Remarque  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Oui         |
|Outlook         |Oui         ||
|SharePoint Online, OneDrive         |Oui         |
|Exchange         |Oui         |
|Client unifié AIP         |Oui         |L’action *supprimer l’étiquette* AIP est mappée à l’action *suppression d’étiquette* dans l’Explorateur d’activités|
|Scanneur unifié AIP         |Oui         |L’action *supprimer l’étiquette* AIP est mappée à l’action *suppression d’étiquette* dans l’Explorateur d’activités |
|Kit de développement logiciel (SDK) MIP         |Oui         |L’action *supprimer l’étiquette* AIP est mappée à l’action *suppression d’étiquette* dans l’Explorateur d’activités |
|Service RMS         |Non applicable         |
|Power BI Desktop et Web         |Non         |Accessible dans les journaux d’audit Microsoft 365 |
|Microsoft Defender for Cloud Apps     |Non         |         |

## <a name="sensitivity-label-file-read"></a>Lecture du fichier d’étiquette de confidentialité

Cet événement est généré chaque fois qu’un document de confidentialité étiqueté ou protégé est ouvert.

|Source  |Signalé dans l’Explorateur d’activités | Remarque  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Oui         |
|Outlook         |Non         |
|SharePoint Online, OneDrive         |Non         |
|Exchange         |Non         |
|Client unifié AIP         |Oui         |L’action *d’accès* AIP est mappée à l’action de *lecture de fichier* dans l’Explorateur d’activités|
|Scanneur unifié AIP         |Oui         |L’action *d’accès* AIP est mappée à l’action de *lecture de fichier* dans l’Explorateur d’activités|
|Kit de développement logiciel (SDK) MIP         |Oui         |L’action *d’accès* AIP est mappée à l’action de *lecture de fichier* dans l’Explorateur d’activités|
|Service RMS         |Oui         |L’action *d’accès* est mappée à l’action de *lecture de fichier* dans l’Explorateur d’activités |
|Power BI Desktop et Web         |Non         |Accessible dans les journaux d’audit Microsoft 365 |
|Microsoft Defender for Cloud Apps     |Non         |         |

## <a name="files-discovered"></a>Fichiers découverts

Cet événement est généré chaque fois que des fichiers sont découverts lorsque le scanneur AIP est utilisé pour analyser des données sensibles à différents emplacements et trouve des fichiers.

|Source  |Signalé dans l’Explorateur d’activités | Remarque  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Non applicable         |
|Outlook         |Non applicable         |
|SharePoint Online, OneDrive         |Non applicable         |
|Exchange         |Non applicable         |
|Client unifié AIP         |Non applicable       |
|Scanneur unifié AIP         |Oui         |L’action *de découverte* AIP est *mappée aux fichiers découverts* dans l’Explorateur d’activités|
|Kit de développement logiciel (SDK) MIP         |Oui         |L’action *de découverte* AIP est mappée à l’action *découverte de fichier* dans l’Explorateur d’activités|
|Service RMS         |Non applicable         |
|Power BI Desktop et Web         |Non applicable         |
|Microsoft Defender for Cloud Apps     |Non applicable         |         |

## <a name="sensitivity-label-file-renamed"></a>Fichier d’étiquette de confidentialité renommé

Cet événement est généré chaque fois qu’un document avec une étiquette de confidentialité est renommé.

|Source  | Signalé dans l’Explorateur d’activités | Remarque  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Oui         |
|Outlook         |Non applicable         |
|SharePoint Online, OneDrive         |Non        |
|Exchange         |Non applicable         |
|Client unifié AIP         |Non         |
|Scanneur unifié AIP         |Non         |
|Kit de développement logiciel (SDK) MIP         |Non         |
|Service RMS         |Non      |
|Power BI Desktop et Web         |Non         |
|Microsoft Defender for Cloud Apps     |Non         |         |

## <a name="file-removed"></a>Fichier supprimé

Cet événement est généré chaque fois que le scanneur AIP détecte qu’un fichier précédemment analysé a été supprimé.

|Source  |Signalé dans l’Explorateur d’activités | Remarque  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Non applicable         |
|Outlook         |Non applicable         |
|SharePoint Online, OneDrive         |Non applicable           |
|Exchange         |Non applicable         |
|Client unifié AIP         |Non applicable            |
|Scanneur unifié AIP         |Oui         |
|Kit de développement logiciel (SDK) MIP         |Non applicable            |
|Service RMS         |Non applicable         |
|Power BI Desktop et Web         |Non applicable  |
|Microsoft Defender for Cloud Apps     |Non applicable        |         |

### <a name="protection-applied"></a>Protection appliquée

Cet événement est généré. La première protection est ajoutée manuellement à un élément qui n’a pas d’étiquette.

|Source  |Signalé dans l’Explorateur d’activités | Remarque  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Non         |
|Outlook         |Non         |
|SharePoint Online, OneDrive         |Non applicable           |
|Exchange         |Non       |
|Client unifié AIP         |Oui            |
|Scanneur unifié AIP         |Non applicable         |
|Kit de développement logiciel (SDK) MIP         |Oui            |
|Service RMS         |Non applicable         |
|Power BI Desktop et Web         |Non applicable            |
|Microsoft Defender for Cloud Apps     |Non applicable        |         |

## <a name="protection-changed"></a>Protection modifiée

Cet événement est généré chaque fois que la protection sur un document sans étiquette est modifiée manuellement.

|Source  |Signalé dans l’Explorateur d’activités |
|---------|---------|
|Word, Excel, PowerPoint         |Non         |
|Outlook         |Non         |
|SharePoint Online, OneDrive         |Non applicable           |
|Exchange         |Non       |
|Client unifié AIP         |Oui            |
|Scanneur unifié AIP         |Non applicable         |
|Kit de développement logiciel (SDK) MIP         |Oui            |
|Service RMS         |Non applicable         |
|Power BI Desktop et Web         |Non applicable            |
|Microsoft Defender for Cloud Apps     |Non applicable        |

## <a name="protection-removed"></a>Protection supprimée

Cet événement est généré chaque fois que la protection sur un document sans étiquette est modifiée manuellement.

|Source  |Signalé dans l’Explorateur d’activités |
|---------|---------|
|Word, Excel, PowerPoint         |Non         |
|Outlook         |Non         |
|SharePoint Online, OneDrive         |Non applicable           |
|Exchange         |Non       |
|Client unifié AIP         |Oui            |
|Scanneur unifié AIP         |Non applicable         |
|Kit de développement logiciel (SDK) MIP         |Oui            |
|Service RMS         |Non applicable         |
|Power BI Desktop et Web         |Non applicable            |
|Microsoft Defender for Cloud Apps     |Non applicable        |

## <a name="dlp-policy-matched"></a>Stratégie DLP mise en correspondance

Cet événement est généré chaque fois qu’une stratégie DLP est mise en correspondance sur un document ou un e-mail.

|Source  |Signalé dans l’Explorateur d’activités |
|---------|---------|
|Exchange         |Oui       |
|SharePoint Online|Oui          |
|OneDrive |Oui|
|Équipes |Oui   |
|Appareils Windows 10         |Oui |
|MAC         |Non     |
|Sur site         |Non|
|Microsoft Defender for Cloud Apps     |Non        |

Les événements pour les appareils Windows 10 (DLP de point de terminaison) sont les suivants :

- Fichier supprimé
- Fichier créé
- Fichier copié dans le Presse-papiers
- Fichier modifié
- Fichier lu
- Fichier imprimé
- Fichier renommé
- Fichier copié sur le partage réseau
- Fichier consulté par une application non autorisée

## <a name="retention-label-applied"></a>Étiquette de rétention appliquée

Cet événement est généré chaque fois qu’un document sans étiquette est étiqueté ou qu’un e-mail est envoyé avec une étiquette de rétention.

- Il est capturé au moment de l’enregistrement d’un document et au moment de l’envoi d’un e-mail.

|Source  |Signalé dans l’Explorateur d’activités |
|---------|---------|
|Exchange         |Non       |
|SharePoint Online|Oui          |
|OneDrive |Oui|

## <a name="retention-label-changed"></a>Étiquette de rétention modifiée

Cet événement est généré chaque fois qu’une étiquette est mise à jour sur un document ou un e-mail.

- Il est capturé au moment de l’enregistrement d’un document et au moment de l’envoi d’un e-mail.

|Source  |Signalé dans l’Explorateur d’activités |
|---------|---------|
|Exchange         |Non       |
|SharePoint Online|Oui          |
|OneDrive |Oui|

## <a name="retention-label-removed"></a>Étiquette de rétention supprimée

Cet événement est généré chaque fois qu’une étiquette est supprimée d’un fichier ou d’un document.

- Il est capturé au moment de l’enregistrement d’un document et au moment de l’envoi d’un e-mail.

|Source  |Signalé dans l’Explorateur d’activités |
|---------|---------|
|Exchange         |Non       |
|SharePoint Online|Oui          |
|OneDrive |Oui|

## <a name="known-issues"></a>Problèmes connus
  
- Lorsque l’info-bulle d’outil d’étiquette recommandée est affichée à un utilisateur final, elle n’est pas capturée. Toutefois, si l’utilisateur choisit d’appliquer l’étiquette recommandée, l’étiquette s’affiche sous le champ *Comment appliqué* comme *recommandé*.

- Le texte de justification n’est actuellement pas disponible sur l’étiquette de confidentialité rétrogradée à partir de SharePoint et OneDrive.

- Les types d’informations sensibles ne sont actuellement pas disponibles pour les activités d’étiquetage automatique à partir de Word, Excel, PowerPoint et Outlook, ainsi que SharePoint Online et OneDrive.
