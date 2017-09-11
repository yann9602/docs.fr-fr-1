---
title: "Procédure : diffuser des fragments XML en continu à partir d’un XmlReader (Visual Basic) | Documents Microsoft"
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
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c9c60bb4730ef6569390f76f63c40a2cbd1c9524
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="6a9df-102">Procédure : diffuser des fragments XML en continu à partir d’un XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a9df-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="6a9df-103">Lorsque vous devez traiter de grands fichiers XML, il peut être impossible de charger l’intégralité de l’arborescence XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="6a9df-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="6a9df-104">Cette rubrique montre comment diffuser des fragments à l’aide d’un <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="6a9df-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="6a9df-105">Une des méthodes plus efficaces d’utiliser un <xref:System.Xml.XmlReader>pour lire <xref:System.Xml.Linq.XElement>objets consiste à écrire votre propre méthode d’axe personnalisée.</xref:System.Xml.Linq.XElement> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="6a9df-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="6a9df-106">Une méthode d’axe retourne généralement une collection telle que <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>, comme illustré dans l’exemple dans cette rubrique.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="6a9df-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="6a9df-107">Dans la méthode d’axe personnalisée, après avoir créé le fragment XML en appelant le <xref:System.Xml.Linq.XNode.ReadFrom%2A>(méthode), retourner la collection à l’aide `yield return`.</xref:System.Xml.Linq.XNode.ReadFrom%2A></span><span class="sxs-lookup"><span data-stu-id="6a9df-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="6a9df-108">Cela fournit une sémantique d'exécution différée à votre méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="6a9df-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="6a9df-109">Lorsque vous créez une arborescence XML à partir d’un <xref:System.Xml.XmlReader>objet, la <xref:System.Xml.XmlReader>doit être positionné sur un élément.</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="6a9df-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="6a9df-110">Le <xref:System.Xml.Linq.XNode.ReadFrom%2A>méthode ne retourne pas jusqu'à ce qu’il a lu la balise de fermeture de l’élément.</xref:System.Xml.Linq.XNode.ReadFrom%2A></span><span class="sxs-lookup"><span data-stu-id="6a9df-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="6a9df-111">Si vous souhaitez créer une arborescence partielle, vous pouvez instancier un <xref:System.Xml.XmlReader>, positionnez le lecteur sur le nœud que vous souhaitez convertir en un <xref:System.Xml.Linq.XElement>de l’arborescence, puis créer la <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="6a9df-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="6a9df-112">La rubrique [procédure : diffuser des fragments XML en continu avec accès aux informations d’en-tête (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contient des informations et un exemple sur la diffusion en continu un document plus complexe.</span><span class="sxs-lookup"><span data-stu-id="6a9df-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="6a9df-113">La rubrique [Comment : effectuer de diffusion en continu transformer des Documents XML volumineux (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contient un exemple d’utilisation de LINQ to XML pour transformer des documents XML extrêmement volumineux tout en maintenant un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="6a9df-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a9df-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="6a9df-114">Example</span></span>  
 <span data-ttu-id="6a9df-115">Cet exemple crée une méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="6a9df-115">This example creates a custom axis method.</span></span> <span data-ttu-id="6a9df-116">Vous pouvez l'interroger à l'aide d'une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a9df-116">You can query it by using a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query.</span></span> <span data-ttu-id="6a9df-117">La méthode d'axe personnalisée, `StreamRootChildDoc`, est une méthode conçue spécifiquement pour lire un document qui possède un élément `Child` à répétition.</span><span class="sxs-lookup"><span data-stu-id="6a9df-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
<span data-ttu-id="6a9df-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6a9df-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="6a9df-119">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6a9df-119">This example produces the following output:</span></span>  
  
<span data-ttu-id="6a9df-120"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6a9df-120"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="6a9df-121">Dans cet exemple, le document source est très petit.</span><span class="sxs-lookup"><span data-stu-id="6a9df-121">In this example, the source document is very small.</span></span> <span data-ttu-id="6a9df-122">Toutefois, cet exemple aurait un faible encombrement mémoire même s'il y avait des millions d'éléments `Child`.</span><span class="sxs-lookup"><span data-stu-id="6a9df-122">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a9df-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a9df-123">See Also</span></span>  
 <span data-ttu-id="6a9df-124">[Procédure pas à pas : Implémentation IEnumerable(Of T) en Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md) </span><span class="sxs-lookup"><span data-stu-id="6a9df-124">[Walkthrough: Implementing IEnumerable(Of T) in Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md) </span></span>  
<span data-ttu-id="6a9df-125"> [L’analyse XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)</span><span class="sxs-lookup"><span data-stu-id="6a9df-125"> [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)</span></span>
