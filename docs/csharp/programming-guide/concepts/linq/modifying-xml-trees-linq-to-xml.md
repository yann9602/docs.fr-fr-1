---
title: "Modification d’arborescences XML (LINQ to XML) (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 8ec47e6d-2363-4694-be46-8d5ca4d15fc9
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0cb4ff851dbea97f254d5290ce021d560849e3d9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="modifying-xml-trees-linq-to-xml-c"></a><span data-ttu-id="c5b9a-102">Modification d’arborescences XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c5b9a-102">Modifying XML Trees (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c5b9a-103"> est un magasin en mémoire pour une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="c5b9a-103"> is an in-memory store for an XML tree.</span></span> <span data-ttu-id="c5b9a-104">Une fois que vous avez chargé ou analysé une arborescence XML à partir d’une source, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vous permet de modifier cette arborescence sur place, puis de la sérialiser, par exemple en l’enregistrant dans un fichier ou en l’envoyant vers un serveur distant.</span><span class="sxs-lookup"><span data-stu-id="c5b9a-104">After you load or parse an XML tree from a source, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] lets you modify that tree in place, and then serialize the tree, perhaps saving it to a file or sending it to a remote server.</span></span>  
  
 <span data-ttu-id="c5b9a-105">Lorsque vous modifiez une arborescence sur place, vous utilisez certaines méthodes, telles que <xref:System.Xml.Linq.XContainer.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5b9a-105">When you modify a tree in place, you use certain methods, such as <xref:System.Xml.Linq.XContainer.Add%2A>.</span></span>  
  
 <span data-ttu-id="c5b9a-106">Il existe cependant une autre approche, qui consiste à utiliser la construction fonctionnelle pour générer une nouvelle arborescence avec une forme différente.</span><span class="sxs-lookup"><span data-stu-id="c5b9a-106">However, there is another approach, which is to use functional construction to generate a new tree with a different shape.</span></span> <span data-ttu-id="c5b9a-107">Cette approche peut s'avérer plus robuste et plus facile à développer, selon les types de modifications que vous devez apporter à votre arborescence XML et selon la taille de l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="c5b9a-107">Depending on the types of changes that you need to make to your XML tree, and depending on the size of the tree, this approach can be more robust and easier to develop.</span></span> <span data-ttu-id="c5b9a-108">La première rubrique dans cette section compare ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="c5b9a-108">The first topic in this section compares these two approaches.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5b9a-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c5b9a-109">In This Section</span></span>  
  
|<span data-ttu-id="c5b9a-110">Rubrique</span><span class="sxs-lookup"><span data-stu-id="c5b9a-110">Topic</span></span>|<span data-ttu-id="c5b9a-111">Description</span><span class="sxs-lookup"><span data-stu-id="c5b9a-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c5b9a-112">Comparaison de la modification d’arborescence XML en mémoire et de la Construction fonctionnelle (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c5b9a-112">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)|<span data-ttu-id="c5b9a-113">Compare la modification d’une arborescence XML en mémoire à la construction fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="c5b9a-113">Compares modifying an XML tree in memory to functional construction.</span></span>|  
|[<span data-ttu-id="c5b9a-114">Ajout d’éléments, d’attributs et de nœuds à une arborescence XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c5b9a-114">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|<span data-ttu-id="c5b9a-115">Fournit des informations sur l’ajout d’éléments, d’attributs ou de nœuds à une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="c5b9a-115">Provides information about adding elements, attributes, or nodes to an XML tree.</span></span>|  
|[<span data-ttu-id="c5b9a-116">Modification d’éléments, d’attributs et de nœuds dans une arborescence XML</span><span class="sxs-lookup"><span data-stu-id="c5b9a-116">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|<span data-ttu-id="c5b9a-117">Fournit des informations sur la modification d'éléments, d'attributs ou de nœuds existants.</span><span class="sxs-lookup"><span data-stu-id="c5b9a-117">Provides information about modifying existing elements, attributes, or nodes.</span></span>|  
|[<span data-ttu-id="c5b9a-118">Suppression d’éléments, d’attributs et de nœuds d’une arborescence XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c5b9a-118">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|<span data-ttu-id="c5b9a-119">Fournit des informations sur la suppression d’éléments, d’attributs ou de nœuds d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="c5b9a-119">Provides information about removing elements, attributes, or nodes from the XML tree.</span></span>|  
|[<span data-ttu-id="c5b9a-120">Gestion des paires nom/valeur (C#)</span><span class="sxs-lookup"><span data-stu-id="c5b9a-120">Maintaining Name/Value Pairs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|<span data-ttu-id="c5b9a-121">Décrit comment maintenir des informations d'applications qu'il est préférable de conserver sous la forme de paires nom/valeur, telles que des informations de configuration ou des paramètres globaux.</span><span class="sxs-lookup"><span data-stu-id="c5b9a-121">Describes how to maintain application information that is best kept as name/value pairs, such as configuration information or global settings.</span></span>|  
|[<span data-ttu-id="c5b9a-122">Guide pratique pour modifier l’espace de noms pour toute une arborescence XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c5b9a-122">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|<span data-ttu-id="c5b9a-123">Montre comment déplacer une arborescence XML d’un espace de noms à un autre.</span><span class="sxs-lookup"><span data-stu-id="c5b9a-123">Shows how to move an XML tree from one namespace into another.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5b9a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5b9a-124">See Also</span></span>  
 [<span data-ttu-id="c5b9a-125">Guide de programmation (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c5b9a-125">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

