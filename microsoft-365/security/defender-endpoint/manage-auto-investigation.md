---
title: Examiner les actions de correction à la suite d’examens automatisés
description: Examiner et approuver (ou rejeter) les actions de correction à la suite d’un examen automatisé.
keywords: autoir, automatisé, investigation, détection, correction, action, en attente, approuvé
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: how-to
ms.date: 01/29/2021
ms.technology: mde
ms.openlocfilehash: 48674292e5a72ccc371ff4bf43dc499f19b3886d
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064054"
---
# <a name="review-remediation-actions-following-an-automated-investigation"></a>Examiner les actions de correction à la suite d’un examen automatisé

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


## <a name="remediation-actions"></a>Actions de correction

[Lorsqu’une enquête automatisée](automated-investigations.md) s’exécute, un verdict est généré pour chaque élément de preuve examiné. Les verdicts peuvent être *malveillants,* *suspects* ou *aucune menace trouvée.* 

En fonction de

- le type de menace, 
- le verdict qui en résulte et 
- la configuration des groupes [d’appareils](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/machine-groups) de votre organisation ; 

Les actions de correction peuvent se produire automatiquement ou uniquement après approbation par l’équipe des opérations de sécurité de votre organisation. 

Voici quelques exemples :

- **Exemple 1**: les groupes d’appareils de Fabrikam sont définies sur **Complet :** corriger les menaces automatiquement (paramètre recommandé). Dans ce cas, des actions de correction sont effectuées automatiquement pour les artefacts considérés comme malveillants à la suite d’un examen automatisé (voir Examiner [les actions terminées).](#review-completed-actions)

- **Exemple 2**: les appareils de Contoso sont inclus dans un groupe d’appareils qui est définie pour Semi - exiger l’approbation de **toute correction.** Dans ce cas, l’équipe des opérations de sécurité de Contoso doit examiner et approuver toutes les actions de correction à la suite d’un examen automatisé (voir Examiner [les actions en attente).](#review-pending-actions)

- **Exemple 3 :** Les groupes d’appareils Tailspin Toys ont la réponse **automatisée** Non (non recommandé). Dans ce cas, les examens automatisés ne se produisent pas. Aucune action de correction n’est prise ou en [](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center) attente, et aucune action n’est enregistrée dans le centre de gestion des périphériques pour leurs appareils (voir Gérer les groupes [d’appareils).](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/machine-groups#manage-device-groups)

Qu’elle soit prise automatiquement ou après approbation, une enquête automatisée peut entraîner une ou plusieurs des actions de correction :
- Mettre en quarantaine un fichier
- Supprimer une clé de Registre 
- Kill a process 
- Arrêter un service 
- Désactiver un pilote 
- Supprimer une tâche programmée

## <a name="review-pending-actions"></a>Passer en revue les actions en attente

1. Go to the Microsoft 365 security center ( [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.
2. Dans le volet de navigation, choisissez **Centre de notifications**. 
3. Examinez les éléments sous **l’onglet En** attente. 
4. Sélectionnez une action pour ouvrir son volet volant.
5. Dans le volet volant, examinez les informations, puis prenez l’une des étapes suivantes :
   - Sélectionnez **Ouvrir la page Examen** pour afficher plus de détails sur l’enquête.
   - Sélectionnez **Approuver** pour lancer une action en attente.
   - Sélectionnez **Rejeter** pour empêcher une action en attente d’être prise.
   - Sélectionnez **Go hunt** (Aller à la recherche) pour passer [à la recherche avancée](advanced-hunting-overview.md). 

## <a name="review-completed-actions"></a>Passer en revue les actions terminées

1. Go to the Microsoft 365 security center ( [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.
2. Dans le volet de navigation, choisissez **Centre de notifications**. 
3. Examinez les éléments sous **l’onglet** Historique. 
4. Sélectionnez un élément pour afficher plus de détails sur cette action de correction.
 
## <a name="undo-completed-actions"></a>Annuler les actions terminées

Si vous avez déterminé qu’un appareil ou un fichier n’est pas une menace, vous pouvez annuler les actions de correction qui ont été prises, que ces actions soient prises automatiquement ou manuellement. Dans le centre de actions, sous **l’onglet** Historique, vous pouvez annuler l’une des actions suivantes :  

| Source d’action | Actions prises en charge |
|:---|:---|
| - Examen automatisé <br/>- Antivirus Microsoft Defender <br/>- Actions de réponse manuelles | - Isoler l’appareil <br/>- Restreindre l’exécution du code <br/>- Mettre en quarantaine un fichier <br/>- Supprimer une clé de Registre <br/>- Arrêter un service <br/>- Désactiver un pilote <br/>- Supprimer une tâche programmée |

### <a name="to-undo-multiple-actions-at-one-time"></a>Pour annuler plusieurs actions à la fois

1. Go to the Action center ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ) and sign in.
2. Sous **l’onglet** Historique, sélectionnez les actions à annuler. Veillez à sélectionner les éléments qui ont le même type d’action. Un volet volant s’ouvre.
3. Dans le volet volant, sélectionnez **Annuler.**

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Pour supprimer un fichier de la quarantaine sur plusieurs appareils 

1. Go to the Action center ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ) and sign in.
2. Sous **l’onglet** Historique, sélectionnez un élément qui possède le fichier de mise en quarantaine du type **d’action.**
3. Dans le volet volant, sélectionnez Appliquer **à X plus d’instances** de ce fichier, puis **sélectionnez Annuler**.

## <a name="automation-levels-automated-investigation-results-and-resulting-actions"></a>Niveaux d’automatisation, résultats d’enquête automatisés et actions résultantes

Les niveaux d’automatisation affectent si certaines actions de correction sont prises automatiquement ou uniquement lors de l’approbation. Parfois, votre équipe en matière d’opérations de sécurité a davantage d’étapes à suivre, en fonction des résultats d’une enquête automatisée. Le tableau suivant récapitule les niveaux d’automatisation, les résultats des enquêtes automatisées et la procédure à suivre dans chaque cas. 

|Paramètre de groupe d’appareils | Résultats d’enquête automatisés | Procédure |
|:---|:---|:---|
|**Complète : corriger automatiquement les menaces** (paramètre recommandé) |Un verdict de *malveillant est* atteint pour une preuve. <br/><br/>Des mesures correctives appropriées sont prises automatiquement. |[Passer en revue les actions terminées](#review-completed-actions) |
|**Complète : corriger automatiquement les menaces** |Un verdict suspect *est* atteint pour un élément de preuve. <br/><br/>Les actions de correction sont en attente d’approbation pour continuer. | [Approuver (ou rejeter) les actions en attente](#review-pending-actions) |
|**Semi - exiger l’approbation de toutes les corrections**  |Un verdict de malveillant *ou* *suspect est* atteint pour un élément de preuve. <br/><br/>Les actions de correction sont en attente d’approbation pour continuer.  |[Approuver (ou rejeter) les actions en attente](#review-pending-actions) |
|**Semi - exiger l’approbation pour la correction des dossiers principaux** |Un verdict de *malveillant est* atteint pour une preuve. <br/><br/>Si l’artefact est un fichier ou un exécutable et se trouve dans un répertoire du système d’exploitation, tel que le dossier Windows ou le dossier Des fichiers de programme, les actions de correction sont en attente d’approbation. <br/><br/>Si l’artefact ne *se trouve pas* dans un répertoire du système d’exploitation, des actions de correction sont prises automatiquement. |1. Approuver [(ou rejeter) les actions en attente](#review-pending-actions)<br/><br/>2. Examiner [les actions terminées](#review-completed-actions) |
|**Semi - exiger l’approbation pour la correction des dossiers principaux** |Un verdict suspect *est* atteint pour un élément de preuve. <br/><br/>Les actions de correction sont en attente d’approbation.  |[Approuver (ou rejeter) les actions en attente](#review-pending-actions).|
|**Semi - exiger l’approbation pour la correction des dossiers non temporaires** |Un verdict de *malveillant est* atteint pour une preuve. <br/><br/>Si l’artefact est un fichier ou un exécutable qui ne se trouve pas dans un dossier temporaire, tel que le dossier de téléchargement ou le dossier temporaire de l’utilisateur, les actions de correction sont en attente d’approbation. <br/><br/>Si l’artefact est un  fichier ou un exécutable qui se trouve dans un dossier temporaire, des actions de correction sont prises automatiquement.  |1. Approuver [(ou rejeter) les actions en attente](#review-pending-actions)<br/><br/>2. Examiner [les actions terminées](#review-completed-actions)  |
|**Semi - exiger l’approbation pour la correction des dossiers non temporaires** |Un verdict suspect *est* atteint pour un élément de preuve. <br/><br/>Les actions de correction sont en attente d’approbation. |[Approuver (ou rejeter) les actions en attente](#review-pending-actions)  | 
|N’importe quel **niveau d’automatisation** complet **ou** semi-automatique |Un verdict *d’absence de menaces* trouvées est atteint pour une preuve. <br/><br/>Aucune action de correction n’est prise et aucune action n’est en attente d’approbation. |[Consulter les détails et les résultats des enquêtes automatisées](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/auto-investigation-action-center) |
|**Aucune réponse automatisée** (non recommandée)|Aucune enquête automatisée ne s’exécute, donc aucun verdict n’est atteint et aucune action de correction n’est prise ou en attente d’approbation. |[Envisagez de définir ou de modifier vos groupes d’appareils pour utiliser **l’automatisation** complète **ou semi-automatique**](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/machine-groups) |

Dans Microsoft Defender pour le point de terminaison, tous les verdicts sont suivis dans le centre [de l’action.](auto-investigation-action-center.md#new-a-unified-action-center)

## <a name="next-steps"></a>Étapes suivantes

- [En savoir plus sur les fonctionnalités de réponse en direct](live-response.md)
- [Recherche proactive des menaces avec le chasse avancée](advanced-hunting-overview.md)
- [Corriger les faux positifs/négatifs dans Microsoft Defender pour le point de terminaison](defender-endpoint-false-positives-negatives.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des examens automatisés](automated-investigations.md)