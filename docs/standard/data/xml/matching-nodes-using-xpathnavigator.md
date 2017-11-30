---
title: "Mise en correspondance de nœuds avec XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a51c358ecb50c94ccde9f86ba80fc8f0670f82d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="81f5b-102">Mise en correspondance de nœuds avec XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="81f5b-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="81f5b-103">La classe <xref:System.Xml.XPath.XPathNavigator> fournit la méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> permettant de déterminer si un nœud correspond à une expression XPath.</span><span class="sxs-lookup"><span data-stu-id="81f5b-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="81f5b-104">La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> prend une expression XPath comme entrée et retourne un objet <xref:System.Boolean> indiquant si le nœud actuel correspond à l'expression XPath donnée ou à l'objet <xref:System.Xml.XPath.XPathExpression> compilé donné.</span><span class="sxs-lookup"><span data-stu-id="81f5b-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="81f5b-105">Mise en correspondance de nœuds</span><span class="sxs-lookup"><span data-stu-id="81f5b-105">Matching Nodes</span></span>  
 <span data-ttu-id="81f5b-106">La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> retourne `true` si le nœud actuel correspond à l'expression XPath spécifiée.</span><span class="sxs-lookup"><span data-stu-id="81f5b-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="81f5b-107">Par exemple, dans le code suivant, la méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> retournera `true` si le nœud actuel est l'élément `b` et si l'élément `b` a un attribut `c`.</span><span class="sxs-lookup"><span data-stu-id="81f5b-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81f5b-108">La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> ne modifie pas l'état de l'objet <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="81f5b-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a><span data-ttu-id="81f5b-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81f5b-109">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="81f5b-110">Traitement des données XML à l’aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="81f5b-110">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="81f5b-111">Sélectionnez les données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="81f5b-111">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="81f5b-112">Évaluer les Expressions XPath à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="81f5b-112">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="81f5b-113">Types de nœuds reconnus avec les requêtes XPath</span><span class="sxs-lookup"><span data-stu-id="81f5b-113">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="81f5b-114">Espaces de noms et des requêtes XPath</span><span class="sxs-lookup"><span data-stu-id="81f5b-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="81f5b-115">Expressions XPath compilées</span><span class="sxs-lookup"><span data-stu-id="81f5b-115">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
