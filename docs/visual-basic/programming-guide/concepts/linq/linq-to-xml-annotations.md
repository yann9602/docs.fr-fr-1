---
title: LINQ to XML Annotations2 | Documents Microsoft
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
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 97f5386630ba687e4401ee0cfb70f7170e273a53
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="e176e-102">Annotations LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="e176e-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="e176e-103">Annotations dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] vous permettent d’associer n’importe quel objet arbitraire de n’importe quel type arbitraire avec n’importe quel composant XML dans une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="e176e-103">Annotations in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="e176e-104">Pour ajouter une annotation à un composant XML, tel qu’un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>, vous appelez le <xref:System.Xml.Linq.XObject.AddAnnotation%2A>méthode.</xref:System.Xml.Linq.XObject.AddAnnotation%2A> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="e176e-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="e176e-105">Vous pouvez récupérer des annotations par type.</span><span class="sxs-lookup"><span data-stu-id="e176e-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="e176e-106">Notez que les annotations ne font pas partie du jeu d'informations XML ; elles ne sont pas sérialisées ou désérialisées.</span><span class="sxs-lookup"><span data-stu-id="e176e-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e176e-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e176e-107">Methods</span></span>  
 <span data-ttu-id="e176e-108">Vous pouvez utiliser les méthodes suivantes lorsque vous travaillez avec des annotations :</span><span class="sxs-lookup"><span data-stu-id="e176e-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="e176e-109">Méthode</span><span class="sxs-lookup"><span data-stu-id="e176e-109">Method</span></span>|<span data-ttu-id="e176e-110">Description</span><span class="sxs-lookup"><span data-stu-id="e176e-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e176e-111"><xref:System.Xml.Linq.XObject.AddAnnotation%2A></xref:System.Xml.Linq.XObject.AddAnnotation%2A></span><span class="sxs-lookup"><span data-stu-id="e176e-111"><xref:System.Xml.Linq.XObject.AddAnnotation%2A></span></span>|<span data-ttu-id="e176e-112">Ajoute un objet à la liste d’annotation d’un <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="e176e-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="e176e-113"><xref:System.Xml.Linq.XObject.Annotation%2A></xref:System.Xml.Linq.XObject.Annotation%2A></span><span class="sxs-lookup"><span data-stu-id="e176e-113"><xref:System.Xml.Linq.XObject.Annotation%2A></span></span>|<span data-ttu-id="e176e-114">Obtient le premier objet annotation du type spécifié à partir d’un <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="e176e-114">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="e176e-115"><xref:System.Xml.Linq.XObject.Annotations%2A></xref:System.Xml.Linq.XObject.Annotations%2A></span><span class="sxs-lookup"><span data-stu-id="e176e-115"><xref:System.Xml.Linq.XObject.Annotations%2A></span></span>|<span data-ttu-id="e176e-116">Obtient une collection d’annotations du type spécifié pour un <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="e176e-116">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="e176e-117"><xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></span><span class="sxs-lookup"><span data-stu-id="e176e-117"><xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></span></span>|<span data-ttu-id="e176e-118">Supprime les annotations du type spécifié à partir d’un <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="e176e-118">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e176e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e176e-119">See Also</span></span>  
 [<span data-ttu-id="e176e-120">LINQ to XML (Visual Basic) de la programmation avancée</span><span class="sxs-lookup"><span data-stu-id="e176e-120">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
