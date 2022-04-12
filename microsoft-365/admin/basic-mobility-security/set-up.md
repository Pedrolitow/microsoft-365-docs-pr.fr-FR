---
title: Configurer Mobility + Security
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Configurez mobilité et sécurité de base pour sécuriser et gérer les appareils mobiles de vos utilisateurs en effectuant des actions telles que la réinitialisation à distance d’un appareil.
ms.openlocfilehash: b26906c0f374f5dc103fe26e4619663195da6ebd
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780828"
---
# <a name="set-up-basic-mobility-and-security"></a>Configurer Mobility + Security

La mobilité et la sécurité de base intégrées pour Microsoft 365 vous permet de sécuriser et de gérer les appareils mobiles des utilisateurs tels que les iPhone, les iPad, les Android et les téléphones Windows. Vous pouvez créer et gérer des stratégies de sécurité des appareils, réinitialiser un appareil à distance et afficher des rapports détaillés sur les appareils.

Vous avez des questions ? Pour obtenir une FAQ pour vous aider à répondre aux questions courantes, consultez Les [questions fréquentes (FAQ) sur la mobilité et la sécurité de base](frequently-asked-questions.yml). N’oubliez pas que vous ne pouvez pas utiliser un compte d’administrateur délégué pour gérer la mobilité et la sécurité de base. Pour plus d’informations, consultez [Partenaires : Offre d’administration déléguée](https://support.microsoft.com/office/partners-offer-delegated-administration-26530dc0-ebba-415b-86b1-b55bc06b073e). 

La gestion des appareils fait partie du Centre de sécurité & conformité. Vous devez donc vous y rendre pour lancer la configuration de base de la mobilité et de la sécurité.

## <a name="activate-the-basic-mobility-and-security-service"></a>Activer le service Mobilité et sécurité de base

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.

2. Accédez à [Activer la mobilité et la sécurité de base](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx).

   L’activation de la mobilité et de la sécurité de base peut prendre un certain temps. Une fois l’opération terminée, vous recevrez un e-mail expliquant les étapes à suivre.

## <a name="set-up-mobile-device-management"></a>Configurer mobile Gestion des appareils

Lorsque le service est prêt, effectuez les étapes suivantes pour terminer l’installation.

### <a name="step-1-required-configure-domains-for-basic-mobility-and-security"></a>Étape 1 : (Obligatoire) Configurer des domaines pour la mobilité et la sécurité de base

Si vous n’avez pas de domaine personnalisé associé à Microsoft 365 ou si vous ne gérez pas Windows appareils, vous pouvez ignorer cette section. Sinon, vous devez ajouter des enregistrements DNS pour le domaine sur votre hôte DNS. Si vous avez déjà ajouté les enregistrements, dans le cadre de la configuration de votre domaine avec Microsoft 365, vous êtes tous définis. Après avoir ajouté les enregistrements, Microsoft 365 utilisateurs de votre organisation qui se connectent à leur appareil Windows avec une adresse e-mail qui utilise votre domaine personnalisé sont redirigés pour s’inscrire à Mobilité et sécurité de base.

Vous avez besoin d’aide pour configurer les enregistrements ? Recherchez votre bureau d’enregistrement de domaines et sélectionnez le nom du bureau d’enregistrement pour accéder à l’aide pas à pas pour créer un enregistrement DNS dans la liste fournie dans [Ajouter des enregistrements DNS pour connecter votre domaine](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider). Utilisez ces instructions pour créer des enregistrements CNAME décrits dans [Simplifier l’inscription Windows sans Azure AD Premium](/mem/intune/enrollment/windows-enroll#simplify-windows-enrollment-without-azure-ad-premium).

Après avoir ajouté les deux enregistrements CNAME, revenez au Centre de sécurité & conformité et accédez à la gestion **de Data Loss** **PreventionDevice** >  pour effectuer l’étape suivante.

### <a name="step-2-required-configure-an-apns-certificate-for-ios-devices"></a>Étape 2 : (Obligatoire) Configurer un certificat APNs pour les appareils iOS

Pour gérer des appareils iOS comme iPad et iPhone, vous devez créer un certificat APNs.

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.

2. Dans votre type de navigateur : [https://protection.office.com](https://protection.office.com/).

3. Sélectionnez **Gestion de la protection contre la** >  perte de **données,** puis choisissez **Certificat APNs pour les appareils iOS**.

4. Dans la page Paramètres certificat de notification Push Apple, choisissez **Suivant**.

5. Sélectionnez **Télécharger votre fichier CSR** et enregistrez la demande de signature de certificat quelque part sur votre ordinateur dont vous vous souviendrez. Sélectionnez **Suivant**.

6. Dans la page Créer un certificat APNs :

   - Select Apple APNS Portal to open the Apple Push Certificates Portal. 
   - Sign in with an Apple ID.

     > [!IMPORTANT]
     > Use a company Apple ID associated with an email account that will remain with your organization even if the user who manages the account leaves. Save this ID because you'll need to use the same ID when it's time to renew the certificate.

   - Select Create a Certificate and accept the Terms of Use.
   - Accédez à la demande de signature de certificat que vous avez téléchargée sur votre ordinateur à partir de Microsoft 365 et selectUpload.
   - Download the APN certificate created by the Apple Push Certificate Portal to your computer.

     > [!TIP]
     > If you're having trouble downloading the certificate, refresh your browser.

7. Retour à Microsoft 365 et sélectionnez **Suivant**.

8.  Browse to the APN certificate you downloaded from the Apple Push Certificates Portal.

9. Sélectionnez **Terminer**.

### <a name="step-3-recommended-set-up-multi-factor-authentication"></a>Étape 3 : (recommandé) Configurer l’authentification multifacteur

L’authentification multifacteur permet de sécuriser la connexion à Microsoft 365 pour l’inscription des appareils mobiles en exigeant une deuxième forme d’authentification. Les utilisateurs doivent reconnaître un appel téléphonique, un SMS ou une notification d’application sur leur appareil mobile après avoir entré correctement leur mot de passe de compte professionnel. Ils ne peuvent inscrire leur appareil qu’une fois cette deuxième forme d’authentification terminée. Une fois les appareils utilisateur inscrits dans Mobilité et sécurité de base, les utilisateurs peuvent accéder aux ressources Microsoft 365 uniquement avec leur compte professionnel.

Pour savoir comment activer l’authentification multifacteur dans le portail Azure AD, consultez [Configurer l’authentification multifacteur](../security-and-compliance/set-up-multi-factor-authentication.md).

Une fois que vous avez configuré l’authentification multifacteur, revenez au Centre de sécurité & conformité et accédez aux stratégies **data loss** **preventionDevice** >  **managementDevice** >  pour effectuer l’étape suivante.

### <a name="step-4-recommended-manage-device-security-policies"></a>Étape 4 : (recommandé) Gérer les stratégies de sécurité des appareils

L’étape suivante consiste à créer et déployer des stratégies de sécurité des appareils pour protéger vos données d’organisation Microsoft 365. Par exemple, vous pouvez empêcher la perte de données si un utilisateur perd son appareil en créant une stratégie pour verrouiller les appareils après cinq minutes d’inactivité et réinitialiser les appareils après trois échecs de connexion.

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.

2. Sélectionnez [Activer le Gestion des appareils mobile](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). Si le service est activé, les étapes d’activation s’affichent, vous verrez un lien vers [Gérer les appareils](https://admin.microsoft.com/adminportal/home#/MifoDevices) .

3. Accédez aux **stratégies d’appareil**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Paramètres de stratégie de sécurité et de mobilité de base.":::

4. Créez et déployez des stratégies de sécurité d’appareil appropriées pour votre organisation en suivant les étapes [décrites dans Créer des stratégies de sécurité des appareils dans Mobilité et sécurité de base](create-device-security-policies.md).

> [!TIP]
>
> - Lorsque vous créez une stratégie, vous pouvez définir la stratégie pour autoriser l’accès et signaler une violation de stratégie lorsqu’un appareil utilisateur n’est pas conforme à la stratégie. Cela vous permet de voir combien d’appareils mobiles sont affectés par la stratégie sans bloquer l’accès à Microsoft 365.
>
> - Avant de déployer une nouvelle stratégie pour tous les membres de votre organisation, nous vous recommandons de la tester sur les appareils utilisés par un petit nombre d’utilisateurs.
>
> - En outre, avant de déployer des stratégies, informez votre organisation des impacts potentiels de l’inscription d’un appareil dans Mobilité et sécurité de base. Selon la façon dont vous configurez les stratégies, les appareils qui ne sont pas conformes aux stratégies (appareils non conformes) peuvent être bloqués pour accéder à Microsoft 365. Les appareils non conformes peuvent également avoir des applications installées, des photos et d’autres informations personnelles qui, sur un appareil inscrit, peuvent être supprimées si l’appareil est réinitialisé. Pour plus d’informations, consultez [Réinitialiser un appareil mobile dans Mobilité et sécurité de base](wipe-mobile-device.md).

## <a name="make-sure-users-enroll-their-devices"></a>Assurez-vous que les utilisateurs inscrivent leurs appareils

Une fois que vous avez créé et déployé une stratégie de gestion des appareils mobiles, chaque utilisateur sous licence Microsoft 365 de votre organisation que la stratégie d’appareil applique reçoit un message d’inscription la prochaine fois qu’il se connecte à Microsoft 365 à partir de son appareil mobile. Ils doivent effectuer les étapes d’inscription et d’activation avant de pouvoir accéder à Microsoft 365 e-mail et documents. Pour plus d’informations, consultez [Inscrire votre appareil mobile à l’aide de mobilité et de sécurité de base](enroll-your-mobile-device.md).

> [!IMPORTANT]
> Si la langue préférée d’un utilisateur n’est pas prise en charge par le processus d’inscription, les utilisateurs peuvent recevoir une notification d’inscription et des étapes sur leurs appareils mobiles dans une autre langue. Toutes les langues prises en charge dans Microsoft 365 ne sont pas prises en charge pour le processus d’inscription sur les appareils mobiles.

Les utilisateurs disposant d’appareils Android ou iOS doivent installer l’application Portail d'entreprise dans le cadre du processus d’inscription.

## <a name="related-content"></a>Contenu associé

[Fonctionnalités de mobilité et de sécurité de base](capabilities.md) (article)\
[Créer des stratégies de sécurité des appareils dans Mobilité et sécurité de base](create-device-security-policies.md) (article)
