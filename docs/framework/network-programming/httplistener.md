---
title: "HttpListener | Microsoft Docs"
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
  - "HTTP"
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# HttpListener
La classe <xref:System.Net.HttpListener> fournit un écouteur de protocole HTTP contrôlé par programmation.  L'écouteur est actif pendant toute la durée de vie de l'objet <xref:System.Net.HttpListener> et s'exécute au sein de votre application.  
  
## HTTP.SYS  
 La classe <xref:System.Net.HttpListener> repose sur HTTP.sys, qui est l'écouteur en mode noyau qui gère tout le trafic HTTP pour Windows.  HTTP.sys assure la gestion des connexions, la limitation de la bande passante et la journalisation du serveur web.  Utilisez l'outil `HttpCfg.exe` pour ajouter des certificats SSL.  Pour plus d'informations, consultez la documentation sur l'outil [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) dans la documentation du [serveur](http://go.microsoft.com/fwlink/?LinkID=178285).  
  
## Voir aussi  
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpWebRequest>   
 <xref:System.Net.HttpWebResponse>   
 [Serveur HTTP](http://go.microsoft.com/fwlink/?LinkID=178285)   
 [Améliorations de la sécurité dans les informations Internet](http://go.microsoft.com/fwlink/?LinkID=178286)   
 [Exemple d'application hôte ASPX HttpListener](http://go.microsoft.com/fwlink/?LinkID=179560)   
 [Exemple de technologie HttpListener](http://go.microsoft.com/fwlink/?LinkID=179558)   
 [Exemples de programmation réseau](../../../docs/framework/network-programming/network-programming-samples.md)