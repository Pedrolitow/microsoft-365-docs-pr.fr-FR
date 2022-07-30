---
title: Modifier les serveurs de noms pour configurer Microsoft 365 avec n’importe quel bureau d’enregistrement de domaines
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- VSBFY23
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEU150
- GEA150
ms.assetid: a8b487a9-2a45-4581-9dc4-5d28a47010a2
description: Découvrez comment ajouter et configurer votre domaine dans Microsoft 365 afin que vos services tels que le courrier électronique et Skype Entreprise Online utilisent votre propre nom de domaine.
ms.openlocfilehash: e33bfad12c3785e95ca328c4f0e82ab640d549d0
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2022
ms.locfileid: "67085946"
---
# <a name="change-nameservers-to-set-up-microsoft-365-with-any-domain-registrar"></a>Modifier les serveurs de noms pour configurer Microsoft 365 avec n’importe quel bureau d’enregistrement de domaines

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Suivez ces instructions pour ajouter et configurer votre domaine dans Microsoft 365 afin que vos services comme le courrier électronique et Teams utilisent votre propre nom de domaine. Pour ce faire, vous allez vérifier votre domaine, puis remplacer les serveurs de noms de votre domaine par Microsoft 365 afin que les enregistrements DNS corrects puissent être configurés pour vous. Suivez ces étapes si les instructions suivantes décrivent votre situation :

- Vous disposez de votre propre domaine et souhaitez le configurer pour qu’il fonctionne avec Microsoft 365.

- Vous souhaitez que Microsoft 365 gère vos enregistrements DNS pour vous. Si vous le souhaitez, vous pouvez [gérer vos propres enregistrements DNS](../setup/add-domain.md).

## <a name="add-a-txt-or-mx-record-for-verification"></a>Ajouter un enregistrement TXT ou MX à des fins de vérification

> [!NOTE]
> Vous ne devez créer qu'un seul des deux enregistrements. TXT est le type d'enregistrement préféré, mais certains fournisseurs d'hébergement DNS ne le prennent pas en charge, auquel cas vous pouvez créer un enregistrement MX à la place.

Avant que vous puissiez utiliser votre domaine avec Microsoft 365, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft 365 que le domaine vous appartient.

> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement.

### <a name="find-the-area-on-your-dns-hosting-providers-website-where-you-can-create-a-new-record"></a>Recherchez la zone sur le site web de votre fournisseur d’hébergement DNS où vous pouvez créer un enregistrement

1. Connectez-vous sur le site web de votre fournisseur d'hébergement DNS.

2. Choisissez votre domaine.

3. Recherchez la page dans laquelle vous pouvez modifier les enregistrements DNS pour votre domaine.

### <a name="create-the-record"></a>Créer l’enregistrement

Selon que vous créez un enregistrement TXT ou un enregistrement MX, effectuez l’une des opérations suivantes :

**Si vous créez un enregistrement TXT, utilisez les valeurs suivantes :**

<br>

****

|Type d’enregistrement|Alias ou nom d’hôte|Valeur|Durée de vie|
|---|---|---|---|
|TXT|Effectuez l'une des opérations suivantes : Tapez **@**, laissez le champ vide ou entrez le nom de votre domaine.  <p> **Remarque** : différents hôtes DNS ont des exigences différentes pour ce champ.|MS=ms *XXXXXXXX* <p> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Microsoft 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|Définissez cette valeur sur **1 heure** ou sur l'équivalent en minutes ( **60** ), en secondes ( **3600** ), etc.|
|||||

**Si vous créez un enregistrement MX, utilisez les valeurs suivantes :**

<br>

****

|Type d’enregistrement|Alias ou nom d’hôte|Valeur|Priority (Priorité)|TTL (Durée de vie)|
|---|---|---|---|---|
|MX|Entrez soit **@**, soit votre nom de domaine. |MS=ms *XXXXXXXX* **Remarque :** il s’agit d’un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Microsoft 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|Pour **Priorité**, afin d’éviter les conflits avec l’enregistrement MX utilisé pour le flux de courrier électronique, utilisez une priorité plus basse que la priorité des enregistrements MX existants. Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml).|Définissez cette valeur sur **1 heure** ou sur l'équivalent en minutes ( **60** ), en secondes ( **3600** ), etc.|
||||||

### <a name="save-the-record"></a>Enregistrer l’enregistrement

L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Microsoft 365 et demandez à Microsoft 365 de rechercher l’enregistrement.

Lorsque Microsoft 365 trouve l’enregistrement TXT approprié, votre domaine est vérifié.

1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez.

3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.

4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.

> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

Quand vous arrivez à la dernière étape de l’Assistant Configuration des domaines dans Microsoft 365, il vous reste une tâche. Pour configurer votre domaine avec les services Microsoft 365, tels que le courrier électronique, vous modifiez les enregistrements de serveur de noms (ou NS) de votre domaine auprès de votre bureau d’enregistrement de domaines pour qu’ils pointent vers les serveurs de noms principaux et secondaires Microsoft 365. Ensuite, étant donné que Microsoft 365 héberge votre DNS, les enregistrements DNS requis pour vos services sont automatiquement configurés pour vous. Vous pouvez mettre à jour les enregistrements de serveur de noms vous-même en suivant les étapes fournies éventuellement par votre bureau d'enregistrement de domaines dans l'aide disponible sur son site web. Si vous n'êtes pas familiarisé avec DNS, contactez le support du bureau d'enregistrement de domaines.

::: moniker range="o365-worldwide"

Pour changer vous-même les serveurs de noms de votre domaine sur le site web de votre bureau d'enregistrement de domaines, procédez comme suit :

1. Recherchez la zone sur le site web du bureau d’enregistrement de domaines où vous pouvez modifier les serveurs de noms de votre domaine ou une zone dans laquelle vous pouvez utiliser des serveurs de noms personnalisés.

2. Créez des enregistrements de serveur de noms ou modifiez les enregistrements de serveur de noms existants pour qu’ils correspondent aux valeurs suivantes :

    - Prénom : ns1.bdm.microsoftonline.com
    - Deuxième serveur de noms : ns2.bdm.microsoftonline.com
    - Troisième serveur de noms : ns3.bdm.microsoftonline.com
    - Quatrième serveur de noms : ns4.bdm.microsoftonline.com

   > [!TIP]
   > Il est préférable d’ajouter les quatre enregistrements, mais si votre bureau d’enregistrement ne prend en charge que deux enregistrements, ajoutez **ns1.bdm.microsoftonline.com** et **ns2.bdm.microsoftonline.com**.

3. Enregistrez vos modifications.

> [!CAUTION]
> Lorsque vous modifiez les enregistrements NS de votre domaine pour qu’ils pointent vers les serveurs de noms Microsoft 365, tous les services actuellement associés à votre domaine sont affectés. Si vous avez ignoré des étapes de l’Assistant, telles que l’ajout d’adresses e-mail, ou si vous utilisez votre domaine pour des blogs, des paniers d’achat ou d’autres services, des étapes supplémentaires sont requises. Dans le cas contraire, cette modification peut entraîner des temps d’arrêt du service, tels que l’absence d’accès aux e-mails ou l’inaccessibilité de votre site web actuel.

::: moniker-end

::: moniker range="o365-21vianet"

1. Identifiez la zone sur le site web du bureau d'enregistrement de domaines dans laquelle vous pouvez modifier les serveurs de noms pour votre domaine.

2. Créez deux enregistrements de serveur de noms, ou modifiez les enregistrements existants pour qu'ils correspondent aux valeurs suivantes :

   - Prénom : ns1.dns.partner.microsoftonline.cn
   - Deuxième serveur de noms : ns2.dns.partner.microsoftonline.cn

   > [!TIP]
   > Vous devez utiliser au moins deux enregistrements de serveur de noms. S’il existe d’autres serveurs de noms répertoriés, vous pouvez les supprimer ou les remplacer par **ns3.dns.partner.microsoftonline.cn** et **ns4.dns.partner.microsoftonline.cn**.

3. Enregistrez vos modifications.

> [!CAUTION]
> Lorsque vous modifiez les enregistrements NS de votre domaine pour qu’ils pointent vers le Office 365 géré par les serveurs de noms 21Vianet, tous les services actuellement associés à votre domaine sont affectés. Si vous avez ignoré des étapes de l’Assistant, telles que l’ajout d’adresses e-mail, ou si vous utilisez votre domaine pour des blogs, des paniers d’achat ou d’autres services, des étapes supplémentaires sont requises. Dans le cas contraire, cette modification peut entraîner des temps d’arrêt du service, tels que l’absence d’accès aux e-mails ou l’inaccessibilité de votre site web actuel.

::: moniker-end

Voici, par exemple, quelques étapes supplémentaires qui peuvent être nécessaires pour le courrier et l'hébergement du site web :

- Déplacez toutes les adresses e-mail qui utilisent votre domaine vers Microsoft 365 avant de modifier vos enregistrements NS.

- Vous voulez ajouter un domaine actuellement utilisé avec une adresse de site web, par exemple `https://www.fourthcoffee.com`? Vous pouvez suivre les étapes ci-dessous pendant que vous ajoutez le domaine pour conserver son site web hébergé où le site est hébergé maintenant afin que les utilisateurs puissent toujours accéder au site web après avoir modifié les enregistrements NS du domaine pour qu’ils pointent vers Microsoft 365.

1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

2. Dans la page **Domaines**, sélectionnez un domaine.

3. Dans la page des détails du domaine, sélectionnez l’onglet **Enregistrements DNS** .

4. Sélectionnez **Ajouter un enregistrement**.

5. Dans le volet **Ajouter un enregistrement DNS personnalisé**, dans la liste déroulante **Type**, sélectionnez **A (Adresse).**

6. Dans la zone **Nom d’hôte ou Alias** , tapez **@**.

7. Dans la zone **Adresse IP** , tapez l’adresse IP statique du site web où il est actuellement hébergé. Par exemple, 172.16.140.1.

   > [!IMPORTANT]
   > Il doit s’agir d’une adresse IP _statique_ pour le site web, et non d’une adresse IP _dynamique_ . Pour vous assurer que vous pouvez obtenir une adresse IP statique pour votre site web public, consultez le site qui héberge votre site web.

8. Si vous souhaitez modifier le paramètre de durée de vie de l’enregistrement, sélectionnez une nouvelle durée dans la liste déroulante **TTL** . Sinon, passez à l’étape 9.

9. Sélectionnez **Enregistrer**.

De plus, vous pouvez créer un enregistrement CNAME pour aider les clients à trouver votre site web.

1. Sélectionnez **Ajouter un enregistrement**.
2. Dans le volet **Ajouter un enregistrement DNS personnalisé**, dans la liste déroulante **Type**, sélectionnez **CNAME (Alias).**
3. Dans la zone **Nom d’hôte ou Alias** , tapez **www**.
4. Dans la zone **Points à l’adresse** , tapez le nom de domaine complet (FQDN) de votre site web. Par exemple, **contoso.5om**.
5. Si vous souhaitez modifier le paramètre de durée de vie de l’enregistrement, sélectionnez une nouvelle durée dans la liste déroulante **TTL** . Sinon, passez à l’étape 6.
6. Sélectionnez **Enregistrer**.

Une fois les enregistrements du serveur de noms mis à jour pour pointer vers Microsoft, la configuration de votre domaine est terminée. Email est routée vers Microsoft, et le trafic vers votre adresse de site web continue d’être acheminé vers votre hôte de site web actuel.

> [!NOTE]
> Your nameserver record updates may take up to several hours to update across the Internet's DNS system. Ensuite, vos e-mails Microsoft et d’autres services seront tous configurés pour fonctionner avec votre domaine.

## <a name="related-content"></a>Contenu associé

[Ajouter des enregistrements DNS pour connecter votre domaine](create-dns-records-at-any-dns-hosting-provider.md) (article)\
[Rechercher et corriger les problèmes, y compris de messagerie, après avoir ajouté votre domaine ou des enregistrements DNS](find-and-fix-issues.md) (article)\
[Gérer des domaines](/admin) (page de lien)
