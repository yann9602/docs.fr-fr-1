---
title: "Authentification de base et authentification Digest | Microsoft Docs"
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
  - "authentification (.NET Framework), classes"
  - "Authentification de base"
  - "authentification (.NET Framework), de base"
  - "authentification client, de base"
  - "authentification utilisateur, de base"
  - "authentification (.NET Framework), Digest"
  - "réception de données, authentification"
  - "authentification client, Digest"
  - "Internet, authentification"
  - "authentification Digest"
  - "envoi de données, authentification"
  - "ressources réseau, authentification"
  - "authentification utilisateur, Digest"
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# Authentification de base et authentification Digest
L'implémentation d' <xref:System.Net> de l'authentification de base et de résumé est conforme à RFC2617 – authentification HTTP : Authentification de base et Digest \(disponibles sur le site Web du World Wide Web Consortium \(W3C\) à l'adresse www.w3.org\).  
  
 Pour utiliser l'authentification de base et de résumé, une application doit fournir un nom d'utilisateur et un mot de passe dans la propriété d' <xref:System.Net.WebRequest.Credentials%2A> de l'objet d' <xref:System.Net.WebRequest> qu'elle utilise pour demander des données à partir de Internet, comme indiqué dans l'exemple suivant.  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
>  Les données envoyées avec de base et l'authentification Digest ne sont pas chiffrées, les données peuvent être vues par un adversaire.  En outre, les informations d'identification d'authentification de base \(nom d'utilisateur et mot de passe\) sont envoyées en clair et peuvent être désactivées.  
  
## Voir aussi  
 [Authentification NTLM et Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)   
 [Authentification Internet](../../../docs/framework/network-programming/internet-authentication.md)