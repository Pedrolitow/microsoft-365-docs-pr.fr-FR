---
title: analyse Email dans les enquêtes sur les Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- m365-security
- m365initiative-defender-office365
keywords: réponse automatisée aux incidents, investigation, correction, protection contre les menaces
description: Découvrez le fonctionnement de l’analyse des e-mails dans les enquêtes dans Microsoft Defender pour Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 1d7c4f0f01f1aff00e36e5930fa9566e1f6a7993
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68048635"
---
# <a name="email-analysis-in-investigations-for-microsoft-defender-for-office-365"></a>analyse Email dans les enquêtes sur les Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Au cours de l’examen automatisé des alertes, Microsoft Defender pour Office 365 analyse l’e-mail d’origine à la recherche de menaces et identifie d’autres e-mails qui sont liés à l’e-mail d’origine et qui peuvent faire partie d’une attaque. Cette analyse est importante, car les attaques par e-mail se composent rarement d’un seul e-mail.

L’analyse des e-mails de l’enquête automatisée identifie les clusters de courrier à l’aide des attributs de l’e-mail d’origine pour rechercher les e-mails envoyés et reçus par votre organisation. Cela est similaire à ce qu’un analyste des opérations de sécurité recherche pour les e-mails associés dans l’Explorateur ou la chasse avancée. Plusieurs requêtes sont utilisées pour identifier les e-mails correspondants, car les attaquants transforment généralement les paramètres d’e-mail pour éviter la détection de sécurité. L’analyse du clustering effectue ces vérifications pour déterminer comment gérer les e-mails impliqués dans l’enquête :

- L’analyse de l’e-mail crée des requêtes (clusters) d’e-mails à l’aide d’attributs de l’e-mail d’origine : valeurs de l’expéditeur (adresse IP, domaine d’envoi) et contenu (objet, ID de cluster) afin de rechercher les e-mails associés.
- Si l’analyse des URL et fichiers de l’e-mail d’origine identifie que certains sont malveillants (autrement dit, des programmes malveillants ou des hameçonnages), il crée également des requêtes ou des clusters d’e-mails contenant l’URL ou le fichier malveillant.
- Email’analyse du clustering compte les menaces associées aux e-mails correspondants dans le cluster pour déterminer si les e-mails sont malveillants, suspects ou n’ont aucune menace claire. Si le cluster d’e-mails correspondant à la requête a une quantité suffisante de courrier indésirable, de hameçonnage normal, de menaces de hameçonnage ou de programmes malveillants à haut niveau de confiance, le cluster de messagerie reçoit ce type de menace qui lui est appliqué.
- L’analyse du clustering de courriers électroniques vérifie également l’emplacement de remise le plus récent de l’e-mail d’origine et des e-mails dans les clusters de messagerie pour déterminer si les e-mails ont potentiellement encore besoin d’être supprimés ou ont déjà été corrigés ou empêchés. Cette analyse est importante, car les attaquants transforment le contenu malveillant ainsi que les stratégies de sécurité et la protection peuvent varier d’une boîte aux lettres à l’autre. Cette fonctionnalité entraîne des situations où le contenu malveillant peut rester dans les boîtes aux lettres, même si un ou plusieurs e-mails malveillants ont été détectés et supprimés par le vidage automatique de zéro heure (ZAP).
- Email les clusters considérés comme malveillants en raison de programmes malveillants, de hameçonnage à haut niveau de confiance, de fichiers malveillants ou de menaces d’URL malveillantes bénéficient d’une action en attente de suppression réversible des e-mails lorsqu’ils se trouvent toujours dans la boîte aux lettres cloud (boîte de réception ou dossier indésirable). Si les e-mails malveillants ou les clusters de messagerie sont uniquement « Non dans la boîte aux lettres » (bloqué, mis en quarantaine, échoué, supprimé de manière réversible, etc.) ou « Local/Externe » sans aucune dans la boîte aux lettres cloud, aucune action en attente n’est configurée pour les supprimer.
- Si l’un des clusters de messagerie est déterminé comme malveillant, la menace identifiée par le cluster est appliquée à l’e-mail d’origine impliqué dans l’enquête. Ce comportement est similaire à celui d’un analyste des opérations de sécurité qui utilise les résultats de la chasse aux e-mails pour déterminer le verdict d’un e-mail d’origine en fonction des e-mails correspondants. Ce résultat garantit que, que les URL, les fichiers ou les indicateurs de messagerie source d’un e-mail d’origine soient détectés ou non, le système peut identifier les e-mails malveillants susceptibles d’échapper à la détection par le biais de la personnalisation, de la morphisation, de l’évasion ou d’autres techniques d’attaque.
- Dans l’enquête de compromission de l’utilisateur, des clusters de messagerie supplémentaires sont créés pour identifier les problèmes de messagerie potentiels créés par la boîte aux lettres. Ce processus inclut un cluster de courrier propre (bons e-mails de l’utilisateur, exfiltration de données potentielle et e-mails de commande/contrôle potentiels), des clusters de courrier suspect (e-mails contenant du courrier indésirable ou un hameçonnage normal) et des clusters de courrier malveillant (e-mails contenant des programmes malveillants ou hameçonnage à haut niveau de confiance). Ces clusters de messagerie fournissent des données d’analystes des opérations de sécurité pour déterminer quels autres problèmes doivent être résolus à partir d’une compromission, et une visibilité sur les e-mails qui peuvent avoir déclenché les alertes d’origine (par exemple, les hameçonnages/courriers indésirables qui ont déclenché des restrictions d’envoi d’utilisateurs)

Email l’analyse du clustering par le biais de requêtes d’entité malveillantes et de similarité garantit que les problèmes de messagerie sont entièrement identifiés et nettoyés, même si un seul e-mail d’une attaque est identifié. Vous pouvez utiliser des liens à partir des vues du volet latéral détails du cluster de courrier pour ouvrir les requêtes dans l’Explorateur ou La chasse avancée afin d’effectuer une analyse plus approfondie et de modifier les requêtes si nécessaire. Cette fonctionnalité permet l’affinement et la correction manuels si vous trouvez les requêtes du cluster de messagerie trop étroites ou trop larges (y compris les e-mails non liés).

Voici d’autres améliorations apportées à l’analyse des e-mails dans les enquêtes.

## <a name="air-investigation-ignores-advanced-delivery-items-secops-mailbox-and-phishedu-messages"></a>L’enquête AIR ignore les éléments de remise avancés (boîte aux lettres SecOps et messages PhishEDU)

Pendant l’analyse du clustering de courriers électroniques, toutes les requêtes de clustering ignorent les boîtes aux lettres de sécurité configurées en tant que boîtes aux lettres Opérations de sécurité dans la stratégie de remise avancée. De même, les requêtes de clustering de courriers électroniques ignorent les messages de simulation de hameçonnage (éducation) configurés dans la stratégie advanced delivery. Ni les valeurs d’exclusion SecOps ni PhishEdu ne sont affichées dans la requête pour simplifier et faciliter la lecture des attributs de clustering. Cette exclusion garantit que le renseignement sur les menaces et les boîtes aux lettres opérationnelles (boîtes aux lettres SecOps) et les simulations de hameçonnage (PhishEdu) sont ignorés pendant l’analyse des menaces et ne sont pas supprimés pendant toute correction.

>[!Note]
>Lors de l’ouverture d’un cluster de messagerie pour l’afficher dans l’Explorateur à partir des détails du cluster de messagerie, les filtres de boîte aux lettres PhishEdu et SecOps sont appliqués dans l’Explorateur, mais ne s’affichent pas. Si vous modifiez les filtres, les dates ou l’actualisation de la requête dans la page de l’Explorateur, les exclusions de filtre PhishEdu/SecOps sont supprimées et les e-mails correspondant à ceux-ci s’affichent à nouveau. Si vous actualisez la page Explorateur à l’aide de la fonction d’actualisation du navigateur, les filtres de requête d’origine sont retentés, y compris les filtres PhishEdu/SecOps, mais suppriment les modifications ultérieures que vous avez apportées.
>

## <a name="air-updates-pending-email-action-status"></a>État de l’action d’e-mail en attente des mises à jour AIR

L’analyse du courrier électronique de l’enquête calcule les menaces de courrier électronique et les emplacements au moment de l’enquête pour créer la preuve et les actions de l’enquête. Ces données peuvent devenir obsolètes lorsque des actions en dehors de l’enquête affectent les e-mails impliqués dans l’enquête. Par exemple, la chasse et la correction manuelles des opérations de sécurité peuvent nettoyer les e-mails inclus dans une enquête. De même, les actions de suppression approuvées dans le cas d’enquêtes parallèles ou les actions de mise en quarantaine automatique de vidage automatique de zéro heure (ZAP) peuvent avoir supprimé les e-mails. En outre, les détections différées de menaces après la remise du courrier électronique peuvent modifier le nombre de menaces incluses dans les requêtes/clusters de messagerie de l’enquête.

Pour vous assurer que les actions d’investigation sont à jour, toute enquête comportant des actions en attente réexécutera régulièrement les requêtes d’analyse de messagerie pour mettre à jour les emplacements et les menaces de courrier.

- Lorsque les données du cluster de messagerie changent, elles mettent à jour le nombre de menaces et d’emplacements de remise les plus récents.
- Si les e-mails ou le cluster d’e-mails avec des actions en attente ne sont plus dans la boîte aux lettres, l’action en attente est annulée et l’e-mail/cluster malveillant considéré comme corrigé.
- Une fois que toutes les menaces de l’enquête ont été corrigées ou annulées comme indiqué ci-dessus, l’enquête passe à un état corrigé et l’alerte d’origine est résolue.

## <a name="the-display-of-incident-evidence-for-email-and-email-clusters"></a>Affichage des preuves d’incident pour les clusters de messagerie et de messagerie

Email preuves basées sur la preuve et la réponse dans l’onglet **Preuve et réponse** pour un incident affiche maintenant les informations suivantes.

:::image type="content" source="../../media/email-analysis-investigations/email-analysis-evidence-example.png" alt-text="Informations d’analyse de l’e-mail dans Evidence and Response" lightbox="../../media/email-analysis-investigations/email-analysis-evidence-example.png":::

À partir des légendes numérotées dans la figure :

1. Vous pouvez effectuer des actions de correction, en plus du **Centre d’actions**.
2. Vous pouvez prendre des mesures de correction pour les clusters de messagerie avec un verdict **malveillant** (mais pas **suspect**).
3. Pour le verdict relatif au courrier indésirable, le hameçonnage est divisé en un niveau de confiance élevé et un hameçonnage normal.

   Pour un verdict malveillant, les catégories de menaces sont les programmes malveillants, le hameçonnage à haut niveau de confiance, l’URL malveillante et le fichier malveillant.

   Pour un verdict suspect, les catégories de menaces sont le courrier indésirable et le hameçonnage normal.

4. Le nombre d’e-mails par est basé sur l’emplacement de livraison le plus récent et inclut les compteurs de courrier électronique dans les boîtes aux lettres, et non dans les boîtes aux lettres et localement.
5. Inclut la date et l’heure de la requête, qui peuvent être mises à jour pour les données les plus récentes.

Pour les clusters de courrier électronique ou de messagerie sous l’onglet **Entités** d’un incident, **l’option Prévention** signifie qu’il n’y avait aucun e-mail malveillant dans la boîte aux lettres pour cet élément (courrier ou cluster). Voici un exemple.

:::image type="content" source="../../media/email-analysis-investigations/email-analysis-evidence-example-prevented.png" alt-text="E-mail empêché." lightbox="../../media/email-analysis-investigations/email-analysis-evidence-example-prevented.png":::

Dans cet exemple, l’e-mail est malveillant, mais pas dans une boîte aux lettres.

## <a name="next-steps"></a>Prochaines étapes

- [Afficher les actions de correction en attente ou terminées](air-review-approve-pending-completed-actions.md)
