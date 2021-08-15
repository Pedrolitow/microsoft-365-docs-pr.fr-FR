---
title: Page Microsoft Defender pour Office 365'entité de messagerie
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 01/21/2021
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les clients Microsoft Defender pour Office 365 E5 et P1 et P2 peuvent désormais obtenir une vue à 360 degrés de chaque courrier électronique avec une page d’entité de messagerie.
ms.openlocfilehash: a1e318541a970b6fbd6fe04ac4b8de421ecff9aba7479393a245bc10e47e5d46
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53897278"
---
# <a name="the-email-entity-page"></a>Page de l’entité d’e-mail

**Dans cet article**
- [Atteindre la page d’entité de messagerie](#reach-the-email-entity-page)
- [Lire la page d’entité de messagerie](#read-the-email-entity-page)
- [Utiliser les onglets de page d’entité de messagerie](#use-email-entity-page-tabs)
- [Nouvelle page de l’entité de messagerie](#new-to-the-email-entity-page)

Les administrateurs de Microsoft Defender pour Office 365 E5 et de Defender pour Office P1 et P2 ont une vue à 360 degrés du courrier électronique à l’aide de la **page** Entité de messagerie. Cette page de courrier électronique d’accès a été créée pour améliorer les informations livrées dans le volant « Détails des e-mails » de [l’Explorateur de menaces.](threat-explorer-views.md)

## <a name="reach-the-email-entity-page"></a>Atteindre la page d’entité de messagerie

La page d’entité de messagerie est disponible dans le portail Microsoft 365 Defender ( ) à l'& <https://security.microsoft.com> **l’Explorateur de** \> **collaboration.** Ou, pour aller directement à la page **De l’Explorateur,** utilisez <https://security.microsoft.com/threatexplorer> .

Dans **l’Explorateur,** sélectionnez l’objet d’un e-mail que vous examinez. Une barre d’or s’affiche en haut du volant du courrier électronique pour ce courrier. Cette invitation à la nouvelle page indique « Essayez notre nouvelle page d’entité de messagerie avec des données enrichies... ». Sélectionnez pour afficher la nouvelle page.

:::image type="content" source="../../media/email-entities-1-navigation-to-ee.png" alt-text="Vous verrez une bannière d’or avec les mots *Essayer notre nouvelle page d’entité de messagerie avec des données enrichies* pour naviguer vers la nouvelle expérience.":::

:::image type="content" source="../../media/email-entities-2-eep.png" alt-text="Ce graphique de la page d’entité de messagerie se concentre sur les titres que vous verrez. Notez que l’en-tête de l’e-mail s’affiche ici.":::

> [!NOTE]
> Les autorisations nécessaires pour afficher et utiliser cette page sont les mêmes que pour afficher **l’Explorateur.** L’administrateur doit être membre de l’administrateur global ou du lecteur global, ou administrateur de sécurité ou lecteur sécurité. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

## <a name="read-the-email-entity-page"></a>Lire la page d’entité de messagerie

La structure est conçue pour être facile à lire et à parcourir en un coup d’œil. Divers onglets en haut de la page vous permettent d’examiner plus en détail. Voici comment fonctionne la disposition :

1. Les champs les plus requis sont sur le côté gauche du volant. Ces détails sont « résessants » ; ils sont donc ancrés à gauche, quel que soit l’onglet dans le reste du volant.

    :::image type="content" source="../../media/email-entities-3-left-panel.png" alt-text="Graphique de la page d’entité de messagerie avec le côté gauche mis en évidence. Le titre et les faits sur la remise du courrier sont ici.":::

2. Dans le coin supérieur droit se trouver les actions qui peuvent être prises sur un e-mail. Toutes les actions qui peuvent être entreprises par le biais de **l’Explorateur** sont également disponibles via la page d’entité de messagerie.

    :::image type="content" source="../../media/email-entities-5-preview.png" alt-text="Graphique de la page d’entité de messagerie avec le côté *droite* mis en surbrillant, cette fois. Des actions telles que « Aperçu du courrier électronique » et « Mettre en quarantaine » sont ici.":::

3. Une analyse plus approfondie peut être effectuée en triant le reste de la page. Vérifiez les détails de détection du courrier électronique, l’état de l’authentification du courrier électronique et l’en-tête. Cette zone doit être examiné au cas par cas, mais les informations de ces onglets sont disponibles pour tous les messages électroniques.

    :::image type="content" source="../../media/email-entities-4-middle-panel.png" alt-text="Le panneau principal de cette page inclut l’en-tête de courrier électronique et l’état d’authentification.":::

### <a name="use-email-entity-page-tabs"></a>Utiliser les onglets de page d’entité de messagerie

Les onglets en haut de la page d’entité vous permettent d’examiner efficacement les messages électroniques.

1. **Chronologie**: l’affichage chronologique  d’un e-mail (par chronologie de l’Explorateur) indique la remise d’origine aux événements de post-remise qui se produisent sur un e-mail. Pour les e-mails qui n’ont aucune action de post-remise, l’affichage affiche la ligne de remise d’origine dans l’affichage chronologique. Les événements tels que : la purge automatique heure zéro (ZAP), la correction, les clics d’URL et les événements provenant de sources telles que : système, administrateur et utilisateur, s’affichent ici, dans l’ordre dans lequel ils se sont produits.
2. **Analyse**: l’analyse montre les champs qui aident les administrateurs à analyser un courrier électronique en profondeur. Pour les cas où les administrateurs doivent mieux comprendre la détection, l’expéditeur/le destinataire et les détails de l’authentification de messagerie, ils doivent utiliser l’onglet Analyse. Des liens pour les pièces jointes et les URL sont également trouvés sur cette page, sous « Entités associées ». Les pièces jointes et les menaces identifiées sont numéroées ici et un clic vous permet d’accéder directement aux pages pièces jointes et URL. Cet onglet dispose également d’une option d’affichage d’en-tête pour *afficher l’en-tête de l’e-mail.* Les administrateurs peuvent comparer les détails des en-têtes de courrier électronique, côte à côte avec les informations du panneau principal, pour plus de clarté.
3. **Pièces jointes**: examine les pièces jointes trouvées dans l’e-mail avec d’autres détails trouvés sur les pièces jointes. Le nombre de pièces jointes affichées est actuellement limité à 10. Notez que les détails de détonation pour les pièces jointes qui sont malveillantes sont également affichés ici.
4. **URL : cet** onglet répertorie les URL trouvées dans l’e-mail avec d’autres détails sur les URL. Le nombre d’URL est limité à 10 pour l’instant, mais ces 10 url sont priorisées pour afficher d’abord les *URL malveillantes.* La hiér donc vous permet de gagner du temps et de deviner le travail. Les URL qui ont été trouvées comme malveillantes et détonées sont également affichées ici.
5. **Courriers électroniques similaires**: cet onglet répertorie tous les messages électroniques similaires à *l’ID de message réseau +* combinaison de destinataires spécifiques à ce courrier électronique. La similarité est basée sur *le corps du message,* uniquement. Les déterminations réalisées sur les messages pour les classer comme « similaires » n’incluent pas de considération sur *les pièces jointes.*

## <a name="new-to-the-email-entity-page"></a>Nouvelle page de l’entité de messagerie

Il existe de nouvelles fonctionnalités qui s’inséront dans cette page d’entité de messagerie. Voici la liste.

### <a name="email-preview-for-cloud-mailboxes"></a>Aperçu du courrier électronique pour les boîtes aux lettres cloud

Les administrateurs peuvent afficher un aperçu des e-mails dans les boîtes aux lettres ***cloud,*** si les messages sont toujours présents dans le cloud. En cas de suppression (par un administrateur ou un utilisateur) ou ZAP (mise en quarantaine), les e-mails ne sont plus présents dans l’emplacement cloud. Dans ce cas, les administrateurs ne pourront pas afficher un aperçu de ces messages spécifiques. Les e-mails qui ont été supprimés, ou lorsque la remise a échoué, n’ont jamais été envoyés dans la boîte aux lettres. Par conséquent, les administrateurs ne pourront pas non plus prévisualiser ces e-mails.

> [!WARNING]
> L’aperçu des e-mails nécessite un rôle spécial appelé **Aperçu.** Vous pouvez ajouter ce rôle dans le portail Microsoft 365 Defender comme décrit dans les rôles de collaboration & messagerie dans le [portail Microsoft 365 Defender.](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal) Vous devrez peut-être créer un groupe de rôles de collaboration Email &  et ajouter le rôle Aperçu à ce nouveau groupe de rôles ou ajouter le rôle Aperçu à un groupe de rôles qui **permet** aux administrateurs de votre organisation de travailler dans  **l’Explorateur.**

### <a name="detonation-details"></a>Détails de la détonation

Ces détails sont spécifiques aux pièces jointes et URL des e-mails. Les utilisateurs peuvent voir ces détails  en allant dans l’Explorateur et en appliquant le filtre de technologie de détection au détonation de fichier ou à la détonation d’URL. Les e-mails filtrés pour la détonation de fichiers contiennent un fichier malveillant avec des détails de détonation, et ceux filtrés pour les URL contiennent une URL malveillante et ses détails de détonation.

Les utilisateurs voient des détails de détonation enrichis pour les pièces jointes ou URL malveillantes connues trouvées dans leurs e-mails, qui ont été détonées pour leur client spécifique. Il comprend la chaîne de détonation, le résumé de la détonation, la capture d’écran et les détails du comportement observé pour aider les clients à comprendre pourquoi la pièce jointe ou l’URL a été considérée comme malveillante et détonée.

1. *Chaîne de détonation*. Une détonation de fichier ou d’URL unique peut déclencher plusieurs détonations. La chaîne de détonation suit le chemin d’accès des détonations, y compris le fichier ou l’URL malveillant d’origine à l’origine du verdict, ainsi que tous les autres fichiers ou URL qui ont été impactés par la détonation. Ces URL ou fichiers joints peuvent ne pas être directement présents dans l’e-mail, mais il est important d’inclure cette analyse pour déterminer pourquoi le fichier ou l’URL a été trouvé comme malveillant.  

    > [!NOTE]
    > Cela peut uniquement afficher l’élément de niveau supérieur si aucune des entités liées à celui-ci n’a été trouvée problématique ou a été désaxée.

1. Le résumé de la détonation fournit un résumé de base pour la détonation, tel que le temps d’analyse, l’heure à laquelle la *détonation* s’est produite, le système d’exploitation et l’application, le système d’exploitation et l’application dans lesquels la détonation s’est produite, la taille du fichier et la raison du verdict.
1. *Les captures d’écran* montrent les captures d’écran capturées lors de la détonation. Il peut y avoir plusieurs captures d’écran pendant la détonation. Aucune capture d’écran n’est capturée pour
    - Fichiers de type conteneur tels .zip ou .rar.
    - Si une URL s’ouvre dans un lien qui télécharge directement un fichier. Toutefois, vous verrez le fichier téléchargé dans la chaîne de détonation.
1. Les *détails* du comportement sont une exportation qui affiche des détails de comportement tels que des événements exacts qui ont eu lieu lors de la détonation et des éléments observables qui contiennent des URL, des adresses IP, des domaines et des fichiers qui ont été trouvés lors de la détonation (et qui peuvent être problématiques ou indésirables). Sachez qu’il n’y a peut-être pas de détails de comportement pour :
    - Fichiers de conteneur tels .zip ou .rar contenant d’autres fichiers.

:::image type="content" source="../../media/email-entities-6-detonation-page.png" alt-text="Capture d’écran du résumé de la détonation montrant la chaîne, le résumé, les détails de la détonation et la capture d’écran sous le titre *Analyse approfondie*.":::

### <a name="other-innovations"></a>Autres innovations

*Balises*: ces balises sont appliquées aux utilisateurs. Si l’utilisateur est un destinataire, les administrateurs voient une *balise de* destinataire. De même, si l’utilisateur est un expéditeur, une *balise d’expéditeur.* Cela s’affiche dans le côté gauche de la page des  entités de messagerie (dans la partie décrite comme étant resserrante et, par conséquent, ancrée à la page).

*Emplacement de remise le* plus récent : l’emplacement de remise le plus récent est l’emplacement où un courrier électronique a été envoyé après des actions système telles que ZAP, ou des actions d’administrateur telles que Déplacer vers les éléments supprimés, se terminent. L’emplacement de remise le plus récent n’est pas destiné à informer les administrateurs de l’emplacement *actuel du* message. Par exemple, si un utilisateur supprime un message ou le déplace vers l’archive, l’emplacement de remise ne sera pas mis à jour. Toutefois, si une action du système a eu lieu et mis à jour l’emplacement (par exemple, une zap qui entraîne le déplacement d’un e-mail en quarantaine), cela met à jour l’emplacement de remise le plus récent en quarantaine.

*Détails de l’e-mail*: détails requis pour une compréhension approfondie du courrier électronique disponible dans *l’onglet Analyse.*

- *Exchange de transport (également appelées* règles de flux de messagerie ou ETR) : ces règles sont appliquées à un message au niveau de la couche de transport et prévalent sur les verdicts de hameçonnage et de courrier indésirable. Ils peuvent uniquement être créés et modifiés dans le Centre d’administration Exchange, mais si une etr s’applique à un message, le nom et le GUID ETR s’afficheront ici. Informations précieuses à des fins de suivi.

- *Remplacements système*: il s’agit d’un moyen d’effectuer des exceptions à l’emplacement de remise prévu pour un message en remplacement de l’emplacement de remise donné par le système (selon la technologie de détection et de menace).

- *Règle de boîte aux* lettres indésirable : « Courrier indésirable » est une règle de boîte de réception masquée qui est activée par défaut dans chaque boîte aux lettres.
  - Lorsque la règle de courrier indésirable est activée sur la boîte aux lettres, Exchange Online Protection (EOP) est en mesure de déplacer des messages vers le courrier indésirable en fonction de certains critères. Le déplacement peut être basé sur l’action de verdict de filtrage du courrier indésirable Déplacer *le message* vers le dossier Courrier indésirable ou sur la liste des expéditeurs bloqués de la boîte aux lettres. La désactivation de la règle de courrier indésirable empêche la remise de messages dans le dossier Courrier indésirable en fonction de la liste *Coffre expéditeurs* de la boîte aux lettres.
  - Lorsque la règle  de courrier indésirable est désactivée sur la boîte aux lettres, EOP ne peut pas déplacer les messages vers le dossier Courrier indésirable en fonction de l’action de verdict de filtrage du courrier indésirable Déplacer le *message* vers le dossier Courrier indésirable ou la collection de listes sécurisées de la boîte aux lettres.

- *Niveau de réclamation en bloc (BCL)*: niveau de réclamation en bloc (BCL) du message. Une valeur BCL supérieure indique qu’un message en nombre est plus susceptible de générer des réclamations (résultat naturel si le courrier électronique est susceptible d’être du courrier indésirable).

- *Niveau de confiance du courrier indésirable (SCL)*: niveau de confiance du courrier indésirable (SCL) du message. Plus cette valeur est élevée, plus il est probable que le message est un courrier indésirable.

- *Nom de domaine*: est le nom de domaine de l’expéditeur.

- *Propriétaire du* domaine : spécifie le propriétaire du domaine d’envoi.

- *Emplacement du* domaine : spécifie l’emplacement du domaine d’envoi.

- *Date de création du* domaine : spécifie la date de création du domaine d’envoi. Vous pouvez faire attention à un domaine nouvellement créé si d’autres signaux indiquent un comportement suspect.

*Authentification de messagerie*: méthodes d’authentification de messagerie Microsoft 365 par SPF, DKIM et DMARC.

- Sender Policy Framework (**SPF)**: décrit les résultats de la vérification SPF du message. Les valeurs possibles peuvent être :
  - Pass (adresse IP) : vérification SPF du message passé et inclut l’adresse IP de l’expéditeur. Le client est autorisé à envoyer ou à relayer le courrier électronique avec le domaine de l’expéditeur.
  - Échec (adresse IP) : la vérification SPF du message a échoué et inclut l’adresse IP de l’expéditeur. Dans ce cas, on parle parfois d’échec sévère.
  - Softfail (raison) : l’enregistrement SPF a désigné l’hôte comme n’étant pas autorisé à envoyer mais est en transition.
  - Neutre : l’enregistrement SPF indique explicitement qu’il n’indique pas si l’adresse IP est autorisée à envoyer des messages.
  - Aucun : le domaine n’a pas d’enregistrement SPF ou l’enregistrement SPF n’est pas évalué comme un résultat.
  - Leror : une erreur temporaire s’est produite. Par exemple, une erreur DNS. Cette même vérification peut être effectuée ultérieurement.
  - Permerror : une erreur permanente s’est produite. Par exemple, un enregistrement SPF mal mis en forme dans le domaine.

- DomainKeys Identified Mail (**DKIM**) :
  - Pass : indique la vérification DKIM pour le message passé.
  - Échec (raison) : indique que la vérification DKIM pour le message a échoué et pourquoi. Par exemple, parce que le message n’a pas été signé ou que la signature n’a pas été vérifiée.
  - Aucun : indique que le message n’a pas été signé. Cela n’indique pas forcément que le domaine a un enregistrement DKIM ou que l’évaluation de l’enregistrement DKIM ne donne pas de résultat, mais simplement que ce message n’a pas été signé.

- Domain-based Message Authentication, Reporting, and Conformance (**DMARC**) :
  - Pass : indique la vérification DMARC pour le message passé.
  - Échec : indique que la vérification DMARC du message a échoué.
  - Bestguesspass : indique qu’il n’existe aucun enregistrement TXT DMARC pour le domaine, mais que s’il en existait un, la vérification DMARC aurait réussi.
  - Aucun : indique qu’il n’existe aucun enregistrement TXT DMARC pour le domaine d’envoi dans le DNS.

*Authentification* composite : il s’agit d’une valeur utilisée par Microsoft 365 pour combiner l’authentification de messagerie comme SPF, DKIM et DMARC, afin de déterminer si le message est authentique. Il utilise le *domaine De :* du courrier comme base d’évaluation.
