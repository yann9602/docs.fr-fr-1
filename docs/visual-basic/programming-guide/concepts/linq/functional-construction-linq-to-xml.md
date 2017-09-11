---
title: Construction fonctionnelle (LINQ to XML) (Visual Basic) | Documents Microsoft
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
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
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
ms.openlocfilehash: b88b67aca337b893f9f276c8e4a6589b6946069b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="72c4a-102">Construction fonctionnelle (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72c4a-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="72c4a-103">fournit un moyen puissant de créer des éléments XML appelé *construction fonctionnelle*.</span><span class="sxs-lookup"><span data-stu-id="72c4a-103"> provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="72c4a-104">La construction fonctionnelle est la capacité à créer une arborescence XML en une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="72c4a-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="72c4a-105">Plusieurs fonctionnalités clés de l'interface de programmation [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] autorisent la construction fonctionnelle :</span><span class="sxs-lookup"><span data-stu-id="72c4a-105">There are several key features of the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="72c4a-106">Le <xref:System.Xml.Linq.XElement>constructeur prend différents types d’arguments comme contenu.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="72c4a-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="72c4a-107">Par exemple, vous pouvez passer à un autre <xref:System.Xml.Linq.XElement>objet, qui devient un élément enfant.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="72c4a-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="72c4a-108">Vous pouvez passer un <xref:System.Xml.Linq.XAttribute>objet, qui devient un attribut de l’élément.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="72c4a-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="72c4a-109">Ou vous pouvez passer tout autre type d'objet, qui est converti en chaîne et devient le contenu texte de l'élément.</span><span class="sxs-lookup"><span data-stu-id="72c4a-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="72c4a-110">Le <xref:System.Xml.Linq.XElement>constructeur prend un `params` tableau de type <xref:System.Object>, de sorte que vous puissiez passer toute quantité d’objets au constructeur.</xref:System.Object> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="72c4a-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="72c4a-111">Cela vous permet de créer un élément dont le contenu est complexe.</span><span class="sxs-lookup"><span data-stu-id="72c4a-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="72c4a-112">Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l’objet est énumérée et tous les éléments dans la collection sont ajoutés.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="72c4a-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="72c4a-113">Si la collection contient <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>des objets, chaque élément de la collection est ajouté séparément.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="72c4a-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="72c4a-114">Ceci est important car il vous permet de transmettre les résultats d’une [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requête au constructeur.</span><span class="sxs-lookup"><span data-stu-id="72c4a-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="72c4a-115">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="72c4a-115">The following is an example:</span></span>  
  
 <span data-ttu-id="72c4a-116">Ces fonctionnalités vous permettent d’écrire du code à l’aide de littéraux XML pour créer une arborescence XML et également d’écrire du code qui utilise les résultats de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requêtes lorsque vous créez une arborescence XML :</span><span class="sxs-lookup"><span data-stu-id="72c4a-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries when you create an XML tree:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="72c4a-117">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="72c4a-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72c4a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72c4a-118">See Also</span></span>  
 [<span data-ttu-id="72c4a-119">Création d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72c4a-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
