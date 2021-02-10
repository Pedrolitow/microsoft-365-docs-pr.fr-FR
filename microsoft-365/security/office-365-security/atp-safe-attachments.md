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
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 6e13311e-92ae-495e-a619-56d770199170
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur la fonctionnalité pièces jointes sécurisées dans Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5e85695a6d0fba221f3c614ec33b3552d37153e2
ms.sourcegitcommit: 3dc795ea862b180484f76b3eb5d046e74041252b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2021
ms.locfileid: "50175846"
---
# <a name="safe-attachments-in-microsoft-defender-for-office-365"></a>Pièces jointes sécurisées dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 plan 1 et plan 2](https://go.microsoft.com/fwlink/?linkid=2148715)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Les pièces jointes sécurisées dans Microsoft Defender pour [Office 365](office-365-atp.md) fournissent une couche supplémentaire de protection pour les pièces jointes de courrier électronique qui ont déjà été analysées par la protection anti-programme malveillant dans [Exchange Online Protection (EOP).](anti-malware-protection.md) Plus précisément, les pièces jointes sécurisées utilisent un environnement virtuel pour vérifier les pièces jointes dans les messages électroniques avant qu’elles ne soit remis aux destinataires (processus appelé _détonation)._

La protection des pièces jointes sécurisées pour les messages électroniques est contrôlée par les stratégies de pièces jointes sécurisées. Il n’existe aucune stratégie de pièces jointes sécurisées par défaut, donc pour obtenir la protection des pièces jointes sécurisées, vous devez créer une ou plusieurs stratégies de **pièces jointes sécurisées.** Pour obtenir des instructions, voir Configurer des stratégies de pièces [jointes sécurisées dans Defender pour Office 365.](set-up-atp-safe-attachments-policies.md)

Le tableau suivant décrit les scénarios de pièces jointes sécurisées dans les organisations Microsoft 365 et Office 365 qui incluent Microsoft Defender pour Office 365 (en d’autres termes, l’absence de licence n’est jamais un problème dans les exemples).

****

|Scénario|Résultat|
|---|---|
|Aucune stratégie de pièces jointes sécurisées n’est configurée pour l’organisation Microsoft 365 E5 de Pat.|Pat n’est pas protégé par les pièces jointes sécurisées. <p> Un administrateur doit créer au moins une stratégie de pièces jointes sécurisées pour que la protection des pièces jointes sécurisées soit active. En outre, les conditions de la stratégie doivent inclure Pat si Pat doit être protégé par des pièces jointes sécurisées.|
|L’organisation de Lee dispose d’une stratégie de pièces jointes sécurisées qui s’applique uniquement aux employés du service financier. Lee est membre du service des ventes.|Lee n’est pas protégé par les pièces jointes sécurisées. <p> Les employés du service financier sont protégés par des pièces jointes sécurisées, mais pas les employés des ventes (et d’autres employés).|
|Hier, un administrateur de l’organisation de Jean a créé une stratégie de pièces jointes sécurisées qui s’applique à tous les employés. Plus tôt dans la journée, Jean a reçu un message électronique qui inclut une pièce jointe.|Jean est protégé par des pièces jointes sécurisées. <p> En règle générale, l’application d’une nouvelle stratégie prend environ 30 minutes.|
|L’organisation de Chris a des stratégies de pièces jointes sécurisées de longue date pour tous les membres de l’organisation. Chris reçoit un e-mail qui a une pièce jointe, puis le envoie à des destinataires externes.|Chis est protégé par des pièces jointes sécurisées. <p> Si les destinataires externes ont également des stratégies de pièces jointes sécurisées dans leur organisation, les messages transmis sont soumis à ces stratégies.|
|

L’analyse des pièces jointes sécurisées a lieu dans la même région que vos données Microsoft 365. Pour plus d’informations sur la géographie du centre de données, voir [Où se trouvent vos données ?](https://products.office.com/where-is-your-data-located?geo=All)

> [!NOTE]
> Les fonctionnalités suivantes se trouvent dans les paramètres globaux des stratégies de pièces jointes sécurisées dans le Centre de sécurité & conformité, mais ces paramètres sont activés ou désactivés globalement et ne nécessitent pas de stratégies de pièces jointes sécurisées :
>
> - [Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams.](atp-for-spo-odb-and-teams.md)
>
> - [Documents sécurisés dans Microsoft 365 E5](safe-docs.md)

## <a name="safe-attachments-policy-settings"></a>Paramètres de stratégie de pièces jointes sécurisées

Cette section décrit les paramètres des stratégies de pièces jointes sécurisées :

- **Réponse aux programmes malveillants inconnus** pour les pièces jointes sécurisées : ce paramètre contrôle l’action d’analyse des programmes malveillants de pièces jointes sécurisées dans les messages électroniques. Les options disponibles sont décrites dans le tableau suivant :

  ****

  |Option|Effet|À utiliser lorsque vous souhaitez :|
  |---|---|---|
  |**Off**|Les pièces jointes ne sont pas analysées pour les programmes malveillants par les pièces jointes sécurisées. Les messages sont toujours analysés à la recherche de programmes malveillants par [la protection anti-programme malveillant dans EOP.](anti-malware-protection.md)|Désactiver l’analyse pour les destinataires sélectionnés. <p> Éviter les retards inutiles dans le routage du courrier interne. <p> **Cette option n’est pas recommandée pour la plupart des utilisateurs. Vous ne devez utiliser cette option que pour désactiver l’analyse des pièces jointes fiables pour les destinataires qui reçoivent uniquement des messages d’expéditeurs fiables.**|
  |**Moniteur**|Fournit des messages avec pièces jointes, puis suit ce qui se produit avec les programmes malveillants détectés. <p> La remise des messages sûrs peut être retardée en raison de l’analyse des pièces jointes sécurisées.|Découvrez où les programmes malveillants détectés sont détectés dans votre organisation.|
  |**Bloquer**|Empêche la livraison des messages avec des pièces jointes de programmes malveillants détectés. <p> Les messages sont [mis en quarantaine](manage-quarantined-messages-and-files.md) lorsque seuls les administrateurs (et non les utilisateurs finaux) peuvent examiner, libérer ou supprimer les messages. <p> Bloque automatiquement les instances futures des messages et pièces jointes. <p> La remise des messages sûrs peut être retardée en raison de l’analyse des pièces jointes sécurisées.|Protège votre organisation contre les attaques répétées à l’aide des mêmes pièces jointes de programmes malveillants. <p> Il s’agit de la valeur par défaut et de la valeur recommandée dans les stratégies de sécurité standard [et](preset-security-policies.md)stricte.|
  |**Replace**|Supprime les pièces jointes de programmes malveillants détectés. <p> Informe les destinataires que les pièces jointes ont été supprimées. <p>  Les messages sont [mis en quarantaine](manage-quarantined-messages-and-files.md) lorsque seuls les administrateurs (et non les utilisateurs finaux) peuvent examiner, libérer ou supprimer les messages. <p> La remise des messages sûrs peut être retardée en raison de l’analyse des pièces jointes sécurisées.|Augmenter la visibilité pour les destinataires que les pièces jointes ont été supprimées en raison de programmes malveillants détectés.|
  |**Remise dynamique**|Remettre les messages immédiatement, mais remplace les pièces jointes par des espaces réservé jusqu’à ce que l’analyse des pièces jointes sécurisées soit terminée. <p> Pour plus d’informations, voir la section Remise dynamique dans les [stratégies de pièces jointes sécurisées](#dynamic-delivery-in-safe-attachments-policies) plus loin dans cet article.|Évitez les retards de messages tout en protégeant les destinataires contre les fichiers malveillants. <p> Permettre aux destinataires d’afficher un aperçu des pièces jointes en mode sans échec pendant l’analyse.|
  |

- Rediriger la pièce jointe lors de la détection : activez la **redirection** et envoyez la pièce jointe à l’adresse de messagerie suivante : Pour **bloquer,** surveiller ou remplacer **des** actions, envoyez des messages contenant des pièces jointes contenant des programmes malveillants à l’adresse de messagerie interne ou externe spécifiée pour analyse et examen.

  La recommandation pour les paramètres de stratégie Standard et Strict consiste à activer la redirection. Pour plus d’informations, [voir Paramètres des pièces jointes sécurisées.](recommended-settings-for-eop-and-office365-atp.md#safe-attachments-settings)

- Appliquez la sélection ci-dessus si l’analyse des programmes **malveillants** pour les pièces jointes arrive à arriver ou si une erreur se produit : l’action spécifiée par la réponse de programmes malveillants inconnus de pièces **jointes sécurisées** est appliquée aux messages même lorsque l’analyse des pièces jointes sécurisées ne peut pas se terminer. Sélectionnez toujours cette option si vous sélectionnez **Activer la redirection.** Dans le cas contraire, les messages peuvent être perdus.

- **Filtres de** destinataires : vous devez spécifier les conditions de destinataire et les exceptions qui déterminent à qui s’applique la stratégie. Vous pouvez utiliser ces propriétés pour les conditions et les exceptions :

  - **Le destinataire est**
  - **Le domaine du destinataire est**
  - **Le destinataire est membre de**

  Vous ne pouvez utiliser une condition ou une exception qu'une seule fois, mais la condition ou l'exception peut contenir plusieurs valeurs. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

- **Priorité**: si vous créez plusieurs stratégies, vous pouvez spécifier l’ordre dans le cas où elles sont appliquées. Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

  Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

### <a name="dynamic-delivery-in-safe-attachments-policies"></a>Remise dynamique dans les stratégies de pièces jointes sécurisées

> [!NOTE]
> La remise dynamique fonctionne uniquement pour les boîtes aux lettres Exchange Online.

L’action de remise dynamique dans les stratégies de pièces jointes sécurisées vise à éliminer les retards de remise des messages électroniques qui peuvent être causés par l’analyse des pièces jointes sécurisées. Le corps du message électronique est remis au destinataire avec un espace réservé pour chaque pièce jointe. L’espace réservé reste jusqu’à ce que la pièce jointe soit sûre, puis la pièce jointe peut être ouverte ou téléchargée.

Si une pièce jointe est malveillante, le message est mis en quarantaine. Seuls les administrateurs (et non les utilisateurs finaux) peuvent examiner, libérer ou supprimer des messages mis en quarantaine par l’analyse des pièces jointes sécurisées. Pour plus d’informations, voir Gérer les messages et fichiers mis en [quarantaine en tant qu’administrateur.](manage-quarantined-messages-and-files.md)

La plupart des fichiers PDF et des documents Office peuvent être aperçus en mode sans échec lorsque l’analyse des pièces jointes sécurisées est en cours. Si une pièce jointe n’est pas compatible avec l’aperçu de remise dynamique, les destinataires voient un espace réservé pour la pièce jointe jusqu’à ce que l’analyse des pièces jointes sécurisées soit terminée.

Si vous utilisez un appareil mobile et que les FDF ne sont pas rendus dans l’aperçu de remise dynamique sur votre appareil mobile, essayez d’ouvrir le message dans Outlook sur le web (anciennement Outlook Web App) à l’aide de votre navigateur mobile.

Voici quelques considérations pour la remise dynamique et les messages transmis :

- Si le destinataire transmis est protégé par une stratégie de pièces jointes sécurisées qui utilise l’option De remise dynamique, le destinataire voit l’espace réservé, avec la possibilité d’afficher un aperçu des fichiers compatibles.

- Si le destinataire transmis n’est pas protégé par une stratégie de pièces jointes sécurisées, le message et les pièces jointes sont remis sans analyse des pièces jointes ou espaces de pièces jointes.

Dans certains cas, la remise dynamique ne peut pas remplacer les pièces jointes dans les messages. Ces différents cas de figure sont présentés ci-dessous :

- Messages dans les dossiers publics.

- Messages acheminés vers la boîte aux lettres d’un utilisateur à l’aide de règles personnalisées.

- Messages déplacés (automatiquement ou manuellement) des boîtes aux lettres cloud vers d’autres emplacements, y compris les dossiers d’archivage.

- Messages supprimés.

- Le dossier de recherche de boîte aux lettres de l’utilisateur est dans un état d’erreur.

- Organisations Exchange Online où le Lanceur est activé. Pour résoudre ce problème, [voir KB4014438](https://support.microsoft.com/help/4014438).

- [S/MIME)](s-mime-for-message-signing-and-encryption.md) messages chiffrés.

- Vous avez configuré l’action de remise dynamique dans une stratégie de pièces jointes sécurisées, mais le destinataire ne prend pas en charge la remise dynamique (par exemple, le destinataire est une boîte aux lettres dans une organisation Exchange sur site). Toutefois, les liens sécurisés dans Microsoft Defender pour [Office 365](set-up-atp-safe-links-policies.md) sont en mesure d’analyser les pièces jointes de fichiers Office qui contiennent des URL (selon la configuration des [paramètres](configure-global-settings-for-safe-links.md) globaux des liens sécurisés).

## <a name="submitting-files-for-malware-analysis"></a>Envoi de fichiers pour l’analyse des programmes malveillants

- Si vous recevez un fichier que vous souhaitez envoyer à Microsoft pour analyse, consultez Soumettre des programmes malveillants et non malveillants [à Microsoft pour analyse.](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)

- Si vous recevez un message électronique (avec ou sans pièce jointe) que vous souhaitez envoyer à Microsoft pour analyse, reportez-vous aux messages et fichiers de [rapport à Microsoft.](report-junk-email-messages-to-microsoft.md)
