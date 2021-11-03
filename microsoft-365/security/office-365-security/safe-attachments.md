---
title: Pièces jointes fiables
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6e13311e-92ae-495e-a619-56d770199170
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur la Coffre pièces jointes dans Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: efe1b985a7df7e8066533bf3789e38120dd97787
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60668421"
---
# <a name="safe-attachments-in-microsoft-defender-for-office-365"></a>Coffre Pièces jointes dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Coffre Les pièces jointes dans [Microsoft Defender pour Office 365](defender-for-office-365.md) fournissent une couche de protection supplémentaire pour les pièces jointes de courrier électronique qui ont déjà été analysées par la protection anti-programme malveillant dans Exchange Online Protection [(EOP).](anti-malware-protection.md) Plus précisément, Coffre pièces jointes utilise un environnement virtuel pour vérifier les pièces jointes dans les messages électroniques avant qu’elles ne soit remis aux destinataires (processus appelé _détonation)._

La protection des pièces jointes fiables pour les messages électroniques est contrôlée par des stratégies de pièces jointes fiables. Bien qu’il n’existe aucune stratégie de pièces jointes Coffre par défaut, la stratégie de sécurité prédéfinit de **protection** intégrée fournit une protection Coffre pièces jointes à tous les destinataires (utilisateurs qui ne sont pas définis dans les stratégies de pièces jointes Coffre personnalisées). Pour plus d’informations, voir [Stratégies de sécurité prédéfini dans EOP](preset-security-policies.md)et Microsoft Defender pour Office 365 . Vous pouvez également créer des stratégies Coffre pièces jointes qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques. Pour obtenir des instructions, voir [Configurer Coffre pièces jointes dans Microsoft Defender pour Office 365](set-up-safe-attachments-policies.md).

Le tableau suivant décrit les scénarios pour les pièces jointes Coffre dans les organisations Microsoft 365 et Office 365 qui incluent Microsoft Defender pour Office 365 (en d’autres termes, l’absence de licence n’est jamais un problème dans les exemples).

<br>

****

|Scénario|Résultat|
|---|---|
|L’organisation Microsoft 365 E5 pat n’a aucune stratégie Coffre pièces jointes configurée.|Pat est protégé par Coffre pièces jointes en raison de la stratégie de sécurité prédéfinit de **protection** intégrée qui s’applique à tous les destinataires qui ne sont pas définis dans les stratégies Coffre pièces jointes.|
|L’organisation de Lee dispose d’une stratégie Coffre pièces jointes qui s’applique uniquement aux employés du service financier. Lee est membre du service des ventes.|Lee et le reste du service commercial sont protégés par les pièces jointes Coffre en raison de la stratégie de sécurité prédéfinie de **protection** intégrée qui s’applique à tous les destinataires qui ne sont pas définis dans les stratégies de pièces jointes Coffre.|
|Hier, un administrateur de l’organisation de Jean a créé une stratégie Coffre pièces jointes qui s’applique à tous les employés. Plus tôt dans la journée, Jean a reçu un message électronique qui inclut une pièce jointe.|Jean est protégé par Coffre pièces jointes en raison de cette stratégie Coffre pièces jointes personnalisée. <p> En règle générale, l’application d’une nouvelle stratégie prend environ 30 minutes.|
|L’organisation de Chris a des stratégies Coffre pièces jointes de longue date pour tous les membres de l’organisation. Chris reçoit un message électronique qui a une pièce jointe, puis le envoie à des destinataires externes.|Chis est protégé par des pièces jointes Coffre’un autre. <p> Si les destinataires externes d’Microsoft 365 organisation, les messages transmis sont également protégés par Coffre pièces jointes.|
|

L’analyse des pièces jointes fiables a lieu dans la même région que l’emplacement de vos données Microsoft 365. Pour plus d’informations sur la géographie du centre de données, voir [Où se trouvent vos données ?](https://products.office.com/where-is-your-data-located?geo=All)

> [!NOTE]
> Les fonctionnalités suivantes se trouvent dans les paramètres globaux des stratégies Coffre pièces jointes dans le portail Microsoft 365 Defender web. Toutefois, ces paramètres sont activés ou désactivés globalement et ne nécessitent pas Coffre stratégies de pièces jointes :
>
> - [Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md).
> - [Documents sécurisés dans Microsoft 365 E5](safe-docs.md)

## <a name="safe-attachments-policy-settings"></a>Coffre Paramètres de stratégie de pièces jointes

Cette section décrit les paramètres des stratégies Coffre pièces jointes :

- **Coffre de programmes malveillants inconnus attachments**: ce paramètre contrôle l’action d’analyse des programmes malveillants Coffre pièces jointes dans les messages électroniques. Les options disponibles sont décrites dans le tableau suivant :

  <br>

  ****

  |Option|Effet|À utiliser lorsque vous souhaitez :|
  |---|---|---|
  |**Désactivé**|Les pièces jointes ne sont pas analysées à la recherche de programmes malveillants Coffre pièces jointes. Les messages sont toujours analysés à la recherche de programmes malveillants par [la protection anti-programme malveillant dans EOP.](anti-malware-protection.md)|Désactiver l’analyse des destinataires sélectionnés. <p> Éviter les retards inutiles dans le routage du courrier interne. <p> **Cette option n’est pas recommandée pour la plupart des utilisateurs. Vous devez uniquement utiliser cette option pour désactiver l’analyse Coffre pièces jointes pour les destinataires qui reçoivent uniquement des messages d’expéditeurs fiables.**|
  |**Moniteur**|Fournit les messages avec pièces jointes, puis suit ce qui se produit avec les programmes malveillants détectés. <p> La remise des messages sûrs peut être retardée en raison Coffre’analyse des pièces jointes.|Découvrez où les programmes malveillants détectés sont détectés dans votre organisation.|
  |**Bloquer**|Empêche la livraison des messages avec des pièces jointes de programmes malveillants détectés. <p> Les messages sont mis en quarantaine. Par défaut, seuls les administrateurs (et non les utilisateurs) peuvent examiner, libérer ou supprimer les messages.<sup>\*</sup> <p> Bloque automatiquement les instances futures des messages et pièces jointes. <p> La remise des messages sûrs peut être retardée en raison Coffre’analyse des pièces jointes.|Protège votre organisation contre les attaques répétées à l’aide des mêmes pièces jointes de programmes malveillants. <p> Il s’agit de la valeur par défaut et de la valeur recommandée dans les stratégies de sécurité standard [et](preset-security-policies.md)stricte.|
  |**Replace**|Supprime les pièces jointes de programmes malveillants détectés. <p> Informe les destinataires que les pièces jointes ont été supprimées. <p>  Les messages qui contiennent des pièces jointes malveillantes sont mis en quarantaine. Par défaut, seuls les administrateurs (et non les utilisateurs) peuvent examiner, libérer ou supprimer les messages.<sup>\*</sup> <p> La remise des messages sûrs peut être retardée en raison Coffre’analyse des pièces jointes.|Augmenter la visibilité pour les destinataires que les pièces jointes ont été supprimées en raison de programmes malveillants détectés.|
  |**Remise dynamique**|Remettre les messages immédiatement, mais remplace les pièces jointes par des espaces réservé jusqu’Coffre’analyse des pièces jointes est terminée. <p> Les messages qui contiennent des pièces jointes malveillantes sont mis en quarantaine. Par défaut, seuls les administrateurs (et non les utilisateurs) peuvent examiner, libérer ou supprimer les messages.<sup>\*</sup> <p> Pour plus d’informations, voir la section Remise dynamique [dans Coffre pièces jointes](#dynamic-delivery-in-safe-attachments-policies) plus loin dans cet article.|Évitez les retards de messages tout en protégeant les destinataires contre les fichiers malveillants.|
  |

  <sup>\*</sup>Les administrateurs peuvent  créer et affecter des stratégies de mise en quarantaine Coffre stratégies de pièces jointes qui définissent ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

- Rediriger la pièce jointe lors de la détection : activez la **redirection** et envoyez la pièce jointe à l’adresse de messagerie suivante : Pour **bloquer,** surveiller ou remplacer **des** actions, envoyez des messages contenant des pièces jointes contenant des programmes malveillants à l’adresse de messagerie interne ou externe spécifiée pour analyse et examen.

  La recommandation pour les paramètres de stratégie Standard et Strict consiste à activer la redirection. Pour plus d’informations, [voir Coffre Paramètres des pièces jointes.](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)

- Appliquez la sélection ci-dessus si l’analyse des programmes malveillants pour les pièces **jointes** arrive à arriver ou si une erreur se produit : l’action spécifiée par Coffre La réponse anti-programme malveillant **attachments** inconnue est appliquée aux messages même lorsque l’analyse des pièces jointes Coffre ne peut pas se terminer. Sélectionnez toujours cette option si vous sélectionnez **Activer la redirection.** Dans le cas contraire, les messages peuvent être perdus.

- **Filtres de** destinataires : vous devez spécifier les conditions de destinataire et les exceptions qui déterminent à qui s’applique la stratégie. Vous pouvez utiliser ces propriétés pour les conditions et les exceptions :
  - **Le destinataire est**
  - **Le domaine du destinataire est**
  - **Le destinataire est membre de**

  Vous ne pouvez utiliser une condition ou une exception qu'une seule fois, mais la condition ou l'exception peut contenir plusieurs valeurs. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

- **Priorité**: si vous créez plusieurs stratégies, vous pouvez spécifier l’ordre dans le cas où elles sont appliquées. Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

  Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

### <a name="dynamic-delivery-in-safe-attachments-policies"></a>Remise dynamique dans les stratégies Coffre pièces jointes

> [!NOTE]
> La remise dynamique fonctionne uniquement pour Exchange Online boîtes aux lettres.

L’action de remise dynamique Coffre stratégies de pièces jointes vise à éliminer les retards de remise des messages électroniques qui peuvent être causés par Coffre’analyse des pièces jointes. Le corps du message électronique est remis au destinataire avec un espace réservé pour chaque pièce jointe. L’espace réservé reste jusqu’à ce que la pièce jointe soit sûre, puis la pièce jointe peut être ouverte ou téléchargée.

Si une pièce jointe est malveillante, le message est mis en quarantaine.

La plupart des fichiers PDF et Office documents peuvent être prévisualiser en mode sans échec pendant Coffre’analyse des pièces jointes est en cours. Si une pièce jointe n’est pas compatible avec l’aperçu de remise dynamique, les destinataires voient un espace réservé pour la pièce jointe jusqu’à ce Coffre’analyse des pièces jointes soit terminée.

Si vous utilisez un appareil mobile et que les FDF ne sont pas rendus dans l’aperçu de remise dynamique sur votre appareil mobile, essayez d’ouvrir le message dans Outlook sur le web (anciennement appelé Outlook Web App) à l’aide de votre navigateur mobile.

Voici quelques considérations pour la remise dynamique et les messages transmis :

- Si le destinataire transmis est protégé par une stratégie de pièces jointes Coffre qui utilise l’option De remise dynamique, le destinataire voit l’espace réservé, avec la possibilité d’afficher un aperçu des fichiers compatibles.
- Si le destinataire transmis n’est pas protégé par une stratégie de pièces jointes Coffre, le message et les pièces jointes sont remis sans l’analyse des pièces jointes Coffre ou les espaces réservé aux pièces jointes.

Dans certains cas, la remise dynamique ne peut pas remplacer les pièces jointes dans les messages. Ces différents cas de figure sont présentés ci-dessous :

- Messages dans les dossiers publics.
- Messages acheminés vers la boîte aux lettres d’un utilisateur à l’aide de règles personnalisées.
- Messages déplacés (automatiquement ou manuellement) des boîtes aux lettres cloud vers d’autres emplacements, y compris les dossiers d’archivage.
- Les règles de boîte de réception déplacent le message hors de la boîte de réception dans un autre dossier.
- Messages supprimés.
- Le dossier de recherche de boîte aux lettres de l’utilisateur est dans un état d’erreur.
- Exchange Online organisations où le Lanceur est activé. Pour résoudre ce problème, voir [KB4014438](https://support.microsoft.com/help/4014438).
- [S/MIME)](/exchange/security-and-compliance/smime-exo/smime-exo) messages chiffrés.
- Vous avez configuré l’action de remise dynamique dans une stratégie de pièces jointes Coffre, mais le destinataire ne prend pas en charge la remise dynamique (par exemple, le destinataire est une boîte aux lettres dans une organisation Exchange local). Toutefois, Coffre Liens dans [Microsoft Defender](set-up-safe-links-policies.md) pour Office 365 est en mesure d’analyser les pièces jointes de fichier Office qui contiennent des URL (selon la configuration des [paramètres](configure-global-settings-for-safe-links.md) globaux des liens Coffre).

## <a name="submitting-files-for-malware-analysis"></a>Envoi de fichiers pour l’analyse des programmes malveillants

- Si vous recevez un fichier que vous souhaitez envoyer à Microsoft pour analyse, consultez Soumettre des programmes malveillants et non malveillants [à Microsoft pour analyse.](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)
- Si vous recevez un message électronique (avec ou sans pièce jointe) que vous souhaitez envoyer à Microsoft pour analyse, reportez-vous aux messages et fichiers de [rapport à Microsoft.](report-junk-email-messages-to-microsoft.md)
