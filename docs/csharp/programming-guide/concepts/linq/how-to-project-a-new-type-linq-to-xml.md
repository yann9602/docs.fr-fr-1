---
title: Guide pratique pour projeter un nouveau type (LINQ to XML) (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d3deb826bdccdc2a24db84c006fe317a2321442
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Guide pratique pour projeter un nouveau type (LINQ to XML) (C#)
Les autres exemples de cette section ont illustré des requêtes qui retournent des résultats comme <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> de `string` et <xref:System.Collections.Generic.IEnumerable%601> de `int`. Il s'agit de types de résultats courants, mais ils ne conviennent pas à chaque scénario. Dans de nombreux cas, vous souhaiterez que vos requêtes retournent un objet <xref:System.Collections.Generic.IEnumerable%601> d'un autre type.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment instancier des objets dans la clause `select`. Le code définit tout d'abord une nouvelle classe avec un constructeur, puis modifie l'instruction `select` de sorte que l'expression soit une nouvelle instance de la nouvelle classe.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
class NameQty {  
    public string name;  
    public int qty;  
    public NameQty(string n, int q)  
    {  
        name = n;  
        qty = q;  
    }  
};  
  
class Program {  
    public static void Main() {  
        XElement po = XElement.Load("PurchaseOrder.xml");  
  
        IEnumerable<NameQty> nqList =  
            from n in po.Descendants("Item")  
            select new NameQty(  
                    (string)n.Element("ProductName"),  
                    (int)n.Element("Quantity")  
                );  
  
        foreach (NameQty n in nqList)  
            Console.WriteLine(n.name + ":" + n.qty);  
    }  
}  
```  
  
 Cet exemple utilise la méthode `M:System.Xml.Linq.XElement.Element` introduite dans la rubrique [Guide pratique pour récupérer un seul élément enfant (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). Il utilise également des casts pour récupérer les valeurs des éléments retournés par la méthode `M:System.Xml.Linq.XElement.Element`.  
  
 Cet exemple génère la sortie suivante :  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Projections et transformations (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
