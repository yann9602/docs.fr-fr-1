---
title: "Enabling JIT-Attach Debugging | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "JIT-attach debugging"
  - "debugging [.NET Framework], JIT-attach debugging"
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# Enabling JIT-Attach Debugging
Le débogage JIT\-attach est l'expression utilisée pour décrire l'attachement d'un débogueur à un processus lorsque vous rencontrez des erreurs. Il peut également être déclenché par des fonctions ou des méthodes spécifiques.  
  
 Le débogage JIT\-attach est utilisé dans les conditions d'erreur suivantes :  
  
-   Exceptions non gérées \(dans du code natif et managé\).  
  
-   La méthode <xref:System.Environment.FailFast%2A?displayProperty=fullName> ou [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) fonction \(famille Windows 7\).  
  
-   Erreurs d'exécution irrécupérables.  
  
 Le débogage JIT\-attach est également déclenché par des appels aux méthodes et aux fonctions suivantes :  
  
-   Méthode <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=fullName>.  
  
-   Méthode <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=fullName>.  
  
-   [DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) \(fonction Win32\).  
  
 Avant [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], le .NET Framework fournissait des clés de Registre séparées pour contrôler le comportement des débogueurs natifs et managés.  Depuis [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], le contrôle est consolidé dans une clé de Registre unique : HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\Current Version\\AeDebug.  Les valeurs attribuées à cette clé déterminent si un débogueur est appelé, et, le cas échéant, s'il est appelé avec une boîte de dialogue nécessitant une intervention de l'utilisateur.  Pour plus d'informations sur cette clé de Registre, consultez [Configuration du débogage automatique](http://go.microsoft.com/fwlink/?LinkId=181767) dans MSDN Library.  
  
## Voir aussi  
 [Debugging, Tracing, and Profiling](../../../docs/framework/debug-trace-profile/index.md)   
 [Simplification du débogage d'une image](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)   
 [Enabling Profiling](http://msdn.microsoft.com/fr-fr/3b669676-f0e0-4ebf-8674-68986dd2020d)