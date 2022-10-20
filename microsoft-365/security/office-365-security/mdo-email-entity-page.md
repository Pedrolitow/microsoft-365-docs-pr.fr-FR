---
title: Page d’entité d’e-mail Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 10/14/2022
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-security
ms.subservice: mdo
ms.localizationpriority: medium
ms.collection:
- m365-security
- m365initiative-defender-office365
ms.custom: ''
description: Microsoft Defender pour Office 365 clients E5 et P1 et P2 peuvent voir les détails de l’e-mail dans l’Explorateur (Explorateur de menaces), notamment les en-têtes de courrier pour la copie, les détails de détection, les menaces détectées, les emplacements de remise les plus récents et originaux, les actions de remise et les ID tels que l’ID de message réseau, etc.
search.appverid: met150
ms.openlocfilehash: a7f6cbc013cf5a3b8a319a51447f857a16f096fd
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68645118"
---
# <a name="the-email-entity-page"></a>Page de l’entité d’e-mail

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Dans cet article**
- [Atteindre la page d’entité d’e-mail](#how-to-get-to-the-email-entity-page)
- [Lire la page d’entité d’e-mail](#how-to-read-the-email-entity-page)
- [Utiliser des onglets de page d’entité de messagerie](#how-to-use-the-email-entity-page-tabs)
- [Nouveautés de la page d’entité d’e-mail](#available-on-the-email-entity-page)

Les administrateurs de Microsoft Defender pour Office 365 E5 et Defender pour Office P1 et P2 ont une vue à 360 degrés de l’e-mail à l’aide de la **page d’entité Email**. Cette page d’e-mail go-to a été créée pour améliorer les informations [fournies dans le menu volant « Détails de l’e-mail » de l’Explorateur de menaces](threat-explorer-views.md).

Consultez les détails de l’e-mail dans l’Explorateur/l’Explorateur des menaces, y compris les en-têtes de courrier *avec l’option de copie*, les détails de détection, les menaces détectées, les emplacements de remise les plus récents et d’origine, les actions de remise et les ID tels que l’ID de message réseau, etc.

## <a name="how-to-get-to-the-email-entity-page"></a>Comment accéder à la page d’entité d’e-mail

Accédez au portail Microsoft 365 Defender dans <https://security.microsoft.com>**l’Explorateur** de **collaboration** \> Email &. Ou, pour accéder directement à la page **Explorateur** , utilisez <https://security.microsoft.com/threatexplorer>.

1. Dans **l’Explorateur**, sélectionnez l’objet d’un e-mail que vous examinez.
1. Le menu volant de l’e-mail pour ce courrier s’ouvre.
1. Vous verrez **l’entité Ouvrir l’e-mail**.
1. Sélectionnez-le pour la présentation approfondie de votre e-mail.

:::image type="content" source="../../media/email-entities-1-navigation-to-ee.png" alt-text="Une fois l’e-mail sélectionné, vous obtenez un menu volant avec des détails et la page Ouvrir l’entité pour l’e-mail en haut." lightbox="../../media/email-entities-1-navigation-to-ee.png":::

:::image type="content" source="../../media/email-entities-2-eep.png" alt-text="Graphique de la page d’entité d’e-mail qui se concentre sur les titres que vous verrez" lightbox="../../media/email-entities-2-eep.png":::

> [!NOTE]
> Les autorisations nécessaires pour afficher et utiliser cette page sont les mêmes que pour afficher **l’Explorateur**. L’administrateur doit être membre de l’administrateur général ou du lecteur général, ou administrateur de sécurité ou lecteur de sécurité. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

## <a name="how-to-read-the-email-entity-page"></a>Guide pratique pour lire la page d’entité d’e-mail

La structure est conçue pour être facile à lire et à parcourir en un clin d’œil. Différents onglets en haut de la page vous permettent d’examiner plus en détail. Voici comment fonctionne la disposition :

1. Les champs les plus requis se trouvent sur le côté gauche du menu volant. Ces détails sont « collants », ce qui signifie qu’ils sont ancrés à gauche, quel que soit l’onglet vers lequel vous naviguez dans le reste du menu volant.

    :::image type="content" source="../../media/email-entities-3-left-panel.png" alt-text="Graphique de la page d’entité d’e-mail avec le côté gauche mis en évidence" lightbox="../../media/email-entities-3-left-panel.png":::

2. En haut à droite se trouvent les actions qui peuvent être effectuées sur un e-mail. Toutes les actions qui peuvent être effectuées via **l’Explorateur** seront également disponibles via la page d’entité de messagerie.

    :::image type="content" source="../../media/email-entities-5-preview.png" alt-text="Graphique de la page d’entité d’e-mail avec le côté droit mis en évidence" lightbox="../../media/email-entities-5-preview.png":::

3. Une analyse plus approfondie peut être effectuée en triant le reste de la page. Vérifiez les détails de la détection des e-mails, l’état de l’authentification par e-mail et l’en-tête. Cette zone doit être examinée au cas par cas, mais les informations contenues dans ces onglets sont disponibles pour tout e-mail.

    :::image type="content" source="../../media/email-entities-4-middle-panel.png" alt-text="Panneau principal de la page qui inclut l’en-tête d’e-mail et l’état de l’authentification" lightbox="../../media/email-entities-4-middle-panel.png":::

### <a name="how-to-use-the-email-entity-page-tabs"></a>Comment utiliser les onglets de page d’entité d’e-mail

Les onglets situés en haut de la page d’entité vous permettent d’examiner efficacement les e-mails.

1. **Chronologie** : la vue chronologie d’un e-mail (par chronologie **de l’Explorateur** ) affiche la remise d’origine aux événements post-remise qui se produisent sur un e-mail. Pour les e-mails qui n’ont aucune action post-remise, la vue affiche la ligne de remise d’origine en mode chronologie. Événements tels que : Vidage automatique de zéro heure (ZAP), Corriger, clics d’URL, etc., à partir de sources telles que : système, administrateur et utilisateur, s’affichent ici, dans l’ordre dans lequel ils se sont produits.
2. **Analyse** : l’analyse montre des champs qui aident les administrateurs à analyser un e-mail en profondeur. Pour les cas où les administrateurs doivent en savoir plus sur la détection, l’expéditeur/le destinataire et les détails de l’authentification par e-mail, ils doivent utiliser l’onglet Analyse. Des liens pour les pièces jointes et les URL se trouvent également sur cette page, sous « Entités associées ». Les pièces jointes et les menaces identifiées sont numérotées ici, et le fait de cliquer vous permet d’accéder directement aux pages Pièces jointes et URL. Cet onglet comporte également une option d’en-tête Affichage pour *afficher l’en-tête de l’e-mail*. Les administrateurs peuvent comparer les détails des en-têtes de courrier, côte à côte avec les informations du panneau principal, pour plus de clarté.
3. **Pièces jointes** : examine les pièces jointes trouvées dans l’e-mail avec d’autres détails trouvés sur les pièces jointes. Le nombre de pièces jointes affichées est actuellement limité à 10. Notez que les détails de la détonation pour les pièces jointes jugées malveillantes sont également affichés ici.
4. **URL** : cet onglet répertorie les URL trouvées dans l’e-mail avec d’autres détails sur les URL. Le nombre d’URL est limité à 10 actuellement, mais ces 10 sont prioritaires pour afficher *d’abord les URL malveillantes*. La hiérarchisation vous permet de gagner du temps et de deviner du travail. Les URL qui ont été jugées malveillantes et détonées seront également affichées ici.
5. **E-mails similaires** : cet onglet répertorie tous les e-mails similaires à la combinaison *id de message réseau + destinataire* spécifique à cet e-mail. La similarité est basée uniquement sur le *corps du message*. Les déterminations prises sur les messages électroniques pour les classer comme « similaires » n’incluent pas une considération des *pièces jointes*.

## <a name="available-on-the-email-entity-page"></a>Disponible sur la page d’entité d’e-mail

Voici quelques informations utiles pour commencer.

### <a name="email-preview-for-cloud-mailboxes"></a>Email préversion pour les boîtes aux lettres cloud

Les administrateurs peuvent afficher un aperçu des e-mails dans les boîtes aux lettres cloud ***, si*** les messages sont toujours présents dans le cloud. En cas de suppression réversible (par un administrateur ou un utilisateur) ou ZAP (en quarantaine), les e-mails ne sont plus présents dans l’emplacement cloud. Dans ce cas, les administrateurs ne pourront pas afficher un aperçu de ces messages spécifiques. Les e-mails qui ont été supprimés, ou lorsque la remise a échoué, ne sont jamais entrés dans la boîte aux lettres. Par conséquent, les administrateurs ne pourront pas non plus afficher un aperçu de ces e-mails.

> [!WARNING]
> L’aperçu des e-mails nécessite un rôle spécial appelé **Aperçu**. Vous pouvez ajouter ce rôle dans le portail Microsoft 365 Defender comme décrit dans [Email & rôles de collaboration dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal). Vous devrez peut-être créer un groupe de rôles **de collaboration Email &** et ajouter le rôle **Aperçu** à ce nouveau groupe de rôles ou ajouter le rôle **Aperçu** à un groupe de rôles qui permet aux administrateurs de votre organisation de travailler dans **l’Explorateur**.

### <a name="detonation-details"></a>Détails de la détonation

Ces détails sont spécifiques aux pièces jointes et URL de courrier électronique. Les utilisateurs peuvent voir ces détails en allant dans l’Explorateur et en appliquant le filtre *de technologie de détection* défini à la détonation de fichier ou à la détonation d’URL. Les e-mails filtrés pour la détonation de fichier contiennent un fichier malveillant avec des détails de détonation, et ceux filtrés pour les URL contiennent une URL malveillante et ses détails de détonation.

Les utilisateurs verront des détails de détonation enrichis pour les pièces jointes ou URL malveillantes connues trouvées dans leurs e-mails, qui ont été détonées pour leur locataire spécifique. Il inclut la chaîne de détonation, le résumé de la détonation, la capture d’écran et les détails du comportement observé pour aider les clients à comprendre pourquoi la pièce jointe ou l’URL a été jugée malveillante et détonée.

1. *Chaîne de détonation*. Une détonation d’URL ou de fichier unique peut déclencher plusieurs détonations. La chaîne de détonation suit le chemin des détonations, y compris le fichier ou l’URL malveillants d’origine à l’origine du verdict, ainsi que tous les autres fichiers ou URL affectés par la détonation. Ces URL ou fichiers joints peuvent ne pas être directement présents dans l’e-mail, mais il est important d’inclure cette analyse pour déterminer pourquoi le fichier ou l’URL a été détecté comme malveillant.  

    > [!NOTE]
    > Cela peut afficher uniquement l’élément de niveau supérieur si aucune des entités liées à celui-ci n’a été jugée problématique ou a été détonée.

1. *Le résumé de la détonation* fournit un résumé de base pour la détonation, comme le *temps d’analyse*, l’heure à laquelle la détonation s’est produite, le système d’exploitation et l’application, le système d’exploitation et l’application dans lesquels la détonation s’est produite, la taille du fichier et le motif du verdict.
1. *Les captures d’écran* montrent les captures d’écran capturées pendant la détonation. Il peut y avoir plusieurs captures d’écran pendant la détonation. Aucune capture d’écran n’est capturée pour
    - Fichiers de type conteneur tels que .zip ou .rar.
    - Si une URL s’ouvre dans un lien qui télécharge directement un fichier. Toutefois, vous verrez le fichier téléchargé dans la chaîne de détonation.
1. *Les détails du comportement* sont une exportation qui affiche des détails de comportement tels que les événements exacts qui ont eu lieu pendant la détonation, et les observables qui contiennent des URL, des adresses IP, des domaines et des fichiers qui ont été trouvés pendant la détonation (et qui peuvent être problématiques ou bénins). N’oubliez pas qu’il peut n’y avoir aucun détail de comportement pour :
    - Fichiers conteneur tels que .zip ou .rar contenant d’autres fichiers.

:::image type="content" source="../../media/email-entities-6-detonation-page.png" alt-text="Résumé de la détonation montrant la chaîne, le résumé, les détails de la détonation et la capture d’écran sous le titre *Analyse approfondie*" lightbox="../../media/email-entities-6-detonation-page.png":::

### <a name="other-features-that-make-the-email-entity-page-helpful"></a>Autres fonctionnalités qui rendent la page d’entité Email utile

*Balises* : il s’agit de balises appliquées aux utilisateurs. Si l’utilisateur est un destinataire, les administrateurs voient une balise *de destinataire* . De même, si l’utilisateur est un expéditeur, une balise *d’expéditeur* . Cela apparaît dans le côté gauche de la page d’entités de messagerie (dans la partie qui est décrite comme *collante* et, par conséquent, ancrée à la page).

*Emplacement de remise le plus* récent : l’emplacement de remise le plus récent est l’emplacement où un e-mail a atterri après que des actions système telles que ZAP, ou des actions d’administration telles que Déplacer vers des éléments supprimés, se terminent. L’emplacement de remise le plus récent n’est pas destiné à informer les administrateurs de l’emplacement *actuel* du message. Par exemple, si un utilisateur supprime un message ou le déplace vers l’archive, l’emplacement de remise n’est pas mis à jour. Toutefois, si une action système a eu lieu et a mis à jour l’emplacement (par exemple, un ZAP entraînant le passage d’un e-mail en quarantaine), cela met à jour l’emplacement de remise le plus récent en quarantaine.

*Email détails* : détails requis pour une compréhension plus approfondie des e-mails disponibles sous l’onglet *Analyse*.

- *Règles de transport Exchange (également appelées règles de flux de messagerie ou ETR)* : ces règles sont appliquées à un message au niveau de la couche de transport et sont prioritaires sur les verdicts de hameçonnage et de courrier indésirable. Les règles de flux de messagerie sont créées et modifiées dans le Centre d’administration Exchange, <https://admin.exchange.microsoft.com/#/transportrules>mais si une règle de flux de messagerie s’applique à un message, le nom et le GUID de la règle s’affichent ici. Informations précieuses à des fins de suivi.

- *Remplacement principal : Source* : le remplacement principal et la source font référence au paramètre client ou utilisateur qui a eu un impact sur la remise de l’e-mail, en remplaçant l’emplacement de remise donné par le système (conformément à la technologie de menace et de détection). Par exemple, il peut s’agir d’un e-mail bloqué en raison d’une règle de transport configurée par le locataire ou d’un e-mail autorisé en raison d’un paramètre d’utilisateur final pour les expéditeurs approuvés. 

- *Toutes les substitutions* : toutes les substitutions font référence à la liste des remplacements (paramètres client ou utilisateur) appliqués à l’e-mail, ce qui peut avoir ou non eu un impact sur la remise d’un e-mail. Par exemple, si une règle de transport configurée par le locataire, ainsi qu’un paramètre de stratégie configuré par le locataire (par exemple, à partir des listes de blocs d’autorisation du locataire), est appliquée à un e-mail, les deux sont répertoriées dans ce champ. Vous pouvez vérifier le champ de remplacement principal pour déterminer le paramètre qui a impacté la remise de l’e-mail. 

- *Niveau de plainte en bloc (BCL)* : niveau de réclamation en bloc (BCL) du message. Une bcl plus élevée indique qu’un message électronique en bloc est plus susceptible de générer des plaintes (résultat naturel si l’e-mail est susceptible d’être du courrier indésirable).

- *Niveau de confiance du courrier indésirable (SCL)* : niveau de confiance du courrier indésirable (SCL) du message. Plus cette valeur est élevée, plus il est probable que le message est un courrier indésirable.

- *Type de client* : indique le type de client à partir duquel l’e-mail a été envoyé comme REST.

- *Transfert* : pour les scénarios avec transfert automatique, il indique l’utilisateur de transfert ainsi que le type de transfert comme le transfert ETR ou SMTP.

- *Liste de distribution* : affiche la liste de distribution, si le destinataire a reçu l’e-mail en tant que membre de la liste. Il affiche la liste de distribution de niveau supérieur si des listes de distribution imbriquées sont impliquées.  

- *À, Cc* : indique les adresses répertoriées dans les champs À, Cc d’un e-mail. Les informations contenues dans ces champs sont limitées à 5 000 caractères.

- *Nom de domaine* : nom de domaine de l’expéditeur.

- *Propriétaire du domaine* : spécifie le propriétaire du domaine d’envoi.

- *Emplacement du domaine* : spécifie l’emplacement du domaine d’envoi.

- *Date de création du domaine* : spécifie la date de création du domaine d’envoi. Un domaine nouvellement créé peut être prudent si d’autres signaux indiquent un comportement suspect.

*Email l’authentification* : Email méthodes d’authentification utilisées par Microsoft 365 incluent SPF, DKIM et DMARC.

- Sender Policy Framework (**SPF**) : décrit les résultats de la vérification SPF du message. Les valeurs possibles peuvent être les suivantes :
  - Passe (adresse IP) : le SPF vérifie le message passé et inclut l’adresse IP de l’expéditeur. Le client est autorisé à envoyer ou à relayer le courrier électronique avec le domaine de l’expéditeur.
  - Échec (adresse IP) : la vérification SPF du message a échoué et inclut l’adresse IP de l’expéditeur. Dans ce cas, on parle parfois d’échec sévère.
  - Softfail (raison) : l’enregistrement SPF a indiqué que l’hôte n’était pas autorisé à envoyer, mais qu’il était en transition.
  - Neutre : l’enregistrement SPF indique explicitement qu’il n’indique pas si l’adresse IP est autorisée à envoyer.
  - Aucun : le domaine n’a pas d’enregistrement SPF ou l’enregistrement SPF n’est pas évalué à un résultat.
  - Temperror : une erreur temporaire s’est produite. Par exemple, une erreur DNS. Cette même vérification peut être effectuée ultérieurement.
  - Permerror : une erreur permanente s’est produite. Par exemple, un enregistrement SPF mal mis en forme dans le domaine.

- DomainKeys Identified Mail (**DKIM)** :
  - Passe : indique la vérification DKIM du message passé.
  - Échec (raison) : indique la vérification DKIM du message ayant échoué et pourquoi. Par exemple, parce que le message n’a pas été signé ou que la signature n’a pas été vérifiée.
  - Aucun : indique que le message n’a pas été signé. Cela peut indiquer ou non que le domaine a un enregistrement DKIM ou que l’enregistrement DKIM n’est pas évalué à un résultat, mais seulement que ce message n’a pas été signé.

- Authentification, création de rapports et conformité des messages basée sur le domaine (**DMARC**) :
  - Passe : indique la vérification DMARC pour le message passé.
  - Échec : indique que la vérification DMARC du message a échoué.
  - Bestguesspass : indique qu’il n’existe aucun enregistrement TXT DMARC pour le domaine, mais que si un enregistrement existait, la vérification DMARC du message aurait réussi.
  - Aucun : indique qu’il n’existe aucun enregistrement TXT DMARC pour le domaine d’envoi dans DNS.

*Authentification composite* : il s’agit d’une valeur utilisée par Microsoft 365 pour combiner l’authentification par e-mail comme SPF, DKIM et DMARC, pour déterminer si le message est authentique. Il utilise le domaine *From :* du courrier comme base d’évaluation.

## <a name="actions-you-can-take-on-the-email-entity-page"></a>Actions que vous pouvez effectuer sur la page d’entité Email

Les équipes de sécurité peuvent désormais effectuer des actions de courrier électronique telles que la suppression réversible et la suppression définitive, passer au courrier indésirable, passer à la boîte de réception, déclencher une enquête, envoyer à Microsoft pour révision en ligne, et ainsi de suite. **Les** actions de bloc au niveau du locataire, telles que le fichier et l’URL ou l’expéditeur, peuvent également être déclenchées à partir de la page d’entité Email.  

Vous serez en mesure de sélectionner **Effectuer des actions** dans le coin supérieur droit de la page d’entité, ce qui ouvre l’Assistant Action pour vous permettre de sélectionner l’action spécifique dont vous avez besoin. 
![Effectuez une action à partir de la page d’entité.](../../media/Take-ActionWizard-Email-entity.png)

Dans l’Assistant Action, vous pouvez effectuer des actions par e-mail, des soumissions de courrier électronique, bloquer le domaine de l’expéditeur et de l’expéditeur, des actions d’investigation et une approbation en deux étapes (ajouter à la correction) dans le même volet latéral. Ceci suit un flux cohérent pour faciliter l’utilisation. L’Assistant Action utilise le même système que celui utilisé par les actions de l’Explorateur (pour les actions de suppression, d’envoi et d’investigation), par exemple. Vous pourrez voir et suivre ces actions dans le [centre d’action unifié](https://security.microsoft.com/action-center/history) (pour les e-mails supprimés), dans le [portail d’envoi](https://security.microsoft.com/reportsubmission) (pour les soumissions) et dans la page [Autoriser/Bloquer les listes](https://security.microsoft.com/tenantAllowBlockList) de locataires pour (blocs TABL). 

Nous apportons également l’URL de bloc au niveau du locataire et la pièce jointe à l’URL d’entité Email et aux onglets Pièces jointes respectifs. Une fois l’approbation effectuée, toutes les URL de blocs et toutes les listes de blocs (ou TABL) des listes d’autorisations et de blocs peuvent être suivies sous tabl/URL et les pages tabl/fichier. 
![Effectuez l’action bloquer l’URL à partir de la page d’entité.](../../media/Block-URL-Email-entity.png)

Consultez [les autorisations](permissions-microsoft-365-security-center.md) requises pour effectuer ces actions. 

 
### <a name="the-email-summary-panel"></a>Panneau récapitulatif Email

Le panneau récapitulatif de l’e-mail est une vue récapitulative de la page d’entité de messagerie complète. Il contient des détails standardisés sur l’e-mail (par exemple, les détections), ainsi que des informations spécifiques au contexte (par exemple, pour les métadonnées de mise en quarantaine ou de soumission). Le panneau récapitulatif de l’e-mail remplace les menus volants traditionnels Détections en temps réel, Explorateur de menaces, Soumissions et Rapports.

> [!div class="mx-imgBorder"]
> ![Ouvrez le lien d’entité d’e-mail.](../../media/open-email-entity-mdo.png)

> [!NOTE]
> Pour afficher tous les composants, cliquez sur le lien **Ouvrir l’entité d’e-mail** pour ouvrir la page d’entité de messagerie complète.  

Le panneau récapitulatif de l’e-mail est divisé en sections suivantes :  

- *Détails de la remise* : contient des informations sur les menaces et le niveau de confiance, les technologies de détection et l’emplacement de livraison d’origine et le dernier emplacement correspondant.

- Email détails : contient des informations sur *les propriétés* d’e-mail telles que le nom de l’expéditeur, l’adresse de l’expéditeur, l’heure de réception, les détails de l’authentification et d’autres détails.

- *URL* : par défaut, vous verrez 3 URL et leurs menaces correspondantes. Vous pouvez toujours sélectionner **Afficher toutes les URL** pour développer et afficher toutes les URL et les exporter.  

- *Pièces jointes* : par défaut, vous verrez 3 pièces jointes. Vous pouvez toujours sélectionner **Afficher toutes les pièces jointes** pour les développer et afficher toutes les pièces jointes. 

En plus des sections ci-dessus, vous verrez également des sections spécifiques à peu d’expériences intégrées au panneau récapitulatif : 

- Soumissions: 

    - *Détails de la soumission* : contient des informations sur les soumissions spécifiques, telles que :
        - Date d’envoi
        - Sujet
        - Type d’envoi
        - Motif de l’envoi
        - ID de soumission
        - Soumis par

    - *Détails du résultat* : les messages envoyés sont examinés. Vous pouvez voir le résultat de votre soumission ainsi que les étapes suivantes recommandées.

- Quarantaine:  

    - *Détails de la quarantaine* : contient des détails spécifiques à la quarantaine. Pour plus d’informations, consultez [Gérer les messages mis en quarantaine](manage-quarantined-messages-and-files.md#view-quarantined-message-details).

        - Expires : Date et heure auxquelles le message sera automatiquement et définitivement supprimé de la quarantaine.
        - Déplacé pour : toutes les adresses e-mail (le cas échéant) auxquelles le message a été envoyé.
        - Pas encore déplacé pour : toutes les adresses e-mail (le cas échéant) auxquelles le message n'a pas encore été envoyé.

    - *Actions de quarantaine* : pour plus d’informations sur les différentes actions de quarantaine, consultez [Gérer les messages mis en quarantaine](manage-quarantined-messages-and-files.md#take-action-on-quarantined-email).
