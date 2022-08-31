---
title: Vues de campagne dans Microsoft Defender pour Office 365 Plan
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: mcostea
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Découvrez les vues de campagne dans Microsoft Defender pour Office 365.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 7d705e77e7d288ea6cee594d02277d2c9bb54db1
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67473961"
---
# <a name="campaign-views-in-microsoft-defender-for-office-365"></a>Affichages des campagnes dans Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)

Les vues de campagne sont une fonctionnalité de Microsoft Defender pour Office 365 Plan 2 (par exemple, Microsoft 365 E5 ou des organisations disposant d’un module complémentaire plan 2 Defender pour Office 365). Les vues de campagne dans le portail Microsoft 365 Defender identifient et classent les attaques par hameçonnage dans le service. Campaign Views permet d’effectuer les opérations suivantes :

- Examiner et répondre efficacement aux attaques par hameçonnage.
- Mieux comprendre l’étendue de l’attaque.
- Afficher la valeur pour les décideurs.

Campaign Views vous permet de voir la présentation d’une attaque plus rapidement et plus complètement que n’importe quel autre utilisateur.

Regardez cette courte vidéo sur la façon dont les vues de campagne dans Microsoft Defender pour Office 365 vous aident à comprendre les campagnes d’attaque ciblant votre organisation.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGBL8]

## <a name="what-is-a-campaign"></a>Qu’est-ce qu’une campagne ?

Une campagne est une attaque par e-mail coordonné contre une ou plusieurs organisations. Email attaques qui volent des informations d’identification et des données d’entreprise sont un secteur important et lucratif. À mesure que les technologies augmentent afin d’arrêter les attaques, les attaquants modifient leurs méthodes afin d’assurer la réussite continue.

Microsoft tire parti des grandes quantités de données anti-hameçonnage, anti-courrier indésirable et anti-programme malveillant sur l’ensemble du service pour aider à identifier les campagnes. Nous analysons et classons les informations d’attaque en fonction de plusieurs facteurs. Par exemple :

- **Source d’attaque** : adresses IP sources et domaines de messagerie de l’expéditeur.
- **Propriétés du message** : contenu, style et tonalité des messages.
- **Destinataires du message** : lien entre les destinataires. Par exemple, les domaines des destinataires, les fonctions de travail des destinataires (administrateurs, cadres, etc.), les types d’entreprise (grandes, petites, publiques, privées, etc.) et les secteurs d’activité.
- **Charge utile d’attaque** : liens malveillants, pièces jointes ou autres charges utiles dans les messages.

Une campagne peut être de courte durée ou peut s’étendre sur plusieurs jours, semaines ou mois avec des périodes actives et inactives. Une campagne peut être lancée auprès de votre organisation spécifique, ou votre organisation peut faire partie d’une campagne plus importante au sein de plusieurs entreprises.

## <a name="campaign-views-in-the-microsoft-365-defender-portal"></a>Vues de campagne dans le portail Microsoft 365 Defender

Les vues de campagne sont disponibles dans le portail Microsoft 365 Defender à <https://security.microsoft.com> **l’adresse Email & campagnes de collaboration**\>, ou directement à <https://security.microsoft.com/campaigns>.

:::image type="content" source="../../media/campaigns-overview.png" alt-text="Vue d’ensemble des campagnes dans le portail Microsoft 365 Defender" lightbox="../../media/campaigns-overview.png":::

Vous pouvez également accéder aux vues de campagne à partir de :

- Email & campagnes  **d’affichage de** \> **l’Explorateur** \> **de collaboration** \>
- Email &'onglet **Afficher** \> la **campagne** **de tous les e-mails** \> de **l’Explorateur** \> **de collaboration** \>
- **Email &'onglet**  Campagne **de hameçonnage** \> **de l’Explorateur** \>  \> de collaboration \>
-  onglet Campagne contre les **programmes malveillants** \> **de l’Explorateur**  \> \> de Email & collaboration  \>

Pour accéder aux vues de campagne, vous devez être membre des groupes de **rôles Gestion de l’organisation**, **Administrateur de la sécurité** ou **Lecteur de sécurité** dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

## <a name="campaigns-overview"></a>Vue d’ensemble des campagnes

La page vue d’ensemble affiche des informations sur toutes les campagnes.

Sous l’onglet **Campagne** par défaut, la zone **de type Campagne** affiche un graphique à barres qui affiche le nombre de destinataires par jour. Par défaut, le graphique affiche les données **phish** et **malware** .

> [!TIP]
> Si vous ne voyez pas de données de campagne, essayez de modifier la plage de [dates ou les filtres](#filters-and-settings).

Le tableau sous le graphique de la page vue d’ensemble affiche les informations suivantes sous l’onglet **Campagne** :

- **Nom**

- **Exemple d’objet** : la ligne d’objet de l’un des messages de la campagne. Notez que tous les messages de la campagne n’auront pas nécessairement le même sujet.

- **Ciblé** : pourcentage calculé par : (nombre de destinataires de la campagne dans votre organisation) / (nombre total de destinataires de la campagne dans toutes les organisations du service). Cette valeur indique la mesure dans laquelle la campagne est dirigée uniquement vers votre organisation (valeur supérieure) et également vers d’autres organisations du service (valeur inférieure).

- **Type** : cette valeur est **phish** ou **malware**.

- **Sous-type** : cette valeur contient plus de détails sur la campagne. Par exemple :
  - **Phish**: Si disponible, la marque qui est hameçonnée par cette campagne. Par exemple, `Microsoft`, `365`, `Unknown`, `Outlook`ou `DocuSign`.
  - **Programme malveillant** : par exemple, `HTML/PHISH` ou `HTML/<MalwareFamilyName>`.

  Si disponible, la marque qui est hameçonnée par cette campagne. Lorsque la détection est pilotée par Defender pour Office 365 technologie, le préfixe **ATP est** ajouté à la valeur de sous-type.

- **Destinataires** : nombre d’utilisateurs qui ont été ciblés par cette campagne.

- **Boîte de réception** : nombre d’utilisateurs qui ont reçu des messages de cette campagne dans leur boîte de réception (non remis à leur dossier Junk Email).

- **Clic** : nombre d’utilisateurs qui ont cliqué sur l’URL ou ouvert la pièce jointe dans le message d’hameçonnage.

- **Taux de clic** : pourcentage calculé par «**Boîte de réception** **cliqué** /  ». Cette valeur est un indicateur de l’efficacité de la campagne. En d’autres termes, si les destinataires ont pu identifier le message comme hameçonnage, et s’ils n’ont pas cliqué sur l’URL de charge utile.

  Notez que **le taux de clics** n’est pas utilisé dans les campagnes de programmes malveillants.

- **Visité** : combien d’utilisateurs ont réussi à accéder au site web de la charge utile. S’il existe des valeurs **cliquées** , mais que les liens sécurisés ont bloqué l’accès au site web, cette valeur sera égale à zéro.

**L’onglet Origine** de la campagne affiche les sources de message sur une carte du monde.

### <a name="filters-and-settings"></a>Filtres et paramètres

En haut de la page **Campagne** , il existe plusieurs paramètres de filtre et de requête pour vous aider à rechercher et isoler des campagnes spécifiques.

:::image type="content" source="../../media/campaign-filters-and-settings.png" alt-text="Filtres de campagne" lightbox="../../media/campaign-filters-and-settings.png":::

Le filtrage le plus simple que vous pouvez effectuer est la date/heure de début et la date/heure de fin.

Pour filtrer davantage l’affichage, vous pouvez effectuer un filtrage de propriété unique avec plusieurs valeurs en cliquant sur le bouton **Type de campagne** , en effectuant votre sélection, puis en cliquant sur **Actualiser**.

Les propriétés de campagne filtrables disponibles dans le bouton **Type** de campagne sont décrites dans la liste suivante :

- **De base** :
  - **Type de campagne** : Sélectionnez **Programme malveillant** ou **Hameçonnage**. L’effacement des sélections a le même résultat que la sélection des deux.
  - **Nom de la campagne**
  - **Sous-type de campagne**
  - **Expéditeur**
  - **Destinataires**
  - **Domaine de l’expéditeur**
  - **Sujet**
  - **Nom de fichier des pièces jointes**
  - **Famille de programmes malveillants**
  - **Balises** : utilisateurs ou groupes auxquels la balise utilisateur spécifiée a été appliquée (y compris les comptes prioritaires). Pour plus d’informations sur les balises utilisateur, consultez [Balises utilisateur](user-tags.md).
  - **Action de remise**
  - **Action supplémentaire**
  - **Orientation**
  - **Technologie de détection**
  - **Emplacement de livraison d’origine**
  - **Emplacement de livraison le plus récent**
  - **Remplacements système**

- **Avancé** :
  - **ID de message Internet** : disponible dans le champ **d’en-tête Message-ID de l’en-tête** de message. Un exemple de valeur est `<08f1e0f6806a47b4ac103961109ae6ef@server.domain>` (notez les crochets d’angle).
  - **ID de message réseau** : valeur GUID disponible dans le champ d’en-tête **X-MS-Exchange-Organization-Network-Message-Id de l’en-tête** de message.
  - **IP de l’expéditeur**
  - **Pièce jointe SHA256** : Pour rechercher la valeur de hachage SHA256 d’un fichier dans Windows, exécutez la commande suivante dans une invite de commandes : `certutil.exe -hashfile "<Path>\<Filename>" SHA256`.
  - **Cluster ID**
  - **ID d’alerte**
  - **ID de stratégie d’alerte**
  - **ID de campagne**
  - **Signal d’URL ZAP**

- **URLs**:
  - **Domaine d’URL**
  - **Domaine et chemin d’accès d’URL**
  - **URL**
  - **Chemin de l’URL**
  - **Cliquez sur verdict**

Pour un filtrage plus avancé, y compris le filtrage par plusieurs propriétés, vous pouvez cliquer sur le bouton **Filtre avancé** pour générer une requête. Les mêmes propriétés de campagne sont disponibles, mais avec les améliorations suivantes :

- Vous pouvez cliquer sur **Ajouter une condition** pour sélectionner plusieurs conditions.
- Vous pouvez choisir l’opérateur **And** ou **Or** entre les conditions.
- Vous pouvez sélectionner l’élément de **groupe Condition** en bas de la liste des conditions pour former des conditions composées complexes.

Lorsque vous avez terminé, cliquez sur le bouton **Requête** .

Après avoir créé un filtre de base ou avancé, vous pouvez l’enregistrer à l’aide de la **requête Enregistrer** ou **Enregistrer la requête sous**. Plus tard, lorsque vous revenez à la page **Campagnes** , vous pouvez charger un filtre enregistré en cliquant sur **Paramètres de requête enregistrés**.

Pour exporter le graphique ou la liste des campagnes, cliquez sur **Exporter** et sélectionnez **Exporter les données du graphique** ou exporter la liste des **campagnes**.

Si vous avez un abonnement Microsoft Defender pour point de terminaison, vous pouvez cliquer sur **Paramètres MDE** pour connecter ou déconnecter les informations de campagnes avec Microsoft Defender pour point de terminaison. Pour plus d’informations, consultez [Intégrer Microsoft Defender pour Office 365 à Microsoft Defender pour point de terminaison](integrate-office-365-ti-with-mde.md).

## <a name="campaign-details"></a>Détails de la campagne

Lorsque vous cliquez sur le nom d’une campagne, les détails de la campagne s’affichent dans un menu volant.

### <a name="campaign-information"></a>Informations sur la campagne

En haut de l’affichage des détails de la campagne, les informations de campagne suivantes sont disponibles :

- **ID de campagne** : identificateur de campagne unique.
- **Activité** : durée et activité de la campagne.
- Les données suivantes pour le filtre de plage de dates que vous avez sélectionné (ou que vous sélectionnez dans la chronologie) :
- **Impact**
- **Messages** : nombre total de destinataires.
- **Boîte de réception** : nombre de messages qui ont été remis à la boîte de réception, et non au dossier Junk Email.
- **Lien cliqué** : nombre d’utilisateurs qui ont cliqué sur la charge utile de l’URL dans le message de hameçonnage.
- **Lien visité** : nombre d’utilisateurs qui ont visité l’URL.
- **Ciblé (%)**: pourcentage calculé par : (nombre de destinataires de la campagne dans votre organisation) / (nombre total de destinataires de la campagne dans toutes les organisations du service). Notez que cette valeur est calculée pendant toute la durée de vie de la campagne et ne change pas en fonction des filtres de dates.
- Filtres de date/heure de début et de fin pour le flux de campagne, comme décrit dans la section suivante.
- Chronologie interactive de l’activité de campagne : la chronologie montre l’activité tout au long de la durée de vie de la campagne. Vous pouvez pointer sur les points de données du graphique pour voir la quantité de messages détectés.

:::image type="content" source="../../media/campaign-details-campaign-info.png" alt-text="Informations sur la campagne" lightbox="../../media/campaign-details-campaign-info.png":::

### <a name="campaign-flow"></a>Flux de la campagne

Au milieu de la vue des détails de la campagne, des détails importants sur la campagne sont présentés dans un diagramme de flux horizontal (appelé diagramme _Sankey_ ). Ces détails vous aideront à comprendre les éléments de la campagne et l’impact potentiel au sein de votre organisation.

> [!TIP]
> Les informations affichées dans le diagramme de flux sont contrôlées par le filtre de plage de dates dans la chronologie, comme décrit dans la section précédente.

:::image type="content" source="../../media/campaign-details-no-recipient-actions.png" alt-text="Détails de la campagne qui ne contiennent pas de clics d’URL utilisateur" lightbox="../../media/campaign-details-no-recipient-actions.png":::

Si vous pointez sur une bande horizontale dans le diagramme, vous pouvez voir le nombre de messages associés (par exemple, les messages d’une adresse IP source particulière, les messages provenant de l’adresse IP source en utilisant le domaine d’expéditeur spécifié, etc.).

Le diagramme contient les informations suivantes :

- **Adresses IP de l’expéditeur**
- **Domaines de l’expéditeur**
- **Verdicts de filtre** : les valeurs de verdict sont liées aux verdicts de filtrage du hameçonnage et du courrier indésirable disponibles, comme décrit dans [les en-têtes de messages anti-courrier indésirable](anti-spam-message-headers.md). Les valeurs disponibles sont décrites dans le tableau suivant :

  |Valeur|Verdict du filtre de courrier indésirable|Description|
  |---|---|---|
  |**Autorisé**|`SFV:SKN` <p> `SFV:SKI`|Le message a été marqué comme non courrier indésirable et/ou ignoré avant d’être évalué par le filtrage du courrier indésirable. Par exemple, le message a été marqué comme non indésirable par une règle de flux de courrier (également appelée règle de transport). <p> Le message a ignoré le filtrage du courrier indésirable pour d’autres raisons. Par exemple, l’expéditeur et le destinataire semblent se trouver dans la même organisation.|
  |**Bloqué**|`SFV:SKS`|Le message a été marqué comme courrier indésirable avant d’être évalué par le filtrage du courrier indésirable. Par exemple, par une règle de flux de messagerie.|
  |**Détecté**|`SFV:SPM`|Le message a été marqué comme courrier indésirable par le filtrage du courrier indésirable.|
  |**Non détecté**|`SFV:NSPM`|Le message a été marqué comme non courrier indésirable par filtrage du courrier indésirable.|
  |**Date de publication**|`SFV:SKQ`|Le message a ignoré le filtrage du courrier indésirable, car il a été libéré de la quarantaine.|
  |**Autoriser le locataire**<sup>\*</sup>|`SFV:SKA`|Le message a ignoré le filtrage du courrier indésirable en raison des paramètres d’une stratégie anti-courrier indésirable. Par exemple, l’expéditeur se trouvait dans la liste des expéditeurs autorisés ou dans la liste des domaines autorisés.|
  |**Bloc de locataire**<sup>\*\*</sup>|`SFV:SKA`|Le message a été bloqué par le filtrage du courrier indésirable en raison des paramètres d’une stratégie anti-courrier indésirable. Par exemple, l’expéditeur se trouvait dans la liste des expéditeurs autorisés ou dans la liste des domaines autorisés.|
  |**Autoriser l’utilisateur**<sup>\*</sup>|`SFV:SFE`|Le message a ignoré le filtrage du courrier indésirable, car l’expéditeur se trouvait dans la liste des expéditeurs approuvés d’un utilisateur.|
  |**Bloc d’utilisateur**<sup>\*\*</sup>|`SFV:BLK`|Le message a été bloqué par filtrage du courrier indésirable, car l’expéditeur se trouvait dans la liste des expéditeurs bloqués d’un utilisateur.|
  |**ZAP**|s/o|[Le vidage automatique de zéro heure (ZAP)](zero-hour-auto-purge.md) a déplacé le message remis vers le dossier junk Email ou la mise en quarantaine. Vous configurez l’action dans les [stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).|

  <sup>\*</sup> Passez en revue vos stratégies anti-courrier indésirable, car le message autorisé aurait probablement été bloqué par le service.

  <sup>\*\*</sup> Passez en revue vos stratégies anti-courrier indésirable, car ces messages doivent être mis en quarantaine et non remis.

- **Destinations des messages** : vous souhaiterez probablement examiner les messages qui ont été remis aux destinataires (dans la boîte de réception ou le dossier Courrier indésirable Email), même si les utilisateurs n’ont pas cliqué sur l’URL de la charge utile dans le message. Vous pouvez également supprimer les messages mis en quarantaine de la mise en quarantaine. Pour plus d’informations, consultez [messages électroniques mis en quarantaine dans EOP](quarantine-email-messages.md).
  - **Dossier supprimé**
  - **Abandonné**
  - **Externe** : le destinataire se trouve dans votre organisation de messagerie locale dans des environnements hybrides.
  - **Échec**
  - **Transmis**
  - **Boîte de réception**
  - **Dossier Courrier indésirable**
  - **Mise en quarantaine**
  - **Unknown**

- **Clics d’URL** : ces valeurs sont décrites dans la section suivante.

> [!NOTE]
> Dans toutes les couches qui contiennent plus de 10 éléments, les 10 premiers éléments sont affichés, tandis que les autres sont regroupés dans **Autres**.

#### <a name="url-clicks"></a>Clics d’URL

Lorsqu’un message d’hameçonnage est remis au dossier Boîte de réception ou Courrier indésirable Email d’un destinataire, il est toujours possible que l’utilisateur clique sur l’URL de la charge utile. Le fait de ne pas cliquer sur l’URL est une petite mesure de réussite, mais vous devez déterminer pourquoi le message de hameçonnage a même été remis à la boîte aux lettres.

Si un utilisateur a cliqué sur l’URL de charge utile dans le message de hameçonnage, les actions sont affichées dans la zone **de clics d’URL** du diagramme dans l’affichage des détails de la campagne.

- **Autorisé**
- **BlockPage** : le destinataire a cliqué sur l’URL de la charge utile, mais son accès au site web malveillant a été bloqué par une stratégie [liens fiables](safe-links.md) dans votre organisation.
- **BlockPageOverride** : le destinataire a cliqué sur l’URL de charge utile dans le message, les liens sécurisés ont essayé de les arrêter, mais ils ont été autorisés à remplacer le bloc. Inspectez vos [stratégies de liens fiables](set-up-safe-links-policies.md) pour voir pourquoi les utilisateurs sont autorisés à remplacer le verdict liens fiables et à continuer sur le site web malveillant.
- **PendingDetonationPage** : les pièces jointes sécurisées dans Microsoft Defender pour Office 365 sont en cours d’ouverture et d’examen de l’URL de charge utile dans un environnement d’ordinateur virtuel.
- **PendingDetonationPageOverride** : le destinataire a été autorisé à remplacer le processus de détonation de charge utile et à ouvrir l’URL sans attendre les résultats.

### <a name="tabs"></a>Onglets

Les onglets de la vue détails de la campagne vous permettent d’examiner plus en détail la campagne.

> [!TIP]
> Les informations affichées sur les onglets sont contrôlées par le filtre de plage de dates dans la chronologie, comme décrit dans la section [Informations](#campaign-information) de campagne.

- **Clics sur l’URL** : si les utilisateurs n’ont pas cliqué sur l’URL de charge utile dans le message, cette section est vide. Si un utilisateur a pu cliquer sur l’URL, les valeurs suivantes sont remplies :
  - **Utilisateur**<sup>\*</sup>
  - **URL**<sup>\*</sup>
  - **Heure du clic**
  - **Cliquez sur verdict**

- **Adresses IP de l’expéditeur**
  - **IP de l’expéditeur**<sup>\*</sup>
  - **Nombre total**
  - **Boîte de réception**
  - **Non boîte de réception**
  - **SPF passé** : l’expéditeur a été authentifié par le [SPF (Sender Policy Framework).](how-office-365-uses-spf-to-prevent-spoofing.md) Un expéditeur qui ne réussit pas la validation SPF indique un expéditeur non authentifié ou le message usurpe l’identité d’un expéditeur légitime.

- **Expéditeurs**
  - **Expéditeur** : il s’agit de l’adresse réelle de l’expéditeur dans la commande SMTP MAIL FROM, qui n’est pas nécessairement l’adresse de messagerie From : que les utilisateurs voient dans leurs clients de messagerie.
  - **Nombre total**
  - **Boîte de réception**
  - **Non boîte de réception**
  - **DKIM passé** : l’expéditeur a été authentifié par [la messagerie DKIM (Domain Keys Identified Mail).](support-for-validation-of-dkim-signed-messages.md) Un expéditeur qui ne réussit pas la validation DKIM indique un expéditeur non authentifié, ou le message usurpe l’identité d’un expéditeur légitime.
  - **DMARC passé** : l’expéditeur a été authentifié par [L’authentification, la création de rapports et la conformité (DMARC) basée sur le domaine](use-dmarc-to-validate-email.md). Un expéditeur qui ne réussit pas la validation DMARC indique un expéditeur non authentifié, ou le message usurpe l’identité d’un expéditeur légitime.

- **Pièces jointes**
  - **Filename**
  - **SHA256**
  - **Famille de programmes malveillants**
  - **Nombre total**

- **URL**
  - **URL**<sup>\*</sup>
  - **Nombre total**

<sup>\*</sup> Le fait de cliquer sur cette valeur ouvre un nouveau menu mobile qui contient plus de détails sur l’élément spécifié (utilisateur, URL, etc.) au-dessus de la vue Détails de la campagne. Pour revenir à la vue Détails de la campagne, cliquez sur **Terminé** dans la nouvelle fenêtre mobile.

### <a name="buttons"></a>Boutons

Les boutons situés en bas de la vue détails de la campagne vous permettent d’examiner et d’enregistrer des détails sur la campagne :

- **Explorer les messages** : utilisez la puissance de l’Explorateur de menaces pour approfondir l’examen de la campagne :
  - **Tous les messages** : ouvre un nouvel onglet de recherche de l’Explorateur de menaces à l’aide de la valeur **d’ID de campagne** comme filtre de recherche.
  - **Messages boîte de réception** : ouvre un nouvel onglet de recherche de l’Explorateur de menaces à l’aide de **l’ID de campagne** et de l’emplacement **de remise : Boîte de réception** en tant que filtre de recherche.
  - **Messages internes** : ouvre un nouvel onglet de recherche de l’Explorateur de menaces à l’aide de **l’ID de campagne** et **de la directionnalité : Intra-org** comme filtre de recherche.

- Télécharger le rapport sur les **menaces** : Téléchargez les détails de la campagne dans un document Word (par défaut, nommé CampaignReport.docx). Notez que le téléchargement contient des détails sur toute la durée de vie de la campagne (pas seulement les dates de filtre que vous avez sélectionnées).
