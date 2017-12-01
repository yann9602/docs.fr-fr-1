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
# <a name="matching-nodes-using-xpathnavigator"></a>Mise en correspondance de nœuds avec XPathNavigator
La classe <xref:System.Xml.XPath.XPathNavigator> fournit la méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> permettant de déterminer si un nœud correspond à une expression XPath. La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> prend une expression XPath comme entrée et retourne un objet <xref:System.Boolean> indiquant si le nœud actuel correspond à l'expression XPath donnée ou à l'objet <xref:System.Xml.XPath.XPathExpression> compilé donné.  
  
## <a name="matching-nodes"></a>Mise en correspondance de nœuds  
 La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> retourne `true` si le nœud actuel correspond à l'expression XPath spécifiée. Par exemple, dans le code suivant, la méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> retournera `true` si le nœud actuel est l'élément `b` et si l'élément `b` a un attribut `c`.  
  
> [!NOTE]
>  La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> ne modifie pas l'état de l'objet <xref:System.Xml.XPath.XPathNavigator>.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Traitement des données XML à l’aide du modèle de données XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Sélectionnez les données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Évaluer les Expressions XPath à l’aide de XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Types de nœuds reconnus avec les requêtes XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Espaces de noms et des requêtes XPath](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Expressions XPath compilées](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
