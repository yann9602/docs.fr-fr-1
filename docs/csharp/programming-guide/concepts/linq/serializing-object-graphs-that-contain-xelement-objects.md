---
title: "Sérialisation de graphiques d’objets qui contiennent des objets XElement (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b7da4429360beb20fa304b592020d48666fe732
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="6c7ac-102">Sérialisation de graphiques d’objets qui contiennent des objets XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="6c7ac-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="6c7ac-103">Cette rubrique présente la fonctionnalité de sérialisation de graphiques d'objets qui contiennent des références à des objets de type <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="6c7ac-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="6c7ac-104">Afin de faciliter ce type de sérialisation, <xref:System.Xml.Linq.XElement> implémente l'interface <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="6c7ac-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="6c7ac-105">Notez que seule la classe <xref:System.Xml.Linq.XElement> implémente la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="6c7ac-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c7ac-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6c7ac-106">In This Section</span></span>  
  
|<span data-ttu-id="6c7ac-107">Rubrique</span><span class="sxs-lookup"><span data-stu-id="6c7ac-107">Topic</span></span>|<span data-ttu-id="6c7ac-108">Description</span><span class="sxs-lookup"><span data-stu-id="6c7ac-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6c7ac-109">Guide pratique pour sérialiser à l’aide de XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="6c7ac-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="6c7ac-110">Montre comment sérialiser à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6c7ac-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="6c7ac-111">Guide pratique pour sérialiser à l’aide de DataContractSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="6c7ac-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="6c7ac-112">Montre comment sérialiser à l'aide de <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6c7ac-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c7ac-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c7ac-113">See Also</span></span>  
 [<span data-ttu-id="6c7ac-114">Programmation LINQ to XML avancée (C#)</span><span class="sxs-lookup"><span data-stu-id="6c7ac-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
