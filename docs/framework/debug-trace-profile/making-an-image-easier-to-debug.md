---
title: "Simplification du débogage d'une image"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e05af51010e92586a9f1de423f6304ea8db78168
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="making-an-image-easier-to-debug"></a>Simplification du débogage d'une image
Lors de la compilation de code non managé, vous pouvez configurer une image exécutable pour le débogage en définissant des commutateurs ou des options de ligne de commande de l’IDE. Par exemple, vous pouvez utiliser l’option de ligne de commande /**Zi** dans Visual C++ pour lui demander de produire des fichiers de symboles de débogage (extension de fichier .pdb). De même, l’option de ligne de commande /**Od** indique au compilateur de désactiver l’optimisation. Le code résultant s’exécute plus lentement, mais il est plus facile à déboguer quand c’est nécessaire.  
  
 Lors de la compilation de code managé .NET Framework, des compilateurs comme Visual C++, Visual Basic et C# compilent leur programme source en langage MSIL (Microsoft Intermediate Language). MSIL est ensuite compilé selon le mode JIT, juste avant l’exécution, en code machine natif. Comme avec le code non managé, vous pouvez configurer une image exécutable pour le débogage en définissant des commutateurs ou des options de ligne de commande de l’IDE. De plus, vous pouvez configurer la compilation JIT pour le débogage presque de la même façon.  
  
 Cette configuration JIT a deux aspects :  
  
-   Vous pouvez demander au compilateur JIT de générer des informations de suivi. Ceci permet au débogueur de faire correspondre une chaîne d’instructions MSIL à son équivalent en code machine, et d’effectuer le suivi des emplacements de stockage des variables locales et des arguments de fonction.  Dans le .NET Framework version 2.0, le compilateur JIT génère toujours des informations de suivi : il est donc inutile de les demander.  
  
-   Vous pouvez demander au compilateur JIT de ne pas optimiser le code machine résultant.  
  
 Normalement, le compilateur qui génère le code MSIL définit ces options du compilateur JIT de façon appropriée, en fonction des commutateurs ou des options de ligne de commande de l’IDE que vous spécifiez, par exemple /**Od**.  
  
 Dans certains cas, vous pouvez changer le comportement du compilateur JIT afin que le code machine généré soit plus facile à déboguer. Par exemple, vous pouvez générer des informations de suivi JIT pour une version commerciale ou pour l’optimisation du contrôle. Vous pouvez faire cela avec un fichier d’initialisation (.ini).  
  
 Par exemple, si l’assembly que vous voulez déboguer s’appelle MyApp.exe, vous pouvez créer un fichier texte nommé MyApp.ini dans le même dossier sous le nom MyApp.exe, qui contient ces trois lignes :  
  
```  
[.NET Framework Debugging Control]  
GenerateTrackingInfo=1  
AllowOptimize=0  
```  
  
 Vous pouvez définir la valeur de chaque option sur 0 ou 1. Les options absentes ont 0 comme valeur par défaut. La définition de `GenerateTrackingInfo` sur 1 et de `AllowOptimize` sur 0 est ce qui permet le débogage le plus facile.  
  
> [!NOTE]
>  Dans le .NET Framework version 2.0, le compilateur JIT génère toujours des informations de suivi, quelle que soit la valeur de `GenerateTrackingInfo` ; la valeur de `AllowOptimize` a cependant toujours un effet. Quand vous utilisez le générateur d’images natives [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) pour précompiler l’image native sans optimisation, le fichier .ini doit être présent dans le dossier cible avec `AllowOptimize=0` quand Ngen.exe s’exécute. Si vous avez précompilé un assembly sans optimisation, vous devez supprimer le code précompilé à l’aide de l’option **/uninstall**de NGen.exe avant de réexécuter Ngen.exe pour précompiler le code avec optimisation. Si le fichier .ini n’est pas présent dans le dossier, Ngen.exe précompile par défaut le code avec optimisation.  
  
> [!NOTE]
>  <xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> contrôle les paramètres pour un assembly. **DebuggableAttribute** comprend deux champs qui enregistrent les paramètres spécifiant si le compilateur JIT doit optimiser et/ou générer des informations de suivi. Dans le .NET Framework version 2.0, le compilateur JIT génère toujours des informations de suivi.  
  
> [!NOTE]
>  Pour une version commerciale, les compilateurs ne définissent rien pour **DebuggableAttribute**. Le comportement par défaut du compilateur JIT est de générer du code machine avec les performances les plus élevées, mais le plus difficile à déboguer. L’activation du suivi dans JIT diminue légèrement les performances, tandis que la désactivation de l’optimisation les réduit considérablement.  
  
> [!NOTE]
>  **DebuggableAttribute** s’applique à la totalité d’un assembly, et non pas à des modules individuels dans l’assembly. Les outils de développement doivent donc attacher des attributs personnalisés au jeton de métadonnées de l’assembly si un assembly a déjà été créé, ou à la classe appelée **System.Runtime.CompilerServices.AssemblyAttributesGoHere**. L’outil ALink promeut ensuite ces attributs **DebuggableAttribute** de chaque module vers l’assembly dont ils font partie. Si un conflit se produit, l’opération ALink échoue.  
  
> [!NOTE]
>  Dans la version 1.0 du .NET Framework, le compilateur Microsoft Visual C++ ajoute **DebuggableAttribute** quand les options du compilateur **/clr** et **/Zi** sont spécifiées. Dans la version 1.1 du .NET Framework, vous devez ajouter **DebugabbleAttribute** manuellement dans votre code ou en utilisant l’option de l’éditeur de liens **/ASSEMBLYDEBUG**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage, traçage et profilage](../../../docs/framework/debug-trace-profile/index.md)  
 [Activation du débogage juste-à-temps](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 [Activation du profilage](http://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
