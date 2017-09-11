---
title: "Comment : créer un Document avec des espaces de noms (LINQ to XML) (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 60206722fff1d10c8368cbdd24ec6ca15dd207be
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="74fe0-102">Comment : créer un document avec des espaces de noms (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74fe0-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="74fe0-103">Cette rubrique montre comment créer un document avec des espaces de noms dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="74fe0-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="74fe0-104">Lorsque vous utilisez des littéraux XML en Visual Basic, les utilisateurs peuvent définir un espace de noms XML global par défaut.</span><span class="sxs-lookup"><span data-stu-id="74fe0-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="74fe0-105">Cet espace de noms est l'espace de noms par défaut pour les littéraux XML et les propriétés XML.</span><span class="sxs-lookup"><span data-stu-id="74fe0-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="74fe0-106">L'espace de noms XML par défaut peut être défini au niveau projet ou au niveau fichier.</span><span class="sxs-lookup"><span data-stu-id="74fe0-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="74fe0-107">S'il est défini au niveau fichier, il remplace l'espace de noms par défaut défini au niveau projet.</span><span class="sxs-lookup"><span data-stu-id="74fe0-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="74fe0-108">Vous pouvez également définir d'autres espaces de noms et spécifier les préfixes d'espaces de noms de ces espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="74fe0-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="74fe0-109">Vous définissez les espaces de noms par défaut et les espaces de noms avec préfixe à l'aide du mot clé `Imports`.</span><span class="sxs-lookup"><span data-stu-id="74fe0-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="74fe0-110">Pour plus d’informations, consultez [Introduction aux littéraux XML en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="74fe0-110">For more information, see [Introduction to XML Literals in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="74fe0-111">Notez que l'espace de noms XML par défaut s'applique uniquement aux éléments, et non aux attributs.</span><span class="sxs-lookup"><span data-stu-id="74fe0-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="74fe0-112">Par défaut, les attributs ne sont jamais dans aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="74fe0-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="74fe0-113">Toutefois, vous pouvez utiliser un préfixe d'espace de noms pour placer un attribut dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="74fe0-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74fe0-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="74fe0-114">Example</span></span>  
 <span data-ttu-id="74fe0-115">Cet exemple crée un document qui contient un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="74fe0-115">This example creates a document that contains a namespace.</span></span>  
  
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
  
 <span data-ttu-id="74fe0-116">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="74fe0-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="74fe0-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="74fe0-117">Example</span></span>  
 <span data-ttu-id="74fe0-118">Cet exemple crée un document qui contient deux espaces de noms, dont l'un est l'espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="74fe0-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
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
  
 <span data-ttu-id="74fe0-119">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="74fe0-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="74fe0-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="74fe0-120">Example</span></span>  
 <span data-ttu-id="74fe0-121">L'exemple suivant crée un document qui contient plusieurs espaces de noms, tous deux avec des préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="74fe0-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="74fe0-122">Lors de la sérialisation d'une arborescence XML, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] émet des déclarations d'espaces de noms selon les besoins, de sorte que chaque élément soit dans son espace de noms désigné.</span><span class="sxs-lookup"><span data-stu-id="74fe0-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
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
  
 <span data-ttu-id="74fe0-123">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="74fe0-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74fe0-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74fe0-124">See Also</span></span>  
 [<span data-ttu-id="74fe0-125">Utilisation des espaces de noms XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74fe0-125">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
