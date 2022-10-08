---
title: Piloter Microsoft 365 depuis mon domaine personnalisé
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- scotvorg
- Adm_O365
- Adm_TOC
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment piloter la fonctionnalité de messagerie depuis mon domaine personnalisé vers une boîte aux lettres Microsoft 365 à l’aide de deux comptes de test uniquement.
ms.openlocfilehash: f48da1748b8ace33e291054cb698e3887fd23684
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68192660"
---
# <a name="pilot-microsoft-365-from-my-custom-domain"></a>Piloter Microsoft 365 depuis mon domaine personnalisé

Vous pouvez piloter Microsoft 365 avec les conditions et limitations suivantes :

- Votre fournisseur de messagerie actuel doit fournir le transfert de messages électroniques.

- Vous devez gérer vos enregistrements DNS Microsoft 365 auprès de votre fournisseur d’hébergement DNS, plutôt que de laisser Microsoft 365 les gérer pour vous.

    Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Ajouter des enregistrements DNS pour connecter votre domaine](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- Les informations de disponibilité des utilisateurs sur l’autre serveur de messagerie ne sont pas disponibles.

- Les administrateurs ne peuvent pas administrer tous les comptes d’utilisateurs depuis un seul emplacement.

- Les utilisateurs risquent de ne pas pouvoir utiliser le filtrage du courrier indésirable Microsoft 365.

- C’est recommandé pour un très petit nombre d’utilisateurs et ne s’applique qu’à l’utilisation d’un e-mail pour un pilote.

## <a name="set-up-a-microsoft-365-pilot"></a>Configurer un pilote Microsoft 365

Pour configurer un pilote Microsoft 365, procédez comme suit :

### <a name="step-1-sign-in-to-the-microsoft-365-admin-center"></a>Étape 1 : connectez-vous au Centre d’administration Microsoft 365

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) avec votre compte professionnel ou scolaire.

2. Dans le volet de navigation gauche, sélectionnez **Paramètres** > **Domaines**.

### <a name="step-2-verify-that-you-own-the-domain-you-want-to-use"></a>Étape 2 : vérifiez que vous êtes propriétaire du domaine que vous voulez utiliser

1. Dans la page **Domaines**, sélectionnez **Ajouter un domaine**.

2. Tapez le nom de domaine dans la zone, sélectionnez **Utiliser ce domaine**, puis sélectionnez **Continuer**.

3. Sélectionnez les services que vous souhaitez tester avec votre domaine, tels que la messagerie électronique et la messagerie instantanée.

4. Sur la page **Vérifier** le domaine, suivez les instructions détaillées, puis sélectionnez **Vérifier**.

    La prise en compte des modifications DNS peut prendre de quelques minutes à 72 heures.

    Une fois la vérification effectuée avec succès, vous êtes invité à modifier vos enregistrements DNS.

### <a name="step-3-mark-the-domain-as-shared-in-exchange-online"></a>Étape 3 : marquez le domaine comme partagé dans Exchange Online

1. Dans le centre d’administration Exchange, dans la section **Flux de courrier**, sélectionnez **Domaines acceptés**, puis sélectionnez le domaine que vous souhaitez modifier.

2. Double-cliquez pour ouvrir la fenêtre, puis sélectionnez **Relais interne**.

3. Sélectionnez **Enregistrer**.

    La prise en compte de ce paramètre peut nécessiter quelques minutes.

### <a name="step-4-unblock-the-existing-email-server-optional"></a>Étape 4 : débloquez éventuellement le serveur de messagerie existant (facultatif)

Microsoft 365 utilise Exchange Online Protection (EOP) pour la protection contre le courrier indésirable. EOP peut bloquer votre serveur de messagerie existant s’il détecte un nombre élevé de courrier indésirable transmis par votre serveur de messagerie actuel. Si vous faites confiance à la protection contre le courrier indésirable pour votre autre fournisseur de messagerie, vous pouvez débloquer le serveur dans Microsoft 365.

> [!NOTE]
> Le déblocage de votre serveur de messagerie existant permet aux courriers indésirables transmis par votre serveur d’origine d’être transmis aux boîtes aux lettres Microsoft 365. Ensuite, vous ne pouvez pas évaluer la façon dont Microsoft 365 bloque le courrier indésirable.

1. Dans le volet de navigation du centre d’administration Exchange, sélectionnez **Protection**, puis **Filtre de connexion**.

2. Dans la **liste d’adresses IP autorisées**, sélectionnez **+**, puis ajoutez l’adresse IP du serveur de messagerie de votre fournisseur de messagerie actuel.

### <a name="step-5-create-user-accounts-and-set-the-primary-reply-to-address"></a>Étape 5 : créez des comptes d’utilisateurs et définissez l’adresse de réponse principale

1. Dans le volet de navigation gauche du Centre d’administration Microsoft 365, sélectionnez **Utilisateurs** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Utilisateurs actifs**</a>.

2. Créez deux comptes de test en ajoutant deux utilisateurs existants.

    Pour chaque compte, sélectionnez **+ Ajouter un utilisateur**, puis renseignez les informations requises, y compris la méthode de mot de passe que vous souhaitez tester.

    Pour vous assurer que les messages électroniques d’un utilisateur restent identiques, le champ **Nom d’utilisateur** doit correspondre à l’adresse de messagerie actuelle de l’utilisateur.

3. Sélectionnez la licence appropriée, cliquez sur **Suivant**, puis sur **Terminer l’ajout**.

4. En regard de **Nom d’utilisateur**, sélectionnez votre nom de domaine personnalisé dans la liste déroulante.

5. Sélectionnez **Créer** > **Fermer**.

### <a name="step-6-configure-mail-to-flow-from-microsoft-365-or-office-365-to-email-server"></a>Étape 6 : Configurer la messagerie pour que les messages circulent depuis Microsoft 365 ou Office 365 vers un serveur de messagerie

Voici les deux étapes à suivre :

1. Configurer votre environnement Microsoft 365 ou Office 365.

2. Configurer un connecteur depuis Microsoft 365 ou Office 365 vers votre serveur de messagerie.

### <a name="1-configure-your-microsoft-365-or-office-365-environment"></a>1. Configurer votre environnement Microsoft 365 ou Office 365

Assurez-vous que vous avez effectué les opérations suivantes dans Microsoft 365 ou Office 365 :

1. To set up connectors, you need permissions assigned before you can begin. To check what permissions you need, see the Microsoft 365 and Office 365 connectors entry in the [Feature permissions in Exchange Online](/exchange/permissions-exo/feature-permissions) topic.

2. Si vous voulez que vos courriers électroniques soient relayés par EOP ou Exchange Online de vos serveurs de messagerie vers Internet, deux solutions sont possibles :

   - Use a certificate configured with a subject name that matches an accepted domain in Microsoft 365 or Office 365. We recommend that your certificate's common name or subject alternative name matches the primary SMTP domain for your organization. For details, see [Prerequisites for your on-premises email environment](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#prerequisites-for-your-on-premises-email-environment).

   - OU -

   - Vous pouvez vérifier que tous les domaines et sous-domaines d'expéditeurs de votre organisation sont des domaines acceptés dans Microsoft 365 ou Office 365.

   Pour obtenir plus d’informations sur la définition de domaines acceptés, voir [Gestion des domaines acceptés dans Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) et [Activer le flux de messagerie pour les sous-domaines dans Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains). 

3. Indiquez si vous souhaitez utiliser des règles de flux de courrier (également appelées règles de transport) ou des noms de domaine pour remettre le courrier de Microsoft 365 ou Office 365 vers vos serveurs de courrier. La plupart des entreprises choisit de remettre les messages pour tous les domaines acceptés. Pour plus d'informations, consultez la rubrique [Scénario : routage des messages conditionnels dans Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/conditional-mail-routing).

> [!NOTE]
> You can set up mail flow rules as described in [Mail flow rule actions in Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions). For example, you might want to use mail flow rules with connectors if your mail is currently directed via distribution lists to multiple sites.

### <a name="2-set-up-a-connector-from-microsoft-365-or-office-365-to-your-email-server"></a>2. Configurer un connecteur depuis Microsoft 365 ou Office 365 vers votre serveur de messagerie.

To create a connector in Microsoft 365 or Office 365, select **Admin** > **Exchange** to go to the Exchange admin center. Next, select **mail flow** > <a href="https://go.microsoft.com/fwlink/?linkid=2183136" target="_blank">**Connectors**</a>.

Configuration de connecteurs à l’aide de l’Assistant.

Pour démarrer l’Assistant, cliquez sur le signe plus **+**. Dans le premier écran, sélectionnez **De** Office 365 et **À** votre serveur de courrier de l’organisation.

Click **Next**, and follow the instructions in the wizard. Click the **Help** or **Learn More** links if you need more information. The wizard will guide you through setup. At the end, make sure your connector validates. If the connector does not validate, double-click the message displayed to get more information, and see [Validate connectors](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/validate-connectors) for help resolving issues.



### <a name="step-7-update-dns-records-at-your-dns-hosting-provider"></a>Étape 7 : mettez à jour les enregistrements DNS auprès de votre fournisseur d’hébergement DNS

Connectez-vous au site Web de votre fournisseur d’hébergement DNS, puis suivez les instructions de la rubrique [Ajouter des enregistrements DNS pour connecter votre domaine](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**Prévoyez les deux exceptions suivantes :**

- Ne créez pas d’enregistrement MX et n’en modifiez pas un existant.

- Si vous disposez déjà d’un enregistrement SPF (Sender Policy Framework) pour votre fournisseur de messagerie précédent, au lieu de créer un enregistrement SPF (TXT) pour Exchange Online, ajoutez simplement « include:spf.protection.outlook.com » à l’enregistrement TXT actuel.

    Par exemple, « v=spf1 mx include:adatum.com include:spf.protection.outlook.com ~all ».

    If you don't have an SPF record, modify the one recommended by Microsoft 365 to include the domain for your current email provider, and add spf.protection.outlook.com. This authorizes outgoing messages from both email systems.

### <a name="step-8-set-up-email-forwarding-at-your-current-provider"></a>Étape 8 : configurez le transfert de messages électroniques sur votre fournisseur actuel

Sur votre fournisseur de messagerie actuel, configurez le transfert pour les comptes de messagerie de vos utilisateurs vers votre domaine onmicrosoft.com :

- Transférez une boîte aux lettres d’un utilisateur A vers usera@yourcompany.onmicrosoft.com

- Transférez une boîte aux lettres d’un utilisateur B vers usera@yourcompany.onmicrosoft.com

Une fois cette étape terminée, tous les messages envoyés à usera@yourcompany.com et userb@yourcompany.com sont disponibles dans Microsoft 365.

> [!NOTE]
> Contactez votre fournisseur de messagerie actuel pour connaître les étapes exactes relatives à la configuration du transfert de messages électroniques.<br/>
> Il n’est pas nécessaire de conserver une copie des messages sur le fournisseur de messagerie actuel.<br/>
> La plupart des fournisseurs transfèrent les messages électroniques sans toucher à l’adresse de réponse de l’expéditeur, afin que les réponses parviennent à l’expéditeur d’origine.

### <a name="step-9-test-mail-flow"></a>Étape 9 : testez le flux de courrier

1. Connectez-vous à Outlook Web App à l’aide des informations d’identification de l’utilisateur A.

2. Effectuez ces tests :

    - Testez le courrier électronique local de Microsoft en envoyant un courrier électronique, par exemple, à l’utilisateur B. Le courrier électronique est remis immédiatement. Dans ce scénario, le message n’est pas acheminé vers la boîte aux lettres de l’utilisateur B sur votre serveur d’origine, car la boîte aux lettres Microsoft 365 est locale.

    - Testez le courrier électronique à un utilisateur sur le système de messagerie existant en envoyant un courrier électronique, par exemple, à l’utilisateur C. Le courrier électronique est remis à la boîte aux lettres de l’utilisateur C sur votre serveur de messagerie d’origine.

    - Vérifiez que le transfert est correctement configuré depuis un compte externe, ou depuis un compte de messagerie d’employé sur le système de messagerie existant. Par exemple, depuis le compte de serveur d’origine pour l’utilisateur C ou un compte Hotmail, envoyez un courrier électronique à l’utilisateur A, puis vérifiez qu’il arrive dans la boîte aux lettres Microsoft 365 de l’utilisateur A.

### <a name="step-10-move-mailbox-contents"></a>Étape 10 : déplacez le contenu de la boîte aux lettres

Because you are moving only two test users, and User A and User B are both using Outlook, you can move the email by opening the old .PST file in the new Outlook profile and copying the messages, calendar items, contacts, and so on. For more information, see [Import email, contacts, and calendar from an Outlook .pst file](https://support.microsoft.com/office/import-email-contacts-and-calendar-from-an-outlook-pst-file-431a8e9a-f99f-4d5f-ae48-ded54b3440ac).

Une fois que vous les avez importés aux emplacements appropriés dans la boîte aux lettres Microsoft 365, ces éléments sont accessibles à partir de n’importe quel appareil, où que vous soyez.
