---
title: "Comment : sécuriser des messages au sein de sessions fiables"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3f27b1a4de2019660e0facb081300a79eae65b99
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Comment : sécuriser des messages au sein de sessions fiables

Cette rubrique décrit les étapes requises pour activer la sécurité au niveau du message pour les messages échangés dans une session fiable utilisant l’une des liaisons fournies par le système qui prennent en charge une telle session, mais pas par défaut. Activer une session sécurisée et fiable, soit impérativement en utilisant du code ou de façon déclarative dans le fichier de configuration. Cette procédure utilise le client et les fichiers de configuration du service pour activer la session fiable sécurisée.

La procédure inclut les trois tâches clés suivantes :

1. Spécifiez que le client et le service échangent des messages dans une session fiable.

1. Requérez la sécurité au niveau du message dans la session fiable.

1. Spécifiez le type d'informations d'identification que le client doit utiliser pour être authentifié auprès du service.

Il est important dans la première tâche que l’élément de configuration de point de terminaison contienne un `bindingConfiguration` attribut qui fait référence à une configuration de liaison nommée (dans cet exemple) `MessageSecurity`. Le [  **\<liaison >** ](../../../../docs/framework/misc/binding.md) élément de configuration puis référence ce nom pour activer les sessions fiables en définissant le `enabled` attribut de la [  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) élément `true`. Vous pouvez requérir que les assurances de remise ordonnée soient disponibles dans une session fiable en affectant à l'attribut `ordered` la valeur `true`.

Pour la copie de la source de l’exemple sur lequel repose cette procédure de configuration, consultez le [Session fiable de WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

Les éléments essentiels de la seconde tâche sont effectuées en définissant le `mode` attribut de la  **\<sécurité >** élément contenu dans le  **\<liaison >** élément du client et du service à `Message`.

Les éléments essentiels de la troisième tâche sont effectuées en définissant le `clientCredentialType` attribut de la  **\<message >** élément contenu dans le  **\<sécurité >** élément du client et du service à `Certificate`.

> [!NOTE]
> Lorsque vous utilisez la sécurité des messages avec les sessions fiables, une messagerie fiable tente d’authentifier un client non authentifié jusqu'à ce qu’un délai d’attente se produit au lieu de lever une exception sur premier échec.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurer le service avec une liaison WSHttpBinding afin d’utiliser une session fiable

Cette procédure est décrite dans [Comment : échange de Messages au sein d’une Session fiable](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurer le client avec une liaison WSHttpBinding afin d’utiliser une session fiable

Cette procédure est décrite dans [Comment : échange de Messages au sein d’une Session fiable](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Définir le mode et le ClientCredentialType dans la configuration

1. Ajouter un élément de liaison approprié à la [  **\<liaisons >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) élément du fichier de configuration. L’exemple suivant ajoute un [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) élément.

1. Ajouter un  **\<liaison >** et définissez son `name` attribut une valeur appropriée. L’exemple utilise le nom `MessageSecurity`.

1. Ajouter un  **\<sécurité >** et affectez le `mode` attribut `Message`.

1. Dans le  **\<sécurité >** élément, ajouter un  **\<message >** et affectez le `clientCredentialType` attribut `Certificate`.

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
