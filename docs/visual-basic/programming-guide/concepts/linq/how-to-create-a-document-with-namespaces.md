---
title: "Comment : créer un document avec des espaces de noms (LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 038e2924603eba7250620bc2792ec87b8e978787
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="2ad45-102">Comment : créer un document avec des espaces de noms (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ad45-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="2ad45-103">Cette rubrique montre comment créer un document avec des espaces de noms dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2ad45-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="2ad45-104">Lorsque vous utilisez des littéraux XML en Visual Basic, les utilisateurs peuvent définir un espace de noms XML global par défaut.</span><span class="sxs-lookup"><span data-stu-id="2ad45-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="2ad45-105">Cet espace de noms est l'espace de noms par défaut pour les littéraux XML et les propriétés XML.</span><span class="sxs-lookup"><span data-stu-id="2ad45-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="2ad45-106">L'espace de noms XML par défaut peut être défini au niveau projet ou au niveau fichier.</span><span class="sxs-lookup"><span data-stu-id="2ad45-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="2ad45-107">S'il est défini au niveau fichier, il remplace l'espace de noms par défaut défini au niveau projet.</span><span class="sxs-lookup"><span data-stu-id="2ad45-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="2ad45-108">Vous pouvez également définir d'autres espaces de noms et spécifier les préfixes d'espaces de noms de ces espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="2ad45-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="2ad45-109">Vous définissez les espaces de noms par défaut et les espaces de noms avec préfixe à l'aide du mot clé `Imports`.</span><span class="sxs-lookup"><span data-stu-id="2ad45-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="2ad45-110">Pour plus d’informations, consultez [Introduction aux littéraux XML en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="2ad45-110">For more information, see [Introduction to XML Literals in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="2ad45-111">Notez que l'espace de noms XML par défaut s'applique uniquement aux éléments, et non aux attributs.</span><span class="sxs-lookup"><span data-stu-id="2ad45-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="2ad45-112">Par défaut, les attributs ne sont jamais dans aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2ad45-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="2ad45-113">Toutefois, vous pouvez utiliser un préfixe d'espace de noms pour placer un attribut dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2ad45-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ad45-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ad45-114">Example</span></span>  
 <span data-ttu-id="2ad45-115">Cet exemple crée un document qui contient un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2ad45-115">This example creates a document that contains a namespace.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child aw:Att="attvalue"/>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="2ad45-116">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2ad45-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="2ad45-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ad45-117">Example</span></span>  
 <span data-ttu-id="2ad45-118">Cet exemple crée un document qui contient deux espaces de noms, dont l'un est l'espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="2ad45-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child Att="attvalue"/>  
                <fc:Child2>child2 content</fc:Child2>  
            </Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="2ad45-119">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2ad45-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="2ad45-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ad45-120">Example</span></span>  
 <span data-ttu-id="2ad45-121">L'exemple suivant crée un document qui contient plusieurs espaces de noms, tous deux avec des préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="2ad45-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="2ad45-122">Lors de la sérialisation d'une arborescence XML, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] émet des déclarations d'espaces de noms selon les besoins, de sorte que chaque élément soit dans son espace de noms désigné.</span><span class="sxs-lookup"><span data-stu-id="2ad45-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="2ad45-123">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2ad45-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ad45-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ad45-124">See Also</span></span>  
 [<span data-ttu-id="2ad45-125">Utilisation des espaces de noms XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ad45-125">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
