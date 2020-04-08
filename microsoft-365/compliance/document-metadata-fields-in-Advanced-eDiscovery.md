---
title: Champs de métadonnées de document dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Cet article définit les champs de métadonnées pour les documents dans un ensemble de révision dans un cas dans Advanced eDiscovery dans Microsoft 365.
ms.openlocfilehash: f53a754fce482ddc0944d84059b1e346e93f5067
ms.sourcegitcommit: 053d42480d8aa3792ecb0027ddd53d383a029474
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "42941236"
---
# <a name="document-metadata-fields-in-advanced-ediscovery"></a>Champs de métadonnées de document dans Advanced eDiscovery

Le tableau suivant répertorie les champs de métadonnées pour les documents dans un ensemble de révision dans un cas dans Advanced eDiscovery. Le tableau fournit les informations suivantes :

- Nom du **champ** et **nom du champ d’affichage :** nom du champ de métadonnées et nom du champ affiché lors de l’affichage des métadonnées de fichier d’un document sélectionné dans un jeu de révision. Certains champs de métadonnées ne sont pas inclus lors de l’affichage des métadonnées de fichier d’un document. Ces champs sont mis en surbrillance avec un astérisque (*).

- **Nom du champ pouvant** faire l’objet d’une recherche : Nom de la propriété que vous pouvez rechercher lors de l’exécution d’une [requête Review Set](review-set-search.md). Une cellule vide signifie que vous ne pouvez pas rechercher le champ dans une requête d’ensemble de révision.

- **Nom du champ exporté :** Nom du champ de métadonnées qui est inclus lors de l’exportation des documents.  Une cellule vide signifie que le champ n’est pas inclus dans les métadonnées exportées.

- **Description :** Description du champ de métadonnées.

> [!NOTE]
> Le champ **Mots clés** dans la [recherche Set search](https://docs.microsoft.com/microsoft-365/compliance/review-set-search) utilise le langage de requête de mot clé (KQL). Les champs figurant dans la colonne **nom du champ** pouvant faire l’objet d’une recherche peuvent être utilisés dans le champ **Mots clés** d’une recherche de jeu de réexamen pour former des requêtes complexes sans que vous n’ayez à utiliser le générateur de requêtes. Pour plus d’informations sur KQL, voir [référence de syntaxe du langage de requête de mot clé](https://go.microsoft.com/fwlink/?LinkId=269603).

|Nom du **champ** et **nom du champ d’affichage**|**Nom de champ pouvant faire l’objet d’une recherche**|**Nom du champ exporté**|**Description**|
|:-----|:-----|:-----|:-----|
|ID de contenu de pièce jointe|AttachmentContentId||ID de contenu de la pièce jointe de l’élément.|
|Noms des pièces jointes|AttachmentNames|Attachment_Names|Liste des noms des pièces jointes.|
|Score de privilège client pour les avocats|AttorneyClientPrivilegeScore||Avocat-score de contenu du modèle de privilège client.|
|Auteur|Auteur|Doc_authors|Auteur à partir des métadonnées du document.|
|Cci|Cci|Email_bcc|Champ CCI pour les types de message. Le format **est \<DisplayName SMTPAddress>**.|
|Cc|Cc|Email_cc|Champ CC pour les types de message. Le format **est \<DisplayName SMTPAddress>**.|
|Étiquettes de conformité|ComplianceLabels|Compliance_labels|[Étiquettes de rétention](labels.md) appliquées au contenu dans Office 365.|
|Tracé transparent|CompoundPath|Compound_path|Chemin lisible par l’utilisateur qui décrit la source de l’élément.|
|Texte|Contenu||Texte extrait de l’élément.|
|Corps de la conversation|Corps de la conversation||Corps de la conversation de l’élément.|
|Sujet de conversation|Sujet de conversation||Sujet de conversation de l’élément.|
|ID de conversation|ConversationId|Conversation_ID|ID de conversation du message.|
|Index des conversations||Conversation_index|Index des conversations à partir du message.|
|Heure du fichier PDF de conversation|ConversationPdfTime||Date de création de la version PDF de la conversation.|
|Temps de gravure de la rédaction de conversation|ConversationRedactionBurnTime||Date à laquelle la version PDF de la conversation a été créée pour la conversation.|
|Date de création du document|CreatedTime|Doc_date_created|Créer une date à partir des métadonnées du document.|
|Custodian|Custodian|Custodian|Nom du dépositaire auquel l’élément a été associé.|
|Date|Date|Date|Date est un champ calculé qui dépend du type de fichier.<br /><br />Courrier électronique : date d’envoi<br />Pièces jointes de courrier électronique : date de dernière modification du document ; si elle n’est pas disponible, la date d’envoi du parent<br />Documents incorporés : date de dernière modification du document ; s’il n’est pas disponible, date de la dernière modification du parent<br />Documents SPO (y compris les pièces jointes modernes) : date de dernière modification de SharePoint ; Si non disponible, la date de la dernière modification des documents<br />Documents non-Office 365 : date de dernière modification<br />Réunions : date de début de la réunion<br />Messagerie vocale : date d’envoi<br />Messagerie instantanée : date d’envoi|
|Autres chemins d’accès|Dedupedcompoundpath|Deduped_compound_path|Liste des chemins d’accès composés de documents qui sont des doublons exactes (courrier électronique : basé sur le contenu, les documents : basé sur le hachage).|
|Autres dépositaires|DedupedCustodians|Deduped_custodians|Liste des dépositaires de documents qui sont des doublons exactes (pour la messagerie électronique, en fonction du contenu ; pour les documents, basés sur le hachage).|
|Autres ID de fichier|DedupedFileIds|Deduped_file_IDs|Liste des ID de fichier des documents qui sont des doublons exactes (pour la messagerie électronique, en fonction du contenu, en fonction du hachage).|
|Commentaires de document|DocComments|Doc_comments|Commentaires des métadonnées du document.|
|Société de document||Doc_company|Société à partir des métadonnées du document.|
|DocIndex*|||Index de la famille. **-1** ou **0** signifie qu’il s’agit de la racine.|
|Mots clés de document||Doc_keywords|Mots clés des métadonnées du document.|
|Document modifié par||Doc_modified_by|Date de dernière modification à partir des métadonnées de document.|
|Révision de document||Doc_revision|Révision des métadonnées du document.|
|Objet du document||Doc_subject|Objet des métadonnées du document.|
|Modèle de document||Doc_template|Modèle à partir des métadonnées du document.|
|Thème dominant|DominantTheme|Dominant_theme|Thème dominant calculé pour l’analyse.|
|Sous-ensemble dupliqué||Duplicate_subset|ID de groupe pour les doublons exacts.|
|EmailAction*||Email_action|Les valeurs sont **None**, **reply**ou **Forward**; en fonction de la ligne d’objet d’un message.|
|Accusé de réception de courrier électronique||Email_delivery_receipt|Adresse e-mail fournie dans les en-têtes Internet pour accusé de réception.|
|Importance|EmailImportance|Email_importance|Importance du message : **0** -faible ; **1** -normal ; **2** -haute|
|EmailLevel*||Email_level|Indique le niveau d’un message dans le thread de messagerie auquel il appartient ; les pièces jointes héritent la valeur de leur message parent.|
|ID du message électronique||Email_message_ID|ID de message Internet du message.|
|EmailReadReceipt*||Email_read_receipt|Adresse de messagerie fournie dans les en-têtes Internet pour la confirmation de lecture.|
|Sécurité de messagerie|EmailSecurity|Email_security|Paramètre de sécurité du message : **0** -aucun ; **1** -signé ; **2** -chiffrée ; **3** -chiffrés et signés.|
|Sensibilité du courrier électronique|EmailSensitivity|email_sensitivity|Paramètre de confidentialité du message : **0** -aucun ; **1** personnel ; **2** -privé ; **3** -CompanyConfidential.|
|Message électronique|EmailSet|Email_set|ID de groupe pour tous les messages dans le même groupe de courriers.|
|EmailThread*||Email_thread|Position du message dans le jeu de courriers électroniques ; se compose d’ID de nœud de la racine vers le message actuel et est séparé par des points (.).|
|Type de contenu extrait||Extracted_content_type|Type de contenu extrait sous la forme d’un type MIME ; par exemple, **image/JPEG**|
|ExtractedTextLength*||Extracted_text_length|Nombre de caractères dans le texte extrait.|
|Problème avec le score de pertinence de la famille 1 *||Family_relevance_score_case_issue_1|Pertinence du scénario de pertinence de la famille 1 par rapport à la pertinence.|
|FamilyDuplicateSet*||Family_duplicate_set|Identificateur numérique des familles qui sont des doublons exactes des uns des autres (même contenu et de toutes les mêmes pièces jointes).|
|ID de famille|FamilyId|Family_ID|ID de famille groupe tous les éléments ; pour le courrier électronique, cela inclut le message et toutes les pièces jointes ; pour les documents, cela inclut le document et tous les éléments incorporés.|
|Taille de la famille||Family_size|Nombre de documents dans la famille.|
|Pertinence du fichier casse du problème 1 *||File_relevance_score_case_issue_1|Pertinence du fichier cas du problème 1 par rapport à la pertinence.|
|Classe file|FileClass|File_class|Pour le contenu provenant de SharePoint et OneDrive : **document**; pour le contenu à partir d’Exchange : **e-mail** ou **pièce jointe**.|
|ID de fichier|FileId|File_ID|Identificateur de document unique dans le cas.|
|Date du système de fichiers créée||File_system_date_created|Date de création à partir du système de fichiers (s’applique uniquement aux données non Office 365).|
|Date du système de fichiers modifiée||File_system_date_modified|Date de modification à partir du système de fichiers (s’applique uniquement aux données non Office 365).|
|Type de fichier|FileType||Type de fichier de l’élément en fonction de l’extension de fichier.|
|Avec pièce jointe|HasAttachment|Email_has_attachment|Indique si le message contient des pièces jointes.|
|A un avocat|HasAttorney||**True** lorsqu’au moins un des participants figure dans la liste des avocats ; Sinon, la valeur est **false**.|
|Telle||Has_text|Indique si l’élément contient du texte ou non. les valeurs possibles sont **true** et **false**.|
|ID non modifiable||Immutable_ID|Cet ID est utilisé pour identifier de manière unique un document au sein d’un ensemble de révision. Ce champ ne peut pas être utilisé dans une recherche de jeu de révision et l’ID ne peut pas être utilisé pour accéder à un document dans son emplacement d’origine.|
|Type inclusif|InclusiveType|Inclusive_type|Type inclusif calculé pour l’analyse : **0** -non inclus ; **1** -inclus ; **2** -inclus moins ; copie **3** -inclusive.|
|En réponse à l’ID||In_reply_to_ID|En réponse à l’ID du message.|
|Est représentatif|IsRepresentative|Is_representative|Un document dans chaque ensemble de doublons exact est marqué comme représentatif.|
|Classe de l’élément|ItemClass|Item_class|Classe d’élément fournie par Exchange Server ; par exemple, **IPM. Note**|
|Dernière modification|LastModifiedDate|Doc_date_modified|Date de dernière modification à partir des métadonnées de document.|
|ID de chargement|LoadId|Load_ID|ID du jeu de charges dans lequel l’élément a été ajouté à un jeu de révision.|
|Emplacement|Emplacement|Emplacement|Chaîne qui indique le type d’emplacement à partir duquel les documents ont été issus.<br /><br />Données **importées** -données non Office 365<br />**Teams** -Microsoft teams<br />**Exchange** -boîtes aux lettres Exchange<br />**SharePoint** -sites SharePoint<br />**Onedrive** -comptes onedrive|
|Nom de l’emplacement|LocationName|Location_name|Chaîne qui identifie la source de l’élément. Pour Exchange, il s’agit de l’adresse SMTP de la boîte aux lettres ; pour SharePoint et OneDrive, l’URL de la collection de sites.|
|Marqué comme représentant|MarkAsRepresentative||Un document de chaque ensemble de doublons exact est marqué comme représentant.|
|Marqué comme problème pré-balisé 1 *||Marked_as_pre_tagged_Case_issue_1|Marqué comme prébalisage du problème 1 de la pertinence.|
|Marqué comme problème de cas de semence 1 *||Marked_as_seed_Case_issue_1|Marqué comme générateur de cas de générateur 1 de pertinence.|
|Date de fin de la réunion|MeetingEndDate|Meeting_end_date|Date de fin de la réunion pour les réunions.|
|Date de début de la réunion|MeetingStartDate|Meeting_start_date|Date de début de réunion pour les réunions.|
|Type de message|MessageKind|Message_kind|Type de message à rechercher. Valeurs possibles : ** <br /> <br />documents <br /> <br />de contacts <br />courrier <br />électronique <br />ExternalData <br />télécopies messagerie instantanée journaux <br />des réunions <br />microsoftteams** (renvoie des éléments de conversation, de réunions et d’appels dans Microsoft Teams) ** <br />notes <br />publie <br />RSSFeeds <br />tâches <br />de messagerie vocale**| 
|Extension Native|NativeExtension|Native_extension|Extension native de l’élément.|
|Nom de fichier natif|NativeFileName|Native_file_name|Nom de fichier natif de l’élément.|
|NativeMD5||Native_MD5|Hachage MD5 du flux de fichier.|
|ND/ET tri : exclusion des pièces jointes|NdEtSortExclAttach|ND_ET_sort_excl_attach|Concaténation du thread de courrier (ET) défini et du jeu de quasi-doublon (ND). Ce champ est utilisé pour un tri efficace lors de la révision. Un **D** est préfixé à des jeux ND et un **E** est préfixé sur et définit.|
|Tri ND/ET : pièces jointes incluses|NdEtSortInclAttach|ND_ET_sort_incl_attach|Concaténation d’une série de threads de messagerie (ET) définie et d’un jeu de quasi-doublon (ND). Ce champ est utilisé pour un tri efficace lors de la révision. Un **D** est préfixé à des jeux ND et un **E** est préfixé sur et définit. Chaque élément de messagerie dans un ET un ensemble est suivi des pièces jointes appropriées.|
|Problème 1 de cas de score de pertinence normalisé||Normalized_relevance_score_case_issue_1|Note de pertinence normalisée problème 1 par rapport à la pertinence.|
|Auteurs O365||O365_authors|Auteur à partir de SharePoint.|
|O365 créé par||O365_created_by|Créé par à partir de SharePoint.|
|Date de création d’O365||O365_date_created|Date de création à partir de SharePoint.|
|Date d’Office 365 modifiée||O365_date_modified|Date de dernière modification à partir de SharePoint.|
|O365 modifié par||O365_modified_by|Modifié par à partir de SharePoint.|
|ID parent|ParentId|Parent_ID|ID du parent de l’élément.|
|ParentNode||Parent_node|Message électronique le plus proche dans le fil de discussion.|
|Chemin d’accès parent|ParentPath|Parent_path|Chemin d’accès composé du parent direct de l’élément.|
|Domaines des participants|ParticipantDomains|Email_participant_domains|Liste de tous les domaines des participants d’un message.|
|Participants|Participants|Email_participants|Liste de tous les participants d’un message ; par exemple, expéditeur, à, CC, CCI.|
|ID de tableau croisé dynamique|PivotId|Pivot_ID|ID d’un tableau croisé dynamique.|
|Potentiellement privilégié|PotentiallyPrivileged|Potentially_privileged|True si le modèle de détection des privilèges du client estime que le document est potentiellement privilégié|
|État de traitement|ProcessingStatus|Error_code|État de traitement après l’ajout de l’élément à un jeu de révision.|
|Problème de lecture du cas pour le pourcentage 1||Read_percent_Case_issue_1|Lire le problème de cas de pourcentage 1 par rapport à la pertinence.|
|Centile en lecture|ReadPercentile||En lecture de centile pour le document en fonction de la pertinence.|
|Nombre de destinataires||Recipient_count|Nombre de destinataires dans le message.|
|Domaines de destinataires|RecipientDomains|Email_recipient_domains|Liste de tous les domaines de destinataires d’un message.|
|Destinataires|Destinataires|Email_recipients|Liste de tous les destinataires d’un message (à, CC, CCI).|
|Problème de cas de groupe de chargement de pertinence 1||Relevance_load_group_case_issue_1|Cas de groupe de chargement de pertinence 1 de pertinence.|
|Description du cas du problème 1 du statut de pertinence||Relevance_status_description_Case_issue_1|État de pertinence Description du cas problème 1 par rapport à la pertinence.|
|Problème lié à la balise de pertinence 1||Relevance_tag_case_issue_1|Balise de pertinence problème 1 par rapport à la pertinence.|
|Commentaire de pertinence||Relevance_comment|Champ de commentaire à partir de la pertinence.|
|Score de pertinence|RelevanceScore||Score de pertinence d’un document basé sur la pertinence.|
|Balise de pertinence|RelevanceTag||Score de pertinence d’un document basé sur la pertinence.|
|ID représentatif|RepresentativeId||Identificateur numérique de chaque ensemble de doublons exacts.|
|Expéditeur|Expéditeur|Email_sender|Champ sender (from) pour les types de message. Le format **est \<DisplayName SmtpAddress>**.|
|Expéditeur/auteur|SenderAuthor||Champ calculé composé de l’expéditeur ou de l’auteur de l’élément.|
|Domaine de l’expéditeur|SenderDomain|Email_sender_domain|Domaine de l’expéditeur.|
|Sent|Sent|Email_date_sent|Date d’envoi du message.|
|Ordre défini : en premier|SetOrderInclusivesFirst|Set_order_inclusives_first|Champ de tri-courrier électronique et pièces jointes : compteur-chronologique ; documents : tableau croisé dynamique, puis par décroissant de score de similarité.|
|SimilarityPercent||Similarity_percent|Indique le degré de similarité d’un document par tableau croisé dynamique du jeu presque dupliqué.|
|Taille de fichier Native|Taille|Native_size|Nombre d’octets de l’élément natif.|
|Subject|Subject|Email_subject|Objet du message.|
|Subject/title|SubjectTitle||Champ calculé constitué de l’objet ou du titre de l’élément.|
|Marqué par le problème 1||Tagged_by_Case_issue_1|Utilisateur qui a balisé ce document pour le problème 1 en pertinence.|
|Balises|Balises|Balises|Balises appliquées dans un jeu de révision.|
|Liste des thèmes|ThemesList|Themes_list|Liste des thèmes telle qu’elle est calculée pour l’analyse.|
|Titre|Titre|Doc_title|Titre des métadonnées du document.|
|À|À|Email_to|Champ à pour les types de message. Le format **est\<DisplayName SmtpAddress>**|
|Unique dans le groupe de courriers|UniqueInEmailSet||**False** s’il existe un doublon de la pièce jointe dans son jeu de courriers.|
|A été résolu|WasRemediated|Was_Remediated|**True** si l’élément a été résolu, sinon **false**.|
|Statistiques|WordCount|Word_count|Nombre de mots dans l’élément.|
|||||

> [!NOTE]
> Pour plus d’informations sur les propriétés pouvant faire l’objet d’une recherche lors de la recherche d’emplacements de contenu Office 365 lorsque vous collectez des données pour un cas avancé de découverte électronique, voir [requêtes de mots clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md).
