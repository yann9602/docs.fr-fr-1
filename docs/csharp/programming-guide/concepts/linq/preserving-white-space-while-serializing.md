---
title: "Conservation des espaces blancs lors de la sérialisation3"
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
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eed3f2a2627fb5901692d67095efbdd5c874b54c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="60240-102">Conservation des espaces blancs lors de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="60240-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="60240-103">Cette rubrique décrit comment contrôler les espaces blancs lors de la sérialisation d'une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="60240-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="60240-104">Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d'espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="60240-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="60240-105">Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés.</span><span class="sxs-lookup"><span data-stu-id="60240-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="60240-106">Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60240-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="60240-107">Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="60240-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="60240-108">Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière.</span><span class="sxs-lookup"><span data-stu-id="60240-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="60240-109">Pour ce faire dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous devez conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.</span><span class="sxs-lookup"><span data-stu-id="60240-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="60240-110">Comportement d'espace blanc des méthodes qui sérialisent des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="60240-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="60240-111">Les méthodes suivantes dans les classes <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XDocument> sérialisent une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="60240-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="60240-112">Vous pouvez sérialiser une arborescence XML vers un fichier, un objet <xref:System.IO.TextReader> ou un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="60240-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="60240-113">La méthode `ToString` sérialise vers une chaîne.</span><span class="sxs-lookup"><span data-stu-id="60240-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=fullName>  
  
 <span data-ttu-id="60240-114">Si la méthode ne prend pas l'objet <xref:System.Xml.Linq.SaveOptions> comme argument, elle mettra en forme (en retrait) le code XML sérialisé.</span><span class="sxs-lookup"><span data-stu-id="60240-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="60240-115">Dans ce cas, tous les espaces blancs non significatifs dans l'arborescence XML seront ignorés.</span><span class="sxs-lookup"><span data-stu-id="60240-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="60240-116">Si la méthode prend l'objet <xref:System.Xml.Linq.SaveOptions> comme argument, vous pouvez spécifier qu'elle ne mettra pas en forme (en retrait) le code XML sérialisé.</span><span class="sxs-lookup"><span data-stu-id="60240-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="60240-117">Dans ce cas, tous les espaces blancs dans l’arborescence XML seront conservés.</span><span class="sxs-lookup"><span data-stu-id="60240-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60240-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60240-118">See Also</span></span>  
 [<span data-ttu-id="60240-119">Sérialisation d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="60240-119">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)

