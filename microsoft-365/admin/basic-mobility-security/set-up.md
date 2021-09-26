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
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Configurer la mobilité et la sécurité de base pour sécuriser et gérer les appareils mobiles de vos utilisateurs en faisant des actions telles que la wiping à distance d’un appareil.
ms.openlocfilehash: 07f8283353432b06aea67ba9cf8bbc505d6c3012
ms.sourcegitcommit: aebcdbef52e42f37492a7f780b8b9b2bc0998d5c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2021
ms.locfileid: "59775131"
---
# <a name="set-up-basic-mobility-and-security"></a>Configurer Mobility + Security

La mobilité et la sécurité de base intégrées pour Microsoft 365 vous aident à sécuriser et gérer les appareils mobiles des utilisateurs tels que les iPhone, iPad, Android et Windows mobiles. Vous pouvez créer et gérer des stratégies de sécurité des appareils, réinitialiser un appareil à distance et afficher des rapports détaillés sur les appareils.

Vous avez des questions ? Pour obtenir un FORUM AUX QUESTIONS pour vous aider à répondre à des questions courantes, consultez forum aux questions fréquemment posées sur la mobilité [et la sécurité .](frequently-asked-questions.yml) Sachez que vous ne pouvez pas utiliser un compte d’administrateur délégué pour gérer la mobilité et la sécurité de base. Pour plus d’informations, [voir Partenaires : Proposer une administration déléguée.](https://support.microsoft.com/office/partners-offer-delegated-administration-26530dc0-ebba-415b-86b1-b55bc06b073e) 

La gestion des appareils fait partie du Centre de sécurité & conformité. Vous devez donc y aller pour lancer la configuration de la mobilité et de la sécurité de base.

## <a name="activate-the-basic-mobility-and-security-service"></a>Activer le service De mobilité et sécurité de base

1. Connectez-vous Microsoft 365 avec votre compte d’administrateur global.

2. Go to [Activate Basic Mobility and Security](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx).

   L’activation de la mobilité et de la sécurité de base peut prendre un certain temps. Une fois terminé, vous recevrez un courrier électronique qui vous explique les étapes à suivre.

## <a name="set-up-mobile-device-management"></a>Configurer la gestion des appareils mobiles

Lorsque le service est prêt, remplissez les étapes suivantes pour terminer l’installation.

### <a name="step-1-required-configure-domains-for-basic-mobility-and-security"></a>Étape 1 : (Obligatoire) Configurer des domaines pour la mobilité et la sécurité de base

Si vous n’avez pas de domaine personnalisé associé à Microsoft 365 ou si vous ne gérez pas Windows appareils, vous pouvez ignorer cette section. Dans le cas contraire, vous devrez ajouter des enregistrements DNS pour le domaine sur votre hôte DNS. Si vous avez déjà ajouté les enregistrements, dans le cadre de la configuration de votre domaine avec Microsoft 365, vous êtes tous définies. Après avoir ajouté les enregistrements, Microsoft 365 utilisateurs de votre organisation qui se connectent sur leur appareil Windows avec une adresse de messagerie qui utilise votre domaine personnalisé sont redirigés vers l’inscription à Basic Mobility and Security.

Vous avez besoin d’aide pour la configuration des enregistrements ? Recherchez votre bureau d’enregistrement de domaines et sélectionnez le nom du bureau d’enregistrement pour passer à l’aide pas à pas pour créer un enregistrement DNS dans la liste fournie dans Ajouter des enregistrements [DNS](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider)pour connecter votre domaine. Utilisez ces instructions pour créer des enregistrements CNAME décrits dans [Simplifier Windows inscription sans Azure AD Premium](/mem/intune/enrollment/windows-enroll#simplify-windows-enrollment-without-azure-ad-premium).

Après avoir ajouté les deux enregistrements CNAME, revenir au Centre de sécurité & conformité et accéder à la gestion des appareils de protection contre la perte de données pour passer à  >     l’étape suivante.

### <a name="step-2-required-configure-an-apns-certificate-for-ios-devices"></a>Étape 2 : (Obligatoire) Configurer un certificat APNs pour les appareils iOS

Pour gérer les appareils iOS tels que iPad et les iPhones, vous devez créer un certificat APNs.

1. Connectez-vous Microsoft 365 avec votre compte d’administrateur global.

2. Dans votre type de navigateur :  [https://protection.office.com](https://protection.office.com/) .

3. Sélectionnez  **Gestion des appareils de protection contre** la perte de   >  **** données, puis sélectionnez **Certificat APNs pour les appareils iOS.**

4. Dans la page Certificat de notification Push Apple Paramètres, choisissez **Suivant**.

5. Sélectionnez **Télécharger votre fichier CSR et** enregistrez la demande de signature de certificat dans un endroit de votre ordinateur que vous   mémoriserez. Sélectionnez **Suivant**.

6. Dans la page Créer un certificat APNs :

   - Sélectionnez Le portail Apple APNS pour ouvrir le portail de certificats Push Apple.
   - Sign in with an Apple ID.

     > [!IMPORTANT]
     > Use a company Apple ID associated with an email account that will remain with your organization even if the user who manages the account leaves. Save this ID because you'll need to use the same ID when it's time to renew the certificate.

   - Sélectionnez Créer un certificat et acceptez les conditions d’utilisation.
   - Accédez à la demande de signature de certificat que vous avez téléchargée sur votre ordinateur à partir Microsoft 365 et selectUpload.
   - Download the APN certificate created by the Apple Push Certificate Portal to your computer.

     > [!TIP]
     > If you're having trouble downloading the certificate, refresh your browser.

7. Revenir à Microsoft 365 puis sélectionnez **Suivant.**

8.  Browse to the APN certificate you downloaded from the Apple Push Certificates Portal.

9. Sélectionnez  **Terminer.**

### <a name="step-3-recommended-set-up-multi-factor-authentication"></a>Étape 3 : (Recommandé) Configurer l’authentification multifacteur

L’authentification multifacteur permet de sécuriser la Microsoft 365 pour l’inscription des appareils mobiles en exigeant un second formulaire d’authentification. Les utilisateurs doivent reconnaître un appel téléphonique, un SMS ou une notification d’application sur leur appareil mobile après avoir correctement entré le mot de passe de leur compte de travail. Ils ne peuvent inscrire leur appareil qu’une fois cette deuxième forme d’authentification terminée. Une fois que les appareils des utilisateurs sont inscrits à Basic Mobility and Security, les utilisateurs peuvent accéder aux ressources Microsoft 365 uniquement avec leur compte de travail.

Pour savoir comment activer l’authentification multifacteur dans le portail Azure AD, voir [Configurer l’authentification multifacteur.](../security-and-compliance/set-up-multi-factor-authentication.md)

Après avoir installé l’ation MFA, revenir au **** Centre de sécurité & conformité et accédez aux stratégies de périphérique de gestion des appareils de protection contre la perte de données pour passer à   >     >  ****   l’étape suivante.

### <a name="step-4-recommended-manage-device-security-policies"></a>Étape 4 : (Recommandé) Gérer les stratégies de sécurité des appareils

L’étape suivante consiste à créer et déployer des stratégies de sécurité d’appareil pour protéger Microsoft 365 données de votre organisation. Par exemple, vous pouvez éviter la perte de données si un utilisateur perd son appareil en créant une stratégie pour verrouiller les appareils après cinq minutes d’inactivité et effacer les appareils après trois échecs de connect.

1. Connectez-vous Microsoft 365 avec votre compte d’administrateur global.

2. Sélectionnez [Activer la gestion des appareils mobiles.](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx) Si le service est activé, à la place, les étapes d’activation vous verrez un lien vers [Gérer les appareils.](https://admin.microsoft.com/adminportal/home#/MifoDevices)  

3. Go to **Device policies**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Paramètres de stratégie de sécurité et de mobilité de base.":::

4. Créez et déployez des stratégies de sécurité d’appareil adaptées à votre organisation en suivant les étapes de création de stratégies de sécurité des appareils [dans Basic Mobility and Security](create-device-security-policies.md).

> [!TIP]
>
> - Lorsque vous créez une stratégie, vous pouvez la définir pour autoriser l’accès et signaler une violation de stratégie lorsqu’un appareil utilisateur n’est pas conforme à la stratégie. Cela vous permet de voir le nombre d’appareils mobiles touchés par la stratégie sans bloquer l’accès Microsoft 365.
>
> - Avant de déployer une nouvelle stratégie pour tous les membres de votre organisation, nous vous recommandons de la tester sur les appareils utilisés par un petit nombre d’utilisateurs.
>
> - En outre, avant de déployer des stratégies, faites savoir à votre organisation les impacts potentiels de l’inscription d’un appareil dans Basic Mobility and Security. Selon la façon dont vous avez installé les stratégies, l’accès aux appareils qui ne sont pas conformes aux stratégies (appareils non conformes) peut être bloqué et Microsoft 365. Les appareils non conformes peuvent également avoir des applications installées, des photos et d’autres informations personnelles qui, sur un appareil inscrit, peuvent être supprimées si l’appareil est nettoyé. Pour plus d’informations, voir [Effacer un appareil mobile dans Basic Mobility and Security](wipe-mobile-device.md).

## <a name="make-sure-users-enroll-their-devices"></a>Assurez-vous que les utilisateurs inscrivent leurs appareils

Une fois que vous avez créé et déployé une stratégie de gestion des appareils mobiles, chaque utilisateur Microsoft 365 sous licence de votre organisation que la stratégie d’appareil applique reçoit un message d’inscription la prochaine fois qu’il se connecte à Microsoft 365 à partir de son appareil mobile. Ils doivent effectuer les étapes d’inscription et d’activation avant de pouvoir accéder Microsoft 365 courrier électronique et aux documents. Pour plus d’informations, voir [Inscrire votre appareil mobile à l’aide de Basic Mobility and Security](enroll-your-mobile-device.md).

> [!IMPORTANT]
> Si la langue préférée d’un utilisateur n’est pas prise en charge par le processus d’inscription, les utilisateurs peuvent recevoir des notifications d’inscription et des étapes sur leurs appareils mobiles dans une autre langue. Toutes les langues ne sont pas Microsoft 365 sont actuellement pris en charge pour le processus d’inscription sur les appareils mobiles.

Les utilisateurs avec des appareils Android ou iOS doivent installer l’application Portail d'entreprise dans le cadre du processus d’inscription.

## <a name="related-content"></a>Contenu connexe

[Fonctionnalités de la mobilité et de la sécurité de](capabilities.md) base (article)\
[Créer des stratégies de sécurité des appareils dans Basic Mobility and Security](create-device-security-policies.md) (article)