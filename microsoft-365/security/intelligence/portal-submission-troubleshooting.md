---
title: Résoudre les erreurs du portail MSI provoquées par le blocage de l'administrateur.
description: Résoudre les erreurs du portail MSI
ms.reviewer: ''
keywords: sécurité, exemple d’aide de soumission, fichier de logiciels malveillants, fichier virus, fichier cheval de Troie, envoyer, envoyer à Microsoft, envoyer un exemple, virus, cheval de Troie, ver, non détecté, ne détecte pas, e-mail microsoft, programme malveillant e-mail, je pense que c’est un programme malveillant, je pense que c’est un virus, où puis-je envoyer un virus, est-ce un virus, MSE, ne détecte pas, aucune signature, aucune détection, fichier suspect,  MMPC, Centre de protection Microsoft contre les programmes malveillants, chercheurs, analystes, WDSI, renseignement de sécurité
ms.service: microsoft-365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.openlocfilehash: a26ce96ba8ffbea080baa941cff5258d186ed568
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67737265"
---
# <a name="troubleshooting-malware-submission-errors-caused-by-administrator-block"></a>Résolution des erreurs d’envoi de programmes malveillants provoquées par un bloc administrateur

Dans certains cas, un bloc d’administrateur peut entraîner des problèmes d’envoi lorsque vous essayez d’envoyer un fichier potentiellement infecté au [site web microsoft Security Intelligence](https://www.microsoft.com/wdsi) à des fins d’analyse. Le processus suivant montre comment résoudre ce problème.

## <a name="review-your-settings"></a>Vérifiez vos paramètres

Ouvrez les [paramètres de votre application Azure Enterprise](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/). Sous **Applications d’entreprise,** >  **les utilisateurs peuvent donner leur consentement aux applications qui accèdent aux données de l’entreprise en leur nom**. Vérifiez si Oui ou Non est sélectionné.

- Si **non** est sélectionné, un administrateur Azure AD pour le locataire client doit donner son consentement à l’organisation. Selon la configuration avec Azure AD, les utilisateurs peuvent être en mesure d’envoyer une demande directement à partir de la même boîte de dialogue. S’il n’existe aucune option pour demander le consentement de l’administrateur, les utilisateurs doivent demander que ces autorisations soient ajoutées à leur administrateur Azure AD. Pour plus d’informations, accédez à la section suivante.

- Si **Oui** est sélectionné, vérifiez que le paramètre d’application Security Intelligence Windows Defender **activé pour que les utilisateurs se connectent soit** défini sur **Oui** [dans Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d). Si **non** est sélectionné, vous devez demander à un administrateur Azure AD de l’activer.

## <a name="implement-required-enterprise-application-permissions"></a>Implémenter les autorisations d’application d’entreprise requises

Ce processus nécessite un administrateur général ou d’application dans le locataire.

1. Ouvrez [les paramètres de l’application d’entreprise](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d).
2. Sélectionnez **Accorder le consentement administrateur pour l’organisation**.
3. Si vous pouvez le faire, passez en revue les autorisations d’API requises pour cette application, comme le montre l’image suivante. Fournissez le consentement du locataire.

    ![accorder l’image de consentement.](../../media/security-intelligence-images/msi-grant-admin-consent.jpg)

4. Si l’administrateur reçoit une erreur lors de la tentative de consentement manuellement, essayez [l’option 1](#option-1-approve-enterprise-application-permissions-by-user-request) ou [l’option 2](#option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin) comme solutions de contournement possibles.

## <a name="option-1-approve-enterprise-application-permissions-by-user-request"></a>Option 1 Approuver les autorisations d’application d’entreprise par demande de l’utilisateur

> [!NOTE]
> Il s’agit actuellement d’une fonctionnalité en préversion.

Les administrateurs Azure Active Directory doivent autoriser les utilisateurs à demander le consentement de l’administrateur aux applications. Vérifiez que le paramètre est configuré sur **Oui** dans [les applications d’entreprise](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/).

![Paramètres utilisateur des applications d’entreprise.](../../media/security-intelligence-images/msi-enterprise-app-user-setting.jpg)

Pour plus d’informations, consultez [Configurer Administration workflow de consentement](/azure/active-directory/manage-apps/configure-admin-consent-workflow).

Une fois ce paramètre vérifié, les utilisateurs peuvent passer par la connexion du client d’entreprise à [Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) et envoyer une demande de consentement administrateur, y compris une justification.

![Flux de connexion Contoso.](../../media/security-intelligence-images/msi-contoso-approval-required.png)

Administration pourrez examiner et approuver les demandes de [consentement de l’administrateur Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AccessRequests/menuId/) des autorisations d’application.

Une fois le consentement fourni, tous les utilisateurs du locataire pourront utiliser l’application.

## <a name="option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin"></a>Option 2 Fournir le consentement de l’administrateur en authentifier l’application en tant qu’administrateur

Ce processus nécessite que les administrateurs généraux passent par le flux de connexion du client Entreprise auprès de [Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission).

![Flux de connexion de consentement.](../../media/security-intelligence-images/msi-microsoft-permission-required.jpg)

Ensuite, les administrateurs examinent les autorisations et veillent à sélectionner **Consentement pour le compte de votre organisation**, puis **sélectionnent Accepter**.

Tous les utilisateurs du locataire pourront désormais utiliser cette application.

## <a name="option-3-delete-and-readd-app-permissions"></a>Option 3 : Supprimer et lire les autorisations d’application

Si aucune de ces options ne résout le problème, essayez les étapes suivantes (en tant qu’administrateur) :

1. Supprimez les configurations précédentes de l’application. Accédez aux [applications d’entreprise](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/982e94b2-fea9-4d1f-9fca-318cda92f90b) et sélectionnez **Supprimer**.

   ![Supprimez les autorisations d’application.](../../media/security-intelligence-images/msi-properties.png)

2. Capturez TenantID à partir des [propriétés](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).

3. Remplacez {tenant-id} par le locataire spécifique qui doit accorder le consentement à cette application dans l’URL ci-dessous. Copiez cette URL dans le navigateur. Le reste des paramètres est déjà terminé.
``https://login.microsoftonline.com/{tenant-id}/v2.0/adminconsent?client_id=f0cf43e5-8a9b-451c-b2d5-7285c785684d&state=12345&redirect_uri=https%3a%2f%2fwww.microsoft.com%2fwdsi%2ffilesubmission&scope=openid+profile+email+offline_access``

   ![Autorisations nécessaires.](../../media/security-intelligence-images/msi-microsoft-permission-requested-your-organization.png)

4. Passez en revue les autorisations requises par l’application, puis sélectionnez **Accepter**.

5. Vérifiez que les autorisations sont appliquées dans le [Azure-Portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/ce60a464-5fca-4819-8423-bcb46796b051).

   ![Vérifiez que les autorisations sont appliquées.](../../media/security-intelligence-images/msi-permissions.jpg)

6. Connectez-vous à [Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) en tant qu’utilisateur d’entreprise disposant d’un compte non administrateur pour voir si vous avez accès.

 Si l’avertissement n’est pas résolu après avoir suivi ces étapes de dépannage, appelez le support Microsoft.