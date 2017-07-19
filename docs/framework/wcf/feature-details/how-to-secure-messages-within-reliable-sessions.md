---
title: "Comment&#160;: s&#233;curiser des messages au sein de sessions fiables | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# Comment&#160;: s&#233;curiser des messages au sein de sessions fiables
Cette rubrique décrit les étapes requises pour activer la sécurité au niveau du message pour les messages échangés dans une session fiable utilisant l'une des liaisons fournies par le système qui prennent en charge une telle session, mais pas par défaut.Vous pouvez activer une session fiable sécurisée soit de façon impérative en utilisant le code, soit de façon déclarative dans le fichier de configuration.Cette procédure utilise le client et les fichiers de configuration du service pour activer la session fiable sécurisée.  
  
 La procédure inclut les trois tâches clés suivantes :  
  
1.  Spécifiez que le client et le service échangent des messages dans une session fiable.  
  
2.  Requérez la sécurité au niveau du message dans la session fiable.  
  
3.  Spécifiez le type d'informations d'identification que le client doit utiliser pour être authentifié auprès du service.  
  
 Il est important, dans la première tâche, que l'élément de configuration du point de terminaison contienne un attribut `bindingConfiguration` qui référence une configuration de liaison nommée \(dans cet exemple\) "MessageSecurity". L'élément de configuration [\<liaison\>](../../../../docs/framework/misc/binding.md) peut référencer ensuite ce nom pour activer des sessions fiables en affectant à l'attribut `enabled` de l'élément [reliableSession](http://msdn.microsoft.com/fr-fr/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) la valeur `true`.Vous pouvez requérir que les assurances de remise ordonnée soient disponibles dans une session fiable en affectant à l'attribut `ordered` la valeur `true`.  
  
 Pour la copie source de l'exemple sur lequel cette procédure de configuration est basée, consultez [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).  
  
 Les éléments essentiels de la deuxième tâche sont accomplis en affectant à l'attribut `mode` de l'élément \<`security`\> contenu dans l'élément \<`binding`\> du client et du service la valeur `Message`.  
  
 Les éléments essentiels de la troisième tâche sont accomplis en affectant à l'attribut `clientCredentialType` de l'élément \<`message`\> contenu dans l'élément \<`security`\> du client et du service la valeur `Certificate`.  
  
> [!NOTE]
>  Lors de l'utilisation de la sécurité de message avec les sessions fiables, si le client n'est pas authentifié, la messagerie fiable essaie de l'authentifier jusqu'à l'expiration du délai au lieu de lever une exception sur premier échec.  
  
### Pour configurer le service avec une liaison WSHttpBinding afin d'utiliser une session fiable  
  
1.  Cette procédure est décrite dans [Comment : échanger des messages au sein d'une session fiable](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).  
  
### Pour configurer le client avec une liaison WSHttpBinding afin d'utiliser une session fiable  
  
1.  Cette procédure est décrite dans [Comment : échanger des messages au sein d'une session fiable](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).  
  
### Pour définir le mode et la propriété ClientCredentialType dans la configuration  
  
1.  Ajoutez un élément de liaison approprié à l'élément [\<liaisons\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) du fichier de configuration.L'exemple suivant ajoute un élément [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
2.  Ajoutez un élément \<`binding`\>, puis affectez à son attribut `name` une valeur appropriée.  
  
3.  Ajoutez un élément `<security>`, puis affectez à l'attribut `mode` la valeur `Message`.  
  
     L'exemple suivant affecte au mode la valeur `Message`, puis affecte à l'attribut `clientCredentialType` de l'élément \<`message`\> la valeur `Certificate`.  
  
    ```  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" />  
           <message clientCredentialType = " Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```