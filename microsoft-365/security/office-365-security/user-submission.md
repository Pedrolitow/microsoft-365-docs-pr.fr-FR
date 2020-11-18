---
title: Stratégie de soumission des utilisateurs
f1.keywords:
- NOCSH
ms.author: siosulli
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent apprendre à configurer une boîte aux lettres pour collecter le courrier indésirable et le courrier indésirable transmis par les utilisateurs.
ms.openlocfilehash: 31249ab930c44d84f27efac95d8e57bd88d9742f
ms.sourcegitcommit: ce46d1bd67091d4ed0e2b776dfed55e2d88cdbf4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "49130898"
---
# <a name="user-submissions-policy"></a>Stratégie de soumission des utilisateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online, vous pouvez spécifier une boîte aux lettres pour recevoir les messages signalés comme malveillants ou non malveillants par les utilisateurs. Lorsque les utilisateurs envoient des messages à l’aide des différentes options de création de rapports, vous pouvez utiliser cette boîte aux lettres pour intercepter des messages (Envoyer à la boîte aux lettres personnalisée uniquement) ou recevoir des copies de messages (Envoyer à la boîte aux lettres personnalisée et à Microsoft). Cette fonctionnalité fonctionne avec les options de signalement de message suivantes :

- [Complément de message de rapport](enable-the-report-message-add-in.md)

- [Création de rapports intégrée dans Outlook sur le Web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md) (anciennement appelé Outlook Web App)

- [Création de rapports intégrés dans Outlook pour iOS et Android](report-junk-email-and-phishing-scams-in-outlook-for-iOS-and-Android.md)

  > [!NOTE]
  > Si la création de rapports a été [désactivée dans Outlook sur le Web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web), l’activation des soumissions d’utilisateurs ici remplacera ce paramètre et permettra aux utilisateurs de signaler à nouveau les messages dans Outlook sur le Web.

Vous pouvez également configurer des outils de création de rapports de messages tiers pour transférer des messages vers la boîte aux lettres que vous spécifiez.

La remise des messages signalés par l’utilisateur à une boîte aux lettres personnalisée au lieu de Microsoft permet à vos administrateurs de signaler des messages de façon sélective et manuelle à Microsoft à l’aide de la soumission de l' [administrateur](admin-submission.md).

## <a name="custom-mailbox-prerequisites"></a>Configuration requise pour les boîtes aux lettres personnalisées

Utilisez les articles suivants pour configurer les conditions préalables requises pour que les messages signalés par l’utilisateur soient envoyés à votre boîte aux lettres personnalisée :

- Ignorer le filtrage du courrier indésirable sur la boîte aux lettres personnalisée en créant une règle de flux de messagerie Exchange pour définir le seuil de probabilité de courrier indésirable. Consultez la rubrique [utiliser le centre d’administration Exchange pour créer une règle de flux de messagerie qui définit la valeur SCL d’un message](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message) afin de définir la valeur SCL sur **-1**.

- Désactivez l’analyse des pièces jointes pour les programmes malveillants dans la boîte aux lettres personnalisée. Utilisez l’option [configurer les stratégies de pièces jointes approuvées dans Defender pour Office 365](set-up-atp-safe-attachments-policies.md) pour créer une stratégie de pièces jointes fiables avec le paramètre **désactivé** pour les **pièces jointes approuvées réponse aux programmes malveillants inconnus**.

- Désactivez l’analyse des URL sur les messages dans la boîte aux lettres personnalisée. Utilisez l’option [configurer les stratégies de liens fiables dans Defender pour Office 365](set-up-atp-safe-links-policies.md) pour créer une stratégie de liens fiables avec le paramètre **désactivé** pour **Sélectionner l’action pour les URL potentiellement inconnues dans les messages**.

- Créez une stratégie anti-programme malveillant pour désactiver la purge automatique contre les programmes malveillants. Voir [utiliser le centre de sécurité & conformité pour créer des stratégies de protection contre les programmes malveillants](configure-your-spam-filter-policies.md#use-the-security--compliance-center-to-create-anti-spam-policies) afin de définir la **purge automatique des programmes malveillants** avec la valeur **off**.

- Créez une stratégie de filtrage du courrier indésirable pour désactiver la purge automatique (ZAP) zéro heure pour le courrier indésirable et le hameçonnage dans la boîte aux lettres personnalisée. Consultez la rubrique [utiliser le centre de sécurité & conformité pour créer des stratégies de blocage du courrier indésirable](configure-your-spam-filter-policies.md#use-the-security--compliance-center-to-create-anti-spam-policies) et désactivez la case à cocher **activé** pour le **courrier indésirable zap** et le **hameçonnage zap**.

- Désactivez la règle de courrier indésirable dans la boîte aux lettres personnalisée. Utilisez [configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md) pour désactiver la règle de courrier indésirable. Une fois désactivé, EOP ne peut pas déplacer les messages vers le dossier courrier indésirable en fonction de l’action de filtrage du courrier indésirable **déplacer le message vers le dossier courrier indésirable** ou la collection de listes fiables sur la boîte aux lettres.

Une fois que vous avez vérifié que votre boîte aux lettres correspond à toutes les conditions préalables applicables, [Utilisez le centre de sécurité & conformité pour configurer la boîte aux lettres](#use-the-security--compliance-center-to-configure-the-user-submissions-mailbox) d’envoi des utilisateurs (dans cet article).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **soumissions** de l’utilisateur, utilisez <https://protection.office.com/userSubmissionsReportMessage> .

- Pour modifier la configuration des envois utilisateur, vous devez être membre de l’un des groupes de rôles suivants :

  - **Gestion de l’organisation** ou **Administrateur de sécurité** dans le [Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).
  - **Gestion** de l’organisation dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

## <a name="use-the-security--compliance-center-to-configure-the-user-submissions-mailbox"></a>Utiliser le centre de sécurité & conformité pour configurer la boîte aux lettres d’envoi des utilisateurs

1. Dans le centre de sécurité & conformité, accédez à l’utilisateur de la stratégie de **gestion des menaces** \> **Policy** \> **User submissions**.

2. Dans la page **soumissions** de l’utilisateur qui s’affiche, sélectionnez l’une des options suivantes :

   1. **Activer la fonctionnalité de rapport de message pour Outlook (recommandé)**: sélectionnez cette option si vous utilisez le complément de rapport de message ou le complément de création de rapports dans Outlook sur le Web, puis configurez les paramètres suivants :

      - **Personnaliser le message de confirmation de l’utilisateur final**: cliquez sur ce lien. Dans la fenêtre mobile **personnaliser le message de confirmation** qui s’affiche, configurez les paramètres suivants :

      - **Avant l’envoi**: dans les zones de message de **titre** et de **confirmation** , entrez le texte descriptif que les utilisateurs voient avant de signaler un message à l’aide du complément de message de rapport. Vous pouvez utiliser la variable% type% pour inclure le type d’envoi (courrier indésirable, pas courrier indésirable, hameçonnage, etc.).

        Comme indiqué, si vous sélectionnez une option qui envoie les messages signalés à Microsoft, le texte suivant est également ajouté à la notification :

        > Votre courrier électronique sera envoyé tel quel à Microsoft pour analyse. Certains courriers électroniques peuvent contenir des informations personnelles ou sensibles.

      - **Après l’envoi**: cliquez sur ![ développer ](../../media/scc-expand-icon.png) . Dans les zones de **message** de **titre** et de confirmation, entrez le texte descriptif que les utilisateurs voient lorsqu’ils signalent un message à l’aide du complément de message de rapport. Vous pouvez utiliser la variable% type% pour inclure le type d’envoi.

      Lorsque vous avez terminé, cliquez sur **Enregistrer**. Pour effacer ces valeurs, cliquez sur **restaurer** sur la page **soumissions** de l’utilisateur.

      - **Envoyer les messages signalés à**: effectuez l’une des sélections suivantes :

        - **Microsoft (recommandé)**: la boîte aux lettres d’envoi n’est pas utilisée (tous les messages signalés sont transmis à Microsoft).

        - **Microsoft et une boîte aux lettres personnalisée**: dans la zone qui s’affiche, entrez l’adresse de messagerie d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Les soumissions des utilisateurs seront dirigées vers Microsoft pour analyse et vers la boîte aux lettres personnalisée que votre administrateur ou votre équipe chargée des opérations de sécurité doit analyser.

        - **Boîte aux lettres personnalisée**: dans la zone qui s’affiche, entrez l’adresse de messagerie d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Utilisez cette option si vous souhaitez que le message soit uniquement destiné aux administrateurs ou à l’équipe des opérations de sécurité pour analyse. Les messages ne sont pas envoyés à Microsoft à moins que l’administrateur ne le transfère eux-mêmes.

        > [!NOTE]
        > Les organisations gouvernementales américaines (GCC, GCC-H et DoD) ne peuvent configurer que la **boîte aux lettres personnalisée**. Les deux autres options sont désactivées. 

      Lorsque vous avez terminé, cliquez sur **confirmer**.

      > [!CAUTION]
      > Si vous avez [désactivé la création de rapports de courrier indésirable dans Outlook sur le Web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) à l’aide des stratégies de boîte aux lettres Outlook sur le Web, mais que vous configurez l’un des paramètres précédents pour signaler les messages à Microsoft, les utilisateurs pourront signaler les messages à Microsoft dans Outlook sur le Web à l’aide du complément Report message.

   - **Désactiver la fonctionnalité de rapport de message pour Outlook**: sélectionnez cette option si vous utilisez des outils de création de rapports tiers à la place du complément de rapport de message ou de la création de rapports intégrée dans Outlook sur le Web, puis configurez les paramètres suivants :

      Sélectionnez **utiliser cette boîte aux lettres personnalisée pour recevoir des envois signalés par l’utilisateur**. Dans la zone qui s’affiche, entrez l’adresse de messagerie d’une boîte aux lettres existante qui se trouve déjà dans Office 365. Il doit s’agir d’une boîte aux lettres existante dans Exchange Online qui peut recevoir des courriers électroniques.

      Lorsque vous avez terminé, cliquez sur **confirmer**.

## <a name="message-submission-format"></a>Format de dépôt des messages

Les messages envoyés à des boîtes aux lettres personnalisées doivent suivre un format de message d’envoi spécifique. L’objet (titre de l’enveloppe) de l’envoi doit être au format suivant :

`SafetyAPIAction|NetworkMessageId|SenderIp|FromAddress|(Message Subject)`

où SafetyAPIAction est l’une des valeurs entières suivantes :

- 1 : courrier indésirable
- 2 : légitime
- 3 : hameçonnage

Dans l’exemple suivant :

- Le message est signalé comme hameçonnage.
- L’ID de message réseau est 49871234-6dc6-43e8-ABCD-08d797f20abe.
- L’adresse IP de l’expéditeur est 167.220.232.101.
- L’adresse de l’adresse est test@contoso.com.
- La ligne d’objet du message est « tester la soumission de hameçonnage »

`3|49871234-6dc6-43e8-abcd-08d797f20abe|167.220.232.101|test@contoso.com|(test phishing submission)`

Les messages qui ne suivent pas ce format ne s’afficheront pas correctement dans le portail des dépôts.
