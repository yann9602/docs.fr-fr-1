---
title: "HTTP | Microsoft Docs"
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
  - "protocoles, HTTP"
  - "envoi de données, HTTP"
  - "HttpWebResponse (classe), envoi et réception de données"
  - "HTTP"
  - "réception de données, HTTP"
  - "protocoles d’application, HTTP"
  - "Internet, HTTP"
  - "ressources réseau, HTTP"
  - "HTTP, à propos de HTTP"
  - "HttpWebRequest (classe), envoi et réception de données"
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# HTTP
Le.NET Framework fournit une prise en charge complète du protocole HTTP, qui constitue la majorité du trafic Internet, avec les classes d'<xref:System.Net.HttpWebRequest> et d' <xref:System.Net.HttpWebResponse> .  Ces classes dérivées, d' <xref:System.Net.WebRequest> et d' <xref:System.Net.WebResponse>, sont retournées par défaut chaque fois que la méthode statique <xref:System.Net.WebRequest.Create%2A?displayProperty=fullName> rencontre un URI commençant par « http » ou « https ».  Dans la plupart des cas, les classes de **WebRequest** et de **WebResponse** fournissent tout ce qui est nécessaire pour que l'application, mais si vous avez besoin d'accéder aux fonctionnalités de HTTP spécifiques exposées comme propriétés, vous pouvez convertir le rôle de ces classes à **HttpWebRequest** ou à **HttpWebResponse**.  
  
 **HttpWebRequest** et **HttpWebResponse** encapsulent une transaction standard de demande\-et\- réponse HTTP et fournissent l'accès aux en\-têtes HTTP communes.  Ces classes prennent également en charge la plupart HTTP 1,1 fonctionnalités, y compris le traitement pipeline, l'émission et des données de recevoir en segments, l'authentification, preauthentication, chiffrement, la prise en charge de proxy, validation de certificat de serveur, et gestion de connexion.  Les en\-têtes personnalisés et les en\-têtes non disponibles via les propriétés peuvent être stockés dans et accessibles via la propriété de **En\-têtes** .  
  
 **HttpWebRequest** est la classe par défaut utilisée par **WebRequest** et n'a pas besoin d'être inscrit pour que vous puissiez obtenir l'URI à la méthode de **WebRequest.Create** .  
  
 Vous pouvez rendre votre application suivre HTTP redirige automatiquement en affectant à la propriété d' <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> à **true** \(valeur par défaut\).  L'application redirige l'utilisateur des applications, et la propriété de [ResponseURI](frlrfsystemnethttpwebresponseclassresponseuritopic) de **HttpWebResponse** contiendra la ressource web réelle qui a répondu à la demande.  Si vous définissez **AllowAutoRedirect** à **false**, votre application doit pouvoir gérer les redirections comme des erreurs de protocole HTTP.  
  
 Les applications reçoivent des erreurs de protocole HTTP en interceptant <xref:System.Net.WebException> avec <xref:System.Net.WebException.Status%2A> défini à [WebExceptionStatus.ProtocolError](frlrfsystemnetwebexceptionstatusclasstopic).  La propriété d' <xref:System.Net.WebException.Response%2A> contient **WebResponse** envoyé par le serveur et indique l'erreur réelle HTTP produite.  
  
## Voir aussi  
 [Accès à Internet via un proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)   
 [Utilisation de protocoles d’application](../../../docs/framework/network-programming/using-application-protocols.md)   
 [Comment : accéder aux propriétés spécifiques à HTTP](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)