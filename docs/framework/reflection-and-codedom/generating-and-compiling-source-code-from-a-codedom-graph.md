---
title: "G&#233;n&#233;ration et compilation du code source &#224; partir d&#39;un graphique CodeDOM | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys (.NET Framework), CodeDOM"
  - "compilateurs de code"
  - "modèle CodeDOM (Code Document Object Model), générer du code source"
  - "modèle CodeDOM (Code Document Object Model), graphiques"
  - "générateurs de code"
  - "CodeDOM, générer du code source"
  - "CodeDOM, graphiques"
  - "compiler des assemblys"
  - "compiler le code source, langages multiples"
  - "compilation dynamique"
  - "représenter du code source dynamiquement"
  - "générer des graphiques CodeDOM"
  - "générer du code source dans plusieurs langages"
  - "graphique CodeDOM"
  - "sortir le code source par CodeDOM"
  - "code source (génération)"
  - "code source, générer"
  - "génération de code basé sur un modèle"
  - "convertir d'un langage à un autre"
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# G&#233;n&#233;ration et compilation du code source &#224; partir d&#39;un graphique CodeDOM
L'espace de noms <xref:System.CodeDom.Compiler> fournit des interfaces pour la génération du code source à partir des graphiques d'objets CodeDOM et la gestion de la compilation avec les compilateurs pris en charge.  Un fournisseur de code peut produire du code source dans un langage de programmation particulier conformément à un graphique CodeDOM.  Une classe qui dérive de <xref:System.CodeDom.Compiler.CodeDomProvider> peut fournir en général des méthodes pour générer et compiler le code pour le langage pris en charge par le fournisseur.  
  
## Utilisation d'un fournisseur de code CodeDOM pour générer du code source  
 Pour générer du code source dans un langage particulier, il vous faut un graphique CodeDOM représentant la structure du code source à générer.  
  
 L'exemple suivant montre comment créer une instance d'un <xref:Microsoft.CSharp.CSharpCodeProvider> :  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 Le graphique de génération du code est généralement contenu dans <xref:System.CodeDom.CodeCompileUnit>.  Pour générer le code d'un **CodeCompileUnit** qui contient un graphique CodeDOM, appelez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> du fournisseur de code.  Cette méthode possède un paramètre pour <xref:System.IO.TextWriter> qu'elle utilise afin de générer le code source ; il est donc parfois nécessaire de créer d'abord un **TextWriter** dans lequel il est possible d'écrire.  L'exemple suivant illustre la génération de code à partir de **CodeCompileUnit** et l'écriture du code source généré dans un fichier appelé HelloWorld.cs.  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## Utilisation d'un fournisseur de code CodeDOM pour compiler des assemblys  
 **Appel de la compilation**  
  
 Pour compiler un assembly à l'aide d'un fournisseur CodeDom, vous devez disposer soit du code source à compiler dans un langage pour lequel vous avez un compilateur, soit d'un graphique CodeDOM à partir duquel le code source à compiler peut être généré.  
  
 Si vous compilez un graphique CodeDOM, passez le <xref:System.CodeDom.CodeCompileUnit> contenant le graphique à la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> du fournisseur de code.  Si vous avez un fichier de code source dans un langage que le compilateur comprend, passez le nom du fichier contenant le code source à la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> du fournisseur CodeDom.  Vous pouvez également passer une chaîne contenant le code source dans un langage que le compilateur comprend à la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> du fournisseur CodeDom.  
  
 **Configuration des paramètres de compilation**  
  
 Toutes les méthodes invoquant une compilation standard d'un fournisseur CodeDom ont un paramètre de type <xref:System.CodeDom.Compiler.CompilerParameters> qui indique les options à utiliser pour la compilation.  
  
 Vous pouvez spécifier un nom de fichier pour l'assembly de sortie dans la propriété <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> de **CompilerParameters**.  Sinon, un nom de fichier de sortie par défaut est utilisé.  
  
 Par défaut, un nouveau **CompilerParameters** est initialisé dont la propriété <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> est définie avec la valeur **false**.  Si vous compilez un programme exécutable, vous devez assigner à la propriété **GenerateExecutable** la valeur **true**.  Lorsque **GenerateExecutable** a la valeur **false**, le compilateur génère une bibliothèque de classes.  
  
 Si vous compilez un exécutable à partir d'un graphique CodeDOM, un <xref:System.CodeDom.CodeEntryPointMethod> doit être défini dans le graphe.  S'il existe plusieurs points d'entrée dans le code, il sera peut\-être nécessaire de définir la propriété <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> de **CompilerParameters** en lui assignant le nom de la classe qui définit le point d'entrée à utiliser.  
  
 Pour inclure des informations de débogage dans un exécutable généré, assignez à la propriété <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> la valeur **true**.  
  
 Si votre projet référence des assemblys, vous devez spécifier les noms d'assemblys en tant qu'éléments de <xref:System.Collections.Specialized.StringCollection> comme la propriété <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> du **CompilerParameters** que vous utilisez pour appeler la compilation.  
  
 Vous pouvez compiler un assembly écrit en mémoire plutôt que sur disque en affectant la valeur **true** à la propriété <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A>.  Lorsqu'un assembly est généré en mémoire, votre code peut obtenir une référence à l'assembly généré à partir de la propriété <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> de <xref:System.CodeDom.Compiler.CompilerResults>.  Lorsqu'un assembly est écrit sur disque, vous pouvez obtenir le chemin d'accès à cet assembly à partir de la propriété <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> de **CompilerResults**.  
  
 Pour spécifier une chaîne d'arguments de ligne de commande personnalisés à utiliser lors de l'appel du processus de compilation, affectez cette chaîne à la propriété <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A>.  
  
 Si l'appel du processus de compilation requiert un jeton de sécurité Win32, spécifiez le jeton dans la propriété <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A>.  
  
 Pour lier un fichier de ressources Win32 dans l'assembly compilé, spécifiez son nom dans la propriété <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A>.  
  
 Pour spécifier le niveau d'avertissement auquel la compilation doit être interrompue, assignez à la propriété <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> un entier correspondant au niveau d'avertissement auquel la compilation s'arrête.  Il est également possible de configurer le compilateur de manière à ce qu'il interrompe la compilation en cas d'avertissements, en affectant à la propriété <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> la valeur **true**.  
  
 L'exemple de code suivant montre la compilation d'un fichier source à l'aide d'un fournisseur CodeDom dérivé de la classe <xref:System.CodeDom.Compiler.CodeDomProvider>.  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## Langages avec prise en charge initiale  
 Le .NET Framework fournit des compilateurs de code et des générateurs de code pour les langages suivants : C\#, Visual Basic, C\+\+ et JScript.  La prise en charge de CodeDOM peut être étendue à d'autres langages en implémentant des générateurs de code et des compilateurs de code spécifiques au langage.  
  
## Voir aussi  
 <xref:System.CodeDom>   
 <xref:System.CodeDom.Compiler>   
 [Génération et compilation de code source dynamique](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)   
 [CodeDOM Quick Reference](http://msdn.microsoft.com/fr-fr/c77b8bfd-0a32-4e36-b59a-4f687f32c524)