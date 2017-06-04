---
title: "Comment&#160;: cr&#233;er une classe &#224; l&#39;aide de CodeDOM | Microsoft Docs"
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
  - "modèle CodeDOM (Code Document Object Model), créer des classes"
  - "modèle CodeDOM (Code Document Object Model), graphiques"
  - "CodeDOM, créer des classes"
  - "CodeDOM, graphiques"
  - "graphique CodeDOM"
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er une classe &#224; l&#39;aide de CodeDOM
Les procédures suivantes illustrent la création et la compilation d'un graphique CodeDOM qui génère une classe contenant deux champs, trois propriétés, une méthode, un constructeur et un point d'entrée.  
  
1.  Créez une application console qui utilisera du code CodeDOM pour générer le code source pour une classe.  
  
     Dans cet exemple, la classe génératrice est nommée `Sample` et le code généré est une classe nommée `CodeDOMCreatedClass` dans un fichier nommé SampleCode.  
  
2.  Dans la classe génératrice, initialisez le graphique CodeDOM et utilisez des méthodes CodeDOM pour définir les membres, le constructeur et le point d'entrée \(méthode `Main`\) de la classe générée.  
  
     Dans cet exemple, la classe générée compte deux champs, trois propriétés, un constructeur, une méthode, et une méthode `Main`.  
  
3.  Dans la classe génératrice, créez un fournisseur de code spécifique au langage et appelez sa méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> pour générer le code à partir du graphique.  
  
4.  Compilez et exécutez l'application pour générer le code.  
  
     Dans cet exemple, le code généré se trouve dans un fichier nommé SampleCode.  Compilez et exécutez ce code pour consulter la sortie de l'exemple.  
  
### Pour créer l'application qui exécutera le code CodeDOM  
  
-   Créez une classe d'application console pour contenir le code CodeDOM.  Définissez les champs globaux qui seront utilisés dans la classe pour référencer l'assembly \(<xref:System.CodeDom.CodeCompileUnit>\) et la classe \(<xref:System.CodeDom.CodeTypeDeclaration>\), spécifiez le nom du fichier source généré et déclarez la méthode `Main`.  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### Pour initialiser le graphique CodeDOM  
  
-   Dans le constructeur pour la classe d'application console, initialisez l'assembly et la classe, puis ajoutez les déclarations appropriées au graphique CodeDOM.  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### Pour ajouter des membres au graphique CodeDOM  
  
-   Ajoutez des champs au graphique CodeDOM en ajoutant des objets <xref:System.CodeDom.CodeMemberField> à la propriété <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> de la classe.  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   Ajoutez des propriétés au graphique CodeDOM en ajoutant des objets <xref:System.CodeDom.CodeMemberProperty> à la propriété <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> de la classe.  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   Ajoutez une méthode au graphique CodeDOM en ajoutant un objet <xref:System.CodeDom.CodeMemberMethod> à la propriété <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> de la classe.  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   Ajoutez un constructeur au graphique CodeDOM en ajoutant un objet <xref:System.CodeDom.CodeConstructor> à la propriété <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> de la classe.  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   Ajoutez un point d'entrée au graphique CodeDOM en ajoutant un objet <xref:System.CodeDom.CodeEntryPointMethod> à la propriété <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> de la classe.  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### Pour générer le code à partir du graphique CodeDOM  
  
-   Générez le code source à partir du graphique CodeDOM en appelant la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A>.  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### Pour créer le graphique et générer le code  
  
1.  Ajoutez les méthodes créées aux étapes précédentes à la méthode `Main` définie à la première étape.  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2.  Compilez et exécutez la classe génératrice.  
  
## Exemple  
 L'exemple de code suivant affiche le code des étapes précédentes.  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 Lorsque l'exemple précédent est compilé et exécuté, il produit le code source suivant.  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 Le code source généré produit la sortie suivante une fois compilé et exécuté.  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## Compilation du code  
  
-   Cet exemple de code requiert le jeu d'autorisations `FullTrust` pour une exécution réussie.  
  
## Voir aussi  
 [Utilisation du CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)   
 [Génération et compilation du code source à partir d'un graphique CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)