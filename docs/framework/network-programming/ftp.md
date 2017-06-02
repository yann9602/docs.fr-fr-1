---
title: "FTP | Microsoft Docs"
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
  - "FTP"
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# FTP
Le.NET Framework fournit une prise en charge complète du protocole FTP avec les classes d' <xref:System.Net.FtpWebRequest> et d' <xref:System.Net.FtpWebResponse> .  Ces classes sont dérivées d' <xref:System.Net.WebRequest> et d' <xref:System.Net.WebResponse>.  Dans la plupart des cas, <xref:System.Net.WebRequest> et les classes d' <xref:System.Net.WebResponse> fournissent tout ce qui est nécessaire pour que l'application, mais si vous avez besoin d'accéder aux fonctionnalités de FTP\- détail exposées comme propriétés, vous pouvez convertir le rôle de ces classes à <xref:System.Net.FtpWebRequest> ou à <xref:System.Net.FtpWebResponse>.  
  
## Exemples  
 Pour plus d'informations, consultez les rubriques suivantes : [Comment : télécharger des fichiers avec FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [Comment : charger des fichiers avec FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), et [Comment : répertorier le contenu d’un répertoire avec FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).  
  
## FTP et proxy  
 Si un proxy \(spécifié par la propriété d' <xref:System.Net.FtpWebRequest.Proxy%2A> \) est un proxy HTTP, alors que <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, les commandes et d' <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> en charge.  
  
## Voir aussi  
 [Accès à Internet via un proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)   
 [Exemples de programmation réseau](../../../docs/framework/network-programming/network-programming-samples.md)   
 [Exemple de technologie cliente FTP](http://go.microsoft.com/fwlink/?LinkID=179557)   
 [Exemple de technologie de l'explorateur FTP](http://go.microsoft.com/fwlink/?LinkID=179569)   
 [Utilisation de protocoles d’application](../../../docs/framework/network-programming/using-application-protocols.md)