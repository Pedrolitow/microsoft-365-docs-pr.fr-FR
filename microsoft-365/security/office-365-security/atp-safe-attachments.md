---
title: Pièces jointes sûres
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 6e13311e-92ae-495e-a619-56d770199170
ms.collection:
- M365-security-compliance
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur la fonctionnalité de pièces jointes fiables dans Office 365 Advanced Threat Protection (ATP).
ms.openlocfilehash: 6ff356f34f3e44752b5ad7f5fa433a8c72cd5083
ms.sourcegitcommit: 04c4252457d9b976d31f53e0ba404e8f5b80d527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "48326530"
---
# <a name="safe-attachments-in-office-365-atp"></a>Pièces jointes fiables dans Office 365 ATP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Les pièces jointes fiables dans [Office 365 protection avancée contre les menaces (ATP)](office-365-atp.md) fournissent une couche supplémentaire de protection pour les pièces jointes qui ont déjà été analysées par la protection contre les [programmes malveillants dans Exchange Online Protection (EoP)](anti-malware-protection.md). En particulier, les pièces jointes fiables utilisent un environnement virtuel pour vérifier les pièces jointes des messages électroniques avant leur remise aux destinataires (processus appelé _détonation_).

Protection des pièces jointes fiables pour les messages électroniques est contrôlée par les stratégies de pièces jointes fiables. Il n’existe pas de stratégie de pièces jointes approuvées par défaut, **pour obtenir la protection des pièces jointes fiables, vous devez créer une ou plusieurs stratégies de pièces jointes fiables**. Pour obtenir des instructions, voir [configurer des stratégies de pièces jointes fiables dans la protection](set-up-atp-safe-attachments-policies.md)avancée contre les menaces.

Le tableau suivant décrit les scénarios de pièces jointes fiables dans les organisations Microsoft 365 et Office 365 qui incluent ATP (en d’autres termes, le manque de licence n’est jamais un problème dans les exemples).

****

|Scénario|Résultat|
|---|---|
|Aucune stratégie de pièces jointes approuvées n’est configurée pour l’organisation Microsoft 365 E5 de Pat.|Pat n’est pas protégé par les pièces jointes fiables. <br/><br/> Un administrateur doit créer au moins une stratégie de pièces jointes approuvées pour que la protection des pièces jointes soit active. Par ailleurs, les conditions de la stratégie doivent inclure Pat si Pat doit être protégé par des pièces jointes fiables.|
|L’organisation de Lee a une stratégie de pièces jointes fiables qui s’applique uniquement aux employés financiers. Lee est membre du service des ventes.|Lee n’est pas protégé par les pièces jointes fiables. <br/><br/> Les employés du service financier sont protégés par les pièces jointes fiables, mais pas pour les vendeurs (et les autres employés).|
|Hier, un administrateur de Jean a créé une stratégie de pièces jointes fiables qui s’applique à tous les employés. Plus tôt aujourd’hui, Jean a reçu un message électronique contenant une pièce jointe.|Jean est protégé par des pièces jointes fiables. <br/><br/> En règle générale, il faut environ 30 minutes pour qu’une nouvelle stratégie prenne effet.|
|L’organisation de Chris dispose de stratégies de pièces jointes fiables de longue date pour tous les membres de l’organisation. Chris reçoit un courrier électronique comportant une pièce jointe, puis transfère le message à des destinataires externes.|CHIS est protégé par des pièces jointes fiables. <br/><br/> Si les destinataires externes ont également des stratégies de pièces jointes approuvées dans leur organisation, les messages transférés sont soumis à ces stratégies.|
|

L’analyse des pièces jointes fiables a lieu dans la région où se trouvent vos données Microsoft 365. Pour plus d’informations sur la géographie des centres de données, voir [où se trouvent vos données ?](https://products.office.com/where-is-your-data-located?geo=All)

> [!NOTE]
> Les fonctionnalités suivantes sont situées dans les paramètres globaux des stratégies de pièces jointes approuvées dans le centre de sécurité & conformité, mais ces paramètres sont activés ou désactivés globalement et ne nécessitent aucune stratégie de pièces jointes fiables :
>
> - La protection avancée contre [les menaces pour SharePoint, OneDrive et Microsoft teams](atp-for-spo-odb-and-teams.md).
>
> - [Documents approuvés dans Microsoft 365 E5](safe-docs.md)

## <a name="safe-attachments-policy-settings"></a>Paramètres de stratégie de pièces jointes fiables

Cette section décrit les paramètres des stratégies de pièces jointes approuvées :

- **Pièces jointes fiables réponse aux programmes malveillants inconnus**: ce paramètre contrôle l’action d’analyse anti-programme malveillant des pièces jointes fiables dans les messages électroniques. Les options disponibles sont décrites dans le tableau suivant :

  ****

  |Option|Effet|À utiliser lorsque vous souhaitez :|
  |---|---|---|
  |**Désactivé**|Les pièces jointes ne sont pas analysées par des pièces jointes fiables. Les messages sont toujours analysés pour la protection contre les programmes malveillants [dans EOP](anti-malware-protection.md).|Désactivez l’analyse pour les destinataires sélectionnés. <br/><br/> Éviter les retards inutiles dans le routage du courrier interne. <br/><br/> **Cette option n’est pas recommandée pour la plupart des utilisateurs. Cette option ne doit être utilisée que pour désactiver l’analyse des pièces jointes fiables pour les destinataires qui reçoivent uniquement des messages provenant d’expéditeurs approuvés.**|
  |**Moniteur**|Remet les messages avec des pièces jointes, puis effectue le suivi de ce qui se produit avec des programmes malveillants <br/><br/> La remise de messages fiables peut être retardée en raison de l’analyse des pièces jointes approuvées.|Voir WHERE détection des programmes malveillants dans votre organisation.|
  |**Bloquer**|Empêche la remise des messages dont les pièces jointes aux programmes malveillants sont détectées. <br/><br/> Les messages sont [mis en quarantaine](manage-quarantined-messages-and-files.md) lorsque seuls les administrateurs (pas les utilisateurs finaux) peuvent consulter, publier ou supprimer les messages. <br/><br/> Bloque automatiquement les instances futures des messages et des pièces jointes. <br/><br/> La remise de messages fiables peut être retardée en raison de l’analyse des pièces jointes approuvées.|Protège votre organisation contre les attaques répétées à l’aide des mêmes pièces jointes. <br/><br/> Il s’agit de la valeur par défaut et de la valeur recommandée dans [stratégies de sécurité prédéfinies](preset-security-policies.md)standard et strict.|
  |**Replace**|Supprime les pièces jointes malveillantes détectées. <br/><br/> Avertir les destinataires que des pièces jointes ont été supprimées. <br/><br/>  Les messages sont [mis en quarantaine](manage-quarantined-messages-and-files.md) lorsque seuls les administrateurs (pas les utilisateurs finaux) peuvent consulter, publier ou supprimer les messages. <br/><br/> La remise de messages fiables peut être retardée en raison de l’analyse des pièces jointes approuvées.|Augmenter la visibilité aux destinataires pour lesquels les pièces jointes ont été supprimées en raison d’un programme malveillant détecté.|
  |**Remise dynamique**|Remet les messages immédiatement, mais remplace les pièces jointes par des espaces réservés jusqu’à la fin de l’analyse des pièces jointes fiables. <br/><br/> Pour plus d’informations, consultez la section relative [à la remise dynamique des stratégies de pièces jointes approuvées](#dynamic-delivery-in-safe-attachments-policies) plus loin dans cette rubrique.|Éviter les retards de message tout en protégeant les destinataires des fichiers malveillants <br/> <br/> Autoriser les destinataires à prévisualiser les pièces jointes en mode sans échec lors de l’analyse|
  |

- **Rediriger la pièce jointe sur la détection : activez la redirection** et **envoyez la pièce jointe à l’adresse de messagerie suivante**: pour les actions **bloquer**, **surveiller**ou **remplacer** , envoyez des messages contenant des pièces jointes de programmes malveillants à l’adresse de messagerie interne ou externe spécifiée à des fins d’analyse et d’enquête.

  La recommandation pour les paramètres de stratégie standard et strict est d’activer la redirection. Pour plus d’informations, consultez la rubrique [paramètres de pièces jointes fiables](recommended-settings-for-eop-and-office365-atp.md#safe-attachments-settings).

- **Appliquer la sélection ci-dessus si l’analyse anti-programme malveillant pour les pièces jointes expire ou si une erreur se produit**: l’action spécifiée par les **pièces jointes approuvées une réponse inconnue aux programmes malveillants** est prise sur les messages, même lorsque l’analyse Sélectionnez toujours cette option si vous sélectionnez **activer la redirection**. Sinon, les messages peuvent être perdus.

- **Filtres de destinataires**: vous devez spécifier les conditions de destinataire et les exceptions qui déterminent la personne à laquelle la stratégie s’applique. Vous pouvez utiliser ces propriétés pour les conditions et les exceptions :

  - **Le destinataire est**
  - **Le domaine du destinataire est**
  - **Le destinataire est membre de**

  Vous ne pouvez utiliser une condition ou une exception qu'une seule fois, mais la condition ou l'exception peut contenir plusieurs valeurs. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

- **Priority**: Si vous créez plusieurs stratégies, vous pouvez spécifier l’ordre dans lequel elles sont appliquées. Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

  Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

### <a name="dynamic-delivery-in-safe-attachments-policies"></a>Stratégies de remise dynamique dans les pièces jointes fiables

> [!NOTE]
> La remise dynamique fonctionne uniquement pour les boîtes aux lettres Exchange Online.

L’action de remise dynamique dans les stratégies de pièces jointes approuvées cherche à éliminer les retards de remise du courrier qui peuvent être causés par l’analyse des pièces jointes fiables. Le corps du message électronique est remis au destinataire avec un espace réservé pour chaque pièce jointe. L’espace réservé reste jusqu’à ce que la pièce jointe soit fiable, puis la pièce jointe devient disponible pour l’ouverture ou le téléchargement.

Si une pièce jointe est indésirable, le message est mis en quarantaine. Seuls les administrateurs (pas les utilisateurs finaux) peuvent consulter, publier ou supprimer des messages mis en quarantaine par l’analyse des pièces jointes fiables. Pour plus d’informations, consultez la rubrique [gestion des messages et des fichiers mis en quarantaine en tant qu’administrateur](manage-quarantined-messages-and-files.md).

La plupart des documents PDF et Office peuvent être prévisualisés en mode sans échec pendant l’analyse des pièces jointes fiables. Si une pièce jointe n’est pas compatible avec le prévisualisation de remise dynamique, les destinataires verront un espace réservé pour la pièce jointe jusqu’à ce que l’analyse des pièces jointes fiables soit terminée.

Si vous utilisez un appareil mobile et que les fichiers PDF ne sont pas rendus dans l’aperçu de remise dynamique sur votre appareil mobile, essayez d’ouvrir le message dans Outlook sur le Web (anciennement appelé Outlook Web App) à l’aide de votre navigateur mobile.

Voici quelques éléments à prendre en compte pour la remise et les messages transférés dynamiquement :

- Si le destinataire transféré est protégé par une stratégie de pièces jointes fiables qui utilise l’option de remise dynamique, le destinataire voit alors l’espace réservé, avec la possibilité de prévisualiser les fichiers compatibles.

- Si le destinataire transféré n’est pas protégé par une stratégie de pièces jointes fiables, le message et les pièces jointes seront remis sans les espaces réservés de pièces jointes ou d’analyse de pièces jointes fiables.

## <a name="scenarios-where-safe-attachments-doesnt-scan-messages"></a>Scénarios dans lesquels les pièces jointes fiables n’analysent pas les messages

Il existe des scénarios dans lesquels les pièces jointes fiables ne peuvent pas analyser les messages :

- Messages dans les dossiers publics.

- Les messages qui sont routés vers et vers la boîte aux lettres d’un utilisateur à l’aide de règles personnalisées.

- Messages déplacés (automatiquement ou manuellement) en dehors des boîtes aux lettres Cloud vers d’autres emplacements, y compris les dossiers d’archivage.

- Messages supprimés.

- Le dossier de recherche de boîte aux lettres de l’utilisateur est dans un état d’erreur.

- Organisations Exchange Online où Exclaimer est activé. Pour résoudre ce, consultez [KB4014438](https://support.microsoft.com/help/4014438).

- [S/MIME)](s-mime-for-message-signing-and-encryption.md) messages chiffrés.

- Vous avez configuré l’action de remise dynamique dans une stratégie de pièces jointes fiables, mais le destinataire ne prend pas en charge la remise dynamique (par exemple, le destinataire est une boîte aux lettres dans une organisation Exchange locale). Toutefois, les [liens fiables dans office 365 ATP](set-up-atp-safe-links-policies.md) peuvent analyser les pièces jointes des fichiers Office qui contiennent des URL (en fonction de la configuration des liens fiables).

## <a name="submitting-files-for-malware-analysis"></a>Envoi de fichiers pour l’analyse contre les programmes malveillants

- Si vous recevez un fichier que vous souhaitez envoyer à Microsoft pour analyse, reportez-vous [à soumettre des programmes malveillants et autres programmes malveillants à Microsoft pour analyse](submitting-malware-and-non-malware-to-microsoft-for-analysis.md).

- Si vous recevez un message électronique (avec ou sans pièce jointe) que vous souhaitez envoyer à Microsoft pour analyse, reportez-vous à la rubrique [signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).
