---
title: Piloter Microsoft 365 depuis mon domaine personnalisé
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Adm_O365
ms.custom: ''
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment piloter la fonctionnalité de messagerie depuis mon domaine personnalisé vers une boîte aux lettres Microsoft 365 à l’aide de deux comptes de test uniquement.
ms.openlocfilehash: bdcf86474a7f2edb458075e884c20e56d231df6d
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51197838"
---
# <a name="pilot-microsoft-365-from-my-custom-domain"></a>Piloter Microsoft 365 depuis mon domaine personnalisé

Vous pouvez piloter Microsoft 365 avec les conditions et limitations suivantes :

- Votre fournisseur de messagerie actuel doit fournir le transfert de messages électroniques.

- Vous devez gérer vos enregistrements DNS Microsoft 365 auprès de votre fournisseur d’hébergement DNS, plutôt que de laisser Microsoft 365 les gérer pour vous.

    Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Ajouter des enregistrements DNS pour connecter votre domaine](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- Les informations de disponibilité des utilisateurs sur l’autre serveur de messagerie ne sont pas disponibles.

- Les administrateurs ne peuvent pas administrer tous les comptes d’utilisateurs depuis un seul emplacement.

- Les utilisateurs risquent de ne pas pouvoir utiliser le filtrage du courrier indésirable Microsoft 365.

- C’est recommandé pour un très petit nombre d’utilisateurs et ne s’applique qu’à l’utilisation d’un e-mail pour un pilote.

## <a name="set-up-a-microsoft-365-pilot"></a>Configurer un pilote Microsoft 365

Pour configurer un pilote Microsoft 365, procédez comme suit :

### <a name="step-1-sign-in-to-the-microsoft-365-admin-center"></a>Étape 1 : connectez-vous au Centre d’administration Microsoft 365

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) avec votre compte professionnel ou scolaire.

2. Dans le volet de navigation gauche, sélectionnez **Paramètres** > **Domaines**.

### <a name="step-2-verify-that-you-own-the-domain-you-want-to-use"></a>Étape 2 : vérifiez que vous êtes propriétaire du domaine que vous voulez utiliser

1. Dans la page **Domaines**, sélectionnez **Ajouter un domaine**.

2. Tapez le nom de domaine dans la zone, sélectionnez **Utiliser ce domaine**, puis sélectionnez **Continuer**.

3. Sélectionnez les services que vous souhaitez tester avec votre domaine, tels que la messagerie électronique et la messagerie instantanée.

5. Sur la page **Vérifier** le domaine, suivez les instructions détaillées, puis sélectionnez **Vérifier**.

    La prise en compte des modifications DNS peut prendre de quelques minutes à 72 heures.

    Une fois la vérification effectuée avec succès, vous êtes invité à modifier vos enregistrements DNS.

### <a name="step-3-mark-the-domain-as-shared-in-exchange-online"></a>Étape 3 : marquez le domaine comme partagé dans Exchange Online

1. Dans le centre d’administration Exchange, dans la section **Flux de courrier**, sélectionnez **Domaines acceptés**, puis sélectionnez le domaine que vous souhaitez modifier.

2. Double-cliquez pour ouvrir la fenêtre, puis sélectionnez **Relais interne**. 

3. Sélectionnez **Enregistrer**.

    La prise en compte de ce paramètre peut nécessiter quelques minutes.

### <a name="step-4-unblock-the-existing-email-server-optional"></a>Étape 4 : débloquez éventuellement le serveur de messagerie existant (facultatif)

Microsoft 365 utilise Exchange Online Protection (EOP) pour la protection contre le courrier indésirable. EOP peut bloquer votre serveur de messagerie existant s’il détecte un nombre élevé de courrier indésirable transmis par votre serveur de messagerie actuel. Si vous faites confiance à la protection contre le courrier indésirable pour votre autre fournisseur de messagerie, vous pouvez débloquer le serveur dans Microsoft 365.

> [!NOTE]
> Le déblocage de votre serveur de messagerie existant permet aux courriers indésirables transmis par votre serveur d’origine d’être transmis aux boîtes aux lettres Microsoft 365. Ensuite, vous ne pouvez pas évaluer la façon dont Microsoft 365 bloque le courrier indésirable.

1. Dans le volet de navigation du centre d’administration Exchange, sélectionnez **Protection**, puis **Filtre de connexion**.

2. Dans la **liste d’adresses IP autorisées**, sélectionnez **+**, puis ajoutez l’adresse IP du serveur de messagerie de votre fournisseur de messagerie actuel. 

### <a name="step-5-create-user-accounts-and-set-the-primary-reply-to-address"></a>Étape 5 : créez des comptes d’utilisateurs et définissez l’adresse de réponse principale

1. Dans le volet de navigation gauche du Centre d’administration Microsoft 365, sélectionnez **Utilisateurs** > **Utilisateurs actifs**.

2. Créez deux comptes de test en ajoutant deux utilisateurs existants.

    Pour chaque compte, sélectionnez **+ Ajouter un utilisateur**, puis renseignez les informations requises, y compris la méthode de mot de passe que vous souhaitez tester.

    Pour vous assurer que les messages électroniques d’un utilisateur restent identiques, le champ **Nom d’utilisateur** doit correspondre à l’adresse de messagerie actuelle de l’utilisateur.

3. Sélectionnez la licence appropriée, cliquez sur **Suivant**, puis sur **Terminer l’ajout**. 

4. En regard de **Nom d’utilisateur**, sélectionnez votre nom de domaine personnalisé dans la liste déroulante. 

5. Sélectionnez **Créer** > **Fermer**.

### <a name="step-6-configure-mail-to-flow-from-microsoft-365-or-office-365-to-email-server"></a>Étape 6 : Configurer la messagerie pour que les messages circulent depuis Microsoft 365 ou Office 365 vers un serveur de messagerie

Voici les deux étapes à suivre :

1. Configurer votre environnement Microsoft 365 ou Office 365.

2. Configurer un connecteur depuis Microsoft 365 ou Office 365 vers votre serveur de messagerie.

### <a name="1-configure-your-microsoft-365-or-office-365-environment"></a>1. Configurer votre environnement Microsoft 365 ou Office 365

Assurez-vous que vous avez effectué les opérations suivantes dans Microsoft 365 ou Office 365 :

1. Pour configurer des connecteurs, vous avez besoin d’autorisations attribuées avant de commencer. Pour vérifier les autorisations dont vous avez besoin, consultez l’entrée sur les connecteurs Microsoft 365 et Office 365 dans la rubrique [Autorisations de fonctionnalité dans EOP](https://docs.microsoft.com/microsoft-365/security/office-365-security/feature-permissions-in-eop).

2. Si vous voulez que vos courriers électroniques soient relayés par EOP ou Exchange Online de vos serveurs de messagerie vers Internet, deux solutions sont possibles :

   - Vous pouvez utiliser un certificat configuré avec un nom d’objet qui correspond à un domaine accepté dans Microsoft 365 ou Office 365. Nous recommandons que le nom commun ou l’autre nom d’objet de votre certificat corresponde au domaine SMTP principal de votre organisation. Pour obtenir des détails, voir [Conditions requises pour votre environnement de messagerie locale](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#prerequisites-for-your-on-premises-email-environment).

   - OU -

   - Vous pouvez vérifier que tous les domaines et sous-domaines d'expéditeurs de votre organisation sont des domaines acceptés dans Microsoft 365 ou Office 365.

   Pour obtenir plus d’informations sur la définition de domaines acceptés, voir [Gestion des domaines acceptés dans Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) et [Activer le flux de messagerie pour les sous-domaines dans Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains). 

3. Indiquez si vous souhaitez utiliser des règles de flux de courrier (également appelées règles de transport) ou des noms de domaine pour remettre le courrier de Microsoft 365 ou Office 365 vers vos serveurs de courrier. La plupart des entreprises choisit de remettre les messages pour tous les domaines acceptés. Pour plus d'informations, consultez la rubrique [Scénario : routage des messages conditionnels dans Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/conditional-mail-routing).

> [!NOTE]
> Vous pouvez configurer des règles de flux de courrier, comme décrit dans [Actions de règle de flux de courrier dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions). Par exemple, vous pouvez utiliser des règles de flux de courrier avec des connecteurs si votre courrier électronique est actuellement redirigé via des listes de distribution vers plusieurs sites.

### <a name="2-set-up-a-connector-from-microsoft-365-or-office-365-to-your-email-server"></a>2. Configurer un connecteur depuis Microsoft 365 ou Office 365 vers votre serveur de messagerie.

Pour créer un connecteur dans Microsoft 365 ou Office 365, cliquez sur **Administrateur**, puis sur **Exchange** pour accéder au Centre d'administration Exchange. Cliquez ensuite sur **flux de messagerie**, puis sur **connecteurs**.

Configuration de connecteurs à l’aide de l’Assistant.

Pour démarrer l’Assistant, cliquez sur le signe plus **+**. Dans le premier écran, sélectionnez **De** Office 365 et **À** votre serveur de courrier de l’organisation.

Cliquez sur **Suivant**, et suivez les instructions de l’Assistant. Cliquez sur les liens « **Aide** » ou « **En savoir plus** » pour plus d’informations. L’Assistant vous guidera à chaque étape de la configuration. À la fin, vérifiez que votre connecteur est validé. Si le connecteur n’est pas validé, double-cliquez sur le message affiché pour obtenir plus d’informations, et consultez la rubrique [Valider des connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/validate-connectors) pour obtenir de l’aide afin de résoudre les problèmes.



### <a name="step-7-update-dns-records-at-your-dns-hosting-provider"></a>Étape 7 : mettez à jour les enregistrements DNS auprès de votre fournisseur d’hébergement DNS

Connectez-vous au site Web de votre fournisseur d’hébergement DNS, puis suivez les instructions de la rubrique [Ajouter des enregistrements DNS pour connecter votre domaine](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**Prévoyez les deux exceptions suivantes :**

- Ne créez pas d’enregistrement MX et n’en modifiez pas un existant.

- Si vous disposez déjà d’un enregistrement SPF (Sender Policy Framework) pour votre fournisseur de messagerie précédent, au lieu de créer un enregistrement SPF (TXT) pour Exchange Online, ajoutez simplement « include:spf.protection.outlook.com » à l’enregistrement TXT actuel.

    Par exemple, « v=spf1 mx include:adatum.com include:spf.protection.outlook.com ~all ».

    Si vous ne disposez pas encore d’enregistrement SPF, modifiez celui recommandé par Microsoft 365 pour y inclure le domaine de votre fournisseur de messagerie actuel, puis ajoutez spf.protection.outlook.com. Cette action autorise les messages sortants provenant des deux systèmes de courrier.

### <a name="step-8-set-up-email-forwarding-at-your-current-provider"></a>Étape 8 : configurez le transfert de messages électroniques sur votre fournisseur actuel

Sur votre fournisseur de messagerie actuel, configurez le transfert pour les comptes de messagerie de vos utilisateurs vers votre domaine onmicrosoft.com :

- Transférez une boîte aux lettres d’un utilisateur A vers usera@yourcompany.onmicrosoft.com

- Transférez une boîte aux lettres d’un utilisateur B vers usera@yourcompany.onmicrosoft.com

Une fois cette étape terminée, tous les messages envoyés à usera@yourcompany.com et userb@yourcompany.com sont disponibles dans Microsoft 365.

> [!NOTE]
> Contactez votre fournisseur de messagerie actuel pour connaître les étapes exactes relatives à la configuration du transfert de messages électroniques.<br/>
> Il n’est pas nécessaire de conserver une copie des messages sur le fournisseur de messagerie actuel.<br/>
> La plupart des fournisseurs transfèrent les messages électroniques sans toucher à l’adresse de réponse de l’expéditeur, afin que les réponses parviennent à l’expéditeur d’origine.

### <a name="step-9-test-mail-flow"></a>Étape 9 : testez le flux de courrier

1. Connectez-vous à Outlook Web App à l’aide des informations d’identification de l’utilisateur A.

2. Effectuez ces tests :

    - Testez le courrier électronique local de Microsoft en envoyant un courrier électronique, par exemple, à l’utilisateur B. Le courrier électronique est remis immédiatement. Dans ce scénario, le message n’est pas acheminé vers la boîte aux lettres de l’utilisateur B sur votre serveur d’origine, car la boîte aux lettres Microsoft 365 est locale.

    - Testez le courrier électronique à un utilisateur sur le système de messagerie existant en envoyant un courrier électronique, par exemple, à l’utilisateur C. Le courrier électronique est remis à la boîte aux lettres de l’utilisateur C sur votre serveur de messagerie d’origine.

    - Vérifiez que le transfert est correctement configuré depuis un compte externe, ou depuis un compte de messagerie d’employé sur le système de messagerie existant. Par exemple, depuis le compte de serveur d’origine pour l’utilisateur C ou un compte Hotmail, envoyez un courrier électronique à l’utilisateur A, puis vérifiez qu’il arrive dans la boîte aux lettres Microsoft 365 de l’utilisateur A.

### <a name="step-10-move-mailbox-contents"></a>Étape 10 : déplacez le contenu de la boîte aux lettres

Étant donné que vous déplacez uniquement deux utilisateurs de test, et que l’utilisateur A et l’utilisateur B utilisent Outlook, vous pouvez déplacer le courrier électronique en ouvrant l’ancien fichier .PST dans le nouveau profil Outlook et en copiant les messages, les éléments de calendrier, les contacts, etc. Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Importer le courrier, les contacts et le calendrier à partir d’un fichier .pst Outlook](https://support.microsoft.com/office/import-email-contacts-and-calendar-from-an-outlook-pst-file-431a8e9a-f99f-4d5f-ae48-ded54b3440ac).

Une fois que vous les avez importés aux emplacements appropriés dans la boîte aux lettres Microsoft 365, ces éléments sont accessibles à partir de n’importe quel appareil, où que vous soyez.