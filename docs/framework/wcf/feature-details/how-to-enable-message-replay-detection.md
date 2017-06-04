---
title: "Comment&#160;: activer la d&#233;tection de relecture des messages | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "détection de relecture (WCF)"
  - "sécurité WCF"
  - "WCF, liaisons personnalisées"
  - "WCF, sécurité"
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Comment&#160;: activer la d&#233;tection de relecture des messages
Une attaque par relecture se produit lorsqu'un intrus copie un flux de messages entre deux correspondants et relit le flux à l'un ou plusieurs des correspondants.Sauf atténuation, les ordinateurs sujets à l'attaque traiteront le flux comme messages légitimes, ce qui a des conséquences néfastes telles que des ordres redondants d'un élément.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la détection de relecture des messages, consultez [Détection de relecture des messages](http://go.microsoft.com/fwlink/?LinkId=88536) \(page éventuellement en anglais\).  
  
 La procédure suivante illustre différentes propriétés que vous pouvez utiliser pour contrôler la détection de relecture à l'aide de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
### Pour contrôler la détection de relecture sur le client à l'aide du code  
  
1.  Créez un <xref:System.ServiceModel.Channels.SecurityBindingElement> à utiliser dans un <xref:System.ServiceModel.Channels.CustomBinding>.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).L'exemple suivant utilise un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> créé avec le <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> de la classe <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2.  Utilisez la propriété <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> pour retourner une référence à la classe <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> et définir les propriétés suivantes, selon le cas :  
  
    1.  `DetectReplay`.Valeur booléenne.Elle détermine si le client doit détecter les relectures à partir du serveur.La valeur par défaut est `true`.  
  
    2.  `MaxClockSkew`.Valeur <xref:System.TimeSpan>.Détermine l'inclinaison d'horloge que peut tolérer le mécanisme de relecture entre le client et le serveur.Le mécanisme de sécurité examine l'horodatage envoyé et détermine s'il a été envoyé il y a trop longtemps.La valeur par défaut est 5 minutes.  
  
    3.  `ReplayWindow`.Valeur `TimeSpan`.Détermine pendant combien de temps un message peut vivre sur le réseau après que le serveur l'a envoyé \(par le biais d'intermédiaires\) avant d'atteindre le client.Le client effectue le suivi des signatures des messages envoyés dans le `ReplayWindow` le plus récent pour les besoins de la détection de relecture.  
  
    4.  `ReplayCacheSize`.Valeur entière.Le client stocke les signatures du message dans un cache.Ce paramètre spécifie combien de signatures le cache peut stocker.Si le nombre de messages envoyés dans la dernière fenêtre de relecture atteint la limite de cache, les nouveaux messages sont rejetés jusqu'à ce que les signatures mises en cache les plus anciennes atteignent la limite de temps.La valeur par défaut est 500000.  
  
### Pour contrôler la détection de relecture sur le service à l'aide du code  
  
1.  Créez un <xref:System.ServiceModel.Channels.SecurityBindingElement> à utiliser dans un <xref:System.ServiceModel.Channels.CustomBinding>.  
  
2.  Utilisez la propriété <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> pour retourner une référence à la classe <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> et définissez les propriétés comme décrit précédemment.  
  
### Pour contrôler la détection de relecture dans la configuration pour le client ou le service  
  
1.  Créez un [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Créez un élément `<security>`.  
  
3.  Créez un [\<localClientSettings\>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) ou un [\<localServiceSettings\>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4.  Définissez les valeurs d'attributs suivantes, le cas échéant : `detectReplays`, `maxClockSkew`, `replayWindow` et `replayCacheSize`.L'exemple suivant définit les attributs d'un élément `<localServiceSettings>` et d'un élément `<localClientSettings>` :  
  
    ```  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## Exemple  
 L'exemple suivant crée un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à l'aide de la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> et définit les propriétés de relecture de la liaison.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## Étendue de relecture : sécurité de message uniquement  
 Notez que les procédures suivantes s'appliquent uniquement au mode de sécurité Message.Pour les modes Transport et Transport avec informations d'identification de message, les mécanismes de transport détectent les relectures.  
  
## Remarques relatives aux conversations sécurisées  
 Pour les liaisons qui activent les conversations sécurisées, vous pouvez ajuster ces paramètres à la fois pour le canal d'application et pour la liaison du démarrage de conversation sécurisée.Par exemple, vous pouvez désactiver les relectures pour le canal d'application mais les activer pour le canal de démarrage qui établit la conversation sécurisée.  
  
 Si vous n'utilisez pas de sessions de conversation sécurisée, la détection des relectures n'est pas garantie dans les scénarios de batterie de serveurs et lorsque le processus est recyclé.Cela s'applique aux liaisons fournies par le système suivantes :  
  
-   <xref:System.ServiceModel.BasicHttpBinding>.  
  
-   Objet <xref:System.ServiceModel.WSHttpBinding> avec la propriété <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> qui a la valeur `false`.  
  
## Compilation du code  
  
-   Les espaces de noms suivants sont requis pour compiler le code :  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>   
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>   
 [Conversations sécurisées et sessions sécurisées](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)   
 [\<localClientSettings\>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)   
 [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)