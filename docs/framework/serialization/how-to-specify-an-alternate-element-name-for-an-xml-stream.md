---
title: "Comment&#160;: sp&#233;cifier un nom d&#39;&#233;l&#233;ment diff&#233;rent pour un flux&#160;XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "classes, substituer"
  - "classes (substituer)"
  - "substituer la sérialisation XML"
  - "sérialisation, substituer"
  - "sérialisation XML, substituer"
  - "Flux XML, spécifier un nom d'élément différent pour"
ms.assetid: 5cc1c0b0-f94b-4525-9a41-88a582cd6668
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Comment&#160;: sp&#233;cifier un nom d&#39;&#233;l&#233;ment diff&#233;rent pour un flux&#160;XML
[Exemple de code](#cpconoverridingserializationofclasseswithxmlattributeoverridesclassanchor1)  
  
 Via [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx), vous pouvez générer plusieurs flux de données XML avec un même ensemble de classes.Vous pouvez procéder ainsi car deux services Web XML différents nécessitent les mêmes informations de base, avec seulement de légères différences.Par exemple, imaginez deux services Web XML qui traitent des commandes de livres. Ils nécessitent donc tous les deux des numéros ISBN.Un service utilise la balise \<ISBN\> tandis que l'autre utilise la balise \<BookID\>.Vous disposez d'une classe nommée `Book` qui contient un champ nommé `ISBN`.Lorsqu'une instance de la classe `Book` est sérialisée, elle utilise par défaut le nom de membre \(ISBN\) comme nom d'élément de balise.Pour le premier service Web XML, c'est ce qui est prévu.Toutefois, pour envoyer le flux de données XML au deuxième service Web XML, vous devez substituer la sérialisation afin que le nom d'élément de la balise soit `BookID`.  
  
### Pour créer un flux de données XML avec un nom d'élément différent  
  
1.  Créez une instance de la classe [XmlElementAttribute](frlrfSystemXmlSerializationXmlElementAttributeClassTopic).  
  
2.  Affectez "BookID" à <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> de <xref:System.Xml.Serialization.XmlElementAttribute>.  
  
3.  Créez une instance de la classe [XmlAttributes](frlrfSystemXmlSerializationXmlAttributesClassTopic).  
  
4.  Ajoutez l'objet **XmlElementAttribute** à la collection accessible via la propriété <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> de <xref:System.Xml.Serialization.XmlAttributes>.  
  
5.  Créez une instance de la classe [XmlAttributeOverrides](frlrfSystemXmlSerializationXmlAttributeOverridesClassTopic).  
  
6.  Ajoutez **XmlAttributes** à <xref:System.Xml.Serialization.XmlAttributeOverrides>, en passant le type de l'objet à substituer et le nom du membre substitué.  
  
7.  Créez une instance de la classe **XmlSerializer** avec **XmlAttributeOverrides**.  
  
8.  Créez une instance de la classe `Book` et sérialisez ou désérialisez\-la.  
  
## Exemple  
  
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
  
```  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## Voir aussi  
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [XmlElementAttribute](frlrfSystemXmlSerializationXmlElementAttributeClassTopic)   
 [XmlAttributes](frlrfSystemXmlSerializationXmlAttributesClassTopic)   
 [XmlAttributeOverrides](frlrfSystemXmlSerializationXmlAttributeOverridesClassTopic)   
 [Comment : sérialiser un objet](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [Comment : désérialiser un objet](../../../docs/framework/serialization/how-to-deserialize-an-object.md)   
 [Comment : désérialiser un objet](../../../docs/framework/serialization/how-to-deserialize-an-object.md)