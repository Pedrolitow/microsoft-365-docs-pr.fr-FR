---
title: Modifier les serveurs de noms pour configurer Microsoft 365 avec n’importe quel bureau d’enregistrement de domaines
f1.keywords:
- CSH
ms.author: efrene
author: efrene
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
description: Découvrez comment ajouter et configurer votre domaine dans Microsoft 365 afin que vos services tels que la messagerie électronique et Skype Entreprise Online utilisent votre propre nom de domaine.
ms.openlocfilehash: f66099b7496bc60a7b12618785d1596eab70b174
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68728684"
---
# <a name="change-nameservers-to-set-up-microsoft-365-with-any-domain-registrar"></a>Modifier les serveurs de noms pour configurer Microsoft 365 avec n’importe quel bureau d’enregistrement de domaines

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Suivez ces instructions pour ajouter et configurer votre domaine dans Microsoft 365 afin que vos services tels que la messagerie électronique et Teams utilisent votre propre nom de domaine. Pour ce faire, vous allez vérifier votre domaine, puis remplacer les serveurs de noms de votre domaine par Microsoft 365 afin que les enregistrements DNS appropriés puissent être configurés pour vous. Suivez ces étapes si les instructions suivantes décrivent votre situation :

- Vous disposez de votre propre domaine et souhaitez le configurer pour qu’il fonctionne avec Microsoft 365.

- Vous souhaitez que Microsoft 365 gère vos enregistrements DNS pour vous. Si vous le souhaitez, vous pouvez [gérer vos propres enregistrements DNS](../setup/add-domain.md).

## <a name="add-a-txt-or-mx-record-for-verification"></a>Ajouter un enregistrement TXT ou MX à des fins de vérification

> [!NOTE]
> You will create only one or the other of these records. TXT is the preferred record type, but some DNS hosting providers don't support it, in which case you can create an MX record instead.

Before you use your domain with Microsoft 365, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft 365 that you own the domain.

> [!NOTE]
> This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.

### <a name="find-the-area-on-your-dns-hosting-providers-website-where-you-can-create-a-new-record"></a>Recherchez la zone sur le site web de votre fournisseur d’hébergement DNS dans laquelle vous pouvez créer un enregistrement

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
|TXT|Effectuez l'une des opérations suivantes : Tapez **@**, laissez le champ vide ou entrez le nom de votre domaine.  <p> **Remarque** : Les différents hôtes DNS ont des exigences différentes pour ce champ.|MS=ms *XXXXXXXX* <p> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Microsoft 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|Définissez cette valeur sur **1 heure** ou sur l'équivalent en minutes ( **60** ), en secondes ( **3600** ), etc.|
|||||

**Si vous créez un enregistrement MX, utilisez les valeurs suivantes :**

<br>

****

|Type d’enregistrement|Alias ou nom d’hôte|Valeur|Priorité|Durée de vie|
|---|---|---|---|---|
|MX|Entrez soit **@**, soit votre nom de domaine. |MS=ms *XXXXXXXX* **Remarque :** Il s’agit d’un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Microsoft 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)|Pour **Priorité**, afin d’éviter les conflits avec l’enregistrement MX utilisé pour le flux de courrier électronique, utilisez une priorité plus basse que la priorité des enregistrements MX existants. Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml).|Définissez cette valeur sur **1 heure** ou sur l'équivalent en minutes ( **60** ), en secondes ( **3600** ), etc.|
||||||

### <a name="save-the-record"></a>Enregistrer l’enregistrement

L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Microsoft 365 et demandez à Microsoft 365 de rechercher l’enregistrement.

Lorsque Microsoft 365 trouve l’enregistrement TXT approprié, votre domaine est vérifié.

1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez.

3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.

4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.

> [!NOTE]
> Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).

## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

Lorsque vous arrivez à la dernière étape de l’Assistant Configuration des domaines dans Microsoft 365, il vous reste une tâche. Pour configurer votre domaine avec les services Microsoft 365, comme la messagerie, vous modifiez les enregistrements de serveur de noms (ou NS) de votre domaine auprès de votre bureau d’enregistrement de domaines pour qu’ils pointent vers les serveurs de noms principaux et secondaires Microsoft 365. Ensuite, étant donné que Microsoft 365 héberge votre DNS, les enregistrements DNS requis pour vos services sont configurés automatiquement pour vous. Vous pouvez mettre à jour les enregistrements de serveur de noms vous-même en suivant les étapes fournies éventuellement par votre bureau d'enregistrement de domaines dans l'aide disponible sur son site web. Si vous n'êtes pas familiarisé avec DNS, contactez le support du bureau d'enregistrement de domaines.

::: moniker range="o365-worldwide"

Pour changer vous-même les serveurs de noms de votre domaine sur le site web de votre bureau d'enregistrement de domaines, procédez comme suit :

1. Recherchez la zone sur le site web du bureau d’enregistrement de domaines dans laquelle vous pouvez modifier les serveurs de noms de votre domaine ou une zone dans laquelle vous pouvez utiliser des serveurs de noms personnalisés.

2. Créez des enregistrements de serveur de noms ou modifiez les enregistrements de serveur de noms existants pour qu’ils correspondent aux valeurs suivantes :

    - First nameserver : ns1.bdm.microsoftonline.com
    - Deuxième serveur de noms : ns2.bdm.microsoftonline.com
    - Troisième serveur de noms : ns3.bdm.microsoftonline.com
    - Quatrième serveur de noms : ns4.bdm.microsoftonline.com

   > [!TIP]
   > Il est préférable d’ajouter les quatre enregistrements, mais si votre bureau d’enregistrement ne prend en charge que deux, ajoutez **ns1.bdm.microsoftonline.com** et **ns2.bdm.microsoftonline.com**.

3. Enregistrez vos modifications.

> [!CAUTION]
> Lorsque vous modifiez les enregistrements NS de votre domaine pour qu’ils pointent vers les serveurs de noms Microsoft 365, tous les services actuellement associés à votre domaine sont affectés. Si vous avez ignoré des étapes de l’Assistant, telles que l’ajout d’adresses e-mail, ou si vous utilisez votre domaine pour des blogs, des paniers d’achat ou d’autres services, des étapes supplémentaires sont nécessaires. Dans le cas contraire, cette modification peut entraîner un temps d’arrêt du service, par exemple un manque d’accès à la messagerie ou l’inaccessible de votre site web actuel.

::: moniker-end

::: moniker range="o365-21vianet"

1. Identifiez la zone sur le site web du bureau d'enregistrement de domaines dans laquelle vous pouvez modifier les serveurs de noms pour votre domaine.

2. Créez deux enregistrements de serveur de noms, ou modifiez les enregistrements existants pour qu'ils correspondent aux valeurs suivantes :

   - First nameserver : ns1.dns.partner.microsoftonline.cn
   - Deuxième serveur de noms : ns2.dns.partner.microsoftonline.cn

   > [!TIP]
   > Vous devez utiliser au moins deux enregistrements de serveur de noms. Si d’autres serveurs de noms sont répertoriés, vous pouvez les supprimer ou les modifier en **ns3.dns.partner.microsoftonline.cn** et **ns4.dns.partner.microsoftonline.cn**.

3. Enregistrez vos modifications.

> [!CAUTION]
> Lorsque vous modifiez les enregistrements NS de votre domaine pour qu’ils pointent vers le Office 365 géré par les serveurs de noms 21Vianet, tous les services actuellement associés à votre domaine sont affectés. Si vous avez ignoré des étapes de l’Assistant, telles que l’ajout d’adresses e-mail, ou si vous utilisez votre domaine pour des blogs, des paniers d’achat ou d’autres services, des étapes supplémentaires sont nécessaires. Dans le cas contraire, cette modification peut entraîner un temps d’arrêt du service, par exemple un manque d’accès à la messagerie ou l’inaccessible de votre site web actuel.

::: moniker-end

Voici, par exemple, quelques étapes supplémentaires qui peuvent être nécessaires pour le courrier et l'hébergement du site web :

- Déplacez toutes les adresses e-mail qui utilisent votre domaine vers Microsoft 365 avant de modifier vos enregistrements NS.

- Vous souhaitez ajouter un domaine actuellement utilisé avec une adresse de site web, comme `https://www.fourthcoffee.com`? Vous pouvez effectuer les étapes ci-dessous pendant que vous ajoutez le domaine pour conserver son site web hébergé là où le site est hébergé afin que les utilisateurs puissent toujours accéder au site web après avoir modifié les enregistrements NS du domaine pour qu’ils pointent vers Microsoft 365.

1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

2. Dans la page **Domaines**, sélectionnez un domaine.

3. Dans la page détails du domaine, sélectionnez l’onglet **Enregistrements DNS** .

4. Sélectionnez **Ajouter un enregistrement**.

5. Dans le volet **Ajouter un enregistrement DNS personnalisé**, dans la liste déroulante **Type**, sélectionnez **A (Adresse).**

6. Dans la zone **Nom d’hôte ou Alias** , tapez **@**.

7. Dans la zone **Adresse IP** , tapez l’adresse IP statique du site web où elle est actuellement hébergée. Par exemple, 172.16.140.1.

   > [!IMPORTANT]
   > Il doit s’agir d’une adresse IP _statique_ pour le site web, et non d’une adresse IP _dynamique_ . Pour vous assurer que vous pouvez obtenir une adresse IP statique pour votre site web public, vérifiez auprès du site qui héberge votre site web.

8. Si vous souhaitez modifier le paramètre de durée de vie de l’enregistrement, sélectionnez une nouvelle durée dans la liste déroulante **TTL** . Sinon, passez à l’étape 9.

9. Sélectionnez **Enregistrer**.

De plus, vous pouvez créer un enregistrement CNAME pour aider les clients à trouver votre site web.

1. Sélectionnez **Ajouter un enregistrement**.
2. Dans le volet **Ajouter un enregistrement DNS personnalisé**, dans la liste déroulante **Type**, sélectionnez **CNAME (Alias).**
3. Dans la zone **Nom d’hôte ou Alias** , tapez **www**.
4. Dans la zone **Points à l’adresse** , tapez le nom de domaine complet (FQDN) de votre site web. Par exemple, **contoso.com**.
5. Si vous souhaitez modifier le paramètre de durée de vie de l’enregistrement, sélectionnez une nouvelle durée dans la liste déroulante **TTL** . Sinon, passez à l’étape 6.
6. Sélectionnez **Enregistrer**.

Une fois que les enregistrements du serveur de noms sont mis à jour pour pointer vers Microsoft, la configuration de votre domaine est terminée. Email est acheminé vers Microsoft, et le trafic vers l’adresse de votre site web continue d’être acheminé vers votre hôte de site web actuel. »

> [!NOTE]
> Your nameserver record updates may take up to several hours to update across the Internet's DNS system. Votre messagerie Microsoft et d’autres services seront alors prêts à fonctionner avec votre domaine.

## <a name="related-content"></a>Contenu associé

[Ajouter des enregistrements DNS pour connecter votre domaine](create-dns-records-at-any-dns-hosting-provider.md) (article)\
[Rechercher et corriger les problèmes, y compris de messagerie, après avoir ajouté votre domaine ou des enregistrements DNS](find-and-fix-issues.md) (article)\
[Gérer des domaines](/admin) (page de lien)
