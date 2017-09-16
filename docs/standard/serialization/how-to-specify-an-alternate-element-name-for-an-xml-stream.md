---
title: "Guide pratique pour spécifier un nom d’élément différent pour un flux XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XML serialization, overriding
- serialization, overriding
- XML stream, specifying alternate element name for
- overriding XML serialization
- classes, overriding
- overriding classes
ms.assetid: 5cc1c0b0-f94b-4525-9a41-88a582cd6668
caps.latest.revision: 7
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: bd06d53ff1d28b3b3ec9937b4c3efdb1d784c481
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a>Guide pratique pour spécifier un nom d’élément différent pour un flux XML
[Exemple de code](#cpconoverridingserializationofclasseswithxmlattributeoverridesclassanchor1)  
  
 Grâce à [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx), vous pouvez générer plusieurs flux XML avec un même ensemble de classes. Vous pouvez procéder ainsi car deux services Web XML différents nécessitent les mêmes informations de base, avec seulement de légères différences. Par exemple, imaginez deux services Web XML qui traitent des commandes de livres. Ils nécessitent donc tous les deux des numéros ISBN. Un service utilise la balise \<ISBN> tandis que l’autre utilise la balise \<BookID>. Vous disposez d'une classe nommée `Book` qui contient un champ nommé `ISBN`. Lorsqu'une instance de la classe `Book` est sérialisée, elle utilise par défaut le nom de membre (ISBN) comme nom d'élément de balise. Pour le premier service Web XML, c'est ce qui est prévu. Toutefois, pour envoyer le flux de données XML au deuxième service Web XML, vous devez substituer la sérialisation afin que le nom d'élément de la balise soit `BookID`.  
  
### <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a>Pour créer un flux de données XML avec un nom d'élément différent  
  
1.  Créez une instance de la classe <xref:System.Xml.Serialization.XmlElementAttribute>.  
  
2.  Affectez "BookID" à <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> de <xref:System.Xml.Serialization.XmlElementAttribute>.  
  
3.  Créez une instance de la classe <xref:System.Xml.Serialization.XmlAttributes>.  
  
4.  Ajoutez l'objet `XmlElementAttribute` à la collection accessible via la propriété <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> de <xref:System.Xml.Serialization.XmlAttributes>.  
  
5.  Créez une instance de la classe <xref:System.Xml.Serialization.XmlAttributeOverrides>.  
  
6.  Ajoutez `XmlAttributes` à <xref:System.Xml.Serialization.XmlAttributeOverrides>, en passant le type de l'objet à substituer et le nom du membre substitué.  
  
7.  Créez une instance de la classe `XmlSerializer` avec `XmlAttributeOverrides`.  
  
8.  Créez une instance de la classe `Book` et sérialisez ou désérialisez-la.  
  
## <a name="example"></a>Exemple  
  
```vb  
Public Class SerializeOverride()  
    ' Creates an XmlElementAttribute with the alternate name.  
    Dim myElementAttribute As XmlElementAttribute = _  
    New XmlElementAttribute()  
    myElementAttribute.ElementName = "BookID"  
    Dim myAttributes As XmlAttributes = New XmlAttributes()  
    myAttributes.XmlElements.Add(myElementAttribute)  
    Dim myOverrides As XmlAttributeOverrides = New XmlAttributeOverrides()  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes)  
    Dim mySerializer As XmlSerializer = _  
    New XmlSerializer(GetType(Book), myOverrides)  
    Dim b As Book = New Book()  
    b.ISBN = "123456789"  
    ' Creates a StreamWriter to write the XML stream to.  
    Dim writer As StreamWriter = New StreamWriter("Book.xml")  
    mySerializer.Serialize(writer, b);  
End Class  
```  
  
```csharp  
public class SerializeOverride()  
{  
    // Creates an XmlElementAttribute with the alternate name.  
    XmlElementAttribute myElementAttribute = new XmlElementAttribute();  
    myElementAttribute.ElementName = "BookID";  
    XmlAttributes myAttributes = new XmlAttributes();  
    myAttributes.XmlElements.Add(myElementAttribute);  
    XmlAttributeOverrides myOverrides = new XmlAttributeOverrides();  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes);  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(Book), myOverrides)  
    Book b = new Book();  
    b.ISBN = "123456789"  
    // Creates a StreamWriter to write the XML stream to.  
    StreamWriter writer = new StreamWriter("Book.xml");  
    mySerializer.Serialize(writer, b);  
}  
```  
  
 Le flux de données XML peut se présenter comme suit.  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Serialization.XmlElementAttribute>   
 <xref:System.Xml.Serialization.XmlAttributes>   
 <xref:System.Xml.Serialization.XmlAttributeOverrides>   
 [Sérialisation XML et SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)   
 [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx)   
 [Guide pratique pour sérialiser un objet](../../../docs/standard/serialization/how-to-serialize-an-object.md)   
 [Guide pratique pour désérialiser un objet](../../../docs/standard/serialization/how-to-deserialize-an-object.md)   
 [Guide pratique pour désérialiser un objet](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

