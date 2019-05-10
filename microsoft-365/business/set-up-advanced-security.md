---
title: Configurer des stratégies de sécurité avancées pour les utilisateurs professionnels de Microsoft 365
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
description: Configurez Office 365 Advanced Threat Protection et protégez les données sensibles.
ms.openlocfilehash: 4728e11a16fdf8a461f5687632df75699923f846
ms.sourcegitcommit: db1dfb2df2c2f7beced3b57bc772d106c189e88a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "33663634"
---
# <a name="set-up-advanced-security-policies"></a>Configurer des stratégies de sécurité avancées

En plus des stratégies que vous pouvez configurer dans le [Centre d’administration](security-features.md#microsoft-365-business-admin-center-security-features), vous pouvez ajouter une protection supplémentaire contre les menaces informatiques en configurant [Office 365 Advanced Threat Protection](https://support.office.com/article/e100fe7c-f2a1-4b7d-9e08-622330b83653) (ATP). Vous pouvez également protéger les informations sensibles en configurant la protection [contre la perte de données](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) (DLP), Azure information protection (AIP), [l’archivage Exchange Online](https://products.office.com/exchange/microsoft-exchange-online-archiving-email)et gérer vos appareils dans le [portail Intune](#go-to-intune-admin-center).

Pour obtenir une vue d’ensemble des moyens les plus importants de protection de votre entreprise, notamment l’utilisation de l’authentification multiFACTEUR (MFA) pour créer une deuxième forme de connexion, consultez la rubrique [Top 10 des méthodes de sécurisation de Microsoft 365 business plan](https://docs.microsoft.com/office365/admin/security-and-compliance/secure-your-business-data) .

Pour obtenir des instructions faciles à suivre, consultez [la rubrique sécuriser vos vidéos de formation](https://support.office.com/article/e12187b8-216a-4490-9e3b-df34a06fb787) pour les entreprises.

## <a name="increase-email-malware-protection"></a>Augmenter la protection contre les programmes malveillants

Les programmes malveillants sont des logiciels qui peuvent endommager vos ordinateurs ou le réseau, et éventuellement vous dérober des données, y compris des informations personnelles ou clientes. Microsoft 365 Business inclut un niveau de base de protection contre les programmes malveillants, mais vous pouvez augmenter cette protection en configurant des paramètres supplémentaires. Voir [activer](https://support.office.com/article/02b5783a-eea0-42e8-8856-62440718c3f0) la vidéo de formation à la détection de programmes malveillants pour obtenir des instructions.

## <a name="set-up-advanced-threat-protection-features"></a>Configurer les fonctionnalités avancées de protection contre les menaces

- **Protection contre les pièces jointes potentiellement dangereuses:** La fonctionnalité ATP identifie le contenu malveillant en ouvrant des pièces jointes de courrier électronique dans un environnement virtuel et en effectuant une analyse du comportement résultant. Le contenu est évalué pour déterminer son objectif (normal ou malveillant) et la protection avancée contre la remise de pièces jointes potentiellement dangereuses, ce qui vous permet de vous protéger contre les systèmes de hameçonnage et les infections par ransomware. Pour activer la protection des pièces jointes, consultez la rubrique relative à la configuration de la documentation d’aide [des pièces jointes approuvées pour Office 365](https://support.office.com/article/078eb946-819a-4e13-8673-fe0c0ad3a775) et [protection contre les fichiers malveillants](https://support.office.com/article/e7e68934-23dc-4b9c-b714-e82e27a8f8a5) vidéo de formation.
    
- **Protégez votre environnement lorsque les utilisateurs cliquent sur des liens malveillants:** La fonctionnalité ATP examine également les liens dans les courriers électroniques lorsqu’un utilisateur clique dessus. Si un lien n’est pas sécurisé, l’utilisateur est averti de ne pas visiter le site ou d’être informé que le site a été bloqué. Cela permet de vous protéger contre les schémas de phishing. Pour activer ce paramètre, consultez la rubrique [set up Office 365 ATP Safe Links](https://docs.microsoft.com/en-us/office365/securitycompliance/set-up-atp-safe-links-policies) Help documentation de l’aide et protégez-vous [contre les sites malveillants](https://support.office.com/article/61492713-53c2-47da-a6e7-fa97479e97fa) vidéo de formation.

- **Protégez votre environnement de la tentative d’hameçonnage:**  La protection contre le hameçonnage ATP applique un ensemble de modèles d’apprentissage automatique avec des algorithmes de détection d’emprunt d’identité aux messages entrants pour assurer une protection contre les attaques par hameçonnage lorsqu’une personne tente d’extraire des informations de votre part en prétendant être une Prenez. Pour l’activer, voir Configurer la documentation d’aide [anti-hameçonnage ATP](https://docs.microsoft.com/office365/securitycompliance/set-up-anti-phishing-policies) et [protéger contre les tentatives de hameçonnage](https://support.office.com/article/86c425e1-1686-430a-9151-f7176cce4f2c) vidéo de formation courte.

## <a name="set-up-dlp-features"></a>Configurer les fonctionnalités DLP

Voir [Create a DLP Policy from a template](https://support.office.com/article/59414438-99f5-488b-975c-5023f2254369) pour obtenir un exemple sur la façon de configurer une stratégie de protection contre les informations d’identification personnelle (PII). 
  
DLP comprend de nombreux modèles de stratégie prêts à l’emploi pour de nombreux paramètres régionaux différents. Par exemple, les données financières de l’Australie, le Canada Personal Information Act, les données financières américaines, etc. Consultez la rubrique relative aux [modèles de stratégie DLP](https://support.office.com/article/c2e588d3-8f4f-4937-a286-8c399f28953a) pour une liste complète. Tous ces modèles peuvent être activés de la même manière que l’exemple de modèle PII. 
  
## <a name="set-up-email-retention-with-exchange-online-archiving"></a>Configurer la rétention du courrier électronique avec archivage Exchange Online

 Les fonctionnalités de licence d' **archivage Exchange Online** vous permettent de conserver des normes de conformité et de réglementation en conservant le contenu de la messagerie électronique à des fins de découverte électronique. Elle permet également de réduire les risques en cas de litige et de récupérer les données après une violation de la sécurité ou lorsque vous devez récupérer des éléments supprimés. Pour activer ces fonctionnalités, vous pouvez utiliser la conservation pour litige pour conserver tout le contenu d’un utilisateur ou utiliser des stratégies de rétention pour une personnalisation plus importante. 
  
**Conservation pour litige:** Vous pouvez conserver tout le contenu des boîtes aux lettres, y compris les éléments supprimés, en mettant la boîte aux lettres entière d’un utilisateur en conservation pour litige. 
    
Pour placer une boîte aux lettres en conservation pour litige, dans le centre d’administration:
    
1. Dans le volet de navigation de gauche **** \> , accédez à utilisateurs **actifs**.
    
2. Sélectionnez un utilisateur dont vous souhaitez placer la boîte aux lettres en conservation pour litige et, dans le volet utilisateur, développez **paramètres de messagerie** , puis en regard de **paramètres supplémentaires** , choisissez **modifier les propriétés Exchange**.
    
3. Sur la page boîte aux lettres de l’utilisateur, choisissez les fonctionnalités de boîte aux lettres * * dans le volet de navigation de gauche, puis cliquez sur le lien **activer** en **conservation pour litige**.
    
4. Dans la boîte de dialogue **conservation pour litige** , vous pouvez spécifier la durée de la conservation pour litige dans le champ Durée de la **conservation pour litige** , laissez le champ vide si vous voulez placer un blocage infini. Vous pouvez également ajouter des notes et diriger le propriétaire de la boîte aux lettres vers un site Web vous devrez peut-être \> **** en savoir plus sur la conservation pour litige.
    
**Rétention:** Vous pouvez activer des stratégies de rétention personnalisées, par exemple, pour conserver un certain temps ou supprimer définitivement le contenu à la fin de la période de rétention. Pour en savoir plus, consultez la rubrique [vue d’ensemble des stratégies de](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423)rétention.
## <a name="set-up-azure-information-protection-features"></a>Configurer les fonctionnalités Azure information protection

Azure information protection (AIP) est une solution basée sur le Cloud qui permet à une organisation de classer et, le cas échéant, de protéger ses documents et e-mails en appliquant des étiquettes. Les étiquettes peuvent être appliquées automatiquement par les administrateurs qui définissent des règles et des conditions, manuellement par les utilisateurs ou une combinaison pour laquelle les utilisateurs reçoivent des recommandations.

La possibilité d’appliquer les restrictions suivantes lors de l’envoi de messages électroniques dans Outlook sur le Web est automatiquement activée pour tous les utilisateurs:
  
- **Ne pas transférer**: les destinataires peuvent lire le message, mais ils ne peuvent pas transférer, imprimer ou copier du contenu
    
- **Encrypt**: l’intégralité du message est chiffrée. Les destinataires doivent prendre des mesures supplémentaires pour confirmer leur identité avant d’accéder au contenu chiffré et ne peuvent pas supprimer le chiffrement.
    
- **Confidential**: donne aux employés de votre organisation des autorisations complètes sur le contenu et les pièces jointes de messagerie, mais pas sur les personnes externes à votre organisation. Les propriétaires de données peuvent suivre et révoquer du contenu à tout moment.
    
- **Hautement confidentiel**: cette restriction peut être appliquée aux données hautement confidentielles, ce qui permet aux employés d’afficher, de modifier et de répondre, mais pas de transférer, d’imprimer ou de copier les données. Les propriétaires de données peuvent suivre et révoquer du contenu à tout moment.

### <a name="make-sure-azure-information-protection-is-activated"></a>Vérifier que Azure information protection est activé

Pour vérifier qu’AIP est activé:

1. Connectez-vous à [Azure Portal](https://portal.azure.com/).

2. Sélectionnez **tous les services** et tapez *Azure information protection* dans la **zone de recherche**.

3. Une fois que les résultats s’affichent, cliquez sur le bouton Démarrer en regard d' **Azure information protection** pour en faire un favori et le retrouver facilement plus tard.

4. Sélectionnez **activation de protection** **Azure information protection** \> et assurez-vous que l’État est défini sur activé. 

### <a name="view-the-azure-information-protection-policy-and-default-labels"></a>Afficher la stratégie Azure information protection et les étiquettes par défaut 

Pour afficher et modifier les étiquettes existantes:

1. Dans le tableau de bord Azure information protection **** \> , sélectionnez **étiquettes**classifications. <br/>![Étiquettes standard pour Azure information protection.](media/AIPLabels.png)

2. Vous pouvez choisir n’importe quelle étiquette pour afficher les options, vous pouvez modifier le nom d’affichage, les couleurs, etc.
 
3. Pour créer les vôtres, consultez la rubrique [Modify and Create New labels](https://docs.microsoft.com/azure/information-protection/infoprotect-tutorial-step2) . 

### <a name="install-the-azure-information-protection-client-manually"></a>Installation manuelle du client Azure information protection

Pour installer manuellement le client AIP:

1. Téléchargez **AzInfoProtection. exe** à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).
 
2. Vous pouvez vérifier que l’installation a fonctionné en affichant un document Word et en vous assurant que l’option **protéger** est disponible sous l’onglet **Accueil** . <br/>![Onglet protection dans un document Word.](media/Word_Protect.png)

Pour plus d’informations, consultez [la rubrique installer le client](https://docs.microsoft.com/azure/information-protection/infoprotect-tutorial-step3).

## <a name="go-to-intune-admin-center"></a>Accéder au centre d’administration Intune

1. Connectez-vous à [Azure Portal](https://portal.azure.com/).

2. Sélectionnez **tous les services** et tapez *Intune* dans la **zone de recherche**.

3. Une fois que les résultats s’affichent, cliquez sur le bouton Démarrer en regard de **Microsoft Intune** pour en faire un favori et le retrouver facilement plus tard.

En plus du centre d’administration, vous pouvez utiliser Intune pour inscrire et gérer les appareils de votre organisation. Pour plus d’informations, reportez-vous à la rubrique [fonctionnalités par méthode d’enregistrement pour les périphériques Windows](https://docs.microsoft.com/intune/enrollment-method-capabs) et les [options d’enregistrement pour les appareils gérés par Intune](https://docs.microsoft.com/intune/enrollment-options).

## <a name="microsoft-secure-score"></a>Degré de sécurisation Microsoft

