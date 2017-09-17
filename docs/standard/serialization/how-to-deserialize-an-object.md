---
title: "Comment : désérialiser un objet"
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
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
caps.latest.revision: 4
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 4cda35e71de77c63b2b4f414446c3af06fb407b1
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-deserialize-an-object"></a>Comment : désérialiser un objet
Lorsque vous désérialisez un objet, le format de transport vous permet de déterminer si vous créez un flux de données ou un objet de fichier. Après avoir déterminé le format de transport, vous pouvez appeler la méthode <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> ou <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A>, si nécessaire.  
  
### <a name="to-deserialize-an-object"></a>Pour désérialiser un objet  
  
1.  Construisez un <xref:System.Xml.Serialization.XmlSerializer> à l'aide du type d'objet à désérialiser.  
  
2.  Appelez la méthode <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> pour produire un réplica de l'objet. Lorsque vous effectuez une désérialisation, vous devez exécuter un transtypage de l'objet retourné au type d'origine (comme illustré dans l'exemple suivant). Celui-ci désérialise l'objet dans un fichier (bien qu'il puisse également être désérialisé dans un flux de données).  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à la sérialisation XML](../../../docs/standard/serialization/introducing-xml-serialization.md)   
 [Guide pratique pour sérialiser un objet](../../../docs/standard/serialization/how-to-serialize-an-object.md)

