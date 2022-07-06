---
title: Configurer le chiffrement des messages Microsoft Purview
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/16/2022
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 7ff0c040-b25c-4378-9904-b1b50210d00e
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Découvrez le chiffrement de messages Microsoft Purview qui permet la communication par e-mail protégée avec des personnes à l’intérieur et à l’extérieur de votre organisation.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.openlocfilehash: 828588491c3efbc696994f6073ca4ce849a64be5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622126"
---
# <a name="set-up-message-encryption"></a>Configurer le chiffrement des messages

Le chiffrement de messages Microsoft Purview permet aux organisations de partager des e-mails protégés avec n’importe qui sur n’importe quel appareil. Les utilisateurs peuvent échanger des messages protégés avec d’autres organisations Microsoft 365, ainsi que des tiers à l’aide de Outlook.com, Gmail et d’autres services de messagerie.

Suivez les étapes ci-dessous pour vous assurer que le chiffrement de messages Microsoft Purview est disponible dans votre organisation.

## <a name="verify-that-azure-rights-management-is-active"></a>Vérifiez que Azure Rights Management est activé.

Le chiffrement de messages Microsoft Purview tire parti des fonctionnalités de protection [d’Azure Rights Management Services (Azure RMS)](/azure/information-protection/what-is-information-protection), la technologie utilisée par [Azure Information Protection](/azure/information-protection/what-is-azure-rms) pour protéger les e-mails et les documents via le chiffrement et les contrôles d’accès.

La seule condition préalable à l’utilisation du chiffrement de messages Microsoft Purview est qu’[Azure Rights Management](/azure/information-protection/what-is-azure-rms) doit être activé dans le locataire de votre organisation. Si c’est le cas, Microsoft 365 active automatiquement le chiffrement des messages et vous n’avez rien à faire.

Azure RMS est également activé automatiquement pour la plupart des offres éligibles, de sorte que vous n’avez probablement pas besoin d’effectuer quoi que ce soit à cet égard. Voir [Activation de Microsoft Azure Rights Management](/azure/information-protection/activate-service) pour plus d’informations.

> [!IMPORTANT]
> Si vous utilisez Active Directory Rights Management service (AD RMS) avec Exchange Online, vous devez [migrer vers Azure Information Protection](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) avant de pouvoir utiliser le chiffrement des messages. Le chiffrement de messages Microsoft Purview n’est pas compatible avec AD RMS.

Pour plus d’informations, voir :

- [Faq sur le chiffrement de messages](ome-faq.yml) pour vérifier si votre plan d’abonnement inclut Azure Information Protection (qui inclut la fonctionnalité Azure RMS).
- [Azure Information Protection](https://azure.microsoft.com/services/information-protection/) pour plus d’informations sur l’achat d’un abonnement éligible.

### <a name="manually-activating-azure-rights-management"></a>Activation manuelle d’Azure Rights Management

Si vous avez désactivé Azure RMS, ou si le service n’a pas été automatiquement activé pour une raison quelconque, vous pouvez l’activer manuellement dans le :

- **Centre d’administration Microsoft 365** : reportez-vous à [Comment activer Azure Rights Management à partir du centre d’administration](/azure/information-protection/activate-office365) pour obtenir des instructions.
- **Portail Azure** : reportez-vous à [Comment activer Azure Rights Management à partir du portail Azure](/azure/information-protection/activate-azure) pour obtenir des instructions.

## <a name="configure-management-of-your-azure-information-protection-tenant-key"></a>Configurer la gestion de votre clé de client Azure Information Protection

Il s’agit d’une étape facultative. Autoriser Microsoft à gérer la clé racine pour Azure Information Protection est le paramètre par défaut et la meilleure pratique recommandée pour la plupart des organisations. Si cela est le cas, vous n’avez rien à faire.

Il existe de nombreuses raisons, par exemple des exigences de conformité, qui peuvent nécessiter de créer et gérer votre propre clé racine (également connue sous le nom Utilisation de votre propre clé (BYOK)). Si c’est le cas, nous vous recommandons d’effectuer les étapes requises avant de configurer le chiffrement de messages Microsoft Purview. Pour plus d’informations, reportez-vous à [Planification et implémentation de votre clé de client Azure Information Protection](/information-protection/plan-design/plan-implement-tenant-key).

## <a name="verify-microsoft-purview-message-encryption-configuration-in-exchange-online-powershell"></a>Vérifier la configuration du chiffrement de messages Microsoft Purview dans le PowerShell Exchange Online

Vous pouvez vérifier que votre client Microsoft 365 est correctement configuré pour utiliser le chiffrement de messages Microsoft Purview dans le [PowerShell Exchange Online](/powershell/exchange/exchange-online-powershell).

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) à l’aide d’un compte disposant des autorisations d’administrateur général dans votre client Microsoft 365.

2. Exécutez la cmdlet Get-IRMConfiguration.

     Vous devez voir une valeur de $True pour le paramètre AzureRMSLicensingEnabled, ce qui indique que le chiffrement de messages Microsoft Purview est configuré dans votre locataire. Si ce n’est pas le cas, utilisez Set-IRMConfiguration pour définir la valeur d’AzureRMSLicensingEnabled sur $True pour activer le chiffrement de messages Microsoft Purview.

3. Exécutez la cmdlet Test-IRMConfiguration en utilisant la syntaxe suivante :

   ```powershell
   Test-IRMConfiguration [-Sender <email address> -Recipient <email address>]
   ```

   **Exemple** :

   ```powershell
   Test-IRMConfiguration -Sender securityadmin@contoso.com -Recipient securityadmin@contoso.com
   ```

   - Pour l'expéditeur et le destinataire, utilisez l'adresse e-mail de n'importe quel utilisateur de votre client Microsoft 365.

     Vos résultats doivent être similaires à ce qui suit :

     ```console
     Results : Acquiring RMS Templates ...
                - PASS: RMS Templates acquired.  Templates available: Contoso  - Confidential View Only, Contoso  - Confidential, Do Not
            Forward.
            Verifying encryption ...
                - PASS: Encryption verified successfully.
            Verifying decryption ...
                - PASS: Decryption verified successfully.
            Verifying IRM is enabled ...
                - PASS: IRM verified successfully.

            OVERALL RESULT: PASS
     ```

   - Le nom de votre organisation remplacera *Contoso*.

   - Les noms des modèles par défaut peuvent être différents de ceux affichés ci-dessus. Pour plus d’informations, reportez-vous à [Configurer et gérer des modèles pour Azure Information Protection](/azure/information-protection/configure-policy-templates).

4. Si le test échoue avec un message d’erreur **Échec de l’acquisition des modèles RMS**, exécutez les commandes suivantes et exécutez l’applet de commande Test-IRMConfiguration pour vérifier que ça marche.

   ```powershell
   $RMSConfig = Get-AadrmConfiguration
   $LicenseUri = $RMSConfig.LicensingIntranetDistributionPointUrl
   Set-IRMConfiguration -LicensingLocation $LicenseUri
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```
5. Exécutez la cmdlet Remove-PSSession pour vous déconnecter du service Rights Management.

     ```powershell
     Remove-PSSession $session
     ```

## <a name="next-steps-define-mail-flow-rules-to-use-microsoft-purview-message-encryption"></a>Étapes suivantes : définir des règles de flux de messagerie pour utiliser le chiffrement de messages Microsoft Purview

S’il existe des règles de flux de messagerie précédemment configurées pour chiffrer le courrier électronique dans votre organisation, vous devez mettre à jour les règles existantes pour utiliser le chiffrement de messages Microsoft Purview. Pour les nouveaux déploiements, vous devez créer des règles de flux de messagerie.

> [!IMPORTANT]
> Si vous ne mettez pas à jour les règles de flux de messagerie existantes, vos utilisateurs continueront à recevoir des messages chiffrés qui utilisent le format de pièce jointe HTML précédent, au lieu de la nouvelle expérience transparente.

Les règles de flux de messagerie déterminent les conditions dans lesquelles les e-mails doivent être chiffrés, ainsi que les conditions pour supprimer ce chiffrement. Lorsque vous configurez une action pour une règle, tous les messages correspondant aux conditions de la règle sont chiffrés lorsqu’elles sont envoyées.

Pour connaître les étapes de création du chiffrement de message des règles de flux de messagerie, consultez [Définir des règles de flux de messagerie pour chiffrer les messages électroniques dans Office 365](define-mail-flow-rules-to-encrypt-email.md).

Pour mettre à jour les règles existantes afin d’utiliser le chiffrement de messages Microsoft Purview :

1. Dans le Centre d’administration Microsoft 365, accédez à **Centres d’administration** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.
2. Dans le Centre d’administration Exchange, accédez à **Flux de messagerie > Règles**.
3. Pour chaque règle, dans **Procédez comme suit** :
    - Sélectionnez **Modifier la sécurité des messages**.
    - Sélectionnez **Appliquer le chiffrement des messages Office 365 et la protection des droits**.
    - Sélectionnez un modèle RMS dans la liste.
    - Cliquez sur **Enregistrer**.
    - Sélectionnez **OK**.
