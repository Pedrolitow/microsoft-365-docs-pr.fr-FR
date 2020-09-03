---
title: Configurer Mobility + Security
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
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: Configurez la mobilité et la sécurité de base pour sécuriser et gérer les appareils mobiles de vos utilisateurs.
ms.openlocfilehash: 0d62c209d4eb9d0da9096ccd5ca2d4a387becf95
ms.sourcegitcommit: 2179abfe0b7a8bea917eb1c1057ed3795bdf91e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "47336858"
---
# <a name="set-up-basic-mobility-and-security"></a>Configurer Mobility + Security

La mobilité et la sécurité de base intégrées pour Microsoft 365 vous aident à sécuriser et à gérer les appareils mobiles des utilisateurs tels que les iPhone, les iPad, les Androids et les téléphones Windows. Vous pouvez créer et gérer des stratégies de sécurité des appareils, réinitialiser un appareil à distance et afficher des rapports détaillés sur les appareils.

Vous avez des questions ? Pour consulter un FAQ afin de répondre aux questions courantes, voir [Basic Mobility and Security Frequently-Asked Forum aux questions (FAQ)](basic-mobility-and-security-frequently-asked-questions.md). N’oubliez pas que vous ne pouvez pas utiliser un compte d’administrateur délégué pour gérer la sécurité et la mobilité de base. Pour plus d’informations, consultez la rubrique [partenaires : proposer une administration déléguée](https://support.microsoft.com/office/partners-offer-delegated-administration-26530dc0-ebba-415b-86b1-b55bc06b073e). 

La gestion des périphériques fait partie du centre de sécurité & conformité afin que vous deviez y accéder pour lancer le programme d’installation MDM.

## <a name="activate-the-basic-mobility-and-security-service"></a>Activer le service de sécurité et de mobilité de base

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.
    

2. Rendez-vous sur activation de la [mobilité et de la sécurité de base](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx).
    
    L’activation de la mobilité et de la sécurité de base peut prendre un certain temps. Une fois l’opération terminée, vous recevez un courrier électronique qui explique les prochaines étapes à suivre.

## <a name="set-up-mobile-device-management"></a>Configurer la gestion des appareils mobiles

Lorsque le service est prêt, effectuez les étapes suivantes pour terminer l’installation.

### <a name="step-1-required-configure-domains-for-mdm"></a>Étape 1 : (obligatoire) configurer des domaines pour MDM

Si vous n’avez pas de domaine personnalisé associé à Microsoft 365 ou si vous ne gérez pas les appareils Windows, vous pouvez ignorer cette section. Dans le cas contraire, vous devrez ajouter des enregistrements DNS pour le domaine au niveau de votre hôte DNS. Si vous avez déjà ajouté les enregistrements, dans le cadre de la configuration de votre domaine avec Microsoft 365, toutes les données sont définies. Une fois que vous avez ajouté les enregistrements, les utilisateurs de Microsoft 365 de votre organisation qui se connectent sur leur appareil Windows avec une adresse de messagerie qui utilise votre domaine personnalisé sont redirigés pour s’inscrire à la sécurité et la mobilité de base.

Vous avez besoin d’aide pour configurer les enregistrements ? Recherchez votre bureau d’enregistrement de domaines et sélectionnez le nom du serveur d’inscriptions pour accéder à l’aide étape par étape pour la création d’un enregistrement DNS dans la liste fournie dans [Ajouter des enregistrements DNS pour connecter votre domaine](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider). Suivez ces instructions pour créer des enregistrements CNAMe décrits dans simplifier l’enregistrement [Windows sans Azure ad Premium](https://docs.microsoft.com/mem/intune/enrollment/windows-enroll#simplify-windows-enrollment-without-azure-ad-premium).

Une fois que vous avez ajouté les deux enregistrements CNAME, revenez dans le centre de sécurité & conformité et accédez à la gestion des périphériques de **protection contre**  >  **Device management**   la perte de données pour effectuer l’étape suivante.

### <a name="step-2-required-configure-an-apns-certificate-for-ios-devices"></a>Étape 2 : (obligatoire) configurer un certificat APNs pour les appareils iOS

Pour gérer les appareils iOS comme iPad et iPhone, vous devez créer un certificat APNs.

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.   

2. Dans votre navigateur, tapez :  [https://protection.office.com](https://protection.office.com/) .  

3. Sélectionnez gestion des périphériques de **protection contre la perte de données**   >  **Device management**, puis choisissez le **certificat APNs pour les appareils iOS**.   

4. Sur la page Paramètres du certificat de notification de type Apple, choisissez **suivant**.  

5. Sélectionnez **Télécharger votre fichier CSR**   et enregistrez la demande de signature de certificat sur un emplacement de votre ordinateur dont vous vous souviendrez. Sélectionnez **suivant**.
    
6. Sur la page créer un certificat APNs :
    
    - Sélectionnez Apple APNS Portal pour ouvrir le portail Appled Certificates.
    - Sign in with an Apple ID.

    >[!IMPORTANT]
    >Use a company Apple ID associated with an email account that will remain with your organization even if the user who manages the account leaves. Save this ID because you'll need to use the same ID when it's time to renew the certificate.

    - Sélectionnez créer un certificat et accepter les conditions d’utilisation.
    
    - BrowseTo la demande de signature de certificat que vous avez téléchargée sur votre ordinateur à partir de Microsoft 365 et selectUpload.
    
    - Certificat APN Downloadthe créé par le portail de certificats poussés Apple sur votre ordinateur.

    >[!TIP]
    >If you're having trouble downloading the certificate, refresh your browser.

7. Revenez à Microsoft 365 et cliquez sur **suivant**.   

8.  Browse to the APN certificate you downloaded from the Apple Push Certificates Portal.   

9. Sélectionnez  **Terminer**.  

### <a name="step-3-recommended-set-up-multi-factor-authentication"></a>Étape 3 : (recommandé) configuration de l’authentification multifacteur

MFA contribue à sécuriser la connexion à Microsoft 365 pour l’inscription des appareils mobiles en exigeant une deuxième forme d’authentification. Les utilisateurs doivent accuser réception d’un appel téléphonique, d’un message texte ou d’une notification d’application sur leur appareil mobile après avoir entré correctement leur mot de passe de compte professionnel. Ils peuvent inscrire leur appareil uniquement après la fin de cette deuxième forme d’authentification. Une fois que les appareils utilisateur sont intégrés dans la mobilité et la sécurité de base, les utilisateurs peuvent accéder aux ressources de Microsoft 365 avec uniquement leur compte professionnel.

Pour savoir comment activer l’authentification multifacteur dans le portail Azure AD, reportez-vous à la rubrique [set up Multi-Factor Authentication](https://go.microsoft.com/fwlink/p/?LinkId=519255).

Après avoir configuré l’authentification multifacteur, revenez dans le centre de sécurité & conformité et accédez à stratégies de périphérique de **protection contre**   >  **Device management**   >  **Device policies**   la perte de données pour effectuer l’étape suivante.

### <a name="step-4-recommended-manage-device-security-policies"></a>Étape 4 : (recommandé) gérer les stratégies de sécurité des appareils

L’étape suivante consiste à créer et déployer des stratégies de sécurité de périphérique afin de protéger vos données d’organisation 365 Microsoft. Par exemple, vous pouvez éviter la perte de données si un utilisateur perd son appareil en créant une stratégie pour verrouiller les appareils après cinq minutes d’inactivité et de réinitialisation des périphériques après trois échecs de connexion.

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général. 

2. Sélectionnez [activer la gestion des appareils mobiles](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). Si le service est activé, les étapes d’activation vous verrez un lien permettant de [gérer les appareils](https://admin.microsoft.com/adminportal/home#/MifoDevices)   .
    
3. Accédez à **stratégies d’appareil**.

     :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Paramètres de stratégie de mobilité et de sécurité de base":::

4. Créez et déployez des stratégies de sécurité de périphérique appropriées pour votre organisation en suivant les étapes décrites dans [Create Device Security Policies in Basic Mobility and Security](create-device-security-policies-in-basic-mmobility-and-security.md).

>[!TIP]
    - Lorsque vous créez une stratégie, vous pouvez définir la stratégie pour autoriser l’accès et la violation de la stratégie de rapport lorsqu’un périphérique utilisateur n’est pas conforme à la stratégie. Cela vous permet de voir le nombre d’appareils mobiles concernés par la stratégie sans bloquer l’accès à Microsoft 365.<br/>-Avant de déployer une nouvelle stratégie pour tous les membres de votre organisation, nous vous recommandons de la tester sur les appareils utilisés par un petit nombre d’utilisateurs.<br/>-En outre, avant de déployer des stratégies, votre organisation connaît les impacts potentiels de l’inscriptions d’un appareil dans la mobilité et la sécurité de base. En fonction de la façon dont vous configurez les stratégies, les appareils qui ne sont pas conformes aux stratégies (appareils non conformes) peuvent être bloqués pour accéder à Microsoft 365. Les appareils non conformes peuvent également avoir des applications installées, des photos et d’autres informations personnelles qui, sur un appareil d’enregistrement, peuvent être supprimées si l’appareil est effacé. Pour plus d’informations, reportez-vous à [la rubrique essuyage d’un appareil mobile dans Basic Mobility and Security](wipe-mobile-device.md).
    
## <a name="make-sure-users-enroll-their-devices"></a>Vérifier que les utilisateurs inscrivent leurs appareils

Une fois que vous avez créé et déployé une stratégie de gestion des appareils mobiles, chaque utilisateur Microsoft 365 sous licence de votre organisation auquel la stratégie d’appareil s’applique reçoit un message d’inscription lors de sa prochaine connexion à Microsoft 365 à partir de son appareil mobile. Ils doivent effectuer les étapes d’enregistrement et d’activation avant de pouvoir accéder aux courriers et documents Microsoft 365. Pour plus d’informations, consultez [la rubrique inscrire votre appareil mobile à l’aide de la sécurité et de la sécurité de base](enroll-your-mobile-device-using-basic-mobility-and-security.md).

>[!IMPORTANT]
>Si la langue par défaut d’un utilisateur n’est pas prise en charge par le processus d’enregistrement, les utilisateurs peuvent recevoir une notification d’enregistrement et des étapes sur leurs appareils mobiles dans une autre langue. Toutes les langues prises en charge dans Microsoft 365 ne sont actuellement pas prises en charge pour le processus d’enregistrement sur les appareils mobiles.

Les utilisateurs disposant d’appareils Android ou iOS doivent installer l’application portail d’entreprise dans le cadre du processus d’enregistrement.

## <a name="related-topics"></a>Voir aussi

[Fonctionnalités de la mobilité et de la sécurité de base](capabilities-of-basic-mobility-and-secruity.md)<br/>
[Créer des stratégies de sécurité des appareils dans la sécurité et la mobilité de base](create-device-security-policies-in-basic-mmobility-and-security.md)