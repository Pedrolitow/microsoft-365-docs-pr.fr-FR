---
title: Demandes Customer Lockbox
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
search.appverid:
- BCS160
- MET150
- MOE150
ms.custom: admindeeplinkMAC
description: Découvrez les demandes Customer Lockbox qui vous permettent de contrôler la façon dont un ingénieur du support Technique Microsoft peut accéder à vos données lorsque vous rencontrez un problème.
ms.openlocfilehash: cf9a2a6d682ca87e97986389f640a536775ca014
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953823"
---
# <a name="microsoft-purview-customer-lockbox"></a>Microsoft Purview Customer Lockbox

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Cet article fournit des conseils de déploiement et de configuration pour Customer Lockbox. Customer Lockbox prend en charge les demandes d’accès aux données dans Exchange Online, SharePoint Online, OneDrive Entreprise et Teams. Pour recommander la prise en charge d’autres services, envoyez une demande sur le [portail de commentaires](https://feedbackportal.microsoft.com).

Pour voir les options de licence permettant à vos utilisateurs de tirer parti des offres Microsoft Purview, consultez les [Microsoft 365 conseils de gestion des licences pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

Customer Lockbox garantit que Microsoft ne peut pas accéder à votre contenu pour effectuer des opérations de service sans votre approbation explicite. Customer Lockbox vous permet d’entrer dans le processus de flux de travail d’approbation utilisé par Microsoft pour vous assurer que seules les demandes autorisées autorisent l’accès à votre contenu. Pour en savoir plus sur le processus de flux de travail de Microsoft, consultez [Privileged Access Management](privileged-access-management-solution-overview.md).

Parfois, les ingénieurs Microsoft aident à résoudre les problèmes qui surviennent avec le service. En règle générale, les ingénieurs corrigent les problèmes à l’aide d’outils de télémétrie et de débogage étendus mis en place par Microsoft pour ses services. Toutefois, dans certains cas, un ingénieur Microsoft doit accéder à votre contenu pour déterminer la cause racine et résoudre le problème. Customer Lockbox exige que l’ingénieur vous demande l’accès en tant que dernière étape du flux de travail d’approbation. Cela vous donne la possibilité d’approuver ou de refuser la demande pour votre organisation, et de fournir un contrôle d’accès direct à votre contenu.

## <a name="customer-lockbox-overview-video"></a>Vidéo de vue d’ensemble de Customer Lockbox

> [!VIDEO https://www.microsoft.com/videoplayer/embed/8fecf10b-1f03-4849-8b67-76d3d2a43f26?autoplay=false]

## <a name="customer-lockbox-workflow"></a>Flux de travail Customer Lockbox

Ces étapes décrivent le flux de travail classique lorsqu’un ingénieur Microsoft démarre une demande Customer Lockbox :

1. Une personne d’une organisation rencontre un problème avec sa boîte aux lettres Microsoft 365.

2. Si l’utilisateur trouve la solution au problème, mais qu’il ne parvient pas à le corriger, il envoie une demande d’assistance au Support Microsoft.

3. Un ingénieur du support Microsoft examine la demande de service et détermine la nécessité d’accéder au locataire de l’organisation pour réparer le problème.

4. L’ingénieur du Support Microsoft se connecte à l’outil de demande Customer Lockbox et effectue une demande d’accès aux données incluant le nom du client de l’organisation, le numéro de la demande de service et la durée pendant laquelle l’ingénieur doit accéder aux données.

5. Une fois la demande approuvée par le gestionnaire du support technique Microsoft, Customer Lockbox envoie à l’approbateur désigné dans l’organisation une notification par e-mail concernant la demande d’accès en attente de Microsoft.

    ![Exemple de notification par e-mail Customer Lockbox.](../media/CustomerLockbox1.png)

   Toute personne qui se voit attribuer le rôle d’administrateur [d’approbateur d’accès Customer Lockbox](/office365/admin/add-users/about-admin-roles) dans Centre d'administration Microsoft 365 peut approuver les demandes Customer Lockbox.

6. L’approbateur se connecte au Centre d'administration Microsoft 365 et approuve la demande. Cette étape déclenche la création d’un enregistrement d’audit disponible en effectuant une recherche dans le journal d’audit. Pour plus d’informations, consultez [Auditer les demandes Customer Lockbox](#auditing-customer-lockbox-requests).

   Si le client rejette la demande ou n’approuve pas la demande dans les 12 heures, la demande expire et aucun accès n’est accordé à l’ingénieur Microsoft.

   > [!IMPORTANT]
   > Microsoft n’inclut aucun lien dans les notifications par e-mail Customer Lockbox vous demandant de vous connecter à Office 365.

7. Une fois que l’approbateur de l’organisation a approuvé la demande, l’ingénieur Microsoft reçoit le message d’approbation, se connecte au locataire et résout le problème du client. Les ingénieurs Microsoft ont la durée demandée pour résoudre le problème après lequel l’accès est automatiquement révoqué.

> [!NOTE]
> Chaque action effectuée par un ingénieur Microsoft est enregistrée dans le journal d’audit. Vous pouvez rechercher et consulter ces enregistrements d’audit.

## <a name="turn-customer-lockbox-requests-on-or-off"></a>Activer ou désactiver les demandes Customer Lockbox

Vous pouvez activer les contrôles Customer Lockbox dans le Centre d’administration Microsoft 365. Lorsque vous activez Customer Lockbox, Microsoft doit obtenir l’approbation de votre organisation avant d’accéder au contenu de votre locataire.

1. À l’aide d’un compte professionnel ou scolaire auquel est attribué l’administrateur général ou le rôle **d’approbateur d’accès Customer Lockbox** , accédez à [https://admin.microsoft.com](https://admin.microsoft.com) et connectez-vous.

2. Choisissez **Paramètres** >  **Org Paramètres** >  **Security & Privacy**.

3. Sélectionnez **Sécurité & Confidentialité**, puis **Customer Lockbox** dans la colonne de gauche. Cochez la case **Exiger l’approbation de toutes les demandes d’accès aux données** et enregistrez les modifications pour activer la fonctionnalité.

    ![Require approval for Customer Lockbox](../media/CustomerLockbox4-new.png)

## <a name="approve-or-deny-a-customer-lockbox-request"></a>Approuver ou refuser une demande d’accès au Customer Lockbox

1. À l’aide d’un compte professionnel ou scolaire auquel est attribué l’administrateur général ou le rôle **d’approbateur d’accès Customer Lockbox** , accédez à [https://admin.microsoft.com](https://admin.microsoft.com) et connectez-vous.

2. Choisissez **Support > Customer Lockbox Requests**.

    ![Cliquez sur Support, puis sur Demandes Customer Lockbox.](../media/CustomerLockbox5.png)

    Une liste des demandes Customer Lockbox s’affiche.

    ![Liste des demandes Customer Lockbox.](../media/CustomerLockbox6.png)

3. Sélectionnez une demande Customer Lockbox, puis **choisissez Approuver** ou **Refuser**.

    ![Approuver les demandes Customer Lockbox.](../media/CustomerLockbox7.png)

    Un message de confirmation concernant l’approbation de la demande Customer Lockbox s’affiche.

    ![Refuser les demandes Customer Lockbox.](../media/CustomerLockbox8.png)

> [!NOTE]
> Utilisez l’applet de commande Set-AccessToCustomerDataRequest pour approuver, refuser ou annuler les demandes Microsoft Purview Customer Lockbox qui contrôlent l’accès à vos données par les ingénieurs du support technique Microsoft. Pour plus d’informations, consultez [Set-AccessToCustomerDataRequest](/powershell/module/exchange/set-accesstocustomerdatarequest).

## <a name="auditing-customer-lockbox-requests"></a>Audit des demandes d’accès au Customer Lockbox

Les enregistrements d’audit qui correspondent aux demandes Customer Lockbox sont enregistrés dans le journal d’audit Microsoft 365. Vous pouvez accéder à ces journaux à l’aide de [l’outil de recherche de journaux d’audit](search-the-audit-log-in-security-and-compliance.md) dans le portail de conformité Microsoft Purview. Les actions liées à l’acceptation ou au refus d’une demande Customer Lockbox et les actions effectuées par les ingénieurs Microsoft (lorsque les demandes d’accès sont approuvées) sont également consignées dans le journal d’audit. Vous pouvez rechercher et consulter ces enregistrements d’audit.

### <a name="search-the-audit-log-for-activity-related-to-customer-lockbox-requests"></a>Recherchez dans le journal d’audit l’activité liée aux demandes Customer Lockbox

Avant de pouvoir utiliser le journal d’audit pour suivre les demandes de Customer Lockbox, vous devez effectuer certaines étapes pour configurer la journalisation d’audit, notamment l’attribution d’autorisations pour rechercher dans le journal d’audit. Pour plus d’informations, consultez [Configurer l’audit Microsoft Purview (Standard).](set-up-basic-audit.md) Une fois que vous avez terminé la configuration, procédez comme suit pour créer une requête de recherche dans le journal d’audit afin de retourner les enregistrements d’audit liés à Customer Lockbox :

1. Accédez à <https://compliance.microsoft.com>.
  
2. Connectez-vous à l’aide d’un compte qui a reçu les autorisations appropriées pour effectuer une recherche dans le journal d’audit.

3. Dans le volet gauche du centre de conformité, choisissez **Audit**.

    L’onglet **Rechercher** de la page **Audit** s’affiche.

    ![Page de recherche dans les journaux d’audit.](../media/auditlogsearch1.png)
  
4. Configurez les critères de recherche suivants : 

   1. **Date de début** et **date de fin**. Sélectionnez une plage de dates et d’heures pour afficher les événements survenus pendant cette période.  

   2. **Activités**. Laissez ce champ vide afin que la recherche retourne des enregistrements d’audit pour toutes les activités. Cela est nécessaire pour retourner les enregistrements d’audit liés aux demandes Customer Lockbox et à l’activité correspondante effectuée par les ingénieurs Microsoft.

   3. **Utilisateurs**. Laissez ce champ vide.

   4. **Fichier, dossier ou site**. Laissez ce champ vide.

5. Cliquez sur **Rechercher** pour effectuer la recherche à l’aide de vos critères de recherche. 

    Les résultats de la recherche s’affichent après quelques instants. D’autres résultats de recherche seront ajoutés à la page jusqu’à ce que la recherche soit terminée.

6. Cliquez sur l’en-tête dans la colonne **Activité** pour trier les résultats par ordre alphabétique en fonction des valeurs de la colonne **Activité** .

7. Faites défiler vers le bas et recherchez les enregistrements d’audit avec une activité **de Set-AccessToCustomerDataRequest**. Les enregistrements avec cette activité sont liés à un approbateur de votre organisation qui approuve ou refuse une demande Customer Lockbox.

8. Vous pouvez également cliquer sur l’en-tête dans la colonne **Utilisateur** pour trier les résultats par ordre alphabétique à l’aide des valeurs de la colonne **Utilisateur** . Recherchez la valeur de **l’opérateur Microsoft**, qui indique les activités effectuées par un ingénieur Microsoft en réponse à une demande Customer Lockbox approuvée. La colonne **Activité** affiche l’action effectuée par l’ingénieur.

      ![Filtrer sur « Opérateur Microsoft » pour afficher les enregistrements d’audit](../media/CustomerLockbox10.png)

9. Dans la liste des résultats, cliquez sur un enregistrement d’audit pour l’afficher.

### <a name="export-the-audit-log-search-results"></a>Exporter les résultats de la recherche dans le journal d’audit

Vous pouvez également exporter les résultats de la recherche dans le journal d’audit vers un fichier CSV, puis ouvrir le fichier dans Excel pour utiliser les fonctionnalités de filtrage et de tri afin de faciliter la recherche et l’affichage des enregistrements d’audit liés à une demande d’accès Customer Lockbox.

Pour exporter des enregistrements d’audit, suivez les étapes précédentes pour rechercher dans le journal d’audit. Une fois la recherche terminée, sélectionnez **Exporter > Télécharger tous les résultats** en haut de la page des résultats de la recherche. Une fois le processus d’exportation terminé, vous pouvez télécharger le fichier CSV sur votre ordinateur local. Pour obtenir des instructions plus détaillées, consultez [Exporter, configurer et afficher les enregistrements du journal d’audit](export-view-audit-log-records.md).

Après avoir téléchargé le fichier, vous pouvez l’ouvrir dans Excel, puis filtrer sur la colonne **Opérations** pour afficher les enregistrements d’audit pour les activités **Set-AccessToCustomerDataRequest**. Vous pouvez également filtrer sur la colonne **UserIds** (à l’aide de la valeur **Opérateur Microsoft**) pour afficher les enregistrements d’audit des activités effectuées par les ingénieurs Microsoft.

> [!NOTE]
> Lors de l’affichage des enregistrements d’audit dans le fichier CSV, des informations supplémentaires sont contenues dans la colonne **AuditData** . Les informations de cette colonne sont contenues dans un objet JSON, qui contient plusieurs propriétés configurées en tant que paires *property:value* séparées par des virgules. Vous pouvez utiliser la fonctionnalité de transformation JSON dans le Éditeur Power Query dans Excel pour fractionner chaque propriété de l’objet JSON de la colonne **AuditData** en plusieurs colonnes afin que chaque propriété ait sa propre colonne. Cela facilite l’interprétation de ces informations. Pour obtenir des instructions détaillées, consultez [Mettre en forme le journal d’audit exporté à l’aide de la Éditeur Power Query](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).

### <a name="use-powershell-to-search-and-export-audit-records"></a>Utiliser PowerShell pour rechercher et exporter des enregistrements d’audit

Une alternative à l’utilisation de l’outil de recherche d’audit dans le portail de conformité Microsoft Purview consiste à exécuter l’applet de commande [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) dans Exchange Online PowerShell. L’un des avantages de l’utilisation de PowerShell est que vous pouvez rechercher spécifiquement les activités **ou activités Set-AccessToCustomerDataRequest** effectuées par les ingénieurs Microsoft liées à une demande Customer Lockbox.

Après vous [être connecté à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), exécutez l’une des commandes suivantes. Remplacez les espaces réservés par une plage de dates spécifique.

`Set-AccessToCustomerDataRequest` Rechercher des activités

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -Operations Set-AccessToCustomerDataRequest
```

Rechercher les activités effectuées par les ingénieurs Microsoft

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -UserIds "Microsoft Operator"
```

Pour plus d’informations et d’exemples, consultez [Utiliser PowerShell pour rechercher et exporter des enregistrements de journal d’audit](export-view-audit-log-records.md#use-powershell-to-search-and-export-audit-log-records).

Nous avons également fourni un script PowerShell que vous pouvez utiliser pour rechercher dans le journal d’audit et exporter les résultats dans un fichier CSV. Pour plus d’informations, consultez [Utiliser un script PowerShell pour rechercher dans le journal d’audit](audit-log-search-script.md).

### <a name="audit-record-for-a-customer-lockbox-request"></a>Enregistrement d’audit pour une demande Customer Lockbox

Lorsqu’une personne de votre organisation approuve ou refuse une demande Customer Lockbox, l’enregistrement d’audit est enregistré dans le journal d’audit contenant les informations suivantes.

| Propriété de l’enregistrement d’audit| Description|
|:---------- |:----------|
| Date       | La date et heure d’approbation ou de refus de la demande d’accès au Customer Lockbox.
| Adresse IP | L’adresse IP de l’ordinateur utilisé par l’approbateur pour approuver ou refuser une demande. |
| Utilisateur       | Le compte de service BOXServiceAccount@\[customerforest.prod.outlook.com\].            |
| Activité   | Set-AccessToCustomerDataRequest :il s’agit de l’activité d’audit enregistrée lorsque vous approuvez ou refusez une demande d’accès au Customer Lockbox.                                |
| Item       | Guid de la demande Customer Lockbox                             |

La capture d’écran suivante montre un exemple d’enregistrement d’audit qui correspond à une demande Customer Lockbox approuvée. Si une demande Customer Lockbox a été refusée, la valeur du `ApprovalDecision` paramètre est `Deny`.

![Enregistrement d’audit pour une demande Customer Lockbox approuvée.](../media/CustomerLockbox9.png)

### <a name="audit-record-for-an-action-performed-by-a-microsoft-engineer"></a>L’enregistrement d’audit d’une action effectuée par un ingénieur Microsoft

Les actions effectuées par un ingénieur Microsoft après l’approbation d’une demande de Customer Lockbox (et qui peuvent entraîner l’accès au contenu client) sont enregistrées dans le journal d’audit. Ces enregistrements contiennent les informations suivantes.

| Propriété de l’enregistrement d’audit| Description|
|:---------- |:----------|
| Date       | Date et heure à laquelle l’action a été effectuée. Le délai d’exécution de cette action est de 4 heures après l’approbation de la demande Customer Lockbox.              |
| Adresse IP | L’adresse IP de l’ordinateur utilisé par l’ingénieur Microsoft. |
| Utilisateur       | Opérateur Microsoft ; cette valeur indique que l’enregistrement est lié à une demande Customer Lockbox.                                  |
| Activité   | Le nom de l’activité effectuée par l’ingénieur Microsoft.|
| Élément       | \<empty\>                                             |

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="which-microsoft-365-services-does-customer-lockbox-apply-to"></a>À quels services Microsoft 365 Customer Lockbox s’applique-t-il ?

Customer Lockbox est actuellement pris en charge dans Exchange Online, SharePoint Online, OneDrive Entreprise et Teams.

### <a name="is-customer-lockbox-available-to-all-customers"></a>Customer Lockbox est-il disponible pour tous les clients ?

Customer Lockbox est inclus dans les abonnements Microsoft 365 ou Office 365 E5 et peut être ajouté à d’autres plans avec un Information Protection et conformité ou un abonnement de module complémentaire Conformité avancée. Pour plus d’informations, consultez [Plans et tarification](https://products.office.com/business/office-365-enterprise-e5-business-software) .

### <a name="what-is-customer-content"></a>Qu’est-ce que le contenu client ?

Le contenu client est les données créées par les utilisateurs de services et d’applications Microsoft 365. Les exemples de contenu client sont les suivants :

- Corps ou pièces jointes d’e-mails

- Contenu du site SharePoint

- Informations dans le corps d’un fichier SharePoint

- Skype Entreprise corps du fichier de présentation

- Messages instantanés (IM) ou conversations vocales

- Texte entré dans Teams conversations et canaux Teams, par exemple, les conversations 1:1, les conversations de groupe, les canaux partagés, les canaux privés et les conversations de réunion

- Autres données collées dans Teams threads de conversation, tels que des extraits de code, des images, des messages audio et vidéo, et des liens

- Données d’application et de bot dans les conversations Teams et les canaux Teams

- flux d’activité Teams

- Teams enregistrements et transcriptions de réunion

- Messagerie vocale

- Fichiers publiés dans Teams conversations et canaux Teams

- Blob généré par le client ou données de stockage structurées (par exemple, les conteneurs SQL)

- Informations de sécurité appartenant au client (par exemple, certificats, clés de chiffrement et mots de passe)

- Inférences et toutes les inférences suivantes, si le contenu du client reste

Pour plus d’informations sur le contenu client dans Office 365, consultez le [centre de gestion de la confidentialité Office 365](https://products.office.com/business/office-365-trust-center-privacy/).

### <a name="who-is-notified-when-there-is-a-request-to-access-my-content"></a>Qui est averti en cas de demande d’accès à mon contenu ?

Les administrateurs généraux et toute personne ayant reçu le rôle d’administrateur d’approbateur d’accès Customer Lockbox sont avertis. Il s’agit également des mêmes utilisateurs qui peuvent approuver les demandes Customer Lockbox.

### <a name="who-can-approve-or-reject-these-requests-in-my-organization"></a>Qui pouvez approuver ou rejeter ces demandes dans mon organisation ?

Les administrateurs généraux et toute personne disposant du rôle d’administrateur d’approbateur d’accès Customer Lockbox peuvent approuver les demandes Customer Lockbox. Les clients contrôlent ces attributions de rôles dans leur organisation.

### <a name="how-do-i-opt-in-to-customer-lockbox"></a>Comment faire accepter Customer Lockbox ?

Un administrateur général peut activer et configurer Customer Lockbox dans le Centre d'administration Microsoft 365.

### <a name="if-i-approve-a-customer-lockbox-request-what-can-the-engineer-do-and-how-will-i-know-what-the-microsoft-engineer-did"></a>Si j’approuve une demande Customer Lockbox, que peut faire l’ingénieur et comment savoir ce que l’ingénieur Microsoft a fait ?

Après avoir approuvé une demande Customer Lockbox, l’ingénieur Microsoft a accordé ces privilèges nécessaires pour accéder au contenu du client à l’aide d’applets de commande pré-approuvées. Les actions effectuées par les ingénieurs Microsoft en réponse aux demandes Customer Lockbox sont enregistrées et accessibles dans le journal d’audit du Centre de sécurité & conformité.

### <a name="how-do-i-know-that-microsoft-follows-the-approval-process"></a>Comment faire savez que Microsoft suit le processus d’approbation ?

Vous pouvez référencer les notifications d’approbation par e-mail envoyées aux administrateurs et aux approbateurs de votre organisation avec l’historique des demandes Customer Lockbox dans le [Centre d'administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339).

Customer Lockbox est inclus dans le dernier [rapport d’audit SOC 1 SSAE 16](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports). Pour plus d’informations, vous trouverez les derniers rapports dans le [portail d’approbation de services Microsoft](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports).

### <a name="can-microsoft-modify-the-list-of-approvers-for-my-tenant-if-not-how-is-it-prevented"></a>Microsoft peut-il modifier la liste des approbateurs pour mon locataire ? Si ce n’est pas le cas, comment est-il empêché ?

Seul un administrateur général de votre organisation peut spécifier qui peut approuver les demandes Customer Lockbox. Cela signifie que seuls les membres du groupe Administrateur général dans Azure Active Directory peuvent spécifier qui peut approuver la demande. L’appartenance au groupe Administrateur général dans Azure Active Directory est gérée uniquement par votre organisation.

### <a name="what-if-i-need-more-information-about-a-content-access-request-to-approve-it"></a>Que se passe-t-il si j’ai besoin d’informations supplémentaires sur une demande d’accès au contenu pour l’approuver ?

Chaque demande Customer Lockbox contient un numéro de demande de service Microsoft 365. Vous pouvez contacter Support Microsoft et référencer ce numéro de service pour obtenir plus d’informations sur la demande.

### <a name="when-a-customer-lockbox-request-is-approved-how-long-are-the-permissions-valid"></a>Quand une demande Customer Lockbox est approuvée, combien de temps les autorisations sont-ils valides ?

Actuellement, la période maximale pour les autorisations d'accès accordées à l'ingénieur Microsoft est de 4 heures. L'ingénieur Microsoft peut également demander une période plus courte.

### <a name="how-can-i-get-a-history-of-all-customer-lockbox-requests"></a>Comment puis-je obtenir l’historique de toutes les demandes Customer Lockbox ?

Toutes les demandes Customer Lockbox sont affichées dans le [Centre d'administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339).

### <a name="how-do-i-correlate-the-content-access-requests-with-the-related-audit-logs"></a>Comment faire mettre en corrélation les demandes d’accès au contenu avec les journaux d’audit associés ?

Le flux d’activité du Centre de conformité contient les activités de journal de Customer Lockbox. Les clients peuvent référencer les activités du journal Customer Lockbox à partir du flux d’activité par rapport à la demande de courrier qu’ils reçoivent.

### <a name="what-happens-when-a-customer-doesnt-respond-to-a-customer-lockbox-request"></a>Que se passe-t-il lorsqu’un client ne répond pas à une demande Customer Lockbox ?

Les demandes d’accès Customer Lockbox ont une durée par défaut de 12 heures. Si vous ne répondez pas à une demande dans un délai de 12 heures, la demande expire.

### <a name="what-does-microsoft-do-when-a-customer-rejects-a-customer-lockbox-request"></a>Que fait Microsoft lorsqu’un client rejette une demande Customer Lockbox ?

Si un client rejette une demande Customer Lockbox, aucun accès au contenu client ne se produit. Si un utilisateur de votre organisation continue de rencontrer un problème de service qui oblige Microsoft à accéder au contenu client pour résoudre le problème, le problème de service peut persister et Microsoft l’informera.

### <a name="how-do-i-set-up-alerts-whenever-a-request-has-been-approved"></a>Comment faire configurer des alertes chaque fois qu’une demande a été approuvée ?

Il n’existe aucune option intégrée pour alerter les administrateurs. Toutefois, les administrateurs peuvent configurer des alertes à l’aide [de Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security#to-create-policies).

### <a name="does-customer-lockbox-protect-against-data-requests-from-law-enforcement-agencies-or-other-third-parties"></a>Customer Lockbox protège-t-il contre les demandes de données émanant d’organismes d’application de la loi ou d’autres tiers ?

Non. Microsoft prend au sérieux les demandes tierces de données client. En tant que fournisseur de services cloud, Microsoft défend toujours la confidentialité des données client. Si nous obtenons une assignation, Microsoft tente toujours de rediriger le tiers vers le client pour obtenir les informations. (Lisez le blog de Brad Smith : [Protection des données des clients contre l’espionnage gouvernemental](https://blogs.microsoft.com/blog/2013/12/04/protecting-customer-data-from-government-snooping/)). Nous publions régulièrement [des informations détaillées](https://www.microsoft.com/corporate-responsibility/lerr) sur les demandes d’application de la loi que Microsoft reçoit.

Pour plus d’informations, consultez le Centre de gestion de la [confidentialité Microsoft](https://www.microsoft.com/trustcenter/default.aspx) concernant les demandes de données tierces et la section « Divulgation des données client » dans les [conditions des services en ligne](https://www.microsoft.com/Licensing/product-licensing/products.aspx) .

### <a name="how-does-microsoft-ensure-that-a-member-of-its-staff-doesnt-have-standing-access-to-customer-content-in-office-365-applications"></a>Comment Microsoft s’assure-t-il qu’un membre de son personnel n’a pas un accès permanent au contenu client dans Office 365 applications ?

Microsoft implémente des mesures préventives étendues via des systèmes de contrôle d’accès et des mesures de détection pour identifier et résoudre les tentatives de contournement de ces systèmes de contrôle d’accès. Microsoft 365 fonctionne avec les principes du privilège minimum et de l’accès juste-à-temps. Par conséquent, aucun personnel Microsoft n’a l’autorisation d’accéder au contenu client de façon continue. Si l’autorisation est accordée, elle est pour une durée limitée.

Microsoft 365 utilise un système de contrôle d’accès appelé *Lockbox* pour traiter les demandes d’autorisations qui permettent d’effectuer des fonctions opérationnelles et administratives au sein du service. Un opérateur doit demander l’accès au contenu client à l’aide de Lockbox, ce qui oblige une deuxième personne à prendre des mesures sur la demande (par exemple, l’approuver) avant d’accorder l’accès. Cette deuxième personne ne peut pas être le demandeur et doit être désignée pour approuver l’accès au contenu du client. Ce n’est que si la demande est approuvée que l’opérateur acquiert un accès temporaire au contenu client. Une fois la période d’élévation expirée, Lockbox révoque l’accès.

Pour plus d’informations sur les pratiques générales de sécurité de Microsoft, reportez-vous aux [conditions générales des services en ligne](https://www.microsoft.com/licensing/product-licensing/products) .

### <a name="under-what-circumstances-do-microsoft-engineers-need-access-to-my-content"></a>Dans quelles circonstances les ingénieurs Microsoft ont-ils besoin d’accéder à mon contenu ?

Le scénario le plus courant où les ingénieurs Microsoft ont besoin d’accéder au contenu client est lorsque le client effectue une demande de support qui nécessite un accès pour la résolution des problèmes. Un principe fondamental de Microsoft 365 est que le service fonctionne sans que Microsoft n’accède au contenu client. Presque toutes les opérations de service effectuées par Microsoft sont entièrement automatisées et l’implication humaine est hautement contrôlée et abstraite du contenu client. L’objectif de Microsoft 365 est l’accès au contenu client pour prendre en charge le service n’est pas nécessaire tant que le client n’a pas approuvé une demande spécifique d’accès Microsoft.

### <a name="i-already-thought-my-data-was-secure-with-the-microsoft-cloud-so-why-do-i-need-customer-lockbox"></a>J’ai déjà pensé que mes données étaient sécurisées avec le cloud Microsoft, alors pourquoi ai-je besoin de Customer Lockbox ?

Customer Lockbox fournit une couche de contrôle supplémentaire en offrant aux clients la possibilité d’accorder une autorisation d’accès explicite pour les opérations de service. En démontrant que des procédures sont en place pour l’autorisation d’accès explicite aux données, Customer Lockbox aide également les clients à respecter certaines obligations de conformité telles que HIPAA et FEDRAMP.
