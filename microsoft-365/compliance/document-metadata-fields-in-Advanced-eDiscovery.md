---
title: Les champs de métadonnées des documents dans la découverte électronique
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Cet article définit les champs de métadonnées des documents dans un ensemble de révisions dans un cas dans Microsoft Purview eDiscovery (Premium) dans Microsoft 365.
ms.openlocfilehash: a6fc8479d3ecd2b89c0331220fb7f88f46bda1e4
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629748"
---
# <a name="document-metadata-fields-in-ediscovery-premium"></a>Les champs de métadonnées des documents dans la découverte électronique

Le tableau suivant répertorie les champs de métadonnées des documents dans un jeu de révision dans un cas dans Microsoft Purview eDiscovery (Premium). Le tableau fournit les informations suivantes :

- **Nom** du **champ et nom du champ d’affichage :** nom du champ de métadonnées et nom du champ affiché lors de l’affichage des métadonnées de fichier d’un document sélectionné dans un jeu de révision. Certains champs de métadonnées ne sont pas inclus lors de l’affichage des métadonnées de fichier d’un document. Ces champs sont mis en surbrillance avec un astérisque (*).

- **Nom du champ pouvant faire l’objet d’une recherche :** Nom de la propriété que vous pouvez rechercher lors de l’exécution d’une [requête d’ensemble de révision](review-set-search.md). Une cellule vide signifie que vous ne pouvez pas rechercher le champ dans une requête d’ensemble de révision.

- **Nom du champ exporté :** Nom du champ de métadonnées inclus lors de l’exportation des documents.  Une cellule vide signifie que le champ n’est pas inclus dans les métadonnées exportées.

- **Description:** Description du champ de métadonnées.

> [!NOTE]
> Le champ **Mots clés** dans la [recherche de l’ensemble de révision](./review-set-search.md) utilise le langage KQL (Keyword Query Language). Les champs répertoriés dans la colonne **Nom de champ pouvant** faire l’objet d’une recherche peuvent être utilisés dans le champ **Mots clés** d’une recherche d’ensemble de révision pour former des requêtes complexes sans avoir à utiliser le générateur de requêtes. Pour plus d’informations sur KQL, consultez la [référence de syntaxe du langage de requête](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference) de mot clé.

<br>

****

|Nom du champ et nom du champ d’affichage|Nom du champ pouvant faire l’objet d’une recherche|Nom du champ exporté|Description|
|---|---|---|---|
|ID de contenu de pièce jointe|AttachmentContentId||ID de contenu de pièce jointe de l’élément.|
|Score de privilège client d’avocat|AttorneyClientPrivilegeScore||Score de contenu du modèle de privilèges avocat-client.|
|Auteur|Auteur|Doc_authors|Créer à partir des métadonnées du document.|
|Cci|Cci|Email_bcc|Champ CCI pour les types de messages. Format **DisplayName \<SMTPAddress\>**.|
|Cc|Cc|Email_cc|Champ Cc pour les types de messages. Format **DisplayName \<SMTPAddress\>**.|
|Étiquettes de conformité|ComplianceLabels|Compliance_labels|[Étiquettes de rétention](retention.md) appliquées au contenu dans Office 365.|
|Chemin d’accès composé|CompoundPath|Compound_path|Chemin lisible par l’homme qui décrit la source de l’élément.|
|Contenu*|Content||Texte extrait de l’élément.|
|Corps de la conversation|ConversationBody||Corps de conversation de l’élément.|
|Conversation ID|ConversationId|Conversation_ID|ID de conversation du message. Pour les conversations teams 1:1 et de groupe, tous les fichiers de transcription et leurs éléments de famille dans la même conversation partagent le même ID de conversation. Pour plus d’informations, consultez le [flux de travail eDiscovery (Premium) pour le contenu dans Microsoft Teams](teams-workflow-in-advanced-ediscovery.md).|
|ID de la famille de conversations|ConversationFamilyID|ConversationFamilyID|ID qui identifie les éléments individuels d’une conversation ainsi que les éléments connexes de la conversation.|
|Conversation Index||Conversation_index|Index de conversation du message.|
|Nom de la conversation||ConversationName|Ce champ dépend du type de contenu.<br>**Conversation Teams 1:1 :** 40 premiers caractères du premier message.<br>**Conversation Teams 1:N :** Nom de la conversation de groupe ; s’il n’est pas disponible, les 40 premiers caractères du premier message.<br>**Billet de canal Teams :** Post title or announcement subhead; s’il n’est pas disponible, les 40 premiers caractères du premier message.|
|Heure pdf de la conversation|ConversationPdfTime||Date de création de la version PDF de la conversation.|
|Temps d’arrêt de la rédaction de conversation|ConversationRedactionBurnTime||Date à laquelle la version PDF de la conversation a été créée pour la conversation.|
|Rubrique de conversation|ConversationTopic||Rubrique de conversation de l’élément.|
|Conversation Type|ConversationType|ConversationType|Type de conversation de conversation. Les valeurs sont les suivantes : <br>**Conversations de groupe et teams 1:1 et toutes les conversations Yammer :** Groupe<br>**Canaux Teams et canaux privés :** Canal|
|Contient le message supprimé|ContainsDeletedMessage|ContainsDeletedMessage|Indique si la transcription de conversation inclut un message supprimé|
|Contient le message modifié|ContainsEditedMessage|ContainsEditedMessage|Indique si la transcription de conversation inclut un message modifié|
|Titre de l’annonce Teams|TeamsAnnouncementTitle|TeamsAnnouncementTitle|Titre d’une [annonce teams](https://support.microsoft.com/office/send-an-announcement-to-a-channel-8f244ea6-235a-4dcc-9143-9c5b801b4992).|
|||Converted_file_path|Chemin d’accès du fichier d’exportation converti. Pour l’utilisation interne de Microsoft uniquement.|
|Consignataire|Consignataire|Consignataire|Nom du consignateur à lequel l’élément a été associé.|
|Date|Date|Date|Date est un champ calculé qui dépend du type de fichier.<p>**E-mail** : date d’envoi<br>**Pièces jointes par e-mail** : date de dernière modification du document ; si elle n’est pas disponible, date d’envoi du parent<br>**Documents incorporés** : date de dernière modification du document ; s’il n’est pas disponible, date de la dernière modification du parent<br>**Documents SPO (y compris les pièces jointes modernes)** : date de la dernière modification du document ; s’il n’est pas disponible, date de dernière modification de SharePoint<br>**Documents non Office 365** : date de dernière modification<br>**Réunions** : date de début de la réunion<br>**Messagerie vocale** : date d’envoi<br>**MESSAGE INSTANTANÉ** : Date d’envoi<br>**Teams** : date d’envoi|
|Commentaires sur le document|DocComments|Doc_comments|Commentaires des métadonnées du document.|
|Entreprise de documents||Doc_company|Société à partir des métadonnées du document.|
|Date de création du document|CreatedTime|Doc_date_created|Créez la date à partir des métadonnées du document.|
|DocIndex*|||Index dans la famille. **-1** ou **0** signifie qu’il s’agit de la racine.|
|Mots clés de document||Doc_keywords|Mots clés des métadonnées du document.|
|Document modifié par||Doc_modified_by|Utilisateur qui a modifié le document pour la dernière fois à partir des métadonnées du document.|
|Révision de document|Doc_Version|Doc_Version|Révision à partir des métadonnées du document.|
|Objet du document||Doc_subject|Objet des métadonnées du document.|
|Modèle de document||Doc_template|Modèle à partir des métadonnées du document.|
|DocLastSavedBy||Doc_last_saved_by|Nom de l’utilisateur qui a enregistré le document pour la dernière fois.|
|Thème dominant|DominantTheme|Dominant_theme|Thème dominant tel qu’il est calculé pour l’analytique.|
|Sous-ensemble dupliqué||Duplicate_subset|ID de groupe pour les doublons exacts.|
|EmailAction*||Email_action|Les valeurs sont **None**, **Reply** ou **Forward** ; en fonction de la ligne d’objet d’un message.|
|Reçu de remise par e-mail demandé||Email_delivery_receipt|Adresse e-mail fournie dans les en-têtes Internet pour le reçu de remise.|
|Importance|EmailImportance|Email_importance|Importance du message : **0** - Faible ; **1** - Normal; **2** - Élevé|
|Erreurs de traitement ignorées|ErrorIgnored|Error_Ignored|L’erreur a été ignorée et non corrigée.|
|EmailInternetHeaders|EmailInternetHeaders|Email_internet_headers|Ensemble complet d’en-têtes d’e-mail à partir de l’e-mail|
|EmailLevel*||Email_level|Indique le niveau d’un message dans le thread de messagerie auquel il appartient ; les pièces jointes héritent de la valeur de son message parent.|
|ID de message électronique||Email_message_ID|ID de message Internet du message.|
|EmailReadReceiptRequested||Email_read_receipt|Adresse e-mail fournie dans les en-têtes Internet pour confirmation de lecture.|
|Sécurité des e-mails|EmailSecurity|Email_security|Paramètre de sécurité du message : **0** - Aucun ; **1** - Signé; **2** - Chiffré ; **3** - Chiffré et signé.|
|Confidentialité de l’e-mail|EmailSensitivity|email_sensitivity|Paramètre de confidentialité du message : **0** - Aucun ; **1** Personnel; **2** - Privé; **3** - CompanyConfidential.|
|Ensemble de courriers électroniques|EmailSet|Email_set|ID de groupe pour tous les messages du même ensemble de courriers électroniques.|
|EmailThread*||Email_thread|Position du message dans l’ensemble d’e-mails ; se compose d’ID de nœud de la racine au message actuel et sont séparés par des points (.).|
|||Export_native_path|Chemin d’accès du fichier exporté.|
|Type de contenu extrait||Native_type|Type de contenu extrait, sous forme de type mime ; par exemple, **image/jpeg**|
|||Extracted_text_path|Chemin d’accès au fichier texte extrait dans l’exportation.|
|ExtractedTextLength*||Extracted_text_length|Nombre de caractères dans le texte extrait.|
|FamilyDuplicateSet*||Family_duplicate_set|Identificateur numérique pour les familles qui sont des doublons exacts les uns des autres (même contenu et toutes les mêmes pièces jointes).|
|ID de famille|FamilyId|Family_ID|Regroupe les pièces jointes et les éléments extraits de l’e-mail et des conversations avec son élément parent. Cela inclut la conversation ou l’e-mail, ainsi que toutes les pièces jointes et éléments extraits.|
|Taille de la famille||Family_size|Nombre de documents dans la famille.|
|Classe de fichier|FileClass|File_class|Pour le contenu de SharePoint et OneDrive : **Document**. <br>Pour le contenu d’Exchange : **e-mail** ou **pièce jointe**. <br>Pour le contenu de Teams ou Yammer : **Conversations**.|
|ID de fichier|FileId|File_ID|Identificateur de document unique dans le cas.|
|Date de création du système de fichiers||File_system_date_created|Date de création à partir du système de fichiers (s’applique uniquement aux données non Office 365).|
|Date de modification du système de fichiers||File_system_date_modified|Date de modification du système de fichiers (s’applique uniquement aux données non Office 365).|
|Type de fichier|FileType||Type de fichier de l’élément basé sur l’extension de fichier.|
|ID de groupe|GroupId|Group_ID|Regroupe tous les éléments de l’e-mail et des documents. Pour l’e-mail, cela inclut le message et toutes les pièces jointes et les éléments extraits. Pour les documents, cela inclut le document et tous les éléments incorporés.|
|A une pièce jointe|EmailHasAttachment|Email_has_attachment|Indique si le message contient ou non des pièces jointes.|
|A un avocat|HasAttorney||**True** lorsqu’au moins l’un des participants est trouvé dans la liste des avocats; sinon, la valeur est **False**.|
|HasText*||Has_text|Indique si l’élément a du texte ou non ; les valeurs possibles sont **True** et **False**.|
|ID non modifiable||Immutable_ID|Cet ID est utilisé pour identifier de manière unique un document dans un ensemble de révisions. Ce champ ne peut pas être utilisé dans une recherche d’ensemble de révisions et l’ID ne peut pas être utilisé pour accéder à un document dans son emplacement natif.|
|Type inclusif|InclusiveType|Inclusive_type|Type inclusif calculé pour l’analytique : **0** - non inclusif ; **1** - inclus; **2** - inclus moins; **3** - copie inclusive.|
|Dans Répondre à l’ID||In_reply_to_ID|En réponse à l’ID du message.|
|InputFileExtension||Original_file_extension|Extension de fichier d’origine du fichier.|
|InputFileID||Input_file_ID|ID de fichier de l’élément de niveau supérieur dans le jeu de révision. Pour une pièce jointe, cet ID est l’ID du parent. Cela peut être utilisé pour regrouper des familles.|
|Pièce jointe moderne|IsModernAttachment||Ce fichier est une pièce jointe moderne ou un fichier lié.|
|Est issu de la version du document|IsFromDocumentVersion||Le document actuel est issu d’une version différente d’un autre document.|
|Pièce jointe d’e-mail|IsEmailAttachment||Cet élément est issu d’une pièce jointe d’e-mail qui s’affiche en tant qu’élément attaché au message.|
|Est inclus dans la pièce jointe|IsInlineAttachment||Ceci a été attaché inline et apparaît dans le corps du message.|
|Est représentatif|IsRepresentative|Is_representative|Un document dans chaque ensemble de doublons exacts est marqué comme représentatif.|
|Classe de l’élément|ItemClass|Item_class|Classe d’élément fournie par le serveur Exchange ; par exemple, **IPM. Note**|
|Dernière modification|LastModifiedDate|Doc_date_modified|Date de dernière modification à partir des métadonnées du document.|
|ID de chargement|LoadId|Load_ID|ID du jeu de charge dans lequel l’élément a été ajouté à un jeu de révision.|
|Emplacement|Emplacement|Emplacement|Chaîne qui indique le type d’emplacement d’origine des documents.<p>**Données importées** - Données non Office 365<br>**Teams** - Microsoft Teams<br>**Exchange** - Boîtes aux lettres Exchange<br>**SharePoint** - Sites SharePoint<br>**OneDrive** - Comptes OneDrive|
|Nom de l’emplacement|LocationName|Location_name|Chaîne qui identifie la source de l’élément. Pour l’échange, il s’agit de l’adresse SMTP de la boîte aux lettres ; pour SharePoint et OneDrive, l’URL de la collection de sites.|
|||Marked_as_pivot|Ce fichier est le tableau croisé dynamique dans un jeu de doublons proche.|
|Marqué comme représentant|MarkAsRepresentative||Un document de chaque jeu de doublons exacts est marqué comme représentant.|
|Date de fin de la réunion|MeetingEndDate|Meeting_end_date|Date de fin de la réunion pour les réunions.|
|Date de début de la réunion|MeetingStartDate|Meeting_start_date|Date de début de la réunion pour les réunions.|
|Type de message|MessageKind|Message_kind|Type de message à rechercher. Valeurs **possibles :<p> contacts docs <br><br>email <br>externaldata <br>faxes <br>im <br>journals <br>meetings <br>microsoftteams** (renvoie des éléments de conversations, de réunions et d’appels dans Microsoft Teams) **<br>notes <br>post <br>rssfeeds <br>tasks <br>voicemail**|
|ID parent de pièce jointe moderne||ModernAttachment_ParentId|ID immuable du parent du document.|
|Native Extension|NativeExtension|Native_extension|Extension native de l’élément.|
|Nom de fichier natif|NativeFileName|Native_file_name|Nom de fichier natif de l’élément.|
|NativeMD5||Native_MD5|Hachage MD5 (valeur de hachage 128 bits) du flux de fichiers.|
|NativeSHA256||Native_SHA_256|Hachage SHA256 (valeur de hachage 256 bits) du flux de fichiers.|
|Tri ND/ET : exclusion des pièces jointes|NdEtSortExclAttach|ND_ET_sort_excl_attach|Concaténation du jeu de threads d’e-mail (ET) et du jeu en quasi-double (ND). Ce champ est utilisé pour un tri efficace au moment de l’examen. Un **D** est préfixé en jeux ND et un **E** est préfixé en jeux ET.|
|Tri ND/ET : y compris les pièces jointes|NdEtSortInclAttach|ND_ET_sort_incl_attach|Concaténation d’un ensemble de threads de messagerie (ET) et d’un jeu en quasi-double (ND). Ce champ est utilisé pour un tri efficace au moment de l’examen. Un **D** est préfixé en jeux ND et un **E** est préfixé en jeux ET. Chaque élément de messagerie d’un ensemble ET est suivi de ses pièces jointes appropriées.|
|Near Duplicate Set||ND_set|Les éléments similaires au document croisé dynamique partagent les mêmes ND_set.|
|Auteurs O365||O365_authors|Créer à partir de SharePoint.|
|O365 créé par||O365_created_by|Créé à partir de SharePoint.|
|Date O365 créée||O365_date_created|Date de création à partir de SharePoint.|
|O365ModifiedDate||O365_date_modified|Date à laquelle un document (ou version de document) collecté à partir de SharePoint ou OneDrive Entreprise a été modifié. Il s’agit de la même date modifiée que celle affichée dans l’historique des versions dans l’expérience utilisateur SharePoint et OneDrive.|
|O365 modifié par||O365_modified_by|Modifié par SharePoint ou OneDrive.|
|Autres consignats|DedupedCustodians|Deduped_custodians|Liste des consignats de documents qui sont des doublons exacts (pour le courrier électronique, en fonction du contenu ; pour les documents, en fonction du hachage).|
|Autres ID de fichier|DedupedFileIds|Deduped_file_IDs|Liste des ID de fichier des documents qui sont des doublons exacts (pour l’e-mail, en fonction du contenu ; pour les documents, en fonction du hachage).|
|Autres chemins d’accès|Dedupedcompoundpath|Deduped_compound_path|Liste des chemins composés des documents qui sont des doublons exacts (e-mail : basé sur le contenu, documents : basé sur le hachage).|
|Parent ID|ParentId|Parent_ID|ID du parent de l’élément.|
|ParentNode||Parent_node|Message électronique précédent le plus proche dans le thread d’e-mail.|
|Domaines des participants|ParticipantDomains|Email_participant_domains|Liste de tous les domaines des participants d’un message.|
|Participants|Participants|Email_participants|Liste de tous les participants d’un message ; par exemple, Sender, To, Cc, CCI.|
|ID de tableau croisé dynamique|PivotId|Pivot_ID|ID d’un tableau croisé dynamique.|
|Privilèges potentiels|PotentiallyPrivileged|Potentially_privileged|True si le modèle de détection de privilèges avocat-client considère le document comme potentiellement privilégié|
|État du traitement|ProcessingStatus|Error_code|État du traitement après l’ajout de l’élément à un jeu de révision.|
|Centile de lecture|ReadPercentile||Lire le centile du document en fonction de la pertinence.|
|Received|Received|Email_date_received|Date et heure auxquelles l’e-mail a été reçu en UTC.|
|Nombre de destinataires||Recipient_count|Nombre de destinataires dans le message.|
|Domaines de destinataire|RecipientDomains|Email_recipient_domains|Liste de tous les domaines des destinataires d’un message.|
|Destinataires|Destinataires|Email_recipients|Liste de tous les destinataires d’un message (À, Cc, Cci).|
|||Redacted_file_path|Chemin d’accès du fichier de remplacement expurgé dans l’exportation.|
|||Redacted_text_path|Chemin d’accès du remplacement du fichier texte expurgé dans l’exportation. Pour l’utilisation interne de Microsoft uniquement.|
|Problème de cas de balise de pertinence 1||Relevance_tag_case_issue_1|Balise de pertinence Case issue 1 de Relevance.|
|Score de pertinence|RelevanceScore||Score de pertinence d’un document basé sur la pertinence.|
|Balise de pertinence|RelevanceTag||Score de pertinence d’un document basé sur la pertinence.|
|ID représentatif|RepresentativeId||Identificateur numérique de chaque jeu de doublons exacts.|
|||Row_number|Numéro de ligne de l’élément dans le fichier de chargement.|
|Expéditeur|Expéditeur|Email_sender|Champ Expéditeur (à partir) pour les types de messages. Format **DisplayName \<SmtpAddress>**.|
|Expéditeur/auteur|SenderAuthor||Champ calculé composé de l’expéditeur ou de l’auteur de l’élément.|
|Domaine de l’expéditeur|SenderDomain|Email_sender_domain|Domaine de l’expéditeur.|
|Sent|Sent|Email_date_sent|Date d’envoi du message.<br>Conversations : date de début de la transcription|
|Définir l’ordre : Inclusive First|SetOrderInclusivesFirst|Set_order_inclusives_first|Champ de tri - e-mail et pièces jointes : contre-chronologique; documents : pivotez d’abord, puis en décroissant le score de similarité.|
|Définir l’ID||Set_ID|Les documents de contenu similaire (ND_set) ou d’e-mail dans le même thread de messagerie (Email_set) partagent les mêmes Set_ID.|
|SimilarityPercent||Similarity_percent|Indique à quel point un document est similaire au tableau croisé dynamique du jeu en double proche.|
|Taille de fichier native|Size|Native_size|Nombre d’octets de l’élément natif.|
|Sujet|Sujet|Email_subject|Objet du message.|
|Objet/titre|SubjectTitle||Champ calculé composé de l’objet ou du titre de l’élément.|
|Balises|Balises|Balises|Balises appliquées dans un ensemble de révisions.|
|Nom du canal|Canal|ChannelName|Il s’agit du nom du canal Teams. S’applique uniquement au contenu Microsoft Teams.|
|Nom de l’équipe|TeamName|TeamName|**Équipes:** Nom de l’équipe<br>**Yammer:** Nom de la communauté|
|Liste de thèmes|ThemesList|Themes_list|Les thèmes sont répertoriés comme calculés pour l’analytique.|
|Titre|Titre|Doc_title|Titre des métadonnées du document. Titre des métadonnées du document. Pour le contenu Teams et Yammer, il s’agit de la valeur de la propriété ConversationName.|
|À|À|Email_to|Champ Pour les types de messages. Format **DisplayName\<SmtpAddress>**|
|Unique dans l’ensemble de courriers électroniques|UniqueInEmailSet||**False** s’il existe un doublon de la pièce jointe dans son jeu de courriers électroniques.|
|ID de groupe de versions||Version_Group_Id|Regroupe les différentes versions du même document.|
|VersionNumber||Version_Number|Numéro de version d’un document collecté à partir de SharePoint ou OneDrive Entreprise. Il s’agit du même numéro de version que celui affiché dans l’historique des versions dans l’expérience utilisateur SharePoint et OneDrive.|
|A été corrigé|WasRemediated|Was_Remediated|**True** si l’élément a été corrigé, sinon **False**.|
|Statistiques|WordCount|Word_count|Nombre de mots dans l’élément.|
|||||

> [!NOTE]
> Pour plus d’informations sur les propriétés pouvant faire l’objet d’une recherche lors de la recherche Office 365 emplacements de contenu lorsque vous collectez des données pour un cas eDiscovery (Premium), consultez [requêtes de mots clés et conditions de recherche de contenu](keyword-queries-and-search-conditions.md).
