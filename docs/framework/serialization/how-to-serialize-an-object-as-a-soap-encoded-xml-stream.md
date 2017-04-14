---
title: "Comment&#160;: s&#233;rialiser un objet en tant que flux&#160;XML encod&#233; selon le protocole&#160;SOAP | Microsoft Docs"
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
  - "sérialisation, SOAP"
  - "SOAP, sérialisation XML"
  - "sérialisation XML, SOAP"
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Comment&#160;: s&#233;rialiser un objet en tant que flux&#160;XML encod&#233; selon le protocole&#160;SOAP
[Exemple de code](#cpconxmlserializationusingsoapprotocolanchor1)  
  
 Un message SOAP étant construit à l'aide de code XML, [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) peut être utilisé pour sérialiser des classes et générer des messages encodés selon le protocole SOAP.Le XML résultant est conforme à la section 5 du document du World Wide Web Consortium \(www.w3.org\) document, "Simple Object Access Protocol \(SOAP\) 1.1".Lorsque vous créez un service Web XML qui communique à l'aide de messages SOAP, vous pouvez personnaliser le flux de données XML en appliquant un ensemble d'attributs SOAP spéciaux aux classes et membres de classes.Pour obtenir une liste d'attributs, consultez [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
### Pour sérialiser un objet en tant que flux de données XML encodé selon le protocole SOAP  
  
1.  Créez la classe à l'aide de l'[Outil XML Schema Definition \(Xsd.exe\)](../../../docs/framework/serialization/xml-schema-definition-tool-xsd-exe.md).  
  
2.  Appliquez un ou plusieurs des attributs spéciaux se trouvant dans **System.Xml.Serialization**.Consultez la liste indiquée dans « Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP ».  
  
3.  Créez un **XmlTypeMapping** en créant un nouveau **SoapReflectionImporter** et en appelant la méthode **ImportTypeMapping** avec le type de la classe sérialisée.  
  
     L'exemple de code suivant appelle la méthode **ImportTypeMapping**de la classe **SoapReflectionImporter** pour créer un **XmlTypeMapping**.  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping = (New SoapReflectionImporter(). _  
    ImportTypeMapping(GetType(Group))  
  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping = (new SoapReflectionImporter().  
    ImportTypeMapping(typeof(Group));  
    ```  
  
4.  Créez une instance de la classe **XmlSerializer** en passant **XmlTypeMapping** au constructeur <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29>.  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  Appelez la méthode **Serialize** ou **Deserialize**.  
  
## Exemple  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping = (New SoapReflectionImporter(). _  
ImportTypeMapping(GetType(Group))  
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping = (new SoapReflectionImporter().ImportTypeMapping(typeof(Group));  
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## Voir aussi  
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)   
 [Sérialisation XML avec les services Web XML](../../../docs/framework/serialization/xml-serialization-with-xml-web-services.md)   
 [Comment : sérialiser un objet](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [Comment : désérialiser un objet](../../../docs/framework/serialization/how-to-deserialize-an-object.md)   
 [Comment : substituer la sérialisation XML encodée selon le protocole SOAP](../../../docs/framework/serialization/how-to-override-encoded-soap-xml-serialization.md)