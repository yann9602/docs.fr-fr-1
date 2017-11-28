---
title: construction fonctionnelle (LINQ to XML) (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f357de98fae60b3d0b6548ef195b462b4e2f6a5a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="8b6c2-102">construction fonctionnelle (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8b6c2-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="8b6c2-103"> offre un moyen puissant de créer des éléments XML appelé *construction fonctionnelle*.</span><span class="sxs-lookup"><span data-stu-id="8b6c2-103"> provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="8b6c2-104">La construction fonctionnelle est la capacité à créer une arborescence XML en une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="8b6c2-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="8b6c2-105">Plusieurs fonctionnalités clés de l'interface de programmation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] autorisent la construction fonctionnelle :</span><span class="sxs-lookup"><span data-stu-id="8b6c2-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="8b6c2-106">Le constructeur <xref:System.Xml.Linq.XElement> prend différents types d'arguments comme contenu.</span><span class="sxs-lookup"><span data-stu-id="8b6c2-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="8b6c2-107">Par exemple, vous pouvez passer un autre objet <xref:System.Xml.Linq.XElement>, qui devient un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="8b6c2-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="8b6c2-108">Vous pouvez passer un objet <xref:System.Xml.Linq.XAttribute>, qui devient un attribut de l'élément.</span><span class="sxs-lookup"><span data-stu-id="8b6c2-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="8b6c2-109">Ou vous pouvez passer tout autre type d'objet, qui est converti en chaîne et devient le contenu texte de l'élément.</span><span class="sxs-lookup"><span data-stu-id="8b6c2-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="8b6c2-110">Le constructeur <xref:System.Xml.Linq.XElement> prend un tableau `params` de type <xref:System.Object>, de sorte que vous puissiez passer toute quantité d'objets au constructeur.</span><span class="sxs-lookup"><span data-stu-id="8b6c2-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="8b6c2-111">Cela vous permet de créer un élément dont le contenu est complexe.</span><span class="sxs-lookup"><span data-stu-id="8b6c2-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="8b6c2-112">Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l'objet est énumérée et tous les éléments de la collection sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="8b6c2-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="8b6c2-113">Si la collection contient des objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, chaque élément de la collection est ajouté séparément.</span><span class="sxs-lookup"><span data-stu-id="8b6c2-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="8b6c2-114">Ceci est important, car cela vous permet de passer les résultats d’une requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] au constructeur.</span><span class="sxs-lookup"><span data-stu-id="8b6c2-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="8b6c2-115">Ces fonctionnalités vous permettent d’écrire du code pour créer une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="8b6c2-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="8b6c2-116">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="8b6c2-116">The following is an example:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="8b6c2-117">Ces fonctionnalités permettent également d’écrire du code qui utilise les résultats de requêtes [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] lorsque vous créez une arborescence XML, comme suit :</span><span class="sxs-lookup"><span data-stu-id="8b6c2-117">These features also enable you to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree, as follows:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="8b6c2-118">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="8b6c2-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b6c2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b6c2-119">See Also</span></span>  
 [<span data-ttu-id="8b6c2-120">Création d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8b6c2-120">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
