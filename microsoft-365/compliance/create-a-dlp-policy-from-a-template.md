---
title: Création d'une stratégie DLP à partir d'un modèle
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.NewPolicyFromTemplate
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-mar2020
- admindeeplinkCOMPLIANCE
description: Dans cet article, vous allez découvrir comment créer des stratégies DLP à l’aide de l’un des modèles inclus dans Office 365.
ms.openlocfilehash: 92c26c23461c9a03e50ea3a8f0ebb20a2b5151ba
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61939104"
---
# <a name="create-a-dlp-policy-from-a-template"></a>Création d’une stratégie DLP à partir d’un modèle

Le moyen le plus simple et le plus courant de commencer à utiliser les stratégies DLP consiste à utiliser l’un des modèles inclus dans le centre de conformité Microsoft 365 de données. Vous pouvez utiliser l’un de ces modèles tel qu’il est ou personnaliser les règles pour répondre aux exigences de conformité spécifiques de votre organisation.

Microsoft 365 comprend plus de 40 modèles prêts à l’emploi qui peuvent vous aider à répondre à un large éventail de besoins courants en matière de réglementation et de stratégie d’entreprise. Voir ; [Modèles de stratégie](dlp-policy-reference.md#policy-templates) pour une liste complète. 

Vous pouvez affiner un modèle en modifiant l’une de ses règles existantes ou en ajoutant de nouvelles règles. Par exemple, vous pouvez ajouter de nouveaux types d’informations sensibles à une règle, modifier les décomptes dans une règle pour rendre son déclenchement plus facile ou plus difficile, permettre aux utilisateurs de remplacer les actions d’une règle en fournissant une justification ou modifier les destinataires des notifications et des rapports d’incident. Un modèle de stratégie DLP est un point de départ flexible pour de nombreux scénarios de conformité courants.

Vous pouvez également choisir le modèle personnalisé, sans règle par défaut, et configurer votre stratégie DLP de A à Z, pour répondre aux exigences de conformité spécifiques de votre organisation.

## <a name="permissions"></a>Autorisations

Les membres de votre équipe de mise en conformité qui créeront des stratégies DLP ont besoin des autorisations d’accès au Centre de conformité. Par défaut, votre administrateur client aura accès aux responsables de la mise en conformité et aux autres personnes. Procédez comme suit :
  
1. Créer un groupe dans Microsoft 365 et d’y ajouter des responsables de la mise en conformité.
    
2. Créer un groupe de rôles sur la page **Autorisations** du Centre de sécurité et de conformité. 

3. Lors de la création du groupe de rôles, utilisez la **section** Choisir des rôles pour ajouter le rôle suivant au groupe de rôles : **DLP Compliance Management**.
    
4. Utilisez la section **Choisir des membres** pour ajouter le groupe Microsoft 365 que vous avez créé précédemment au groupe de rôles.

Utilisez le rôle Gestion de la conformité **DLP** en affichage seul pour créer un groupe de rôles avec des privilèges d’affichage seul pour les stratégies DLP et les rapports DLP.

Pour plus d’informations, voir [Give users access to the Office 365 Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
Ces autorisations sont nécessaires pour créer et appliquer une stratégie DLP et non pour appliquer des stratégies.

### <a name="roles-and-role-groups-in-preview"></a>Rôles et groupes de rôles en prévisualisation

Il existe des rôles et des groupes de rôles en prévisualisation que vous pouvez tester pour affiner vos contrôles d’accès.

Voici une liste des rôles Protection des données Microsoft (MIP) en prévisualisation. Pour en savoir plus à ce sujet, voir [Rôles](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) dans le Centre de sécurité & conformité

- Administrateur de la protection des informations
- Analyste de la protection des informations
- Enquêteur de la protection des informations
- Lecteur de protection des informations

Voici une liste des groupes de rôles MIP en prévisualisation. Pour en savoir plus sur les groupes de rôles, voir Groupes de [rôles dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Protection des informations
- Administrateurs de la protection des informations
- Analystes de la protection des informations
- Enquêteurs de la protection des informations
- Lecteurs de protection des informations

### <a name="create-the-dlp-policy-from-a-template"></a>Créer la stratégie DLP à partir d’un modèle

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centre de conformité Microsoft 365</a>.

2. Dans le Centre de conformité, \> navigation gauche \> **Solutions** \> **Stratégies** \>  \> de protection contre la perte de données + Créer une stratégie .

    ![Créez un bouton de stratégie.](../media/b1e48a08-92e2-47ca-abdc-4341694ddc7c.png)
          
3. Choisissez le modèle de stratégie DLP qui protège les types d’informations sensibles dont vous avez \> besoin.

4. Nommez la stratégie \> **Suivant**.
 
<!--In this example, you'll select **Privacy** \> **U.S. Personally Identifiable Information (PII) Data** because it already includes most of the types of sensitive information that you want to protect - you'll add a couple later.

    When you select a template, you can read the description on the right to learn what types of sensitive information the template protects.

    ![Page for choosing a DLP policy template.](../media/775266f6-ad87-4080-8d7c-97f2e7403b30.png)-->

5. Pour choisir les emplacements que la stratégie DLP doit protéger et accepter l’étendue par défaut pour chaque emplacement ou personnaliser l’étendue. Voir [emplacements pour](dlp-policy-reference.md#locations) les options d’portée.

6. Cliquez sur \> **Suivant**.
 
1. <!-->, faites l’une des choses suivantes :

   - Choose **All locations in Office 365** \> **Next**.
   - Choose **Let me choose specific locations** \> **Next**. Pour cet exemple, choisissez ceci.

   Pour inclure ou exclure un emplacement entier tel que tous les e-mails  Exchange ou tous les comptes OneDrive, mettez l’état de cet emplacement sur ou hors service.

   Pour inclure uniquement des sites SharePoint ou des comptes  OneDrive Entreprise spécifiques, sélectionnez État, puis cliquez sur les liens sous Inclure pour choisir des sites ou des comptes spécifiques.  Lorsque vous appliquez une stratégie à un site, les règles configurées dans cette stratégie sont automatiquement appliquées à tous les sous-sites de ce site.

   ![Options pour les emplacements où une stratégie DLP peut être appliquée.](../media/ee50a61a-e867-4571-a150-3eec8d83650f.png)

   Dans cet exemple, pour protéger les informations sensibles stockées dans  tous les comptes OneDrive Entreprise, désactiver l’état pour  les sites de messagerie **Exchange** et **SharePoint** et laisser l’état pour les comptes **OneDrive**.-->

7. Choose **Review and customize default settings from the template** \> **Next**.

8. Un modèle de stratégie DLP contient des règles prédéfinies avec les conditions et actions qui détectent et agissent sur des types spécifiques d’informations sensibles. Vous pouvez modifier, supprimer ou désactiver l’une des règles existantes ou en ajouter de nouvelles. Lorsque vous avez terminé, cliquez sur **Suivant**.

    ![Règles étendues dans le modèle de stratégie PII des États-Unis.](../media/3bc9f1b6-f8ad-4334-863a-24448bb87687.png)

9. Choisissez de détecter le moment où ce contenu est partagé au sein de votre organisation ou en dehors de votre organisation si vous avez sélectionné l’un de ces emplacements :
    1. Exchange
    1. SharePoint
    1. OneDrive
    1. Teams chat et messages de canal 

10. Cliquez sur **Suivant**.

11. Dans la page **Actions de protection,** si vous le souhaitez, vous pouvez personnaliser les notifications de conseil de stratégie et les e-mails de notification. Enable **When content matches the policy conditions, show policy tips to users and send them an email notification,** then choose **Customize the tip and email**.
12. Sélectionnez **Suivant**.


<!--    In this example, the U.S. PII Data template includes two predefined rules:

   - **Low volume of content detected U.S. PII** This rule looks for files containing between 1 and 10 occurrences of each of three types of sensitive information (ITIN, SSN, and U.S. passport numbers), where the files are shared with people outside the organization. If found, the rule sends an email notification to the primary site collection administrator, document owner, and person who last modified the document.

   - **High volume of content detected U.S. PII** This rule looks for files containing 10 or more occurrences of each of the same three sensitive information types, where the files are shared with people outside the organization. If found, this action also sends an email notification, plus it restricts access to the file. For content in a OneDrive for Business account, this means that permissions for the document are restricted for everyone except the primary site collection administrator, document owner, and person who last modified the document.

    To meet your organization's specific requirements, you may want to make the rules easier to trigger, so that a single occurrence of sensitive information is enough to block access for external users. After looking at these rules, you understand that you don't need low and high count rules—you need only a single rule that blocks access if any occurrence of sensitive information is found.

    So you expand the rule named **Low volume of content detected U.S. PII** \> **Delete rule**.

    ![Delete rule button.](../media/bc36f7d2-0fae-4af1-92e8-95ba51077b12.png)

9. Now, in this example, you need to add two sensitive information types (U.S. bank account numbers and U.S. driver's license numbers), allow people to override a rule, and change the count to any occurrence. You can do all of this by editing one rule, so select **High volume of content detected U.S. PII** \> **Edit rule**.

    ![Edit rule button.](../media/eaf54067-4945-4c98-8dd6-fb2c5d6de075.png)

10. To add a sensitive information type, in the **Conditions** section \> **Add or change types**. Then, under **Add or change types** \> choose **Add** \> select **U.S. Bank Account Number** and **U.S. Driver's License Number** \> **Add** \> **Done**.

    ![Option to Add or change types.](../media/c6c3ae86-f7db-40a8-a6e4-db11692024be.png)

    ![Add or change types pane.](../media/fdbb96af-b914-4a6c-a97b-bbd014689965.png)

11. To change the count (the number of instances of sensitive information required to trigger the rule), under **Instance count** \> choose the **min** value for each type \> enter 1. The minimum count cannot be empty. The maximum count can be empty; an empty **max** value convert to **any**.

    When finished, the min count for all of the sensitive information types should be **1** and the max count should be **any**. In other words, any occurrence of this type of sensitive information will satisfy this condition.

    ![Instance counts for sensitive information types.](../media/5c6e08cb-59a9-4558-b54b-d899836d4737.png)

12. For the final customization, you don't want your DLP policies to block people from doing their work when they have a valid business justification or encounter a false positive, so you want the user notification to include options to override the blocking action.

    In the **User notifications** section, you can see that email notifications and policy tips are turned on by default for this rule in the template.

    In the **User overrides** section, you can see that overrides for a business justification are turned on, but overrides to report false positives are not. Choose **Override the rule automatically if they report it as a false positive**.

    ![User notifications section and User overrides section.](../media/62720e7a-a939-4c03-b414-67748f3d64a0.png)

13. At the top of the rule editor, change the name of this rule from the default **High volume of content detected U.S. PII** to **Any content detected with U.S. PII** because it's now triggered by any occurrence of its sensitive information types.

14. At the bottom of the rule editor \> **Save**.

15. Review the conditions and actions for this rule \> **Next**.

    On the right, notice the **Status** switch for the rule. If you turn off an entire policy, all rules contained in the policy are also turned off. However, here you can turn off a specific rule without turning off the entire policy. This can be useful when you need to investigate a rule that is generating a large number of false positives.

16. On the next page, read and understand the following, and then choose whether to turn on the rule or test it out first \> **Next**.

     Before you create your DLP policies, you should consider rolling them out gradually to assess their impact and test their effectiveness before you fully enforce them. For example, you don't want a new DLP policy to unintentionally block access to thousands of documents that people require to get their work done.

    If you're creating DLP policies with a large potential impact, we recommend following this sequence:

17. Start in test mode without Policy Tips and then use the DLP reports to assess the impact. You can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, you can fine tune the rules as needed. In test mode, DLP policies will not impact the productivity of people working in your organization.

18. Move to Test mode with notifications and Policy Tips so that you can begin to teach users about your compliance policies and prepare them for the rules that are going to be applied. At this stage, you can also ask users to report false positives so that you can further refine the rules.

19. Turn on the policies so that the rules are enforced and the content's protected. Continue to monitor the DLP reports and any incident reports or notifications to make sure that the results are what you intend.

    ![Options for using test mode and turning on policy.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

20. Review your settings for this policy \> choose **Create**.

After you create and turn on a DLP policy, it's deployed to any content sources that it includes, such as SharePoint Online sites or OneDrive for Business accounts, where the policy begins automatically enforcing its rules on that content.


## Example: Identify sensitive information across all OneDrive for Business sites and restrict access for people outside your organization

OneDrive for Business accounts make it easy for people across your organization to collaborate and share documents. But a common concern for compliance officers is that sensitive information stored in OneDrive for Business accounts may be inadvertently shared with people outside your organization. A DLP policy can help mitigate this risk.

In this example, you'll create a DLP policy that identifies U.S. PII data, which includes Individual Taxpayer Identification Numbers (ITIN), Social Security Numbers, and U.S. passport numbers. You'll get started by using a template, and then you'll modify the template to meet your organization's compliance requirements—specifically, you'll:

- Add a couple of types of sensitive information—U.S. bank account numbers and U.S. driver's license numbers—so that the DLP policy protects even more of your sensitive data.

- Make the policy more sensitive, so that a single occurrence of sensitive information is enough to restrict access for external users.

- Allow users to override the actions by providing a business justification or reporting a false positive. This way, your DLP policy won't prevent people in your organization from getting their work done, provided they have a valid business reason for sharing the sensitive information.


## View the status of a DLP policy

At any time, you can view the status of your DLP policies on the **Policy** page in the **Data loss prevention** section of the Security &amp; Compliance Center. Here you can find important information, such as whether a policy was successfully enabled or disabled, or whether the policy is in test mode.

Here are the different statuses and what they mean.

<br>

****

|Status|Explanation|
|---|---|
|**Turning on…**|The policy is being deployed to the content sources that it includes. The policy is not yet enforced on all sources.|
|**Testing, with notifications**|The policy is in test mode. The actions in a rule are not applied, but policy matches are collected and can be viewed by using the DLP reports. Notifications about policy matches are sent to the specified recipients.|
|**Testing, without notifications**|The policy is in test mode. The actions in a rule are not applied, but policy matches are collected and can be viewed by using the DLP reports. Notifications about policy matches are not sent to the specified recipients.|
|**On**|The policy is active and enforced. The policy was successfully deployed to all its content sources.|
|**Turning off...**|The policy is being removed from the content sources that it includes. The policy may still be active and enforced on some sources. Turning off a policy may take up to 45 minutes.|
|**Off**|The policy is not active and not enforced. The settings for the policy (sources, keywords, duration, etc) are saved.|
|**Deleting...**|The policy is in the process of being deleted. The policy is not active and not enforced. It normally takes an hour for a policy to delete.|
|

## Turn off a DLP policy

You can edit or turn off a DLP policy at any time. Turning off a policy disables all of the rules in the policy.

To edit or turn off a DLP policy, on the **Policy** page \> select the policy \> **Edit policy**.

![Edit policy button.](../media/ce319e92-0519-44fe-9507-45a409eaefe4.png)

In addition, you can turn off each rule individually by editing the policy and then toggling off the **Status** of that rule, as described above.

## More information

- [Learn about data loss prevention](dlp-learn-about-dlp.md)
- [Send notifications and show policy tips for DLP policies](use-notifications-and-policy-tips.md)
- [Create a DLP policy to protect documents with FCI or other properties](protect-documents-that-have-fci-or-other-properties.md)
- [What the DLP policy templates include](what-the-dlp-policy-templates-include.md)
- [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)
