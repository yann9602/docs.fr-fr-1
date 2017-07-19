---
title: "Simplification du d&#233;bogage d&#39;une image | Microsoft Docs"
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
  - "images (.NET Framework), débogage"
  - "image exécutable à déboguer"
  - "débogage (.NET Framework), images exécutables pour"
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# Simplification du d&#233;bogage d&#39;une image
Lors de la compilation d'un code non managé, vous pouvez configurer une image exécutable à déboguer en définissant des commutateurs IDE ou des options de ligne de commande.  Par exemple, vous pouvez utiliser l'option de ligne de commande \/**Zi** dans Visual C\+\+ pour lui demander d'émettre des fichiers de symboles de débogage \(extension de fichier .pdb\).  De son côté, l'option de ligne de commande \/**Od** indique au compilateur de désactiver l'optimisation.  Le code obtenu s'exécute plus lentement, mais est plus facile à déboguer \(le cas échéant\).  
  
 Lors de la compilation d'un code managé .NET Framework, des compilateurs tels que Visual C\+\+, Visual Basic et C\# compilent leur programme source en langage MSIL \(Microsoft Intermediate Language\).  MSIL est ensuite traité par un compilateur JIT en code machine natif, avant d'être exécuté.  Comme dans le cas du code non managé, vous pouvez configurer une image exécutable à déboguer en définissant des commutateurs IDE ou des options de ligne de commande.  En outre, vous pouvez configurer la compilation JIT en vue du débogage pratiquement de la même façon.  
  
 Cette configuration JIT présente deux aspects :  
  
-   Vous pouvez demander au compilateur JIT de générer des informations de suivi.  Le débogueur peut ainsi faire correspondre à une chaîne MSIL une chaîne de son code machine, et de suivre l'emplacement où les variables locales et les arguments de fonction sont stockés.  Dans .NET Framework version 2.0, le compilateur JIT génère toujours des informations de suivi ; il est donc inutile de les demander.  
  
-   Vous pouvez demander au compilateur JIT de ne pas optimiser le code machine résultant.  
  
 Normalement, le compilateur qui génère le code MSIL définit ces options du compilateur JIT correctement, en fonction des commutateurs IDE ou des options de ligne de commande que vous spécifiez, par exemple \/**Od**.  
  
 Dans certains cas, il est possible de modifier le comportement du compilateur JIT de sorte que le code machine qu'il génère soit plus facile à déboguer.  Par exemple, il est possible de générer des informations de suivi JIT pour une version commerciale ou de contrôler l'optimisation.  Vous pouvez effectuer ces opérations avec un fichier d'initialisation \(.ini\).  
  
 Par exemple, si l'assembly que vous voulez déboguer s'appelle MyApp.exe, vous pouvez créer un fichier texte nommé MyApp.ini dans le même dossier que MyApp.exe, qui contient ces trois lignes :  
  
```  
[.NET Framework Debugging Control]  
GenerateTrackingInfo=1  
AllowOptimize=0  
```  
  
 Vous pouvez affecter à chaque option la valeur 0 ou 1, et toute option absente a la valeur par défaut 0.  L'attribution de la valeur 1 à `GenerateTrackingInfo` et de la valeur 0 à `AllowOptimize` permet un débogage facile.  
  
> [!NOTE]
>  Dans le .NET Framework version 2.0, le compilateur JIT génère toujours des informations de suivi indépendantes de la valeur de `GenerateTrackingInfo` ; toutefois, la valeur `AllowOptimize` a toujours un effet.  Lors de l'utilisation de l'[Ngen.exe \(Native Image Generator\)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) pour précompiler l'image native sans optimisation, le fichier .ini doit être présent dans le dossier cible avec `AllowOptimize=0` lorsque le fichier Ngen.exe est exécuté.  Si vous avez précompilé un assembly sans optimisation, vous devez supprimer le code précompilé à l'aide de l'option **\/uninstall** du fichier NGen.exe avant de réexécuter Ngen.exe pour précompiler le code de manière optimisée.  Si le fichier .ini n'est pas présent dans le dossier, par défaut, le fichier Ngen.exe précompile le code de manière optimisée.  
  
> [!NOTE]
>  L'attribut <xref:System.Diagnostics.DebuggableAttribute?displayProperty=fullName> contrôle les paramètres d'un assembly.  **DebuggableAttribute** comprend deux champs qui enregistrent les paramètres indiquant si le compilateur JIT doit optimiser et\/ou si des informations de suivi doivent être générées.  Dans .NET Framework version 2.0, le compilateur JIT génère toujours des informations de suivi.  
  
> [!NOTE]
>  Pour une version commerciale, les compilateurs ne définissent pas **DebuggableAttribute**.  Le comportement par défaut du compilateur JIT consiste à générer les performances les plus élevées, et le code machine le plus difficile à déboguer.  L'activation du suivi JIT diminue légèrement les performances, alors que la désactivation de l'optimisation les réduit considérablement.  
  
> [!NOTE]
>  L'attribut **DebuggableAttribute** s'applique à tout un assembly à la fois, et non aux différents modules qui composent celui\-ci.  Par conséquent, les outils de développement doivent joindre des attributs personnalisés au jeton de métadonnées de l'assembly, si un assembly a déjà été créé, ou à la classe appelée **System.Runtime.CompilerServices.AssemblyAttributesGoHere**.  L'outil ALink élève ensuite ces attributs **DebuggableAttribute** de chaque module vers l'assembly dont ils deviennent une partie.  En cas de conflit, l'opération ALink échoue.  
  
> [!NOTE]
>  Dans la version 1.0 de .NET Framework, le compilateur Microsoft Visual C\+\+ ajoute **DebuggableAttribute** lorsque les options de compilateur **\/clr** et **\/Zi**  sont spécifiées.  Dans la version 1.1 de .NET Framework, vous devez soit ajouter manuellement **DebugabbleAttribute** à votre code soit utiliser l'option d'éditeur de liens **\/ASSEMBLYDEBUG**.  
  
## Voir aussi  
 [Debugging, Tracing, and Profiling](../../../docs/framework/debug-trace-profile/index.md)   
 [Enabling JIT\-Attach Debugging](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)   
 [Enabling Profiling](http://msdn.microsoft.com/fr-fr/3b669676-f0e0-4ebf-8674-68986dd2020d)