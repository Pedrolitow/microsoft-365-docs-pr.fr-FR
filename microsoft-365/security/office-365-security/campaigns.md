---
title: Affichages des campagnes dans Microsoft Defender pour Office 365 plan
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: mcostea
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Découvrez les affichages campagne dans Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d1b080968675de25374019ea96e68cb6e9a63aa2fe72533759065cd4fbbc44c0
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "56854324"
---
# <a name="campaign-views-in-microsoft-defender-for-office-365"></a>Affichages des campagnes dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)

Les affichages de campagne sont une fonctionnalité de Microsoft Defender pour Office 365 Plan 2 (par exemple, Microsoft 365 E5 ou les organisations avec un module Office 365 Plan 2). Les affichages de campagne dans le Microsoft 365 Defender identifient et classent les attaques par hameçonnage dans le service. Campaign Views permet d’effectuer les opérations suivantes :

- Examiner et répondre efficacement aux attaques par hameçonnage.
- Mieux comprendre l’étendue de l’attaque.
- Afficher la valeur pour les décideurs.

Campaign Views vous permet de voir la présentation d’une attaque plus rapidement et plus complètement que n’importe quel autre utilisateur.

## <a name="what-is-a-campaign"></a>Qu’est-ce qu’une campagne ?

Une campagne est une attaque par e-mail coordonné contre une ou plusieurs organisations. Les attaques par courrier électronique qui volent des informations d’identification et des données d’entreprise sont un secteur d’activité important. À mesure que les technologies augmentent pour arrêter les attaques, les attaquants modifient leurs méthodes afin de garantir un succès continu.

Microsoft exploite les grandes quantités de données anti-hameçonnage, anti-courrier indésirable et anti-programme malveillant dans l’ensemble du service pour vous aider à identifier les campagnes. Nous analysons et classons les informations d’attaque en fonction de plusieurs facteurs. Par exemple :

- **Source de l’attaque**: adresses IP sources et domaines de messagerie de l’expéditeur.
- **Propriétés du** message : le contenu, le style et le ton des messages.
- **Destinataires du message**: lien entre les destinataires. Par exemple, les domaines des destinataires, les fonctions de travail des destinataires (administrateurs, cadres, etc.), les types d’entreprise (grandes, petites, publiques, privées, etc.) et les secteurs d’activité.
- **Charge utile d’attaque**: liens malveillants, pièces jointes ou autres charges utiles dans les messages.

Une campagne peut avoir une durée de vie courte ou s’étendre sur plusieurs jours, semaines ou mois avec des périodes actives et inactives. Une campagne peut être lancée sur votre organisation spécifique, ou votre organisation peut faire partie d’une campagne plus importante au sein de plusieurs entreprises.

## <a name="campaign-views-in-the-microsoft-365-defender-portal"></a>Affichages des campagnes dans le portail Microsoft 365 Defender web

Les affichages de campagne sont disponibles dans le portail Microsoft 365 Defender ( ) sur la & campagnes de <https://security.microsoft.com> **collaboration,** ou directement \> à <https://security.microsoft.com/campaigns> l’adresse .

![Vue d’ensemble des campagnes dans Microsoft 365 Defender web](../../media/campaigns-overview.png)

Vous pouvez également obtenir les affichages campagne à partir des points de vue de campagne :

- **Collaboration par & messagerie** \> **Explorateur** \> **Affichage** \> **Campagnes**
- **Collaboration par & messagerie** \> **Explorateur** \> **Affichage** \> **Tous les e-mails** \> **Onglet Campagne**
- **Collaboration par & messagerie** \> **Explorateur** \> **Affichage** \> **Hameçonnage** \> **Onglet Campagne**
- **Collaboration par & messagerie** \> **Explorateur** \> **Affichage** \> **Programmes malveillants** \> **Onglet Campagne**

Pour accéder aux affichages campagne, vous devez être membre  des groupes de rôles Gestion de l’organisation, Administrateur de la sécurité ou Lecteur sécurité dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

## <a name="campaigns-overview"></a>Vue d’ensemble des campagnes

La page vue d’ensemble affiche des informations sur toutes les campagnes.

Sous l’onglet **Campagne** par défaut, la zone **Type** de campagne affiche un graphique à barres qui indique le nombre de destinataires par jour. Par défaut, le graphique affiche les données **de** hameçonnage et **de programmes** malveillants.

> [!TIP]
> Si vous ne voyez pas de données de campagne, essayez de modifier la plage de dates ou les [filtres.](#filters-and-settings)

Le tableau sous le graphique de la page vue d’ensemble affiche les informations suivantes sous **l’onglet** Campagne :

- **Nom**

- **Exemple d’objet** : la ligne d’objet de l’un des messages de la campagne. Notez que tous les messages de la campagne n’auront pas nécessairement le même objet.

- **Ciblé**: pourcentage calculé par : (nombre de destinataires de la campagne dans votre organisation) / (nombre total de destinataires de la campagne dans toutes les organisations du service). Cette valeur indique le degré auquel la campagne s’adresse uniquement à votre organisation (une valeur supérieure) ou à d’autres organisations dans le service (une valeur inférieure).

- **Type**: cette valeur est **hameçonnage** ou **programme malveillant.**

- **Sous-type**: cette valeur contient plus de détails sur la campagne. Par exemple :
  - **Hameçonnage**: si disponible, marque faisant l’objet d’un hameçonnage par cette campagne. Par exemple, `Microsoft` , `365` , ou `Unknown` `Outlook` `DocuSign` .
  - **Programme** malveillant : par exemple, `HTML/PHISH` ou `HTML/<MalwareFamilyName>` .

  Si disponible, la marque faisant l’objet d’un hameçonnage par cette campagne. Lorsque la détection est pilotée par Defender pour Office 365 technologie, le préfixe **ATP-** est ajouté à la valeur de sous-type.

- **Destinataires** : nombre d’utilisateurs qui ont été ciblés par cette campagne.

- **Boîte de réception :** nombre d’utilisateurs qui ont reçu des messages de cette campagne dans leur boîte de réception (non remis dans leur dossier Courrier indésirable).

- **Clicked**: nombre d’utilisateurs qui ont cliqué sur l’URL ou ouvert la pièce jointe dans le message d’hameçonnage.

- **Taux de** clic : pourcentage calculé par «**Boîte de**  /  **réception cliquée**». Cette valeur est un indicateur de l’efficacité de la campagne. En d’autres termes, si les destinataires ont pu identifier le message comme hameçonnage et s’ils n’ont pas cliqué sur l’URL de la charge utile.

  Notez que **le taux de clics** n’est pas utilisé dans les campagnes anti-programme malveillant.

- **Visité :** nombre d’utilisateurs qui ont réellement effectué l’accès au site web de charge utile. S’il existe **des valeurs Clicked,** mais Coffre liens ont bloqué l’accès au site web, cette valeur est zéro.

**L’onglet Origine** de la campagne affiche les sources des messages sur une carte du monde.

### <a name="filters-and-settings"></a>Filtres et paramètres

En haut de la page **Campagne,** plusieurs paramètres de filtre et de requête vous permettent de rechercher et d’isoler des campagnes spécifiques.

![Filtres de campagne](../../media/campaign-filters-and-settings.png)

Le filtrage le plus simple que vous pouvez faire est la date/l’heure de début et la date/heure de fin.

Pour filtrer davantage l’affichage, vous pouvez effectuer un filtrage de propriété unique avec plusieurs valeurs en cliquant sur le bouton **Type** de campagne, en sélectionnant, puis en cliquant sur **Actualiser**.

Les propriétés filtrables de campagne disponibles dans le bouton **Type** de campagne sont décrites dans la liste suivante :

- **De base**:
  - **Type de campagne**: sélectionner un **programme malveillant ou** un **hameçonnage.** La suppression des sélections a le même résultat que la sélection des deux.
  - **Nom de la campagne**
  - **Sous-type de campagne**
  - **Expéditeur**
  - **Destinataires**
  - **Domaine de l’expéditeur**
  - **Subject**
  - **Nom de fichier des pièces jointes**
  - **Famille de programmes malveillants**
  - **Balises**: utilisateurs ou groupes pour lesquels la balise utilisateur spécifiée a été appliquée (y compris les comptes de priorité). Pour plus d’informations sur les balises utilisateur, voir [Balises utilisateur.](user-tags.md)
  - **Action de remise**
  - **Action supplémentaire**
  - **Orientation**
  - **Technologie de détection**
  - **Emplacement de remise d’origine**
  - **Emplacement de remise le plus récent**
  - **Remplacements système**

- **Avancé**:
  - **ID de message Internet**: disponible dans le champ d’en-tête **Message-ID** de l’en-tête du message. Un exemple de valeur est `<08f1e0f6806a47b4ac103961109ae6ef@server.domain>` (notez les crochets).
  - **ID de message** réseau : valeur GUID disponible dans le champ d’en-tête **X-MS-Exchange-Organization-Network-Message-Id** dans l’en-tête du message.
  - **IP de l’expéditeur**
  - **Pièce jointe SHA256**: pour rechercher la valeur de hachage SHA256 d’un fichier dans Windows, exécutez la commande suivante dans une invite de commandes : `certutil.exe -hashfile "<Path>\<Filename>" SHA256` .
  - **Cluster ID**
  - **ID d’alerte**
  - **ID de stratégie d’alerte**
  - **ID de campagne**
  - **Signal d’URL ZAP**

- **URL**:
  - **Domaine d’URL**
  - **Domaine et chemin d’accès d’URL**
  - **URL**
  - **Chemin d’URL**
  - **Cliquez sur verdict**

Pour un filtrage plus avancé, y compris le  filtrage par plusieurs propriétés, vous pouvez cliquer sur le bouton Filtre avancé pour créer une requête. Les mêmes propriétés de campagne sont disponibles, mais avec les améliorations suivantes :

- Vous pouvez cliquer **sur Ajouter une condition pour** sélectionner plusieurs conditions.
- Vous pouvez choisir l’opérateur **And** ou **Or** entre les conditions.
- Vous pouvez sélectionner **l’élément de groupe Condition** en bas de la liste des conditions pour former des conditions composées complexes.

Lorsque vous avez terminé, cliquez sur **le bouton Requête.**

Après avoir créé un filtre de base ou  avancé, vous pouvez l’enregistrer à l’aide de la requête Enregistrer ou enregistrer **la requête sous**. Plus tard, lorsque vous revenirz à la page **Campagnes,** vous pouvez charger un filtre enregistré en cliquant sur **Paramètres de requête enregistrés.**

Pour exporter le graphique ou la liste des campagnes, cliquez sur **Exporter** et sélectionnez Exporter les données **du graphique** ou Exporter la liste **des campagnes.**

Si vous avez un abonnement Microsoft Defender pour les points de terminaison, vous pouvez cliquer sur **MDE Paramètres** pour connecter ou déconnecter les informations des campagnes avec Microsoft Defender for Endpoint. Pour plus d’informations, voir [Intégrer Microsoft Defender pour Office 365 microsoft Defender pour le point de terminaison.](integrate-office-365-ti-with-mde.md)

## <a name="campaign-details"></a>Détails de la campagne

Lorsque vous cliquez sur le nom d’une campagne, les détails de la campagne apparaissent dans un volant.

### <a name="campaign-information"></a>Informations sur la campagne

En haut de l’affichage Détails de la campagne, les informations de campagne suivantes sont disponibles :

- **ID de campagne :** identificateur de campagne unique.
- **Activité**: durée et activité de la campagne.
- Les données suivantes pour le filtre de plage de dates que vous avez sélectionné (ou que vous sélectionnez dans la chronologie) :
- **Impact**
- **Messages**: nombre total de destinataires.
- **Boîte de réception :** nombre de messages qui ont été remis à la boîte de réception, et non au dossier Courrier indésirable.
- **Lien cliqué :** nombre d’utilisateurs qui ont cliqué sur la charge utile de l’URL dans le message d’hameçonnage.
- **Lien visité :** nombre d’utilisateurs qui ont visité l’URL.
- **Ciblé (%)**: pourcentage calculé par : (nombre de destinataires de la campagne dans votre organisation) / (nombre total de destinataires de la campagne dans toutes les organisations du service). Notez que cette valeur est calculée sur toute la durée de vie de la campagne et ne change pas en fonction des filtres de date.
- Filtres de date/heure de début et de fin des données/heure pour le flux de campagne, comme décrit dans la section suivante.
- Chronologie interactive de l’activité de la campagne : la chronologie affiche l’activité tout au long de la durée de vie de la campagne. Vous pouvez pointer sur les points de données dans le graphique pour voir la quantité de messages détectés.

![Informations sur la campagne](../../media/campaign-details-campaign-info.png)

### <a name="campaign-flow"></a>Flux de la campagne

Au milieu de l’affichage Détails de la campagne, des détails importants sur la campagne sont présentés dans un diagramme de flux horizontal (appelé diagramme _Sankey)._ Ces détails vous aideront à comprendre les éléments de la campagne et l’impact potentiel au sein de votre organisation.

> [!TIP]
> Les informations affichées dans le diagramme de flux sont contrôlées par le filtre de plage de dates dans la chronologie, comme décrit dans la section précédente.

![Détails de la campagne ne contenant pas d’URL d’utilisateur](../../media/campaign-details-no-recipient-actions.png)

Si vous pointez sur une bande horizontale dans le diagramme, vous pouvez voir le nombre de messages associés (par exemple, les messages d’une adresse IP source particulière, les messages provenant de l’adresse IP source en utilisant le domaine d’expéditeur spécifié, etc.).

Le diagramme contient les informations suivantes :

- **Adresses IP de l’expéditeur**
- **Domaines de l’expéditeur**
- **Verdicts de filtre**: les valeurs de verdict sont liées aux verdicts de filtrage du courrier indésirable et du hameçonnage disponibles, comme décrit dans les [en-têtes de message anti-courrier indésirable.](anti-spam-message-headers.md) Les valeurs disponibles sont décrites dans le tableau suivant :

  <br>

  ****

  |Valeur|Verdict du filtre anti-courrier indésirable|Description|
  |---|---|---|
  |**Autorisé**|`SFV:SKN` <p> `SFV:SKI`|Le message a été marqué comme n’étant pas du courrier indésirable et/ou a ignoré le filtrage avant d’être évalué par le filtrage du courrier indésirable. Par exemple, le message a été marqué comme n’étant pas un courrier indésirable par une règle de flux de messagerie (également appelée règle de transport). <p> Le message a ignoré le filtrage du courrier indésirable pour d’autres raisons. Par exemple, l’expéditeur et le destinataire semblent se trouver dans la même organisation.|
  |**Bloqué**|`SFV:SKS`|Le message a été marqué comme courrier indésirable avant d’être évalué par le filtrage du courrier indésirable. Par exemple, par une règle de flux de messagerie.|
  |**Détecté**|`SFV:SPM`|Le message a été marqué comme courrier indésirable par le filtrage du courrier indésirable.|
  |**Non détecté**|`SFV:NSPM`|Le message a été marqué comme n’étant pas un courrier indésirable par filtrage du courrier indésirable.|
  |**Released**|`SFV:SKQ`|Le message a ignoré le filtrage du courrier indésirable car il a été libéré de la quarantaine.|
  |**Autoriser le client**<sup>\*</sup>|`SFV:SKA`|Le message a ignoré le filtrage du courrier indésirable en raison des paramètres d’une stratégie anti-courrier indésirable. Par exemple, l’expéditeur se trouvait dans la liste des expéditeurs autorisés ou dans la liste des domaines autorisés.|
  |**Bloc de client**<sup>\*\*</sup>|`SFV:SKA`|Le message a été bloqué par le filtrage du courrier indésirable en raison des paramètres d’une stratégie anti-courrier indésirable. Par exemple, l’expéditeur se trouvait dans la liste des expéditeurs autorisés ou dans la liste des domaines autorisés.|
  |**Autoriser l’utilisateur**<sup>\*</sup>|`SFV:SFE`|Le message a ignoré le filtrage du courrier indésirable, car l’expéditeur se trouvait dans la liste des Coffre d’un utilisateur.|
  |**Blocage de l’utilisateur**<sup>\*\*</sup>|`SFV:BLK`|Le message a été bloqué par le filtrage du courrier indésirable car l’expéditeur se trouvait dans la liste des expéditeurs bloqués d’un utilisateur.|
  |**ZAP**|s/o|[La purge automatique de zéro heure (ZAP)](zero-hour-auto-purge.md) a déplacé le message remis dans le dossier Courrier indésirable ou mis en quarantaine. Vous configurez l’action dans votre stratégie anti-courrier indésirable.|
  |

  <sup>\*</sup> Examinez vos stratégies anti-courrier indésirable, car le message autorisé aurait probablement été bloqué par le service.

  <sup>\*\*</sup> Examinez vos stratégies anti-courrier indésirable, car ces messages doivent être mis en quarantaine et non remis.

- **Destinations des messages**: vous souhaiterez probablement examiner les messages qui ont été remis aux destinataires (dans la boîte de réception ou dans le dossier Courrier indésirable), même si les utilisateurs n’ont pas cliqué sur l’URL de la charge utile dans le message. Vous pouvez également supprimer les messages mis en quarantaine de la quarantaine. Pour plus d’informations, voir [Messages électroniques mis en quarantaine dans EOP.](quarantine-email-messages.md)
  - **Dossier supprimé**
  - **Dropped**
  - **Externe**: le destinataire se trouve dans votre organisation de messagerie sur site dans des environnements hybrides.
  - **Échec**
  - **Forwarded**
  - **Boîte de réception**
  - **Dossier Courrier indésirable**
  - **Mise en quarantaine**
  - **Unknown**

- **Clics d’URL**: ces valeurs sont décrites dans la section suivante.

> [!NOTE]
> Dans toutes les couches qui contiennent plus de 10 éléments, les 10 premiers éléments sont affichés, tandis que les autres sont regroupés dans **d’autres**.

#### <a name="url-clicks"></a>Clics d’URL

Lorsqu’un message de hameçonnage est remis dans la boîte de réception ou le dossier Courrier indésirable d’un destinataire, il est toujours possible que l’utilisateur clique sur l’URL de la charge utile. Ne pas cliquer sur l’URL est une petite mesure de réussite, mais vous devez déterminer pourquoi le message de hameçonnage a même été remis à la boîte aux lettres.

Si un utilisateur a cliqué sur l’URL de la charge utile dans le message d’hameçonnage, les actions s’affichent dans la zone de **clics de l’URL** du diagramme dans l’affichage Détails de la campagne.

- **Autorisé**
- **BlockPage**: le destinataire [a](safe-links.md) cliqué sur l’URL de la charge utile, mais son accès au site web malveillant a été bloqué par une stratégie de liens Coffre dans votre organisation.
- **BlockPageOverride**: le destinataire a cliqué sur l’URL de la charge utile dans le message, Coffre Links a tenté de les arrêter, mais il a été autorisé à remplacer le bloc. Examinez vos [stratégies Coffre liens](set-up-safe-links-policies.md) pour voir pourquoi les utilisateurs sont autorisés à remplacer le verdict Coffre liens et à continuer vers le site web malveillant.
- **PendingDetonationPage**: Coffre pièces jointes dans Microsoft Defender pour Office 365 est en cours d’ouverture et d’examen de l’URL de charge utile dans un environnement d’ordinateur virtuel.
- **PendingDetonationPageOverride**: le destinataire a été autorisé à remplacer le processus de détonation de la charge utile et à ouvrir l’URL sans attendre les résultats.

### <a name="tabs"></a>Onglets

Les onglets de l’affichage Détails de la campagne vous permettent d’examiner plus en détail la campagne.

> [!TIP]
> Les informations affichées dans les onglets sont contrôlées par le filtre de plage de dates dans la chronologie, comme décrit dans la section [Informations sur la](#campaign-information) campagne.

- **Url clicks**: If users didn’t click on the payload URL in the message, this section will be blank. Si un utilisateur a pu cliquer sur l’URL, les valeurs suivantes sont remplies :
  - **Utilisateur**<sup>\*</sup>
  - **URL**<sup>\*</sup>
  - **Temps de clic**
  - **Cliquez sur verdict**

- **Adresses IP de l’expéditeur**
  - **IP de l’expéditeur**<sup>\*</sup>
  - **Nombre total**
  - **Boîte de réception**
  - **Non boîte de réception**
  - **SPF transmis**: l’expéditeur a été authentifié par le [SPF (Sender Policy Framework).](how-office-365-uses-spf-to-prevent-spoofing.md) Un expéditeur qui ne passe pas la validation SPF indique un expéditeur non authentifié ou le message usurpe un expéditeur légitime.

- **Expéditeurs**
  - **Expéditeur :** il s’agit de l’adresse de l’expéditeur réelle dans la commande SMTP MAIL FROM, qui n’est pas nécessairement l’adresse de messagerie De : que les utilisateurs voient dans leurs clients de messagerie.
  - **Nombre total**
  - **Boîte de réception**
  - **Non boîte de réception**
  - **DKIM transmis**: l’expéditeur a été authentifié par [DKIM (Domain Keys Identified Mail).](support-for-validation-of-dkim-signed-messages.md) Un expéditeur qui ne passe pas la validation DKIM indique un expéditeur non authentifié ou le message usurpe un expéditeur légitime.
  - **DMARC transmis**: l’expéditeur a été authentifié par l’authentification de message basée sur le domaine, la rapport et [la conformité (DMARC)](use-dmarc-to-validate-email.md). Un expéditeur qui ne passe pas la validation DMARC indique un expéditeur non authentifié ou le message usurpe un expéditeur légitime.

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

Les boutons situés en bas de l’affichage Détails de la campagne vous permettent d’examiner et d’enregistrer des détails sur la campagne :

- **Explorer les messages**: utilisez la puissance de l’Explorateur de menaces pour examiner plus en détail la campagne :
  - **Tous les messages**: ouvre un nouvel onglet de recherche de l’Explorateur de menaces en utilisant la valeur **ID** de campagne comme filtre de recherche.
  - **Messages de la boîte de** réception : ouvre un nouvel  onglet de recherche de l’Explorateur de menaces à l’aide de **l’ID** de campagne et de l’emplacement de remise : Boîte de réception comme filtre de recherche.
  - **Messages internes**: ouvre un nouvel onglet de recherche de l’Explorateur de menaces à l’aide de l’ID de campagne et de la **direction : intra-organisationnelle** comme filtre de recherche. 

- **Télécharger le rapport sur les** menaces : téléchargez les détails de la campagne dans un document Word (par défaut, nommé CampaignReport.docx). Notez que le téléchargement contient des détails tout au long de la durée de vie de la campagne (pas seulement les dates de filtre que vous avez sélectionnées).
