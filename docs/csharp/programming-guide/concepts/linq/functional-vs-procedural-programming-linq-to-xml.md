---
title: "Comparaison entre la programmation fonctionnelle Programmation procédurale (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b6aa8ce45afdb68f7ff544b8c8f2f5e1e4a79533
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="0e173-102">Comparaison entre la programmation fonctionnelle Programmation procédurale (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0e173-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0e173-103">Il existe différents types d'applications XML :</span><span class="sxs-lookup"><span data-stu-id="0e173-103">There are various types of XML applications:</span></span>  
  
-   <span data-ttu-id="0e173-104">Certaines applications prennent des documents XML sources et produisent de nouveaux documents XML d'une forme différente des documents sources.</span><span class="sxs-lookup"><span data-stu-id="0e173-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
-   <span data-ttu-id="0e173-105">Certaines applications prennent des documents XML sources et produisent des documents d'une forme totalement différente, tels que des fichiers texte CSV ou HTML.</span><span class="sxs-lookup"><span data-stu-id="0e173-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
-   <span data-ttu-id="0e173-106">Certaines applications prennent des documents XML sources et insèrent des enregistrements dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="0e173-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
-   <span data-ttu-id="0e173-107">Certaines applications prennent des données à partir d'une autre source, telle qu'une base de données, et créent des documents XML à partir de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="0e173-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="0e173-108">Il existe d'autres types d'applications XML, mais ceux-ci sont représentatifs des types de fonctionnalités qu'un programmateur XML doit implémenter.</span><span class="sxs-lookup"><span data-stu-id="0e173-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="0e173-109">Avec tous ces types d'applications, un développeur peut suivre deux approches contrastées :</span><span class="sxs-lookup"><span data-stu-id="0e173-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
-   <span data-ttu-id="0e173-110">Construction fonctionnelle à l'aide d'une approche déclarative.</span><span class="sxs-lookup"><span data-stu-id="0e173-110">Functional construction using a declarative approach.</span></span>  
  
-   <span data-ttu-id="0e173-111">Modification d'arborescence XML en mémoire à l'aide de procédures de code.</span><span class="sxs-lookup"><span data-stu-id="0e173-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="0e173-112">LINQ to XML prend en charge les deux approches.</span><span class="sxs-lookup"><span data-stu-id="0e173-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="0e173-113">Lors de l'utilisation de l'approche fonctionnelle, vous écrivez des transformations qui prennent les documents sources et génèrent des documents de résultats complètement nouveaux de la forme souhaitée.</span><span class="sxs-lookup"><span data-stu-id="0e173-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="0e173-114">Lors de la modification d'une arborescence XML en place, vous écrivez du code qui traverse et parcourt les nœuds d'une arborescence XML en mémoire, en insérant, supprimant et modifiant des nœuds si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0e173-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="0e173-115">Vous pouvez utiliser LINQ to XML avec l'une ou l'autre de ces approches.</span><span class="sxs-lookup"><span data-stu-id="0e173-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="0e173-116">Vous utilisez les mêmes classes et, dans certains cas, les mêmes méthodes.</span><span class="sxs-lookup"><span data-stu-id="0e173-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="0e173-117">Toutefois, la structure et les objectifs des deux approches sont très différents.</span><span class="sxs-lookup"><span data-stu-id="0e173-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="0e173-118">Par exemple, dans différentes situations, l'une ou l'autre approche fournira souvent de meilleures performances et utilisera plus ou moins de mémoire.</span><span class="sxs-lookup"><span data-stu-id="0e173-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="0e173-119">En outre, l'une ou l'autre approche sera plus facile à écrire et génèrera du code plus facile à maintenir.</span><span class="sxs-lookup"><span data-stu-id="0e173-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="0e173-120">Pour voir une comparaison de ces deux approches, consultez [Comparaison de la modification d’arborescence XML en mémoire et de la construction fonctionnelle (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0e173-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="0e173-121">Pour obtenir un didacticiel sur l’écriture de transformations fonctionnelles, consultez [Transformations fonctionnelles pures de données XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0e173-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e173-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e173-122">See Also</span></span>  
 [<span data-ttu-id="0e173-123">Vue d’ensemble de la programmation LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0e173-123">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
