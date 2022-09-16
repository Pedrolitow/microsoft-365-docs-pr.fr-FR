---
title: Configuration d’Azure AD pour le contenu chiffré par Protection des données Microsoft Purview
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection: M365-security-compliance
description: Comment configurer les paramètres d’accès interlocataire Azure AD et les stratégies d’accès conditionnel pour le contenu chiffré par Protection des données Microsoft Purview.
ms.openlocfilehash: 70594e80518a83a8f7aabf05ab2e53da6c8b85f5
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67735783"
---
# <a name="azure-ad-configuration-for-encrypted-content"></a>Configuration d’Azure AD pour le contenu chiffré

Si vous protégez des éléments sensibles tels que des e-mails et des documents à l’aide du chiffrement du service Azure Rights Management à partir de [Protection des données Microsoft Purview](information-protection.md), certaines configurations Azure Active Directory (Azure AD) peuvent empêcher l’accès autorisé à ce contenu chiffré.

De même, si vos utilisateurs reçoivent des e-mails chiffrés d’une autre organisation ou collaborent avec d’autres organisations qui chiffrent des documents à l’aide du service Azure Rights Management, il se peut que vos utilisateurs ne puissent pas ouvrir cet e-mail ou ce document en raison de la façon dont Azure AD est configuré.

Par exemple :

- Un utilisateur ne peut pas ouvrir les e-mails chiffrés envoyés à partir d’une autre organisation. Ou un utilisateur signale que les destinataires d’une autre organisation ne peuvent pas ouvrir un e-mail chiffré qu’il leur a envoyé.

- Votre organisation collabore avec une autre organisation sur un projet commun, et les documents de projet sont protégés en les chiffrant, en leur accordant l’accès à l’aide de groupes dans Azure AD. Les utilisateurs ne peuvent pas ouvrir les documents chiffrés par les utilisateurs de l’autre organisation.

- Les utilisateurs peuvent ouvrir un document chiffré lorsqu’ils se trouvent dans le bureau, mais ils ne peuvent pas le faire lorsqu’ils tentent d’accéder à ce document à distance et qu’ils sont invités à demander l’authentification multifacteur (MFA).

Pour vous assurer que l’accès au service de chiffrement n’est pas bloqué par inadvertance, utilisez les sections suivantes pour configurer Azure AD de votre organisation ou relayer les informations à un administrateur Azure AD d’une autre organisation. Sans accès à ce service, les utilisateurs ne peuvent pas être authentifiés et autorisés à ouvrir du contenu chiffré.

## <a name="cross-tenant-access-settings-and-encrypted-content"></a>Paramètres d’accès entre locataires et contenu chiffré

> [!IMPORTANT]
> Les paramètres d’accès entre locataires d’une autre organisation peuvent être responsables de l’impossibilité pour les utilisateurs d’ouvrir le contenu chiffré par vos utilisateurs ou de l’impossibilité pour vos utilisateurs d’ouvrir le contenu chiffré par l’autre organisation.
> 
> Le message que les utilisateurs voient indique l’organisation qui a bloqué l’accès. Vous devrez peut-être diriger l’administrateur Azure AD d’une autre organisation vers cette section.

Par défaut, il n’y a rien à configurer pour que l’authentification interlocataire fonctionne lorsque les utilisateurs protègent le contenu à l’aide du chiffrement du service Azure Rights Management. Toutefois, votre organisation peut restreindre l’accès à l’aide [des paramètres d’accès interlocataire des identités externes](/azure/active-directory/external-identities/cross-tenant-access-overview) Azure AD. À l’inverse, une autre organisation peut également configurer ces paramètres pour restreindre l’accès avec les utilisateurs de votre organisation. Ces paramètres affectent l’ouverture d’éléments chiffrés, qui incluent des e-mails chiffrés et des documents chiffrés.

Par exemple, une autre organisation peut avoir des paramètres configurés qui empêchent ses utilisateurs d’ouvrir le contenu chiffré par votre organisation. Dans ce scénario, jusqu’à ce que son administrateur Azure AD reconfigure ses paramètres interlocataires, un utilisateur externe qui tente d’ouvrir ce contenu voit un message lui indiquant **qu’Access est bloqué par votre organisation** avec une référence à **votre administrateur client**.

Exemple de message pour l’utilisateur connecté à partir de l’organisation Fabrikam, Inc, lorsque leur instance Azure AD locale bloque l’accès :

![Exemple de message lorsque le locataire Azure AD local bloque l’accès au contenu chiffré.](../media/blocked-by-your-org.png)

Vos utilisateurs verront un message similaire lorsqu’il s’agit de votre configuration Azure AD qui bloque l’accès.

Du point de vue de l’utilisateur connecté, s’il s’agit d’une autre organisation Azure AD responsable du blocage de l’accès, les modifications apportées à **Access sont bloquées par l’organisation** et affichent le nom de domaine de cette autre organisation dans le corps du message. Par exemple :

![Exemple de message lorsqu’un autre locataire Azure AD bloque l’accès au contenu chiffré.](../media/blocked-by-external-org.png)

Chaque fois que les paramètres d’accès entre locataires restreignent l’accès par les applications, ils doivent être configurés pour autoriser l’accès à **Microsoft Azure Information Protection**, qui a l’ID d’application suivant :

````plaintext
00000012-0000-0000-c000-000000000000
````

Si cet accès n’est pas autorisé, les utilisateurs ne peuvent pas être authentifiés et autorisés à ouvrir du contenu chiffré. Cette configuration peut être définie en tant que paramètre par défaut et en tant que paramètre organisationnel :

- Pour autoriser le partage de contenu chiffré avec une autre organisation, créez un paramètre entrant qui autorise l’accès à Microsoft Azure Information Protection (ID : 00000012-0000-0000-c000-000000000000). 

- Pour autoriser l’accès au contenu chiffré que les utilisateurs reçoivent d’autres organisations, créez un paramètre sortant qui autorise l’accès à Microsoft Azure Information Protection (ID : 00000012-0000-0000-c000-000000000000000).

Lorsque ces paramètres sont configurés pour Microsoft Azure Information Protection, l’application affiche **Microsoft Rights Management Services**.

Pour obtenir des instructions sur la configuration de ces paramètres d’accès entre locataires, consultez [Configurer les paramètres d’accès entre locataires pour B2B Collaboration](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-collaboration).

Si vous avez également configuré des stratégies d’accès conditionnel Azure AD qui nécessitent une authentification multifacteur (MFA) pour les utilisateurs, consultez la section suivante sur la configuration de l’accès conditionnel pour le contenu chiffré.

## <a name="conditional-access-policies-and-encrypted-documents"></a>Stratégies d’accès conditionnel et documents chiffrés

Si votre organisation a implémenté des stratégies [d’accès conditionnel Azure Active Directory](/azure/active-directory/conditional-access/overview) qui incluent **Microsoft Azure Information Protection** et que la stratégie s’étend aux utilisateurs externes qui doivent ouvrir des documents chiffrés par votre organisation :

- Pour les utilisateurs externes qui disposent d’un compte Azure AD dans leur propre locataire, nous vous recommandons d’utiliser [des paramètres d’accès interlocataire d’identités externes](/azure/active-directory/external-identities/cross-tenant-access-overview) pour configurer les paramètres d’approbation pour les revendications MFA d’une, plusieurs ou toutes les organisations Azure AD externes.

- Pour les utilisateurs externes non couverts par l’entrée précédente, par exemple, les utilisateurs qui n’ont pas de compte Azure AD ou qui n’ont pas configuré les paramètres d’accès entre locataires pour les paramètres d’approbation, ces utilisateurs externes doivent avoir un compte invité dans votre locataire.
    
Sans l’une de ces configurations, les utilisateurs externes ne pourront pas ouvrir le contenu chiffré et verront un message d’erreur. Le texte du message peut l’informer que son compte doit être ajouté en tant qu’utilisateur externe dans le client, avec des instructions incorrectes pour ce scénario pour **SSe déconnecter et se reconnecter avec un compte utilisateur Azure Active Directory différent.**.

Si vous ne pouvez pas répondre à ces exigences de configuration pour les utilisateurs externes qui doivent ouvrir du contenu chiffré par votre organisation, vous devez supprimer Microsoft Azure Information Protection des stratégies d’accès conditionnel ou exclure des utilisateurs externes des stratégies.

Pour plus d’informations, consultez la question fréquemment posée, [je vois qu’Azure Information Protection est répertorié comme une application cloud disponible pour l’accès conditionnel. Comment cela fonctionne-t-il ?](/azure/information-protection/faqs#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

## <a name="guest-accounts-for-external-users-to-open-encrypted-documents"></a>Comptes invités permettant aux utilisateurs externes d’ouvrir des documents chiffrés

Vous aurez peut-être besoin de comptes invités dans votre locataire Azure AD pour permettre aux utilisateurs externes d’ouvrir des documents chiffrés par votre organisation. Options pour créer les comptes invités :

- Créez vous-même ces comptes invités. Vous pouvez spécifier une adresse de messagerie que ces utilisateurs utilisent déjà. Par exemple, son adresse Gmail.
    
    Cette option vous permet de restreindre l’accès et les droits à des utilisateurs spécifiques en spécifiant leur adresse de messagerie dans les paramètres de chiffrement. L'inconvénient est la surcharge administrative liée à la création du compte et à la coordination avec la configuration de l'étiquette.

- Utilisez [l’intégration de SharePoint et OneDrive à Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration) afin que les comptes invités soient automatiquement créés lorsque vos utilisateurs partagent des liens.
    
    Cette option offre un coût d’administration minimal, car les comptes sont créés automatiquement et une configuration d’étiquette plus simple. Dans ce scénario, vous devez sélectionner l’option de chiffrement [Ajouter des utilisateur authentifiés](encryption-sensitivity-labels.md#requirements-and-limitations-for-add-any-authenticated-users), car vous ne connaissez pas les adresses de messagerie à l’avance. Ce paramètre ne vous permet pas de restreindre l’accès et les droits d’utilisation à des utilisateurs spécifiques.

Les utilisateurs externes peuvent également utiliser un compte Microsoft pour ouvrir des documents chiffrés lorsqu’ils utilisent les applications Windows et Microsoft 365 ([anciennement des applications Office 365](/deployoffice/name-change)) ou la version autonome d’Office 2019. Plus récemment pris en charge pour les autres plateformes, les comptes Microsoft sont également pris en charge pour l’ouverture de documents chiffrés sur macOS (Microsoft 365 Apps, version 16.42+), Android (version 16.0.13029+) et iOS (version 2.42+). 

Par exemple, un utilisateur de votre organisation partage un document chiffré avec un utilisateur extérieur à votre organisation, et les paramètres de chiffrement spécifient une adresse de messagerie Gmail pour l’utilisateur externe. Cet utilisateur externe peut créer son propre compte Microsoft qui utilise son adresse de messagerie Gmail. Ensuite, une fois qu’ils se sont ouverts avec ce compte, ils peuvent ouvrir le document et le modifier, conformément aux restrictions d’utilisation qui leur sont spécifiées. Pour consulter un exemple pas à pas de ce scénario, consultez[Ouverture et modification du document protégé](/azure/information-protection/secure-collaboration-documents#opening-and-editing-the-protected-document).

> [!NOTE]
> L’adresse de messagerie du compte Microsoft doit correspondre à l’adresse de messagerie spécifiée pour restreindre l’accès aux paramètres de chiffrement.

Lorsqu’un utilisateur avec un compte Microsoft ouvre un document chiffré de cette façon, il crée automatiquement un compte invité pour le client si un compte invité du même nom n’existe pas encore. Lorsque le compte invité existe, il peut ensuite être utilisé pour ouvrir des documents dans SharePoint et OneDrive à l’aide d’Office sur le web, en plus d’ouvrir des documents chiffrés à partir des applications Office de bureau et mobiles pris en charge.

Toutefois, le compte invité automatique n’est pas créé immédiatement dans ce scénario, en raison d’une latence de réplication. Si vous spécifiez des adresses e-mail personnelles dans le cadre de vos paramètres de chiffrement, nous vous recommandons de créer des comptes invités correspondants dans Azure Active Directory. Indiquez ensuite à ces utilisateurs qu’ils doivent utiliser ce compte pour ouvrir un document chiffré de votre organisation.

> [!TIP]
> Étant donné que vous ne savez pas si les utilisateurs externes utiliseront une application cliente Office prise en charge, le partage de liens à partir de SharePoint et OneDrive après avoir créé des comptes invités (pour des utilisateurs spécifiques) ou lorsque vous utilisez [l’intégration de SharePoint et OneDrive à Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview) (pour tout utilisateur authentifié) est une méthode plus fiable pour prendre en charge la collaboration sécurisée avec les utilisateurs externes.

## <a name="next-steps"></a>Prochaines étapes

Pour connaître les configurations que vous devrez peut-être effectuer pour les services d’infrastructure réseau, consultez [Pare-feu et infrastructure réseau](/azure/information-protection/requirements#firewalls-and-network-infrastructure).

Si vous utilisez [des étiquettes de confidentialité](sensitivity-labels.md) pour chiffrer des documents et des e-mails, vous pouvez être intéressé par la [prise en charge des utilisateurs externes et du contenu étiqueté](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content) pour comprendre quels paramètres d’étiquette s’appliquent entre les locataires. Pour obtenir des instructions de configuration pour les paramètres de chiffrement d’étiquette, consultez [Restreindre l’accès au contenu à l’aide d’étiquettes de confidentialité pour appliquer le chiffrement](encryption-sensitivity-labels.md).

Vous souhaitez savoir comment et quand le service de chiffrement est accessible ? Consultez [la procédure pas à pas du fonctionnement d’Azure RMS : première utilisation, protection du contenu, consommation de contenu](/azure/information-protection/how-does-it-work#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption).




