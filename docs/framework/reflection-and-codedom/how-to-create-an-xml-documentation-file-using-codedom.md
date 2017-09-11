---
title: "Guide pratique pour créer un fichier de documentation XML à l’aide de CodeDOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7d5569fd22cc8469052cc318fd50a5f8ef94c1a9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="78d38-102">Guide pratique pour créer un fichier de documentation XML à l’aide de CodeDOM</span><span class="sxs-lookup"><span data-stu-id="78d38-102">How to: Create an XML Documentation File Using CodeDOM</span></span>
<span data-ttu-id="78d38-103">Vous pouvez utiliser CodeDOM pour créer du code qui génère de la documentation XML.</span><span class="sxs-lookup"><span data-stu-id="78d38-103">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="78d38-104">Le processus implique la création du graphique CodeDOM qui contient les commentaires de documentation XML, la génération du code et la compilation du code généré avec l’option du compilateur qui crée la sortie de documentation XML.</span><span class="sxs-lookup"><span data-stu-id="78d38-104">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a><span data-ttu-id="78d38-105">Pour créer un graphique CodeDOM qui contient des commentaires de documentation XML</span><span class="sxs-lookup"><span data-stu-id="78d38-105">To create a CodeDOM graph that contains XML documentation comments</span></span>  
  
1.  <span data-ttu-id="78d38-106">Créez un <xref:System.CodeDom.CodeCompileUnit> contenant le graphique CodeDOM pour l’exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="78d38-106">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2.  <span data-ttu-id="78d38-107">Utilisez le constructeur <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> avec le paramètre `docComment` défini sur `true` pour créer les éléments et le texte de commentaires de documentation XML.</span><span class="sxs-lookup"><span data-stu-id="78d38-107">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     <span data-ttu-id="78d38-108">[!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]  [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]</span><span class="sxs-lookup"><span data-stu-id="78d38-108">[!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]  [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]</span></span>  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="78d38-109">Pour générer le code à partir de CodeCompileUnit</span><span class="sxs-lookup"><span data-stu-id="78d38-109">To generate the code from the CodeCompileUnit</span></span>  
  
1.  <span data-ttu-id="78d38-110">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> pour générer le code et créer un fichier source à compiler.</span><span class="sxs-lookup"><span data-stu-id="78d38-110">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     <span data-ttu-id="78d38-111">[!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]  [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]</span><span class="sxs-lookup"><span data-stu-id="78d38-111">[!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]  [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]</span></span>  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="78d38-112">Pour compiler le code et générer le fichier de documentation</span><span class="sxs-lookup"><span data-stu-id="78d38-112">To compile the code and generate the documentation file</span></span>  
  
1.  <span data-ttu-id="78d38-113">Ajoutez l’option du compilateur **/doc** à la propriété <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> d’un objet <xref:System.CodeDom.Compiler.CompilerParameters> et passez l’objet à la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> pour créer le fichier de documentation XML quand le code est compilé.</span><span class="sxs-lookup"><span data-stu-id="78d38-113">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     <span data-ttu-id="78d38-114">[!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]  [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]</span><span class="sxs-lookup"><span data-stu-id="78d38-114">[!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]  [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="78d38-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="78d38-115">Example</span></span>  
 <span data-ttu-id="78d38-116">L’exemple de code suivant crée un graphique CodeDOM avec des commentaires de documentation, génère un fichier de code à partir du graphique, compile le fichier et crée un fichier de documentation XML associé.</span><span class="sxs-lookup"><span data-stu-id="78d38-116">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 <span data-ttu-id="78d38-117">[!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)] [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="78d38-117">[!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)] [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]</span></span>  
  
 <span data-ttu-id="78d38-118">L’exemple de code crée la documentation XML suivante dans le fichier HelloWorldDoc.xml.</span><span class="sxs-lookup"><span data-stu-id="78d38-118">The code example creates the following XML documentation in the HelloWorldDoc.xml file.</span></span>  
  
```xml  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="78d38-119">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="78d38-119">Compiling the Code</span></span>  
  
-   <span data-ttu-id="78d38-120">Cet exemple de code nécessite le jeu d’autorisations `FullTrust` pour s’exécuter correctement.</span><span class="sxs-lookup"><span data-stu-id="78d38-120">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78d38-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78d38-121">See Also</span></span>  
 <span data-ttu-id="78d38-122">[Documentation de votre code avec le langage XML](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span><span class="sxs-lookup"><span data-stu-id="78d38-122">[Documenting Your Code with XML](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span></span>  
 <span data-ttu-id="78d38-123">[Commentaires sur la documentation XML](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md) </span><span class="sxs-lookup"><span data-stu-id="78d38-123">[XML Documentation Comments](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md) </span></span>  
 [<span data-ttu-id="78d38-124">Documentation XML</span><span class="sxs-lookup"><span data-stu-id="78d38-124">XML Documentation</span></span>](/cpp/ide/xml-documentation-visual-cpp)

