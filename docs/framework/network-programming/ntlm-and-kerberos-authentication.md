---
title: "Authentification NTLM et Kerberos | Microsoft Docs"
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
  - "authentification (.NET Framework), NTLM"
  - "authentification (.NET Framework), Kerberos"
  - "authentification utilisateur, Kerberos"
  - "authentification utilisateur, NTLM"
  - "Kerberos (authentification)"
  - "réception de données, authentification"
  - "NTLM (authentification)"
  - "Internet, authentification"
  - "authentification client, Kerberos"
  - "envoi de données, authentification"
  - "ressources réseau, authentification"
  - "classes (.NET Framework), authentification"
  - "authentification client, NTLM"
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Authentification NTLM et Kerberos
L'authentification par défaut et l'authentification Kerberos NTLM utilisent les informations d'identification de l'utilisateur Microsoft Windows NT associées à l'application appelante de tenter l'authentification avec le serveur.  Lorsque vous utilisez l'authentification non définie par défaut NTLM, l'application définit le type d'authentification à NTLM et utilise un objet d' <xref:System.Net.NetworkCredential> pour passer le nom d'utilisateur, le mot de passe, et le champ à l'hôte, comme indiqué dans l'exemple suivant.  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = _  
    New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials =   
    new NetworkCredential(UserName, SecurelyStoredPassword, Domain);  
```  
  
 Les applications qui doivent se connecter aux services web à l'aide de les informations d'identification de l'utilisateur de l'application peuvent faire avec les informations d'identification par défaut de l'utilisateur, comme indiqué dans l'exemple suivant.  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = CredentialCache.DefaultCredentials  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials = CredentialCache.DefaultCredentials;  
```  
  
 Le module d'authentification de négociation détermine si le serveur distant utilise l'authentification NTLM ou Kerberos, et envoie la réponse appropriée.  
  
> [!NOTE]
>  L'authentification NTLM ne fonctionne pas via un serveur proxy.  
  
## Voir aussi  
 [Authentification de base et authentification Digest](../../../docs/framework/network-programming/basic-and-digest-authentication.md)   
 [Authentification Internet](../../../docs/framework/network-programming/internet-authentication.md)