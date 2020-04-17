---
title: Configurer la stratégie anti-hameçonnage par défaut dans EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: ''
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à modifier les paramètres de détection d’usurpation d’identité disponibles dans la stratégie anti-hameçonnage par défaut dans les organisations Office 365 avec des boîtes aux lettres Exchange Online.
ms.openlocfilehash: 1a8527a55796910e79fbf70b824de828ca48591b
ms.sourcegitcommit: db8702cf578b02c6fd6a2670c177b456efae4748
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "43537532"
---
# <a name="configure-the-default-anti-phishing-policy-in-eop"></a>Configurer la stratégie anti-hameçonnage par défaut dans EOP

Les organisations Office 365 avec des boîtes aux lettres Exchange Online et les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online ont une stratégie anti-hameçonnage par défaut. Cette stratégie contient un nombre limité de fonctionnalités d’usurpation d’identité qui sont activées par défaut. Pour plus d’informations, reportez-vous à la rubrique [usurpation des paramètres dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#spoof-settings).

Les organisations Office 365 avec des boîtes aux lettres Exchange Online peuvent modifier la stratégie anti-hameçonnage par défaut dans le centre de sécurité & de sécurité Office 365 ou dans Exchange Online PowerShell. Les organisations EOP autonomes sans boîte aux lettres Exchange Online ne peuvent pas modifier leur stratégie anti-hameçonnage par défaut.

Pour plus d’informations sur la création et la modification des stratégies anti-hameçonnage plus avancées disponibles dans Office 365 Advanced Threat Protection, consultez la rubrique [configure ATP anti-phishing Policies in office 365](configure-atp-anti-phishing-policies.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **anti-hameçonnage** , utilisez <https://protection.office.com/antiphishing>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. Pour ajouter, modifier et supprimer des stratégies de détection d’hameçonnage, vous devez être membre des groupes de rôles de gestion de l' **organisation** ou d' **administrateur de sécurité** . Pour un accès en lecture seule aux stratégies de détection d’hameçonnage, vous devez être membre du groupe de rôles **lecteur de sécurité** . Pour plus d’informations sur les groupes de rôles dans le Centre de sécurité et conformité, voir [Autorisations dans le Centre de sécurité et conformité Office 365](permissions-in-the-security-and-compliance-center.md).

- Pour connaître les paramètres recommandés pour la stratégie anti-hameçonnage par défaut, consultez les paramètres de la [stratégie anti-hameçonnage par défaut EOP](recommended-settings-for-eop-and-office365-atp.md#eop-default-anti-phishing-policy-settings).

- Autorisez jusqu’à 30 minutes pour l’application de la stratégie mise à jour.

- Pour plus d’informations sur l’endroit où les stratégies de détection d’hameçonnage sont appliquées dans le pipeline de filtrage, consultez la rubrique [Order and Precedence of Mail Protection in Office 365](how-policies-and-protections-are-combined.md).

### <a name="use-the-security--compliance-center-to-modify-the-default-anti-phishing-policy"></a>Utiliser le centre de sécurité & conformité pour modifier la stratégie anti-hameçonnage par défaut

La stratégie anti-hameçonnage par défaut est nommée Office antiphishing par défaut et n’apparaît pas dans la liste des stratégies. Pour modifier la stratégie anti-hameçonnage par défaut, procédez comme suit :

1. Dans le centre de sécurité & conformité, accédez à **protection anti-hameçonnage**de la **stratégie** \> de **gestion** \> des menaces.

2. Sur la page **anti-hameçonnage** , cliquez sur **stratégie par défaut**.

3. La page **modifier votre stratégie d’anti-hameçonnage Office 365 par défaut** apparaît. Dans la section **usurpation** , cliquez sur **modifier**.

   Notez que ces paramètres sont identiques aux paramètres d’usurpation d’identité disponibles dans les stratégies anti-hameçonnage ATP.

   - **Usurpation des paramètres de filtrage**: la valeur par défaut est **activée**, et nous vous recommandons de la laisser activée. Pour le désactiver, faites glisser le bouton de bascule sur **désactivé**. Pour plus d’informations, consultez la rubrique [configure usurpation Intelligence in Office 365](learn-about-spoof-intelligence.md).

     > [!NOTE]
     > Vous n’avez pas besoin de désactiver la protection contre l’usurpation d’identité si votre enregistrement MX ne pointe pas vers Office 365 ; vous activez le filtrage amélioré pour les connecteurs à la place. Pour obtenir des instructions, voir [Enhanced Filtering for Connectors in Exchange Online](https://docs.microsoft.com/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

   - **Activer la fonctionnalité d’expéditeur non authentifié**: ajoute un point d’interrogation à la photo de l’expéditeur si le message ne parvient pas à vérifier l’authentification de messagerie. Pour plus d’informations, reportez-vous à la rubrique [usurpation des paramètres dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#spoof-settings). La valeur par défaut est **Activée**. Pour le désactiver, faites glisser le bouton de bascule sur **désactivé**.

   - **Actions**: spécifiez l’action à effectuer sur les messages qui échouent à l’aide d’usurpation d’identité :

     **Si un message électronique est envoyé par un utilisateur qui n’est pas autorisé à usurper votre domaine**:

     - **Déplacer le message vers les dossiers de courrier indésirable des destinataires** (il s’agit de la valeur par défaut.)
     - **Mettre en quarantaine le message**

   - **Vérifiez vos paramètres**: au lieu de cliquer sur chaque étape individuelle, les paramètres sont affichés dans un résumé.

     - Vous pouvez cliquer sur **modifier** dans chaque section pour revenir à la page appropriée.
     - Vous pouvez activer ou **Désactiver** les paramètres suivants **directement sur cette** page :

       - **Activer la protection contre l’usurpation d’identité**
       - **Activer la fonctionnalité d’expéditeur non authentifié**

   Lorsque vous avez terminé, cliquez sur **Enregistrer** sur une page.

4. Sur la page **modifier votre stratégie par défaut pour les antiphishing Office 365** , vérifiez vos paramètres, puis cliquez sur **Fermer**.

## <a name="use-the-security--compliance-center-to-view-the-default-anti-phishing-policy"></a>Utiliser le centre de sécurité & conformité pour afficher la stratégie anti-hameçonnage par défaut

1. Dans le centre de sécurité & conformité, puis accédez à **Policy** \> **protection contre les** **menaces** \> pour le hameçonnage.

2. Cliquez sur **stratégie par défaut** pour afficher la stratégie anti-hameçonnage par défaut.

## <a name="use-exchange-online-powershell-to-configure-the-default-anti-phishing-policy"></a>Utiliser Exchange Online PowerShell pour configurer la stratégie anti-hameçonnage par défaut

### <a name="use-powershell-to-view-the-default-anti-phish-policy"></a>Utiliser PowerShell pour afficher la stratégie anti-hameçonnage par défaut

Pour afficher la stratégie anti-hameçonnage par défaut, exécutez la commande suivante :

```PowerShell
Get-AntiPhishPolicy -Identity "Office365 AntiPhish Default"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-antiphishpolicy permet](https://docs.microsoft.com/powershell/module/exchange/advanced-threat-protection/Get-AntiPhishPolicy).

### <a name="use-powershell-to-modify-the-default-anti-phish-policy"></a>Utiliser PowerShell pour modifier la stratégie anti-hameçonnage par défaut

Pour modifier la stratégie anti-hameçonnage par défaut, utilisez la syntaxe suivante :

```powershell
Set-AntiPhishPolicy -Identity "Office365 AntiPhish Default" [-AuthenticationFailAction <MoveToJmf | Quarantine>] [-EnableAntispoofEnforcement <$true | $false>] [-EnableUnauthenticatedSender <$true | $false>]
```

Cet exemple modifie l’action pour les messages usurpés dont l’authentification échoue lors de la mise en quarantaine.

```powershell
Set-AntiPhishPolicy -Identity "Office365 AntiPhish Default" -AuthenticationFailAction Quarantine
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-antiphishpolicy permet](https://docs.microsoft.com/powershell/module/exchange/advanced-threat-protection/Set-AntiPhishPolicy).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez bien configuré la stratégie anti-hameçonnage par défaut, effectuez l’une des opérations suivantes :

- Dans le centre de sécurité & conformité, accédez à **stratégie** \> de **gestion** \> **des menaces-hameçonnage** \> , cliquez sur **stratégie par défaut** et affichez les détails dans le menu volant.

- Dans Exchange Online PowerShell, exécutez la commande suivante et vérifiez les paramètres :

  ```PowerShell
  Get-AntiPhishPolicy -Identity "Office365 AntiPhish Default"
  ```
