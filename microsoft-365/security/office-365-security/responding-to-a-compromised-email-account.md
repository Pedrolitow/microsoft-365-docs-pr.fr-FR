---
title: Réponse à un compte de messagerie compromis
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.collection:
- o365_security_incident_response
- M365-security-compliance
- m365solution-smb
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
localization_priority: Priority
search.appverid:
- MET150
description: Découvrez comment reconnaître un compte de messagerie compromis et y répondre à l’aide des outils disponibles dans Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 774d96fb22bb13d4b4edcfab45f27ca9e52c5e88
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50908829"
---
# <a name="responding-to-a-compromised-email-account"></a>Réponse à un compte de messagerie compromis

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

**Résumé** Découvrez comment reconnaître et répondre à un compte de messagerie compromis dans Microsoft 365.

## <a name="what-is-a-compromised-email-account-in-microsoft-365"></a>Qu’est un compte de messagerie compromis dans Microsoft 365 ?

L’accès aux boîtes aux lettres, données et autres services Microsoft 365 est contrôlé en utilisant des informations d’identification, par exemple un nom d’utilisateur et un mot de passe ou code confidentiel. Lorsqu’une personne autre que l’utilisateur initial vole ces informations d’identification, les informations d’identification volées sont considérés comme être compromises. Avec ces informations, le pirate peut se connecter en tant qu’utilisateur d’origine et effectuer des actions illicites.
En utilisant les informations d’identification volées, le pirate peut accéder à la boîte aux lettres de l'utilisateur Microsoft 365, aux dossiers SharePoint ou aux fichiers enregistrés dans le OneDrive de l’utilisateur. Souvent, les pirate envoient des messages électroniques en tant qu’utilisateur d’origine à des destinataires internes ou externes à l’organisation. Lorsque l’utilisateur malveillant envoie des données par messages électroniques à des destinataires externes, il s’agit « d’exfiltration de données ».

## <a name="symptoms-of-a-compromised-microsoft-email-account"></a>Symptômes d’un compte de messagerie Microsoft Corporation compromis

Les utilisateurs peuvent noter et rapporter des activités inhabituelles dans leur boîte aux lettres Microsoft 365. Voici quelques symptômes courantes :

- Des « activités douteuses », comme des courriers électroniques manquants ou supprimées.

- D’autres utilisateurs peuvent recevoir des messages électroniques du compte compromis sans que ces courriers correspondant n’apparaissent dans le dossier **Éléments envoyés** de l’expéditeur.

- La présence de règles de boîte de réception qui n’ont pas été créées par l’utilisateur initial ou l’administrateur. Ces règles peuvent automatiquement transférer des messages électroniques à des adresses inconnues ou les déplacer vers les dossiers **Notes**, **Courrier indésirable**, ou **Abonnements RSS**.

- Le nom d’affichage de l’utilisateur peut être modifié dans la liste d’adresses globale.

- La boîte aux lettres de l’utilisateur peut se trouver bloquée et ne peut plus envoyer de messages électroniques.

- Les dossiers Éléments envoyés ou Éléments supprimés dans Microsoft Outlook ou Outlook sur le web (anciennement Outlook Web App) contiennent des messages communs aux comptes piratés, comme par exemple « Je suis bloquée à Londres, envoyez-moi de l’argent. »

- Des modifications inhabituelle du profil, telles que le nom, le numéro de téléphone ou le code postal qui ont été mis à jour.

- Des modifications inhabituelle des informations d’identification, comme par exemple plusieurs requêtes de modification du mot de passe.

- La fonctionnalité de transfert du courrier a été ajoutée récemment.

- Une signature inhabituelle a été récemment ajoutée, par exemple, une signature apocryphe prétendant être une banque ou faisant référence à une ordonnance médicale.

Si un utilisateur rapporte un des symptômes ci-dessus, vous devez lancer un examen approfondi. Le centre de sécurité et conformité de Microsoft 365 et le portail Azure proposent des outils pour vous aider à investiguer les activités d’un compte d’utilisateur qui semble avoir été compromis.

- **Journaux d’audit unifiés dans le Centre de sécurité et conformité** : passez en revue toutes les activités du compte suspect en filtrant les résultats pour la plage de dates couvrant depuis immédiatement avant une activité suspecte jusqu’à la date du jour. Ne pas filtrer sur les activités au cours de la recherche.

- **Journaux d’audit de l’administrateur dans le Centre d'administration Exchange** : vous pouvez utiliser le Centre d’administration Exchange (EAC) dans Exchange Online pour rechercher et afficher les entrées dans le journal d’audit de l’administrateur. Le journal d’audit de l’administrateur enregistre des actions spécifiques, basées sur les cmdlets Exchange Online PowerShell, effectuées par les administrateurs et les utilisateurs disposant de privilèges d’administration. Les entrées du journal d’audit de l’administrateur vous fournissent des informations sur la cmdlet qui a été exécutée, les paramètres utilisés, l’utilisateur qui a exécuté la cmdlet et les objets concernés.

- **Utilisez les journaux de connexion Azure AD et autres rapports de risque du portail Azure AD** : examinez les valeurs de ces colonnes :

  - Examen des adresses IP
  - emplacements de connexion
  - heure de connexion
  - réussite ou échec des connexions

## <a name="how-to-secure-and-restore-email-function-to-a-suspected-compromised-microsoft-365-account-and-mailbox"></a>Comment sécuriser et restaurer la fonction de messagerie pour un compte Microsoft 365 supposé compromis et ses boîtes aux lettres

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=RE2jvOb&AutoPlayVideo=false]

Même après avoir récupéré l’accès à votre compte, l’utilisateur malveillant peut avoir ajouté des portes d’entrée malveillantes (back-door) qui lui permettront de reprendre le contrôle du compte.

Vous devez effectuer au plus vite toutes les étapes suivantes afin de récupérer l’accès à votre compte, pour vous assurer que l’utilisateur malveillant ne reprenne pas le contrôle de votre compte. Ces étapes permettent de supprimer les portes d’entrée malveillantes que le pirate peut avoir ajouté à votre compte. Une fois ces étapes effectuées, nous vous recommandons d’exécuter une analyse antivirus pour vous assurer que votre ordinateur n’est pas compromis.

### <a name="step-1-reset-the-users-password"></a>Étape 1 : Réinitialisez le mot de passe de l’utilisateur.

Suivez les procédures décrites dans [Réinitialiser un mot de passe d’entreprise pour une autre personne](../../admin/add-users/reset-passwords.md#reset-my-admin-password).

> [!IMPORTANT]
>
> - Ne pas envoyer de nouveau mot de passe à l’utilisateur initial par courrier électronique, car l’utilisateur malveillant a toujours accès à la boîte aux lettres à ce stade.
>
> - Assurez-vous que le mot de passe est robuste et qu’il contient des lettres majuscules et minuscules, au moins un chiffre et au moins un caractère spécial.
>
> - Ne pas réutiliser un de vos cinq derniers mots de passe. Même si l’exigence de l’historique de mot de passe vous permet de réutiliser un mot de passe plus récent, vous devez en sélectionner un que l’utilisateur malveillant ne peut pas deviner.
>
> - Si votre identité locale est fédérée avec Microsoft 365, vous devez modifier votre mot de passe local, puis vous devez informer votre administrateur de l’attaque.
>
> - Veillez à mettre à jour les mots de passe d’application. Les mots de passe d’application ne sont pas automatiquement révoqués lors de la réinitialisation du mot de passe d’un compte utilisateur. L’utilisateur doit supprimer les mots de passe d’application existants et en créer de nouveaux. Pour obtenir des instructions, voir [Créer et supprimer des mots de passe d’application à partir de la page Vérification de sécurité supplémentaire](/azure/active-directory/user-help/multi-factor-authentication-end-user-app-passwords#create-and-delete-app-passwords-from-the-additional-security-verification-page).
>
> - Nous vous recommandons vivement d’activer l’authentification multifacteur (MFA) pour éviter les compromissions, en particulier pour les comptes avec des privilèges d’administration. Pour en savoir plus sur l’authentification multifacteur, voir [Configurer l’authentification multifacteur](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

### <a name="step-2-remove-suspicious-email-forwarding-addresses"></a>Étape 2 : Supprimer des adresses de transfert de courrier suspectes

1. Ouvrez le Centre d’administration Microsoft 365 à l’adresse <https://admin.microsoft.com>

2. Accédez à **Utilisateurs** \> **Utilisateurs actifs**. Recherchez le compte de l’utilisateur en question, puis sélectionnez l’utilisateur (ligne) sans activer la case à cocher.

3. Dans le menu volant de détails qui s’affiche, sélectionnez l’onglet **Courrier**.

4. Si la valeur de la section **Transfert de courrier** est **Appliqué**, cliquez sur **Gérer le transfert de courrier**. Dans le menu volant **Gérer le transfert de courrier** qui s’affiche, désactivez **Transférer tous les courriers envoyés à cette boîte aux lettres**, puis cliquez sur **Enregistrer les modifications**.

### <a name="step-3-disable-any-suspicious-inbox-rules"></a>Étape 3 : Désactiver toutes règles de boîte de réception suspectes

1. Ouvrez la boîte aux lettres d’archivage avec Outlook sur le web.

2. Cliquez sur l’icône en forme d’engrenage, puis **Courrier**.

3. Cliquez sur **Règles de boîte de réception et de rangement** et passer en revue les règles.

4. Désactiver ou supprimer des règles suspectes.

### <a name="step-4-unblock-the-user-from-sending-mail"></a>Étape 4 : Redonner à l’utilisateur l’autorisation d’envoyer des messages électroniques

Si la boîte aux lettres soupçonnée d'avoir été compromise a été utilisée illicitement pour envoyer des pourriels, il est probable que la boîte aux lettres ne peut plus envoyer de messages électroniques.

Pour débloquer la boîte aux lettres et permettre l’envoi de messages électroniques, suivez les procédures décrites dans [Suppression d’un utilisateur du portail Utilisateurs restreints après l’envoi de courrier indésirable](removing-user-from-restricted-users-portal-after-spam.md).

### <a name="step-5-optional-block-the-user-account-from-signing-in"></a>Étape 5 (facultatif) : Empêcher le compte d’utilisateur de se connecter

> [!IMPORTANT]
> Vous pouvez bloquer le compte soupçonné d'avoir été compromis et l’empêcher de se connecter jusqu'à ce qu’à votre avis, il est sûr de réactiver l’accès.

1. Ouvrez le Centre d’administration Microsoft 365 et accédez à **Utilisateurs** \> **Utilisateurs actifs**.

2. Recherchez et sélectionnez le compte d’utilisateur, cliquez sur l’![icône Plus](../../media/ITPro-EAC-MoreOptionsIcon.png), puis sélectionnez **Modifier l’état de connexion**.

3. Dans le volet **Bloquer la connexion** qui s’affiche, sélectionnez **Bloquer la connexion de cet utilisateur**, puis cliquez sur **Enregistrer les modifications**.

4. Ouvrez le Panneau de configuration Exchange (CAE) à l’adresse <admin.protection.outlook.com/ecp/>, puis accédez à **Destinataires > Boîtes aux lettres**.

5. Recherchez et sélectionnez l’utilisateur. Dans le volet Détails, procédez comme suit :

   - Dans la section **Fonctionnalités téléphoniques et vocales**, procédez comme suit :

     - Sélectionnez **Désactiver ActiveSync Exchange** puis cliquez sur **Oui** dans le message d’avertissement qui s’affiche.
     - Sélectionnez **Désactiver OWA pour les appareils** puis cliquez sur **Oui** dans le message d’avertissement qui s’affiche.

   - Dans la section **Connectivité de la messagerie** pour Outlook sur le web, cliquez sur **Désactiver** puis sur **Oui** dans le message d’avertissement qui s’affiche.

### <a name="step-6-optional-remove-the-suspected-compromised-account-from-all-administrative-role-groups"></a>Étape 6 (facultatif) : Supprimer le compte soupçonné d'avoir été compromis de tous les groupes de rôles d’administration

> [!NOTE]
> L’appartenance au groupe de rôles d’administration peut être restaurée une fois que le compte a été sécurisé.

1. Connectez-vous à l’aide d’un compte d’administrateur global :

2. Dans le Centre d’administration Microsoft 365, procédez comme suit :

   1. Accédez à **Utilisateurs** \> **Utilisateurs actifs**.
   2. Recherchez et sélectionnez le compte d’utilisateur, cliquez sur l’![icône Plus](../../media/ITPro-EAC-MoreOptionsIcon.png), puis sélectionnez **Gérer les rôles**.
   3. Supprimez les rôles d’administrateur attribués au compte. Lorsque vous avez terminé, cliquez sur **Enregistrer les modifications**.

3. Dans le Centre de sécurité et de conformité à l'adresse <https://protection.office.com>, procédez comme suit :

   Sélectionnez **Autorisations**, puis chaque groupe de rôles dans la liste, et recherchez le compte d’utilisateur dans la section **Membres** du menu volant de détails qui s’affiche. Si le groupe de rôles contient le compte d’utilisateur, procédez comme suit :

   a. Cliquez sur **Modifier** en regard de **Membres**.
   b. Dans le menu volant **Modification des membres choisis** qui apparaît, cliquez sur **Modifier**.
   c. Dans le menu volant **Sélectionner des membres** qui apparaît, sélectionnez le compte d’utilisateur, puis cliquez sur **Supprimer**. Lorsque vous avez terminé, cliquez sur **Terminé**, **Enregistrer**, puis **Fermer**.

4. Dans le Centre d’administration Exchange, à l’adresse <admin.protection.outlook.com/ecp/>, procédez comme suit :

   Sélectionnez **Autorisations**, puis chaque groupe de rôles manuellement, et, dans le volet Détails, vérifiez les comptes d’utilisateurs dans la section **Membres**.  Si le groupe de rôles contient le compte d’utilisateur, procédez comme suit :

   a. Sélectionnez le groupe de rôles, cliquez sur **Modifier** ![Icône Modifier](../../media/ITPro-EAC-EditIcon.png).
   b. Dans la section **Membre**, sélectionnez le compte d’utilisateur, puis cliquez sur **Supprimer** ![Icône Supprimer](../../media/ITPro-EAC-RemoveIcon.gif). Lorsque vous avez terminé, cliquez sur **Enregistrer**.

### <a name="step-7-optional-additional-precautionary-steps"></a>Étape 7 (facultatif) : Mesures de précaution supplémentaires

1. Vérifiez vos éléments envoyés. Vous devriez peut-être informer les membres de votre liste de contacts que votre compte a été compromis. L’utilisateur malveillant les a peut-être contacté pour demander de l’argent ou tenter d’usurper leur identité, par exemple, a déclaré que vous étiez bloqué dans un pays étranger et que vous aviez besoin d'argent, ou leur a peut-être envoyé un virus pour pirater leur ordinateur.

2. Tout autre service qui utilise ce compte Exchange en tant que compte de courrier en alternative a pu être compromis. Tout d’abord, effectuez ces étapes pour votre abonnement Microsoft 365, puis pour vos autres comptes.

3. Assurez-vous que vos informations de contact, tels que les numéros de téléphone et adresses, sont correctes.

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Sécuriser Microsoft 365 comme un pro de la cyber-sécurité

Votre abonnement Microsoft 365 inclut un ensemble puissant de fonctionnalités de sécurité que vous pouvez utiliser pour protéger vos données et vos utilisateurs.  Utilisez la [Feuille de route du Centre de sécurité Microsoft 365 : principales priorités pour les 30 premiers jours, 90 premiers jours et au-delà](security-roadmap.md), pour implémenter les meilleures pratiques recommandées par Microsoft pour sécuriser votre client Microsoft 365.

- Tâches à effectuer lors des 30 premiers jours.  Elle ont un effet immédiat et n’ont qu’un faible impact négatif sur vos utilisateurs.

- Tâches à accomplir dans les 90 premiers jours. Ces tâches prennent un peu plus de temps à planifier et à implémenter, mais augmentent considérablement votre sécurité.

- Au-delà de 90 jours. Ces améliorations sont à mettre en place pendant les 90 premiers jours.

## <a name="see-also"></a>Voir aussi

- [Détecter et résoudre les attaques par injections sur les règles d’Outlook et les formulaires personnalisés dans Microsoft 365](detect-and-remediate-outlook-rules-forms-attack.md)

- [Centre de plaintes contre la criminalité sur Internet ](https://www.ic3.gov/Home/Ransomware)

- [Securities and Exchange Commission (SEC) : fraude à « l’hameçonnage » (phishing)](https://www.sec.gov/investor/pubs/phishing.htm)

- Pour signaler un courrier électronique indésirable directement à Microsoft et à votre administrateur [Utiliser le complément Message de Rapport](https://support.microsoft.com/office/b5caa9f1-cdf3-4443-af8c-ff724ea719d2)