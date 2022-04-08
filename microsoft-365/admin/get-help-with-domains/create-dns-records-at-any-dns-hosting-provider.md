---
title: Ajouter des enregistrements DNS pour connecter votre domaine
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
search.appverid:
- MET150
description: Connectez un domaine d’un fournisseur d’hébergement DNS à Microsoft 365 en vérifiant votre domaine et en mettant à jour les enregistrements DNS dans le compte de votre bureau d’enregistrement.
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
- admindeeplinkMAC
ms.openlocfilehash: 08d28a5586c92d0e439170807f750150d9fbe17c
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2022
ms.locfileid: "64704776"
---
# <a name="add-dns-records-to-connect-your-domain"></a>Ajouter des enregistrements DNS pour connecter votre domaine

Si vous avez acheté un domaine auprès d’un fournisseur d’hébergement tiers, vous pouvez le connecter à Microsoft 365 en mettant à jour les enregistrements DNS dans le compte de votre bureau d’enregistrement.

À la fin de ces étapes, votre domaine reste enregistré auprès de l’hôte à qui vous avez acheté le domaine, mais Microsoft 365 peut l’utiliser pour vos adresses de messagerie (telles que utilisateur@votredomaine.com) et d’autres services.

Si vous n’ajoutez pas de domaine, les membres de votre organisation utiliseront le domaine onmicrosoft.com pour leur adresse de messagerie jusqu’à ce que vous le fassiez. Il est important d’ajouter votre domaine avant d’ajouter des utilisateurs, de sorte que vous n’ayez pas à les reconfigurer.

[Consultez la FAQ dédiée aux domaines](../setup/domains-faq.yml) si vous ne trouvez pas ci-dessous ce que vous recherchez .

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="step-1-add-a-txt-or-mx-record-to-verify-you-own-the-domain"></a>Étape 1 : Ajouter un enregistrement TXT ou MX pour vérifier que vous êtes propriétaire du domaine

### <a name="recommended-verify-with-a-txt-record"></a>Recommandé : vérifier avec un enregistrement TXT

Vous devez tout d’abord prouver que vous êtes le propriétaire du domaine que vous voulez ajouter à Microsoft 365.

1. Connectez-vous au Centre d’administration Microsoft 365, puis sélectionnez **Afficher tout** > **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domaines**</a>.
2. Dans un nouvel onglet ou une nouvelle fenêtre de navigateur, connectez-vous à votre fournisseur d’hébergement DNS, puis recherchez l’emplacement où vous gérez vos paramètres DNS (par exemple, Paramètres de fichier de zone, Gérer les domaines, Gestionnaire de domaine, Gestionnaire DNS).
3. Accédez à la page Gestionnaire DNS de votre fournisseur et ajoutez à votre domaine l’enregistrement TXT indiqué dans le centre d’administration.

   L’ajout de cet enregistrement n’affecte pas votre e-mail ou les autres services existants, et vous pouvez le supprimer de façon sécurisée une fois que votre domaine est connecté à Microsoft 365.

   Exemple :

   - Nom TXT : `@`
   - Valeur TXT : MS = MS # # # # # # # # (ID unique du centre d’administration)
   - TTL : `3600` (ou votre fournisseur par défaut)

4. Sauvegardez l’enregistrement, revenez au centre d’administration, puis sélectionnez **Vérifier**. Il faut généralement 15 minutes pour que les modifications apportées aux enregistrements soient enregistrées, mais cela peut prendre plus de temps. Accordez un peu de temps et quelques tentatives pour récupérer la modification.

Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.

### <a name="verify-with-an-mx-record"></a>Vérifier avec un enregistrement MX

Si votre bureau d’enregistrement ne prend pas en charge l’ajout d'enregistrements TXT, vous pouvez procéder à la vérification en ajoutant un enregistrement MX.

1. Connectez-vous au Centre d’administration Microsoft 365, puis sélectionnez **Afficher tout** > **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domaines**</a>.
2. Dans un nouvel onglet ou une nouvelle fenêtre de navigateur, connectez-vous à votre fournisseur d’hébergement DNS, puis recherchez l’emplacement où vous gérez vos paramètres DNS (par exemple, Paramètres de fichier de zone, Gérer les domaines, Gestionnaire de domaine, Gestionnaire DNS).
3. Accédez à la page Gestionnaire DNS de votre fournisseur et ajoutez à votre domaine l’enregistrement MX indiqué dans le centre d’administration.

La **Priorité** de cet enregistrement MX doit être la plus élevée de tous les enregistrements MX existants pour le domaine. Sinon, il peut interférer avec l'envoi et la réception d'e-mails. Vous devez supprimer ces enregistrements dès que la vérification du domaine est terminée.

Vérifiez que les champs sont définis par les valeurs suivantes :

- Type d’enregistrement : `MX`
- Priorité : définissez sur n’importe quelle valeur importante qui n’est pas déjà utilisée.
- Nom de l’hôte : `@`
- Adresse de pointage : copiez la valeur à partir du centre d’administration et collez-la ici.
- TTL : `3600` (ou votre fournisseur par défaut)

Lorsque Microsoft trouve l’enregistrement MX approprié, votre domaine est vérifié.

## <a name="step-2-add-dns-records-to-connect-microsoft-services"></a>Étape 2 : ajouter des enregistrements DNS pour connecter les services Microsoft

Dans un nouvel onglet ou une nouvelle fenêtre de navigateur, connectez-vous à votre fournisseur d’hébergement DNS, puis recherchez l’emplacement où vous gérez vos paramètres DNS (par exemple, Paramètres de fichier de zone, Gérer les domaines, Gestionnaire de domaine, Gestionnaire DNS).

Vous pourrez ajouter plusieurs types d’enregistrements DNS selon les services que vous voulez activer.

### <a name="add-an-mx-record-for-email-outlook-exchange-online"></a>Ajouter un enregistrement MX pour la messagerie électronique (Outlook, Exchange Online)

**Avant de commencer :** si les utilisateurs disposent déjà d’une adresse de messagerie avec votre domaine (par exemple, utilisateur@votredomaine.com), créez leur compte dans le centre d’administration avant de configurer vos enregistrements MX. Ainsi, ils continueront à recevoir du courrier électronique. Lorsque vous mettez à jour l’enregistrement MX de votre domaine, tout nouveau message électronique adressé à une personne utilisant votre domaine mène désormais vers Microsoft 365. Un courrier électronique que vous avez déjà reste chez votre hôte de courrier actuel, sauf si vous décidez de [migrer les courriers électroniques et contacts vers Microsoft 365.](../setup/migrate-email-and-contacts-admin.md)

Vous obtiendrez les informations relatives à l’enregistrement MX à partir de l’Assistant Configuration du domaine du centre d’administration.

Sur le site Web de votre fournisseur d’hébergement, créez un nouvel enregistrement MX. Vérifiez que les champs sont définis par les valeurs suivantes :

- Type d’enregistrement : `MX`
- Priorité : sélectionnez la valeur la plus élevée disponible, généralement `0`.
- Nom de l’hôte : `@`
- Adresse de pointage : copiez la valeur à partir du centre d’administration et collez-la ici.
- TTL : `3600`

> [!NOTE]
> Exchange Online prend en charge uniquement les valeurs TTL inférieures à 6 heures (21 600 secondes).

Sauvegardez l’enregistrement et supprimez tous les autres enregistrements MX.

### <a name="add-cname-records-to-connect-other-services-teams-exchange-online-aad-mdm"></a>Ajouter des enregistrements CNAME pour connecter d’autres services (Teams, Exchange Online, AAD, MDM)

Vous obtiendrez les informations relatives aux enregistrements CNAME à partir de l’Assistant Configuration du domaine du centre d’administration.

Sur le site Web de votre fournisseur d’hébergement, ajoutez les enregistrements CNAME pour chaque service auquel vous voulez vous connecter.
Dans le nouvel enregistrement, vérifiez que chacun des champs sont définis par les valeurs suivantes :

- Type d’enregistrement : `CNAME (Alias)`
- Hôte : collez les valeurs que vous copiez à partir du centre d’administration ici.
- Adresse de pointage : copiez la valeur à partir du centre d’administration et collez-la ici.
- TTL : `3600` (ou votre fournisseur par défaut)

### <a name="add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online"></a>Ajouter ou modifier un enregistrement TXT SPF afin d’éviter les courriers indésirables (Outlook, Exchange Online)

**Avant de commencer :** Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft 365. Ajoutez plutôt les valeurs Microsoft 365 requises à l’enregistrement actuel sur le site Web de votre fournisseur d’hébergement de manière à n’avoir qu’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs.

Sur le site web de votre fournisseur d’hébergement, modifiez l'enregistrement SPF existant ou créez un enregistrement SPF.
Vérifiez que les champs sont définis par les valeurs suivantes :

- Type d’enregistrement : `TXT (Text)`
- Hôte : `@`
- Valeur TXT :`v=spf1 include:spf.protection.outlook.com -all`
- TTL : `3600` (ou votre fournisseur par défaut)

Enregistrez l'enregistrement.

Validez votre enregistrement SPF en utilisant l'un des [Outils de validation SPF](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain) suivants

SPF est conçu pour lutter contre l’usurpation d’adresse, mais il existe des techniques d’usurpation d’adresse contre lesquelles SPF ne peut rien faire. Pour vous protéger contre ces techniques, une fois que vous avez configuré votre SPF, vous devez également configurer DKIM et DMARC pour Microsoft 365.

Pour commencer, consultez la rubrique [Utilisation du DKIM pour valider les e-mails sortants envoyés à partir de votre domaine dans Microsoft 365](../../security/office-365-security/use-dkim-to-validate-outbound-email.md) et [Utilisation du DMARC pour valider les e-mails dans Microsoft 365](../../security/office-365-security/use-dmarc-to-validate-email.md).

### <a name="add-srv-records-for-communications-services-teams-skype-for-business"></a>Ajouter des enregistrements SRV pour les services de communications (Teams, Skype Entreprise)

Sur le site Web de votre fournisseur d’hébergement, ajoutez les enregistrements SRV pour chaque service auquel vous voulez vous connecter.
Dans le nouvel enregistrement, vérifiez que chacun des champs sont définis par les valeurs suivantes :

- Type d’enregistrement : `SRV (Service)`
- Nom : `@`
- Cible : copiez la valeur à partir du centre d’administration et collez-la ici.
- Protocole : copiez la valeur à partir du centre d’administration et collez-la ici.
- Service : copiez la valeur à partir du centre d’administration et collez-la ici.
- Priorité : `100`
- Poids : `1`
- Port : copiez la valeur à partir du centre d’administration et collez-la ici.
- TTL : `3600` (ou votre fournisseur par défaut)

Enregistrez l'enregistrement.

#### <a name="srv-record-field-restrictions-and-workarounds"></a>Restrictions relatives aux champs d’enregistrement SRV et solutions de contournement

Certains fournisseurs d’hébergement imposent des restrictions sur les valeurs de champs dans les enregistrements SRV. Voici quelques solutions de contournement courantes pour ces restrictions.

##### <a name="name"></a>Nom

Si votre fournisseur d’hébergement n’autorise pas la définition de ce champ sur **@**, laissez ce champ vide. Utilisez cette approche *uniquement* lorsque votre fournisseur d’hébergement utilise des champs distincts pour les valeurs Service et Protocole. Dans le cas contraire, consultez les notes sur les valeurs Service et Protocole ci-dessous.

##### <a name="service-and-protocol"></a>Service et Protocole

Si votre fournisseur d’hébergement ne fournit pas ces champs pour les enregistrements SRV, vous devez spécifier les valeurs de **Service** et **Protocole** dans le champ **Nom** de l’enregistrement. Remarque : suivant votre fournisseur d’hébergement, le champ **Nom** peut avoir une autre appellation, comme **Hôte**, **Nom de l’hôte** ou **Sous-domaine**. Pour ajouter ces valeurs, vous devez créer une seule chaîne, en séparant les valeurs par un point.

Exemple : `_sip._tls`

##### <a name="priority-weight-and-port"></a>Priorité, Poids, et Port

Si votre fournisseur d’hébergement ne fournit pas ces champs pour les enregistrements SRV, vous devez spécifier ces valeurs dans le champs **Cible** de l’enregistrement. Remarque : selon votre fournisseur d’hébergement, le champ **Cible** peut être appelé différemment, comme **Contenu**, **Adresse IP** ou **Hôte cible**.

Pour ajouter ces valeurs, créez une seule chaîne, en séparant les valeurs par des espaces, *ou parfois par un point*. Si vous n’êtes pas sûr, consultez votre fournisseur. Les valeurs doivent être incluses dans cet ordre : Priorité, Poids, Port, Cible.

- Exemple 1 : `100 1 443 sipdir.online.lync.com.`
- Exemple 2 : `100 1 443 sipdir.online.lync.com`

## <a name="related-content"></a>Contenu associé

[Modifier les serveurs de noms de manière à configurer Microsoft 365 avec n'importe quel bureau d'enregistrement de domaines](change-nameservers-at-any-domain-registrar.md) (article)\
[Rechercher et corriger les problèmes, y compris de messagerie, après avoir ajouté votre domaine ou des enregistrements DNS](find-and-fix-issues.md) (article)\
[Gérer des domaines](/admin) (page de lien)
