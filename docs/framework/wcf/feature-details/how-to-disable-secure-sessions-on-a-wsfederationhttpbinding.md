---
title: "Comment&#160;: d&#233;sactiver des sessions s&#233;curis&#233;es sur une classe WSFederationHttpBinding | Microsoft Docs"
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
  - "fédération"
  - "WCF, fédération"
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
caps.latest.revision: 16
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 16
---
# Comment&#160;: d&#233;sactiver des sessions s&#233;curis&#233;es sur une classe WSFederationHttpBinding
Certains services peuvent requérir des informations d'identification fédérées mais ne prennent pas en charge les sessions sécurisées.Dans ce cas, vous devez désactiver la fonctionnalité de session sécurisée.Contrairement à <xref:System.ServiceModel.WsHttpBinding>, la classe <xref:System.ServiceModel.WSFederationHttpBinding> n'offre aucun moyen de désactiver les sessions sécurisées lors de la communication avec un service.À la place, vous devez créer une liaison personnalisée qui remplace les paramètres de session sécurisée par un démarrage.  
  
 Cette rubrique montre comment modifier les éléments de liaison contenus dans une <xref:System.ServiceModel.WSFederationHttpBinding> pour créer une liaison personnalisée.Le résultat est identique à <xref:System.ServiceModel.WSFederationHttpBinding> mais n'utilise pas de sessions sécurisées.  
  
### Pour créer une liaison fédérée personnalisée sans session sécurisée  
  
1.  Créez une instance de la classe <xref:System.ServiceModel.WSFederationHttpBinding> soit impérativement dans du code, soit en la chargeant à partir du fichier de configuration.  
  
2.  Clonez la <xref:System.ServiceModel.WSFederationHttpBinding> dans une <xref:System.ServiceModel.Channels.CustomBinding>.  
  
3.  Recherchez <xref:System.ServiceModel.Channels.SecurityBindingElement> dans <xref:System.ServiceModel.Channels.CustomBinding>.  
  
4.  Recherchez <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> dans <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
5.  Remplacez le <xref:System.ServiceModel.Channels.SecurityBindingElement> d'origine par l'élément de liaison de sécurité de démarrage des <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.  
  
## Exemple  
 L'exemple suivant permet de créer une liaison fédérée personnalisée sans session sécurisée.  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## Compilation du code  
  
-   Pour compiler l'exemple de code, créez un projet qui référence l'assembly System.ServiceModel.dll.  
  
## Voir aussi  
 [Liaisons et sécurité](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)