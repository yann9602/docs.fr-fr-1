---
title: "Contrats de routage | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
caps.latest.revision: 7
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 7
---
# Contrats de routage
Les contrats de routage définissent les modèles de messages que le service de routage peut traiter.Chaque contrat est sans type et permet au service de recevoir un message sans connaissance du schéma ni de l'action du message.Cela permet au service de routage de router des messages de manière générique, sans configuration supplémentaire pour les caractéristiques sous\-jacentes des messages routés.  
  
## Contrats de routage  
 Puisque le service de routage accepte un objet Message WCF générique, le plus important lorsque vous sélectionnez un contrat est de prendre en compte la forme du canal utilisé lors de la communication avec les clients et les services.Lors du traitement des messages, le service de routage utilise des pompes de messages symétriques, en conséquence, la forme du contrat entrant doit généralement correspondre à la forme du contrat sortant.Toutefois dans certains cas, le répartiteur du modèle de service peut modifier les formes : par exemple, le répartiteur convertit un canal duplex en canal demande\-réponse ou supprime la prise en charge de session d'un canal si elle n'est pas indispensable et n'est pas utilisée \(c'est\-à\-dire, avec **SessionMode.Allowed**, en convertissant un **IInputSessionChannel** en **IInputChannel**\).  
  
 Pour prendre en charge ces pompes de messages, le service de routage fournit des contrats dans l'espace de noms <xref:System.ServiceModel.Routing>, qui doivent être utilisés lors de la définition des points de terminaison de service utilisés par le service de routage.Ces contrats sont sans type, ce qui autorise la réception de tout type ou action de message et permet au service de routage de gérer des messages sans connaître le schéma de message spécifique.Pour plus d'informations sur les contrats utilisés par le service de routage, consultez [Routing Contracts](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Les contrats fournis par le service de routage se trouvent dans l'espace de noms <xref:System.ServiceModel.Routing> et sont décrits dans le tableau suivant.  
  
|Contrat|Forme|Forme de canal|  
|-------------|-----------|--------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode \= SessionMode.Allowed<br /><br /> AsyncPattern \= true<br /><br /> IsOneWay \= true|IInputChannel \-\> IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode \= SessionMode.Required<br /><br /> AsyncPattern \= true<br /><br /> IsOneWay \= true|IInputSessionChannel \-\> IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode \= SessionMode.Allowed<br /><br /> AsyncPattern \= true|IReplyChannel \-\> IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode\=SessionMode.Required<br /><br /> CallbackContract\=typeof\(ISimplexSession\)<br /><br /> AsyncPattern \= true<br /><br /> IsOneWay \= true<br /><br /> TransactionFlow\(TransactionFlowOption.Allowed\)|IDuplexSessionChannel \-\> IDuplexSessionChannel|  
  
## Voir aussi  
 [Routing Service](http://msdn.microsoft.com/fr-fr/5ac8718c-bcef-456f-bfd5-1e60a30d6eaa)   
 [Introduction au routage](../../../../docs/framework/wcf/feature-details/routing-introduction.md)