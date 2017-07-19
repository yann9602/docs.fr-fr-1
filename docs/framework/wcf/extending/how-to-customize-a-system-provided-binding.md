---
title: "Comment&#160;: personnaliser une liaison fournie par le syst&#232;me | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Comment&#160;: personnaliser une liaison fournie par le syst&#232;me
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] inclut plusieurs liaisons fournies par le système qui vous permettent de configurer quelques\-unes des propriétés des éléments de liaison sous\-jacents, mais pas toutes les propriétés.  Cette rubrique explique comment attribuer des propriétés aux éléments de liaison afin de créer une liaison personnalisée.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la façon de créer et de configurer directement des éléments de liaison sans utiliser les liaisons fournies par le système, consultez [Liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la création et l'extension des liaisons personnalisées, consultez [Extension de liaisons](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
 Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], toutes les liaisons sont composées d'*éléments de liaison*.  Chaque élément de liaison dérive de la classe <xref:System.ServiceModel.Channels.BindingElement>.  Les liaisons fournies par le système telles que <xref:System.ServiceModel.BasicHttpBinding> créent et configurent leurs propres éléments de liaison.  Cette rubrique vous indique comment accéder aux propriétés de ces éléments de liaison qui ne sont pas exposés directement sur la liaison et comment les modifier ; il s'agit, notamment, de la classe <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Les éléments de liaison individuels sont inclus dans une collection représentée par la classe <xref:System.ServiceModel.Channels.BindingElementCollection> et sont ajoutés dans l'ordre suivant : Transaction Flow, Reliable Session, Security, Composite Duplex, One\-way, Stream Security, Message Encoding et Transport.  Notez que les éléments de liaison répertoriés ne sont pas tous requis dans chaque liaison.  Les éléments de liaison définis par l'utilisateur peuvent également apparaître dans cette collection et doivent figurer dans le même ordre que précédemment.  Par exemple, un transport défini par l'utilisateur doit être le dernier élément de la collection d'éléments de liaison.  
  
 La classe <xref:System.ServiceModel.BasicHttpBinding> contient trois éléments de liaison :  
  
1.  Un élément de liaison de sécurité facultatif, soit la classe <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> utilisée avec le transport HTTP \(sécurité de niveau transport\), soit la classe <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> utilisée lorsque la couche transport fournit la sécurité, auquel cas le transport HTTPS est utilisé.  
  
2.  Un élément de liaison d'encodeur de message requis, <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ou <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.  
  
3.  Un élément de liaison de transport requis, <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, ou <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
 Dans cet exemple nous allons créer une instance de la liaison, générer une *liaison personnalisée* à partir de là, examiner les éléments de liaison dans la liaison personnalisée et, lorsque nous aurons trouvé l'élément de liaison HTTP, affecter à sa propriété `KeepAliveEnabled` la valeur `false`.  La propriété `KeepAliveEnabled` n'est pas exposée directement sur `BasicHttpBinding`, nous devons donc créer une liaison personnalisée pour naviguer jusqu'à l'élément de liaison et définir cette propriété.  
  
### Pour modifier une liaison fournie par le système  
  
1.  Créez une instance de la classe <xref:System.ServiceModel.BasicHttpBinding> et affectez à son mode de sécurité la valeur de sécurité au niveau du message.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  Créez une liaison personnalisée à partir de la liaison et ensuite une classe <xref:System.ServiceModel.Channels.BindingElementCollection> à partir de l'une des propriétés de la liaison personnalisée.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  Parcourez la classe <xref:System.ServiceModel.Channels.BindingElementCollection> et lorsque vous trouverez la classe <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, affectez à sa propriété <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> la valeur `false`.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>   
 <xref:System.ServiceModel.BasicHttpBinding>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md)