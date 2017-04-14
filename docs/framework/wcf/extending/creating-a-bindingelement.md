---
title: "Cr&#233;ation d&#39;un &#233;l&#233;ment de liaison | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Cr&#233;ation d&#39;un &#233;l&#233;ment de liaison
Les liaisons et les éléments de liaison \(qui étendent respectivement les objets <xref:System.ServiceModel.Channels.Binding?displayProperty=fullName> et <xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName>\) correspondent à l'emplacement où le modèle d'application [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est associé aux fabrications de canaux ainsi qu'aux écouteurs de canal.Sans liaisons, l'utilisation des canaux personnalisés nécessite une programmation de niveau canal comme expliqué dans [Programmation de service au niveau du canal](../../../../docs/framework/wcf/extending/service-channel-level-programming.md) et [Programmation au niveau du canal client](../../../../docs/framework/wcf/extending/client-channel-level-programming.md).Cette rubrique aborde les spécifications minimales vous permettant d'utiliser vos canaux dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], de développer un <xref:System.ServiceModel.Channels.BindingElement> pour ceux\-ci et de les utiliser à partir d'applications, comme expliqué à l'étape 4 de [Développement de canaux](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## Vue d'ensemble  
 Créer un <xref:System.ServiceModel.Channels.BindingElement> pour votre canal permet aux développeurs de l'utiliser dans une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Les objets <xref:System.ServiceModel.Channels.BindingElement> peuvent être utilisés dans la classe <xref:System.ServiceModel.ServiceHost?displayProperty=fullName> pour connecter une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à votre canal sans avoir les informations de type exactes de votre canal.  
  
 Une fois l'élément <xref:System.ServiceModel.Channels.BindingElement> créé, vous pouvez activer des fonctionnalités supplémentaires selon vos spécifications en vous conformant aux autres étapes figurant dans [Développement de canaux](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## Ajout d'un élément de liaison  
 Pour implémenter un élément <xref:System.ServiceModel.Channels.BindingElement>personnalisé, écrivez une classe qui hérite de <xref:System.ServiceModel.Channels.BindingElement>.Par exemple, si vous avez développé un canal `ChunkingChannel` capable de fragmenter de grands messages en plusieurs segments, puis de les recomposer en fin de traitement, vous pouvez utiliser ce canal sur n'importe quelle liaison en implémentant un élément <xref:System.ServiceModel.Channels.BindingElement> et en configurant la liaison de sorte à ce qu'elle puisse utiliser ce dernier.Un canal `ChunkingChannel` est utilisé à titre d'exemple dans cette rubrique afin d'illustrer les spécifications requises à l'implémentation d'un élément de liaison.  
  
 L'élément `ChunkingBindingElement` est chargé de créer la fabrication `ChunkingChannelFactory` et l'écouteur `ChunkingChannelListener`.Cet élément se substitue aux implémentations <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> et <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> et s'assure que le paramètre de type correspond à <xref:System.ServiceModel.Channels.IDuplexSessionChannel> \(il s'agit de la seule forme de canal prise en charge par notre exemple de canal `ChunkingChannel`\) et que les autres éléments de liaison dans la liaison prennent effectivement en charge cette forme de canal.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> vérifie au préalable que la forme de canal demandée peut être construite, puis récupère une liste d'actions de message à fragmenter.Cette méthode crée ensuite une fabrication `ChunkingChannelFactory` en lui passant la fabrication de canal interne.Remarque : si vous créez un élément de liaison de transport, cet élément est le dernier dans la pile de liaison. Vous devez, par conséquent, créer un écouteur de canal ou une fabrication de canal.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> utilise une implémentation similaire pour créer `ChunkingChannelListener` et lui passer l'écouteur de canal interne.  
  
 Dans le cadre d'un canal de transport, [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md), par exemple, effectue la substitution suivante.  
  
 Dans notre exemple, l'élément de liaison est `UdpTransportBindingElement`, lequel dérive de <xref:System.ServiceModel.Channels.TransportBindingElement>.Dans le code ci\-dessous se rapportant à notre exemple, les méthodes suivantes sont substituées pour générer les fabrications associées au canal.  
  
```  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
            return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
            return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Notre exemple contient également des membres permettant de cloner l'élément `BindingElement` et de retourner le schéma \(soap.udp\).  
  
#### Protocole d'éléments de liaison  
 Les nouveaux éléments de liaison peuvent remplacer ou augmenter tout élément de liaison inclus en ajoutant de nouveaux transports, encodages ou protocoles de niveau supérieur.Pour créer un nouvel élément de liaison de protocole, commencez par étendre la classe <xref:System.ServiceModel.Channels.BindingElement>.Vous devez ensuite implémenter au minimum la méthode <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=fullName> ainsi que  `ChannelProtectionRequirements` en utilisant la méthode <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=fullName>.Cette opération retourne <xref:System.ServiceModel.Security.ChannelProtectionRequirements> pour l'élément de liaison défini.Pour plus d'informations, consultez <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> doit retourner une nouvelle copie de cet élément de liaison.Dans le cadre de nos meilleures pratiques, nous vous recommandons d'implémenter, en tant que créateur de cet élément de liaison, la méthode <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> à l'aide d'un constructeur de copie qui appelle le constructeur de copie de base, puis clone tous les champs supplémentaires figurant dans cette classe.  
  
#### Éléments de liaison de transport  
 Pour créer un nouvel élément de liaison de transport, étendez l'interface <xref:System.ServiceModel.Channels.TransportBindingElement>.Vous devez ensuite implémenter au minimum la méthode <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> et la propriété <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=fullName>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> doit retourner une nouvelle copie de cet élément de liaison.Dans le cadre de nos meilleures pratiques, nous vous recommandons d'implémenter, en tant que créateur de cet élément de liaison, la méthode de clonage à l'aide d'un constructeur de copie qui appelle le constructeur de copie de base, puis clone tous les champs supplémentaires figurant dans cette classe.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> : la propriété <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> retourne le modèle URI correspondant au protocole de transport représenté par l'élément de liaison.Par exemple, <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=fullName> et <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=fullName> retournent « http » et « net.tcp » à partir de leurs propriétés <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> respectives.  
  
#### Éléments de liaison d'encodage  
 Pour créer un nouvel élément de liaison d'encodage, commencez par étendre la classe <xref:System.ServiceModel.Channels.BindingElement> et implémenter la classe <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=fullName>.Vous devez ensuite implémenter au minimum les méthodes <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=fullName> ainsi que la propriété <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=fullName>.  
  
-   <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>.Retourne une nouvelle copie de cet élément de liaison.Dans le cadre de nos meilleures pratiques, nous vous recommandons d'implémenter, en tant que créateur de cet élément de liaison, la méthode <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> à l'aide d'un constructeur de copie qui appelle le constructeur de copie de base, puis clone tous les champs supplémentaires figurant dans cette classe.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>.Retourne une fabrication <xref:System.ServiceModel.Channels.MessageEncoderFactory> qui fournit un handle à la classe effective, laquelle implémente votre nouvel encodeur et doit étendre <xref:System.ServiceModel.Channels.MessageEncoder>.Pour plus d'informations, consultez <xref:System.ServiceModel.Channels.MessageEncoderFactory> et <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>.Retourne la version <xref:System.ServiceModel.Channels.MessageVersion> utilisée dans cet encodage, laquelle correspond aux versions de SOAP et WS\-Addressing utilisées.  
  
 Pour une liste exhaustive des méthodes et propriétés optionnelles compatibles avec les éléments de liaison d'encodage définis par l'utilisateur, consultez <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Pour plus d'informations sur la création d'un élément de liaison, consultez [Création de liaisons définies par l'utilisateur](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
 Une fois l'élément de liaison de votre canal créé, consultez à nouveau la rubrique [Développement de canaux](../../../../docs/framework/wcf/extending/developing-channels.md) si vous souhaitez ajouter une prise en charge du fichier de configuration ou une prise en charge de la publication des métadonnées à votre élément de liaison ou construire une liaison définie par l'utilisateur utilisant votre élément de liaison.  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.BindingElement>   
 [Développement de canaux](../../../../docs/framework/wcf/extending/developing-channels.md)   
 [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)