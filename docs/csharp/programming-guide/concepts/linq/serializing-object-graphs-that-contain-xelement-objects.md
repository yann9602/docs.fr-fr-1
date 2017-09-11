---
title: "Sérialisation de graphiques d’objets qui contiennent des objets XElement (C#)"
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
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
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
ms.openlocfilehash: 4e7b1d6365eb27596477de39577caa4144aa3501
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="e13ea-102">Sérialisation de graphiques d’objets qui contiennent des objets XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="e13ea-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="e13ea-103">Cette rubrique présente la fonctionnalité de sérialisation de graphiques d'objets qui contiennent des références à des objets de type <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e13ea-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="e13ea-104">Afin de faciliter ce type de sérialisation, <xref:System.Xml.Linq.XElement> implémente l'interface <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="e13ea-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="e13ea-105">Notez que seule la classe <xref:System.Xml.Linq.XElement> implémente la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="e13ea-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e13ea-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e13ea-106">In This Section</span></span>  
  
|<span data-ttu-id="e13ea-107">Rubrique</span><span class="sxs-lookup"><span data-stu-id="e13ea-107">Topic</span></span>|<span data-ttu-id="e13ea-108">Description</span><span class="sxs-lookup"><span data-stu-id="e13ea-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e13ea-109">Guide pratique pour sérialiser à l’aide de XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="e13ea-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="e13ea-110">Montre comment sérialiser à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e13ea-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="e13ea-111">Guide pratique pour sérialiser à l’aide de DataContractSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="e13ea-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="e13ea-112">Montre comment sérialiser à l'aide de <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e13ea-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e13ea-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e13ea-113">See Also</span></span>  
 [<span data-ttu-id="e13ea-114">Programmation LINQ to XML avancée (C#)</span><span class="sxs-lookup"><span data-stu-id="e13ea-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

