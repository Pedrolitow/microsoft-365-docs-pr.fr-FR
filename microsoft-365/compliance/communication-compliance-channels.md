---
title: Détecter les signaux des canaux à l’aide de la conformité des communications
description: En savoir plus sur la détection des signaux de canal avec la conformité des communications.
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
ms.openlocfilehash: 940454e95a89748c0b4cfa985a624abd66fb840c
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60703462"
---
# <a name="detect-channel-signals-with-communication-compliance"></a>Détecter les signaux des canaux à l’aide de la conformité des communications

Avec les stratégies de conformité des communications, vous pouvez choisir d’analyser les messages dans une ou plusieurs des plateformes de communication suivantes en tant que groupe ou en tant que sources autonomes. Par défaut, les communications capturées sur ces plateformes sont conservées pendant sept ans pour chaque stratégie, même si les utilisateurs quittent votre organisation et que leurs boîtes aux lettres sont supprimées.

## <a name="microsoft-teams"></a>Microsoft Teams

Les communications de conversation dans les canaux publics Microsoft Teams privés et les conversations individuelles peuvent être analysées. Lorsque les utilisateurs sont affectés à une stratégie de conformité des communications dont la couverture Microsoft Teams est sélectionnée, les communications de conversation des utilisateurs sont automatiquement surveillées dans toutes les Microsoft Teams dont les utilisateurs sont membres. Microsoft Teams couverture est automatiquement incluse pour les modèles de stratégie prédéfin définis et est sélectionnée par défaut dans le modèle de stratégie personnalisé. Teams conversations correspondant aux conditions de stratégie de conformité des communications peuvent prendre jusqu’à 48 heures.

Pour les canaux privés et de conversation privée, les stratégies de conformité des communications prisent en charge l’analyse moderne des pièces jointes. Les pièces jointes modernes [](/onedrive/plan-onedrive-enterprise#modern-attachments) sont des fichiers provenant OneDrive sites [SharePoint](/sharepoint/dev/solution-guidance/modern-experience-customizations) qui sont inclus dans Teams messages. Le texte est automatiquement extrait de ces pièces jointes pour un traitement automatisé et des correspondances potentielles avec les conditions de stratégie de conformité des communications actives et les classifieurs. Aucune configuration supplémentaire n’est nécessaire pour la détection et le traitement des pièces jointes modernes. Le texte est extrait uniquement pour les pièces jointes correspondant aux conditions de stratégie. Le texte n’est pas extrait pour les pièces jointes des messages avec des correspondances de stratégie, même si la pièce jointe a également une correspondance de stratégie.

L’analyse moderne des pièces jointes est prise en charge pour les types de fichiers suivants :

- Microsoft Word (.docx)
- Microsoft Excel (.xlsx)
- Microsoft PowerPoint (.pptx)
- Texte (.txt)
- Portable Document Format (.pdf)

Le texte extrait pour les pièces jointes  modernes est inclus avec le message associé dans le tableau de bord Des alertes en attente pour une stratégie. Le texte extrait d’une pièce jointe est nommé comme nom de fichier de pièce jointe (et extension de format) et comme extension .txt pièce jointe. Par exemple, le texte extrait d’une pièce jointe  nommée *ContosoBusinessPlan.docx* apparaît ContosoBusinessPlan.docx.txtdans le tableau de bord Des alertes en attente pour une stratégie.

Sélectionnez le texte extrait de la pièce jointe pour afficher les détails dans les affichages *Source,* *Texte* simple ou *Annoter.* Après avoir passé en revue, vous pouvez résoudre ou agir sur le texte de la pièce jointe à l’aide des contrôles de barre de commandes. Vous avez également la possibilité de télécharger la pièce jointe pour révision en dehors du processus de révision de conformité des communications.

Utilisez les configurations de gestion de groupe suivantes pour superviser les conversations des utilisateurs individuels et les communications de canal dans Teams :

- **Pour les Teams de conversation :** Affecter des utilisateurs individuels ou affecter un [groupe de distribution](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) à la stratégie de conformité des communications. Ce paramètre s'applique aux relations d'utilisateur/chat en tête à tête ou à plusieurs.
- **Pour les communications Teams canal :** Affectez chaque Microsoft Teams ou groupe Microsoft 365 que vous souhaitez analyser qui contient un utilisateur spécifique à la stratégie de conformité des communications. Si vous ajoutez le même utilisateur à d’autres canaux Microsoft Teams ou à des groupes Microsoft 365, veillez à ajouter ces nouveaux canaux et groupes à la stratégie de conformité des communications. Si un membre du canal est un utilisateur supervisé au sein d’une stratégie et que le *sens* du trafic entrant est configuré dans une stratégie, tous les messages envoyés au sein du canal sont soumis à un examen et à des correspondances de stratégie potentielles (même pour les utilisateurs du canal qui ne sont pas explicitement supervisés). Par exemple, l’utilisateur A est le propriétaire ou un membre d’un canal. L’utilisateur B et l’utilisateur C sont membres du même canal et utilisent un langage qui correspond à la stratégie de contenu inappropriée qui supervise uniquement l’utilisateur A. L’utilisateur B et l’utilisateur C créent des correspondances de stratégie pour les conversations au sein du canal, même s’ils ne sont pas directement supervisés dans la stratégie de contenu inappropriée. Teams conversations entre l’utilisateur B et l’utilisateur C qui se trouve en dehors du canal qui inclut l’utilisateur A ne sont pas soumises à la stratégie de contenu inappropriée qui inclut l’utilisateur A. Pour exclure les membres du canal de la surveillance lorsque d’autres membres du canal sont explicitement supervisés, désactiver le paramètre d’orientation des *communications* entrantes dans la stratégie de conformité des communications applicable.
- Pour Teams communications de conversation avec des environnements de messagerie **hybrides**: la conformité des communications peut surveiller les messages de conversation pour les utilisateurs des organisations avec un déploiement local Exchange ou un fournisseur de messagerie externe ayant activé Microsoft Teams. Vous devez créer un groupe de distribution pour les utilisateurs avec des boîtes aux lettres sur site ou externes à surveiller. Lorsque vous créez une stratégie de conformité des  communications, vous affectez ce groupe de distribution en tant que sélection d’utilisateurs et de groupes Supervisés dans l’Assistant Stratégie. Pour plus d’informations sur les exigences et les limitations relatives à l’activation de la prise en charge du stockage en nuage et de la Teams pour les utilisateurs locaux, voir Rechercher des données de conversation Teams pour les [utilisateurs](search-cloud-based-mailboxes-for-on-premises-users.md)locaux.

## <a name="exchange-email"></a>E-mails Exchange

Les boîtes aux lettres hébergées sur Exchange Online dans le cadre de votre abonnement Microsoft 365 ou Office 365 sont toutes éligibles pour l’analyse des messages. Exchange messages électroniques et pièces jointes correspondant aux conditions de stratégie de conformité des communications peuvent prendre jusqu’à 24 heures. Les types de pièces jointes prises en charge pour la conformité des communications sont les mêmes que les [types de fichiers pris en charge pour les inspections du contenu des règles de flux de messagerie Exchange](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

## <a name="yammer"></a>Yammer

Les messages privés et les conversations publiques et les pièces jointes associées dans Yammer peuvent être analysés. Lorsqu’un utilisateur est ajouté à la stratégie de conformité des communications qui inclut Yammer comme canal défini, les communications entre toutes les communautés Yammer dont l’utilisateur est membre sont incluses dans le processus d’analyse. Yammer conversations et pièces jointes correspondant aux conditions de stratégie de conformité des communications peuvent prendre jusqu’à 24 heures. 

Yammer doit être en [mode natif pour](/yammer/configure-your-yammer-network/overview-native-mode) les stratégies de conformité des communications pour surveiller Yammer communications et les pièces jointes. En mode natif, tous les utilisateurs de Yammer se trouvent dans Azure Active Directory (AAD), tous les groupes sont des Groupes Office 365 et tous les fichiers sont stockés dans SharePoint Online.

## <a name="skype-for-business-online"></a>Skype Entreprise Online

Les communications de conversation et les pièces jointes associées dans Skype Entreprise Online peuvent être supervisées. Les conversations Skype Entreprise Online correspondant aux conditions de la stratégie de conformité des communications peuvent prendre jusqu’à 24 heures. Les conversations supervisées sont provenant de [conversations précédentes enregistrées dans Skype Entreprise Online.](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2)  

Utilisez la configuration de gestion de groupe suivante pour superviser les communications de conversation utilisateur dans Skype Entreprise Online :

- **Pour les Skype Entreprise de conversation** en ligne : affectez des utilisateurs individuels ou attribuez un groupe de [distribution](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) à la stratégie de conformité des communications. Ce paramètre s'applique aux relations d'utilisateur/chat en tête à tête ou à plusieurs.

## <a name="third-party-sources"></a>Sources tierces

Vous pouvez analyser les communications pour les données importées dans les boîtes aux lettres de votre organisation Microsoft 365 à partir de sources tierces telles que [Instant Bloomberg,](archive-instant-bloomberg-data.md) [Slack,](archive-slack-data.md) [Zoom,](archive-zoommeetings-data.md)SMS et bien d’autres. Pour obtenir la liste complète des connecteurs pris en charge dans la conformité des communications, voir [Archiver des données tierces.](archiving-third-party-data.md)

Vous devez configurer un connecteur tiers pour votre organisation Microsoft 365 avant de pouvoir affecter le connecteur à une stratégie de conformité des communications. La section **Sources tierces** de l’Assistant Stratégie de conformité des communications affiche uniquement les connecteurs tiers actuellement configurés.
