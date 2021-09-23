---
title: Analyse du courrier électronique dans les enquêtes pour Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
keywords: réponse automatisée aux incidents, examen, correction, protection contre les menaces
description: Découvrez comment fonctionne l’analyse du courrier électronique dans les enquêtes dans Microsoft Defender pour Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 79867d5d22a78fda9f5b2049688a8bc0b63e9feb
ms.sourcegitcommit: 0ed93816e2c1e6620e68bd1c0f00390062911606
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2021
ms.locfileid: "59483254"
---
# <a name="email-analysis-in-investigations-for-microsoft-defender-for-office-365"></a>Analyse du courrier électronique dans les enquêtes pour Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Lors de l’examen automatisé des alertes, Microsoft Defender pour Office 365 analyse le courrier électronique d’origine pour identifier les menaces et identifie les autres messages électroniques liés à l’e-mail d’origine et potentiellement faisant partie d’une attaque. Cette analyse est importante, car les attaques de courrier électronique se composent rarement d’un seul e-mail.

L’analyse de messagerie de l’examen automatisé identifie les clusters de messagerie à l’aide des attributs de l’e-mail d’origine pour interroger les messages électroniques envoyés et reçus par votre organisation. Cela est similaire à ce qu’un analyste d’opérations de sécurité recherche les e-mails associés dans l’Explorateur ou la recherche avancée. Plusieurs requêtes sont utilisées pour identifier les e-mails correspondants, car les attaquants morphiquent généralement les paramètres de messagerie pour éviter la détection de sécurité. L’analyse de clustering effectue ces vérifications pour déterminer comment gérer les messages électroniques impliqués dans l’examen :

- L’analyse du courrier électronique crée des requêtes (clusters) d’e-mails à l’aide des attributs de l’e-mail d’origine : valeurs de l’expéditeur (adresse IP, domaine d’envoi) et contenu (objet, ID de cluster) afin de rechercher les e-mails associés.
- Si l’analyse des URL et des fichiers du courrier électronique d’origine identifie que certaines d’entre elles sont malveillantes (programme malveillant ou hameçonnage), elle crée également des requêtes ou des clusters d’e-mails contenant l’URL ou le fichier malveillant.
- L’analyse du clustering de messagerie compte les menaces associées aux e-mails correspondants dans le cluster pour déterminer si les e-mails sont malveillants, suspects ou ne sont pas clairement dangereux. Si le cluster d’e-mails correspondant à la requête présente une quantité suffisante de courrier indésirable, de hameçonnage normal, de hameçonnage à haut niveau de confiance ou de menaces de programmes malveillants, le cluster de messagerie reçoit ce type de menace qui lui est appliqué.
- L’analyse du clustering de messagerie vérifie également l’emplacement de remise le plus récent du courrier électronique d’origine et des e-mails dans les clusters de messagerie pour vous aider à identifier si les e-mails ont potentiellement encore besoin d’être suppression ou ont déjà été corrigés ou empêchés. Cette analyse est importante car les personnes malveillantes morphosent le contenu malveillant, ainsi que les stratégies de sécurité et la protection peuvent varier d’une boîte aux lettres à l’autre. Cette fonctionnalité entraîne des situations dans lesquelles du contenu malveillant peut toujours se trouver dans des boîtes aux lettres, même si un ou plusieurs e-mails malveillants ont été détectés et supprimés par une purge automatique d’heure zéro (ZAP).
- Les clusters de messagerie considérés comme malveillants en raison d’un programme malveillant, d’un hameçonnage à haut niveau de confiance, de fichiers malveillants ou de menaces d’URL malveillantes obtiennent une action en attente pour supprimer les messages électroniques lorsqu’ils se trouveraient toujours dans la boîte aux lettres cloud (boîte de réception ou dossier indésirable). Si les messages malveillants ou les clusters de messagerie ne sont que « Non dans la boîte aux lettres » (bloqué, mis en quarantaine, échoué, supprimé (logiciel, etc.) ou « Local/Externe » sans aucune action dans la boîte aux lettres cloud, aucune action en attente n’est définie pour les supprimer.
- Si l’un des clusters de messagerie est identifié comme malveillant, la menace identifiée par le cluster est appliquée de nouveau au courrier électronique d’origine impliqué dans l’enquête. Ce comportement est similaire à celui d’un analyste d’opérations de sécurité utilisant des résultats de recherche de courrier électronique pour déterminer le verdict d’un e-mail d’origine en fonction des e-mails correspondants. Ce résultat garantit que, que les URL, les fichiers ou les indicateurs de courrier source d’un e-mail d’origine soient détectés ou non, le système puisse identifier les e-mails malveillants susceptibles d’éviter toute détection par le biais de la personnalisation, de la morphose, de l’identité ou d’autres techniques d’attaque.
- Dans l’examen de compromission de l’utilisateur, des clusters de messagerie supplémentaires sont créés pour identifier les problèmes potentiels de messagerie créés par la boîte aux lettres. Ce processus inclut un cluster de courriers électroniques nettoyé (messages électroniques de qualité provenant de l’utilisateur, exfiltration potentielle de données et messages électroniques de commande/contrôle potentiels), des clusters de messagerie suspects (e-mails contenant du courrier indésirable ou un hameçonnage normal) et des clusters de messagerie malveillants (e-mails contenant des programmes malveillants ou un hameçonnage à haut niveau de confiance). Ces clusters de messagerie fournissent des données d’analystes d’opérations de sécurité pour déterminer les autres problèmes qui peuvent être résolus à partir d’une compromission et la visibilité sur laquelle les e-mails peuvent avoir déclenché les alertes d’origine (par exemple, hameçonnage/courrier indésirable qui a déclenché des restrictions d’envoi d’utilisateurs)

L’analyse du clustering de courrier électronique via des requêtes de similarité et d’entité malveillante garantit que les problèmes de messagerie sont entièrement identifiés et nettoyés, même si un seul e-mail d’une attaque est identifié. Vous pouvez utiliser des liens à partir des vues du panneau latéral détails du cluster de messagerie pour ouvrir les requêtes dans l’Explorateur ou la recherche avancée pour effectuer une analyse plus approfondie et modifier les requêtes si nécessaire. Cette fonctionnalité permet l’affinement et la correction manuelles si vous trouvez que les requêtes du cluster de messagerie sont trop étroites ou trop larges (y compris les e-mails non liés).

Voici d’autres améliorations apportées à l’analyse du courrier électronique dans les enquêtes.

## <a name="air-investigation-ignores-advanced-delivery-items-secops-mailbox-and-phishedu-messages"></a>L’examen AIR ignore les éléments de remise avancés (boîte aux lettres SecOps et messages PhishEDU)

Pendant l’analyse du clustering de courrier, toutes les requêtes de clustering ignoreront les boîtes aux lettres de sécurité définies en tant que boîtes aux lettres opérations de sécurité dans la stratégie de remise avancée. De même, les requêtes de clustering de courrier électronique ignorent les messages de simulation de hameçonnage (éducation) configurés dans la stratégie de remise avancée. Les valeurs d’exclusion SecOps et PhishEdu ne sont pas affichées dans la requête pour simplifier et faciliter la lecture des attributs de clustering. Cette exclusion garantit que les boîtes aux lettres opérationnelles et d’intelligence des menaces (boîtes aux lettres SecOps) et les simulations de hameçonnage (PhishEdu) sont ignorées pendant l’analyse des menaces et ne sont pas supprimées pendant toute correction.

>[!Note]
>Lors de l’ouverture d’un cluster de messagerie pour l’afficher dans l’Explorateur à partir des détails du cluster de messagerie, les filtres de boîte aux lettres PhishEdu et SecOps seront appliqués dans l’Explorateur, mais ne s’afficheront pas. Si vous modifiez les filtres, les dates ou l’actualisation de la requête dans la page, les exclusions de filtre PhishEdu/SecOps sont supprimées et les e-mails qui correspondent à ceux-ci s’afficheront à nouveau. Si vous actualisez la page Explorer à l’aide de la fonction d’actualisation du navigateur, les filtres de requête d’origine sont chargés à nouveau, y compris les filtres PhishEdu/SecOps, mais suppriment les modifications ultérieures que vous aviez apportées.
>

## <a name="air-updates-pending-email-action-status"></a>Mises à jour AIR en attente de l’état de l’action de courrier électronique

L’analyse de la messagerie d’investigation calcule les menaces et les emplacements de courrier électronique au moment de l’enquête pour créer les preuves et les actions de l’enquête. Ces données peuvent être obsolètes et obsolètes lorsque des actions en dehors de l’examen affectent les messages électroniques impliqués dans l’enquête. Par exemple, la recherche et la correction manuelles des opérations de sécurité peuvent nettoyer les messages électroniques inclus dans une enquête. De même, les actions de suppression approuvées dans des enquêtes parallèles ou des actions de mise en quarantaine automatique zap (Zero-hour auto purge) peuvent avoir supprimé des messages électroniques. En outre, les détections différées de menaces après la remise du courrier électronique peuvent modifier le nombre de menaces incluses dans les requêtes/clusters de messagerie de l’enquête.

Pour s’assurer que les actions d’examen sont à jour, toute enquête qui a des actions en attente ré-exécute régulièrement les requêtes d’analyse de courrier électronique pour mettre à jour les emplacements de courrier et les menaces.

- Lorsque les données du cluster de courrier électronique changent, les menaces et le nombre d’emplacements de remise les plus récents sont mis à jour.
- Si les messages électroniques ou le cluster de messagerie avec des actions en attente ne sont plus dans la boîte aux lettres, l’action en attente est annulée et le courrier électronique/cluster malveillant considéré comme corrigé.
- Une fois que toutes les menaces de l’enquête ont été résolues ou annulées, comme indiqué ci-dessus, l’enquête passe à un état corrigé et l’alerte d’origine est résolue.

## <a name="the-display-of-incident-evidence-for-email-and-email-clusters"></a>Affichage des preuves d’incident pour les clusters de messagerie et de messagerie

Les preuves basées sur un e-mail dans l’onglet Preuve et réponse pour un incident affichent désormais les informations suivantes.

:::image type="content" source="../../media/email-analysis-investigations/email-analysis-evidence-example.png" alt-text="Exemple d’informations d’analyse de courrier électronique dans Evidence and Response." lightbox="../../media/email-analysis-investigations/email-analysis-evidence-example.png":::

À partir des callouts numéroées dans la figure :

1. Vous pouvez effectuer des actions de correction, en plus du centre **de correction.**
2. Vous pouvez prendre des mesures correctives pour les clusters de messagerie avec **un** verdict malveillant (mais pas **suspect).**
3. Pour le verdict du courrier indésirable, le hameçonnage est divisé en hameçonnage normal et à niveau de confiance élevé.

   Pour un verdict malveillant, les catégories de menaces sont les programmes malveillants, le hameçonnage à haut niveau de confiance, l’URL malveillante et le fichier malveillant.

   Pour un verdict suspect, les catégories de menaces sont le courrier indésirable et le hameçonnage normal.

4. Le nombre de messages par est basé sur l’emplacement de remise le plus récent et inclut des compteurs pour les messages électroniques dans les boîtes aux lettres, pas dans les boîtes aux lettres et en local.
5. Inclut la date et l’heure de la requête, qui peuvent être mises à jour pour les données les plus récentes.

Pour les clusters de messagerie ou de messagerie dans l’onglet **Entités** d’un incident, **prevented** signifie qu’il n’y avait aucun courrier malveillant dans la boîte aux lettres pour cet élément (courrier ou cluster). Voici un exemple.

:::image type="content" source="../../media/email-analysis-investigations/email-analysis-evidence-example-prevented.png" alt-text="Exemple de message électronique interdit." lightbox="../../media/email-analysis-investigations/email-analysis-evidence-example-prevented.png":::

Dans cet exemple, le courrier électronique est malveillant, mais pas dans une boîte aux lettres.

## <a name="next-steps"></a>Étapes suivantes

- [Afficher les actions de correction en attente ou terminées](air-review-approve-pending-completed-actions.md)
