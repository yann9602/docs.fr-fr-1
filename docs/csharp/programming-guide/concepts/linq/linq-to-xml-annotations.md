---
title: Annotations LINQ to XML3
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
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3fa8715deac8776f7a512439ee055be6faf4649f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="39db2-102">Annotations LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="39db2-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="39db2-103">Les annotations dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vous permettent d’associer n’importe quel objet arbitraire de n’importe quel type arbitraire à n’importe quel composant XML dans une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="39db2-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="39db2-104">Pour ajouter une annotation à un composant XML, tel qu'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, vous appelez la méthode <xref:System.Xml.Linq.XObject.AddAnnotation%2A>.</span><span class="sxs-lookup"><span data-stu-id="39db2-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="39db2-105">Vous pouvez récupérer des annotations par type.</span><span class="sxs-lookup"><span data-stu-id="39db2-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="39db2-106">Notez que les annotations ne font pas partie du jeu d'informations XML ; elles ne sont pas sérialisées ou désérialisées.</span><span class="sxs-lookup"><span data-stu-id="39db2-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39db2-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="39db2-107">Methods</span></span>  
 <span data-ttu-id="39db2-108">Vous pouvez utiliser les méthodes suivantes lorsque vous travaillez avec des annotations :</span><span class="sxs-lookup"><span data-stu-id="39db2-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="39db2-109">Méthode</span><span class="sxs-lookup"><span data-stu-id="39db2-109">Method</span></span>|<span data-ttu-id="39db2-110">Description</span><span class="sxs-lookup"><span data-stu-id="39db2-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="39db2-111">Ajoute un objet à la liste d'annotation de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="39db2-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="39db2-112">Obtient le premier objet annotation du type spécifié de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="39db2-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="39db2-113">Obtient une collection d'annotations du type spécifié pour un objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="39db2-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="39db2-114">Supprime les annotations du type spécifié d’un objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="39db2-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39db2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39db2-115">See Also</span></span>  
 [<span data-ttu-id="39db2-116">Programmation LINQ to XML avancée (C#)</span><span class="sxs-lookup"><span data-stu-id="39db2-116">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

