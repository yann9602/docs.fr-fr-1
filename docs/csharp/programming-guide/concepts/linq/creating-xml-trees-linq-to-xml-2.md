---
title: "Création d’arborescences XML en C# (LINQ to XML) | Microsoft Docs"
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
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
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
ms.openlocfilehash: 92ba0d345183ec503d61254355f948f82a18f053
ms.lasthandoff: 03/13/2017

---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>Création d’arborescences XML en C# (LINQ to XML)
Cette section fournit des informations sur la création d’arborescences XML en C#.  
  
 Pour plus d’informations sur l’utilisation des résultats de requêtes LINQ comme contenu d’un <xref:System.Xml.Linq.XElement>, consultez [Construction fonctionnelle (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Construction d'éléments  
 Les signatures des constructeurs <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute> vous permettent de passer le contenu de l’élément ou de l’attribut comme arguments du constructeur. Étant donné que l’un des constructeurs prend une quantité variable d’arguments, vous pouvez passer une quantité quelconque d’éléments enfants. Bien entendu, chacun de ces éléments enfants peut contenir ses propres éléments enfants. Pour tout élément, vous pouvez ajouter une quantité quelconque d'attributs.  
  
 Quand vous ajoutez des objets <xref:System.Xml.Linq.XNode> (notamment <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, si le nouveau contenu n’a pas de parent, les objets sont simplement attachés à l’arborescence XML. Si le nouveau contenu a déjà un parent et fait partie d’une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l’arborescence XML. Ceci est illustré dans le dernier exemple de cette rubrique.  
  
 Pour créer un `contacts`<xref:System.Xml.Linq.XElement>, vous pouvez utiliser le code suivant :  
  
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
  
 S’il est mis en retrait correctement, le code permettant de construire des objets <xref:System.Xml.Linq.XElement> ressemble étroitement à la structure du code XML sous-jacent.  
  
## <a name="xelement-constructors"></a>Constructeurs XElement  
 La classe <xref:System.Xml.Linq.XElement> utilise les constructeurs suivants pour la construction fonctionnelle. Notez qu’il existe d’autres constructeurs pour <xref:System.Xml.Linq.XElement>, mais ils ne sont pas répertoriés ici car ils ne sont pas utilisés pour la construction fonctionnelle.  
  
|Constructeur|Description|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|Crée un <xref:System.Xml.Linq.XElement>. Le paramètre `name` spécifie le nom de l'élément ; `content` spécifie le contenu de l'élément.|  
|`XElement(XName name)`|Crée un <xref:System.Xml.Linq.XElement> avec son <xref:System.Xml.Linq.XName> initialisé au nom spécifié.|  
|`XElement(XName name, params object[] content)`|Crée un <xref:System.Xml.Linq.XElement> avec son <xref:System.Xml.Linq.XName> initialisé au nom spécifié. Les attributs et/ou éléments enfants sont créés à partir du contenu de la liste de paramètres.|  
  
 Le paramètre `content` est extrêmement souple. Il prend en charge tout type d’objet qui est un enfant valide d’un <xref:System.Xml.Linq.XElement>. Les règles suivantes s'appliquent à différents types d'objets passés dans ce paramètre :  
  
-   Une chaîne est ajoutée en tant que contenu de texte.  
  
-   Un <xref:System.Xml.Linq.XElement> est ajouté comme élément enfant.  
  
-   Un <xref:System.Xml.Linq.XAttribute> est ajouté comme attribut.  
  
-   Un <xref:System.Xml.Linq.XProcessingInstruction>, un <xref:System.Xml.Linq.XComment> ou un <xref:System.Xml.Linq.XText> est ajouté en comme contenu enfant.  
  
-   Un <xref:System.Collections.IEnumerable> est énuméré, et ces règles sont appliquées de manière récursive aux résultats.  
  
-   Pour tout autre type, sa méthode `ToString` est appelée et le résultat est ajouté en tant que contenu texte.  
  
### <a name="creating-an-xelement-with-content"></a>Création d'un XElement avec du contenu  
 Vous pouvez créer un <xref:System.Xml.Linq.XElement> qui contient du contenu simple avec un appel de méthode unique. Pour cela, spécifiez le contenu comme second paramètre, comme suit :  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Vous pouvez passer tout type d'objet en tant que contenu. Par exemple, le code suivant crée un élément qui contient un nombre à virgule flottante en tant que contenu :  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Le nombre à virgule flottante est boxed et passé au constructeur. Le nombre boxed est converti en une chaîne et utilisé comme contenu de l'élément.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Création d'un XElement avec un élément enfant  
 Si vous passez une instance de la classe <xref:System.Xml.Linq.XElement> comme argument de contenu, le constructeur crée un élément avec un élément enfant :  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Création d'un XElement avec plusieurs éléments enfants  
 Vous pouvez passer plusieurs objets <xref:System.Xml.Linq.XElement> comme contenu. Chacun des objets <xref:System.Xml.Linq.XElement> est inclus comme élément enfant.  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 En étendant l'exemple ci-dessus, vous pouvez créer une arborescence XML entière, comme suit :  
  
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
Console.WriteLine(contacts);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  
  
### <a name="creating-an-empty-element"></a>Création d'un élément vide  
 Pour créer un objet <xref:System.Xml.Linq.XElement> vide, vous ne passez aucun contenu au constructeur. L'exemple suivant crée un élément vide :  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>attachement et clonage  
 Comme mentionné précédemment, quand vous ajoutez des objets <xref:System.Xml.Linq.XNode> (notamment <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, si le nouveau contenu n’a pas de parent, les objets sont simplement attachés à l’arborescence XML. Si le nouveau contenu a déjà un parent et fait partie d’une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l’arborescence XML.  
  
```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
