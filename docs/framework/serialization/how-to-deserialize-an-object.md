---
title: "Comment&#160;: d&#233;s&#233;rialiser un objet | Microsoft Docs"
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
  - "désérialiser des objets"
  - "objets, étapes de désérialisation"
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Comment&#160;: d&#233;s&#233;rialiser un objet
Lorsque vous désérialisez un objet, le format de transport vous permet de déterminer si vous créez un flux de données ou un objet de fichier.Après avoir déterminé le format de transport, vous pouvez appeler la méthode <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> ou <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A>, si nécessaire.  
  
### Pour désérialiser un objet  
  
1.  Construisez un <xref:System.Xml.Serialization.XmlSerializer> à l'aide du type d'objet à désérialiser.  
  
2.  Appelez la méthode <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> pour produire un réplica de l'objet.Lorsque vous effectuez une désérialisation, vous devez exécuter un transtypage de l'objet retourné au type d'origine \(comme illustré dans l'exemple suivant\). Celui\-ci désérialise l'objet dans un fichier \(bien qu'il puisse également être désérialisé dans un flux de données\).  
  
    ```vb  
    Dim myObject As MySerializableClass  
    ' Construct an instance of the XmlSerializer with the type  
    ' of object that is being deserialized.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To read the file, create a FileStream.  
    Dim myFileStream As FileStream = _  
    New FileStream("myFileName.xml", FileMode.Open)  
    ' Call the Deserialize method and cast to the object type.  
    myObject = CType( _  
    mySerializer.Deserialize(myFileStream), MySerializableClass)  
  
    ```  
  
    ```csharp  
    MySerializableClass myObject;  
    // Construct an instance of the XmlSerializer with the type  
    // of object that is being deserialized.  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(MySerializableClass));  
    // To read the file, create a FileStream.  
    FileStream myFileStream =   
    new FileStream("myFileName.xml", FileMode.Open);  
    // Call the Deserialize method and cast to the object type.  
    myObject = (MySerializableClass)   
    mySerializer.Deserialize(myFileStream)  
    ```  
  
## Voir aussi  
 [Introduction à la sérialisation XML](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [Comment : sérialiser un objet](../../../docs/framework/serialization/how-to-serialize-an-object.md)