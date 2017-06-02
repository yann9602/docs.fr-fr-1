---
title: "S&#233;rialisation&#160;XML avec les services&#160;Web XML | Microsoft Docs"
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
  - "fichiers .asmx"
  - "fichiers asmx"
  - "attributs (.NET Framework), sérialisation XML"
  - "sérialisation XML encodée"
  - "sérialisation XML littérale"
  - "sérialisation, attributs"
  - "sérialisation, SOAP"
  - "SOAP, sérialisation XML"
  - "sérialisation XML, attributs"
  - "sérialisation XML, services Web XML."
  - "services Web XML., sérialisation XML"
ms.assetid: a416192f-8102-458e-bc0a-0b8f3f784da9
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# S&#233;rialisation&#160;XML avec les services&#160;Web XML
La sérialisation XML est le mécanisme de transport sous\-jacent utilisé dans l'architecture de services Web XML, exécutée par la classe [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx).Pour contrôler le code XML généré par un service Web XML, vous pouvez appliquer les attributs répertoriés dans [Attributs qui contrôlent la sérialisation XML](../../../docs/framework/serialization/attributes-that-control-xml-serialization.md) et [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md) aux classes, valeurs de retour, paramètres et champs d'un fichier utilisé pour créer un service Web XML \(.asmx\).Pour plus d'informations sur la création d'un service Web XML, consultez [Building XML Web Services Using ASP.NET](http://msdn.microsoft.com/fr-fr/01dfc27c-c68e-4910-a0aa-5e4c2a766b0c).  
  
## Styles littéral et encodé  
 Le code XML généré par un service Web XML peut être mis en forme de deux manières différentes \(style littéral ou encodé\) comme expliqué dans [Customizing SOAP Messages](http://msdn.microsoft.com/fr-fr/1d777288-c0d9-4e6a-b638-f010da031952).Par conséquent, il existe deux ensembles d'attributs qui contrôlent la sérialisation XML.Les attributs répertoriés dans [Attributs qui contrôlent la sérialisation XML](../../../docs/framework/serialization/attributes-that-control-xml-serialization.md) sont prévus pour contrôler le code XML de style littéral.Les attributs répertoriés dans [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md) contrôlent le style encodé.En appliquant ces attributs de manière sélective, vous pouvez personnaliser une application afin qu'elle retourne l'un ou l'autre de ces styles, voire les deux.En outre, ces attributs peuvent être appliqués \(le cas échéant\) aux valeurs de retour et aux paramètres.  
  
### Exemple d'utilisation des deux styles  
 Lorsque vous créez un service Web XML, vous pouvez utiliser les deux ensembles d'attributs sur les méthodes.Dans l'exemple de code suivant, la classe intitulée `MyService` contient deux méthodes de services Web XML, `MyLiteralMethod` et `MyEncodedMethod`.Ces deux méthodes exécutent la même fonction : retourner une instance de la classe `Order`.Dans la classe `Order` , les attributs [XmlTypeAttribute](frlrfSystemXmlSerializationXmlTypeAttributeClassTopic) et [SoapTypeAttribute](frlrfSystemXmlSerializationSoapTypeAttributeClassTopic) s'appliquent tous deux au champ `OrderID` et la propriété `ElementName` de ces deux attributs a des valeurs différentes.  
  
 Pour exécuter l'exemple, collez le code dans un fichier portant une extension .asmx et placez ce fichier dans un répertoire virtuel géré par les Services Internet \(IIS\).Dans un navigateur HTML, tel qu'Internet Explorer, tapez le nom de l'ordinateur, du répertoire virtuel et du fichier.  
  
```vb  
<%@ WebService Language="VB" Class="MyService" %>  
Imports System  
Imports System.Web.Services  
Imports System.Web.Services.Protocols  
Imports System.Xml.Serialization  
Public Class Order  
    ' Both types of attributes can be applied. Depending on which type  
    ' the method used, either one will affect the call.  
    <SoapElement(ElementName:= "EncodedOrderID"), _  
    XmlElement(ElementName:= "LiteralOrderID")> _  
    public OrderID As String  
End Class  
  
Public Class MyService  
    <WebMethod, SoapDocumentMethod> _  
    public Function MyLiteralMethod() As Order   
        Dim myOrder As Order = New Order()  
        return myOrder  
    End Function  
    <WebMethod, SoapRpcMethod> _  
    public Function MyEncodedMethod() As Order   
        Dim myOrder As Order = New Order()  
        return myOrder  
    End Function  
End Class  
  
```  
  
```csharp  
<%@ WebService Language="C#" Class="MyService" %>  
using System;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using System.Xml.Serialization;  
public class Order{  
    // Both types of attributes can be applied. Depending on which type  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
public class MyService{  
    [WebMethod][SoapDocumentMethod]  
    public Order MyLiteralMethod(){  
        Order myOrder = new Order();  
        return myOrder;  
    }  
    [WebMethod][SoapRpcMethod]  
    public Order MyEncodedMethod(){  
        Order myOrder = new Order();  
        return myOrder;  
    }  
}  
```  
  
 L'exemple de code suivant appelle `MyLiteralMethod`.Le nom d'élément est remplacé par "LiteralOrderID."  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethodResponse xmlns="http://tempuri.org/">  
            <MyLiteralMethodResult>  
                <LiteralOrderID>string</LiteralOrderID>  
            </MyLiteralMethodResult>  
        </MyLiteralMethodResponse>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 L'exemple de code suivant appelle `MyEncodedMethod`.Le nom d'élément est "EncodedOrderID."  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:tns="http://tempuri.org/" xmlns:types="http://tempuri.org/encodedTypes" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body soap:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
        <tns:MyEncodedMethodResponse>  
            <MyEncodedMethodResult href="#id1" />  
        </tns:MyEncodedMethodResponse>  
        <types:Order id="id1" xsi:type="types:Order">  
            <EncodedOrderID xsi:type="xsd:string">string</EncodedOrderID>  
        </types:Order>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### Application d'attributs aux valeurs de retour  
 Vous pouvez également appliquer des attributs aux valeurs de retour pour contrôler l'espace de noms, le nom d'élément, etc.L'exemple de code suivant applique l'attribut `XmlElementAttribute` à la valeur de retour de la méthode `MyLiteralMethod`.Ainsi, vous pouvez contrôler l'espace de noms et le nom d'élément.  
  
```vb  
<WebMethod, SoapDocumentMethod> _  
public Function MyLiteralMethod() As _  
<XmlElement(Namespace:="http://www.cohowinery.com", _  
ElementName:= "BookOrder")> _  
Order   
    Dim myOrder As Order = New Order()  
    return myOrder  
End Function  
  
```  
  
```csharp  
[return: XmlElement(Namespace = "http://www.cohowinery.com",  
ElementName = "BookOrder")]  
[WebMethod][SoapDocumentMethod]  
public Order MyLiteralMethod(){  
    Order myOrder = new Order();  
    return myOrder;  
}  
```  
  
 Lorsqu'il est appelé, le code retourne du code XML qui se présente comme suit.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethodResponse xmlns="http://tempuri.org/">  
            <BookOrder xmlns="http://www.cohowinery.com">  
                <LiteralOrderID>string</LiteralOrderID>  
            </BookOrder>  
        </MyLiteralMethodResponse>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### Attributs appliqués à des paramètres  
 Vous pouvez également appliquer des attributs à des paramètres pour spécifier l'espace de noms, le nom d'élément, etc.L'exemple de code suivant ajoute un paramètre à la méthode `MyLiteralMethodResponse` et applique l'attribut `XmlAttributeAttribute` au paramètre.Le nom d'élément et l'espace de noms sont tous deux définis pour le paramètre.  
  
```vb  
<WebMethod, SoapDocumentMethod> _  
public Function MyLiteralMethod(<XmlElement _  
("MyOrderID", Namespace:="http://www.microsoft.com")>ID As String) As _  
<XmlElement(Namespace:="http://www.cohowinery.com", _  
ElementName:= "BookOrder")> _  
Order   
    Dim myOrder As Order = New Order()  
    myOrder.OrderID = ID  
    return myOrder  
End Function  
  
```  
  
```csharp  
[return: XmlElement(Namespace = "http://www.cohowinery.com",  
ElementName = "BookOrder")]  
[WebMethod][SoapDocumentMethod]  
public Order MyLiteralMethod([XmlElement("MyOrderID",   
Namespace="http://www.microsoft.com")] string ID){  
    Order myOrder = new Order();  
    myOrder.OrderID = ID;  
    return myOrder;  
}   
```  
  
 La demande SOAP peut se présenter comme suit.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethod xmlns="http://tempuri.org/">  
            <MyOrderID xmlns="http://www.microsoft.com">string</MyOrderID>  
        </MyLiteralMethod>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### Application d'attributs à des classes  
 Si vous devez contrôler l'espace de noms des éléments qui correspondent aux classes, vous pouvez appliquer `XmlTypeAttribute`, `XmlRootAttribute` et `SoapTypeAttribute`, si nécessaire.Les exemples de code suivants s'appliquent tous trois à la classe `Order`.  
  
```vb  
<XmlType("BigBookService"), _  
SoapType("SoapBookService"), _  
XmlRoot("BookOrderForm")> _  
Public Class Order  
    ' Both types of attributes can be applied. Depending on which  
    ' the method used, either one will affect the call.  
    <SoapElement(ElementName:= "EncodedOrderID"), _  
    XmlElement(ElementName:= "LiteralOrderID")> _  
    public OrderID As String  
End Class  
  
```  
  
```csharp  
[XmlType("BigBooksService", Namespace = "http://www.cpandl.com")]  
[SoapType("SoapBookService")]  
[XmlRoot("BookOrderForm")]  
public class Order{  
    // Both types of attributes can be applied. Depending on which  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
```  
  
 Vous pouvez visualiser les résultats de l'application de `XmlTypeAttribute` et de `SoapTypeAttribute` lorsque vous examinez la description de service, comme illustré dans l'exemple de code suivant.  
  
```  
    <s:element name="BookOrderForm" type="s0:BigBookService" />   
- <s:complexType name="BigBookService">  
- <s:sequence>  
    <s:element minOccurs="0" maxOccurs="1" name="LiteralOrderID" type="s:string" />   
    </s:sequence>  
  
- <s:schema targetNamespace="http://tempuri.org/encodedTypes">  
- <s:complexType name="SoapBookService">  
- <s:sequence>  
    <s:element minOccurs="1" maxOccurs="1" name="EncodedOrderID" type="s:string" />   
    </s:sequence>  
    </s:complexType>  
    </s:schema>  
```  
  
 L'action de `XmlRootAttribute` est visible également dans les résultats des protocoles HTTP GET et HTTP POST, comme suit.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<BookOrderForm xmlns="http://tempuri.org/">  
    <LiteralOrderID>string</LiteralOrderID>  
</BookOrderForm>  
```  
  
## Voir aussi  
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)   
 [Comment : sérialiser un objet en tant que flux XML encodé selon le protocole SOAP](../../../docs/framework/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)   
 [Comment : substituer la sérialisation XML encodée selon le protocole SOAP](../../../docs/framework/serialization/how-to-override-encoded-soap-xml-serialization.md)   
 [Introduction à la sérialisation XML](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [Comment : sérialiser un objet](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [Comment : désérialiser un objet](../../../docs/framework/serialization/how-to-deserialize-an-object.md)