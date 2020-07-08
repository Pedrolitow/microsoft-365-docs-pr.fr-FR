---
title: Renforcer la protection contre les menaces
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: 5abfef7b-5957-484a-b06b-a7c55e013e44
description: Obtenir de l’aide pour augmenter le niveau de protection dans Microsoft 365
ms.openlocfilehash: 0583bcb540991f20b3826549125800c80a3738db
ms.sourcegitcommit: 5b769f74bcc76ac8d38aad815d1728824783cd9f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "45079820"
---
# <a name="increase-threat-protection"></a>Renforcer la protection contre les menaces

Cet article vous aide à renforcer la protection de votre abonnement Microsoft 365 afin de vous protéger contre le hameçonnage, les programmes malveillants et d’autres menaces. Ces recommandations sont appropriées pour les organisations ayant un besoin accru de sécurité, tels que les campagnes politiques, les bureaux d’avocats et les stages de soins de santé. 

Avant de commencer, vérifiez votre score de sécurité Microsoft. Microsoft Secure score analyse la sécurité de votre organisation en fonction de vos activités normales et des paramètres de sécurité et attribue un score. Commencez par prendre note de votre score actuel. L’exécution des actions recommandées dans cet article augmente votre score. L’objectif n’est pas d’obtenir le score maximal, mais de prendre conscience des possibilités de protection de votre environnement qui n’ont pas d’impact négatif sur la productivité de vos utilisateurs. 

Pour plus d’informations, consultez la rubrique [Microsoft Secure score](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-secure-score).


## <a name="raise-the-level-of-protection-against-malware-in-mail"></a>Augmenter le niveau de protection contre les programmes malveillants dans les messages

Votre environnement Office 365 ou Microsoft 365 inclut une protection contre les programmes malveillants, mais vous pouvez augmenter cette protection en bloquant les pièces jointes avec des types de fichiers couramment utilisés pour les programmes malveillants. Pour augmenter la protection contre les programmes malveillants dans le courrier électronique :
  
1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous avec vos informations d’identification de compte d’administrateur. 
    
2. Dans le centre de navigation de gauche du centre de sécurité &amp; conformité, **Threat management**sélectionnez **Policy** \> **protection contre les programmes malveillants**pour la stratégie.
    
3. Double-cliquez sur la stratégie par défaut pour modifier cette stratégie à l’échelle de l’entreprise.
    
4. Cliquez sur **Paramètres**.
    
5. Sous **Common Attachment types Filter**, sélectionnez **activé**. Les types de fichiers bloqués sont répertoriés dans la fenêtre située directement en dessous de ce contrôle.  Veillez à ajouter ces FileTypes :
   - ADE, ADP, Ani, bas, bat, chm, cmd, com, cpl, CRT, HLP, HT, HTA, inf, ins, fournisseur de services Internet, Job, js, jse, lnk, MDA, de mdb, MDE, mdz, MSC, MSI, MSP, MST, PCD, reg, SCR, SCT, SHS, URL, VB, VBE, vbs, WSC, wsf, WSH  <br/> Vous pouvez ajouter ou supprimer des types de fichiers ultérieurement, si nécessaire.
    
6. Cliquez sur **Enregistrer**.
    
Pour plus d’informations, consultez la rubrique [protection contre les programmes malveillants](https://go.microsoft.com/fwlink/?linkid=2015692&amp;clcid=0x409).
  


## <a name="protect-against-ransomware"></a>Se protéger contre les rançongiciels

Les ransomware limitent l’accès aux données en chiffrant les fichiers ou en verrouillant les écrans d’ordinateur. Il tente ensuite de extort l’argent des victimes en demandant « ransomware », généralement sous la forme d’cryptocurrencies comme Bitcoin, dans Exchange pour l’accès aux données. 
  
Vous pouvez vous protéger contre les ransomware en créant une ou plusieurs règles de flux de messagerie pour bloquer les extensions de fichiers couramment utilisées pour les ransomware (elles ont été ajoutées à l’étape [augmenter le niveau de protection contre les programmes malveillants dans le courrier](#raise-the-level-of-protection-against-malware-in-mail) ) ou pour avertir les utilisateurs qui reçoivent ces pièces jointes par courrier électronique.

Outre les fichiers que vous avez bloqués à l’étape précédente, il est également recommandé de créer une règle pour avertir les utilisateurs avant l’ouverture de pièces jointes de fichier Office qui incluent des macros. Les ransomware peuvent être masqués dans les macros, afin que les utilisateurs ne puissent pas ouvrir ces fichiers à partir de personnes qu’ils ne connaissent pas.

Pour créer une règle de transport de messagerie :
  
1. Accédez au centre d’administration <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a> et choisissez **centres d’administration** \> **Exchange**.
    
2. Dans la catégorie **flux de messagerie** , cliquez sur **règles**.
    
3. Cliquez sur **+** , puis sur **créer une règle**.
    
4. Cliquez sur **plus d’options** en bas de la boîte de dialogue pour afficher l’ensemble complet des options. 
    
5. Appliquez les paramètres du tableau suivant pour la règle. Conservez les autres paramètres par défaut, sauf si vous souhaitez les modifier.
    
6. Cliquez sur **Enregistrer**.
    
|**Paramètre**|**Avertir les utilisateurs avant l’ouverture de pièces jointes de fichiers Office**||
|:-----|:-----|:-----|
|Nom  <br/> |Règle anti-ransomware : avertir les utilisateurs  <br/>  |
|Appliquez cette règle si. . .  <br/> |N’importe quelle pièce jointe. . . l’extension de fichier correspond à. . .  <br/> |
|Spécifier des mots ou des expressions  <br/> |Ajoutez les types de fichiers suivants :  <br/> dotm, docm, xlsm, SLTM, xla, xlam, XLL, pptm, potm, ppam, PPSM, sldm  <br/>|
|Procédez comme suit. . .  <br/> |Avertir le destinataire avec un message  <br/> |
|Fournir le texte du message  <br/> |N’ouvrez pas ces types de fichiers provenant de contacts inconnus, car ils peuvent contenir des macros avec du code malveillant.  <br/> |
   
Si vous souhaitez plus d’informations, reportez-vous aux rubriques suivantes :
  
- [Comment traiter les ransomware](https://go.microsoft.com/fwlink/?linkid=2016501&amp;clcid=0x409)
    
- [Restaurer votre espace OneDrive](https://support.office.com/article/fa231298-759d-41cf-bcd0-25ac53eb8a15.aspx)
    


## <a name="stop-auto-forwarding-for-email"></a>Arrêter le transfert automatique pour le courrier électronique

Les pirates qui accèdent à la boîte aux lettres d’un utilisateur peuvent voler votre courrier en définissant la boîte aux lettres pour transférer automatiquement le courrier électronique. Cela peut se produire même sans la sensibilisation de l’utilisateur. Vous pouvez éviter cela en configurant une règle de flux de messagerie. 
  
Pour créer une règle de transport de courrier, regardez [cette courte vidéo](https://support.office.com/article/f9d693ba-5c78-47c0-b156-8e461e062aa7) ou procédez comme suit :
  
1. Dans le centre d’administration Microsoft 365, cliquez sur **centres** d’administration \> **Exchange**.
    
2. Dans la catégorie **flux de messagerie** , cliquez sur **règles**.
    
3. Cliquez sur **+** , puis sur **créer une règle**.
    
4. Cliquez sur **plus d’options** en bas de la boîte de dialogue pour afficher l’ensemble complet des options. 
    
5. Appliquez les paramètres dans le tableau suivant. Conservez les autres paramètres par défaut, sauf si vous souhaitez les modifier.
    
6. Cliquez sur **Enregistrer**.
    
|**Paramètre**|**Avertir les utilisateurs avant l’ouverture de pièces jointes de fichiers Office**|
|:-----|:-----|
|Nom  <br/> |Empêcher le transfert automatique des courriers électroniques vers des domaines externes  <br/> |
|Appliquer cette règle si...  <br/> |Expéditeur. . . est externe/interne. . . Au sein de l’Organisation  <br/> |
|Ajouter une condition  <br/> |Propriétés du message. . . inclure le type de message. . . Transfert automatique  <br/> |
|Procédez comme suit...  <br/> |Bloquer le message. . . rejeter le message et inclure une explication.  <br/> |
|Fournir le texte du message  <br/> |Le transfert automatique du courrier électronique en dehors de cette organisation est interdit pour des raisons de sécurité.  <br/> |


## <a name="protect-your-email-from-phishing-attacks"></a>Protéger votre courrier électronique contre les attaques par hameçonnage

Si vous avez configuré un ou plusieurs domaines personnalisés pour votre environnement Office 365 ou Microsoft 365, vous pouvez configurer une protection anti-hameçonnage ciblée. La protection anti-hameçonnage ATP, partie de la protection avancée contre les menaces d’Office 365, peut vous aider à protéger votre organisation contre les attaques par hameçonnage malveillantes et les attaques par hameçonnage. Si vous n’avez pas configuré de domaine personnalisé, vous n’avez pas besoin d’effectuer cette opération.
  
Nous vous recommandons de prendre en main cette protection en créant une stratégie de protection des utilisateurs les plus importants et de votre domaine personnalisé. 

Pour créer une stratégie anti-hameçonnage ATP, regardez [cette vidéo de formation courte](https://support.office.com/article/86c425e1-1686-430a-9151-f7176cce4f2c)ou effectuez les étapes suivantes :
  
1. Accédez à [https://protection.office.com](https://protection.office.com). 
    
2. Dans le centre de navigation de gauche du centre de sécurité &amp; conformité, sous gestion des **menaces**, sélectionnez **stratégie**.
    
3. Sur la page **stratégie** , choisissez **protection contre le hameçonnage ATP**.
    
4. Sur la page **anti-hameçonnage** , sélectionnez **+ créer**. Un Assistant s’ouvre et vous guide tout au long de la définition de votre stratégie anti-hameçonnage.
    
5. Spécifiez le nom, la description et les paramètres de votre stratégie, comme recommandé dans le graphique ci-dessous. Pour plus d’informations, consultez la rubrique [en savoir plus sur les options de stratégie anti-hameçonnage ATP](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-anti-phishing-policies). 
    
6. Une fois que vous avez vérifié vos paramètres, sélectionnez **créer cette stratégie** ou **Enregistrer**, selon le cas.
    

|**Paramètre ou option**<br/>|**Valeur recommandée** <br/>|
|:-----|:-----|
|Nom  <br/> |Domaine et équipe de campagne la plus intéressante  <br/> |
|Description  <br/> |Assurez-vous que le personnel le plus important et que notre domaine ne sont pas empruntés.  <br/> |
|Ajouter des utilisateurs à protéger  <br/> |Sélectionnez **+ Ajouter une condition, le destinataire est**. Tapez noms d’utilisateur ou entrez l’adresse de messagerie du candidat, du gestionnaire de campagnes et d’autres membres importants du personnel. Vous pouvez ajouter jusqu’à 20 adresses internes et externes que vous souhaitez protéger contre l’emprunt d’identité.  <br/> |
|Ajouter des domaines à protéger  <br/> |Sélectionnez **+ Ajouter une condition, le domaine du destinataire est**. Entrez le domaine personnalisé associé à votre abonnement Microsoft 365, si vous en avez défini un. Vous pouvez entrer plusieurs domaines.  <br/> |
|Choisir des actions  <br/> |Si un message électronique est envoyé par un utilisateur représenté : choisissez **Rediriger le message vers une autre adresse de messagerie**, puis tapez l’adresse de messagerie de l’administrateur de sécurité ; par exemple, *Alice <span> <span> @contoso. com*.          Si le courrier électronique est envoyé par un domaine dont l’identité a été empruntée : sélectionnez **Mettre le message en quarantaine**.  <br/> |
|Veille des boîtes aux lettres  <br/> |Par défaut, la veille des boîtes aux lettres est activée lorsque vous créez une stratégie anti-hameçonnage. Laissez ce paramètre **activé** pour obtenir de meilleurs résultats.  <br/> |
|Ajouter des expéditeurs et domaines de confiance  <br/> |Ici, vous pouvez ajouter votre propre domaine ou tout autre domaine approuvé.  <br/> |
|Appliqué à  <br/> |Sélectionnez **Le domaine du destinataire est**. Sous **Un de ces éléments**, sélectionnez **Choisir**. Sélectionnez **+ Ajouter**. Activez la case à cocher en regard du nom du domaine, par exemple, *contoso. <span> <span> com*, dans la liste, puis sélectionnez **Ajouter**. Sélectionnez **Terminé**.  <br/> |
   
Pour plus d’informations, reportez-vous à la rubrique [set up Office 365 ATP anti-phishing Policies](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-anti-phishing-policies).
  
## <a name="protect-against-malicious-attachments-files-and-links-with-advanced-threat-protection-atp"></a>Se protéger contre les pièces jointes, les fichiers et les liens malveillants à l’aide de la protection avancée contre les menaces

![Bannière pointant vers https://aka.ms/aboutM365preview .](../media/m365admincenterchanging.png)

Tout d’abord, assurez- <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a> vous que le nouvel aperçu du centre d’administration est activé dans le centre d’administration. Activez le bouton bascule en regard du texte dans **le nouveau centre d’administration**.

   ![Le nouvel aperçu du centre d’administration sur.](../media/previewon.png)

Si vous ne voyez pas encore la page de **configuration** avec des cartes dans votre client, voir comment effectuer ces étapes dans le centre de sécurité et de &amp; conformité. Consultez la rubrique [configurer des pièces jointes approuvées ATP dans le centre de sécurité & conformité](#set-up-atp-safe-attachments-in-the-security--compliance-center) et [configurer des liens fiables ATP dans le centre de conformité & de sécurité](#set-up-atp-safe-links-in-the-security--compliance-center).

1.  Dans le volet de navigation de gauche, sélectionnez **configuration**.
2. Sur la page de **configuration** , choisissez **Afficher** sur la carte **de protection avancée** contre les menaces.</br></br>
    ![Choisissez afficher sur la protection renforcée contre les menaces avancées.](../media/startatp.png) 

3. Sur la page **améliorer la protection contre les menaces avancées** , sélectionnez **prise en main**.
4. Dans le volet qui s’ouvre, activez les cases à cocher en regard de **liens et pièces jointes dans courrier électronique**, **analyser les fichiers dans SharePoint, OneDrive et teams**, puis **analysez les liens dans les applications Office Online et de bureau** sous **analyser les éléments de contenu malveillant**.

      - Sous **liens et pièces jointes dans courrier électronique**, tapez tous les utilisateurs ou les utilisateurs spécifiques dont vous souhaitez que les messages électroniques soient analysés.

    ![Activez toutes les cases à cocher dans augmenter la protection contre les menaces avancées.](../media/setatp.png)
5. Choisissez **créer des stratégies** pour activer les pièces jointes approuvées ATP et les liens fiables ATP.

### <a name="set-up-atp-safe-attachments-in-the-security--compliance-center"></a>Configuration des pièces jointes approuvées ATP dans le centre de sécurité & conformité

Les personnes envoient, reçoivent et partagent régulièrement des pièces jointes, telles que des documents, des présentations, des feuilles de calcul, etc. Il n’est pas toujours facile de déterminer si une pièce jointe est fiable ou malveillante en regardant un message électronique. Office 365 Advanced Threat Protection inclut la protection des pièces jointes sécurisées ATP, mais cette protection n’est pas activée par défaut. Nous vous recommandons de créer une règle pour commencer à utiliser cette protection. Cette protection s’étend aux fichiers dans SharePoint, OneDrive et Microsoft Teams.
  
Pour créer une stratégie de pièces jointes approuvées pour la protection avancée contre les menaces, regardez [cette courte vidéo](https://support.office.com/article/e7e68934-23dc-4b9c-b714-e82e27a8f8a5)ou effectuez les étapes suivantes :
  
1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous à l’aide de votre compte d’administrateur. 
    
2. Dans le centre de navigation de gauche du centre de sécurité &amp; conformité, sous gestion des **menaces**, sélectionnez **stratégie**.
    
3. Sur la page stratégie, choisissez **pièces jointes approuvées ATP**.
    
4. Sur la page pièces jointes fiables, appliquez largement cette protection en activant la case à cocher Activer la protection avancée contre **les menaces pour SharePoint, OneDrive et Microsoft teams** . 
    
5. Sélectionnez cette option **+** pour créer une stratégie. 
    
6. Appliquez les paramètres dans le tableau suivant. 
    
7. Après avoir examiné vos paramètres, choisissez **créer cette stratégie** ou **Enregistrer**, selon le cas.
    

|**Paramètre ou option**|**Valeur recommandée** <br/>|
|:-----|:-----|
|Nom  <br/> |Bloquer les courriers électroniques actuels et futurs avec des programmes malveillants détectés.  <br/> |
|Description  <br/> |Bloquer les e-mails et pièces jointes en cours et à venir avec des programmes malveillants détectés.  <br/> |
|Enregistrer les pièces jointes réponse inconnue contre les programmes malveillants  <br/> |Sélectionnez **bloquer-bloquer les courriers électroniques et pièces jointes actuels et futurs avec des programmes malveillants détectés**.  <br/> |
|Redirection de la pièce jointe sur la détection  <br/> |Activer la redirection (activez cette case à cocher) Entrez le compte administrateur ou une configuration de boîte aux lettres pour la mise en quarantaine.          Appliquer la sélection ci-dessus si l’analyse anti-programmes malveillants pour les pièces jointes expire ou si une erreur se produit (sélectionnez cette case).  <br/> |
|Appliqué à  <br/> |Le domaine du destinataire est. . . Sélectionnez votre domaine.  <br/> |
   
Pour plus d’informations, reportez-vous à la rubrique [set up Office 365 ATP anti-phishing Policies](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-anti-phishing-policies).
  
### <a name="set-up-atp-safe-links-in-the-security--compliance-center"></a>Configurer les liens fiables ATP dans le centre de sécurité & conformité

Les pirates masquent parfois des sites Web malveillants dans des liens dans des courriers électroniques ou dans d’autres fichiers. Office 365 ATP Safe Links (liens fiables ATP), composant d’Office 365 Advanced Threat Protection, peut vous aider à protéger votre organisation en fournissant un temps de vérification des adresses Web (URL) dans les messages électroniques et les documents Office. La protection est définie via des stratégies de liens fiables ATP.
  
Nous vous recommandons d’effectuer les opérations suivantes :
  
- Modifiez la stratégie par défaut pour augmenter la protection.
    
- Ajoutez une nouvelle stratégie ciblée pour tous les destinataires de votre domaine.
    
Pour configurer des liens fiables ATP, regardez [cette vidéo de formation courte](https://support.office.com/article/61492713-53c2-47da-a6e7-fa97479e97fa)ou effectuez les étapes suivantes :
  
1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous à l’aide de votre compte d’administrateur. 
    
2. Dans le centre de navigation de gauche du centre de sécurité &amp; conformité, sous gestion des **menaces**, sélectionnez **stratégie**.
    
3. Sur la page stratégie, choisissez **liens fiables ATP**.
    
Pour modifier la stratégie par défaut :
  
1. Sur la page Liens approuvés, sous **stratégies qui s’appliquent à l’ensemble de l’organisation**, sélectionnez la stratégie **par défaut** . 
    
2. Sous **paramètres qui s’appliquent au contenu à l’exception du courrier électronique**, sélectionnez **Microsoft 365 apps pour entreprise, Office pour iOS et Android**.
    
3. Cliquez sur **Enregistrer**. 
    
Pour créer une stratégie ciblée pour tous les destinataires de votre domaine, procédez comme suit :
  
1. Sur la page Liens approuvés, sous **stratégies qui s’appliquent à l’ensemble de l’organisation**, cliquez sur **+** pour créer une stratégie. 
    
2. Appliquez les paramètres présentés dans le tableau suivant.
    
3. Cliquez sur **Enregistrer**. 

|**Paramètre ou option**|**Valeur recommandée** <br/>|
|:-----|:-----|
|Nom  <br/> |Stratégie de liens fiables pour tous les destinataires dans le domaine  <br/> |
|Sélectionner l’action pour les URL potentiellement malveillantes dans les messages  <br/> |Sélectionnez **les URL activées seront réécrites et vérifiées par rapport à une liste de liens malveillants connus lorsque l’utilisateur clique sur le lien**.  <br/> |
|Utiliser les pièces jointes fiables pour analyser le contenu téléchargeable  <br/> |Activez cette case à cocher.  <br/> |
|Appliqué à  <br/> |Le domaine du destinataire est. . . Sélectionnez votre domaine.  <br/> |
   
Pour plus d’informations, reportez-vous à la rubrique [Office 365 ATP Safe Links](https://go.microsoft.com/fwlink/?linkid=2016138&amp;clcid=0x409).
  
## <a name="turn-on-the-unified-audit-log"></a>Activer le journal d’audit unifié

Après avoir activé la recherche du journal d’audit dans le &amp; Centre de sécurité conformité, vous pouvez conserver l’administrateur et d’autres activités de l’utilisateur dans le journal et le Rechercher. 

Vous devez disposer du rôle journaux d’audit dans Exchange Online pour activer ou désactiver la recherche dans le journal d’audit dans votre abonnement Microsoft 365. Par défaut, ce rôle est affecté aux groupes de rôles gestion de la conformité et gestion de l’organisation dans la page autorisations du centre d’administration Exchange. Les administrateurs globaux dans Microsoft 365 sont membres de ce groupe par défaut.

1. Pour activer la recherche dans le journal d’audit, accédez au centre d’administration à l’adresse, puis <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a> Choisissez **conformité** sous **centres d’administration** dans le volet de navigation de gauche. 
2. Sur la **page conformité de Microsoft 365** , sélectionnez **plus de ressources**, puis **ouvrez** la carte du ** &amp; Centre de sécurité Office 365** .

    ![Sélectionnez ouvrir sur le & de conformité cars.](../media/gotosecandcomp.png)
3. Sur la page sécurité et conformité, sélectionnez **recherche** , puis **recherche dans le journal d’audit**.
1. En haut de la page **recherche du journal d’audit** , sélectionnez **activer l’audit**.

Une fois que la fonctionnalité est activée, vous pouvez rechercher des fichiers, des dossiers et de nombreuses activités. Pour plus d’informations, consultez [la rubrique Rechercher dans le journal d’audit](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance).

## <a name="tune-up-anonymous-sharing-settings-for-sharepoint-and-onedrive-files-and-folders"></a>Optimisation des paramètres de partage anonyme pour les fichiers et dossiers SharePoint et OneDrive

(modifiez l’expiration de la liaison anonyme par défaut en 14 jours, définissez le type de partage par défaut sur « personnes spécifiques ») Pour modifier les paramètres de partage pour OneDrive et SharePoint, procédez comme suit :
1. Accédez au centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a> , puis choisissez **SharePoint** sous **centres d’administration** dans le service de navigation de gauche. 
2. Dans le centre d’administration SharePoint, accédez à **stratégies** de \> **partage**.
3. Sur la page **partage** , sous **liens de fichiers et de dossiers**, sélectionnez **personnes spécifiques**, et sous **Paramètres avancés pour les liens tout le monde**, sélectionnez **ces liens doivent expirer dans ce nombre de jours**et tapez 14 (ou un autre nombre de jours pendant lesquels vous souhaitez limiter la durée de vie du lien).

    ![Choisissez des personnes spécifiques et définissez un délai d’expiration de liens de 14 jours.](../media/anyonelinks.png)

## <a name="activity-alerts"></a>Alertes d’activité

Vous pouvez utiliser des alertes d’activité pour effectuer le suivi des activités de l’administrateur et des utilisateurs et détecter les incidents de protection contre les menaces et les logiciels malveillants dans votre organisation. Votre abonnement inclut un ensemble de stratégies par défaut, mais vous pouvez également créer des stratégies personnalisées. Pour plus d’informations, consultez la rubrique [Alert Policies](https://docs.microsoft.com/microsoft-365/compliance/alert-policies). Par exemple, si vous stockez un fichier important dans SharePoint que vous ne voulez pas que quiconque partage en externe, vous pouvez créer une notification qui vous avertit si une personne ne la partage pas.

La figure suivante montre les stratégies par défaut incluses dans Microsoft 365. <br/><br/>
    ![Stratégies d’alerte par défaut incluses avec Microsoft 365](../media/alertpolicies.png)

## <a name="disable-or-manage-calendar-sharing"></a>Désactiver ou gérer le partage de calendrier

Vous pouvez empêcher les membres de votre organisation de partager leurs calendriers, ou vous pouvez également gérer ce qu’ils peuvent partager. Par exemple, vous pouvez limiter le partage aux heures de disponibilité uniquement.

1. Accédez au centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a> et sélectionnez **paramètres** \> **services & compléments**.
2. Sur la page des **compléments & services** , choisissez **calendrier**, puis indiquez si les personnes de votre organisation peuvent partager leurs calendriers avec des personnes extérieures à Office 365 ou Exchange, ou avec n’importe qui. 
    Si vous choisissez l’option partager avec tout le monde, vous pouvez également décider de partager uniquement les informations de disponibilité.

3. Choisissez **enregistrer les modifications** au bas de la page.

    La figure suivante illustre le partage de calendrier non autorisé. </br></br>
    ![Capture d’écran de l’affichage du partage de calendrier externe comme non autorisé.](../media/nocalendarsharing.png)

    La figure suivante illustre les paramètres lorsque le partage de calendrier est autorisé avec un lien de messagerie avec uniquement les informations de disponibilité.

   ![Capture d’écran du partage des disponibilités de calendrier avec tout le monde.](../media/sharefreebusy.png)

Si vos utilisateurs sont autorisés à partager leurs calendriers, consultez [ces instructions](https://support.office.com/article/7ecef8ae-139c-40d9-bae2-a23977ee58d5) pour savoir comment les partager à partir d’Outlook sur le Web.
