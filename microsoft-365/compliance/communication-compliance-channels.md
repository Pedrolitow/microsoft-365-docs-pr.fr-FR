---
title: Détecter les signaux des canaux à l’aide de la conformité des communications
description: En savoir plus sur la détection des signaux de canal avec la conformité des communications.
keywords: Microsoft 365, Microsoft Purview, conformité, conformité des communications
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 0769dd3cfd64f611162803952a1e39b9241ac2ad
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638661"
---
# <a name="detect-channel-signals-with-communication-compliance"></a>Détecter les signaux des canaux à l’aide de la conformité des communications

Avec les stratégies de conformité des communications, vous pouvez choisir d’analyser les messages dans une ou plusieurs des plateformes de communication suivantes en tant que groupe ou en tant que sources autonomes. Les messages d’origine capturés sur ces plateformes sont conservés à l’emplacement de la plateforme d’origine conformément aux stratégies de [rétention et de conservation](/microsoft-365/compliance/information-governance) de votre organisation. Les copies des messages utilisés par les stratégies de conformité des communications pour l’analyse et l’investigation sont conservées tant que la stratégie est en place, même si les utilisateurs quittent votre organisation et que leurs boîtes aux lettres sont supprimées. Lorsqu’une stratégie de communication est supprimée, des copies des messages associés à la stratégie sont également supprimées.

## <a name="microsoft-teams"></a>Microsoft Teams

Les communications de conversation dans les canaux Microsoft Teams publics et privés et les conversations individuelles peuvent être analysées. Lorsque les utilisateurs sont affectés à une stratégie de conformité des communications avec la couverture Microsoft Teams sélectionnée, les communications de conversation pour les utilisateurs sont automatiquement surveillées dans toutes les équipes Microsoft où les utilisateurs sont membres. La couverture Microsoft Teams est automatiquement incluse pour les modèles de stratégie prédéfinis et est sélectionnée par défaut dans le modèle de stratégie personnalisé. Le traitement des conversations Teams correspondant aux conditions de stratégie de conformité des communications peut prendre jusqu’à 48 heures.

Pour les conversations privées et les canaux privés, les stratégies de conformité des communications prennent en charge [les canaux partagés](/MicrosoftTeams/shared-channels) et l’analyse moderne des pièces jointes. La prise en charge des canaux partagés dans Teams est gérée automatiquement et ne nécessite pas de modifications supplémentaires de la configuration de conformité des communications. Le tableau suivant récapitule le comportement de conformité des communications lors du partage de canaux Teams avec des groupes et des utilisateurs :

|**Scénario**|**Comportement de conformité des communications**|
|:-----------|:------------------------------------|
| **Partager un canal avec une équipe interne** | Les stratégies de conformité des communications s’appliquent aux utilisateurs dans l’étendue et à tous les messages du canal partagé |
| **Partager un canal avec une équipe externe** | Les stratégies de conformité des communications s’appliquent aux utilisateurs internes dans l’étendue et aux messages dans le canal partagé pour l’organisation interne |

Les pièces jointes modernes sont des fichiers provenant de sites [OneDrive](/onedrive/plan-onedrive-enterprise#modern-attachments) ou [SharePoint](/sharepoint/dev/solution-guidance/modern-experience-customizations) inclus dans les messages Teams. Le texte est automatiquement extrait de ces pièces jointes pour un traitement automatisé et des correspondances potentielles avec des conditions et classifieurs de stratégie de conformité de communication actifs. Aucune configuration supplémentaire n’est nécessaire pour la détection et le traitement des pièces jointes modernes. Le texte est extrait uniquement pour les pièces jointes correspondant aux conditions de stratégie. Le texte n’est pas extrait pour les pièces jointes pour les messages avec des correspondances de stratégie, même si la pièce jointe a également une correspondance de stratégie.

L’analyse moderne des pièces jointes est prise en charge pour les types de fichiers suivants :

- Microsoft Word (.docx)
- Microsoft Excel (.xlsx)
- Microsoft PowerPoint (.pptx)
- Texte (.txt)
- Portable Document Format (.pdf)

Le texte extrait pour les pièces jointes modernes est inclus dans le message associé dans le tableau de bord Des alertes **en attente** pour une stratégie. Le texte extrait d’une pièce jointe est nommé comme nom de fichier pièce jointe (et extension de format) et l’extension .txt. Par exemple, le texte extrait d’une pièce jointe nommée *ContosoBusinessPlan.docx* apparaît comme *ContosoBusinessPlan.docx.txt* dans le tableau de bord Des alertes **en attente** pour une stratégie.

Sélectionnez le texte extrait de la pièce jointe pour afficher les détails dans les affichages *Source* et *Texte brut* . Après examen, vous pouvez résoudre ou prendre des mesures sur le texte de la pièce jointe à l’aide des contrôles de barre de commandes. Vous avez également la possibilité de télécharger la pièce jointe pour révision en dehors du processus de révision de conformité des communications.

Utilisez les configurations de gestion de groupe suivantes pour superviser les conversations utilisateur individuelles et les communications de canal dans Teams :

- **Pour les communications de conversation Teams :** Affectez des utilisateurs individuels ou attribuez un [groupe de distribution](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) à la stratégie de conformité des communications. Ce paramètre s'applique aux relations d'utilisateur/chat en tête à tête ou à plusieurs.
- **Pour les communications de canal Teams :** Affectez chaque canal Microsoft Teams ou groupe Microsoft 365 que vous souhaitez analyser qui contient un utilisateur spécifique à la stratégie de conformité des communications. Si vous ajoutez le même utilisateur à d’autres canaux Microsoft Teams ou à des groupes Microsoft 365, veillez à ajouter ces nouveaux canaux et groupes à la stratégie de conformité des communications. Si un membre du canal est un utilisateur supervisé au sein d’une stratégie et que la direction *entrante* est configurée dans une stratégie, tous les messages envoyés dans le canal sont sujets à révision et les correspondances de stratégie potentielles (même pour les utilisateurs du canal qui ne sont pas explicitement supervisés). Par exemple, l’utilisateur A est le propriétaire ou un membre d’un canal. L’utilisateur B et l’utilisateur C sont membres du même canal et utilisent la langue correspondant à la stratégie de contenu inappropriée qui supervise uniquement les correspondances de stratégie de création de l’utilisateur A. L’utilisateur B et l’utilisateur C créent des correspondances pour les conversations au sein du canal, même s’ils ne sont pas directement supervisés dans la stratégie de contenu inappropriée. Les conversations teams entre l’utilisateur B et l’utilisateur C qui se trouvent en dehors du canal qui inclut l’utilisateur A ne seraient pas soumises à la stratégie de contenu inappropriée qui inclut l’utilisateur A. Pour exclure les membres du canal de la supervision lorsque d’autres membres du canal sont explicitement supervisés, désactivez le paramètre de direction de communication *entrante* dans la stratégie de conformité des communications applicable.
- **Pour les communications de conversation Teams avec des environnements de messagerie hybrides** : la conformité des communications peut détecter les messages de conversation pour les utilisateurs des organisations disposant d’un déploiement local Exchange ou d’un fournisseur de messagerie externe qui ont activé Microsoft Teams. Vous devez créer un groupe de distribution pour les utilisateurs disposant de boîtes aux lettres locales ou externes à surveiller. Lors de la création d’une stratégie de conformité des communications, vous affectez ce groupe de distribution comme sélection **d’utilisateurs et de groupes supervisés** dans l’Assistant Stratégie. Pour plus d’informations sur les exigences et les limitations relatives à l’activation du stockage cloud et de la prise en charge teams pour les utilisateurs locaux, consultez [Rechercher des données de conversation Teams pour les utilisateurs locaux](search-cloud-based-mailboxes-for-on-premises-users.md).

## <a name="exchange-email"></a>E-mails Exchange

Les boîtes aux lettres hébergées sur Exchange Online dans le cadre de votre abonnement Microsoft 365 ou Office 365 sont toutes éligibles à l’analyse des messages. Le traitement des messages électroniques exchange et des pièces jointes correspondant aux conditions de stratégie de conformité des communications peut prendre environ 24 heures. Les types de pièces jointes prises en charge pour la conformité des communications sont les mêmes que les [types de fichiers pris en charge pour les inspections du contenu des règles de flux de messagerie Exchange](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

## <a name="yammer"></a>Yammer

Les messages privés et les conversations publiques et les pièces jointes associées dans les communautés Yammer peuvent être analysés. Lorsqu’un utilisateur est ajouté à la stratégie de conformité des communications qui inclut Yammer comme canal défini, les communications entre toutes les communautés Yammer dont l’utilisateur est membre sont incluses dans le processus d’analyse. Le traitement des conversations et pièces jointes Yammer correspondant aux conditions de stratégie de conformité des communications peut prendre jusqu’à 24 heures. 

Yammer doit être en [mode natif](/yammer/configure-your-yammer-network/overview-native-mode) pour les stratégies de conformité des communications afin de surveiller les communications et pièces jointes Yammer. En mode natif, tous les utilisateurs de Yammer se trouvent dans Azure Active Directory (AAD), tous les groupes sont des Groupes Office 365 et tous les fichiers sont stockés dans SharePoint Online.

## <a name="third-party-sources"></a>Sources tierces

Vous pouvez analyser les communications à la recherche de données importées dans des boîtes aux lettres de votre organisation Microsoft 365 à partir de sources tierces comme [Instant Bloomberg](archive-instant-bloomberg-data.md), [Slack](archive-slack-data.md), [Zoom](archive-zoommeetings-data.md), SMS et bien d’autres. Pour obtenir la liste complète des connecteurs pris en charge dans la conformité des communications, consultez [Archiver des données tierces](archiving-third-party-data.md).

Vous devez configurer un connecteur tiers pour votre organisation Microsoft 365 avant de pouvoir affecter le connecteur à une stratégie de conformité des communications. La section **Sources tierces** de l’Assistant Stratégie de conformité des communications affiche uniquement les connecteurs tiers actuellement configurés.
