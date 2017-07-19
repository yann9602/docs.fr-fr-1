---
title: "Pratiques recommand&#233;es pour les classes System.Net | Microsoft Docs"
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
  - "envoi de données, pratiques recommandées"
  - "requête de données sur Internet, pratiques recommandées"
  - "WebRequest (classe), pratiques recommandées"
  - "requêtes de données, pratiques recommandées"
  - "WebResponse (classe), pratiques recommandées"
  - "pratiques recommandées, requêtes de données"
  - "réception de données, pratiques recommandées"
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# Pratiques recommand&#233;es pour les classes System.Net
Les recommandations suivantes vous aideront à utiliser les classes contenues dans <xref:System.Net> à leur mieux avantage :  
  
-   Utilisez <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> autant que possible au lieu du type cast aux classes descendantes.  Les applications qui utilisent **WebRequest** et **WebResponse** peuvent tirer parti de nouveaux protocoles Internet sans avoir besoin de modifications du code étendues.  
  
-   En écrivant les applications ASP.NET qui s'exécutent sur un serveur utilisant les classes de **System.Net** , il est souvent préférable, d'un point de performances, pour utiliser les méthodes asynchrones pour <xref:System.Net.WebRequest.GetResponse%2A> et <xref:System.Net.WebResponse.GetResponseStream%2A>.  
  
-   Le nombre de connexions ouvertes vers une ressource Internet peut avoir un impact significatif sur les performances réseau et le débit.  **System.Net** utilise deux connexions par application par hôte par défaut.  L'affectation de la valeur d' <xref:System.Net.ServicePoint.ConnectionLimit%2A> dans <xref:System.Net.ServicePoint> pour votre application peut augmenter ce nombre pour un hôte spécifique.  L'affectation de la valeur d' <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=fullName> peut augmenter cette valeur par défaut pour tous les hôtes.  
  
-   Lorsque vous écrivez des protocoles de socket\- niveau, essayez d'utiliser [TCPClient](frlrfsystemnetsocketstcpclientclasstopic) ou [UDPClient](frlrfsystemnetsocketsudpclientclasstopic) autant que possible au lieu d'écrire directement à <xref:System.Net.Sockets.Socket>.  Ces deux classes clientes encapsulent la création des sockets TCP et UDP sans qu'il soit nécessaire de gérer les détails de la connexion.  
  
-   En accédant aux sites qui nécessitent des informations d'identification, utilisez la classe d' <xref:System.Net.CredentialCache> pour créer un cache des informations d'identification plutôt qu'en fournissant à chaque demande.  La classe de **CredentialCache** recherche le cache pour rechercher les informations d'identification appropriées pour présenter à une requête, d'accélération vous de la responsabilité et de présenter les informations d'identification en fonction de l'URL.  
  
## Voir aussi  
 [Programmation réseau dans le .NET Framework](../../../docs/framework/network-programming/index.md)