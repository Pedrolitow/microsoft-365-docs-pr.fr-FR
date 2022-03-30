---
title: Résoudre les erreurs du portail MSI provoquées par le blocage de l’administrateur
description: Résoudre les erreurs du portail MSI
ms.reviewer: ''
keywords: sécurité, exemple d’aide sur la soumission, fichier de programmes malveillants, fichier antivirus, fichier de chevaux, envoyer, envoyer à Microsoft, soumettre un échantillon, virus, chevau de chevaux, ver, non détecté, ne détecte pas, e-mail microsoft, programme malveillant de messagerie, je pense qu’il s’agit d’un programme malveillant, je pense qu’il s’agit d’un virus, où puis-je envoyer un virus, est-ce un virus, MSE, ne détecte pas, aucune signature, aucune détection, fichier suspect,  MMPC, Centre de protection Microsoft contre les programmes malveillants, chercheurs, analyste, WDSI, intelligence de la sécurité
ms.prod: m365-security
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
ms.technology: m365d
ms.openlocfilehash: e70eb5192a1fd6171b8e515509ad336aa99a2c63
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680276"
---
# <a name="troubleshooting-malware-submission-errors-caused-by-administrator-block"></a>Résolution des erreurs de soumission de programmes malveillants provoquées par le blocage de l’administrateur
Dans certains cas, un blocage d’administrateur peut entraîner des problèmes de soumission lorsque vous essayez de soumettre un fichier potentiellement infecté au site web [d’aide](https://www.microsoft.com/wdsi) à la sécurité Microsoft pour analyse. Le processus suivant montre comment résoudre ce problème.

## <a name="review-your-settings"></a>Vérifiez vos paramètres
Ouvrez vos [paramètres d Enterprise’application Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/). Sous **Enterprise** **ApplicationsUsers** >   peut consentir aux applications accédant aux données de l’entreprise en leur nom, vérifiez si Oui ou Non est sélectionné.

- Si **non** est sélectionné, un administrateur Azure AD du client devra donner son consentement à l’organisation. Selon la configuration avec Azure AD, les utilisateurs peuvent envoyer une demande directement à partir de la même boîte de dialogue. S’il n’existe aucune option pour demander le consentement de l’administrateur, les utilisateurs doivent demander que ces autorisations soient ajoutées à leur administrateur Azure AD. Pour plus d’informations, voir la section suivante.

- Si **Oui** est sélectionné, assurez-vous que le paramètre Windows Defender’application Security Intelligence activé pour que les utilisateurs se connectent **?** soit définie sur **Oui** [dans Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d).Si **non** est sélectionné, vous devez demander à un administrateur Azure AD l’activer. 
  
## <a name="implement-required-enterprise-application-permissions"></a>Implémenter les autorisations Enterprise application requises 
Ce processus nécessite un administrateur global ou d’application dans le client.
 1. Ouvrez [Enterprise paramètres de l’application](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d). 
 2. Sélectionnez **Accorder le consentement administrateur pour l’organisation**.
 3. Si vous êtes en mesure de le faire, examinez les autorisations d’API requises pour cette application, comme l’illustre l’image suivante. Fournissez le consentement du client.

    ![accorder l’image de consentement.](../../media/security-intelligence-images/msi-grant-admin-consent.jpg)

  4. Si l’administrateur reçoit une erreur lors de la tentative de consentement manuel, essayez [l’option 1](#option-1-approve-enterprise-application-permissions-by-user-request) ou [l’option 2](#option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin) comme solution de contournement possible.
  
## <a name="option-1-approve-enterprise-application-permissions-by-user-request"></a>Option 1 Approuver les autorisations d’application d’entreprise par demande de l’utilisateur
> [!Note]
> Il s’agit actuellement d’une fonctionnalité d’aperçu.

Azure Active Directory administrateurs doivent autoriser les utilisateurs à demander le consentement de l’administrateur aux applications. Vérifiez que le paramètre est configuré sur **Oui** dans [Enterprise applications](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/).

![Enterprise paramètres utilisateur des applications.](../../media/security-intelligence-images/msi-enterprise-app-user-setting.jpg)

Vous pouvez obtenir plus d’informations dans [configurer le flux de travail de consentement de l’administrateur](/azure/active-directory/manage-apps/configure-admin-consent-workflow).

Une fois ce paramètre vérifié, les utilisateurs peuvent passer par la signature client d’entreprise sur [microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) et soumettre une demande de consentement de l’administrateur, y compris une justification.

![Flux de la signature Contoso.](../../media/security-intelligence-images/msi-contoso-approval-required.png)

L’administrateur peut examiner et approuver les autorisations d’application demandes de [consentement d’administrateur Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AccessRequests/menuId/).

Après avoir donné son consentement, tous les utilisateurs du client pourront utiliser l’application.
  
## <a name="option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin"></a>Option 2 Fournir le consentement de l’administrateur en authentifier l’application en tant qu’administrateur 
Ce processus nécessite que les administrateurs globaux traversent le flux de Enterprise de la sécurité [microsoft](https://www.microsoft.com/wdsi/filesubmission).

![Flux de la signature de consentement.](../../media/security-intelligence-images/msi-microsoft-permission-required.jpg)

Ensuite, les administrateurs examinent les autorisations et veillent à sélectionner **Consentement** au nom de votre organisation, puis sélectionnent **Accepter**.

Tous les utilisateurs du client pourront désormais utiliser cette application.

## <a name="option-3-delete-and-readd-app-permissions"></a>Option 3 : Supprimer et lire les autorisations de l’application
Si aucune de ces options ne résout le problème, essayez les étapes suivantes (en tant qu’administrateur) :

1. Supprimez les configurations précédentes de l’application. Go to [Enterprise applications](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/982e94b2-fea9-4d1f-9fca-318cda92f90b) and select **delete**.

   ![Supprimer les autorisations d’application.](../../media/security-intelligence-images/msi-properties.png)

2. Capturer TenantID à partir des [propriétés](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).

3. Remplacez {tenant-id} par le client spécifique qui doit donner son consentement à cette application dans l’URL ci-dessous. Copiez cette URL dans le navigateur. Le reste des paramètres est déjà terminé. 
``https://login.microsoftonline.com/{tenant-id}/v2.0/adminconsent?client_id=f0cf43e5-8a9b-451c-b2d5-7285c785684d&state=12345&redirect_uri=https%3a%2f%2fwww.microsoft.com%2fwdsi%2ffilesubmission&scope=openid+profile+email+offline_access``

   ![Autorisations requises.](../../media/security-intelligence-images/msi-microsoft-permission-requested-your-organization.png)

4. Examinez les autorisations requises par l’application, puis sélectionnez **Accepter**. 

5. Confirmez que les autorisations sont appliquées dans [le portail Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/ce60a464-5fca-4819-8423-bcb46796b051).

   ![Examinez que les autorisations sont appliquées.](../../media/security-intelligence-images/msi-permissions.jpg)
   
6. Connectez-vous [à Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) en tant qu’utilisateur d’entreprise avec un compte non administrateur pour voir si vous avez accès.

 Si l’avertissement n’est pas résolu après avoir suivi ces étapes de dépannage, appelez le support Microsoft.