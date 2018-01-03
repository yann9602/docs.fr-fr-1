---
title: Authentification de base et authentification Digest
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], classes
- Basic authentication
- authentication [.NET Framework], basic
- client authentication, basic
- user authentication, basic
- authentication [.NET Framework], digest
- receiving data, authentication
- client authentication, digest
- Internet, authentication
- digest authentication
- sending data, authentication
- network resources, authentication
- user authentication, digest
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7ca66a65c05da3d515358c0fdb26682fa4ec1438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-and-digest-authentication"></a>Authentification de base et authentification Digest
L’implémentation <xref:System.Net> de l’authentification de base et Digest est conforme à la RFC2617 – Authentification HTTP : authentification de base et authentification Digest (disponible sur site web du World Wide Web Consortium www.w3.org).  
  
 Pour utiliser l’authentification de base et l’authentification Digest, une application doit fournir un nom d’utilisateur et un mot de passe dans la propriété <xref:System.Net.WebRequest.Credentials%2A> de l’objet <xref:System.Net.WebRequest> qu’elle utilise pour demander des données à partir d’Internet, comme indiqué dans l’exemple suivant.  
  
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
>  Les données transmises avec une authentification de base et Digest ne sont pas chiffrées, par conséquent les données sont visibles par tous. De plus, les informations d'authentification de base (nom d'utilisateur et mot de passe) sont envoyées en texte clair et peuvent être interceptées.  
  
## <a name="see-also"></a>Voir aussi  
 [Authentification NTLM et Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [Authentification Internet](../../../docs/framework/network-programming/internet-authentication.md)
