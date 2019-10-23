---
title: Renforcer la protection contre les menaces pour Microsoft 365 Business
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
description: Configurez Office 365 Advanced Threat Protection et protégez les données sensibles.
ms.openlocfilehash: fb63ca7e3cf38ecf31aab98e425b02e8b9983bf8
ms.sourcegitcommit: 4d5e4cb3fa3ab45ad15f103c720c77277b22fc23
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "37636749"
---
# <a name="increase-threat-protection"></a>Renforcer la protection contre les menaces

Cet article vous aide à renforcer la protection de votre abonnement Microsoft 365 afin de vous protéger contre le hameçonnage, les programmes malveillants et d’autres menaces. Ces recommandations sont appropriées pour les organisations ayant un besoin accru de sécurité, tels que les agences juridiques et les stages de soins de santé.

Avant de commencer, vérifiez votre score de sécurité Office 365. Le score de sécurité d’Office 365 analyse la sécurité de votre organisation Office 365 en fonction de vos activités normales et des paramètres de sécurité et affecte un score. Commencez par prendre note de votre score actuel. L’exécution des actions recommandées dans cet article augmente votre score. L’objectif est de ne pas atteindre le score maximal, mais de prendre conscience des possibilités de protection de votre environnement qui n’ont pas d’impact négatif sur la productivité de vos utilisateurs. 

Pour plus d’informations, consultez la rubrique [Microsoft Secure score](https://docs.microsoft.com/en-us/office365/securitycompliance/microsoft-secure-score).

## <a name="raise-the-level-of-protection-against-malware-in-mail"></a>Augmenter le niveau de protection contre les programmes malveillants dans les messages

Votre environnement Office 365 ou Microsoft 365 inclut une protection contre les programmes malveillants, mais vous pouvez augmenter cette protection en bloquant les pièces jointes avec des types de fichiers couramment utilisés pour les programmes malveillants. Pour augmenter la protection contre les programmes malveillants dans le courrier électronique :
  
1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous avec vos informations d’identification de compte d’administrateur. 
    
2. Dans le centre de navigation &amp; de gauche du centre de sécurité conformité Office 365, **sous gestion des menaces**, sélectionnez **stratégie** \> **anti-programme malveillant**.
    
3. Double-cliquez sur la stratégie par défaut pour modifier cette stratégie à l’échelle de l’entreprise.
    
4. Cliquez sur **paramètres**.
    
5. Sous **Common Attachment types Filter**, sélectionnez **activé**. Les types de fichiers bloqués sont répertoriés dans la fenêtre située directement en dessous de ce contrôle.  Veillez à ajouter ces FileTypes :
   - ADE, ADP, Ani, bas, bat, chm, cmd, com, cpl, CRT, HLP, HT, HTA, inf, ins, fournisseur de services Internet, Job, js, jse, lnk, MDA, de mdb, MDE, mdz, MSC, MSI, MSP, MST, PCD, reg, SCR, SCT, SHS, URL, VB, VBE, vbs, WSC, wsf, WSH  <br/> Vous pouvez ajouter ou supprimer des types de fichiers ultérieurement, si nécessaire.
    
6. Cliquez sur **Enregistrer**.
    
Pour plus d’informations, consultez la rubrique [protection contre les programmes malveillants](https://go.microsoft.com/fwlink/?linkid=2015692&amp;clcid=0x409).
  
## <a name="protect-against-ransomware"></a>Protéger contre les ransomware

Les ransomware limitent l’accès aux données en chiffrant les fichiers ou en verrouillant les écrans d’ordinateur. Il tente ensuite de extort l’argent des victimes en demandant « ransomware », généralement sous forme de cryptocurrencies comme Bitcoin, dans Exchange pour accéder aux données. 
  
Vous pouvez vous protéger contre les ransomware en créant une ou plusieurs règles de flux de messagerie pour bloquer les extensions de fichiers couramment utilisées pour les ransomware (elles ont été ajoutées à l’étape [augmenter le niveau de protection contre les programmes malveillants dans le courrier](#raise-the-level-of-protection-against-malware-in-mail) ) ou pour avertir les utilisateurs qui reçoivent ces pièces jointes dans les messages électroniques.

Outre les fichiers que vous avez bloqués à l’étape précédente, il est également recommandé de créer une règle pour avertir les utilisateurs avant l’ouverture de pièces jointes de fichier Office qui incluent des macros. Les ransomware peuvent être masqués dans les macros, nous les avertirons donc que les utilisateurs ne pourront pas ouvrir ces fichiers à partir de personnes qu’ils ne connaissent pas.

Pour créer une règle de transport de messagerie :
  
1. <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a> Accédez au centre d’administration et choisissez centres **** \> d’administration **Exchange**.
    
2. Dans la catégorie **flux de messagerie** , cliquez sur **règles**.
    
3. Cliquez **+** sur, puis sur **créer une règle**.
    
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
   
Pour plus d’informations, voir :
  
- [Comment traiter les ransomware](https://go.microsoft.com/fwlink/?linkid=2016501&amp;clcid=0x409)
    
- [Restaurer votre espace OneDrive](https://support.office.com/article/fa231298-759d-41cf-bcd0-25ac53eb8a15.aspx)
    


## <a name="stop-auto-forwarding-for-email"></a>Arrêter le transfert automatique pour le courrier électronique

Les pirates qui accèdent à la boîte aux lettres d’un utilisateur peuvent voler votre courrier en définissant la boîte aux lettres pour transférer automatiquement le courrier électronique. Cela peut se produire même sans la sensibilisation de l’utilisateur. Vous pouvez éviter cela en configurant une règle de flux de messagerie. 
  
Pour créer une règle de transport de courrier, regardez [cette courte vidéo](https://support.office.com/article/f9d693ba-5c78-47c0-b156-8e461e062aa7) ou procédez comme suit :
  
1. Dans le centre d’administration Microsoft 365, cliquez sur **centres** \> d’administration **Exchange**.
    
2. Dans la catégorie **flux de messagerie** , cliquez sur **règles**.
    
3. Cliquez **+** sur, puis sur **créer une règle**.
    
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
    
2. Dans le centre de sécurité &amp; conformité d’Office 365, dans le volet de navigation de gauche, sous **gestion des menaces**, sélectionnez **stratégie**.
    
3. Sur la page **stratégie** , choisissez **protection contre le hameçonnage ATP**.
    
4. Sur la page **anti-hameçonnage** , sélectionnez **+ créer**. Un Assistant s’ouvre et vous guide tout au long de la définition de votre stratégie anti-hameçonnage.
    
5. Spécifiez le nom, la description et les paramètres de votre stratégie, comme recommandé dans le graphique ci-dessous. Pour plus d’informations, consultez la rubrique [en savoir plus sur les options de stratégie anti-hameçonnage ATP](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-anti-phishing-policies#learn-about-atp-anti-phishing-policy-options) . 
    
6. Une fois que vous avez vérifié vos paramètres, choisissez **créer cette stratégie** ou **Enregistrer**, selon le cas.
    

|**Paramètre ou option**<br/>|**Paramètre recommandé** <br/>|
|:-----|:-----|
|Nom  <br/> |Domaine et équipe de campagne la plus intéressante  <br/> |
|Description  <br/> |Assurez-vous que le personnel le plus important et que notre domaine ne sont pas empruntés.  <br/> |
|Ajouter des utilisateurs à protéger  <br/> |Sélectionnez **+ Ajouter une condition, le destinataire est**. Tapez noms d’utilisateur ou entrez l’adresse de messagerie du candidat, du gestionnaire de campagnes et d’autres membres importants du personnel. Vous pouvez ajouter jusqu’à 20 adresses internes et externes que vous souhaitez protéger contre l’emprunt d’identité.  <br/> |
|Ajouter des domaines à protéger  <br/> |Sélectionnez **+ Ajouter une condition, le domaine du destinataire est**. Entrez le domaine personnalisé associé à votre abonnement Microsoft 365, si vous en avez défini un. Vous pouvez entrer plusieurs domaines.  <br/> |
|Choisir les actions  <br/> |Si un message électronique est envoyé par un utilisateur représenté : choisissez **Rediriger le message vers une autre adresse de messagerie**, puis tapez l’adresse de messagerie de l’administrateur de sécurité ; par exemple, *Alice<span><span>@contoso. com*.          Si le courrier électronique est envoyé par un domaine emprunté : choisissez **mettre en quarantaine le message**.  <br/> |
|Intelligence des boîtes aux lettres  <br/> |Par défaut, l’intelligence de boîte aux lettres est activée lorsque vous créez une nouvelle stratégie anti-hameçonnage. Laissez ce paramètre **activé** pour obtenir les meilleurs résultats.  <br/> |
|Ajouter des expéditeurs et des domaines approuvés  <br/> |Ici, vous pouvez ajouter votre propre domaine ou tout autre domaine approuvé.  <br/> |
|Appliqué à  <br/> |Sélectionnez **le domaine du destinataire**. Sous **l’un de ces éléments**, sélectionnez **choisir**. Sélectionnez **+ Ajouter**. Activez la case à cocher en regard du nom du domaine, par exemple, *Contoso<span> . com <span>*, dans la liste, puis sélectionnez **Ajouter**. Sélectionnez **Terminer**.  <br/> |
  
## <a name="protect-against-malicious-attachments-and-files-with-atp-safe-attachments"></a>Protection contre les pièces jointes et les fichiers malveillants avec des pièces jointes fiables ATP

Les personnes envoient, reçoivent et partagent régulièrement des pièces jointes, telles que des documents, des présentations, des feuilles de calcul, etc. Il n’est pas toujours facile de déterminer si une pièce jointe est fiable ou malveillante en regardant un message électronique. Office 365 Advanced Threat Protection inclut la protection des pièces jointes sécurisées ATP, mais cette protection n’est pas activée par défaut. Nous vous recommandons de créer une règle pour commencer à utiliser cette protection. Cette protection s’étend aux fichiers dans SharePoint, OneDrive et Microsoft Teams.
  
Pour créer une stratégie de pièces jointes approuvées pour la protection avancée contre les menaces, regardez [cette courte vidéo](https://support.office.com/article/e7e68934-23dc-4b9c-b714-e82e27a8f8a5)ou effectuez les étapes suivantes :
  
1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous à l’aide de votre compte d’administrateur. 
    
2. Dans le centre de sécurité &amp; conformité d’Office 365, dans le volet de navigation de gauche, sous **gestion des menaces**, sélectionnez **stratégie**.
    
3. Sur la page stratégie, choisissez **pièces jointes approuvées ATP**.
    
4. Sur la page pièces jointes fiables, appliquez largement cette protection en activant la case à cocher Activer la protection avancée contre **les menaces pour SharePoint, OneDrive et Microsoft teams** . 
    
5. Sélectionnez **+** cette option pour créer une stratégie. 
    
6. Appliquez les paramètres dans le tableau suivant. 
    
7. Une fois que vous avez vérifié vos paramètres, choisissez **créer cette stratégie** ou **Enregistrer**, selon le cas.
    

|**Paramètre ou option**|**Paramètre recommandé** <br/>|
|:-----|:-----|
|Nom  <br/> |Bloquer les courriers électroniques actuels et futurs avec des programmes malveillants détectés.  <br/> |
|Description  <br/> |Bloquer les e-mails et pièces jointes en cours et à venir avec des programmes malveillants détectés.  <br/> |
|Enregistrer les pièces jointes réponse inconnue contre les programmes malveillants  <br/> |Sélectionnez **bloquer-bloquer les courriers électroniques et pièces jointes actuels et futurs avec des programmes malveillants détectés**.  <br/> |
|Redirection de la pièce jointe sur la détection  <br/> |Activer la redirection (activez cette case à cocher) Entrez le compte administrateur ou une configuration de boîte aux lettres pour la mise en quarantaine.          Appliquer la sélection ci-dessus si l’analyse anti-programmes malveillants pour les pièces jointes expire ou si une erreur se produit (sélectionnez cette case).  <br/> |
|Appliqué à  <br/> |Le domaine du destinataire est. . . Sélectionnez votre domaine.  <br/> |
   
Pour plus d’informations, reportez-vous à la rubrique [set up Office 365 ATP anti-phishing Policies](https://go.microsoft.com/fwlink/?linkid=2016505&amp;clcid=0x409).
  


## <a name="protect-against-phishing-attacks-with-atp-safe-links"></a>Protection contre les attaques de hameçonnage à l’aide de liens fiables ATP

Les pirates masquent parfois des sites Web malveillants dans des liens dans des courriers électroniques ou dans d’autres fichiers. Office 365 ATP Safe Links (liens fiables ATP), composant d’Office 365 Advanced Threat Protection, peut vous aider à protéger votre organisation en fournissant un temps de vérification des adresses Web (URL) dans les messages électroniques et les documents Office. La protection est définie via des stratégies de liens fiables ATP.
  
Nous vous recommandons d’effectuer les opérations suivantes :
  
- Modifiez la stratégie par défaut pour augmenter la protection.
    
- Ajoutez une nouvelle stratégie ciblée pour tous les destinataires de votre domaine.
    
Pour configurer des liens fiables ATP, regardez [cette vidéo de formation courte](https://support.office.com/article/61492713-53c2-47da-a6e7-fa97479e97fa)ou effectuez les étapes suivantes :
  
1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous à l’aide de votre compte d’administrateur. 
    
2. Dans le centre de sécurité &amp; conformité d’Office 365, dans le volet de navigation de gauche, sous **gestion des menaces**, sélectionnez **stratégie**.
    
3. Sur la page stratégie, choisissez **liens fiables ATP**.
    
Pour modifier la stratégie par défaut :
  
1. Sur la page Liens approuvés, sous **stratégies qui s’appliquent à l’ensemble de l’organisation**, sélectionnez la stratégie **par défaut** . 
    
2. Sous **paramètres qui s’appliquent au contenu à l’exception du courrier électronique**, sélectionnez **Office 365 ProPlus, Office pour iOS et Android**.
    
3. Cliquez sur **Enregistrer**. 
    
Pour créer une stratégie ciblée pour tous les destinataires de votre domaine, procédez comme suit :
  
1. Sur la page Liens approuvés, sous **stratégies qui s’appliquent à l’ensemble de l’organisation**, cliquez sur **+** pour créer une stratégie. 
    
2. Appliquez les paramètres présentés dans le tableau suivant.
    
3. Cliquez sur **Enregistrer**. 

|**Paramètre ou option**|**Paramètre recommandé** <br/>|
|:-----|:-----|
|Nom  <br/> |Stratégie de liens fiables pour tous les destinataires dans le domaine  <br/> |
|Sélectionner l’action pour les URL potentiellement malveillantes dans les messages  <br/> |Sélectionnez **les URL activées seront réécrites et vérifiées par rapport à une liste de liens malveillants connus lorsque l’utilisateur clique sur le lien**.  <br/> |
|Utiliser les pièces jointes fiables pour analyser le contenu téléchargeable  <br/> |Activez cette case à cocher.  <br/> |
|Appliqué à  <br/> |Le domaine du destinataire est. . . Sélectionnez votre domaine.  <br/> |
   
Pour plus d’informations, reportez-vous à la rubrique [Office 365 ATP Safe Links](https://go.microsoft.com/fwlink/?linkid=2016138&amp;clcid=0x409).

## <a name="go-to-intune-admin-center"></a>Accéder au centre d’administration Intune

1. Connectez-vous à [Azure Portal](https://portal.azure.com/).

2. Sélectionnez **tous les services** et tapez *Intune* dans la **zone de recherche**.

3. Une fois que les résultats s’affichent, cliquez sur le bouton Démarrer en regard de **Microsoft Intune** pour en faire un favori et le retrouver facilement plus tard.

En plus du centre d’administration, vous pouvez utiliser Intune pour inscrire et gérer les appareils de votre organisation. Pour plus d’informations, reportez-vous à la rubrique [fonctionnalités par méthode d’enregistrement pour les périphériques Windows](https://docs.microsoft.com/intune/enrollment-method-capabs) et les [options d’enregistrement pour les appareils gérés par Intune](https://docs.microsoft.com/intune/enrollment-options).
