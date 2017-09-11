---
title: "Ajout d’éléments, attributs et nœuds à une arborescence XML (Visual Basic) | Documents Microsoft"
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
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f8ee26aef896a2f404e815823ade83e204270613
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a><span data-ttu-id="aea00-102">Ajout d’éléments, attributs et nœuds à une arborescence XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aea00-102">Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="aea00-103">Vous pouvez ajouter du contenu (éléments, attributs, commentaires, instructions de traitement, texte et CData) à une arborescence XML existante.</span><span class="sxs-lookup"><span data-stu-id="aea00-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="aea00-104">Méthodes pour ajouter du contenu</span><span class="sxs-lookup"><span data-stu-id="aea00-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="aea00-105">Les méthodes suivantes ajoutent du contenu enfant à un <xref:System.Xml.Linq.XElement>ou un <xref:System.Xml.Linq.XDocument>:</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="aea00-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="aea00-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="aea00-106">Method</span></span>|<span data-ttu-id="aea00-107">Description</span><span class="sxs-lookup"><span data-stu-id="aea00-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="aea00-108"><xref:System.Xml.Linq.XContainer.Add%2A></xref:System.Xml.Linq.XContainer.Add%2A></span><span class="sxs-lookup"><span data-stu-id="aea00-108"><xref:System.Xml.Linq.XContainer.Add%2A></span></span>|<span data-ttu-id="aea00-109">Ajoute du contenu à la fin du contenu enfant de l’élément <xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="aea00-109">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<span data-ttu-id="aea00-110"><xref:System.Xml.Linq.XContainer.AddFirst%2A></xref:System.Xml.Linq.XContainer.AddFirst%2A></span><span class="sxs-lookup"><span data-stu-id="aea00-110"><xref:System.Xml.Linq.XContainer.AddFirst%2A></span></span>|<span data-ttu-id="aea00-111">Ajoute du contenu au début du contenu enfant de l’élément <xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="aea00-111">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="aea00-112">Les méthodes suivantes ajoutent du contenu en tant que nœuds frères d’un <xref:System.Xml.Linq.XNode>.</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="aea00-112">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="aea00-113">Le nœud le plus courant auquel vous ajoutez du contenu frère est <xref:System.Xml.Linq.XElement>, bien que vous pouvez ajouter du contenu frère valide à d’autres types de nœuds tels que <xref:System.Xml.Linq.XText>ou <xref:System.Xml.Linq.XComment>.</xref:System.Xml.Linq.XComment> </xref:System.Xml.Linq.XText> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="aea00-113">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="aea00-114">Méthode</span><span class="sxs-lookup"><span data-stu-id="aea00-114">Method</span></span>|<span data-ttu-id="aea00-115">Description</span><span class="sxs-lookup"><span data-stu-id="aea00-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="aea00-116"><xref:System.Xml.Linq.XNode.AddAfterSelf%2A></xref:System.Xml.Linq.XNode.AddAfterSelf%2A></span><span class="sxs-lookup"><span data-stu-id="aea00-116"><xref:System.Xml.Linq.XNode.AddAfterSelf%2A></span></span>|<span data-ttu-id="aea00-117">Ajoute du contenu après le <xref:System.Xml.Linq.XNode>.</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="aea00-117">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<span data-ttu-id="aea00-118"><xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></span><span class="sxs-lookup"><span data-stu-id="aea00-118"><xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></span></span>|<span data-ttu-id="aea00-119">Ajoute du contenu avant le <xref:System.Xml.Linq.XNode>.</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="aea00-119">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aea00-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="aea00-120">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="aea00-121">Description</span><span class="sxs-lookup"><span data-stu-id="aea00-121">Description</span></span>  
 <span data-ttu-id="aea00-122">L'exemple suivant crée deux arborescences XML, puis modifie l'une des arborescences.</span><span class="sxs-lookup"><span data-stu-id="aea00-122">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="aea00-123">Code</span><span class="sxs-lookup"><span data-stu-id="aea00-123">Code</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element1>1</Element1>  
        <Element2>2</Element2>  
        <Element3>3</Element3>  
        <Element4>4</Element4>  
        <Element5>5</Element5>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child2>2</Child2>  
        <Child3>3</Child3>  
        <Child4>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
xmlTree.Add(<NewChild>new content</NewChild>)  
xmlTree.Add( _  
    From el In srcTree.Elements() _  
    Where CInt(el) > 3 _  
    Select el)  
  
' Even though Child9 does not exist in srcTree, the following statement  
' will not throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"))  
Console.WriteLine(xmlTree)  
  
```  
  
### <a name="comments"></a><span data-ttu-id="aea00-124">Commentaires</span><span class="sxs-lookup"><span data-stu-id="aea00-124">Comments</span></span>  
 <span data-ttu-id="aea00-125">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="aea00-125">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aea00-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aea00-126">See Also</span></span>  
 [<span data-ttu-id="aea00-127">Modification d’arborescences XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aea00-127">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
