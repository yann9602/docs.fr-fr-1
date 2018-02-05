---
title: "Évaluation d’expressions XPath à l’aide de XPathNavigator"
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
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d4515b8ebea338a153319dfd02eab8d389b843b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="e7303-102">Évaluation d’expressions XPath à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e7303-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="e7303-103">La classe <xref:System.Xml.XPath.XPathNavigator> fournit la méthode <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> permettant d'évaluer une expression XPath.</span><span class="sxs-lookup"><span data-stu-id="e7303-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="e7303-104">La méthode <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> prend une expression XPath, l'évalue et retourne le type XPath W3C booléen, nombre, chaîne ou collection de nœuds selon le résultat de l'expression XPath.</span><span class="sxs-lookup"><span data-stu-id="e7303-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="e7303-105">Méthode d'évaluation</span><span class="sxs-lookup"><span data-stu-id="e7303-105">The Evaluate Method</span></span>  
 <span data-ttu-id="e7303-106">La méthode <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> prend une expression XPath, l'évalue et retourne un résultat typé tel que booléen (<xref:System.Boolean>), nombre (<xref:System.Double>), chaîne (<xref:System.String>) ou collection de nœuds (<xref:System.Xml.XPath.XPathNodeIterator>).</span><span class="sxs-lookup"><span data-stu-id="e7303-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="e7303-107">Par exemple, la méthode <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> peut être utilisée dans une méthode mathématique.</span><span class="sxs-lookup"><span data-stu-id="e7303-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="e7303-108">L'exemple de code suivant calcule le prix total de tous les livres du fichier `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="e7303-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 <span data-ttu-id="e7303-109">L'exemple prend le fichier `books.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="e7303-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="e7303-110">Fonctions position et last</span><span class="sxs-lookup"><span data-stu-id="e7303-110">position and last Functions</span></span>  
 <span data-ttu-id="e7303-111">La méthode <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> est surchargée.</span><span class="sxs-lookup"><span data-stu-id="e7303-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="e7303-112">L'une des méthodes <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> prend un objet <xref:System.Xml.XPath.XPathNodeIterator> comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="e7303-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="e7303-113">Cette méthode <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> particulière est identique à la méthode <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> qui ne prend qu'un objet <xref:System.Xml.XPath.XPathExpression> comme paramètre, si ce n'est qu'elle permet à un argument node set de spécifier le contexte actuel sur lequel effectuer l'évaluation.</span><span class="sxs-lookup"><span data-stu-id="e7303-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="e7303-114">Ce contexte est obligatoire pour les fonctions XPath `position()` et `last()` car celles-ci se rapportent au nœud de contexte actuel.</span><span class="sxs-lookup"><span data-stu-id="e7303-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="e7303-115">À moins d'être utilisées comme prédicats dans une étape de localisation, l'évaluation des fonctions `position()` et `last()` nécessite une référence à une collection de nœuds, sinon les fonctions `position` et `last` retournent `0`.</span><span class="sxs-lookup"><span data-stu-id="e7303-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7303-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7303-116">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="e7303-117">Traitement des données XML à l’aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="e7303-117">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="e7303-118">Sélection de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e7303-118">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="e7303-119">Mise en correspondance de nœuds avec XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e7303-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="e7303-120">Types de nœuds reconnus avec les requêtes XPath</span><span class="sxs-lookup"><span data-stu-id="e7303-120">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="e7303-121">Requêtes et espaces de noms XPath</span><span class="sxs-lookup"><span data-stu-id="e7303-121">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="e7303-122">Expressions XPath compilées</span><span class="sxs-lookup"><span data-stu-id="e7303-122">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
