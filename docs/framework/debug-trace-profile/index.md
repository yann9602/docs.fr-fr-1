---
title: "Debugging, Tracing, and Profiling | Microsoft Docs"
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
  - "debugging [.NET Framework]"
  - ".NET Framework application configuration, debugging"
  - "debugging [.NET Framework], .NET Framework application debugging"
  - "troubleshooting applications [.NET Framework], profiling"
  - "application development [.NET Framework], debugging"
  - ".NET Framework application configuration, profiling"
  - "profiling applications"
  - "troubleshooting applications [.NET Framework], debugging"
  - "troubleshooting applications [.NET Framework]"
  - "application development [.NET Framework], profiling"
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
caps.latest.revision: 28
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 28
---
# Debugging, Tracing, and Profiling
Pour déboguer une application .NET Framework, le compilateur et l'environnement d'exécution doivent être configurés pour permettre l'attachement d'un débogueur à l'application et la génération de cartes à la fois de symboles et de lignes, si possible, pour l'application et son langage MSIL \(Microsoft Intermediate Language\) correspondant.  Une fois déboguée, une application managée peut être profilée en vue d'améliorer ses performances.  Le profilage évalue et décrit les lignes de code source qui génèrent le code le plus fréquemment exécuté, et le temps que demande leur exécution.  
  
 Les applications .NET Framework sont facilement déboguées à l'aide de Visual Studio, qui gère de nombreux détails de la configuration.  Si Visual Studio n'est pas installé, vous pouvez analyser et améliorer les performances des applications .NET Framework à l'aide des classes de débogage de l'espace de noms <xref:System.Diagnostics> du .NET Framework.  Cet espace de noms comprend les classes <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.TraceSource> pour tracer le flux d'exécution, ainsi que les classes <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog> et <xref:System.Diagnostics.PerformanceCounter> pour profiler le code.  
  
## Dans cette section  
 [Enabling JIT\-Attach Debugging](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 Montre comment configurer le Registre de manière à attacher via le JIT un moteur de débogage à une application .NET Framework.  
  
 [Simplification du débogage d'une image](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 Montre comment activer le suivi JIT et désactiver l'optimisation pour faciliter le débogage d'un assembly.  
  
 [Tracing and Instrumenting Applications](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 Explique comment surveiller l'exécution de votre application et comment l'instrumenter pour afficher la progression ou au contraire les problèmes survenus.  
  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 Décrit les Assistants Débogage managé \(MDA\), des outils de débogage qui fonctionnent conjointement au common language runtime \(CLR\) pour fournir des informations sur l'état d'exécution.  
  
 [Enhancing Debugging with the Debugger Display Attributes](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 Explique comment le développeur d'un type peut contrôler la façon dont ce type s'affiche dans un débogueur.  
  
 [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 Décrit les compteurs que vous pouvez utiliser pour suivre les performances d'une application.  
  
## Rubriques connexes  
 [Débogage d'applications ASP.NET et AJAX](../Topic/Debugging%20ASP.NET%20and%20AJAX%20Applications.md)  
 Indique la configuration requise et fournit des instructions pour déboguer une application ASP.NET pendant le développement ou après le déploiement.  
  
 [Guide de développement](../../../docs/framework/development-guide.md)  
 Fournit un guide sur tous les domaines technologiques clés et les tâches relatives au développement d'applications, notamment la création, la configuration, le débogage, la sécurisation et le déploiement de votre application, ainsi que des informations sur la programmation dynamique, l'interopérabilité, l'extensibilité, la gestion de mémoire et le threading.