---
title: Configurer Mobility + Security
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- highpri
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Configurez Mobilité et sécurité de base pour sécuriser et gérer les appareils mobiles de vos utilisateurs en effectuant des actions telles que la réinitialisation à distance d’un appareil.
ms.openlocfilehash: 0eb9d1a053239ecf3e135c08f34b100c09b4e973
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68719093"
---
# <a name="set-up-basic-mobility-and-security"></a>Configurer Mobility + Security

La fonctionnalité de mobilité et sécurité de base intégrée pour Microsoft 365 vous permet de sécuriser et de gérer les appareils mobiles des utilisateurs, tels que les iPhones, les iPads, les androids et les téléphones Windows. Vous pouvez créer et gérer des stratégies de sécurité des appareils, réinitialiser un appareil à distance et afficher des rapports détaillés sur les appareils.

Vous avez des questions ? Pour obtenir un FAQ pour répondre aux questions courantes, consultez Questions [fréquentes (FAQ) sur la mobilité et la sécurité de base](frequently-asked-questions.yml). N’oubliez pas que vous ne pouvez pas utiliser un compte d’administrateur délégué pour gérer mobilité et sécurité de base. Pour plus d’informations, consultez [Partenaires : Administration déléguée de l’offre](https://support.microsoft.com/office/partners-offer-delegated-administration-26530dc0-ebba-415b-86b1-b55bc06b073e). 

La gestion des appareils fait partie du Centre de conformité sécurité &. Vous devez donc y accéder pour lancer la configuration de la mobilité et de la sécurité de base.

## <a name="activate-the-basic-mobility-and-security-service"></a>Activer le service Mobilité et sécurité de base

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.

2. Accédez à [Activer la mobilité et la sécurité de base](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx).

   L’activation de la mobilité et de la sécurité de base peut prendre un certain temps. Une fois l’opération terminée, vous recevez un e-mail qui explique les étapes suivantes à suivre.

## <a name="set-up-mobile-device-management"></a>Configurer Mobile Gestion des appareils

Lorsque le service est prêt, effectuez les étapes suivantes pour terminer l’installation.

### <a name="step-1-required-configure-domains-for-basic-mobility-and-security"></a>Étape 1 : (Obligatoire) Configurer des domaines pour la mobilité et la sécurité de base

Si vous n’avez pas de domaine personnalisé associé à Microsoft 365 ou si vous ne gérez pas les appareils Windows, vous pouvez ignorer cette section. Sinon, vous devez ajouter des enregistrements DNS pour le domaine au niveau de votre hôte DNS. Si vous avez déjà ajouté les enregistrements, dans le cadre de la configuration de votre domaine avec Microsoft 365, vous êtes prêt. Après avoir ajouté les enregistrements, les utilisateurs Microsoft 365 de votre organisation qui se connectent sur leur appareil Windows avec une adresse e-mail qui utilise votre domaine personnalisé sont redirigés pour s’inscrire à Mobilité et sécurité de base.

Vous avez besoin d’aide pour configurer les enregistrements ? Recherchez votre bureau d’enregistrement de domaines et sélectionnez le nom du bureau d’enregistrement pour accéder à l’aide pas à pas pour créer un enregistrement DNS dans la liste fournie dans [Ajouter des enregistrements DNS pour connecter votre domaine](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider). Suivez ces instructions pour créer des enregistrements CNAME décrits dans [Simplifier l’inscription Windows sans Azure AD Premium](/mem/intune/enrollment/windows-enroll#simplify-windows-enrollment-without-azure-ad-premium).

Après avoir ajouté les deux enregistrements CNAME, revenez au Centre de conformité & de sécurité et accédez à **Protection contre la** >  perte de données **Gestion des** appareils pour effectuer l’étape suivante.

### <a name="step-2-required-configure-an-apns-certificate-for-ios-devices"></a>Étape 2 : (Obligatoire) Configurer un certificat APNs pour les appareils iOS

Pour gérer les appareils iOS tels que les iPad et les iPhone, vous devez créer un certificat APNs.

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.

2. Accédez à la [Centre d'administration Microsoft 365](https://portal.office.com/adminportal/home?#/MifoDevices), puis choisissez **Certificat APNs pour iOS**.

4. Dans la page Paramètres du certificat de notification Push Apple, choisissez **Suivant**.

5. Sélectionnez **Télécharger votre fichier CSR** et enregistrez la demande de signature de certificat dans un emplacement de votre ordinateur dont vous vous souviendrez. Sélectionnez **Suivant**.

6. Dans la page Créer un certificat APNs :

   - Select Apple APNS Portal to open the Apple Push Certificates Portal. 
   - Sign in with an Apple ID.

     > [!IMPORTANT]
     > Use a company Apple ID associated with an email account that will remain with your organization even if the user who manages the account leaves. Save this ID because you'll need to use the same ID when it's time to renew the certificate.

   - Select Create a Certificate and accept the Terms of Use.
   - Accédez à la demande de signature de certificat que vous avez téléchargée sur votre ordinateur à partir de Microsoft 365, puis sélectionnez Charger.
   - Download the APN certificate created by the Apple Push Certificate Portal to your computer.

     > [!TIP]
     > If you're having trouble downloading the certificate, refresh your browser.

7. Retour à Microsoft 365 et sélectionnez **Suivant**.

8.  Browse to the APN certificate you downloaded from the Apple Push Certificates Portal.

9. Sélectionnez **Terminer**.

### <a name="step-3-recommended-set-up-multi-factor-authentication"></a>Étape 3 : (recommandé) Configurer l’authentification multifacteur

L’authentification multifacteur permet de sécuriser la connexion à Microsoft 365 pour l’inscription des appareils mobiles en exigeant une deuxième forme d’authentification. Les utilisateurs doivent accuser réception d’un appel téléphonique, d’un SMS ou d’une notification d’application sur leur appareil mobile après avoir entré correctement le mot de passe de leur compte professionnel. Ils peuvent inscrire leur appareil uniquement une fois cette deuxième forme d’authentification terminée. Une fois que les appareils des utilisateurs sont inscrits dans Mobilité et sécurité de base, les utilisateurs peuvent accéder aux ressources Microsoft 365 uniquement avec leur compte professionnel.

Pour savoir comment activer l’authentification multifacteur dans le portail Azure AD, consultez [Configurer l’authentification multifacteur](../security-and-compliance/set-up-multi-factor-authentication.md).

Après avoir configuré l’authentification multifacteur, revenez au Centre de conformité & de sécurité et accédez à **Protection contre la** >  perte de données **Stratégies d’appareil de gestion des** >  appareils pour effectuer l’étape suivante.

### <a name="step-4-recommended-manage-device-security-policies"></a>Étape 4 : (recommandé) Gérer les stratégies de sécurité des appareils

L’étape suivante consiste à créer et déployer des stratégies de sécurité des appareils pour protéger vos données d’organisation Microsoft 365. Par exemple, vous pouvez empêcher la perte de données si un utilisateur perd son appareil en créant une stratégie pour verrouiller les appareils après cinq minutes d’inactivité et réinitialiser les appareils après trois échecs de connexion.

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.

2. Sélectionnez [Activer mobile Gestion des appareils](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). Si le service est activé, au lieu de cela, les étapes d’activation s’affichent un lien vers [Gérer les appareils](https://admin.microsoft.com/adminportal/home#/MifoDevices) .

3. Accédez à **Stratégies d’appareil**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Paramètres de stratégie sécurité et mobilité de base.":::

4. Créez et déployez des stratégies de sécurité d’appareil appropriées pour votre organisation en suivant les étapes décrites dans [Créer des stratégies de sécurité d’appareil dans Mobilité et sécurité de base](create-device-security-policies.md).

> [!TIP]
>
> - Lorsque vous créez une stratégie, vous pouvez définir la stratégie pour autoriser l’accès et signaler une violation de stratégie lorsqu’un appareil utilisateur n’est pas conforme à la stratégie. Cela vous permet de voir le nombre d’appareils mobiles affectés par la stratégie sans bloquer l’accès à Microsoft 365.
>
> - Avant de déployer une nouvelle stratégie pour tous les membres de votre organisation, nous vous recommandons de la tester sur les appareils utilisés par un petit nombre d’utilisateurs.
>
> - En outre, avant de déployer des stratégies, informez votre organisation des impacts potentiels de l’inscription d’un appareil dans Mobilité et sécurité de base. Selon la façon dont vous configurez les stratégies, les appareils qui ne sont pas conformes aux stratégies (appareils non conformes) peuvent être bloqués pour accéder à Microsoft 365. Les appareils non conformes peuvent également avoir installé des applications, des photos et d’autres informations personnelles qui, sur un appareil inscrit, peuvent être supprimés en cas de réinitialisation de l’appareil. Pour plus d’informations, consultez [Réinitialiser un appareil mobile dans Mobilité et sécurité de base](wipe-mobile-device.md).

## <a name="make-sure-users-enroll-their-devices"></a>Assurez-vous que les utilisateurs inscrivent leurs appareils

Une fois que vous avez créé et déployé une stratégie de gestion des appareils mobiles, chaque utilisateur Microsoft 365 sous licence de votre organisation auquel la stratégie d’appareil s’applique reçoit un message d’inscription la prochaine fois qu’il se connecte à Microsoft 365 à partir de son appareil mobile. Ils doivent effectuer les étapes d’inscription et d’activation avant de pouvoir accéder aux e-mails et aux documents Microsoft 365. Pour plus d’informations, consultez [Inscrire votre appareil mobile à l’aide de Mobilité et sécurité de base](enroll-your-mobile-device.md).

> [!IMPORTANT]
> Si la langue préférée d’un utilisateur n’est pas prise en charge par le processus d’inscription, les utilisateurs peuvent recevoir une notification d’inscription et des étapes sur leurs appareils mobiles dans une autre langue. Toutes les langues prises en charge dans Microsoft 365 ne sont actuellement pas prises en charge pour le processus d’inscription sur les appareils mobiles.

Les utilisateurs disposant d’appareils Android ou iOS doivent installer l’application Portail d'entreprise dans le cadre du processus d’inscription.

## <a name="related-content"></a>Contenu associé

[Fonctionnalités de mobilité et de sécurité de base](capabilities.md) (article)\
[Créer des stratégies de sécurité des appareils dans Mobilité et sécurité de base](create-device-security-policies.md) (article)
