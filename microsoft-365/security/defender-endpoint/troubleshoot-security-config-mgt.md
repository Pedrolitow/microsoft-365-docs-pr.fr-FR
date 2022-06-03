---
title: Résoudre les problèmes d’intégration liés à la gestion de la sécurité pour Microsoft Defender pour point de terminaison
description: Résolvez les problèmes qui peuvent survenir lors de l’intégration d’appareils à l’aide de Security Management pour Microsoft Defender pour point de terminaison.
keywords: résoudre les problèmes d’intégration, d’intégration, de visionneuse d’événements, de collecte et de préversion de données, de données de capteur et de diagnostics
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 4f309c98b7278dbeb062deacf49553b7e73f58da
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873785"
---
# <a name="troubleshoot-onboarding-issues-related-to-security-management-for-microsoft-defender-for-endpoint"></a>Résoudre les problèmes d’intégration liés à la gestion de la sécurité pour Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Gérer Microsoft Defender pour point de terminaison sur les appareils avec Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

La gestion de la sécurité pour Microsoft Defender pour point de terminaison est une fonctionnalité pour les appareils qui ne sont pas gérés par un Microsoft Endpoint Manager, Microsoft Intune ou Microsoft Endpoint Configuration Manager, pour recevoir des configurations de sécurité pour Microsoft Defender pour point de terminaison directement à partir de Endpoint Manager.
Pour plus d’informations sur la gestion de la sécurité pour Microsoft Defender pour point de terminaison, consultez [Gérer les Microsoft Defender pour point de terminaison sur les appareils avec Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Pour obtenir des instructions sur la gestion de la sécurité pour l’intégration Microsoft Defender pour point de terminaison, consultez [Microsoft Defender pour point de terminaison Security Configuration Management](security-config-management.md)

Cette intégration de bout en bout est conçue pour être sans friction et ne nécessite pas d’entrée utilisateur. Toutefois, si vous rencontrez des problèmes lors de l’intégration, vous pouvez afficher et résoudre les erreurs au sein de la plateforme Microsoft Defender pour point de terminaison.

> [!NOTE]
> Si vous rencontrez des problèmes avec le flux d’intégration pour les nouveaux appareils, passez en revue les [Microsoft Defender pour point de terminaison prérequis](/mem/intune/protect/mde-security-integration#prerequisites) et assurez-vous que les instructions d’intégration sont suivies.

Pour plus d’informations sur l’analyseur client, consultez [Troubleshoot sensor health using Microsoft Defender pour point de terminaison Client Analyzer](/microsoft-365/security/defender-endpoint/overview-client-analyzer).

## <a name="registering-domain-joined-computers-with-azure-active-directory"></a>Inscription d’ordinateurs joints à un domaine avec Azure Active Directory

Pour inscrire correctement des appareils auprès de Azure Active Directory, vous devez vous assurer que les éléments suivants sont les suivants :

- Les ordinateurs peuvent s’authentifier auprès du contrôleur de domaine
- Les ordinateurs ont accès aux ressources Microsoft suivantes à partir du réseau de votre organisation :
  - /windows/iot/iot-enterprise/commercialization/licensing
  - https://login.microsoftonline.com
  - https://device.login.microsoftonline.com
- Azure AD Connect est configuré pour synchroniser les objets ordinateur. Par défaut, les unités d’organisation d’ordinateur se trouvent dans l’étendue de synchronisation Azure AD Connect. Si les objets ordinateur appartiennent à des unités d’organisation spécifiques, configurez les unités d’organisation pour qu’elles se synchronisent dans Azure AD Connecter. Pour en savoir plus sur la synchronisation des objets ordinateur à l’aide d’Azure AD Connecter, consultez [filtrage basé sur les unités d’organisation](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#organizational-unitbased-filtering).

> [!IMPORTANT]
> Azure AD Connect ne synchronise pas Windows Server 2012 objets ordinateur R2. Si vous devez les inscrire auprès d’Azure AD pour Security Management pour Microsoft Defender pour point de terminaison, vous devez personnaliser la règle de synchronisation Azure AD Connect pour inclure ces objets d’ordinateur dans l’étendue de synchronisation. Consultez [les instructions d’application de la règle de jointure d’ordinateur dans Azure Active Directory Connecter]().

> [!NOTE]
> Pour terminer correctement le flux d’intégration et indépendamment du système d’exploitation d’un appareil, l’état Azure Active Directory d’un appareil peut changer, en fonction de l’état initial de l’appareil :
>
> <br>
>
>|Démarrage de l’état de l’appareil|Nouvel état de l’appareil|
>|---|---|
>|Déjà AADJ ou HAADJ|Reste tel qu’il est|
>|Ni AADJ ni jointure Azure Active Directory hybride (HAADJ) + Jointure à un domaine|L’appareil est HAADJ’d|
>|Pas AADJ ou HAADJ + Non joint à un domaine|L’appareil est AADJ’d|
>
> Où AADJ représente Azure Active Directory jointure et HAADJ représente Azure Active Directory jointure hybride.

## <a name="troubleshoot-errors-from-the-microsoft-defender-for-endpoint-portal"></a>Résoudre les erreurs à partir du portail Microsoft Defender pour point de terminaison

Par le biais du portail Microsoft Defender pour point de terminaison, les administrateurs de sécurité peuvent désormais résoudre les problèmes de gestion de la sécurité pour l’intégration Microsoft Defender pour point de terminaison.

Dans **l’inventaire des appareils points** \> de terminaison, la colonne **Managed By** a été ajoutée au filtre par canal de gestion (par exemple, MEM).

:::image type="content" source="./images/device-inventory-mde-error.png" alt-text="Page d’inventaire des appareils" lightbox="./images/device-inventory-mde-error.png":::

Pour afficher la liste de tous les appareils qui ont échoué à la gestion de la sécurité pour Microsoft Defender pour point de terminaison processus d’intégration, filtrez la table par **erreur MDE**.

Dans la liste, sélectionnez un appareil spécifique pour afficher les détails de résolution des problèmes dans le panneau latéral, en pointant sur la cause racine de l’erreur et la documentation correspondante.


:::image type="content" source="./images/secconfig-mde-error.png" alt-text="Critères de filtre appliqués sur la page d’inventaire des appareils" lightbox="./images/secconfig-mde-error.png":::

## <a name="run-microsoft-defender-for-endpoint-client-analyzer-on-windows"></a>Exécuter Microsoft Defender pour point de terminaison l’analyseur client sur Windows

Envisagez d’exécuter l’analyseur client sur les points de terminaison qui ne parviennent pas à terminer la gestion de la sécurité pour Microsoft Defender pour point de terminaison flux d’intégration. Pour plus d’informations sur l’analyseur client, consultez [Troubleshoot sensor health using Microsoft Defender pour point de terminaison Client Analyzer](overview-client-analyzer.md).

Le fichier de sortie de l’analyseur client (MDE Client Analyzer Results.htm) peut fournir des informations de résolution des problèmes clés :

- Vérifiez que le système d’exploitation de l’appareil est dans l’étendue de la gestion de la sécurité pour Microsoft Defender pour point de terminaison flux d’intégration dans la section **Détails généraux de l’appareil**
- Vérifier que l’appareil s’est inscrit à Azure Active Directory dans les **détails de gestion de la configuration des appareils**

  :::image type="content" source="images/client-analyzer-results.png" alt-text="Résultats de l’analyseur client" lightbox="images/client-analyzer-results.png":::

Dans la section **Résultats détaillés** du rapport, l’analyseur client fournit également des conseils exploitables.

> [!TIP]
> Assurez-vous que la section Résultats détaillés du rapport n’inclut pas d’erreurs et vérifiez tous les messages « Avertissement ».

Par exemple, dans le cadre du flux d’intégration de Security Management, il est nécessaire que l’ID de locataire Azure Active Directory dans votre locataire Microsoft Defender pour point de terminaison corresponde à l’ID de locataire SCP qui apparaît dans la section **Détails de la gestion** de la configuration des appareils des rapports. Le cas échéant, la sortie du rapport recommande d’effectuer cette vérification.

:::image type="content » source="images/detailed-results.png » alt-text="La page affichant les résultats détaillés » lightbox="images/detailed-results.png »

## <a name="general-troubleshooting"></a>Résolution des problèmes généraux

Si vous n’avez pas pu identifier l’appareil intégré dans AAD ou MEM et que vous n’avez pas reçu d’erreur lors de l’inscription, la vérification de la clé `Computer\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\SenseCM\\EnrollmentStatus` de Registre peut fournir des informations de dépannage supplémentaires.

:::image type="content" source="images/enrollment-status.png" alt-text="Page affichant l’état de l’inscription" lightbox="images/enrollment-status.png":::

Le tableau suivant répertorie les erreurs et les instructions sur ce qu’il faut essayer/vérifier pour résoudre l’erreur. Notez que la liste des erreurs n’est pas complète et est basée sur les erreurs classiques/courantes rencontrées par les clients dans le passé :

<br>

****

|Code d'erreur|État de l’inscription|Actions de l’administrateur|
|---|---|---|
|`5-7`, `9`, `11-12`, `26-33`|Erreur générale|L’appareil a été correctement intégré à Microsoft Defender pour point de terminaison. Toutefois, il y a eu une erreur dans le flux de gestion de la configuration de la sécurité. Cela peut être dû au fait que l’appareil ne répond pas aux [conditions préalables pour Microsoft Defender pour point de terminaison canal de gestion](security-config-management.md). L’exécution de [l’analyseur client](https://aka.ms/BetaMDEAnalyzer) sur l’appareil peut aider à identifier la cause racine du problème. Si cela ne vous aide pas, contactez le support technique.|
| `8`, `44` | problème de configuration Microsoft Endpoint Manager | L’appareil a été correctement intégré à Microsoft Defender pour point de terminaison. Toutefois, Microsoft Endpoint Manager n’a pas été configuré via le centre de Administration pour autoriser Microsoft Defender pour point de terminaison configuration de sécurité. Vérifiez que le [locataire Microsoft Endpoint Manager est configuré et que la fonctionnalité est activée](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management).|
|`13-14`,`20`,`24`,`25`|Problème de connectivité|L’appareil a été correctement intégré à Microsoft Defender pour point de terminaison. Toutefois, il y a eu une erreur dans le flux de gestion de la configuration de sécurité qui peut être due à un problème de connectivité. Vérifiez que les [points de terminaison Azure Active Directory et Microsoft Endpoint Manager sont ouverts](security-config-management.md#connectivity-requirements) dans votre pare-feu.|
|`10`,`42`|Échec général de jointure hybride|L’appareil a été correctement intégré à Microsoft Defender pour point de terminaison. Toutefois, une erreur s’est produite dans le flux de gestion de la configuration de la sécurité et le système d’exploitation n’a pas pu effectuer la jointure hybride. Utilisez [la résolution des problèmes liés aux appareils hybrides joints à Azure Active Directory](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current) pour résoudre les échecs de jointure hybride au niveau du système d’exploitation.|
|`15`|Incompatibilité de locataire|L’appareil a été correctement intégré à Microsoft Defender pour point de terminaison. Toutefois, le flux de gestion de la configuration de la sécurité a rencontré une erreur, car votre ID de locataire Microsoft Defender pour point de terminaison ne correspond pas à votre ID de locataire Azure Active Directory. Assurez-vous que l’ID de locataire Azure Active Directory de votre locataire Defender pour point de terminaison correspond à l’ID de locataire dans l’entrée SCP de votre domaine. Pour plus d’informations, [résolvez les problèmes d’intégration liés à la gestion de la sécurité pour Microsoft Defender pour point de terminaison](troubleshoot-security-config-mgt.md).|
|`16`,`17`|Erreur hybride - Point de connexion de service|L’appareil a été correctement intégré à Microsoft Defender pour point de terminaison. Toutefois, l’enregistrement du point de connexion de service (SCP) n’est pas configuré correctement et l’appareil n’a pas pu être joint à Azure AD. Cela peut être dû à la configuration du SCP pour joindre Enterprise DRS. Assurez-vous que les points d’enregistrement SCP vers AAD et SCP sont configurés en suivant les meilleures pratiques. Pour plus d’informations, consultez [Configurer un point de connexion de service](/azure/active-directory/devices/hybrid-azuread-join-manual#configure-a-service-connection-point).|
|`18`|Erreur de certificat|L’appareil a été correctement intégré à Microsoft Defender pour point de terminaison. Toutefois, une erreur s’est produite dans le flux de gestion de la configuration de la sécurité en raison d’une erreur de certificat d’appareil. Le certificat d’appareil appartient à un autre locataire. Vérifiez que les bonnes pratiques sont suivies lors de la création de [profils de certificat approuvés](/mem/intune/protect/certificates-trusted-root#create-trusted-certificate-profiles).|
|`36` , `37`| AAD Connecter configuration incorrecte |L’appareil a été correctement intégré à Microsoft Defender pour point de terminaison. Toutefois, une erreur s’est produite dans le flux de gestion de la configuration de la sécurité en raison d’une configuration incorrecte dans AAD Connecter. Pour identifier ce qui empêche l’appareil de s’inscrire auprès d’AAD, envisagez d’exécuter [l’outil de résolution des problèmes d’inscription](/samples/azure-samples/dsregtool/dsregtool) d’appareil. Pour Windows Server 2012 R2, exécutez les [instructions de dépannage dédiées](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-legacy).  |
|`38`,`41`|Erreur DNS|L’appareil a été correctement intégré à Microsoft Defender pour point de terminaison. Toutefois, une erreur s’est produite dans le flux de gestion de la configuration de la sécurité en raison d’une erreur DNS. Vérifiez les paramètres de connexion Internet et/ou DNS sur l’appareil. Les paramètres DNS non valides peuvent se trouver du côté de la station de travail. Active Directory vous oblige à utiliser le DNS de domaine pour fonctionner correctement (et non l’adresse du routeur). Pour plus d’informations, consultez [Résolution des problèmes d’intégration liés à la gestion de la sécurité pour Microsoft Defender pour point de terminaison](troubleshoot-security-config-mgt.md).|
|`40`|Problème de synchronisation d’horloge|L’appareil a été correctement intégré à Microsoft Defender pour point de terminaison. Toutefois, il y a eu une erreur dans le flux de gestion de la configuration de la sécurité. Vérifiez que l’horloge est correctement définie et synchronisée sur l’appareil où l’erreur se produit.|

## <a name="azure-active-directory-runtime-troubleshooting"></a>résolution des problèmes de Azure Active Directory Runtime

### <a name="azure-active-directory-runtime"></a>runtime Azure Active Directory

Le principal mécanisme de résolution des problèmes Azure Active Directory Runtime (AADRT) consiste à collecter les traces de débogage. Azure Active Directory Runtime sur Windows utilise le **fournisseur ETW avec l’ID bd67e65c-9cc2-51d8-7399-0bb9899e75c1**. Les traces ETW doivent être capturées avec la reproduction de l’échec (par exemple, si l’échec de jointure se produit, les traces doivent être activées pendant la durée de couverture des appels aux API AADRT pour effectuer la jointure).

Voir ci-dessous une erreur classique dans le journal AADRT et comment la lire :

:::image type="content" source="images/event-properties.png" alt-text="Page propriétés de l’événement" lightbox="images/event-properties.png":::

À partir des informations contenues dans le message, il est possible dans la plupart des cas de comprendre quelle erreur a été rencontrée, quelle API Win32 a retourné l’erreur (le cas échéant), quelle URL (le cas échéant) a été utilisée et quelle erreur d’API runtime AAD a été rencontrée.

## <a name="instructions-for-applying-computer-join-rule-in-aad-connect"></a>Instructions d’application de la règle de jointure d’ordinateur dans AAD Connecter

Pour la gestion de la sécurité pour Microsoft Defender pour point de terminaison sur Windows Server 2012 ordinateurs joints à un domaine R2, une mise à jour vers Azure AD Connecter règle de synchronisation « À partir de AD-Computer jointure » est nécessaire. Pour ce faire, vous pouvez cloner et modifier la règle, ce qui désactivera la règle « In from AD - Computer Join » d’origine. Azure AD Connecter offre par défaut cette expérience pour apporter des modifications aux règles intégrées.

> [!NOTE]
>Ces modifications doivent être appliquées sur le serveur sur lequel AAD Connecter est en cours d’exécution. Si plusieurs instances d’AAD Connecter déployées, ces modifications doivent être appliquées à toutes les instances.

1. Ouvrez l’application Éditeur de règles de synchronisation à partir du menu Démarrer. Dans la liste des règles, recherchez la règle nommée **In from AD – Computer Join**. **Notez la valeur de la colonne « Priorité » pour cette règle.**

   :::image type="content" source="images/57ea94e2913562abaf93749d306dd6cf.png" alt-text="Éditeur de règles de synchronisation" lightbox="images/57ea94e2913562abaf93749d306dd6cf.png":::

2. Lorsque la règle **Entrée à partir d’AD – Jointure de l’ordinateur** est mise en surbrillance, **sélectionnez Modifier**. Dans la boîte de dialogue **Modifier la confirmation de règle réservée** , sélectionnez **Oui**.

   :::image type="content" source="images/8854440d6180a5580efda24110551c68.png" alt-text="Page de confirmation de la règle réservée de modification" lightbox="images/8854440d6180a5580efda24110551c68.png":::

3. La fenêtre **Modifier la règle de synchronisation entrante** s’affiche. Mettez à jour la description de la règle pour noter que Windows Server 2012R2 sera synchronisé à l’aide de cette règle. Laissez toutes les autres options inchangées, à l’exception de la valeur priorité. Entrez une valeur de priorité supérieure à la valeur de la règle d’origine (comme indiqué dans la liste des règles).

   :::image type="content" source="images/ee0f29162bc3f2fbe666c22f14614c45.png" alt-text="Page Modifier la règle de synchronisation entrante dans laquelle vous entrez des valeurs" lightbox="images/ee0f29162bc3f2fbe666c22f14614c45.png":::

4. Sélectionnez **Suivant** trois fois. Vous accédez alors à la section « Transformations » de la règle. Ne modifiez pas les sections « Filtre d’étendue » et « Règles de jointure » de la règle. La section « Transformations » doit maintenant être affichée.

   :::image type="content" source="images/296f2c2a705e41233631c3784373bc23.png" alt-text="Règle de synchronisation entrante" lightbox="images/296f2c2a705e41233631c3784373bc23.png":::

5. Faites défiler jusqu’en bas de la liste des transformations. Recherchez la transformation pour l’attribut **cloudFiltered** . Dans la zone de texte de la colonne **Source** , sélectionnez tout le texte (Contrôle A) et supprimez-le. La zone de texte doit maintenant être vide.

6. Collez le contenu de la nouvelle règle dans la zone de texte.

    ```command
    IIF(
      IsNullOrEmpty([userCertificate])
      ||
      (
        (InStr(UCase([operatingSystem]),"WINDOWS") > 0)
        &&
        (Left([operatingSystemVersion],2) = "6.")
        &&
        (Left([operatingSystemVersion],3) <> "6.3")
      )
      ||
      (
        (Left([operatingSystemVersion],3) = "6.3")
        &&
        (InStr(UCase([operatingSystem]),"WINDOWS") > 0)
        &&
        With(
          $validCerts,
          Where(
            $c,
            [userCertificate],
            IsCert($c) && CertNotAfter($c) > Now() && RegexIsMatch(CertSubject($c), "CN=[{]*" & StringFromGuid([objectGUID]) & "[}]*", "IgnoreCase")),
          Count($validCerts) = 0)
      ),
      True,
      NULL
    )
    ```

7. Sélectionnez **Enregistrer** pour enregistrer la nouvelle règle.

> [!NOTE]
> Une fois cette modification de règle effectuée, une synchronisation complète de votre annuaire Active Directory est requise. Pour les environnements volumineux, il est recommandé de planifier cette modification de règle et la synchronisation complète pendant les périodes de calme Active Directory locales.

## <a name="related-topic"></a>Rubrique connexe

- [Gérer Microsoft Defender pour point de terminaison sur les appareils avec Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
