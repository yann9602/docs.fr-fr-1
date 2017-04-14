---
title: "Programmation de protocoles enfichables | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "téléchargement de ressources Internet, protocoles enfichables"
  - "WebRequest (classe), protocoles enfichables"
  - "réponse à une requête Internet, protocoles enfichables"
  - "WebResponse (classe), protocoles enfichables"
  - "envoi de données, protocoles enfichables"
  - "ressources réseau, protocoles enfichables"
  - "Internet, protocoles enfichables"
  - "programmation de protocoles enfichables"
  - "protocoles enfichables, programmation"
  - "requête de données depuis Internet, protocoles enfichables"
  - "réception de données, protocoles enfichables"
  - "enfichables, protocoles"
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# Programmation de protocoles enfichables
<xref:System.Net.WebRequest> les classes et abstraits d' <xref:System.Net.WebResponse> fournissent la base des protocoles enfichables.  En dérivant les classes spécifiques au protocole d' <xref:System.Net.WebRequest> et d' <xref:System.Net.WebResponse>, une application peut demander des données à une ressource Internet et lire la réponse sans spécifier le protocole utilisé.  
  
 Avant de pouvoir créer <xref:System.Net.WebRequest>spécifique au fournisseur, vous devez enregistrer la méthode de création.  Utilisez la méthode statique d' <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> d' <xref:System.Net.WebRequest> pour stocker un descendant d' <xref:System.Net.WebRequest> pour traiter un ensemble de requêtes à un schéma spécifique Internet, une modèle et à un serveur, ou à un modèle, un serveur, et un chemin d'accès.  
  
 Dans la plupart des cas vous pourrez envoyer et recevoir des données à l'aide de les méthodes et les propriétés d' <xref:System.Net.WebRequest> classe.  Toutefois, si vous devez accéder aux propriétés spécifiques au protocole, vous pouvez convertir le rôle d' <xref:System.Net.WebRequest> à une instance classe dérivée spécifique.  
  
 Pour tirer parti des protocoles enfichables, les descendants d' <xref:System.Net.WebRequest> doivent fournir une transaction par défaut de demande\-et\- réponse qui ne requiert pas de propriétés spécifiques au protocole d'être définies.  Par exemple, la classe d' <xref:System.Net.HttpWebRequest> , qui implémente la classe d' <xref:System.Net.WebRequest> pour HTTP, fournit une demande d' `GET` par défaut et retourne <xref:System.Net.HttpWebResponse> qui contient le flux de données retourné par le serveur Web.  
  
## Voir aussi  
 [dérivation de WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)   
 [Dérivation à partir de WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)   
 [Programmation réseau dans le .NET Framework](../../../docs/framework/network-programming/index.md)   
 [Comment : convertir une classe WebRequest pour accéder à des propriétés spécifiques au protocole](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)