---
title: "Comment&#160;: cr&#233;er un fichier de documentation XML &#224; l&#39;aide de CodeDOM | Microsoft Docs"
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
  - "modèle CodeDOM (Code Document Object Model), générer la documentation XML"
  - "CodeDOM, générer la documentation XML"
  - "documentation XML, créer à l'aide de CodeDOM"
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: cr&#233;er un fichier de documentation XML &#224; l&#39;aide de CodeDOM
CodeDOM peut être utilisé pour créer du code générant une documentation XML.  Le processus implique la création du graphique CodeDOM qui contient les commentaires de documentation XML, la génération du code et la compilation du code généré avec l'option du compilateur qui crée la sortie de documentation XML.  
  
### Pour créer un graphique CodeDOM contenant des commentaires de documentation XML  
  
1.  Créez un <xref:System.CodeDom.CodeCompileUnit> contenant le graphique CodeDOM pour l'exemple d'application.  
  
2.  Utilisez le constructeur <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> avec le jeu de paramètres `docComment` auquel est affectée la valeur `true` pour créer le texte et les éléments de commentaire de la documentation XML.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### Pour générer le code à partir de CodeCompileUnit  
  
1.  Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> pour générer le code et créer un fichier source à compiler.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### Pour compiler le code et générer le fichier de documentation  
  
1.  Ajoutez l'option du compilateur **\/doc** à la propriété <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> d'un objet <xref:System.CodeDom.Compiler.CompilerParameters> et passez l'objet à la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> pour créer le fichier de documentation XML lorsque le code est compilé.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## Exemple  
 L'exemple de code suivant crée un graphique CodeDOM avec des commentaires de documentation, génère un fichier de code à partir du graphique, compile le fichier et crée un fichier de documentation XML associé.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 L'exemple de code crée la documentation XML suivante dans le fichier HelloWorldDoc.xml.  
  
```  
<?xml version="1.0" ?>   
<doc>  
  <assembly>  
    <name>HelloWorld</name>   
  </assembly>  
  <members>  
    <member name="T:Samples.Class1">  
      <summary>  
        Create a Hello World application.   
        <seealso cref="M:Samples.Class1.Main" />   
      </summary>  
    </member>  
    <member name="M:Samples.Class1.Main">  
      <summary>  
        Main method for HelloWorld application.   
        <para>Add a new paragraph to the description.</para>   
      </summary>  
    </member>  
  </members>  
</doc>  
```  
  
## Compilation du code  
  
-   Cet exemple de code requiert le jeu d'autorisations `FullTrust` pour une exécution réussie.  
  
## Voir aussi  
 [Documenting Your Code with XML](../Topic/Documenting%20Your%20Code%20with%20XML%20\(Visual%20Basic\).md)   
 [Commentaires de documentation XML](../Topic/XML%20Documentation%20Comments%20\(C%23%20Programming%20Guide\).md)   
 [Documentation XML](../Topic/XML%20Documentation%20\(Visual%20C++\).md)