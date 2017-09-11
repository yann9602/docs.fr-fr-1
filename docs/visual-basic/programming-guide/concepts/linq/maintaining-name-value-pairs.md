---
title: Maintenance de paires nom-valeur (Visual Basic) | Documents Microsoft
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
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 30e40c73430f385815b7a08a2507343db0fafd4f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="maintaining-namevalue-pairs-visual-basic"></a><span data-ttu-id="0fc84-102">Maintenance de paires nom/valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fc84-102">Maintaining Name/Value Pairs (Visual Basic)</span></span>
<span data-ttu-id="0fc84-103">De nombreuses applications doivent maintenir des informations qu'il est préférable de conserver sous forme de paires nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="0fc84-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="0fc84-104">Il peut s'agir d'informations de configuration ou de paramètres globaux.</span><span class="sxs-lookup"><span data-stu-id="0fc84-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="0fc84-105"> contient des méthodes qui facilitent la maintenance d'un ensemble de paires nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="0fc84-105"> contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="0fc84-106">Vous pouvez conserver les informations en tant qu'attributs ou en tant qu'ensemble d'éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="0fc84-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="0fc84-107">L'une des différences est qu'il ne peut y avoir qu'un seul attribut avec un nom donné pour un élément.</span><span class="sxs-lookup"><span data-stu-id="0fc84-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="0fc84-108">Cette limitation ne s'applique pas aux éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="0fc84-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="0fc84-109">SetAttributeValue et SetElementValue</span><span class="sxs-lookup"><span data-stu-id="0fc84-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="0fc84-110">Les deux méthodes qui facilitent la conservation nom/valeur sont de paires <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>et <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</xref:System.Xml.Linq.XElement.SetElementValue%2A> </xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="0fc84-111">Ces deux méthodes ont une sémantique similaire.</span><span class="sxs-lookup"><span data-stu-id="0fc84-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="0fc84-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>peut ajouter, modifier ou supprimer des attributs d’un élément.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
-   <span data-ttu-id="0fc84-113">Si vous appelez <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>avec un nom d’un attribut qui n’existe pas, la méthode crée un nouvel attribut et l’ajoute à l’élément spécifié.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="0fc84-114">Si vous appelez <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>avec un nom d’un attribut existant et avec certains spécifié le contenu, le contenu de l’attribut est remplacé par le contenu spécifié.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="0fc84-115">Si vous appelez <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>avec un nom d’un attribut et spécifiez null pour le contenu, l’attribut est supprimé de son parent.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="0fc84-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A>peut ajouter, modifier ou supprimer des éléments enfants d’un élément.</xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
-   <span data-ttu-id="0fc84-117">Si vous appelez <xref:System.Xml.Linq.XElement.SetElementValue%2A>avec un nom d’un élément enfant qui n’existe pas, la méthode crée un nouvel élément et l’ajoute à l’élément spécifié.</xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="0fc84-118">Si vous appelez <xref:System.Xml.Linq.XElement.SetElementValue%2A>avec un nom d’un élément existant et avec certains spécifié le contenu, le contenu de l’élément est remplacé par le contenu spécifié.</xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="0fc84-119">Si vous appelez <xref:System.Xml.Linq.XElement.SetElementValue%2A>avec un nom d’un élément existant et spécifiez une valeur null pour le contenu, l’élément est supprimé de son parent.</xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fc84-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="0fc84-120">Example</span></span>  
 <span data-ttu-id="0fc84-121">L'exemple suivant crée un élément sans attribut.</span><span class="sxs-lookup"><span data-stu-id="0fc84-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="0fc84-122">Il utilise ensuite le <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>pour créer et gérer une liste de paires nom/valeur.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22)  
root.SetAttributeValue("Left", 20)  
root.SetAttributeValue("Bottom", 122)  
root.SetAttributeValue("Right", 300)  
root.SetAttributeValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
  
' Replace the value of Top.  
root.SetAttributeValue("Top", 10)  
Console.WriteLine(root)  
  
' Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="0fc84-123">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0fc84-123">This example produces the following output:</span></span>  
  
```  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="0fc84-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="0fc84-124">Example</span></span>  
 <span data-ttu-id="0fc84-125">L'exemple suivant crée un élément sans élément enfant.</span><span class="sxs-lookup"><span data-stu-id="0fc84-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="0fc84-126">Il utilise ensuite le <xref:System.Xml.Linq.XElement.SetElementValue%2A>pour créer et gérer une liste de paires nom/valeur.</xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22)  
root.SetElementValue("Left", 20)  
root.SetElementValue("Bottom", 122)  
root.SetElementValue("Right", 300)  
root.SetElementValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Replace the value of Top.  
root.SetElementValue("Top", 10)  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Remove DefaultColor.  
root.SetElementValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
  
```  
  
 <span data-ttu-id="0fc84-127">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0fc84-127">This example produces the following output:</span></span>  
  
```  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fc84-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fc84-128">See Also</span></span>  
 <span data-ttu-id="0fc84-129"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A></xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-129"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span></span>   
 <span data-ttu-id="0fc84-130"><xref:System.Xml.Linq.XElement.SetElementValue%2A></xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="0fc84-130"><xref:System.Xml.Linq.XElement.SetElementValue%2A></span></span>   
<span data-ttu-id="0fc84-131"> [Modification d’arborescences XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="0fc84-131"> [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)</span></span>
