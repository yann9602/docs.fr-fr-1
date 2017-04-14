---
title: "Utilisation du protocole Secure Sockets Layer | Microsoft Docs"
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
  - "Réseau"
  - "SSL"
  - "Secure Sockets Layer"
  - "requête de données sur Internet, Secure Sockets Layer"
  - "envoi de données, Secure Sockets Layer"
  - "Ressources réseau"
  - "requêtes de données, Secure Sockets Layer"
  - "réception de données, Secure Sockets Layer"
  - "Internet, Secure Sockets Layer"
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# Utilisation du protocole Secure Sockets Layer
Les classes d' <xref:System.Net> utilisent le protocole SSL \(SSL\) pour chiffrer la connexion pour plusieurs protocoles réseau.  
  
 Pour les connexions HTTP, les classes d' <xref:System.Net.WebRequest> et d' <xref:System.Net.WebResponse> utilisez SSL pour communiquer avec le serveur web qui prennent en charge SSL.  La décision d'utiliser SSL est occupée par la classe d' <xref:System.Net.WebRequest> , selon l'URI qu'elle est spécifiée.  Si l'URI commence par « https :  », SSL est utilisé ; si l'URI commence par « http :  », une connexion décryptée est utilisée.  
  
 Pour utiliser SSL avec le protocole FTP \(FTP\), affectez à la propriété d' <xref:System.Net.FtpWebRequest.EnableSsl> true avant d'appeler <xref:System.Net.FtpWebRequest.GetResponse>.  De même, pour utiliser SSL avec le protocole SMTP \(SMTP\), affectez à la propriété d' <xref:System.Net.Mail.SmtpClient.EnableSsl> true avant d'envoyer des messages électroniques.  
  
 La classe d' <xref:System.Net.Security.SslStream> fournit une abstraction flot\- basée sur SSL, et offre de nombreuses façons de configurer la négociation SSL.  
  
## Exemple  
  
### Code  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références à l'espace de noms de **System.Net** .  
  
## Voir aussi  
 [Sécurité dans la programmation réseau](../../../docs/framework/network-programming/security-in-network-programming.md)   
 [Programmation réseau dans le .NET Framework](../../../docs/framework/network-programming/index.md)   
 [Sélection et validation de certificats](../../../docs/framework/network-programming/certificate-selection-and-validation.md)