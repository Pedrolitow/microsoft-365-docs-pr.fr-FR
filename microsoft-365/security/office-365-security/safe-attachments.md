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
description: Les administrateurs peuvent en savoir plus sur la fonctionnalité pièces jointes Coffre dans Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e50904932b95dabdad627a7a3291659c1c4d9584
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115936"
---
# <a name="safe-attachments-in-microsoft-defender-for-office-365"></a>pièces jointes Coffre dans Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Coffre Pièces jointes dans [Microsoft Defender pour Office 365](defender-for-office-365.md) fournit une couche supplémentaire de protection pour les pièces jointes de courrier qui ont déjà été analysées par [la protection anti-programme malveillant dans Exchange Online Protection (EOP).](anti-malware-protection.md) Plus précisément, Coffre pièces jointes utilise un environnement virtuel pour vérifier les pièces jointes dans les messages électroniques avant qu’elles ne soient remises aux destinataires (processus appelé _détonation_).

La protection des pièces jointes fiables pour les messages électroniques est contrôlée par des stratégies de pièces jointes fiables. Bien qu’il n’existe aucune stratégie de Coffre pièces jointes par défaut, la stratégie de sécurité prédéfinie de **protection intégrée** fournit Coffre protection des pièces jointes à tous les destinataires (utilisateurs qui ne sont pas définis dans les stratégies de Coffre pièces jointes personnalisées). Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md). Vous pouvez également créer Coffre stratégies de pièces jointes qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques. Pour obtenir des instructions, consultez [Configurer Coffre stratégies pièces jointes dans Microsoft Defender pour Office 365](set-up-safe-attachments-policies.md).

Le tableau suivant décrit les scénarios de Coffre pièces jointes dans Microsoft 365 et les organisations Office 365 qui incluent des Microsoft Defender pour Office 365 (en d’autres termes, le manque de licences n’est jamais un problème dans les exemples).

|Scénario|Résultat|
|---|---|
|L’organisation Microsoft 365 E5 de Pat n’a pas de stratégie de pièces jointes Coffre configurée.|Pat est protégé par Coffre Pièces jointes en raison de la stratégie de sécurité prédéfinie de **protection intégrée** qui s’applique à tous les destinataires qui ne sont pas définis dans Coffre stratégies pièces jointes.|
|L’organisation de Lee a une stratégie de Coffre Pièces jointes qui s’applique uniquement aux employés financiers. Lee est membre du service des ventes.|Lee et le reste du service des ventes sont protégés par des pièces jointes Coffre en raison de la stratégie de sécurité prédéfinie de **protection intégrée** qui s’applique à tous les destinataires qui ne sont pas définis dans Coffre stratégies pièces jointes.|
|Hier, un administrateur de l’organisation de Jean a créé une stratégie Coffre Pièces jointes qui s’applique à tous les employés. Plus tôt dans la journée, Jean a reçu un e-mail contenant une pièce jointe.|Jean est protégé par Coffre Pièces jointes en raison de cette stratégie de Coffre pièces jointes personnalisée. <br/><br/> En règle générale, l’application d’une nouvelle stratégie prend environ 30 minutes.|
|L’organisation de Chris a des stratégies de pièces jointes Coffre de longue date pour tous les membres de l’organisation. Chris reçoit un e-mail contenant une pièce jointe, puis transmet le message aux destinataires externes.|Chis est protégé par des pièces jointes Coffre. <br/><br/> Si les destinataires externes d’une organisation Microsoft 365, les messages transférés sont également protégés par Coffre pièces jointes.|

L’analyse des pièces jointes fiables a lieu dans la même région que l’emplacement de vos données Microsoft 365. Pour plus d’informations sur la géographie du centre de données, consultez [Où se trouvent vos données ?](https://products.office.com/where-is-your-data-located?geo=All)

> [!NOTE]
> Les fonctionnalités suivantes se trouvent dans les paramètres globaux des stratégies de Coffre pièces jointes dans le portail Microsoft 365 Defender. Toutefois, ces paramètres sont activés ou désactivés globalement et ne nécessitent pas Coffre stratégies de pièces jointes :
>
> - [Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md).
> - [Documents sécurisés dans Microsoft 365 E5](safe-docs.md)

## <a name="safe-attachments-policy-settings"></a>Paramètres de stratégie pièces jointes fiables

Cette section décrit les paramètres des stratégies Coffre Pièces jointes :

- **Coffre réponse de programmes malveillants inconnus pièces jointes** : ce paramètre contrôle l’action de Coffre l’analyse des programmes malveillants pièces jointes dans les messages électroniques. Les options disponibles sont décrites dans le tableau suivant :

  |Option|Effet|Utilisez-la lorsque vous voulez|
  |---|---|---|
  |**Désactivé**|Les pièces jointes ne sont pas analysées pour détecter les programmes malveillants par les pièces jointes fiables. Les messages sont toujours analysés pour rechercher les programmes malveillants par [protection anti-programme malveillant dans EOP](anti-malware-protection.md).|Désactivez l’analyse des destinataires sélectionnés. <br/><br/> Évitez les retards inutiles dans le routage du courrier interne. <br/><br/> **Cette option n’est pas recommandée pour la plupart des utilisateurs. Vous devez utiliser cette option uniquement pour désactiver Coffre l’analyse des pièces jointes pour les destinataires qui reçoivent uniquement des messages d’expéditeurs approuvés. ZAP ne met pas en quarantaine les messages si Coffre pièces jointes est désactivée et qu’un signal de programme malveillant n’est pas reçu. Pour plus d’informations, consultez [La purge automatique zero-hour](zero-hour-auto-purge.md)**|
  |**Moniteur**|Remet des messages avec des pièces jointes, puis effectue le suivi de ce qui se passe avec les programmes malveillants détectés. <br/><br/> La remise des messages sécurisés peut être retardée en raison de l’analyse des pièces jointes Coffre.|Découvrez où les programmes malveillants détectés sont placés dans votre organisation.|
  |**Bloquer**|Empêche la remise des messages avec des pièces jointes de programmes malveillants détectées. <br/><br/> Les messages sont mis en quarantaine. Par défaut, seuls les administrateurs (et non les utilisateurs) peuvent examiner, libérer ou supprimer les messages.<sup>\*</sup> <br/><br/> Bloque automatiquement les instances futures des messages et pièces jointes. <br/><br/> La remise des messages sécurisés peut être retardée en raison de l’analyse des pièces jointes Coffre.|Protège votre organisation contre les attaques répétées à l’aide des mêmes pièces jointes de programmes malveillants. <br/><br/> Il s’agit de la valeur par défaut et de la valeur recommandée dans les [stratégies de sécurité prédéfinies](preset-security-policies.md) Standard et Strict.|
  |**Replace**|Supprime les pièces jointes de programmes malveillants détectées. <br/><br/> Avertit les destinataires que les pièces jointes ont été supprimées. <br/><br/>  Les messages contenant des pièces jointes malveillantes sont mis en quarantaine. Par défaut, seuls les administrateurs (et non les utilisateurs) peuvent examiner, libérer ou supprimer les messages.<sup>\*</sup> <br/><br/> La remise des messages sécurisés peut être retardée en raison de l’analyse des pièces jointes Coffre.|Augmentez la visibilité des destinataires que les pièces jointes ont été supprimées en raison d’un programme malveillant détecté.|
  |**Remise dynamique**|Remet les messages immédiatement, mais remplace les pièces jointes par des espaces réservés jusqu’à ce que l’analyse des pièces jointes fiables soit terminée. <br/><br/> Les messages contenant des pièces jointes malveillantes sont mis en quarantaine. Par défaut, seuls les administrateurs (et non les utilisateurs) peuvent examiner, libérer ou supprimer les messages.<sup>\*</sup> <br/><br/> Pour plus d’informations, consultez la section [Dynamic Delivery dans Coffre attachments policies](#dynamic-delivery-in-safe-attachments-policies) plus loin dans cet article.|Évitez les retards de message tout en protégeant les destinataires contre les fichiers malveillants.|

  <sup>\*</sup>Les administrateurs peuvent créer et affecter des _stratégies de quarantaine_ dans Coffre stratégies pièces jointes qui définissent ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

- **Pièce jointe de redirection lors de la détection : activez la redirection** et **envoyez la pièce jointe à l’adresse e-mail suivante** : pour **les actions Bloquer**, **Surveiller** ou **Remplacer** , envoyez des messages contenant des pièces jointes de programmes malveillants à l’adresse e-mail interne ou externe spécifiée pour analyse et investigation.

  La recommandation pour les paramètres de stratégie Standard et Strict consiste à activer la redirection. Pour plus d’informations, consultez [Coffre paramètres des pièces jointes](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- **Appliquez la sélection ci-dessus si l’analyse des logiciels malveillants pour les pièces jointes expire ou si une erreur se produit** : l’action spécifiée par **Coffre réponse de programmes malveillants inconnus pièces jointes** est effectuée sur les messages même lorsque Coffre’analyse des pièces jointes ne peut pas se terminer. Sélectionnez toujours cette option si vous sélectionnez **Activer la redirection**. Sinon, les messages peuvent être perdus.

- **Filtres de destinataires** : vous devez spécifier les conditions de destinataire et les exceptions qui déterminent à qui la stratégie s’applique. Vous pouvez utiliser ces propriétés pour les conditions et les exceptions :
  - **Le destinataire est**
  - **Le domaine du destinataire est**
  - **Le destinataire est membre de**

  Vous ne pouvez utiliser une condition ou une exception qu'une seule fois, mais la condition ou l'exception peut contenir plusieurs valeurs. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

  > [!IMPORTANT]
  > Plusieurs conditions ou exceptions différentes ne sont pas additives ; ils sont inclusifs. La stratégie est appliquée _uniquement_ aux destinataires qui correspondent à _tous les_ filtres de destinataires spécifiés. Par exemple, vous configurez une condition de filtre de destinataire dans la stratégie avec les valeurs suivantes :
  >
  > - Le destinataire est : romain@contoso.com
  > - Le destinataire est membre de : Executives
  >
  > La stratégie est appliquée à romain@contoso.com _uniquement_ s’il est également membre des groupes exécutifs. S’il n’est pas membre du groupe, la stratégie ne lui est pas appliquée.
  >
  > De même, si vous utilisez le même filtre de destinataires comme exception à la stratégie, la stratégie n’est pas appliquée à romain@contoso.com _uniquement_ s’il est également membre des groupes de cadres. S’il n’est pas membre du groupe, la politique s’applique toujours à lui.

- **Priorité** : si vous créez plusieurs stratégies, vous pouvez spécifier l’ordre dans lequel elles sont appliquées. Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

  Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

### <a name="dynamic-delivery-in-safe-attachments-policies"></a>Distribution dynamique dans les stratégies de pièces jointes Coffre

> [!NOTE]
> La distribution dynamique fonctionne uniquement pour les boîtes aux lettres Exchange Online.

L’action de remise dynamique dans les stratégies de Coffre pièces jointes vise à éliminer les retards de remise des e-mails qui peuvent être causés par Coffre l’analyse des pièces jointes. Le corps du message électronique est remis au destinataire avec un espace réservé pour chaque pièce jointe. L’espace réservé reste jusqu’à ce que la pièce jointe soit trouvée comme étant sécurisée, puis la pièce jointe devient disponible pour l’ouverture ou le téléchargement.

Si une pièce jointe est jugée malveillante, le message est mis en quarantaine.

La plupart des fichiers PDF et des documents Office peuvent être affichés en mode sans échec pendant que l’analyse des pièces jointes fiables est en cours. Si une pièce jointe n’est pas compatible avec l’aperçu de remise dynamique, les destinataires voient un espace réservé pour la pièce jointe jusqu’à ce que Coffre l’analyse des pièces jointes soit terminée.

Si vous utilisez un appareil mobile et que les fichiers PDF ne sont pas affichés dans l’aperçu de la livraison dynamique sur votre appareil mobile, essayez d’ouvrir le message dans Outlook sur le web (anciennement Outlook Web App) à l’aide de votre navigateur mobile.

Voici quelques considérations relatives à la livraison dynamique et aux messages transférés :

- Si le destinataire transféré est protégé par une stratégie de Coffre Pièces jointes qui utilise l’option De remise dynamique, le destinataire voit l’espace réservé, avec la possibilité d’afficher un aperçu des fichiers compatibles.
- Si le destinataire transféré n’est pas protégé par une stratégie de Coffre Pièces jointes, le message et les pièces jointes sont remis sans Coffre l’analyse des pièces jointes ou des espaces réservés de pièces jointes.

Dans certains scénarios, la livraison dynamique ne peut pas remplacer les pièces jointes dans les messages. Ces différents cas de figure sont présentés ci-dessous :

- Messages dans des dossiers publics.
- Messages routées hors de la boîte aux lettres d’un utilisateur à l’aide de règles personnalisées.
- Messages déplacés (automatiquement ou manuellement) hors des boîtes aux lettres cloud vers d’autres emplacements, y compris les dossiers d’archivage.
- Les règles de boîte de réception déplacent le message hors de la boîte de réception dans un autre dossier.
- Messages supprimés.
- Le dossier de recherche de boîte aux lettres de l’utilisateur est dans un état d’erreur.
- Exchange Online organisations où l’option Exclaimer est activée. Pour résoudre ce problème, consultez [KB4014438](https://support.microsoft.com/help/4014438).
- [S/MIME)](/exchange/security-and-compliance/smime-exo/smime-exo) messages chiffrés.
- Vous avez configuré l’action de remise dynamique dans une stratégie de Coffre pièces jointes, mais le destinataire ne prend pas en charge la remise dynamique (par exemple, le destinataire est une boîte aux lettres dans une organisation Exchange locale). Toutefois, [Coffre Liens dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md) est en mesure d’analyser Office pièces jointes de fichier qui contiennent des URL (en fonction de la façon dont [les paramètres globaux de Coffre Liens](configure-global-settings-for-safe-links.md) sont configurés).

## <a name="submitting-files-for-malware-analysis"></a>Envoi de fichiers pour l’analyse des programmes malveillants

- Si vous recevez un fichier que vous souhaitez envoyer à Microsoft à des fins d’analyse, consultez [Envoyer des programmes malveillants et non malveillants à Microsoft à des fins d’analyse](submitting-malware-and-non-malware-to-microsoft-for-analysis.md).
- Si vous recevez un e-mail (avec ou sans pièce jointe) que vous souhaitez envoyer à Microsoft à des fins d’analyse, consultez [les messages de rapport et les fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).
