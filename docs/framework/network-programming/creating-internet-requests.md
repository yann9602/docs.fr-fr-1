---
title: "Cr&#233;ation de requ&#234;tes Internet | Microsoft Docs"
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
  - "WebRequest (classe), envoyer et recevoir des données"
  - "Réseau"
  - "HttpWebResponse (classe), envoyer et recevoir des données"
  - "demande de données sur Internet, créer des requêtes"
  - "Ressources réseau"
  - "Internet, demander des données"
  - "requêtes de données, créer des requêtes"
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# Cr&#233;ation de requ&#234;tes Internet
Les applications créent des instances d' <xref:System.Net.WebRequest> via la méthode d' <xref:System.Net.WebRequest.Create%2A?displayProperty=fullName> .  C'est une méthode statique qui crée une classe dérivée de **WebRequest** sur le modèle URI passé.  
  
## Web, fichiers et demandes de FTP  
 Le.NET Framework fournit la classe d' <xref:System.Net.HttpWebRequest> , dérivée de **WebRequest**, pour traiter les requêtes HTTP ou HTTPS.  Dans la plupart des cas, la classe de **WebRequest** fournit toutes les propriétés que vous devez faire une demande ; néanmoins si nécessaire, vous pouvez effectuer un cast d'objets de **WebRequest** créés par la méthode de **WebRequest.Create** au type de **HttpWebRequest** pour accéder aux propriétés de HTTP spécifiques à la demande.  De même, les handles d'objet de **HttpWebResponse** les réponses aux requêtes HTTP ou HTTPS.  Pour accéder aux propriétés de HTTP spécifiques de **HttpWebResponse** objet, vous devez effectuer un cast d'objets de **WebResponse** au type de **HttpWebResponse** .  
  
 Le.NET Framework fournit également des classes d' <xref:System.Net.FileWebRequest> et d' <xref:System.Net.FileWebResponse> aux demandes de gérer des ressources qui utilisent le « fichier :  » Modèle URI.  De même, <xref:System.Net.FtpWebRequest> et les classes d' <xref:System.Net.FtpWebResponse> sont fournis aux demandes de gérer des ressources qui utilisent le « FTP :  » modèle.  Si votre application est pour une ressource qui utilise l'un de ces modèles, vous pouvez utiliser la méthode de **WebRequest.Create** pour obtenir un objet avec lequel pour rendre votre application.  
  
 Pour traiter les requêtes qui utilisent d'autres protocoles au niveau de l'application, vous devez implémenter des classes spécifiques au protocole dérivées de **WebRequest** et de **WebResponse**.  Pour plus d'informations, consultez [Protocoles enfichables de programmation](../../../docs/framework/network-programming/programming-pluggable-protocols.md).  
  
## Voir aussi  
 [Procédure : demande de données à l’aide de la classe WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)   
 [Demande de données](../../../docs/framework/network-programming/requesting-data.md)