---
title: Construction fonctionnelle (LINQ to XML) (Visual Basic) | Documents Microsoft
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
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9fa8cb3c97a1e23a863296c828c82b240e9ab5db
ms.lasthandoff: 03/13/2017

---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>Construction fonctionnelle (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]fournit un moyen puissant de créer des éléments XML appelé *construction fonctionnelle*. La construction fonctionnelle est la capacité à créer une arborescence XML en une seule instruction.  
  
 Plusieurs fonctionnalités clés de l'interface de programmation [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] autorisent la construction fonctionnelle :  
  
-   Le <xref:System.Xml.Linq.XElement>constructeur prend différents types d’arguments comme contenu.</xref:System.Xml.Linq.XElement> Par exemple, vous pouvez passer à un autre <xref:System.Xml.Linq.XElement>objet, qui devient un élément enfant.</xref:System.Xml.Linq.XElement> Vous pouvez passer un <xref:System.Xml.Linq.XAttribute>objet, qui devient un attribut de l’élément.</xref:System.Xml.Linq.XAttribute> Ou vous pouvez passer tout autre type d'objet, qui est converti en chaîne et devient le contenu texte de l'élément.  
  
-   Le <xref:System.Xml.Linq.XElement>constructeur prend un `params` tableau de type <xref:System.Object>, de sorte que vous puissiez passer toute quantité d’objets au constructeur.</xref:System.Object> </xref:System.Xml.Linq.XElement> Cela vous permet de créer un élément dont le contenu est complexe.  
  
-   Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l’objet est énumérée et tous les éléments dans la collection sont ajoutés.</xref:System.Collections.Generic.IEnumerable%601> Si la collection contient <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>des objets, chaque élément de la collection est ajouté séparément.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> Ceci est important car il vous permet de transmettre les résultats d’une [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requête au constructeur.  
  
 Voici un exemple :  
  
 Ces fonctionnalités vous permettent d’écrire du code à l’aide de littéraux XML pour créer une arborescence XML et également d’écrire du code qui utilise les résultats de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requêtes lorsque vous créez une arborescence XML :  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
