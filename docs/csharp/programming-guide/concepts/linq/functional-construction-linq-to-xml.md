---
title: Construction fonctionnelle (LINQ to XML) (C#) | Microsoft Docs
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
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: aa522bb2c9d1c570aff237a76fc745bad52c8bfc
ms.lasthandoff: 03/13/2017

---
# <a name="functional-construction-linq-to-xml-c"></a>Construction fonctionnelle (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] offre un moyen puissant de créer des éléments XML appelé *construction fonctionnelle*. La construction fonctionnelle est la capacité à créer une arborescence XML en une seule instruction.  
  
 Plusieurs fonctionnalités clés de l'interface de programmation [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] autorisent la construction fonctionnelle :  
  
-   Le constructeur <xref:System.Xml.Linq.XElement> accepte différents types d’arguments comme contenu. Par exemple, vous pouvez passer un autre objet <xref:System.Xml.Linq.XElement>, qui devient un élément enfant. Vous pouvez passer un objet <xref:System.Xml.Linq.XAttribute>, qui devient un attribut de l’élément. Ou vous pouvez passer tout autre type d'objet, qui est converti en chaîne et devient le contenu texte de l'élément.  
  
-   Le constructeur <xref:System.Xml.Linq.XElement> accepte un tableau `params` de type <xref:System.Object>, de sorte que vous puissiez passer toute quantité d’objets au constructeur. Cela vous permet de créer un élément dont le contenu est complexe.  
  
-   Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l’objet est énumérée et tous les éléments de la collection sont ajoutés. Si la collection contient les objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, chaque élément de la collection est ajouté séparément. Ceci est important, car cela vous permet de passer les résultats d’une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] au constructeur.  
  
 Ces fonctionnalités vous permettent d’écrire du code pour créer une arborescence XML. Voici un exemple :  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Ces fonctionnalités permettent également d’écrire du code qui utilise les résultats de requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] lorsque vous créez une arborescence XML, comme suit :  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
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
 [Création d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
